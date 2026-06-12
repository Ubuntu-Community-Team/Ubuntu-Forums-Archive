---
title: "Failing to boot off RAID-1 devices"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2008-01-23
Looks like I spoke too soon on this one - I'm not quite there yet !

Even though the system has been working fine since I got the RAID-1 set up, and "cat /proc/mdstat" shows everything working, I've found that the system will only boot with both drives powered up and connected. If I disconnect either drive it won't boot.

I get exactly the same output regardless of which drive is disconnected (see below): note the *root (hd0, 0)* for both, shouldn't it read hd1 for one of them ?

Also, it's trying to boot off /dev/md0, is that possible if it can't assemble the array ?

:confused::confused::confused::confused:

```
Booting 'Ubuntu 7.10, kernel 2.6.22-14-server'

root (hd0,0)
  Filesystem type is ext2fs, partition type 0xfd
kernel /boot/vmlinuz-2.6.22-14-server root=/dev/md0 acpi=off ro quiet splash
    [Linux-bzImage, setup=0x1e00, size=01b2538]
initrd /boot/initrd.img-2.6.22-14-server
    [Linux-initrd @ 0x1f83b000, 0x7b499b bytes]

Loading, please wait...

stdin: error 0
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
mount: can't read /etc/fstab: No such file or directory
mount: mounting /root/dev on /root/sys/.static/dev failed: No such file or directory
mount: mounting /root/sys on /root/sys/.static/sys failed: No such file or directory
mount: mounting /root/proc on /root/sys/.static/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Busybox v1.1.3 etc.etc.

(initramfs)
```

---

### Post by dbyrne on 2008-02-06
Quick bump up, any help appreciated ?

---

