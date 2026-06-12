---
title: "Fresh install help"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by natman on 2008-04-23
I have Ubuntu 7.10 and going to do a fresh install of Hardy Kubuntu 8.04, my laptop has a Vista and Ubutnu on the one partitioned disk.
The last time i did the whole manual install option was in the breezy badger days:)
Can someone give me a fairly step by step guide to installing over the existing ubuntu ( and the swap bit also ) without killing windows.

Thanks:

---

### Post by IgnorantGuru on 2009-11-01
First take a look at /etc/fstab to see what partition is being used as swap, and which is /.

Also, if you can't tell from fstab which is swap (due to UUIDs being used), enter
```
sudo fdisk -l
```

The swap partition should have Id 82 "Linux swap / Solaris".  And the Ubuntu partition should have Id 83 "Linux"

When you get to the partitioner, select manual partitioning.  Set the swap partition to 'use as swap'.  Set your ubuntu partition to 'mount on /', and choose format it.  Leave the other partitions untouched (keep).  That should do it.

---

### Post by MC707 on 2009-11-01
remember to change / partition to ext4 ;)

---

