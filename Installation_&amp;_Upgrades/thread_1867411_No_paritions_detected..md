---
title: "No paritions detected."
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by eranga1988 on 2011-10-22
I tried to install Ubuntu 11.10 using bootable USB flash drive. But when i was directed to disk management, none of partitions were shown. Only the main hard disk is shown. I got about 8 partitions and I have already installed Windows 7 as well as Backtrack 5R1.
How can I overcome this problem. I not a Linux Pro.

---

### Post by Hakunka-Matata on 2011-10-22
Please post output of code
```
sudo fdisk -l && sudo sfdisk -luM
```

---

### Post by eranga1988 on 2011-10-22
> **Hakunka-Matata said:**
> Please post output of code
```
sudo fdisk -l && sudo sfdisk -luM
```
```
ubuntu@ubuntu:~$ sudo fdisk -l && sudo sfdisk -luM

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62926604    31463271    7  HPFS/NTFS/exFAT
/dev/sda2        62926672   312580095   124826712    5  Extended
/dev/sda3       270100845   291081734    10490445   83  Linux
/dev/sda5        62926674   100245599    18659463    7  HPFS/NTFS/exFAT
/dev/sda6       100245669   135974159    17864245+   7  HPFS/NTFS/exFAT
/dev/sda7       135974224   270100844    67063310+   7  HPFS/NTFS/exFAT
/dev/sda8       310626304   312580095      976896   82  Linux swap / Solaris
/dev/sda9       291082240   310614015     9765888   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15646719     7822336    b  W95 FAT32

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     0+ 30725- 30726-  31463271    7  HPFS/NTFS/exFAT
/dev/sda2     30725+ 152626  121902- 124826712    5  Extended
        start: (c,h,s) expected (1023,254,63) found (1023,1,5)
        end: (c,h,s) expected (1023,254,63) found (1023,53,52)
/dev/sda3     131885+ 142129- 10245-  10490445   83  Linux
        start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4         0      -      0          0    0  Empty
/dev/sda5     30725+ 48948- 18223-  18659463    7  HPFS/NTFS/exFAT
        start: (c,h,s) expected (1023,254,63) found (1023,1,7)
/dev/sda6     48948+ 66393- 17446-  17864245+   7  HPFS/NTFS/exFAT
        start: (c,h,s) expected (1023,254,63) found (1023,1,7)
/dev/sda7     66393+ 131885- 65492-  67063310+   7  HPFS/NTFS/exFAT
        start: (c,h,s) expected (1023,254,63) found (1023,1,2)
/dev/sda8     151673  152626    954     976896   82  Linux swap / Solaris
/dev/sda9     142130  151666   9537    9765888   83  Linux

Disk /dev/sdb: 1021 cylinders, 247 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 1021/247/62).
For this listing I'll assume that geometry.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdb1   *     1   7639   7639    7822336    b  W95 FAT32
        end: (c,h,s) expected (973,245,40) found (972,254,63)
/dev/sdb2         0      -      0          0    0  Empty
/dev/sdb3         0      -      0          0    0  Empty
/dev/sdb4         0      -      0          0    0  Empty
ubuntu@ubuntu:~$ 

```

---

### Post by Hakunka-Matata on 2011-10-22
There appears to be something wrong with the partition table.  Look at sda3, it is a primary partition (sda3) but it starts and ends inside the Extended partition sda2.

---

### Post by eranga1988 on 2011-10-23
> **Hakunka-Matata said:**
> There appears to be something wrong with the partition table.  Look at sda3, it is a primary partition (sda3) but it starts and ends inside the Extended partition sda2.
Thanx mate. I created a new partitions for the ubuntu and made it as primary as I believed it may be good for installing a operating system. I dont know whether it is sda3.
I will try to install with making it back to logical.

---

### Post by Hakunka-Matata on 2011-10-23
And what does the disk partitioning look like now?  Post the output of 'sudo fdisk -l' again, so we can see what you created, and if there is a partition or unallocated space available for a new OS? 

Ubuntu can be installed into either a Logical, or Primary partition.  A primary partition inside an Extended partition is not legal, undefined.

---

### Post by eranga1988 on 2011-10-24
> **Hakunka-Matata said:**
> And what does the disk partitioning look like now?  Post the output of 'sudo fdisk -l' again, so we can see what you created, and if there is a partition or unallocated space available for a new OS? 

Ubuntu can be installed into either a Logical, or Primary partition.  A primary partition inside an Extended partition is not legal, undefined.
I deleted both ext4 partitions and the swap area using Acronis Disk director. And I again created the partitions as logical partitions. Now the problem is solved. Thank you!!!

---

### Post by eranga1988 on 2011-10-24
```
senzeh@Senzeh-Vostro1510:~$ sudo fdisk -l
[sudo] password for senzeh: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62926604    31463271    7  HPFS/NTFS/exFAT
/dev/sda2        62926672   312576704   124825016+   5  Extended
/dev/sda5        62926674   100245599    18659463    7  HPFS/NTFS/exFAT
/dev/sda6       100245669   135974159    17864245+   7  HPFS/NTFS/exFAT
/dev/sda7       135974224   270100844    67063310+   7  HPFS/NTFS/exFAT
/dev/sda8       270100908   289507364     9703228+  83  Linux
/dev/sda9       289507428   310488254    10490413+  83  Linux
/dev/sda10      310488318   312576704     1044193+  82  Linux swap / Solaris
senzeh@Senzeh-Vostro1510:~$ 


```

---

### Post by Hakunka-Matata on 2011-10-24
Hey, that's great news, nice way to start the day.  Glad you got it going.

---

