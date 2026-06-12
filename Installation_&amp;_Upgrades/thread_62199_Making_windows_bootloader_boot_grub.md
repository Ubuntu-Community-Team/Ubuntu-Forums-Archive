---
title: "Making windows bootloader boot grub"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by Zalbor on 2005-09-03
Supposedly, if I use a command like

sudo dd if=/dev/hdc of=/home/zal/ubuntu.grb bs=512 count=1

and transfer the file I just created to a windows partition, I can alter the boot.ini file in windows and add a line like

c:\ubuntu.grb="Ubuntu"

the windows bootloader would have an extra option through which I can give control to grub and boot linux. I've done this in the past and it worked perfectly, but this time although it does boot grub, it says something like "Error 7" (not sure about the number).

The main difference I can think of is that when it did work, grub, windows and linux were on the same hard disk, but now grub is on a different one. Is there still a way I can make it work?

---

