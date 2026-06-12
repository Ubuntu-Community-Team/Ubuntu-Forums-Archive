---
title: "&quot;Can't have a partition outside the disk!&quot; error"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by swmmng on 2013-11-03
I'm trying to install Xubuntu 13.04 on my Asus 1215n eeePC. I have a Windows installation and a Debian installation. I want to format the Debian partition and install Xubuntu there. However, when I tell the installer I want to use that partition as an ext4 partition and mount it as /, I get an endless procession of the error from the title; I have to force the computer to shut down. What's the problem?

Here's the current partitioning:
/dev/sda1    ntfs    Windows 7
/dev/sda2    
/dev/sda3    swap
/dev/sda4    ext4   Debian

---

### Post by fantab on 2013-11-03
Boot from Xubuntu DVD/USB and "Try without installing',  run the terminal and post the output of:
```
 sudo fdisk -l
sudo parted -l
```

---

### Post by swmmng on 2013-11-03
fdisk:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29133921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   241174527   120586240    7  HPFS/NTFS/exFAT
/dev/sda3       241369088   256993279     7812096   82  Linux swap / Solaris
/dev/sda4       256993280   488396799   115701760   83  Linux

Disk /dev/sdb: 15.8 GB, 15823011840 bytes
255 heads, 63 sectors/track, 1923 cylinders, total 30904320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192    30904319    15448064    c  W95 FAT32 (LBA)

```

parted:
```

Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  123GB  123GB   primary  ntfs
 3      124GB   132GB  8000MB  primary  linux-swap(v1)
 4      132GB   250GB  118GB   primary  ext4


Model: Generic USB SD Reader (scsi)
Disk /dev/sdb: 15.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  15.8GB  15.8GB  primary  fat32        boot, lba

```

It appears that partition 2 did get successfully erased like I wanted, and 4 got formatted even though the process couldn't continue.

---

### Post by fantab on 2013-11-03
It would be a good idea to delete those two linux partitions and recreate them using Gparted.

A suggestion: Instead of having one big 118GB partition for '/' it would be better if have one small for '/' and one for /home. Like this:
18GB for Xubuntu '/' [20-25GB for '/' would be plenty]
100GB for /home.

---

### Post by swmmng on 2013-11-03
Same error.

---

### Post by fantab on 2013-11-03
I had edited the earlier post.. anyways. Delete those two Linux partitions and try again.

Good Luck.

---

### Post by swmmng on 2013-11-03
Deleting them and redoing the partition table did the trick! Thanks!

---

### Post by fantab on 2013-11-03
That's good. Mark the thread as 'Solved' using Thread tools.

---

