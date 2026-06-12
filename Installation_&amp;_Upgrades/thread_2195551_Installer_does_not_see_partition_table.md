---
title: "Installer does not see partition table?"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by osbornealex32 on 2013-12-24
Hey everyone, pretty new to Ubuntu / Linux in general. I'm trying to install Ubuntu 12.04 off my USB stick onto my laptop to dual boot against Windows 7. I've scoured the forum and the internet in general to solve this, but can't figure it out for the life of me.

When I initiate the installer, I am never prompted for the "Installation type". I am instead directly taken to a partition table, in theory to select where I would like to put the OS. However, there is no partition table! Which seems weird because I can see everything under GParted.

Below is some terminal stuff that a lot of other posts request.

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  19.6GB  19.6GB  primary  ntfs         boot
 3      19.6GB  500GB   480GB   primary  ntfs


Model: ATA SAMSUNG SSD PM83 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary


Model: Generic Flash Disk (scsi)
Disk /dev/sdc: 1049MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  1049MB  1049MB  primary  fat16        boot

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8c51f1cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    38350847    19134464    7  HPFS/NTFS/exFAT
/dev/sda3        38350848   976762879   469206016    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c51f1e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16775167     8386560   84  OS/2 hidden C: drive

Disk /dev/sdc: 1048 MB, 1048576000 bytes
33 heads, 63 sectors/track, 985 cylinders, total 2048000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4dffa55b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     2047999     1023984    6  FAT16


```

I can provide more details for things I have attempted if you guys would like, but perhaps this is enough for now. Thank you very much in advance for your assistance!

---

### Post by oldfred on 2013-12-24
Is this an Ultrabook with the 32GB a small SSD for caching? Or is that just another flash drive?

The SSD cache is often Intel SRT which uses RAID and then the installer cannot correctly see drive. 
Other issues may be NTFS is hibernated or needs chkdsk which it needs after any resize. Always use Windows to resize & reboot to let it auto run chkdsk.
Also drive was originally gpt and you used Windows to convert to MBR as that does not totally remove old gpt backup partition table.
Also some BIOS settings can make a difference.

---

### Post by fantab on 2013-12-24
You have to make space for Ubuntu/Linux on your HDD. There are two ways to go about it:
1. SHRINK your 480Gb partition to make space for Ubuntu. You can leave the created space as 'Unallocated Space', and let the Ubuntu installer take care of the further setup when you choose 'Install Alongside Windows'. 
It will create two partitions from the given 'unallocated space', one for '/' and one SWAP. 
2. SHRINK your 480Gb partition to make 'Unallocated Space' you need for Ubuntu. Boot with Ubuntu Live DVD/USB and open Gparted. Proceed to make your own partitions and when installing Ubuntu you HAVE to choose 'Something Else' option to guide your Install the desired partition. Remember: 'msdos' partition table has ONLY FOUR PRIMARY partitions limit. To bypass this limitation you have make an EXTENDED partition from the 'Unallocated Space' and make LOGICAL Partitions within it.

If you take charge of the installation manually then it is advised that you create a separate DATA or '/home' partition for your data.
20Gb LOGICAL Ext4 '/' [for Ubuntu System files]
2-4Gb LOGICAL LinuxSWAP
All the remaining GB LOGICAL Ext4 '/home' [for your personal DATA].

Also make sure your Windows7 is NOT hibernating.
Also make sure Intel SRT is switched off in BIOS/UEFI.
Also disable 'Fastboot' if you have it, in BIOS.

Shrink Win7 Partition: [http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

---

