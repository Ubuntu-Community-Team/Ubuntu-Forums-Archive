---
title: "/home: waiting for /dev/mapper/sdaX_crypt after karmic update"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by leetlover on 2009-12-17
Hello,

I've updated my Jaunty install last night with the update manager. Everything went normal, but when I boot the new OS I get a couple of errors:

```
/home: waiting for /dev/mapper/sda6_crypt
swap: waiting for /dev/mapper/sda8_crypt
```

I'm running fully encrypted /, /home and swap partitions (created in Hardy, I upgraded till now). The system boots fine, as I get the passphrase prompts after the errors, but I want to get rid of them. I have searched around the forums and there are several posts, none giving me a working fix. Modifying ureadahead.conf in /etc/init to start on filesystem instead of mountall helps (the passwords prompts are displayed properly and seem to work), but the errors are still there.

Here is my **fstab**:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sda5_crypt /               ext3    errors=remount-ro,relatime 0       1
/dev/mapper/sda8_crypt /home           ext3    defaults,relatime        0       2
/dev/mapper/sda6_crypt none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7 	/boot           ext2    relatime        0       2
/dev/sda2       /mnt/e          ntfs-3g defaults        0       0
/dev/sda3       /mnt/f          ntfs-3g defaults        0       0
usbfs    /proc/bus/usb    usbfs    defaults  0  0
```

And my **crypttab**:
```
sda5_crypt /dev/disk/by-uuid/d489470c-01b9-4813-acac-7c62dd741e0a none luks
sda6_crypt /dev/disk/by-uuid/b52de371-e932-471a-9909-8de2f3bb501f none luks,swap
sda8_crypt /dev/disk/by-uuid/c9816f42-d6dd-4453-b841-60f673c1997d none luks
```

Any help is greatly appreciated, thanks in advance.

---

