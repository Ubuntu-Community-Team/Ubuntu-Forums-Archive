---
title: "/run problem"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by meatlinux on 2012-02-28
Hi there. I am new to linux.

Having this problem at when trying to boot my ubuntu 10.04 LTS.

```
mount: Too many levels of symbolic links
mountall: mount /run [168] terminated with status 32
mountall: Filesystem could not be mounted: /run
```

2tb hdd with 100mb for /boot and a tiny bit for swap and the rest for /

I have did the check disk and result is clean.

My fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=6a611d5e-38a0-400d-914c-dc135721594e /               ext4    errors=remount-ro,user_xattr 0       1
# /boot was on /dev/sda1 during installation
UUID=25c096ab-f15c-4b3a-96d3-4d5ab6ae4f4c /boot           ext2    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=0e40868e-e211-40a0-9096-c5461038e7c8 none            swap    sw              0       0

```

Please help me with this. I have been trying for 2 days.

thanks!

---

### Post by Paddy Landau on 2012-02-28
This is a bit strange.

The [folder /run is a new one for Linux]("http://askubuntu.com/questions/57297/why-has-var-run-been-migrated-to-run"), which has been incorporated into Ubuntu from version 11.10.

You should not be seeing /run on 10.04.

Have you perhaps manually upgraded your kernel beyond the default?

---

