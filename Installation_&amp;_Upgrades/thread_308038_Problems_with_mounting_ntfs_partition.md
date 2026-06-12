---
title: "Problems with mounting ntfs partition"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by romaluca on 2006-11-27
I have follow the tutorial on ubuntuguide.org for How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access.

In file fstab i have this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=74e2486a-06e8-4efd-8561-b52c00d006e3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=eea4d2df-cca7-4dde-88a0-b707a186b83e /home           ext2    defaults        0       2
# /dev/hda1
/media/hda1     ntfs-3g    defaults,locale=en_US.utf8    0    0
# /dev/hda7
UUID=49701aff-ff64-46e3-a3d7-50e1177ab891 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

bur now the view of partition is lost
if i do mount -a the console tell me:
mount: mount point ntfs-3g does not exist


Why? what can i do?
Thanks

---

### Post by taurus on 2006-11-27
You need to mount your /dev/hda1 somewhere first before you use it!!!  Therefore, open a terminal and modify your /dev/hda1 to look like this.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Replace the old one for /dev/hda1 with this one.

```
/media/hda1  /media/windows  ntfs-3g  defaults,locale=en_US.utf8  0  0
```
Save it and create a new mount point and mount it...

```
sudo mkdir /media/windows
sudo mount -a
df -h
```

---

### Post by romaluca on 2006-11-27
I do it but receive this error:
romaluca@romaluca:~$ sudo mount -a
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.

---

### Post by taurus on 2006-11-27
It should be

```
/dev/hda1  /media/windows  ntfs-3g  defaults,locale=en_US.utf8  0  0
```

---

