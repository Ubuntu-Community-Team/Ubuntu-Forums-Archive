---
title: "MBR shown as unallocated"
date: 2017-05-28
forum: Installation &amp; Upgrades
---

### Post by djordjelukic on 2017-05-28
I am trying to install Ubuntu along side my Windows 10 OS but my MBR partition table (not GPT) is not showing.
I have disabled quick boot and hibernation (powercfg.exe /hibernate off) under windows os.


```
[liveuser@localhost-live ~]$ sudo gdisk -l /dev/sda 


GPT fdisk (gdisk) version 1.0.1


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5A4A40FF-8079-40FA-8DF9-E64D9078727F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 4973 sectors (2.4 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   0700  Microsoft basic data
   2         1026048       234438655   111.3 GiB   0700  Microsoft basic data

```


```
[liveuser@localhost-live ~]$ sudo fdisk -l
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xef29344b


Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1          2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2       1026048 234438655 233412608 111.3G  7 HPFS/NTFS/exFAT

```


```
[liveuser@localhost-live ~]$ sudo parted -l
Error: /dev/sda: unrecognised disk label
Model: ATA KINGSTON SHSS37A (scsi)                                        
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

```


[IMG]http://i.imgur.com/MiY54br.png[/IMG]


[IMG]http://i.imgur.com/ATcBSEz.png[/IMG]

---

### Post by yancek on 2017-05-28
I'm not sure why GParted shows the disk as unallocated but the way it is now, there is no way you will be able to install Ubuntu.  You have two windows partition which take up about 99% of the drive leaving about 1GB on which to install Ubuntu.  That won't work, you should have 15-20GB.  To install Ubuntu, use the windows Disk Management tool to shrink the larger partition to leave unallocated space for Ubuntu and since you have an MBR install, make sure you boot and install Ubuntu that way and not UEFI.

---

### Post by oldfred on 2017-05-28
Is BIOS/UEFI set for AHCI? Not RAID nor IDE?
Was drive every RAID or Intel SRT which looks like RAID.
Are partitions in Windows shown as basic not dynamic as only basic works with Linux.

What brand/model system?

Fdisk says it is DOS, but parted says it is unknown??

---

### Post by djordjelukic on 2017-05-30
> **oldfred said:**
> Is BIOS/UEFI set for AHCI? Not RAID nor IDE?
Was drive every RAID or Intel SRT which looks like RAID.
Are partitions in Windows shown as basic not dynamic as only basic works with Linux.

What brand/model system?

Fdisk says it is DOS, but parted says it is unknown??

It is a dell lap-top with UEFI but it is set to legacy boot with AHCI never used RAID or SRT.
tried also UEFI boot with same results.
Windows boots normally and partitions are basic not dynamic.

I need to make Gparted working so i can shrink my partition it has plenty of free space. i never trusted windows tools for partitioning.

P.S even as partitions are showing in fdisk i can not mount them in console im geting an error that dev/sda2 doesnt exist even if fdisk is seeing both partitions(sda1 is 500mb deafult partition made by windows instaler) so disk was formated by windows installer.

---

### Post by oldfred on 2017-05-30
Are you sure Windows fast start up or hibernation is off?

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

