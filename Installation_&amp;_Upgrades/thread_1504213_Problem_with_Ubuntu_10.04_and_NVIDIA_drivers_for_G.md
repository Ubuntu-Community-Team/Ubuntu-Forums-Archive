---
title: "Problem with Ubuntu 10.04 and NVIDIA drivers for GeForce 7600 GS"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Plankman on 2010-06-07
Hi there

I hope someone can help me out. I've finally decided to ditch Windows and go full on with Ubuntu. My problem is that when I install any of the nvidia-glx-* drivers, when I reboot it shows the Ubuntu 1004 splash screen for a few seconds and then my screen just goes to sleep. I had it working fine in wubi, then it started, and it seems to be doing it now with a full install. If I try and start with failsafe x settings, I get a message that X can't find a screen. I really don't know what to do. I've even tried installing the driver from the NVIDIA site and the same thing happens

---

### Post by Plankman on 2010-06-10
It seems the problem may lie with my monitor. I've tried hooking it up to a 17" LCD monitor and it worked fine and I could install the nvidia drivers with no problems. When I hooked up my monitor after that it would only run in 640x480 mode and i couldn't change it. I tried modifying the hor/vert settings in /etc/X11/xorg.conf, but then it tries to load a resolution that is way too high and then it just hangs there. Hopefully someone can give me some clues about what to look at.

---

### Post by drs305 on 2010-06-10
I have a GS7600 and am running 10.04. I am using nouveau without any issues. When going to System, Administration, Hardware Drivers no nvidia drivers are activated and I have no /etc/X11/xorg.conf. If you haven't tried the Lucid defaults, it may be an option that works for you.

---

