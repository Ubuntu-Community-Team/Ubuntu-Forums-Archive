---
title: "Wheres is my harddisk?"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by ssstoffer on 2008-03-31
Hey.:)

Okay, I requested a Ubuntu 7.10 live cd. 
I booted from the cd, and started the installation.
Everything goes fine, until the hard disk partition part.
Ubuntu can’t see my hard drive. 
I’ve tried to *make a fat32 partition in windows, open geparted (it can’t either see my hdd), I’ve tried an alternate cd and I even changed the sata port of my hdd. *

WHAT CAN I DO? :confused:

---

### Post by Pumalite on 2008-03-31
Boot your Live CD and from the Terminal, post:
sudo fdisk -lu

---

### Post by CLomax on 2008-03-31
Best not to take any advice from a 'first cup' but here's what I think:

When you make a partition in XP, it should be unallocated. No NTFS, FAT32, or anything.
But like I said, you're better off waiting for someone with more competence with Ubuntu to help, they won't be long ;]
EDIT: Looks like someone beat me to it.

---

