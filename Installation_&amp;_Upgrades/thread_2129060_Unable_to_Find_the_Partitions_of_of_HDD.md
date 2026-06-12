---
title: "Unable to Find the Partitions of of HDD"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by Hyao on 2013-03-25
Hi there,

I am a novice of Linux and trying to install ubuntu 12.10 (i386) on my laptop after installing Windows 8 (32-bit). I have shrinked 20G from the last partition of my HDD in windows 8. This new partition have no name and has not been formatted. I try to install ubuntu via Live-USB, however, I cannot find the 20G free space. And even worse, the partitions in windows (NTFS) are not displayed, only with the hole disk displayed.

I have noticed that the partitions' type are dynamic for the disk. Should that be a problem? Need I convert it to basic? Can I process the conversion without losing data on the disk?

Or, are there any other problems?

Thank you in advance!

Hyao

---

### Post by darkod on 2013-03-25
Yes, dynamic disk is a problem for linux because that's Microsoft format. If you have installed win8 yourself, it also matters whether you installed in uefi mode, or legacy (bios) mode. The dual boot is easier in legacy mode, but most new machines with preinstalled windows come with uefi. If you install it yourself, you can choose how by booting the dvd in legacy or uefi mode.

You should be able to convert dynamic disk to basic without data loss using EaseUS Partition Wizard, but it's better to have a backup anyway. And the less partitions you have, the better for the process to work. I think it should work fine with up to three partitions, not sure with 4. With 5 or more I don't think you can convert it easily.

If you don't mind reinstalling win8 that might be a better way, especially if you installed it in uefi mode. In that case I would reinstall it in legacy mode making sure the disk is basic and it has msdos partition table on it, not gpt.

---

### Post by oldfred on 2013-03-25
Some of the partition tools now are not including the conversion of dynamic in the free version. But you may be able to find older copies in other software download sites.

Linux seems to be starting to recognize dynamic, before it just did not work. Now it throws errors with grub2 2.00. See bug report.

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

