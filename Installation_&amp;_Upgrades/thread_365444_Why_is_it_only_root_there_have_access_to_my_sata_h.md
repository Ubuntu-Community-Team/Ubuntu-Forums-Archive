---
title: "Why is it only root there have access to my sata hdd"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by ZpiX on 2007-02-19
Hi

I Just get linux and i have mounted my sata hdd but is only root there have access to it... :(

How can i do so i have access to it all the time?

My Fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=3481c3b1-8e56-45e1-a64b-567cbd45b11d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=c51ef074-b5b0-4e25-bef5-7eab771bc0aa none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


/dev/sda1 /media/sda1 ntfs defaults,rw,nls=utf8,umask=0222,gid=46 0 2

---

