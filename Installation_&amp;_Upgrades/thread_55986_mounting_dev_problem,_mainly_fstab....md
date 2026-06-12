---
title: "mounting /dev problem, mainly fstab..."
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by kenl on 2005-08-10
i have only just switched over to linux totally, thought i had a few go at linux awhile back, so i have some knowledge of such.

ok i just got onto ubuntu, yesterday, everything else is working well,
 i did the fdisk -l
and came back with

> fdisk -l

Disk /dev/sdc: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4870    39118243+   c  W95 FAT32 (LBA)
kenl@kenl:~/Desktop/wget-1.10$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9544    76662148+  83  Linux
/dev/hda2            9545        9732     1510110    5  Extended
/dev/hda5            9545        9732     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7649    61440561    c  W95 FAT32 (LBA)
/dev/sda2            7650       18820    89731057+   c  W95 FAT32 (LBA)
/dev/sda3           18821       19457     5116702+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561    c  W95 FAT32 (LBA)
/dev/sdb2            7650       19457    94847760    c  W95 FAT32 (LBA)

Disk /dev/sdc: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4870    39118243+   c  W95 FAT32 (LBA)
 

(ignore last drive sdc1)

so i have sda1, sda2, sda3, sdb1 and sdb2 to deal with.
which all had been converted to fat32 format before i switched.

now i have gone and done, the next command

> 
Sudo mkdir /media/sda1
Sudo mkdir /media/sda2
Sudo mkdir /media/sda3
Sudo mkdir /media/sdb1
Sudo mkdir /media/sdb2


And then i went try mounting them manually

> 
sudo mount /dev/sda1 -t vfat /media/sda1
...
...


and they all show up properly under the /media folders
and i could see all the files that was originally there

now come the fstab

i went and typed

SUDO gedit fstab, and this is what my fstab now looks like

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/media/sda1	vfat	default	0	0
/dev/sda2	/media/sda2	vfat	default	0	0
/dev/sda3	/media/sda3	vfat	default 0       0
/dev/sdb1	/media/sdb1	vfat	default 0	0
/dev/sdb2	/media/sdb2	vfat	default 0       0


the problem now is, everytime i reboot my computer,
while loading it says 

> 
mount: special device /dev/sda1 does not exist
mount: special device /dev/sda2 does not exist
...
...



so when i login and check the folders where the drives resited.
nothing is inside the folder.

how can i go about fixing this. i tried different format, characters for the fstab "option" tab, but still no go.

anyhelp would be greatly appreciated.

regards
Ken

---

### Post by kenl on 2005-08-11
okay i found my solution was that i had to set the options to 
rw,user,noauto	0	0
instead.
which means read/write, any user, auto mount
so it should look like this

/dev/sdb2	/media/sdb2	vfat	rw,user,noauto	0	0

hope this comes helpful to others that has problem with it.

---

