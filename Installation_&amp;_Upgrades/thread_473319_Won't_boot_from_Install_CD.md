---
title: "Won't boot from Install CD"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by 213374U on 2007-06-13
I recently seriously jacked up my Ubuntu while trying to upgrade to compiz.git and deleted the driver for my graphics card. I am just now able to get it to boot up in GNOME Failsafe and partially use my system. So I'm trying to do a fresh install of Feisty but I can't get my system to boot from the CD. Question is, is there another method of installation from CD once already in the terminal or GUI?

---

### Post by Trueno22 on 2007-06-13
from failsafe terminal type sudo aptitude install ubuntu-deesktop

or you can just reconfigure xorg by :

sudo dpkg-reconfigure xserver-xorg choose the vesa driver or nv driver if you have a nvidia card

---

### Post by 213374U on 2007-06-13
scratch that, tried booting from my second CD-ROM drive and it worked. Thanks for the help though.

---

