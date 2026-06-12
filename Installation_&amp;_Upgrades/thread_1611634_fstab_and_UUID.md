---
title: "fstab and UUID"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2010-11-02
I thought that Ubuntu now defaulted to identifying partitions by UUID in fstab, but having just done a clean install of 10.10 amd64, in fstab only the swap partition is identified by UUID, all the other partitions are still in /dev/sdnn format. This is the fstab setup by the install - I haven't touched it. I installed by booting off the live CD and then running the install from the desktop:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               btrfs   defaults        0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sdb3       /home           btrfs   defaults        0       2
/dev/sdb1       /tmp            btrfs   defaults        0       2
/dev/sda2       /var            btrfs   defaults        0       2
/dev/sda3       /var/log        btrfs   defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=a97eef33-e9dc-43ae-925d-d8217f301690 none            swap    sw              0       0
```

---

