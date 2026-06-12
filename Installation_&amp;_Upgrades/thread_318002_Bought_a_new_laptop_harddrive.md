---
title: "Bought a new laptop harddrive"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by Johan! on 2006-12-13
I bought a new harddrive for my laptop, and I'd like to copy the partitions to the new drive.

Problems:
[LIST]
[*]The new drive is not the same size as the old drive. It's slightly smaller.
[*]I cannot connect the drives simultaneously to my computer.
[/LIST]

At the moment I'm backing up each partition of the old drive with dd_rescue.
So when that's finished, I will have an image of each partition on my computer.

What should I do next?
Do I have to create new partitions on the new drive?
If so, do they have to be exactly the same size as the partitions on the old drive?

sudo fdisk -l /dev/sda: (old drive)
```

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7183    57697416    7  HPFS/NTFS
/dev/sda2            7184        7693     4096575   83  Linux
/dev/sda3            7694        9602    15334042+  83  Linux
/dev/sda4            9603        9733     1052257+  82  Linux swap / Solaris

```

---

