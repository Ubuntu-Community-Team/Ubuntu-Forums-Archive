---
title: "Booting HDD images with syslinux"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by GhostC10 on 2011-07-15
Basically, my objective is to build a flash drive that can boot both in qemu for windows (via a batch script) and also boot straight from the bios when plugged in. I'm already halfway there (I got the batch script working)
 
The batch script boot process goes like this:
 
(run script) -> (use EXTLINUX install in image) -> (profit)
 
However, heavyweight distros are agonizingly slow in QEMU unless your hardware is very modern (we're using Fedora 13, we'll be moving to some version of RHEL next semester). Also, they're far too large to load into ramdisks while still having the packages required by the professors. I tried paring it down to fit, and because I had to use memdisk, the changes I made weren't written back to the image.
 
Attempts to set the image as root (LINUX vmlinuz, ROOT=fedora.img) simply resulted in the kernel failing to mount a root filesystem. It should be noted that bootstrap was successful when I booted the partition on my HDD the image was built from.
 
Oops, I think this is in the wrong section. Should it be in Other OSes?
So, I suppose what I'm asking is, can syslinux (or any bootloader) boot an image as if it were a true HDD, without loading the entire image into ramdisk? And how much more information would someone need to help me? I've been at this for over 3 weeks now... If Windows were capable of using a block device, this wouldn't be an issue...

---

