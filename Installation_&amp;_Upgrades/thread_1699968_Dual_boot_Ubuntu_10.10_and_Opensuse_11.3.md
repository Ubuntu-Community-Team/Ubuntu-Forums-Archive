---
title: "Dual boot Ubuntu 10.10 and Opensuse 11.3?"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by ae75rhenium on 2011-03-04
Im kind of new to dual booting and was curious if anyone could point me in the right direction. how to partition my hard drive within ubuntu 10.10 64bit for Opensuse 11.3? I have 350gb HD and kinda wanted to dual boot with opensuse. How do I do this without wiping out Ubuntu as my main OS?

---

### Post by sikander3786 on 2011-03-04
We need to know your existing partition setup i.e, how many partitions, how many primary, what sizes etc and these commands will tell us every thing we need.

[s]Applications > Accessories > Terminal:[/s]

From Lubuntu's Terminal:

```
sudo fdisk -lu
sudo parted -l
```

Please post the complete outputs.

---

### Post by ae75rhenium on 2011-03-04
Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d8d74

---

### Post by sikander3786 on 2011-03-04
> **ae75rhenium said:**
> Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d8d74
We need to see the _complete_ outputs for both those commands. While posting the output, you can click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by ae75rhenium on 2011-03-04
Model: ATA ST3360320AS (scsi)
Disk /dev/sda: 360GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

---

### Post by sikander3786 on 2011-03-04
This is how the complete output looks on my PC.

```
:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091d02

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546   83  Linux
/dev/sda2        51199155    57335984     3068415   82  Linux swap / Solaris
/dev/sda3        57335985   976768064   459716040   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92b2e51d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   83  Linux
```

```
:~$ sudo parted -l
Model: ATA STM3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  26.2GB  26.2GB  primary  ext4            boot
 2      26.2GB  29.4GB  3142MB  primary  linux-swap(v1)
 3      29.4GB  500GB   471GB   primary  ext4


Model: ATA ST31000528AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ext4
```

Can you find all this stuff in your outputs?

---

### Post by ae75rhenium on 2011-03-04
```
rhenium@rhenium-N68SA-M2S:~$ sudo fdisk -lu
[sudo] password for rhenium: 

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d8d74

   Device Boot      Start         End      Blocks   Id  System
rhenium@rhenium-N68SA-M2S:~$ sudo parted -l
Model: ATA ST3360320AS (scsi)
Disk /dev/sda: 360GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.
Error: /dev/fd0: unrecognised disk label 


```This is what I got when I typed the sudo commands in the terminal.

---

### Post by sikander3786 on 2011-03-05
That output tells us that there are no known partitions on your HDD. Really?

Can you please post a screen-shot of GParted from System > Administration sub-menu.

---

### Post by ae75rhenium on 2011-03-05
I this is what I got when I opened Gparted.

---

### Post by ae75rhenium on 2011-03-08
No one can help me with this?

---

### Post by Dimison on 2011-03-11
Did you try on making new partitions to sda1?
Right click -> New partition
and then choose your space for another OS

---

### Post by Quackers on 2011-03-11
Boot from the live cd and select "try ubuntu" then open gparted.
Right-click on the swap partition and select "swapoff".
Right-click on the /dev/sda1 partition (ext4) and select "resize/move"
Select the amount of shrinkage you want and then to apply the change click on the green tick in the toolbar.
When that's run gparted will show /dev/sda1 in its new size, then some unallocated space, then /dev/sda2 and /dev/sda5.
Right-click on /dev/sda2, the extended partition, and select "resize/move". With this one you want to move the partition to the left - so that no unallocated space remains in front of it (swallowing all the unallocated space you just made).
Apply the change.
Then you can install your new operating system in that resultin "free space" inside the extended partition. You won't need another swap space that way, you can use the one you've already got.

---

