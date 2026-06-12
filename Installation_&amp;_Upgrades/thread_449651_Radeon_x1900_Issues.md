---
title: "Radeon x1900 Issues"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by captainquack on 2007-05-20
I just tried installing Feisty on an Alienware Area51 with a Radeon x1900 graphics card. Unfortunately, when using the live cd, X would crash. I used the alternate CD, with hopes of being able to configure X myself after the installation. Unfortunately, it still won't work. I have tried:

sudo dpkg-reconfigure xserver-xorg

using VGA and VESA, but neither of them will work. I also tried using the proprietary ati drivers, but when I run the installer, it says:

Detected version of X does not havce a matching x720 directory

and then lists all of the ways I can override the detected version. If I try 'startx', it gives me:

a bunch of gunk and says:

Fatal Server Error:
Caught signal 11. Server ab orting

XIO: fatal IO error 104 (Connection reset by peer) on X sesrver ":0.0"
        after 0 requests (0 known processed) with 0 events remaining.

Does anyone have any idea what's happening or how to fix it?

Thanks,
Captainquack

---

