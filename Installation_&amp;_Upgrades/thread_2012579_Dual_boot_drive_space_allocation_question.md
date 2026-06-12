---
title: "Dual boot: drive space allocation question"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2012-06-29
Hey guys, I have a laptop with 160GB drive space and 8GB of memory.
This is a spare HDD that i plan to use for testing.

I plan to install Windows 8 first, then Ubuntu.

My plan is to divide/partition the HDD as:
-Windows 8: 40GB primary partition
-Ubuntu 12.04: 15GB primary partition
-swap: 4GB logical partition (good enough??)
-Home:the rest of the drive (either ext4 or ntfs (don't want to use FAT32). Home partition accessible from both OS.

Does it look ok, any better recommendation for hdd allocation?

..

---

### Post by oldfred on 2012-06-29
A /home has to be Linux formated often ext4 for ownership & permissions which Windows formats do not support. If you want to share data create another partition in NTFS and make it a shared data partition to use by both systems.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

