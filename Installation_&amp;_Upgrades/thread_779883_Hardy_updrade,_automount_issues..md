---
title: "Hardy updrade, automount issues."
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by Sutur on 2008-05-03
Hi.

I did the upgrade from 7.10 > 8.04 and was surprised that it worked at all.

However, I do have a few problems with automount/hal, now.

If you take a look at my fstab you won't notice anything wrong with it, but after every boot, the devices change. That is, /dev/sda1 might become /dev/sdb2 after a boot - I only know this because I've labeled them properly, and after looking at gparted after every boot, using the label as a reference, they change.

/etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


proc            /proc           proc    defaults        0       0


/dev/sdb1		/  reiserfs notail          0       0


#/dev/sde1 		/media/ide_02   reiserfs defaults        0       0


/dev/sda1 		/media/sata_01  reiserfs defaults        0       0


# dev/sdc1 		/media/sata_02  reiserfs defaults        0       0


/dev/sdd1 		/media/ide_01   reiserfs defaults        0       0


/dev/sdb3		/media/win      ntfs    defaults,umask=007,gid=46 0       0


/dev/sdb2		none            swap    sw              0       0


/dev/scd0		/media/cdrom0   udf,iso9660 user,noauto,exec 0       0


/dev/hdc		/media/cdrom1   udf,iso9660 user,noauto,exec 0       0


/dev/hdd		/media/cdrom2   udf,iso9660 user,noauto,exec 0       0
```


Any direction would be appreciated :)





There are also quite a few issues with compiz-fusion, especially since I installed some custom plugins, and now won't work or even enable. But they do appear in ccsm, which is odd.

Thanks to anyone in advance.

---

