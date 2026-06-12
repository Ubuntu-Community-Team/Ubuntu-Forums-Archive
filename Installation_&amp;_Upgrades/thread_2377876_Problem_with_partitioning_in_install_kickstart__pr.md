---
title: "Problem with partitioning in install kickstart / preseed with LVM in Ubuntu 16.04"
date: 2017-11-17
forum: Installation &amp; Upgrades
---

### Post by subbrain on 2017-11-17
I want to do the following partitioning scheme during automated installation of ubuntu 16:

I have two disks /dev/sda and /dev/sdb.

1. /dev/sda1 /boot with ext3
2. Grub on /dev/sda
What I would do manually:
3. pvcreate /dev/sdb # I really want to use the whole disk, not a partition on second disk, it's easier to grow through vmware / pvresize etc.
4. vgcreate vg0 /dev/sdb
5. lvcreate -n lv_root -L 6.5G vg0
6. lvcreate -n lv_swap -L 1G vg0
7. mkfs.xfs /dev/vg0/lv_root as /
8. mkswap /dev/vg0/lv_swap for swap

So how to do that in automated install in ubuntu 16?

I thought about to do this task in kickstart %pre but how to tell the debian-installer / kickstart / preseed to use existing partitions further? Or is there a way to do commands above with kickstart or preseed partman?

Thanks for help in advance,
Marco

---

