---
title: "kubuntu won't automount cd/dvd"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-10-14
as the title, kubuntu won't automount any cd's or dvd's, with one exception:  dvd movies will automount and work fine.

game cd's, music cd's, even blank cd's won't automount.  I have to manually mount /media/cdrom0

not sure what you need to help me with this but here is fstab
```
buzzmandt@buzzmandt-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=73689172-9c6b-4382-aca4-488820d60064 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f6b56d18-5867-48ed-a840-8f2b48114010 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
and mtab
```
buzzmandt@buzzmandt-laptop:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/buzzmandt/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=buzzmandt 0 0
/dev/sr0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=buzzmandt 0 0

```

in gnome game cd/dvd's and blank cd's mount, but not music cd's

---

### Post by buzzmandt on 2009-10-14
am I the only one???
I have been running this install since alpha 3 (i think) and could try a live usb and see if it works with that.  I am currently up to date on all updates so I don't know if that'll work.

---

