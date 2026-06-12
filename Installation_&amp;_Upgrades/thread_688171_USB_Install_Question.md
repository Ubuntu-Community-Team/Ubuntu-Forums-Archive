---
title: "USB Install Question"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by davo_ on 2008-02-05
Hi, 

Did some searching around and didn't find anything quite to suit the process here.  I know it's possible to install, and boot linux from a USB thumb drive if you already have Linux installed.  Well, I currently don't have any media handy to burn Ubuntu to a disk and install it there, but I do have a 4gb USB drive.  Is it possible to install ubuntu FROM that without having Linux already installed on a Machine?

Thanks

Dave

---

### Post by lswest on 2008-02-05
well, i'm not sure if it's quite the same for Ubuntu as it is for Backtrack, but i have Backtrack 2.0 on my USB stick.  Basically i downloaded the ISO, used winrar to copy the folders and files over to the USB stick, went into the /boot/ folder, and then ran the boot.bin file there to make the USB bootable.  Might do the trick for you.

*EDIT* just had a look, there is no Boot folder, so you'd have to make your USB bootable using a partitioning program (like PartitionMagic or so) but other than that it should work fine.

---

### Post by davo_ on 2008-02-05
Aye, I should be able to just select my USB drive during the boot process to load from that, shouldn't I without having to edit it's settings or anything shouldn't I?

---

### Post by lswest on 2008-02-05
well, the default configuration is that USB sticks are unbootable, meaning you have to add a boot flag to it before trying to boot from it, but that's as hard as plugging it in, opening a partitioning program and either adding a boot flag or choosing the option "make bootable" or, worst comes to worst, i can upload the boot.bin file i have for you.

---

