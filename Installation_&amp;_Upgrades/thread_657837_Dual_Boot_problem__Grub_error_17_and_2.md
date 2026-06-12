---
title: "Dual Boot problem  Grub error 17 and 2"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by ve7zbm on 2008-01-04
Install of Ubuntu version 606 lts goes normal until after you are asked to reboot and remove the install dvd. Instead of Grub coming up and giving you the choice to boot linux or Windows XP the process halts and an error message 17 comes up. The first time it was error 2 or 20 or 22 I am not sure which. I have 2 125 gig drives, one for XP and the other I intended to load linux on. I hve tried reinstalling but each time new disk partions are created messing up the drive and I still get the error 17!! 

Any suggestions?
ve7zbm

---

### Post by Partyboi2 on 2008-01-04
Try reinstalling grub and see if that works.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If that does not work then have a look at this for some other options
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Circuit99 on 2008-01-04
**The information I give must be read through, then you must understand your problem to figure out solution. This is guide to possible answers. To safe guard your data backup before decide what to do.** 

The problem for you is a possible that you have faulty hard drive use a live cd distribution so that you can mount partitions something like "KNOPPIX". 

Use distribution that you can mount hard drive from a live cd distribition. If you can not mount the linux partition then suspect fault in hardware. Identify hard drives and then get test software for it, if possible. 

If hard drives ok then need to remove ext3 partitions then reinstall lnux.
Use something like "Parted Magic" which has good version of gparted to identify partitions and clean out linux ones which are ext3 . 

Use the link below to gparted screenshot
[http://partedmagic.com/screenshots.html](http://partedmagic.com/screenshots.html)
In the pic you see ntfs and fat32 partitions these are windows do not delete or you will lose Windows Xp.

Another option is to upgrade grub. 

You have two hard drives, I don't know if they are IDE or SATA or one of each, and bios setup, which one you boot into? What is you hardware setup?

:popcorn:

---

### Post by Circuit99 on 2008-01-04
Add one more item,

To fix windows boot use fixmbr which will repair/replace grub to fix windows booting.


:shock:

---

