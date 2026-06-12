---
title: "Can't partition Harddisk using GParted Partition Editor on ubuntu 12.04"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by vtnt on 2013-05-27
Hi,

When trying to use GParted Partition Editor I can see my wholde harddisk /dev/sda1

The row is like
Partition: /dev/sda1
File System:ext4
Mount Point: /
Size: 456GB
used: 16GB
Flags: Boot

When I try to create partition Table I get following message

[I][B]2 partitions are currently active on device /dev/sda.
A new partition table cannot be created when there are active partitions.  Active partitions are those that are in use, such as a mounted file system, or enabled swap space.[/B][/I]
***Use Partition menu options, such as unmount or swapoff, to deactivate all partitions on this device before creating a new partition table.***

So I try to unmount using Gparted I get following message

[I][B]Could not unmount /dev/sda1
[/B][/I]***The partition could not be unmounted from the following mount points:***
***/***
***Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.***

please help.

Thanks,
vtnt.

---

### Post by ahallubuntu on 2013-05-27
~

---

### Post by Mark Phelps on 2013-05-28
As a note ... "sda1" is NOT your whole "hard disk"; instead, it is the first (and possibly, only) partition on your hard disk.

The disk itself is referred to as "sda".

The partitions are referred to as "sda1", "sda2", etc.

---

