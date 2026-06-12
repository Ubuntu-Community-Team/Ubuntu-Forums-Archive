---
title: "Extremely small font when used on HDTV but not monitor"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by rothgar on 2007-09-29
I am using mythbuntu with a backend of ubuntu 7.10 beta 1.  I have a Nvidia 6200 video card using Nvidia drivers (not sure which ones but they auto installed from the restricted drivers manager).

When mythtv starts everything looks fine but when I go into any settings the font is extremely small (unreadable).  When I set the resolution in the xorg.conf file to 800x600 the font looks fine but that is not the point.  I have tried adding the DisplaySize option under monitor in xorg.conf and I tried a few different values but I still cannot read the fonts (325 182, and actual size of tv in mm 952 535). I also tried calculating my own DPI values using Nvidia's formula [found here](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.09/README/appendix-e.html) (I got 34x34) but that still didn't work.

I need to know how I can make the fonts bigger without making the resolution bigger. Thanks in advance.

---

### Post by rothgar on 2007-09-30
I wanna bump this because I need to find a fix for this.

---

### Post by rothgar on 2007-09-30
I think I figured this one out.  It seems that the Nvidia driver was completely ignoring my DPI settings because I declared it to use TVStandard HD720p option and under the screen I set the mode to be 1280x768 (not 720p).  Because it couldn't load that it ignored everything.  Once I fixed that I was able to set the DPI settings to 227 127 and it works great.

---

