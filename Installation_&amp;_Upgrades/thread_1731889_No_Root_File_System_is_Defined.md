---
title: "No Root File System is Defined"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by stormedwolf on 2011-04-17
Ok, so I've installed Ubuntu before, but I've never manually partitioned the hard drive. This time, I want to format my entire hard drive as a FAT32 file system.

So, that being said, this is what I do:

When I get to the install screen that says 'Allocate Drive Space' at the top, I click **Specify Partitions Manually (Advanced)**. Then, Once i hit forward, I see a screen with the free space i have on my hard drive (which is all of it at this point) some buttons (Create Partition Table..., Add..., Delete, Change..., and Revert), and a drop down box for selecting the partition in which the boot loader should be installed. 

Here's where i have my question. Does some of the hard drive have to be Ext4,3, or 2, or can all of it be a FAT32 file system? Also, every time i format all of the drive as FAT32, what should the mount point be? /, /dos, /windows, or something else. (I currently have Ubuntu installed, so there aren't any FAT32 partitions mounted)

Even if I do format the drive and select either /dos or /windows, i get an error:
**No root file system is defined. Please correct this from the partitioning menu.**

Does this mean that i have to have a Ext4 file system? And where should i install the boot file?

I know this might seem a really stupid beginner question, but I'm really lost, Thanks for any help i can get.

---

### Post by oldos2er on 2011-04-17
Ubuntu can't install on a FAT32 partition, it needs a Linux-native file system such as ext3, ext4, etc. The root file system mount point is /

---

### Post by stormedwolf on 2011-04-17
Thanks, I just fixed this actually.

---

