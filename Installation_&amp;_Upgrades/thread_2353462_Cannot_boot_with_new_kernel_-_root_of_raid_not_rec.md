---
title: "Cannot boot with new kernel - root of raid not recongnized &quot;alert uuid does not exist"
date: 2017-02-22
forum: Installation &amp; Upgrades
---

### Post by wtson42 on 2017-02-22
Hello,

I'm trying to update kernel of ubuntu 16.04.2, current version is 3.14.

Disks are setup as raid 0 with root partition on /dev/md2 and home on /dev/md3 

When I boot with new kernel I get error 

```
Gave up wating for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=<root partition uuid> does not exist.
Dropping to a shell! 

```

The UUID it is waiting for is correct for the root partition (I also use UUID in fstab).

If I run blkid in in that busybox after failing to boot it recongnizes /dev/md3 correctly (has correct UUID), but /dev/md2 (root partition) is not recongnized/shown at all. 

The issue seems that raid's root partition doesn't get assembled ? I ran fsck on both partitions and they are fine, I still have old kernel in bootloader and it still works fine.

---

