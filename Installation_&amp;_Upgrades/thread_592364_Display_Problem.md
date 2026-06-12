---
title: "Display Problem"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by bobf3986 on 2007-10-26
I have an HP Pavilion DV6000 with an nvidia Geforce 6 video card. When I run the live dvd I can select the 800 x 600 x 32 by pressing F4 and ubuntu works just fine. However when I installed ubuntu onto my hard drive that option went away and I can't get ubuntu to work. Also I downloaded the newest release of ubuntu 7.10 and none of the video options work so I must continue to use the beta version. Any suggestions?

---

### Post by nineowls on 2007-10-26
can you boot into recovery mode?
if so post the result of following?

lspci -n | grep 0300

(just copied from "Post the way you got the Nvidia driver to work")

---

### Post by Fire_Chief on 2007-10-26
Which video driver are you using? If you only get resolution options for 800x600 and lower, then it sounds like you have the VESA driver selected for the display.

From the command line try running
```
sudo dpkg-reconfigure xserver-xorg
```
When it prompts for the driver to use, select the **nv** driver and proceed through the rest of the wizard. Also, you can choose the available resolutions in the wizard (later step). Ubuntu will choose the highest usable resolution by default when starting X. This should at least get you a decent sized desktop that works.
Later, if you choose, you can download and install the Nvidia binary driver from the Nvidia website. I've had much better luck with it than with the driver listed in Synaptic. YMMV

---

### Post by bobf3986 on 2007-10-26
Result of lspci -n | grep 0300 is   00:05.0 0300: 10de:0244 (rev a2) I forgot to mention this is a laptop if it makes a diffrence.

---

### Post by bobf3986 on 2007-10-26
Thanks Fire_Chief, I am still trying but nothing yet.

---

