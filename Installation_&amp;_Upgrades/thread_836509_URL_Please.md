---
title: "URL Please"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by Craftycorner on 2008-06-21
I need a new fstab.  Can you give me the URL where I can download a fresh ect/fstab?  I forgot where that is.  I've got Kubuntu Dapper Drake.:confused:

---

### Post by hal8000 on 2008-06-21
The filesystem table is created automatically when you install linux. It gets its information from the install program, i.e. you choose a / partition and possibly a /home partition and a /swap partition in order to install ubuntu.

Ubuntu and kubuntu now list partitions by uuid.
You first need to run

sudo ls -l /dev/disk/by-uuid/

This will list your partition ids.
Then use vi or gedit to rebuild fstab:

sudo gedit /etc/fstab


This is what fstab looks like in Hardy heron running Ubuntu, it will be same for Kubuntu


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=3c8d8164-5070-43c4-927f-4a6c455cdb6c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=d3e21034-5180-4788-8108-16771bbc42b4 /home           ext3    relatime        0       2
# /dev/sda6
UUID=dd444861-6177-4745-8951-86a3f5c98005 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


The important part is to reflect your / and /home partitions with your UUID's you may not have a disk drive on your system so ignore last line.

---

