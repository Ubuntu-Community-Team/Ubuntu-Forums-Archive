---
title: "How to fix refresh rate on a second display (ATI restricted driver)"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by elfuego on 2013-10-28
Hi everyone,

I have a desktop computer with Ubuntu 12.04 and ATI/AMD Radeon 7790 in CF connected to two displays:

1. CRT1 Sun microsystems 21" with desired resolution 1600x1200@85Hz
2. DFP5 Acer S221HQL with desired resolution 1920x1080@60Hz

After I have installed restricted drivers I played around and set up the desktop to use both displays. But unfortunatelly, the refresh rate of the CRT display is locked to 60Hz. I have tried setting up a new mode with:

cvt 1600 1200 85

then tried adding the mode to xrandr via:

xrandr --newmode "1600x1200_85.00"  235.00  1600 1728 1896 2192  1200 1203 1207 1262 -hsync +vsync

then

xrandr --addmode CRT1 1600x1200_85.00

This allows me to select 85 Hz refresh rate in Catalyst display manager, but the mode fails to start with "Invalid Settings. The current settings cannot be applied. Possible issues may include: -Display cannot be enabled. -Setting cannot be applied due to insufficient video memory". 

Xrandr --output CRT1 --mode 1600x1200_85.00 fails with

xrandr: Configure crtc 0 failed

Can anyone suggest how to fix the refresh rate or explain what did I do wrong or why doesnt this work? Thanks in advance! :KS

---

### Post by elfuego on 2013-11-01
Nevermind; due to unusually high amount of difficulties of installing ubuntu on this machine starting from grub messing things up with UEFI to ndiswrapper failing to build ([official bug]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1245657")) to no GUI at all after installation of 13.10 (cannot even run in fail safe mode since neither keyboard nor mouse is detected), I have decided to place ubuntu in a sandbox.

I should have done it from the start. In virtual box ubuntu 13.10 runs surprisingly good! Almost at native speed, no drivers issue, no fuss, no bugs, its portable and even runs with full 3D compiz support! I love it :KS I usually ran Linux as host system with windows as guest, but I guess times have changed :P

---

