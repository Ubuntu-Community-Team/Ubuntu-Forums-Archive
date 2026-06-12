---
title: "trouble launching programs"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by constant_attention on 2010-01-19
every now and then, after I install a new program using the software center, after the install, when I try to start the program, nothing happens.

For example, I added blender and it will not launch.

Am I missing something?  Do I need to remove the program and install it again?

---

### Post by constant_attention on 2010-01-19
well, I tried starting the example program (blender) from the terminal.  Here is what I got:

[email]united@united-desktop:~/.blende[/email]r$ blender -w
Compiled with Python version 2.6.4.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x9
  Serial number of failed request:  21
  Current serial number in output stream:  22
[email]united@united-desktop:~/.blende[/email]r$

---

