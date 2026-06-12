---
title: "Jaunty: Video driver for S3 Unichrome IGP ?"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by UranUtan on 2010-03-26
Hi,

Using Ubuntu 9.10 x64, fresh install. The graphic is onboard, VIA S3 Unichrome from the chipset P4M800 Pro.

I have tried to search on this forum and on the Internet but the related posts were too old and don't apply to Karmic. Which strangely enough doesn't have the xorg.conf file.

The OpenChrome videao driver is installed (sudo apt-get install xserver-xorg-video-openchrome). But the screen resolution is still 8000x600.

Would appreciate any advice.

---

### Post by UranUtan on 2010-03-26
Hi,

It has been fixed. But I don't remember what I did. Have tried a bunch of things found on the net but didn't see any changes. After a reboot, the display can now display all the resolutions. May be the sudo apt-get ... I made above followed by a reboot is all that needed to be done.

2D only, 3D doesn't work (setting Visual Effects to mode normal failed). Fortunately, all I need is to set the screen resolution.

---

