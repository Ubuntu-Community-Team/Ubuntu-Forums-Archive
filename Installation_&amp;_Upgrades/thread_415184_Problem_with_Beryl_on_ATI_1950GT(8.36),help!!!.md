---
title: "Problem with Beryl on ATI 1950GT(8.36),help!!!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by josephpei on 2007-04-20
Hardware:amd 3600, ati 1950GT
System: 7.04 amd64
Driver: ati fglrx 8.36

beryl can't work

---

### Post by josephpei on 2007-04-20
josephpei@josephpei:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1950 GT
OpenGL version string: 2.0.6458 (8.36.5)

josephpei@josephpei:~$ glxinfo | grep rendering
direct rendering: Yes

josephpei@josephpei:~$ glxgears 
42229 frames in 5.0 seconds = 8445.735 FPS
41726 frames in 5.0 seconds = 8345.113 FPS
42857 frames in 5.0 seconds = 8571.365 FPS

josephpei@josephpei:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
7679 frames in 5.0 seconds = 1535.800 FPS
8777 frames in 5.0 seconds = 1755.400 FPS

---

### Post by 00arthuryu on 2007-06-17
are you sure you got the right beryl version?
the latest beryl does not work with ATI XGL
you have to downgrade the Beryl version to the previous working version

---

