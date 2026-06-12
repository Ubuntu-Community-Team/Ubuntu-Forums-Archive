---
title: "xorg.conf ignored + # of created screens does not match # of detected devices"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by suesswolf on 2013-05-04
three observations:
1. after ubuntu worked fine for several months, in Feb 2013
     suddenly at boot time instead of showing the login screen, the screen goes orange, 
   -- no login dialogue is visible. I need to press the power button five seconds ...
2. My only workaround at this time is: boot in failsafeX mode (VESA), which is cumbersome
3. Based on what I googled and read I tried:
3a. cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
   --> does not help
    it seems file /etc/X11/xorg.conf is ignored.
3b. boot into recovery mode, select root shell.
    type-> /etc/X11/X -configure
this aborts with message:
Number of created screens does not match number of detected devices

4. I am at a loss :confused:. Is there anything else I could reasonably try to fix this problem? :)


5. my environment:
Ubuntu: 12.10
Kernel: Linux version 3.5.0-28-generic
CPU: Intel Core i3-2120 CPU @ 3.30GHz × 4, 64-bit
Graphics:
lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Turks [Radeon HD 6570]
       vendor: Advanced Micro Devices [AMD] nee ATI
       width: 64 bits
       clock: 33MHz

xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 400, current 1400 x 1050, maximum 1400 x 1050
default connected 1400x1050+0+0 0mm x 0mm
   1400x1050       0.0* 
   1280x1024       0.0  
   1280x960        0.0  
   1152x864        0.0  
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
   720x400         0.0

---

### Post by suesswolf on 2013-09-22
I regularly accept the automatic software updates from Ubuntu. At some point it worked again. It seems to me that the problem occured after one of the patches, and went away with another one. It continues to run fine also under Ubuntu 13.04. Thanks to the ones who fixed the problem.

---

