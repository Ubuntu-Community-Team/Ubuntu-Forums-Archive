---
title: "Why doesn't Ubuntu read the /etc/filesystems?"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by MikkelMJ on 2006-06-25
I've been told that I need to use the /etc/filesystems in order to make Linux load all NTFS volumes with the UFSD module driver instead of the default. But from the bginning it wasn't on my system so I created it, but Ubuntu still doesn't read from it it seems. What am I doing wrong?

Here's a copy of my /etc/filesystems:
mikkel@mikkel:~$ cat /etc/filesystems
# /etc/filesystems
#
# This file defines the filesystems search order used by a
# 'mount -t auto' command.
#

reiserfs

# Uncomment the following line if your modular kernel has vfat
# support and you want mount to try vfat.
vfat
ufsd

# Uncomment the following line if your modular kernel has udf
# support and you want mount to try udf before iso9660.
udf
iso9660

# Keep the last '*' intact as it directs mount to use the
# filesystems list available at /proc/filesystems also.
# Don't remove it unless you REALLY know what you are doing!
*


But as you can see from the /etc/mtab the usb-hotplugable-volumes are still loaded with the NTFS driver:

mikkel@mikkel:~$ cat /etc/mtab
/dev/hda3 / reiserfs rw,notail 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0
/dev/hda1 /media/Windows ufsd rw,nls=utf8,umask=0,gid=46,quiet 0 0
/dev/sda1 /media/A ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iochar set=utf8 0 0
/dev/sda3 /media/C ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iochar set=utf8 0 0
/dev/sda2 /media/B ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iochar set=utf8 0 0


The reason why the hda1 is loaded correctly with the NTFS-driver is that I've told it to in /etc/fstab, but I can't do that for usb-disks as they do not keep the same /dev/*-adress from on time to the next.

By the way, the UFSD-driver is a 100% functional read/write driver for NTFS.

---

