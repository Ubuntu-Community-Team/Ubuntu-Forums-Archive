---
title: "New RAID 1 install problems"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by DigitalFirefly on 2012-02-09
I'm setting up a new PC and trying to install Ubuntu 11 on it. 

I've got 2 1TB drives and I'd like to set it up in RAID 1.

I manually set up each drive with the following partitions
100MB boot partition
32GB swap partition
~960GB root partition

I go to configure software RAID and follow the prompts.

When going to "finish partitioning and write changes to the disk" I get the error: 

"No Root File System is Defined"

Any suggestions?  Does anyone have a link to a good guide for setting up RAID 1 on Ubuntu 11?  I'm having difficulty finding one that works. :confused:

---

### Post by darkod on 2012-02-10
After you create the raid devices, you still have to set up the partitions as usual. For example, for the root partition it would be:

1. Go into Software RAID and configure a raid1 device from the two 960GB partitions you prepared.
2. After that in the list of partitions, a 960GB RAID1 device will show up. Select the Free space of this device and create primary ext4 partition on it, mount point /.

Do the above for every raid device.

The message is clear, you are trying to proceed without telling it what to use as root partition.

I could send you one link later, don't have it at hand right now.

---

### Post by DigitalFirefly on 2012-02-10
> **darkod said:**
> After you create the raid devices, you still have to set up the partitions as usual. For example, for the root partition it would be:

1. Go into Software RAID and configure a raid1 device from the two 960GB partitions you prepared.
2. After that in the list of partitions, a 960GB RAID1 device will show up. Select the Free space of this device and create primary ext4 partition on it, mount point /.

Do the above for every raid device.

The message is clear, you are trying to proceed without telling it what to use as root partition.

I could send you one link later, don't have it at hand right now.


Thank you so much, I think that did it.:D:D:D:D:D

---

