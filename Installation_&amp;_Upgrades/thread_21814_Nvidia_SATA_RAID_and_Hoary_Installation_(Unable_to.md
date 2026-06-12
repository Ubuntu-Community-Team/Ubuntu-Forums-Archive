---
title: "Nvidia SATA RAID and Hoary Installation (Unable to install Grub!!!)"
date: 2005-03-24
forum: Installation &amp; Upgrades
---

### Post by MiddleBrooker on 2005-03-24
Hi,
I'm sorry for the question but I've already browsed this forum to see a solution for my bad problem.

I'm trying to install Ubuntu Hoary on a AMD 64bit system with Nvidia Nforce3 Chipset and Nvidia RAID with two SATA disks in a classical RAID0 setup.
So it's clear that I need a software RAID emulation that I'm trying to make with a manual editing of the partition table during the Hoary installation.
I'm be able to setup all my MD RAID device, but the problem arrive during the Grun installation; infact seem to be impossibile to install Grub on my MD devices  :-k 

I've tried to install it (and also LILO) on /dev/md0 - /dev/md/0 - /dev/sda1 - and the last chance was /dev/fd0 , unfortunally I can't install Grub on the classical floppy disk too :shock:

Please can somebody tell me some resolution for this problem?

Thanks for all the support and sorry for the disturb.

Best Regards,

MiddleBrooker

---

### Post by Synergy on 2006-07-07
The reason for your grub troubles, is because the nvidia raid is a software raid system, meaning it is bios controlled only.  
   The ubuntu installer treats the array as seperate hard drives, because it doesn't have the proper drivers to recognize the raid 0.
   When you installed Grub, you merely installed it to one hard drive, completely ignoring the striped system currently setup.  On the Gentoo live disc it contains dodmraid, which can handle most software raid systems, including the nforce series.
For full instructions, please visit: [http://ubuntuforums.org/showthread.php?t=86219&highlight=raid0](http://ubuntuforums.org/showthread.php?t=86219&highlight=raid0)

Credit goes out to MiddleBrooker, and the great gentoo wiki, where this fix originated.

-Synergy

---

