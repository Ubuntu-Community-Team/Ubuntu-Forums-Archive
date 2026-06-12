---
title: "problem with DVD-ROM drive"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by pradeepadapa on 2006-10-14
hii,
       i hav ubuntu dapper installed with the latest stable 2.6.18 kernel(ya i updated frm 2.5.15 to 2.6.18) ,i hav two drives,

one LG CDR/RW drive
two SAMSUNG DVD-ROM drive, the problem is that my LG CDRW drive works fine when inserted with a cd but the DVD-ROM drive doesnt work when a dvd is inserted in it, when i saw in the /media folder to see whether the DVD-ROM drive was detected or not, i saw it as detected nd labelled as CD-ROM/DVD-ROM drive.

could anyone plse help me how to open the DVD's which are inserted in the DVD-ROM drive.

thanx fr ur reply in advance................ :cool:

---

### Post by Kateikyoushi on 2006-10-14
I also have only cdrom folder /media so that is not the problem.

What is the output of this command ?

```
cat /etc/fstab
```

---

### Post by pradeepadapa on 2006-10-14
hii, the output of the above command which u gav is


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd1       /media/hdd1     ext3    defaults        0       2
/dev/hdd5       /media/hdd5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdd6       /media/hdd6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdd7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


and the output in the /media is

lrwxrwxrwx  1 root root       6 2006-09-06 15:52 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2006-09-06 15:52 cdrom0
drwxr-xr-x  2 root root    4096 2006-10-14 19:48 cdrom-1
drwxr-xr-x 22 root root    4096 2006-09-20 21:39 hdd1
drwxrwx---  9 root plugdev 8192 1970-01-01 05:30 hdd5
drwxrwx--- 20 root plugdev 8192 1970-01-01 05:30 hdd6

---

### Post by pradeepadapa on 2006-10-14
hey anyone plse help me how to open an DVD frm my DVD-ROM drive which is detected by the ubuntu system but the DVD inserted is not being detected or opened.

---

### Post by Kateikyoushi on 2006-10-14
The drives are not set up in your fstab.
First see what those devices are, can dig them out of your dmesg which is pretty long.

```
dmesg
```

---

