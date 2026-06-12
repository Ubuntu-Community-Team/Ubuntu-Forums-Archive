---
title: "Ubuntu RAID install. No root file system is defined.  Please correct from partitioner"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by kntgsp on 2008-01-30
So I managed to get the LiveCD booted to the desktop by disabling RAID in the BIOS.  Before I did this though, I created a 40GB partition on the RAID array for Ubuntu.

So basically, I have Vista running on a 300GB RAID 0 (2 x 150 GB drives) and created a 40 GB NTFS partition on that drive for Ubuntu.  Rebooted to BIOS, disabled the RAID, since you can't boot the LiveCD with RAID enabled.

Boot to the desktop and follow the RAID install guide provided by ubuntuforums, which says to do the following:

System>Administration>Software Sources, add UNIVERSE software repository
System>Administration>Synaptic Package Manager, install dmraid package
Applications>Accessories>Terminal

sudo dmraid -ay, which doesn't give me errors.

So I hit Install, get to the "Prepare partitions" and it detects the 40 GB parition, however when I try to click "Forward" after highlighting it, I get the following message:

"No root file system is defined.  Please correct this from the partitioning menu"

However, it lists everything right:

/dev/mapper/isw_cbcjebabgg_Volume0
----/dev/mapper/isw_cbcjebabgg_Volume0 (type) ntfs (mount point) /media/mapper_isw_cbcjebabgg_Volume0 (size) 258129MB
----/dev/mapper/isw_cbcjebabgg_Volume0 (type) ntfs (mount point) /media/mapper_isw_cbcjebabgg_Volume0 (size) 41943MB

/dev/mapper/isw_cbcjebabgg_Volume01
/dev/mapper/isw_cbcjebabgg_Volume02
/dev/sda
/dev/sdb

So clearly the partition on the RAID array is showing up.  It shows Volume01 and Volume02 as the two hard drives and then Volume0 as the RAID array, with the partitions under it.

Does the partition have to be formatted to something other than NTFS?

---

### Post by Partyboi2 on 2008-01-30
Ubuntu uses ext3 for its native filesystem.

---

