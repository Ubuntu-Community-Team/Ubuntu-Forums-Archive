---
title: "loading new OS on an out-of-order partition"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by derande on 2010-03-11
i'm currently running karmic as my primary OS from sda1. when lucid is released, i plan on installing it on sda6 which is currently a storage partition and setting the /home folder on sda1, after i transfer my personal data to an external drive and wipe sda1.
is there any problem running the boot partition from sda6 instead of sda1 or should the boot partition be sda1 if there is only one OS?

also my sda2 is a combination of sda5 (swap) and sda6 (storage). is this normal (see output of 'sudo fdisk -l' below) or should sda5 and sda6 not be combined into sda2? i'm not sure how these 2 partitions ended up combined into sda2 in the first place...

thank you for the replies!

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ebd8130

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33874   272092873+  83  Linux
/dev/sda2           33875       38913    40475767+   5  Extended
/dev/sda5           37836       38913     8659003+  82  Linux swap / Solaris
/dev/sda6           33875       37835    31816669+  83  Linux

---

### Post by coffeecat on 2010-03-11
> **derande said:**
> i'm not sure how these 2 partitions ended up combined into sda2 in the first place...

I'll answer that one first. sda2 is an extended partition which is simply a container for the two logical partitions sda5 and sda6. Long story short: there is a limitation (for historical reasons) of only 4 primary partitions per hard drive. To get around this, you can have one (but one only) extended partition instead of a primary partition. The purpose of an extended partition is merely a container - you never use it directly. You can create several (I can't remember the limit - at least 20 I think) logical partitions in an extended.

The partition numbering convention is valuable. Partitions #1, #2, #3, #4 can only be primaries or an extended. Logicals are always numbered #5 upwards. Which is why you don't have sda3 or sda4.

sda6 will be fine as a root partition for Lucid. Linux is quite happy booting from a logical partition - unlike Windows. It's not impossible to boot Windows from a logical, but it needs some serious hackery. You'll be able to reformat sda6 in the Lucid installer. And it doesn't matter whether you have one or several OSs on that HD - the Ubuntu root partition can be on sda6. You can use sda1 for data storage.

One point of information. You refer to the boot partition when you mean the root partition in which you will have the /boot directory. Some people have a separate /boot partition (it only needs to be 100MB or so) mounted on the /boot directory in the root filesystem. You don't need to do that but I point this out because the term boot partition properly refers to such a small partition with just the contents of /boot.

Good luck with Lucid. I'm posting from the Alpha and it's mostly looking good. Especially the new colour scheme. :)

---

### Post by srs5694 on 2010-03-11
> **coffeecat said:**
> there is a limitation (for historical reasons) of only 4 primary partitions per hard drive.

Note that this refers only to the Master Boot Record (MBR; aka "msdos" or various other names) partitioning scheme. Most other partitioning systems, such as the GUID Partition Table (GPT) scheme and the Apple Partition Map (APM) scheme, don't make the distinction between primary/extended/logical partitions, and most have a much higher limit on the number of partitions in the main table. It's 128 for a default GPT configuration, for instance, although in GPT that number can be increased to an arbitrarily high value, provided no predefined partitions block expansion of the GPT data structures.

> You can create several (I can't remember the limit - at least 20 I think) logical partitions in an extended.

In terms of the disk data structures, the only limit is one determined by the size of the disk. The logical partitions are defined in a linked-list data structure, meaning that each partition definition (stored in something called an Extended Boot Record, or EBR) points to both the partition it defines and the next EBR. Thus, logical partitions aren't defined in a fixed-size table but in a distributed data structure whose size automatically increases or decreases whenever you add or delete partitions. I suppose the theoretical limit would be about 2 billion (2^31) partitions, if each partition were one sector in size, since MBR uses 32-bit pointers and each EBR occupies one sector. There's probably a much lower practical limit in terms of what Linux can handle, but if so, I don't know offhand what it is.

> sda6 will be fine as a root partition for Lucid. Linux is quite happy booting from a logical partition

This is correct, but with the caveat that whatever boot loader you use in the MBR must support booting off of a logical partition. ("MBR" can refer to both the partitioning scheme and the contents of the first sector generally. The primary boot loader is loaded off the first disk sector.) If you install GRUB or GRUB2 to the MBR, this will be fine, since both varieties of GRUB support booting off of logical partitions. If GRUB goes in the boot partition's filesystem, though, with another boot loader in the MBR, it might or might not work, depending on the MBR boot loader's capabilities.

---

### Post by derande on 2010-03-11
thanks for the helpful replies!

i'm going to go ahead and run lucid alpha 3 on my sda6 tonight and start playing with it.

---

