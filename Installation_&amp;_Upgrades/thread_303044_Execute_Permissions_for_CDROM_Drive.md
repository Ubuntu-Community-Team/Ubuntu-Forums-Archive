---
title: "Execute Permissions for CDROM Drive"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2006-11-19
Also posted in Hardware & Laptops...

I'm having a problem finding out how to unmount & remount my CDROM drive so that I can give myself execute permissions. There is an install program on the CD that I can't execute given the CD has only read-only permissions set.

I've searched through the forums & had a read of the "mount" & "unmount" sections of the manual but came away without an understanding of what to do.

Pointers anyone?

---

### Post by Kerry Lange on 2006-11-19
Is this a stupid question?  I'm a Ubuntu / Linux newbie so wouldn't know.

---

### Post by jtripp on 2008-02-08
I am not sure what the cause is -- it may be due to security settings, but the disk has been mounted without the exec bit set.  From a command line run:

```
> mount
```

This will list all of the mounted partitions,etc.  You should see something like:

```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda on /media/cdrom0 type iso9660 (rw,noexec,nosuid,nodev)

```

The last entry is the important one.  It is the entry about the cdrom.  What you
need to do is set the execute permission on the CDROM.  This can be done 
with:

```

> sudo mount -o remount,exec /media/cdrom0

```

There probably is a way to control the execute bit on CD mounts more globally, but I don't know it.

---

