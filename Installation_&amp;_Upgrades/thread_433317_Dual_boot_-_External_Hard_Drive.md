---
title: "Dual boot - External Hard Drive"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by StormJosh on 2007-05-04
Hey everyone. I've tried searching for some solutions but they dont seem to really match my personal ones. My situation is that if I want to use linux (which I do), I would need to put it on an external hard drive, and have Windows XP on the internal one.

Could someone direct me to a guide on how to accomplish this?

---

### Post by confused57 on 2007-05-04
> **StormJosh said:**
> Hey everyone. I've tried searching for some solutions but they dont seem to really match my personal ones. My situation is that if I want to use linux (which I do), I would need to put it on an external hard drive, and have Windows XP on the internal one.

Could someone direct me to a guide on how to accomplish this?

Maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=80811&page=49&highlight=success+external](http://ubuntuforums.org/showthread.php?t=80811&page=49&highlight=success+external)

You might want to read the original post in this thread, also.

The major mistake people often make when installing Linux to an external hard drive is to install grub to the internal drive's mbr, which is the default in an Ubuntu install...when you do this, you're not able to boot your computer without the external drive connected.

What you can try, is to select your USB hard drive in bios to boot before your internal hard drive...then boot up the live cd, install Ubuntu & select to install grub to the external hd, by typing in "/dev/sda"(or whatever the Ubuntu install recognizes as your external drive).

Another possibility is to set your bios boot order internal drive, then external drive...but make sure to install grub to "/dev/sda"(your external drive?)...then you could use something like the Super Grub Disk to boot your external drive(if you're not able to boot first to a USB drive):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
in fact, I would recommend you burn a copy of the SGD(only a few Mb download), before you attempt to install Ubuntu to your external drive.

---

