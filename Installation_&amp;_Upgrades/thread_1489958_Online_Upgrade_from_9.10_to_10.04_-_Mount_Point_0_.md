---
title: "Online Upgrade from 9.10 to 10.04 - Mount Point 0 Does Not Exist"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by clm2424 on 2010-05-21
Hi:

I have a ThinkPad R51 - after doing the online upgrade from 9.10 to 10.04, the partition fails to boot.

It says Mount Point 0 does not exist.  Mount 0 command fails with Status 32.

This is for /dev/sda1.

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2041    16394301   83  Linux
/dev/sda2            2042        3648    12908227+   5  Extended
/dev/sda5            3493        3648     1253038+  82  Linux swap / Solaris
/dev/sda6            2042        3424    11108884+  83  Linux
/dev/sda7            3425        3492      546178+  82  Linux swap / Solaris

/etc/fstab for the 10.04 partition:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=63f3690d-6863-449f-962c-6b2ef4545a2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ec412833-e379-4c87-ab85-db14a00418b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any ideas?  I tried to boot into recovery mode but most of the utilities seemed to hang/freeze.

Thanks.

---

