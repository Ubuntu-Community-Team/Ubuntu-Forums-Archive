---
title: "failed upgrade - no space left on /tmp"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by duffrecords on 2011-10-28
I recently tried to upgrade nvidia-current via the command line.  While the kernel module was being built, it failed because there was apparently no space left on /tmp.  I checked the partition with df and there is plenty of space.  I rebooted to see if that would clear /tmp but now the kernel will not boot.  The kernel image can't be found so it boots into BusyBox.

I've booted from a live CD, mounted the filesystem, and chrooted into it.  I tried to reinstall the kernel but it starts building the Nvidia kernel module and failing again because there is no space on /tmp.  However, df still shows plenty of free space:
```
# df -h /tmp
Filesystem            Size  Used Avail Use% Mounted on
-                     4.6G  155M  4.3G   4% /tmp
```
Here is the tail end of the errors:
```
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/panic/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/panic/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/panic/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/panic/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-bottom/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-bottom/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-bottom/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_FHsSLX/scripts/init-bottom/ORDER: No space left on device
FATAL: Could not open /tmp/mkinitramfs_FHsSLX/lib/modules/2.6.33-29-realtime-pae/modules.dep.temp for writing: No space left on device
rm: cannot remove `/tmp/mkinitramfs_FHsSLX/lib/modules/2.6.33-29-realtime-pae/modules.*map': No such file or directory
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
What's going on here?

---

