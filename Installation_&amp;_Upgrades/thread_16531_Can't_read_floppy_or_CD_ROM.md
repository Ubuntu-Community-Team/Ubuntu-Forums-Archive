---
title: "Can't read floppy or CD ROM"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by Ron W on 2005-02-22
I've successfully loaded Ubuntu onto my system which is:-

AMD K6/2 - 500MHz
64MB RAM - currently 2MB of which is used by the onboard graphics
dual booted with Windows 98

I have the following problems with removeable medias

1) I am unable to read the floppy

When I double click on the 'Floppy 1' icon in Ubuntu to read a floppy (that I can successfully use on Windows 98) I get the following message:-

'Error
Could not mount floppy 1:
Unable to mount the selected volume:
mount: I could not determine the filesystem type, and none was specified'

2) When I double click on the CD ROM the system freezes.

Ron

---

### Post by towner on 2005-02-22
hi

I think that wallijonn may have silved this earlier, this is his solution


sudo gedit /etc/fstab

Code:
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
sudo gedit /etc/modules

add floppy to the end of the list
reboot

You can find his solution thru  a forum search,
Towner

---

### Post by wallijonn on 2005-02-22
sudo gedit /etc/fstab

/dev/fd0 /media/floppy0 vfat,ext2 rw,user,noauto 0 0

<exit, reboot>

Your CDRom problem may take a longer time to fix. What type is it? Is it installed with another CDR, DVD or HD on its IDE chain?

What does your fstab look like?

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat,ext2    rw,user,noauto  0       0

?

---

### Post by Ron W on 2005-02-23
_Floppy_

> sudo gedit /etc/fstab

/dev/fd0 /media/floppy0 vfat,ext2 rw,user,noauto 0 0

<exit, reboot>
With the above done do I still need to mount and unmount every time I use a floppy? If so, how do I do these, and is there a way that this can be done automatically so that I don't have to remember?

_CD ROM_

> /dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 vfat,ext2 rw,user,noauto 0 0
Am I right to assume that these lines should be in fstab? As I'm not at my computer at the moment I can't check until I get home.

Is it necessary to mount and unmount every CD I put into the CD player?

Ron

---

