---
title: "GUI isn't installing/loading right"
date: 2006-05-03
forum: Installation &amp; Upgrades
---

### Post by neoaddict on 2006-05-03
I think I got Ubuntu installed correctly (had to delete my previous Ubuntu desktop because the HD ran out of space while compiling the 2.6.16 kernel), but whenever I try to load up the login screen, it only displays it on 1/3 of the monitor with really bad colours.

I've tried sudo dpkg-reconfigure xserver-xorg and disabled and enabled frame buffering multiple times.

Can anyone help me with this?  ](*,)

---

### Post by neoaddict on 2006-05-04
Fixed.

Set video driver to S3, used Medium understanding thing for the monitor setup, 1024x768@75 hertz and 16 bit colour.

---

