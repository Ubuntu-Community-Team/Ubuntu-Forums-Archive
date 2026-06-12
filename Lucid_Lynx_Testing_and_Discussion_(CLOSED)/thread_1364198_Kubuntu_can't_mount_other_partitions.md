---
title: "Kubuntu can't mount other partitions"
date: 2009-12-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-12-25
Using Dolphine, when I try to access any other partition I get a red warning message(an example):

```
An error occurred while accessing 'DOWNLOADS', the system
responded: org.freedesktop.Hal.Device.Volume.PermissionDenied:
Refusing to mount device /dev/sda5 for uid=1000.
```

I looked at my User Management and fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda10 during installation
UUID=4ddd7df0-62ef-487b-bd2f-3b92c086d413 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=3c09b1da-04e4-49a0-bc64-8edef15610df none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

fstab is the same as my Ubuntu install, and it works. Any ideas? Thanks.

Edit:Under advance User Settings for Ubuntu. See attached. Where is this in Kubuntu?

---

