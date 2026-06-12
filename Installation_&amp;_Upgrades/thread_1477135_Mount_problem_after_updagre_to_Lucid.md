---
title: "Mount problem after updagre to Lucid"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by edrojo on 2010-05-08
Hi. I just installed Ubuntu 10.04. When PC rebooted it gave the next message:

Press S to skip mounting or M for manual recovery.

It gave me no error. 

Here is my fstab:

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=cb37f231-68fd-452a-90e6-b16fee70e1aa /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=0d4c5629-c06c-4960-afbf-20c4c89e4a6a /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=0ed982c1-9990-4898-928a-fd4e605f4c9a none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any help will be apreciated.

PS: If I press S, it boot normally.

---

