---
title: "hdb1 not reconized any more"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by mouseclone on 2007-04-23
This took me a short while to figure out but i finally got it.

/dev/hdb1 was not mounted because that is the old format for mounting an ext2 file system it seems.  I'm still new to this stuff and have very little time to read up on it all.  but if you use /dev/sdb1 then it will mount and reconise the second drive just fine.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e62fa685-18f7-4064-b090-dd485f11f486 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7b2dbce3-daa6-463d-9ab9-fdfe6e530612 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /home           ext3    defaults        0       1

```

the UUID mounts worked fine.  I'm not sure how to do a UUID mount so I guess it is something that I need to take the time to look up.  but again the /dev/sdb1 mount worked for me after the upgrade a few hours ago.

---

### Post by Gratarian on 2007-04-23
Reason for this is because of the 2.6.20 kernel that Feisty is running. It is treating all the IDE drives as SCSI. Nothing terribly important I suppose. As far as I can tell the UUID is kinda like a drive label to use for association instead of the direct device so if they change this again all your old configs should still work.

---

### Post by rex_the_first on 2007-04-23
To find the UUID and add it to fstab use the command

> sudo vol_id -u device

to display the UUID

---

