---
title: "ltsp localapps flash animation slow"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by astbis on 2010-07-09
Hi

On one client we have accaptable flash support but on another set the performance even with ltsp-localapps is sluggish at best.

System: Ubuntu Jaunty, with an updated system.
My best bets would be the either the hardware isn't powerful enough, what i doubt. And the other is that there is not the necessary graphics support enabled.

Below i added some debug information. But my questions are. What is wrong and how can i do to solve it.

Thanks for any help

### acer client (desktop pc)
$ lspci
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapte

$ glxgears
378 frames in 5.0 seconds = 75.542 FPS
395 frames in 5.0 seconds = 78.954 FPS
398 frames in 5.0 seconds = 79.546 FPS
397 frames in 5.0 seconds = 79.238 FPS
377 frames in 5.0 seconds = 75.326 FPS
384 frames in 5.0 seconds = 76.763 FPS
39 frames in 5.1 seconds =  7.626 FPS
29 frames in 5.1 seconds =  5.699 FPS
29 frames in 5.1 seconds =  5.699 FPS

$ glxinfo
name of display: :7.0
display: :7  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2


### terra client
$ glxgears
236 frames in 5.0 seconds = 47.118 FPS
249 frames in 5.0 seconds = 49.678 FPS
250 frames in 5.0 seconds = 49.801 FPS
249 frames in 5.0 seconds = 49.798 FPS
222 frames in 5.0 seconds = 44.339 FPS
214 frames in 5.1 seconds = 41.817 FPS
38 frames in 5.1 seconds =  7.455 FPS
39 frames in 5.1 seconds =  7.652 FPS
39 frames in 5.1 seconds =  7.655 FPS

$ glx
glxdemo   glxgears  glxheads  glxinfo   
dennis@ltsp212:~$ glxinfo 
name of display: :7.0
display: :7  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

$ lspci
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

---

