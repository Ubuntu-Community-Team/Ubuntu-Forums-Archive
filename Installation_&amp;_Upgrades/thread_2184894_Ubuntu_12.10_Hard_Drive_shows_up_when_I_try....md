---
title: "Ubuntu 12.10 Hard Drive shows up when I try..."
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by computergroove on 2013-10-31
When I try to install 12.10 I am unable to see a hard drive and no matter what I have tried Ubuntu crashes at the point of choosing a hard drive. If I select try ubuntu then I can see my hard dive mounted and I can browse it. What can I do?

---

### Post by Bucky Ball on 2013-10-31
Is there a reason you are installing 12.10? It will be out of support shortly (six months). You would be better off with the LTS, 12.04 LTS (supported until April 2017) or a newer release (which have nine months support, not eighteen).

Apart from this, do you actually have free space on the hard drive to install to??? Also, have you got four partitions on there already?

---

### Post by fantab on 2013-10-31
From 'Try Ubuntu' post the output of:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by computergroove on 2013-10-31
sudo fdisk -l:
Dsik /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (maximum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40000000

Divice boot          Start        End       Blocks      Id    System
/dev/sdb1   *           63   488263544  244131741  7  HPFS/NTFS/exFAT

for the sudo parted -l:

Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number    Start      End       Size    Type       File System    Flags
1            32.3kb    250GB    250GB  primary   ntfs              boot

Warning: unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!



I dont want to multiboot or keep anything on the hard drive. I want to erase everything and run Ubuntu exclusively.

---

### Post by fantab on 2013-10-31
Ubuntu/Linux will NOT install to NTFS formatted HDD or its partition. You have to format it with Ext4 or any other Linux filesystem.

** Your HDD ATA ST3250310AS (scsi), is /dev/sdb meaning its the Second Device.

Boot with Ubuntu DVD/USB and "Try Ubuntu without Installing"... Open/Run Gparted.
1. Delete the NTFS partitiion (/dev/sdb1   *           63   488263544  244131741  7  HPFS/NTFS/exFAT) and 'Apply' changes.
2. Create Partitions as follows (suggested):
*30GB Primary Ext4 Ubuntu mountpoint=/
*30GB Primary Ext4 Free (Just in case for the future)
*2-4GB Primary SWAP
*All the remaing GB Primary Ext4 Data No mountpoint. You can also use this with mountpoint=/home. If you use this as /home then 20GB first partition is plenty instead of 30.
3. Install Ubuntu. At the screen which says 'Installation Type' choose 'Something else and guide Ubuntu install to the partitions. All the MOUNTPOINTS should be assigned now.

OR

2. After deleting the Partition /dev/sdb1, leave the space as 'unallocated' and use Ubuntu installer's automated Partition to do the partitioning for you. The guide below should help you:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Since your HDD is the second device See in the BIOS menu and change it to be the first. If not be careful when installing GRUB Boot-loader. By default it will install to /dev/sda which presenty, I think, is your USB or DVD.

---

