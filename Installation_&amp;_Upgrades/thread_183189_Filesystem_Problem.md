---
title: "Filesystem Problem"
date: 2006-05-27
forum: Installation &amp; Upgrades
---

### Post by S{yndrom}e on 2006-05-27
Hi I have a little problem at the ubuntu boot-up screen. When it is checking off the list (i.e sycrhonizing to npt.ubuntu.com whatever) it gets to mounting local file systems. What it says is exactly this:

Mounting Local Filesystems..................          [COLOR="Red"]Failed[/COLOR]

However this doest *really* seem to have an effect but recently my cpu "consumtion" is always in the 80s and my memory usage is much higher than normal.

Anyways here is the my fstab if that would help anyone

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows vfat defaults 0 0
/dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0


Thank you in advance!

---

### Post by Herman on 2006-05-27
Try [forcing a filesystem check]("http://users.bigpond.net.au/hermanzone/p10.htm#forcefsk") and see if that helps. A filesystem check in Ubuntu is not like defragging in Windows, it is done when you re-boot and shouild only take a few minutes.
It might help or maybe not, but it won't do any harm to try. Regards, Herman

---

### Post by Sutekh on 2006-05-27
[quote=S{yndrom}e]
Anyways here is the my fstab if that would help anyone
```

/dev/hda1 /media/windows vfat defaults 0 0
/dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0
```[/quote] Look you have two entries for the same partition /dev/hda1.  One FAT, one NTFS.

What is the format of the /dev/hda1 partition?  You should remove or 'comment out' the redundant one.

First backup the fstab (always good practice), the edit the file.  I use **nano**, but you can use gedit if you wish
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` When the editor loads, comment out the incorrect entry, by placing a # sign at the beginning of the line.  If the Windows partition is formatted NTFS, the you should finish with this
```

#/dev/hda1 /media/windows vfat defaults 0 0
 /dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0
``` Vice-versa if the Windows partition is FAT.

Save the file (Ctrl+O in nano) and exit (Ctrl+X).  Now you are done!  That will fix the filesystem error, but I dont know about the CPU usage.

---

### Post by blackweaver on 2006-05-28
[QUOTE=Sutekh]```

#/dev/hda1 /media/windows vfat defaults 0 0
 /dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0
``` Vice-versa if the Windows partition is FAT.
[/QUOTE]

or type fdisk -l to find out which partitions have which filesystem and then update yuor /etc/fstab accordingly:-k

---

