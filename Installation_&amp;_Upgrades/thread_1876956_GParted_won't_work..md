---
title: "GParted won't work."
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by jasoncruz98 on 2011-11-07
I want to dual-boot Windows 7 and Ubuntu 11.10 on my hard drive

Right now I have 4 partitions on my hard drive, 

/dev/sda1, (ntfs) which has the SYSTEM label.
/dev/sda2, (ntfs) which contains Windows 7.
/dev/sda3, (ntfs) which has the RECOVERY label.
/dev/sda4, (fat32) which has the HP_TOOLS label.

I want to install ubuntu on the unallocated space (which is 482.22 GB and unformatted), create a linux-swap  partition and a storage partition for both my Windows and Ubuntu files.

But everytime I try and create a new partition, GParted says "It is not possible to create more than 4 primary partitions". I can't even format the unallocated space. 

What am I supposed to do?

---

### Post by coffeecat on 2011-11-07
You have four primary partitions, which is the maximum allowed in the mbr partition table, which is what you have. The only way round this is to delete one of the primary partitions and then create an extended partition in the unallocated space in which you can create as many logical partitions as you need for Ubuntu. With an HP machine you have to delete either the recovery partition or the hp_tools partition. There are pros and cons for each. Here's a post I made some time ago with some more information:

[http://ubuntuforums.org/showpost.php?p=11270314&postcount=2](http://ubuntuforums.org/showpost.php?p=11270314&postcount=2)

Follow the two links to my earlier posts. There is information in those posts relevant only to the threads they were in, but that should give you enough information for how you might wish to proceed.

Post back if you need some more help.

---

### Post by Elfy on 2011-11-07
Thread closed. Please do not post duplicates, it dilutes community effort.

---

