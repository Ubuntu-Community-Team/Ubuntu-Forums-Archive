---
title: "where is XP?"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by downset13 on 2008-07-01
I have two hard drives configured as so:

SDA1: 
Windows XP Partition 80 gig
Recovery Partition 10gig
SDB:
Empty NTFS Partition 90 gig

When I throw in Ubuntu, I want to be able to take part of the Windows XP partition and use it for Ubuntu, and then keep the empty NTFS Partition for storage.  The problem is, I can never get ubuntu to recognize XP in the grub loader!  Even when I get to the transfer account part of the install, it doesn't show any operating systems.
Any help would be great.

---

### Post by upchucky on 2008-07-01
assuming u have successfully got ubuntu working

type  sudo fdisk -l

in the terminal it will show you all your drive partitions and what is where.

if win xp is there then u need to tell grub where to find it, search this forum for grub editing.

if win xp is over written by error, and you still want xp on system then install xp first then ubuntu.

if after the win install, you can't boot anything then you need supergrub to fix the windows bootloader, as your original grub has written over the windows bootloader.

if you are using a live install cd/dvd for ubuntu then the partimage program on it will show you the partitions.

if you manipulate partitions do each operation one at a time, as you can confuse the partitioner when trying to do multiple operations all at once.

if both op systems are there then editing grub or using supergrub will get them both working

---

