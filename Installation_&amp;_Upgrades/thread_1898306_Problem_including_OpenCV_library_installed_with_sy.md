---
title: "Problem including OpenCV library installed with synaptic"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by mohitdaksh on 2011-12-21
Hello everyone,

I wanted to use a library ( Open Computer Vision library) in my C++ programs so I downloaded it from Synaptic. But when I put the "include" directive for the library g++ says it cannot find it. This is the directive that I have been using. I got this from an example somewhere on the web.

```
#include <cv.h>        // Main OpenCV library.
#include <highgui.h>    // OpenCV functions for files and graphical windows.
```I am using the same general command for compiling the program. 
```
g++ -Wall prog.cpp -o prog
```Are any other flags required?


Or can someone tell me how to add a library to gcc so that I can try to do it manually?

---

