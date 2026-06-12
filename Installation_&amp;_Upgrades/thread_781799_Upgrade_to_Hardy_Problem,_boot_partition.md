---
title: "Upgrade to Hardy Problem, boot partition?"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by sanford55 on 2008-05-04
Hi.  I have two computers dual booting between XP and Gutsy.  I upgraded easily from Gutsy to Hardy on one computer and then ran into something I do not understand when I tried to upgrade the  second -- I am new to Ubuntu so it is lack of knowledge rather than a glitch.  The problem is with a Dell Pent 4 2.80GHz with 760 of Ram and 8.4 GB available space.  When I tried to upgrade, I got an error message:  "Not enough free disk space.  Needs. 21M on disk /boot".  Using the cf command, I discovered that on this computer (but not on the one that upgraded easily) I have a /boot partition with only 11090 available space.  It is /dev/Sda2.  Sda1 has 6314456 available and Sda3 has 8812124 available.  I do not know why I ended with such a boot partition on this computer and not on the other since I originally installed Gutsy on both in the same way.  I do not know anything about this, but I assume that I have to get stuff out of this boot partition.  Unfortunately, I do not know how to work with partitions, how to get into this partitian, or, once in, what to take out.  Or am I totally off track?  Advice is much appreciated!  Thanks in advance. Sanford

---

### Post by fixitdude on 2008-05-04
[http://partedmagic.com](http://partedmagic.com)

Parted Magic is a great FREE program with GUI and a boot CD so you can stretch and resize partitions, even NT partitions!

You may be able to use it to make that boot partition bigger.

---

