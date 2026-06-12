---
title: "Can't mount NTFS read-only using fstab?"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by celticmonkey on 2005-08-06
I followed the instructions at "http://ubuntuguide.org/#automountntfs" for using fstab to mount my NTFS partitions as read-only at bootup, but for some reason they seem to be mounting read-write. Any suggestions to modify my fstab to prevent writing to NTFS partitions?

Here's my fstab now:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               reiserfs notail          0       1
/dev/hdb4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/hda	ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /media/hdb1	ntfs    nls=utf8,umask=0222 0       0
/dev/hdb2       /media/hdb2	vfat    iocharset=utf8,umask=000   0       0

Here's the output of mount:

/dev/hdb3 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda1 on /media/hda type ntfs (rw,nls=utf8,umask=0222)
/dev/hdb1 on /media/hdb1 type ntfs (rw,nls=utf8,umask=0222)
/dev/hdb2 on /media/hdb2 type vfat (rw,iocharset=utf8,umask=000)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

---

### Post by edwina on 2005-08-06
I'm only new at this myself, but I believe that the "rw" tag in your mount file indicates read-write access. This implies that your fstab is not setting up read-only status. I believe that this is because read-write is the default (otherwise your main Linux partition could be set up as read-only too easily, which could cause problems) Insert "ro" into your fstab line. For example :-

/dev/hda1 /media/hda ntfs **ro,**nls=utf8,umask=0222 0 0

This is one of the lines from my fstab, which sets up read-only access :-

/dev/sda1       /media/WinXP    ntfs    user,ro,noexec,nls=utf8,umask=0222     0 0

Personally, I don't understand how umask works with ro/rw options, as they seem to address the same issue. Either way, it is working so I'm not messing around with it  ;-) 

I worked this out from tuXfiles, when I was doing it myself:-
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I hope that helps,

Ed

---

### Post by celticmonkey on 2005-08-06
Thanks. That seemed to do the trick!

---

