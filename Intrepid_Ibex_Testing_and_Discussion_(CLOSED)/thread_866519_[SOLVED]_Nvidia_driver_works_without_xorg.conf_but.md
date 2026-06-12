---
title: "[SOLVED] Nvidia driver works without xorg.conf but"
date: 2008-07-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by almostlinux on 2008-07-21
Nvidia (7950 gtx)  driver through nvidia-glx-177 works (I get my max resolution) but when I try

$ glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault


And any games which rely on the card won't work .. :confused:

When I try a xorg.conf file through nvidia-xconfig (or the default one when I installed alpha2) it goes into failsafe mode. How do I go back to the direct rendering goodness?

---

### Post by ronacc on 2008-07-21
if you have a copy of your xorg.conf from hardy use that .

---

### Post by RAOF on 2008-07-21
Alternatively, run nvidia-xconfig and then remove the 'rgb.txt' line from the generated xorg.conf.  Apparently when there isn't an existing xorg.conf nvidia-xconfig will produce a file that isn't a valid xorg.conf for Xserver 1.5.

---

### Post by almostlinux on 2008-07-21
> **RAOF said:**
> Alternatively, run nvidia-xconfig and then remove the 'rgb.txt' line from the generated xorg.conf.  Apparently when there isn't an existing xorg.conf nvidia-xconfig will produce a file that isn't a valid xorg.conf for Xserver 1.5.

perfect .. thanks

---

