---
title: "Unable to partition for installation"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by jason58 on 2014-02-07
When I try to partition some open space on my drive in disk utility, I get this error:

> Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=386451636224, size=104857600000, type=
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
found partition type 0xee => protective MBR for GPT
Exiting MS-DOS parser
Entering EFI GPT parser
GPT magic found
partition_entry_lba=2
num_entries=128
size_of_entry=128
Leaving EFI GPT parser
EFI GPT partition table detected
containing partition table scheme = 3
got it
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Warning: Not all of the space available to /dev/sda appears to be used, you can fix the GPT to use all of the space (an extra 4521 blocks) or continue with the current setting? 
got disk
new partition
guid '' is not valid
type '' for GPT appear to be malformed



When I run fdisk -l I get:
> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9eb5c1c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 32.0 GB, 32017047552 bytes
256 heads, 63 sectors/track, 3877 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf9206b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    15633407     7816688    b  W95 FAT32





Please advise!! I'd really like to get this going so I get to work! Thanks!

---

### Post by oldfred on 2014-02-07
Do you have a gpt partitioned drive?
fdisk and old tools do not work on gpt drives.
You can use parted, gparted or gdisk which is the fdisk for gpt drives.

> Error: The backup GPT table is not at the end of the disk, as it should  be.  This might mean that another operating system believes the disk is  smaller.  Fix, by moving the backup to the end (and removing the old  backup)?

If gpt you need to fix this. If not gpt you need to remove all gpt data to make it MBR(msdos).

If booting with UEFI which all new Windows 8 systems have you must have gpt partitioned drive.

sudo parted -l
sudo apt-get install gdisk
sudo gdisk -l /dev/sda

---

### Post by Bashing-om on 2014-02-07
jason58; Hi ! Welcome to the forum.

We all have to keep up with the times and new technologies.
The advisement from "fdisk" says it all.
> 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

So; install the utility "gdisk" to cope with the newer partitioning scheme "GPT";
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gdisk

```
Then to use "gdisk" from terminal:
```

sudo gdisk -l /dev/sda

``` where "sda" is the 1st physical hardrive, to see the second hard drive -> sdb
See:
```

man gdisk

``` after the tool is installed for details.

Ubuntu's partition editor, GParted, can cope with GPT partitioning, but you must be explicit. 

[INDENT]it is ubuntu
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

