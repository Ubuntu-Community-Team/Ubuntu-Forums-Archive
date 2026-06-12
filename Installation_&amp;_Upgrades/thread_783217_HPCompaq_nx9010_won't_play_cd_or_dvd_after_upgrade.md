---
title: "HP/Compaq nx9010 won't play cd or dvd after upgrade"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by cub on 2008-05-05
I ran an upgrade from 7.10 to 8.04 this weekend and everything seemed fine until I tried to play a cd today. I have tested CD-R, audio cds and DVDs and none will play since the upgrade. I have no idea what happened since everything else works great (from what I have seen)

Any ideas?

My fstab might give some insight?
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=2d6f94e6-a0b4-4691-8cac-e8688ae4ab15 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=be5b30ac-d9f5-4ef4-a306-e7e3ff45a682 /boot           ext3    defaults        0       2
# /dev/hda6
UUID=a957dd07-55c0-47bf-a1cf-e7ffc4ccc6fa /home           ext3    defaults        0       2
# /dev/hda1
UUID=FC8CE7448CE6F852 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=39ac0e3d-2db7-4dd9-976d-dc726393b133 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

