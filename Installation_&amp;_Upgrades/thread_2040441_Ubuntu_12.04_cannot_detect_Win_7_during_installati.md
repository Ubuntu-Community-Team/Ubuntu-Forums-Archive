---
title: "Ubuntu 12.04 cannot detect Win 7 during installation"
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by serious7 on 2012-08-11
In the installation type section, I press "something else". It will show the device "/dev/sda" with no other information. Under device for boot loader installation drop down menu, it shows : "/dev/sdb and /dev/sda ATA Hitachi (1 TB)."

I have a 1 TB hard disk with 2 partitions. The other partition has Windows 7. I'm on AHCI mode right now. When I go to the home folder on Ubuntu, I can see a 189 GB Filesystem and a 811 GB file system (my 2 partitions). What's going on?

My ultimate goal is to dual boot both operating systems.

This is my fdisk output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
240 heads, 63 sectors/track, 129201 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a0f3a6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   368640719   184320328+   7  HPFS/NTFS/exFAT
/dev/sda2       368642048  1953534239   792446096    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders, total 8058880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     8058879     4029424    b  W95 FAT32
ubuntu@ubuntu:~$




**EDIT:**

Mod's please delete this. Im just going to wipe out windows 7 and start fresh.

---

