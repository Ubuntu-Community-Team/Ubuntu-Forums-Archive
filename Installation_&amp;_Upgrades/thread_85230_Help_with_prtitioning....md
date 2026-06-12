---
title: "Help with prtitioning..."
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2005-11-02
I am trying to reconfigure my desktop machine, which is dual-boot. I decided to break the 80Gb disk into 4 partitions: 

1. 5.8Gb - Windows
2. 5.0Gb - Ubuntu /
3. 6.0Gb - Ubuntu /home
4. the rest - FAT32

So I did it using qtparted from system rescue CD. I installed Windows and started Breezy installation when I realised that I forgot to create Linux-swap partition. So I decided to resize FAT32 to free 500Mb for swap.  

I can do it, no problem. But qtparted creates a free space after the partition which is unusable for some reasons. I cannot format it or do anything with it. In Breezy installation it is also marked as unusable. Why is that? I usually have not got any problems with resizing before?

---

### Post by SickTwist on 2005-11-02
How much free space is it? It might not be enough to meet the minimum required by the filesystems you're trying to use. Or it could be that the first four partitions are primary partitions and 4 primary partitions is all that is allowed on one HDD.  The way to get around this limit is to have 1 to 3 primary partitions at the beginning of the drive, followed by an extended partition that takes up *all* of the remaining space on the drive. An extended partition is kind of like a container that you can fill with other partitions which are called logical partitions. There is no limit to the number of logical partitions you can put in the extended partition.

Your partition layout looks good. Ubuntu will use ~2GB after a default install just to give you an idea. The swap partition should be ~2x the size of your RAM (but no greater than 2 GB).

It's been awhile since I installed Windows--how much space did your Windows install take up and what version of Windows is it?

---

### Post by foxy123 on 2005-11-02
[QUOTE=SickTwist]How much free space is it? It might not be enough to meet the minimum required by the filesystems you're trying to use. Or it could be that the first four partitions are primary partitions and 4 primary partitions is all that is allowed on one HDD.  The way to get around this limit is to have 1 to 3 primary partitions at the beginning of the drive, followed by an extended partition that takes up *all* of the remaining space on the drive. An extended partition is kind of like a container that you can fill with other partitions which are called logical partitions. There is no limit to the number of logical partitions you can put in the extended partition.

Your partition layout looks good. Ubuntu will use ~2GB after a default install just to give you an idea. The swap partition should be ~2x the size of your RAM. (no greater than 2 GB).

It's been awhile since I installed Windows--how much space did your Windows install take up and what version of Windows is it?[/QUOTE]

I see. Thanks a lot, I think that's the problem. Can I convert FAT32 partition into extended one without loosing all the data? I have Windows Docs & Settings there. It's not a big deal to reinstall Windows since I have not configure anything there, but would be nice to avoid it.

I am using Windows XP and I guess it takes something around 2Gb. At least 5Gb was always enough for it and Programme Files.

---

### Post by SickTwist on 2005-11-02
No, the only way would be to copy the data to another partition. However, whenever you edit the partition table it is risky business so you should do backups beforehand in case something goes wrong. There is always a chance that all of the partitions on the disk could get messed up. Once you have the partitions in place, formatting them is less risky. Formatting one will not effect the others (just be sure you're formatting the correct one--don't do any of this late at night :) )

Also, whenever I edit partitions on a disk I make sure no other partitions on that disk are mounted. An easy way to do this is to use a live CD if you only have one HDD.

You may want to check out this [guide]("http://fdisk.radified.com/") to partitioning if you want to learn more about it. It has a little information about fdisk ( the Windows program, not the Linux fdisk) usage that you could skip if you want. But it gives a nice overview of the different partition types (primary, extended, logical) and offers advice about how to partition a disk.

---

