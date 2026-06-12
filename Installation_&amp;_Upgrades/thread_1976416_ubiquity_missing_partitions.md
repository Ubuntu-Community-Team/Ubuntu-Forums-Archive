---
title: "ubiquity missing partitions"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by disabled_July202024 on 2012-05-08
i have attached the pics of gparted and ubiquity

i have currently windows xp3 and ubuntu 10.10 installed and i can use them perfectly.Iam trying to do a fresh install to ubuntu 12.o4 from live cd.i can't access my partitions normally but i can mount via mount command in terminal.
thanks

---

### Post by coffeecat on 2012-05-08
The most likely reason for Gparted showing "unallocated" when you have usable partitions is an illegality in the partition table - which is usually easily fixable. Boot into Ubuntu 10.10 and post the output of:

```
sudo fdisk -lu
```

If you highlight the output with the mouse and right-click, you'll be able to copy it for pasting into your post. Please post the output between [noparse]```
 and 
```[/noparse] tags in order to retain formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by disabled_July202024 on 2012-05-08
currently i'm on another machine i will give the output when i access it.
Thanks

---

### Post by disabled_July202024 on 2012-05-09
the output of fdisk -lu is

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f539f53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     4096574     2048256    7  HPFS/NTFS/exFAT
/dev/sda2         4096575    15198273     5550849+   7  HPFS/NTFS/exFAT
/dev/sda3        25192446   312576704   143692129+   f  W95 Ext'd (LBA)
/dev/sda4        86638608   148071104    30716248+   7  HPFS/NTFS/exFAT
/dev/sda5        25192448    46163967    10485760    7  HPFS/NTFS/exFAT
/dev/sda6        46166016    67133439    10483712    7  HPFS/NTFS/exFAT
/dev/sda7        67135488    86638591     9751552   83  Linux
/dev/sda8       148071168   199928924    25928878+   7  HPFS/NTFS/exFAT
/dev/sda9       199928988   251144144    25607578+   7  HPFS/NTFS/exFAT
/dev/sda10      251144208   312576704    30716248+   7  HPFS/NTFS/exFAT

```

---

### Post by coffeecat on 2012-05-09
Yes, you have an illegality in your partition table, and a fairly fundamental one at that. See the figures I've highlighted in red:

> **cchandu2050 said:**
> the output of fdisk -lu is

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f539f53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     4096574     2048256    7  HPFS/NTFS/exFAT
/dev/sda2         4096575    15198273     5550849+   7  HPFS/NTFS/exFAT
/dev/sda3        [COLOR="Red"]25192446[/COLOR]   [COLOR="Red"]312576704[/COLOR]   143692129+   f  W95 Ext'd (LBA)
/dev/sda4        [COLOR="Red"]86638608[/COLOR]   [COLOR="Red"]148071104[/COLOR]    30716248+   7  HPFS/NTFS/exFAT
/dev/sda5        25192448    46163967    10485760    7  HPFS/NTFS/exFAT
/dev/sda6        46166016    67133439    10483712    7  HPFS/NTFS/exFAT
/dev/sda7        67135488    86638591     9751552   83  Linux
/dev/sda8       148071168   199928924    25928878+   7  HPFS/NTFS/exFAT
/dev/sda9       199928988   251144144    25607578+   7  HPFS/NTFS/exFAT
/dev/sda10      251144208   312576704    30716248+   7  HPFS/NTFS/exFAT

```

You have a primary partition sitting inside your extended partition, which is an impossibility. The partition table is saying that sda4 is a primary because it has a partition number between 1 and 4. To be inside an extended partition, a partition must be a logical one and with a number 5 or greater.

This should be easily fixed with fixparts. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

There are Linux and Windows versions available, so you could run it from Windows, Ubuntu 10.10 or even from the Ubuntu live CD. Make sure you backup all important data - you, or rather fixparts, will be editing the partition table and things could go wrong - and save a copy of the partition table as it is now with sfdisk as described there. Also, be sure to download and install fixparts and not gdisk - some people have run gdisk by mistake and dug themselves deeper, hence Rod's warning. 

Out of interest, have you used a 3rd party Windows partitioning tool? This problem has the whiff of such about it. Some of the Windows partitioning tools can be remarkably cavalier with the partition table, as can the Windows installer!

**EDIT**: By the way, fixparts should reassign the partition numbers by renumbering the errant sda4. It might shuffle all the partition numbers from 8 upwards, or it may merely reassign sda4 to sda11 and allow you to have logicals not in numerical order. I don't know which. If it does renumber sda8 up, you need to be aware of this in case you are referencing partitions by device number rather than UUID in /etc/fstab.

---

### Post by disabled_July202024 on 2012-05-09
i did try fix parts but i didn't know exactly what to do.i did backup my partition table

---

### Post by coffeecat on 2012-05-09
> **cchandu2050 said:**
> i did try fix parts but i didn't know exactly what to do.i did backup my partition table

You need to set sda4 as logical. The fixparts commands for this are in the tutorial. But before you do, do you know what is on your current sda4? You have a plethora of NTFS partitions and you need to be sure that your Windows operating system is not on it. Windows can boot only from a primary partition, but your primary sda1 with the boot flag is only 2GB in size which is too small to be a Windows C: partition.

Windows is happy with data partitions being logical, so if sda4 is a data partition, changing its status to logical will be fine. If it is a Windows system partition, then you do have a problem, seeing as it's right in the middle of the extended partition.

---

### Post by disabled_July202024 on 2012-05-09
sda2 is my windows installation and from the tutorial the command to set as logical is l(small l). thanks

---

### Post by disabled_July202024 on 2012-05-09
i have some issues with my sda1 partition so i shrunk it to 2gb.
the only files that reside there are the windows bootloader files

---

