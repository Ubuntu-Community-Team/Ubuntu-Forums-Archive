---
title: "how to install in 3rd partition for 12.04"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by kkruecke on 2012-06-19
I have Windows Vista and Ubuntu 11.04 installed, with grub as the boot manager, and a linux-swap partition. 

I would now like to install 12.04 into a third partition. How do I go about it? Should I need to manually resize the Ubuntu partition (there is plenty of free space), using gparted, and then use the remaining unallocated space to create a new, third partition, also with gparted? Or, will the installation prompt me to create a new partition (in addition to the Windows Vista and 11.04 partitions)?

---

### Post by darkod on 2012-06-19
It's best to boot into live mode first and use Gparted to shrink the 11.04 partition.

After that is finished no need to create a new partition with Gparted. Leave the space as unallocated and when doing the 12.04 install you will have the option to use one of the auto methods or if using the manual partitioning you will be able to create a partition from the unallocated space.

---

### Post by kkruecke on 2012-06-19
Cool. Thanks. I'll resize using gparted from within Try Ubuntu. Then reboot and install.

---

### Post by kkruecke on 2012-06-19
> Leave the space as unallocated and when doing the 12.04 install you will have the option to use one of the auto methods

I choose the Do Something Else option during installation (rather than Erase or Upgrade from 11.04 to 12.04). But when I tried to install into the "freespace" (which I selected from the gparted-like , but it said "no root file system installed." So I added the ext4 filesystem with / as the mount point. It seems to be installing ok....

---

