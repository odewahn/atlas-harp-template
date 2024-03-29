# Perlin Wave

This chapter was written in [Markdown](http://daringfireball.net/projects/markdown/). 

Here's a perlin wave example from Dan Shiffman's Nature of Code book:

<pre data-executable="true" data-language="p5">
var yoff = 0.0;        // 2nd dimension of perlin noise

function setup() {
  createCanvas(710, 400);
}

function draw() {
  background(51);

  fill(255);
  // We are going to draw a polygon out of the wave points
  beginShape(); 
  
  var xoff = 0;       // Option #1: 2D Noise
  // float xoff = yoff; // Option #2: 1D Noise
  
  // Iterate over horizontal pixels
  for (var x = 0; x <= width; x += 10) {
    // Calculate a y value according to noise, map to 
    
    // Option #1: 2D Noise
    var y = map(noise(xoff, yoff), 0, 1, 200,300);

    // Option #2: 1D Noise
    // float y = map(noise(xoff), 0, 1, 200,300);
    
    // Set the vertex
    vertex(x, y); 
    // Increment x dimension for noise
    xoff += 0.05;
  }
  // increment y dimension for noise
  yoff += 0.01;
  vertex(width, height);
  vertex(0, height);
  endShape(CLOSE);
}
</pre>