---
title: "New install-Feisty and ATI X700 - Problems"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by btrotter on 2007-07-02
I found this thread:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

It runs through getting an ATI Radeon X700 video card going with Ubuntu 7.04.
This does in fact get Ubuntu going with what appears to be new drivers, BUT...it seems to have lowered the clock speed of my CPU down to 1Mhz :)

If I try to run it with the ATI drivers, it is like there is something seriously wrong with the CPU as it takes forever to do anything. Bootup takes a long time. Screens take a long time to draw, menus are very laggy,  just everything seems to be running at 1/4 the clock speed. The resolution will then allow me to select the higher res's (1280x1024 and up), but the refresh rate is still at 60hz.

If I revery back to the default xorg.conf file, everything clears up. I am just limited to 1024x768 and 60hz refresh rate.

Has anyone else seen this? Any good suggestions on making it work?

Thank you,
Brian

---

