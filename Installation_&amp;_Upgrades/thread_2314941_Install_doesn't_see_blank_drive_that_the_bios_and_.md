---
title: "Install doesn't see blank drive that the bios and win 10 does see."
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by Randy_church on 2016-02-24
Wiped a WD Black 1TB drive to install ubuntu studio on and the installer won't see it.  Win 10 sees it.  The bios sees it on boot.  The installer does see usb sticks on the machine and the SSD... .have no idea what the problem is... .Any clue for me?

Randy

---

### Post by Randy_church on 2016-02-27
*** Solved ***

I figured since I was not getting any help on this and not finding any answers any where on the internet I would forgo Ubuntu for Gentoo.  FYI I had previously booted to gparted live and int saw the drive and I formated it to ext3 and made a swap partition and still Ubuntu Studio did not see it.  Booted to a live/install DVD of GenToo and used Kparted to start partitioning and formating the drive again and simply unplugged the machine in the middle.  Booted it to the Ubuntu Studio and what do you know, it saw the drive and I now have it installed.  I did find some info about WD black drives use 4096K sectors and that coupled with the fact that the 64MB cache is more like a little SSD are the cause of the problem.  After that, that article was too deep for me these days.

Randy

---

