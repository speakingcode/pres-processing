# Processing Tutorial

Processing is a collection of libraries, tools and a specialized programming environment used for computer-driven visual and audio arts, intending to make it easy to create interactive, visually rich animations and applicatons.

-Free and open source
-Easy to use for beginners but powerful enough for advanced uses
-Suitable for quick sketches and prototypes as well as production work
-Java based, but uses a simpler scripting style that eases learning the basics of coding
-Not limited to use with its own IDE; can be used with any devlopment environment

## Getting Started

### Installation
Download the appropriate files for your platform at http://processing.org/download

#### Windows
Extract folder from .zip file and run `processing.exe`

#### OS-X
Double-click .zip file and drag Processing icon to Applications folder or another folder. Double click Processing icon to start

#### Linux
Extract tarball:
    tar xvfz processing-xxxx.tgz

Change to the extracted directory and run:
    cd processing-xxxx
    ./processing

Many distributions have packaged versions available as well.

### Using the Editor

#### File Menu
Allows you to create, save, and open sketches, export sketches (more on this later), load recent sketches, pull up the preferences menu, load example sketches from the example library, etc.

#### Edit Menu
Common editing functions like undo/redo, copy/cut/paste, comment/uncomment, change indentation, etc.

#### Sketch Menu
Run/Stop the sketch, 'Show' the sketch (fills the entire viewport), import code libraries, etc.

#### Tools Menu
Access common tools like color pickers and add more tools downloaded online

#### Help Menu
Quick access to various help resources on the web.

#### Shortcuts
Several shortcuts are available to create/save/open/export files and to change modes.

#### Export
Export creates single-click applications which can be targetted to Windows, Linux, and OS-X. Additional modes can be downloaded to target additional platforms such as Android or JavaScript

### Hello World
#### Static Sketches
Static sketches are a series of functions that result in a single, static image.

    line(5, 5, 100, 100);

Static sketches can have dynamic functionality such as loops.

    size(400, 400);
    background(0, 0, 0);
    stroke(255);
    line(0, 0, 400, 400);
    line(0, 400, 400, 0);
    fill(128, 0, 100);
    rect(100, 150, 200, 100);
    fill(128, 0, 200);
    stroke(128, 0, 200);
    ellipse(200, 200, 98, 98);
    for (int i = 0; i <= 20; i++)
    {
      int y = 200 + round( 100 * sin(((float)i/20) * (2 * PI)));
      int x = 200 + round( 100 * cos(((float)i/20) * (2 * PI)));
      fill(200 - (i*5) , 64 + (i*7), 100 + (i*5));
      ellipse(x, y, 10, 10);
    }

#### Interactive Sketches
Interactive sketches draw a series of frames by calling the functions `setup()` and `draw()`. `setup()` is called only once, while `draw()` is called repeatedly.

    void setup()
    {
      size(400, 400);
      background(0);
    }
    
    void draw()
    {
      stroke(random(255), random(255), random(255));
      line(0, 0, mouseX, mouseY);
    }

Of course, interactive sketches can be dynamic as well.

    void setup()
    {
      size(400, 400);
    }
    
    void draw()
    {
      background(0, 0, 0);
      for (int i = 0; i <= 20; i++)
      {
        int y = mouseY + round( abs(mouseY - 200) * sin(((float)i/20) * (2 * PI)));
        int x = mouseX + round( abs(mouseX - 200) * cos(((float)i/20) * (2 * PI)));
        fill(200 - (i*5) , 64 + (i*7), 100 + (i*5));
        ellipse(x, y, 10, 10);
      }
    }

## Basic shapes
### Coordinate System
The window is simply a Cartesian coordinate system where each point is 1 pixel, but the y-axis is flipped. (0,0) is the top-left position of the screen. The x-axis increases to the right and the y-axis increases downward.

### Point
A point requires just an x and y value, the coordinates of its position.

    point(15, 17);

