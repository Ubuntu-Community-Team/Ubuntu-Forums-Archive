---
title: "gparted Error finding USB"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by WadeH2o on 2010-09-10
I'm trying to 'share' ubuntu with a friend. Using his 1GB USB drive along with the Startup Disk Creator I loaded Ubuntu 10.04 NB. I then wanted to verify the operation by restarting my own computer to boot from usb with no success(several attempts on two machines). **I'd like to format the USB but again no success**.  I've tried both the Startup Disk Creator to erase and GParted to format. I know that I should be able to see the device from the list on the top right of GParted but its not listed. When I launch GParted from Terminal i get the following:
```
wade@Human:~$ sudo gparted
======================
libparted : 2.2
======================
Input/output error during read on /dev/sdb

```
In Startup Disk Creator this /dev/sdb is listed but when I try to erase I get an error in a new window:
```
org.freedesktop.UDisks.Error.Failed: Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0
got it
got disk
Error: Input/output error during read on /dev/sdb
Error: Input/output error during read on /dev/sdb
Error: Input/output error during write on /dev/sdb
ped_disk_commit_to_dev() failed
BLKRRPART ioctl failed for /dev/sdb: Input/output error

```

Does anyone know what may be causing the problem? You help and advice is appreciated.

---

### Post by ajgreeny on 2010-09-10
What is the output of ```
sudo fdisk -l
```with the USB drive attached?

---

### Post by WadeH2o on 2010-09-10
> **ajgreeny said:**
> What is the output of ```
sudo fdisk -l
```with the USB drive attached?

If I'm reading this correctly the USB is not seen...?
```
wade@Human:~$ sudo fdisk -l
[sudo] password for wade: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf098efd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9726     2241067+   5  Extended
/dev/sda5            9448        9726     2241036   82  Linux swap / Solaris

```

---

### Post by efflandt on 2010-09-10
It sounds like you may have accidentally formatted /dev/sdb (entire USB drive) instead of partition /dev/sdb1.  That is an easy mistake to make with Startup Disk Creator (experience) because it sometimes defaults to the entire USB stick instead of the partition on it..

You probably need to use gparted to create an msdos partition table on the USB, and then create and format /dev/sdb1 as vfat (FAT that can handle long file names).

---

### Post by WadeH2o on 2010-09-10
> **efflandt said:**
> It sounds like you may have accidentally formatted /dev/sdb (entire USB drive) instead of partition /dev/sdb1.  That is an easy mistake to make with Startup Disk Creator (experience) because it sometimes defaults to the entire USB stick instead of the partition on it..

You probably need to use gparted to create an msdos partition table on the USB, and then create and format /dev/sdb1 as vfat (FAT that can handle long file names).

That makes sense! And I now realize what you mean by format the entire USB and not just a partition. I'll pay closer attention from this point forward when using Startup Disk Creator.
EDIT:
I'm able to get GParted to see the USB by opening from terminal command: ```
sudo gparted /dev/sdb 
``` Once I'm here it tells me no partition tables are present and to do so I must first choose Device --> Create Partition Table. I get an error says Unrecognized Disk Label... ```
wade@Human:~$ sudo gparted /dev/sdb
======================
libparted : 2.2
======================
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
Input/output error during read on /dev/sdb
Input/output error during read on /dev/sdb
Input/output error during write on /dev/sdb
```

---

### Post by WadeH2o on 2010-09-12
sorry but a bump is necessary... I'm stuck







:popcorn:

---

### Post by WadeH2o on 2010-09-13
It seems what I've done seems pretty rare. I tried using WinVista but the format dialog box won't even show up. At least Ubuntu gives an error. Can I FORCE a  label onto the USB from a Terminal command?

---

### Post by WadeH2o on 2010-09-15
Any ideas how to remove "Write-protection' on a USB?

---

### Post by jeight on 2010-09-15
Like efflandt said you need to use gparted and format using fat32 or vfat. After formatting you should be able to again format to ext3 or ext4.

If the USB is read only then mount the drive as root and then go to proprties and change permissions. That or us a chmod command like 777 on sdb.

---

