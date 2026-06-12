---
title: "Fiesty upgrade fails: disk space check seems bugged"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by DavidTangye on 2007-05-03
When I start at Upgrade I get the error 
> Not enough free disk space

The upgrade aborts now. Please free at least 3197k of disk space on /boot. Empty your Garbage Bin and remove temporary packages of former installations using 'sudo apt-get clean'.

/boot is not a partition, its in the root partition. Here is /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=b7bce030-9b6a-43a4-9eb1-fbca1bdde76a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=e9abaaf0-de55-4552-a625-e5d05329b077 /home ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=081727d9-f4da-4060-b837-f7ec7dc17950 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=9877-489A /mnt/winfat vfat rw 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=1A6409D86409B811 /mnt/windows ntfs ro,users,umask=0000 0 0
```

This is a very unhacked standard vanilla Ubuntu machine.

---

