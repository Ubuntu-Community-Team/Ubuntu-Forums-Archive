---
title: "Install freezes on partitioning"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by RembrantXVII on 2007-01-22
I'm attempting to install Ubuntu from the desktop Live CD on a HD with Windows XP already installed.

Once I hit Step 5 of 6, I select to re-partition an existing drive. It recognizes both my HDs, but on selecting to allocate 20 gigs to Ubuntu, the install hangs.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

```

Ultimately, Id like to have the 80GB disk partitioned to 60/20GB. Any help in determining why the re-partitioning hangs would be great.

-Rembrant

---

### Post by housam on 2007-01-22
I see that you have windows in the 80Gb HDD. So, you have to defrag it at least 2 times and then resize it using the Gparted tool leaving an unallocated space to create at least new 2 partitions :
one ( / ) for the root  10-15 Gb ext3
one (swap) 1Gb swap
then go for the installation using the manual way.

---

