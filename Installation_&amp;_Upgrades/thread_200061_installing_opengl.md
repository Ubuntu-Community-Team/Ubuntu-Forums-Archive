---
title: "installing opengl"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by chrismiceli on 2006-06-19
I am trying to install the libraries for opengl so i can program with them.  I have already configured SDL but i can not seem to find the right libraries for opengl.  Thanks

---

### Post by Lux Perpetua on 2006-06-19
You should have OpenGL by default, but you'll need some -dev packages to program with them. Specifically, libgl1-mesa-dev (for OpenGL), libglu1-mesa-dev (for GLU), and libglut3-dev (for GLUT).

---

### Post by MrEricSir on 2006-06-19
If you have an NVidia card you'll want the glx-dev package.  I'm sure there's a similar package for ATI.

Mesa's OpenGL implementation is software only (no hardware acceleration.)

---