### Line
A line spans between two points. Drawing a line requires 4 values, corresponding to it's start and end points.

    line(0, 100, 50, 200);

### Rectangle
#### Corner Mode
In the default mode (`CORNER`), a rectangle is specified by the coordinate of it's top-left corner, its width, and its height.

    rect(80,10,20,30);

#### Center Mode
A rectangle can be specified by the coordinate of it's _center_ point, its width, and its height by setting _rectMode_ to `CENTER`.

    rectMode(CENTER);
    rect(50, 200, 50, 40);

#### Corners Mode
A rectangle can be specified by the coordinates of its top-left corner and bottom-right corner by setting _rectMode_ to `CORNERS`.

    rectMode(CORNERS);
    rect(300, 100, 350, 120);

### Ellipse
In the default mode (`CENTER`), an ellipse spans the bounding box specified by its center coordinate, width, and height.

    ellipse(200, 300, 80, 19);

`ellipse()` also supports `CORNER` and `CORNERS` modes.

### Putting it Together
The basic shapes are sufficient to create more interesting images.
    
    size    (200,200);
    rectMode(CENTER);
    rect    (100, 100,  20, 100);
    ellipse (100, 70,   60, 60);
    ellipse (81,  70,   16, 32); 
    ellipse (119, 70,   16, 32); 
    line    (90,  150,  80, 160);
    line    (110, 150,  120,160);

## Color
### Stroke
`stroke()` sets the line or outline color of shapes drawn after it is called. Stroke can be eliminated with `noStroke()`.

### Fill
`fill()` sets the fill color of shapes drawn after it is called. Fill can be eliminated with `noFill()`.

### Background
`background()` sets the color for the entire window when it is called.

### Grayscale
For black & white grayscale shapes, a value ranging from 0 (black) to 255 (white) is passed to the color-setting functions.
    
    size(400, 400);
    background(0);
    stroke(255);
    fill(80);
    rect(100, 100, 100, 50);
    noStroke();
    fill(200);
    rect(120, 120, 60, 10);

### RGB
Color is specified as three values ranging from 0 to 255 each, representing the amount of red, green, and blue.

    size(200, 300); 
    background(0);
    noStroke();
    
    fill(255, 0, 0);
    rect(0, 0, 100, 100);
    
    fill(0, 255, 0);
    rect(0, 100, 100, 100);

    fill(0, 0, 255);
    rect(0, 200, 100, 100);

    fill(127, 0, 0);
    rect(100, 0, 100, 100);

    fill(0, 127, 0);
    rect(100, 100, 100, 100);

    fill(0, 0, 127);
    rect(100, 200, 100, 100);

### Alpha/Transparency
An optional forth value may specify the alpha or transparency of a color, ranging from 0 (fully transparent) to 255 (fully opaque);

    size(200, 300); 
    background(0);
    noStroke();
    
    fill(255, 0, 0);
    rect(0, 0, 100, 100);
    
    fill(0, 255, 0);
    rect(0, 100, 100, 100);

    fill(0, 0, 255);
    rect(0, 200, 100, 100);

    fill(127, 0, 0);
    rect(100, 0, 100, 100);

    fill(0, 127, 0);
    rect(100, 100, 100, 100);

    fill(0, 0, 127);
    rect(100, 200, 100, 100);

    fill(255, 255, 255, 75);
    rect(0, 50, 200, 100);

    fill(255, 255, 255, 150);
    rect(0, 175, 200, 100);

### Color Picker
The Processing editor has a built-in color picker tool which can be accessed by going to `Tools -> Color Selector`.

### Color Modes and Custom Ranges
The `colorMode()` function allows different color modes and ranges to be used, mostly for convenience.

    colorMode(RGB, 100);
    colorMode(RGB, 100, 100, 100, 10);

    colorMode(HSB, 360, 100, 100);

## Objects

## Two-Dimensional Arrays

## Curves

## Data
