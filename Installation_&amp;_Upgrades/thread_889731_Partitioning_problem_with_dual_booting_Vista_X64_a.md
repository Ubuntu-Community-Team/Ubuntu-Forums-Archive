---
title: "Partitioning problem with dual booting Vista X64 and Ubuntu 8.04 64 Bit"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by evelez on 2008-08-14
:confused:Hello, am trying to dual boot ubuntu 8.04 and Vista 64 bit. I installed vista 64 bit first on to my 250 GB HD. I shrunk the 250 GB HD in vista using vista's partitioning tool. The new partition shows has free space on the vista partitioning tool. I made a 25 GB free space partition to install ubuntu.

Once I boot the live cd and reach the partition tool in ubuntu, it gives me the following options,

1. Guided- resize SCSI1 (0,0,0) Partition #3 (SDA) and use freed space of 80 GB

2. Guided- Use entire disk, which I do not want to do, I want to keep vista.

3. Guided- use the largest continuous free space.

 and manual

when I try option 3, it gives me an error which reads- "free space is too small to be automatically partitioned."

When I go into manual it shows the following partitions,

/dev/sda
free space 0mb
/dev/sda1 fat 32 209mb- 209mb used
/dev/sda2 163831mb unknown
free space 134mb
/dev/sda3 ntfs 85883mb and 0mb used
free space 0mb

I only made one partition in vista, which was 25gb in size of free space out of my 250 GB which leaves vista with the rest. 

My 25GB of free space for ubuntu does not show up on the ubuntu partitioning tool. I tried many ways, shrinking via vista, unshrinking via vista and partitioning the drive via ubuntu, but it still shows the same partitions, i wrote above. I find it very weird.

I hope one of you guys can help me. I searched everywhere and to no avail.

Am not new in the dual booting scene but this here has me stumped. Thanks for any help sent over.

---

### Post by meindian523 on 2008-08-14
Please post ```
sudo fdisk -l
```There is trouble imagining the setup with that description.

---

### Post by evelez on 2008-08-14
thanks,

this is what the command gave me,

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8e36690

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27215   218596344    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by meindian523 on 2008-08-14
You need to make a partition out of your /dev/sda2 which is apparently 163 GB in size,and has no filesystem.Use System>>Administration>>Partition Editor(GNU Parted).That's what sense I can make of this situation.

---

### Post by evelez on 2008-08-14
thanks for the help, i figured out the problem, i had Mac OS X installed on my HP PC and it had left behind the 200mb boot partition on the drive, my whole drive is setup the way it was when i had the OS X installed. Thanks I got it from here. Thanks for the brain opener.:)

---

### Post by evelez on 2008-08-14
I fixed it, I erased my drive via ubuntu, reinstalled vista 64 bit and partitioned the drive via ubuntu, gave ubuntu 30 gigs to play with and now am typing this in ubuntu. Am happy. Great system.:)

---

