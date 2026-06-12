---
title: "All data lost on one disk after installing Ubuntu"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by kokka on 2006-09-12
I was going to have dual boot with Ubuntu and Windows XP but after I had finished installing Ubuntu I could not choose between the two operating systems. Then I looked in the disk manager that the disk no longer had a file system. I attached a picture of it, maybe it helps.

Is there any way to get that data back since I really want some of it?

Thanks

---

### Post by orb9220 on 2006-09-13
gedit /etc/fstab
in a terminal
copy and paste the contents here.

---

### Post by kokka on 2006-09-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb2       /media/sdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

