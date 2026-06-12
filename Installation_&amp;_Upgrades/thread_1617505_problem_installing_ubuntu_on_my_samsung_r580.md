---
title: "problem installing ubuntu on my samsung r580"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by Bk2035 on 2010-11-09
I am trying to install ubuntu 10.10 on my samsung r580 but it doesn't recognise my windows partitions and i want to maintain them.

When I use ```
sudo fdisk -lu
``` these are the results:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x483a482d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   812921759   406357456    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x016ed2dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7935999     3963968    b  W95 FAT32

```Please help me. I am new to Ubuntu world.

---

### Post by dino99 on 2010-11-09
here is the problem and the solution:

****
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
*****

so /dev/sda might be ext3 or ext4 format, not gpt

by default dont create partitions for linux with winblows tools :(

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Bk2035 on 2010-11-09
thanks but that will erase my windows partitions because parted magic doesn't recognize my windows partitions either.

so i will be creating those 3 partitions on top of the others.

it has to be another solution.

---

### Post by srs5694 on 2010-11-09
The problem is that the disk has both Master Boot Record (MBR) and GUID Partition Table (GPT) data on it. Chances are the disk was previously used in a Mac, or you have previously experimented with GPT, but you've reverted to MBR partitioning, but without properly wiping out the GPT data. The leftover GPT data is now confusing the installer (and other libparted-based tools will be equally confused).

See [this post of mine](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34) in another thread for a solution to the problem.

---

