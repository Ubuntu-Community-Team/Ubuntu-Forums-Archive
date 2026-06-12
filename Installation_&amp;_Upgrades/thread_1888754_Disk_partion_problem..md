---
title: "Disk partion problem."
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by musabhai6012 on 2011-11-30
I am trying to install Ubuntu 11.10 on my HP DV6-6017TX laptop. I already have windows 7 installed on it. when i am getting the disk partition screen, it shows that my complete 500GB HDD is free space as a single partition (sda). Please help me how to solve the problem.

---

### Post by darkod on 2011-11-30
sda is not a partition, it's a disk device. Partition would have a number which shows the partition number, like sda1, sda2, sda5, etc.

Boot windows and open Disk Management and take a look what it says for your disk.
First thing to check is that you already don't have 4 primary partitions.
The second is whether the disk is dynamic, or basic.

---

### Post by musabhai6012 on 2011-11-30
> 
sda is not a partition, it's a disk device. Partition would have a number which shows the partition number, like sda1, sda2, sda5, etc.

Boot windows and open Disk Management and take a look what it says for your disk.
First thing to check is that you already don't have 4 primary partitions.
The second is whether the disk is dynamic, or basic.


I know that sda is not a partition, its the disk.
I have 3 primary partition (BASIC) and one extended partition( it has got 4 more basic partitions).

---

### Post by Mark Phelps on 2011-12-01
My guess would be, that with that many partitions, the installer is having problems figuring out where to do the installation.

What you will probably have to do is shrink the partitions inside the Extended partition manually, leaving some room for Ubuntu.

Then, when you run the installer, you will need to do Manual Partitioning and select the new unallocated space.

Also, BEFORE you do this, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You will need this later if something goes wrong during the Ubuntu install and Win7 won't boot anymore.

---

