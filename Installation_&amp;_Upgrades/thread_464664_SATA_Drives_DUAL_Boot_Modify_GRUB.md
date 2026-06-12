---
title: "SATA Drives/ DUAL Boot/ Modify GRUB"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by Guns90 on 2007-06-04
Good evening everyone.  I've tried finding the answers to my questions, but at this point I'm just getting more confused.  I've recently built my first 64 bit machine for my kids.  They won't make the switch to Linux, so I've decided to dual boot; Windows XP on the hda1 and Ubuntu AMD64 on hdb1.  Here is what I need help with:

1.  This is the first time I've used SATA drives.  They are not set up in any kind of RAID Array.  Through searches in the forum, I have found how to do an install and set GRUB with IDE Drives and one IDE Drive and one SATA drive; however, I can't find help on installing with two SATA drives (with or without an array).  I would like to know if I need to do anything 'special' concerning the use of two SATA Drives?

2.  Once I install Ubuntu on hdb1, I would like for the machine to boot up to Windows XP on hda1 by default.  Is that simply a mod I need to make to the /boot/grub/menu.lst?

Gary

---

### Post by confused57 on 2007-06-04
> **Guns90 said:**
> Good evening everyone.  I've tried finding the answers to my questions, but at this point I'm just getting more confused.  I've recently built my first 64 bit machine for my kids.  They won't make the switch to Linux, so I've decided to dual boot; Windows XP on the hda1 and Ubuntu AMD64 on hdb1.  Here is what I need help with:

1.  This is the first time I've used SATA drives.  They are not set up in any kind of RAID Array.  Through searches in the forum, I have found how to do an install and set GRUB with IDE Drives and one IDE Drive and one SATA drive; however, I can't find help on installing with two SATA drives (with or without an array).  I would like to know if I need to do anything 'special' concerning the use of two SATA Drives?

2.  Once I install Ubuntu on hdb1, I would like for the machine to boot up to Windows XP on hda1 by default.  Is that simply a mod I need to make to the /boot/grub/menu.lst?

Gary

You might find something useful in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

What I think would work is to set your sdb drive in bios to boot before your sda Window's drive, before you boot up the live cd to install Ubuntu...Grub "should" recognize your Ubuntu sdb drive as (hd0), and add an entry to boot Windows on sda(hd1).

---

