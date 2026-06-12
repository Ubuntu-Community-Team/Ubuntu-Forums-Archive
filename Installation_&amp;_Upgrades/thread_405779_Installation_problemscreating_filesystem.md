---
title: "Installation problems/creating filesystem"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by fredfrinton on 2007-04-10
Help! Upon requesting an install, it seems to break down after 5%, citing that it failed to create a file system, i haven't used partitioning and just looked to wipe the hard disk, i'm certain it's not the cd because i've tried two different versions of Ubuntu and the same problem occurs on both occasion, there is currently no operating system in the computer as the last one broke down!

---

### Post by gingin on 2007-04-10
During instalation from live cd you must partition you hard drive.
 There is no way around. It should be 3 portitions.
1. root
2.home
3.swap file

---

### Post by fredfrinton on 2007-04-10
thanks a lot for your help, i attempted to partition it in that format but still the same problem reccured. I think the problem is with the hard disk, as it recognizes it as 'unknown,' the computer also said that a major failure of the hard disk may happen, will i need to do some sort of reformatting before it will install properly?

---

### Post by fredfrinton on 2007-04-10
The partitions were
Root                       54 Gb              Partition 1 Disc IDE/ATA 1 (Primary) (hda1)
home                     1Kb               Partition 2 Disc IDE/ATA 1 (Primary) (hda2)
swap                      1Gb              Partition 5 Disc IDE/ATA 1 (Logical) (hda5)

The problem seems to be with the root/54 gb

---

### Post by az on 2007-04-10
> **gingin said:**
> During instalation from live cd you must partition you hard drive.
 There is no way around. It should be 3 portitions.
1. root
2.home
3.swap file

I reccomend the automagic partitionning.  I do not suggest you make a seperate home partition.  Just take the default options which does the partitioning for you and only creates a / and a swap.  You have less of a chance of running out of space and the installation is less complicated that way.


> **fredfrinton said:**
> The partitions were
Root                       54 Gb              Partition 1 Disc IDE/ATA 1 (Primary) (hda1)
home                     1Kb               Partition 2 Disc IDE/ATA 1 (Primary) (hda2)
swap                      1Gb              Partition 5 Disc IDE/ATA 1 (Logical) (hda5)

The problem seems to be with the root/54 gb


Look for bad blocks on your drive.  (Open a terminal and run the following)

sudo badblocks /dev/hda1

If there is only an isolated cluster of faulty blocks, you can always create a different partition there and not use it.

---

### Post by ssawatzky on 2007-07-08
This is what helped for me:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259/+viewstatus)

---

