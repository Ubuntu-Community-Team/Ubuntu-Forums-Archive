---
title: "Failed Karmic Upgrade: libblkid.so.1: no version info found."
date: 2009-07-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fraser_m on 2009-07-26
I was upgrading to Karmic (update-manager -d) when there was a power cut. Turned PC back on, GDM fails to start, /etc/init.d/gdm restart: [fail].

So I try dpkg --configure -a. Installs most of the packages, fails on a few, including libgudev-1.0-0, gvfs, gvfs-bin, gvfs-fuse, and a couple more. I dpkg --force-all -r these packages, and redo dpkg --reconfigure -a. Everything seems swell. I reboot, and findfs and fsck both complain of:```
libblkid.so.1: no version information found
```
I get dropped to maintenance shell, with read-only on /, and start to panic. Both dpkg and aptitude can't do anything, and I tried to remount the partition.

Any ideas? chroot it, maybe?

All help appreciated!

---

### Post by xx58 on 2009-07-27
:rolleyes:Open again Terminal and write update-manager -d and it will start at that point where it was end.

---

