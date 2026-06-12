---
title: "2nd harddrive not showing up?"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Digitallysick on 2007-03-20
here is my fstab, my 2nd hd is not showing up =(

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a5bfdcbf-ce96-4c7b-bc21-08e29040068d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=753a7e72-81ed-4ad6-80b3-a952aaee8e15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by K.Mandla on 2007-03-20
From a terminal, try 
```

sudo fdisk -l
```

and see if anything matches the size or partition layout of your drive.

---

