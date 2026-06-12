---
title: "Is there a way to have both Windows xp and Ubuntu ?"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by pinkvector on 2007-07-04
Kinda like the MAC can run windows also... on dual boot or w/e you call it.. (im new to this stuff)

I didnt want to get rid of Windows xp

---

### Post by mattyrigby00 on 2007-07-04
use gparted live cd to shrink the xp partition ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)), then restart your computer so xp can scan the drive (dont worry its doing something right for once), then start up off the ubuntu live cd and in the installation process create a 1-2gb swap partiton and the rest an ext3 partion with / as the mount point, it should detect windows xp and give you the option on startup. you might wanna edit grub.conf when done to make the timeout more than 10 seconds too.

---

