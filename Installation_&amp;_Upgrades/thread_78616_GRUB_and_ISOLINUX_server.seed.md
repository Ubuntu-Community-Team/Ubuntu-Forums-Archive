---
title: "GRUB and ISOLINUX server.seed"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by mr_mop on 2005-10-18
I followed the instructions at [http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)
and managed to install Hoary.  Which is great.
I now want to install Breezy but only want to do a server install.
Is there anyway to modify the menu.lst file

```
 title Ubuntu Installer (hd0,0)
kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd (hd0,0)/boot/initrd.gz
```

to include something like in the isolinux.cfg file

```
LABEL server
  kernel /install/vmlinuz
  append  preseed/file=/cdrom/preseed/server.seed vga=normal initrd=/install/initrd.gz ramdisk_size=12288 root=/dev/rd/0 rw --

```

Thanks

MM

---

