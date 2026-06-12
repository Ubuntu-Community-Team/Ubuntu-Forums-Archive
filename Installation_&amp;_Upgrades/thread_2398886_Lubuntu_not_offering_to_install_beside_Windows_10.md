---
title: "Lubuntu not offering to install beside Windows 10?"
date: 2018-08-18
forum: Installation &amp; Upgrades
---

### Post by Tom_Miller on 2018-08-18
I have successfully used this flashdrive to install Lubuntu on a computer and it offered to install "beside" Windows 10.  It was successful and it is running well.

I am trying to install in on another Win10 with much more limited un-allocated space.  The installer is taking me to a partition creation step rather than an "auto install next to windows" step.  

I am assuming there is not enough space.  How big does the unallocated space need to be?

Tom
Newbee

---

### Post by TheFu on 2018-08-18
I think 5G is the official min, but 25G is really the minimal for a full OS install for most people, assuming you place /home/ onto a different partition.
[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight_GUI_alternative_.28Xubuntu_and_Lubuntu.29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight_GUI_alternative_.28Xubuntu_and_Lubuntu.29) says 5G, but without room to store documents locally.
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall) has more.

My main desktop fits in 17G and it has been upgraded since 2010 for every LTS, so you can keep it tight, with some effort.

If you boot from an Ubuntu/Lubuntu flash drive, "Try Lubuntu", then open a terminal.  Please run **sudo fdisk -l** & **lsblk** and post the output from both commands using the Adv Reply (#) "code tags", so it is lined up correctly.  There are some partitions that Windows makes which aren't something Linux can handle.  If that machine uses one of those more advanced partition types, manual partition is the best solution, I think.

---

### Post by Tom_Miller on 2018-08-18
```
lubuntu@lubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 967.6 MiB, 1014571008 bytes, 1981584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9e5de62e

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          208896 866856793 866647898 413.3G  7 HPFS/NTFS/exFAT
/dev/sda3       954494976 956291071   1796096   877M 27 Hidden NTFS WinRE




Disk /dev/sdb: 7.5 GiB, 8004829184 bytes, 15634432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x02e5f4f7

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15634431 15632384  7.5G  c W95 FAT32 (LBA)


Disk /dev/zram0: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram2: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram3: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram4: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram5: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram6: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram7: 495.7 MiB, 519786496 bytes, 126901 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
lubuntu@lubuntu:~$ 

```

----------------------------------------------
```
lubuntu@lubuntu:~$ sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 967.6M  1 loop /rofs
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   100M  0 part 
&#9500;&#9472;sda2   8:2    0 413.3G  0 part 
&#9492;&#9472;sda3   8:3    0   877M  0 part 
sdb      8:16   1   7.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.5G  0 part /cdrom
sr0     11:0    1  1024M  0 rom  
zram0  252:0    0 495.7M  0 disk [SWAP]
zram1  252:1    0 495.7M  0 disk [SWAP]
zram2  252:2    0 495.7M  0 disk [SWAP]
zram3  252:3    0 495.7M  0 disk [SWAP]
zram4  252:4    0 495.7M  0 disk [SWAP]
zram5  252:5    0 495.7M  0 disk [SWAP]
zram6  252:6    0 495.7M  0 disk [SWAP]
zram7  252:7    0 495.7M  0 disk [SWAP]
lubuntu@lubuntu:~$ 

```

Here is the tests you asked to be run.
If I have to run the Part-ED I will need a specific manual script :(

Tom

---

### Post by TheFu on 2018-08-18
Thanks for the data. Perfectly executed and posted.

Looks like this is a BIOS boot machine with MBR partitioning. That means only 4 primary partitions are available for use, but usually, Ubuntu needs 2 partitions free to install - one for the OS and one for swap.  MBR only allows 4 primary partitions, period.

Hopefully, someone else will see the data and be able to provide better options.

With GPT partitions, the practical limit of partitions isn't something we ever need worry (over 100 allowed) about and most Win10 systems use UEFI and GPT. That is probably why the other system allowed the installation.

There are things that can be done, but it is like surgery. How badly do you want this? Is reinstalling Windows on the table?  There are other, less risky options, if the machine has plenty of RAM and a recent middle-performance CPU.

---

