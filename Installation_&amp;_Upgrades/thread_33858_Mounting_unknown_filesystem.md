---
title: "Mounting unknown filesystem"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by ylawayjdp on 2005-05-12
Hi I recently installed ubuntu 5.04 replacing suse 9.2.  The install has been a sucess and the only problem I have found is that I cannot mount my second hard drive I have posted my fstab below
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdb1	/media/hdb1	vfat	user,unmask=000	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

the hard drive I want to mount is hdb1 and i have created the mount point in media but when I select the drive to explore my files I get the following error

Could not mount device.
The reported error was:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Not completly sure what I am doing to be honest
any advice on what I need to do?

J

---

### Post by derrick1985 on 2005-05-12
[QUOTE=ylawayjdp]Hi I recently installed ubuntu 5.04 replacing suse 9.2.  The install has been a sucess and the only problem I have found is that I cannot mount my second hard drive I have posted my fstab below
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdb1	/media/hdb1	vfat	user,unmask=000	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

the hard drive I want to mount is hdb1 and i have created the mount point in media but when I select the drive to explore my files I get the following error

Could not mount device.
The reported error was:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Not completly sure what I am doing to be honest
any advice on what I need to do?

J[/QUOTE]

What type of drive is it, a Windows drive? If it's Windows 2k/Xp, it would be an ntfs partition, not vfat. If it's win95/98, then it would be a vfat partition.

Type in a terminal:

sudo fdisk -l /dev/hdb

That will list the partitions and the file system types (that fdisk can recognize)

---

### Post by ylawayjdp on 2005-05-12
Thanks for that 
this is what I got from the comand
Disk /dev/hdb: 30.0 GB, 30020272128 bytes
16 heads, 63 sectors/track, 58168 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       58168    29316640+  83  Linux
 
excuse my ignorance but I couldn't see the file type

---

### Post by GTvulse on 2005-05-12
[quote=ylawayjdp]
excuse my ignorance but I couldn't see the file type
[/quote]
fdisk won't inform you about the partition format type in an obvious way (yet the information is there). Rather use parted:

```

sudo parted /dev/hdb print

```

will give you the information you need in a more understandable format.

BTW, the fdisk output shows that your slave disk is formatted as ext2/3 (type 83, Linux).

---

### Post by ylawayjdp on 2005-05-13
Hi I changed my fstab to this 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdb1	/media/hdb1	ext3	user,unmask=000	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

changing the file type of hdb1 to ext3

then I get this message when I try to access hdb1 in konqueror i get this error

Could not mount device.
The reported error was:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

I am really stuck as to what to do to correct this
J

---

### Post by nad on 2005-05-13
The file system description should read:

/dev/hdb1 /media/hdb1 ext3 umask=0222

or:

/dev/hdb1 /media/hdb1 ext3 rw,user,noauto

in which case you will have to mount it manually by double-clicking its' icon in nautilus.

unmask should be umask . The fifth and sixth fields have no meaning for a vfat file system.

---

### Post by GTvulse on 2005-05-13
[quote=nad]
The fifth and sixth fields have no meaning for a vfat file system.
[/quote]

Your overall assesment is correct, but the assertion above is not. You can have the OS do a filesystem check on a vfat partition at startup time. I do think that a '0 2' setting would be more appropriate; checking the root partition must have priority at boot up time.

---

