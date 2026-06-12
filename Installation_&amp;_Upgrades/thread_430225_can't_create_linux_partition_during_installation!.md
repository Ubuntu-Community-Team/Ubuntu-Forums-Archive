---
title: "can't create linux partition during installation!"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by rygar on 2007-05-01
i'm trying to install ubuntu on my pc, which already has an XP partition and and a Vista partition.
the hard drive also has a 25 gig unallocated space which i want to use to create an ubuntu partition.

if i boot from the live cd, the installer gives me two options--manual, and use entire disk.  there is no option to use largest free space.  both options want to format my entire disk.

opening gparted tells me my entire disk is unallocated.

sudo fdisk -l tells me (accurately) that i have /dev/sda1 for Vista and /dev/sda2 for XP

how can i create and format a linux partition to install ubuntu without screwing up my windows partitions??

---

### Post by zvacet on 2007-05-02
Choose manual option and you will see your existing partitions and free space.You will,of course,install Ubuntu on the free space.Partition your Ubuntu like this
1. root =10GB                                                mountpoint /
2.home = rest of free pace exept                  mountpoint /home
3.swap =2xRAM

Ubuntu use ext3 format.

---

### Post by rygar on 2007-05-04
manual installation didn't show anything different.

it turns out, my XP and Vista partitions overlapped (how?  who knows...)

supposedly partition table doctor is supposed to fix this, but it didn't, and i ended up formatting.

---

### Post by Sef on 2007-05-04
> it turns out, my XP and Vista partitions overlapped (how? who knows...)

supposedly partition table doctor is supposed to fix this, but it didn't, and i ended up formatting.

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

