---
title: "How do I align partitions during installation?"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by Obscurious on 2013-05-08
I need the starting offset of my partitions to be a multiple of 8. Is there a way to set this alignment during the installation process of Ubuntu Server 12.04? I have been looking into passing a boot parameter to partman but was wondering if there was a better way to do this?

Here is an example of a misaligned machine:

```

# fdisk -lu

Disk /dev/sda: 34.4 GB, 34359738368 bytes
255 heads, 63 sectors/track, 4177 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xrrrrrrrrr

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    67106815    33302529    5  Extended
/dev/sda5          501760    67106815    33302528   8e  Linux LVM

```

Thus you can see that /dev/sda2 is the misaligned partition since 501758 is not divisible by 8. I set this installation up by selecting "use entire disk" during the partition section at installation. Is there a better option at installation time that will automatically align the partitions? 

Note: I have been abstracting the system as a whole to keep things simple. Let me know if it would help to know the details of the rest of the system (cluster); it has many layers.

---

### Post by darkod on 2013-05-08
Best just make the partitions with parted from live mode in advance. Then you simply use them during the server install.

Set parted to use unit MiB and the first partition to start at 1MiB (that leaves 1MiB unallocated at front). As long as partitions are a whole number of MiBs they will always be aligned since a MiB is always divisible by 4KiB, unlike a whole number of MBs which is not always divisible by 4KiB.

I like parted exactly for this reason, you can set exact start/end of the partitions you create, and you can select the unit size yourself (sector, MiB, GiB, etc).

---

### Post by Obscurious on 2013-05-08
Thank you Darkod. Your solution is elegant and will work just fine. I can't believe I didn't think of it myself.

---

### Post by Obscurious on 2013-05-08
Anyone confused:

MiB = Mebibyte = 2^20
MB = Megabyte = 10^6

Using MiB as the standard unit makes partition necessarily aligned because of what Darko said above.

---

