---
title: "Un-Allocated Disk SPace Issue"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by mcarrigan on 2010-05-20
SO what I wanted to do was create a Win7 Partition an Ubuntu Partition and a large area of shared disk space that I would uses as generic storage for both.  So my Dell came preloaded with Windows in one Part. a dell utility in one and a recovery in one.  I shrank the Windows Vol to 75GB and created my Ubuntu at 75GB as well.  Against better judgment I did not create a swap drive.  But gparted keeps telling me I cannot create more then 5 primary partitions.  So I don't know what to do to get this last Section Formated to use.  So this is what gparted looks like right now:

/dev/sda1 - fat16 - DellUtility
/dev/sda2 - ntfs - RECOVERY
/dev/sda3 - NTFS - Win7
/dev/sda4 - extended
____/dev/sda5 - ext4
unallocated

I haven't done much with Ubuntu yet so I am willing to reload if I need to reformat anything (Ubuntu not Windows).  I may be able to drop the DellUtility as well because I had to stop all Dell Utility's from running because they were over-righting the MBR and killing Grub2.

---

### Post by plucky on 2010-05-20
> But gparted keeps telling me I cannot create more then 5 primary partitions.

You cannot create more than 4 primary partitions,and the extended partition counts as a primary partition.You have reached the maximum number of primary partitions on your disk.

You can extend the extended partition to encase the un-allocated space,and then create a logical partition within the extended partition that both Win7 and Ubuntu can use.You can have as many logical partitions as you require within the extended partition.

You cannot resize the extended partition when the partition is mounted,i.e when booted into Ubuntu, and so you have to use gparted from the Live CD to resize that partition.

Good Luck.

---

### Post by John Bean on 2010-05-20
And just to add: after you enlarge the extended partition to absorb the free space you can create a swap partition as well if you want :-)

---

