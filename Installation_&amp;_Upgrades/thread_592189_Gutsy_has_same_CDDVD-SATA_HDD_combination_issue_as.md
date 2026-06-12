---
title: "Gutsy has same CD/DVD-SATA HDD combination issue as feisty"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by templer666 on 2007-10-26
Hi there,
I just installed Gutsy in the hope that I can finally use GRUB with all the fancy graphics.
My system is a Win XP/Kubuntu.
The problem is, after installing Kubuntu from the CD, the CD/DVD drive isn't working anymore if GRUB is booting from SATA disks. This applies even for Windows which is a serious GRUB bug now existing for roughly 6 months without a fix.

The workaround is to use LILO.

Everything you need to know can be read here:
[http://ubuntuforums.org/showthread.php?t=449357]("http://ubuntuforums.org/showthread.php?t=449357")
The thread in the above link describes the problem and how to get rid of it using LILO.

If anyone in charge of the bootloader stuff in ubuntu reads this, here's what I think:
If it's still true, that GRUB isn't maintained anymore (not as a package in ubuntu but rather as software at all; see above link), I demand it from being removed as default boot manager!

Hope this is of any help for anyone.
Rob

---

