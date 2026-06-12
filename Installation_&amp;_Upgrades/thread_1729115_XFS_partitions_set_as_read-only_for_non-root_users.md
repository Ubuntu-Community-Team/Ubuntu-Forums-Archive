---
title: "XFS partitions set as read-only for non-root users"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by iarlnir stonehands on 2011-04-14
I have created and mounted two 500 Gb XFS type partitions, but have discovered that any non-root users cannot write to these disk mounts.

The following is the contents of my fstab :

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               xfs     defaults        0       1
/dev/sda1       /boot           xfs     defaults        0       2
/dev/sdb1       /usr/local      xfs     defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=56c631a3-87d6-4ffc-9b99-52728f995e51 none            swap    sw              0       0

... I was thinking that I could alter something in the fstab, but I am guessing by the looks of it, that all should be access with 'defaults' set. (Unless I am missing something)

Was wondering if somebody out there could help me change the permissions on /dev/sda2 and /dev/sdb1 as those are the two in question.

Thanks in advance,
Travis

---

