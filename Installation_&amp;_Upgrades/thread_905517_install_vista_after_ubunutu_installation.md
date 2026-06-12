---
title: "install vista after ubunutu installation"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by zixan on 2008-08-30
Hello,

I have Ubuntu 8 running on my laptop.  I want to install Windows Vista, and dual boot my system.

My questions are:

What is the best practice to partition my hard disk.  Currently, I only have Ubuntu running on my 120gb hd, with no secondary paritions.  Should I parition and create space for Vista using Ubuntu-based partitioner, or should I let Vista handle it.

Will installing Vista change grub boot loader configuration, and I won't be able to boot into Ubuntu?

Thanks for the help!  Any other suggestions are more than welcome!

---

### Post by cmat on 2008-08-30
For partitioning, format available space as NTFS. You can make the partiton any size you like but keep in mind Vista is a hog with hard drive space. For partioning Vista`s internal partitioner will not do since it may not recongnise EXT3 or SWAP. You should use gParted LiveCD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) since it can work with more filesystems than Vista`s. 

Vista will overwrite GRUB and you will be unable to boot into Ubuntu. GRUB must be reinstalled at a later time by using the recovery console on the Ubuntu installation disc.

---

### Post by nickgaydos on 2008-08-30
I got my XP disc and deleted the ubuntu partition and installed vista :P

---

