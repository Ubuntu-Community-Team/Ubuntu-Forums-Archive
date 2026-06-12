---
title: "recognze new extrernal HD"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by deposition on 2007-05-03
For some reason when I connect my new external HD Ubunbtu doesn't do anything, i don't know if/how I need to format it or what, but when I plug in my old external HD it is recognized right away.

Thanks in advance.

---

### Post by undecidable on 2007-05-03
Did you try an
fdisk -lu 
to see if it is really not there?

I am not sure if you mean it is not 'there' or just not mounted.

---

### Post by deposition on 2007-05-03
I mean it doesn't show up on my desktop or under places/computer, I see no way to access it, typing fdisk -lu in console does absolutely nothing but leave me with the prompt to type something else.

I tried it on my other Ubuntu box and it doesn't recognize the HD either.

---

### Post by taurus on 2007-05-03
```
sudo fdisk -l
```

---

### Post by deposition on 2007-05-03
With the new external HD pluged in it says 

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14380   115507318+  83  Linux
/dev/sda2           14381       14946     4546395    5  Extended
/dev/sda5           14381       14946     4546363+  82  Linux swap / Solaris

which is the same thing it says without it pulgged in, and with the external HD that works it says

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       24792   199133707+   f  W95 Ext'd (LBA)
/dev/sdb5               2       24792   199133676    7  HPFS/NTFS

---

### Post by taurus on 2007-05-03
From a terminal, do

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sdb5 /media/windows -o nls=utf8,umask=0222
df -h
```

p.s.  You _need_ to unmount it before you unplug it from your computer.

```
cd ~
sudo umount /dev/sdb5
```

---

### Post by deposition on 2007-05-03
when i type sudo mount -t ntfs /dev/sdb5 /media/windows -o nls=utf8,umask=0222 it says mount: special device /dev/sdb1 does not exist

---

### Post by taurus on 2007-05-03
> **deposition said:**
> when i type sudo mount -t ntfs /dev/sdb5 /media/windows -o nls=utf8,umask=0222 it says mount: [COLOR="Red"]**special device /dev/sdb1 does not exist**[/COLOR]

:confused:

---

### Post by deposition on 2007-05-03
does that mean that there is no connected ecternal HD?

---

### Post by taurus on 2007-05-03
Post the output of these two commands from a terminal again?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by deposition on 2007-05-03
> brian@brian-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14380   115507318+  83  Linux
/dev/sda2           14381       14946     4546395    5  Extended
/dev/sda5           14381       14946     4546363+  82  Linux swap / Solaris
brian@brian-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8c15eb7d-ac5b-4391-97f9-f49273e1d7e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6beeae70-27e3-4738-848b-50d3ff608171 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
brian@brian-desktop:~$ 
    j

---

### Post by taurus on 2007-05-03
Did you remove your external harddrive or turn off the power to it because it's not on the list anymore?

---

### Post by deposition on 2007-05-03
no it was on a and plugged in then. So are you saying it was on the list at some point?

I had a different external HD plugged in before that works

---

