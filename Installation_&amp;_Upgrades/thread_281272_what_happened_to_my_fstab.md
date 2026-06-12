---
title: "what happened to my fstab?"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by Eran on 2006-10-20
after upgrading from 6.06 to 6.10, my fstab file got converted in a way that I don't understand it anymore. partitions are called by codes:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=79a3271d-7e87-4ec7-9528-2cf45c283c5b / ext3 defaults,errors=remount-ro 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=78a53dca-b3ef-4c5b-8190-484c9b4ff1fe /home ext3 defaults 0 2
# /dev/hda3 -- converted during upgrade to edgy
UUID=5dfa0ca0-a892-4be7-bcb2-d30a829493bd none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /mnt/floppy     msdos   auto            0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=4521-4DDD /mnt/G Vfat defaults 0 0


```

what happened?

---

### Post by qpieus on 2006-10-20
I found this thread that talks about this:
[http://www.ubuntuforums.org/showthread.php?t=278652]("http://www.ubuntuforums.org/showthread.php?t=278652")

---

