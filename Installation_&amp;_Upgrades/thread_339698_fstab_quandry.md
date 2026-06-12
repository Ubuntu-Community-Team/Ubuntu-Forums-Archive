---
title: "fstab quandry"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by carverj on 2007-01-16
I'm fairly certain I used the last two lines here to mount my slave partitions without problems with breezy 
Do I need to track down UUID number to mount and if so how do I find this label?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=87db2df8-52a4-460f-8cea-fc1a838fd7f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=BAB490F2B490B1FD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=62c78358-bba9-463a-a4f8-2405ee8362df none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
# slave drive parititions I am attempting to mount
/dev/hdb1       /media/hdb1          fat32     defaults         0      2
/dev/hdb6       /media/hdb6          ext3      defaults         0      2
```

Thanks very much

---

### Post by tommcd on 2007-01-16
fstab will work with or without UUIDs AFAIK. The UUIDs were added so that if you cahange your hard drives around fstab can still boot them You can create the UUIDs if you want. See this:
[http://ubuntuforums.org/showthread.php?t=286758](http://ubuntuforums.org/showthread.php?t=286758)
[http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid](http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid)
Just back up your fstab first for safe keeping, then feel free to edit it to suit your needs or create UUIDs.
EDIT: I'm not sure about UUIDs for the fat32 partition though, or if you need them for that. When I get home I'll look at mine and see how winXP is identified in my fstab.

---

### Post by tommcd on 2007-01-16
My winXP partition has a UUID also, so I suppose you can create a UUID for your fat32 partition the same way as in the thread I linked to.

---

