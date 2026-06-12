---
title: "Trying to install ubuntu 13.10 on new alienware"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by rektiphyr on 2014-04-27
Hi all,

I'm having a hard time getting ubuntu intalled on my new laptop. I'm able to boot into live mode from a usb stick, but when I run the installer I don't see any partitions on the disk. The goal is to install ubuntu alongside my windows 7 partition. I've been stuck on this for a while now, any help would be great. I've attached some screenshots and logs that may give more info.

Cheers.

[IMG]http://i58.tinypic.com/33dbbtl.png[/IMG]
[IMG]http://i57.tinypic.com/1fe5p3.jpg[/IMG]

fdisk -l
```


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5543cc3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    21467135    10692608    7  HPFS/NTFS/exFAT
/dev/sda3        21467136  1625833471   802183168    7  HPFS/NTFS/exFAT
/dev/sda4      1625833472  1953523711   163845120    5  Extended
/dev/sda5      1625835520  1953523711   163844096   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5543c936

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    22081535    11039744    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 7998 MB, 7998537728 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15622144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000768e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15620279     7810109    c  W95 FAT32 (LBA)

```

parted -l
```

Model: ATA WDC WD10JPVX-75J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16        diag
 2      41.9MB  11.0GB  10.9GB  primary   ntfs         boot
 3      11.0GB  832GB   821GB   primary   ntfs
 4      832GB   1000GB  168GB   extended
 5      832GB   1000GB  168GB   logical   ext4


Model: ATA LITEONIT DMT-80M (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  11.3GB  11.3GB  primary  ntfs


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdc: 7999MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  7998MB  7998MB  primary  fat32        boot, lba



```

---

### Post by rektiphyr on 2014-04-27
Some further reading has led me to believe this may be happening because I resized the drive using the windows disk management tool, as this can mess up GPT vs MBR? II'ma bit out of my depth here. Can anyone provide more info? Bump.

---

### Post by rektiphyr on 2014-04-28
Update: I have tried 14.04 instead -- same thing. No one has any ideas? Bump.

---

### Post by rektiphyr on 2014-04-29
Well a few days of puttering about with google and I managed to fix it myself. Turns out there was stray GPT data lingering about. I was able to remove it with gdisk and installed 14.04 with no problems. Cheers.

---

