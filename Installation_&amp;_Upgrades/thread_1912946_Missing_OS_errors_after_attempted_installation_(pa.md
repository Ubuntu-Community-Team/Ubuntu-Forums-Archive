---
title: "Missing OS errors after attempted installation (partition tables? bootloader?)"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by spacehippy on 2012-01-21
I just attempted to install ubuntu 11.10 and although I did not go through with the installation, afterwards my computer stopped booting the pre-existing Windows 7.  I got "Missing operating system" errors when I tried to boot from my hard drives immediately after that. It is possible that something in either the partition tables or the bootloader got messed up.  I am able to run ubuntu from the CD but only if I have a memory key or external hard drive plugged in.  In the installation software I can see that my two internal hard drives are there, but otherwise I have not figured out how to mount them when I'm running ubuntu from the CD.  

During the installation procedure the software asked to unmount partitions that had been mounted.  I confirmed.  Before then, I could see the windows partitions but afterwards I stopped being able to.  So initially I could see my hard drives from running the ubuntu CD, although the installation software did not automatically give me an option to install on them.  

The result from
```
sudo fdisk -l
```is
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2           98304    31555583    15728640    7  HPFS/NTFS/exFAT
/dev/sda3   *    31555584  1953544191   960994304    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table                      # This looks important!

Disk /dev/sdc: 16.0 GB, 16008609792 bytes                             # Flash drive
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    31266815    15633392    c  W95 FAT32 (LBA)
boot-repair didn't solve the problem either but this is the output: [http://paste.ubuntu.com/812068/](http://paste.ubuntu.com/812068/)

Most immediately I would just like to go back to being able to use Windows 7.  My ultimate goal is to do an ubuntu/Windows 7 dual boot.

A part of this question is: how do I mount these partitions? 

Many thanks!

---

### Post by darkod on 2012-01-21
You tried to install but didn't go trough with the installation? You mean you aborted it?

If you only want to see how it works you use the Try Ubuntu option and that makes no changes to your system. But if you start and abort the install (or it stops from any reason), usually you can expect problems.

Anyway, you seem to have errors in both disks:

On /dev/sda somehow the partition sda3 is way out of the disk size, compare the total number of sectors on the disk, and the End of sda3.
On /dev/sdb it has some invalid signature in the MBR.

fixparts should be able to help with this. Run it from live mode.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

PS. It is very weird that during installation it would ask you to unmount partitions. Did you have the windows partitions mounted in live mode and you started the install?

---

### Post by spacehippy on 2012-01-21
I started the installation software and got up to the part involving choosing where to install it.  I did not actually go through with the installation.  One problem may have been that I started with my external hard drive turned on...the only place it would let me install without going into partitions was on that drive.  

I think the windows partitions did end up being mounted in live mode, but I'm not completely sure.  

I will try fixparts in live mode and post about how it goes.  Thank you for the reply!  

-Nick

---

### Post by spacehippy on 2012-01-22
I have not gotten it to work.  When I do:
```
sudo fixparts /dev/sdb
```
I get:
> FixParts 0.8.1

Loading MBR data from /dev/sdb

Unable to read MBR data from '/dev/sdb'! Exiting!
Are there ways to better diagnose what's happening on /dev/sdb?  

Am attempting to use testdisk...

---

### Post by darkod on 2012-01-22
Did fixparts manage to fix /dev/sda?

Yes, testdisk might be able to sort out the problem on /dev/sdb, depending what it is.

---

