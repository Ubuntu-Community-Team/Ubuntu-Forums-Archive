---
title: "change primary Linux partitions into logical"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by kemeng on 2012-10-17
Dear All,

I need a little help:

I would like to merge my Ubuntu primary drives into a logical drive . Of course:) I dont want to lose any of my data. (I have no any optical or another external drive to backup just an USB with Ubuntu LIVE).

At this moment my HD looks like this (everything is primary drive):
sda1 ext4 / (root)
sda2 ext4 /home
sda3 linux/swap
sda4 NTFS /Windows8
and I got unallocated place as well

So how can I put those Ubuntu drives (sda1-2-3) under one logical drive without any data losing?
Is it possible? 

Thanks for your help in advance!

---

### Post by oldfred on 2012-10-17
Welcome to the forums.

Moved to your own thread.

Even though question seems same, old thread was over a year old. And some tools have changed.

Also is drive MBR not gpt as that makes a big difference? All partitions in gpt are primary.

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sda > parts.txt


To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Be sure to have current copy of Ubuntu liveCD as you may have to reinstall grub2 or update fstab. And know how to add Boot-Repair as an easy way to fix grub if necessary.  UUID should not change but every place that you use the old way of device like /dev/sda1 will have to be changed as sda1 will be the primary extended and then logical partitions start at sda5.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

