---
title: "Mounting Issues and fstab entries"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by daphatbell on 2005-07-04
I'm almost certain this has been discussed before, but this is my first post, so bear with me! :)  Here is what it states when I use the "mount" command:

This is what it shows when I use the "mount" command:

/dev/hdb8 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda1 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hda5 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hda6 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hdb5 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hdb6 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hdb7 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdf on /media/cdrom2 type udf (ro,noexec,nosuid,nodev,user=yoda)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=yoda)

When it boots up, it seems to be ok with the way the fstab file is written and besides the system saying my SATA drive is non-existant, it gives the impression that everything booted correctly. However, when I browse the computer (places), I can view 9 folders and it should be closer to 90! ](*,) Before it listed all the partitions, but I couldn't access them. Now everything seems to be located in the "filesystem" drive/folder. It really should be this difficult to be honest. All the other distros I have tried, seem to mount the ntfs partitions with no intervention from me. :confused: Any suggestions/comments/hints? ;)

Thanks!

---

### Post by doclivingston on 2005-07-05
[QUOTE=daphatbell]/dev/hda1 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hda5 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hda6 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hdb5 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hdb6 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)
/dev/hdb7 on /mnt/windows type ntfs (ro,umask=0222,uid=1000,gid=1000)[/QUOTE]

That's probably going to cause issues - you shouldn't have more than one thing mounted onto the same directory. Which one of hda1, hda5, hda6 or hda7 is your windows partition?

---

