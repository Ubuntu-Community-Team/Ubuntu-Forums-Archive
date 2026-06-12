---
title: "Partitioning no and where's LVM?"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Chuckels550 on 2007-04-27
I am trying to install Ubuntu 7.04 and configure it for MythTV like I had for Ubuntu 6.10.  It's a fresh install.  However, I cannot find LVM as a choice in the live CD install partition tool.  So I tried setting up the partitions on a 250GB ATA100 Seagate hard drive as primary partitions as follows:

hda1 20 GB mounted at / with EXT3 filesystem
hda2 5 GB swap 
hda3  rest mounted at /var/lib with XFS filesystem

The partition tool won't allow me to set up the third partition as /var/lib - it says that the beginning cannot be before the end.  What is happening?

---

### Post by Geshtar on 2007-04-28
I've been getting the same sort of error in kubuntu 7.04  install CD.  I can setup a swap partition, and a boot partition both as primaries, but then any more parititions I try to make fail, whether they are primary or logical, with that same "Error:  the beginning cannot be before the end"  OR "Error: the end can't be before the start" (something close to that).  It makes absolutely no sense at all.  I've done prior installations of 5.10 and 6.04 and never had problems with the partitioning tool.  Any thoughts would be greatly appreciated as my install is totally blocked by this issue.


/dev/sda
     /dev/sda1   ntfs    60GB <- this is my windows parition    primary
     /dev/sda2   swap  2GB                                                      primary
     /dev/sda3   ext3   250 MB   /boot                                     primary
free space remaining ~325GB

---

