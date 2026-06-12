---
title: "Ubuntu 11.10/Windows 7 Seperate drives, 3rd drive mount issue?"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by FireDart on 2012-02-12
Hello,
I am a on and off Ubuntu user here and need some advice/guidance. I have finally decided I want to use Ubuntu for almost everything, however I am still a major PC gamer so I decided to dual boot with Windows 7 (like I have done in the past).

Since I last did this I built a new desktop and have a SSD 120GB hardrive for Windows 7 (and programs, have only 50GB left) and a 1 TB hardrive for all my files (music, videos, games, web development, etc...).

So I decided to buy another 120GB SDD just for Ubuntu, no partitioning, and all my data is on my 1TB drive. However since I have installed Ubuntu I am unable to access the drive as it is telling me to mount the drive because it can't access it.

This issue is only on Ubuntu.

So my question is, will mounting the drive wipe the drive? I have about 400GB of data on it so losing it is not an option, I can back it up on 2 other drives just in case but would rather not as it would take a while.

Any advice would be great.

Message:
> Unable to mount Media
Error mounting: mount exited with exit code 12: Failed to read last sector (1953517567): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
    or it was not setup correctly (e.g. by not using mdadm --buid ...),
    or wrong device is tried to be mounted
    or the partition table is corrupt (partition is smaller than NTSF),
    or the NTSF boot sector is corrupt (NTSF size is not valid).
Failed to mount '/dev/sbd2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTSF.
Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by darkod on 2012-02-12
No, mounting doesn't touch the data. In linux mounting is necessary to access the disk, without it being mounted it doesn't know where to locate it.

But that message might mean there is some corruption in the partition table, or similar.

Post the results of:
sudo fdisk -l (small L)

It might show something for a start.

---

### Post by FireDart on 2012-02-12
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc36f0dd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   234438655   117115904    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49af9b83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953523119   976761528+  42  SFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e5fc5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   167491583    83744768   83  Linux
/dev/sdc2       167493630   234440703    33473537    5  Extended
/dev/sdc5       200968192   234440703    16736256   82  Linux swap / Solaris
/dev/sdc6       167493632   200968191    16737280   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   625137344   312568641    c  W95 FAT32 (LBA)

Disk /dev/mapper/cryptswap1: 17.1 GB, 17138974720 bytes
255 heads, 63 sectors/track, 2083 cylinders, total 33474560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb3b0cfe

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

That's everything, the 320GB drive is my external drive, just ignore it, it works.

Thank you for the quick replay.

---

### Post by darkod on 2012-02-12
If you look at the part about /dev/sdb, the 1TB disk, the single partition on it, /dev/sdb1 is type SFS. Notice how /dev/sda has NTFS partitions, not SFS.

SFS means the disk is dynamic in windows, not basic. Windows Disk Management will show it too.

SFS is filesystem of Microsoft and that's why it gives an error when trying to mount it. Even though your partition on the dynamic disk is NTFS, it's not exactly the same as ntfs on a basic disk.

Standard MS documentation says changing from dynamic to basic can't be done without data loss, but people here have reported doing it with Partition Wizard (I think, not sure).

But since any such operation would involve making a backup first, I would recommend this:
1. Copy all of that data to external/internal disks, if you can.
2. Delete the partition from windows, and change the disk to Basic.
3. Create new ntfs partition (or more of them if you want).
4. Put the data back.

Ubuntu will have no problems mounting it as basic disk.

---

### Post by FireDart on 2012-02-12
Alright, will need to devote some time to this. Thank you for your help.

---

### Post by oldfred on 2012-02-14
Some more info on converting.

Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)


As with any partition change, good backups are required.

---

### Post by FireDart on 2012-02-20
Alright, sorry for the late response. I got everything working.
Just backed-up all my files and formatted the drive to NTFS.

Then moved everything back. Worked like a charm!

Thanks guys!

---

