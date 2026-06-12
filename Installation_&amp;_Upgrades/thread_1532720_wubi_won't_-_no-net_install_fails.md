---
title: "wubi won't - no-net install fails"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by LiLoather on 2010-07-16
I'm trying to install via wubi with no internet connection.  As the guide says for this situation I have  wubi.exe and the desktop.iso in the same folder but when I try to run wubi it just tells me that it can't download the metalink and thus the ISO - which it can't as there's no internet connection!

Duh!

---

### Post by bcbc on 2010-07-17
try running wubi.exe with the --skipmd5check parameter. Otherwise it tries to verify that you have a valid .iso

You should make sure you have a valid .iso yourself in this case.

---

### Post by LiLoather on 2010-07-17
Thanx, but problem solved.

I was using the ubuntu-10.04-desktop-i386.iso but asking wubi to install kubuntu.  I thought kubuntu was a flavour of Ubuntu installable from the distro but not according to wubi.  Wubi installed ubuntu fine from the .iso - 

well, kind'a.  The wubi installation does not pick up my ICH5 on-board SATA RAID, nor my MegaRAID PCI card so most of my hdd space is invisible to it.

---

