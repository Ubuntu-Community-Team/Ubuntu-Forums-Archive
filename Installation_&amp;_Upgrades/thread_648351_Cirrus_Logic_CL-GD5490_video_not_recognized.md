---
title: "Cirrus Logic CL-GD5490 video not recognized"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by simonmason on 2007-12-23
I keep getting the low res boot up.  I go into screens and drivers and pick the correct driver for my video card, log off, and I am back at low res again.  Any help is appreciated.  Thanks.

---

### Post by markharding557 on 2007-12-26
go into /etc/X11/xorg.conf and see if your card and resolutions are listed
basicaly there will be a line of various resolutions begining with mode,it will use the first one in the line as default.
so you need change the first figures to the resolution you need to be default.
make sure that all the resolutions you are likley to use are there

---

