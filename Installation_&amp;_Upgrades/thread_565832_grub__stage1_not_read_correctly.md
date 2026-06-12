---
title: "grub : stage1 not read correctly"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by jeyros12 on 2007-10-02
Hi,
grub won't install it says : stage1 not read correctly. I want it installed on the MBR (ubuntu is on /dev/hda6)

I have tried :
```
grub-install /dev/hda
```
and :
```
find /boot/grub/stage1
```
but none of them work...

Here is my fstab :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=42163fc0-22a4-46af-b5d2-709afe2e0762 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=863C45503C453D05 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=43D7-87DD  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

tx

---

