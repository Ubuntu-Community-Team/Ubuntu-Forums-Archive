---
title: "Server Upgrade fails due to LVM missalignment"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by Cavaseul on 2013-12-22
I have a small intel atom server running ubuntu server 11.10. Upon installation I allocated the entire disk (2TB) to LVM using the standard partitioning scheme (boot, swap, root, data). So far so good. Unfortunately I can't upgrade to any recent versions because newer versions of Grub don't fit in the disk space that precedes the LVM. This has been documented in long and broad. I have made several attempts to upgrade but each of them failed and leave met with a none working grub although the rest seems to be fine. After reinstalling the original system everything is working again as it was. 

So my question remains: How can I move the entire LVM up a couple of sectors to make more space for grub or how can I upgrade the entire the system without upgrading grub, which is what's causing the problem. 

Anyone? 

Merry Christmas.

---

### Post by Cavaseul on 2014-01-01
The solution is so simple that I am almost shameful of having asked the question in the first place. 
Booted my server using the latest Gparted live cd and shrank the lvm by a couple of MB whilst moving the whole thing towards the end of the disk. Problem solved. Grub2 installs without a glitch. B)

---

