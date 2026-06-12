---
title: "[SOLVED] Error 17: after installing update 2.6.22-15 from 2.5.22-14"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by mountney on 2008-06-27
Ubuntu booting/running fine with 2.6.22-14-generic. 

Using the update manager, installed kernal update 2.6.22-15. Update required reboot - got 

"Error 17: cannot mount selected partition"

If I boot from Ubuntu live CD and choose last option, I can boot/run the existing 15-generic on hd1,0 (sdb) - everything works fine as was true with 14-generic  

Have done grub
root (hd1,0)
setup (hd1)

Have reinstalled grub

No Success!!! Any help appreciated
Thanks

**fdisk -lu** --------------------------------------------------
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xad9bad9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   160826714    80413326    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004a6e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   150239879    75119908+  83  Linux
/dev/sdb2       150239880   156296384     3028252+   f  W95 Ext'd (LBA)
/dev/sdb5       150239943   156296384     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x73b773b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    21334319    10667128+   7  HPFS/NTFS
/dev/sdc2        21334320   156296384    67481032+   f  W95 Ext'd (LBA)
/dev/sdc5        21334383    72629864    25647741    7  HPFS/NTFS
/dev/sdc6        72629928   146609189    36989631    7  HPFS/NTFS
/dev/sdc7       146609253   156296384     4843566    7  HPFS/NTFS

**menu.lst** --------------------------------------------
...
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=09f567c5-ea3a-470a-abe1-84fff62f5824 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=09f567c5-ea3a-470a-abe1-84fff62f5824 ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=09f567c5-ea3a-470a-abe1-84fff62f5824 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=09f567c5-ea3a-470a-abe1-84fff62f5824 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

**device.map** -----------------------------------------
(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

-----------------------------------------
**ls -l /dev/disk/by-uuid**
total 0
lrwxrwxrwx 1 root root 10 2008-06-27 10:17 09f567c5-ea3a-470a-abe1-84fff62f5824 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-06-27 10:17 1422FF2B18B3A7D1 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2008-06-27 17:17 508BFCB0DF947BE4 -> ../../sdc7
lrwxrwxrwx 1 root root 10 2008-06-27 10:17 631c386b-28da-45a4-8907-cbcac24c756e -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-06-27 10:17 64346B0C346AE112 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-06-27 10:17 DEC44CF3C44CD007 -> ../../sdc6
lrwxrwxrwx 1 root root 10 2008-06-27 10:17 E0E8AED1E8AEA4EE -> ../../sda1

-----------------------------------------
**ls -l /media**
total 56
lrwxrwxrwx  1 root root     6 2008-05-15 19:04 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-05-15 19:04 cdrom0
drwxr-xr-x  2 root root  4096 2008-05-15 19:04 cdrom1
lrwxrwxrwx  1 root root     7 2008-05-15 19:04 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-05-15 19:04 floppy0
drwxrwxrwx  1 root root  4096 2008-06-27 10:07 sda1
drwxr-xr-x 22 root root  4096 2008-06-27 12:43 sdb1
drwxr-xr-x  2 root root  4096 2008-06-27 12:38 sdb5
drwxrwxrwx  1 root root  4096 2008-06-27 10:07 sdc1
drwxrwxrwx  1 root root  4096 2008-06-27 10:07 sdc5
drwxrwxrwx  1 root root  4096 2008-06-27 10:07 sdc6
drwxrwxrwx  1 root root  4096 2008-06-27 10:07 sdc7

---------------------------------------------
**ls -l /boot**
total 34516
-rw-r--r-- 1 root root  424317 2008-02-12 02:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  424317 2008-06-10 04:55 abi-2.6.22-15-generic
-rw-r--r-- 1 root root   75311 2008-02-12 02:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2008-06-10 04:55 config-2.6.22-15-generic
drwxr-xr-x 2 root root    4096 2008-06-27 17:06 grub
-rw-r--r-- 1 root root 7237636 2008-06-01 09:38 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7237359 2008-05-16 04:20 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 7237254 2008-06-27 09:59 initrd.img-2.6.22-15-generic
-rw-r--r-- 1 root root 7237393 2008-06-27 09:58 initrd.img-2.6.22-15-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2008-02-12 02:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  823562 2008-06-10 04:55 System.map-2.6.22-15-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 02:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1764760 2008-06-10 04:55 vmlinuz-2.6.22-15-generic

**fstab** -------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                      0  0  
# /dev/sdb1
UUID=09f567c5-ea3a-470a-abe1-84fff62f5824  /               ext3         defaults,errors=remount-ro    0  1  
# /dev/sdb5
UUID=631c386b-28da-45a4-8907-cbcac24c756e  none            swap         sw                            0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec              0  0  
/dev/scd0                                  /media/cdrom1   udf,iso9660  user,noauto,exec              0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec           0  0  
/dev/sdb1                                  /media/sdb1     ext3         errors=remount-ro,user_xattr  0  0  
/dev/sda1                                  /media/sda1     ntfs         defaults                      0  0  
/dev/sdb5                                  /media/sdb5     swap         sw                            0  0  
/dev/sdc1                                  /media/sdc1     ntfs         defaults                      0  0  
/dev/sdc5                                  /media/sdc5     ntfs         defaults                      0  0  
/dev/sdc6                                  /media/sdc6     ntfs         defaults                      0  0  
/dev/sdc7                                  /media/sdc7     ntfs         defaults                      0  0

---

### Post by Pumalite on 2008-06-27
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
Do you have a mix of SATA and IDE?

---

### Post by mountney on 2008-06-27
[FONT="Courier New"]Yes, this is the setup:
                                        
SDA - 80GB IDE Drive	NTFS		sda1
SDB - 80GB SATA Drive	EXT3	Linux	sdb1
SDC - 80GB SATA Drive	NTFS	WinXP	sdc1, sdc5, sdc6, sdc7


SDA             Extra
	sda1		IDE	NTFS	80GB

SDB	sdb1	LINUX	SATA	EXT3	80GB
	sdb5    Swap		


SDC		WinXP	SATA    NTFS    80GB
	sdc1	System          NTFS
	sdc5	Programs        NTFS
	sdc6	Misc		NTFS	
	sdc7	Swap		NTFS

This config worked OK with 2.6.22-14-generic...

appreciate your looking at this...[/FONT]

---

### Post by mountney on 2008-06-28
[SIZE="3"]**Problem solved!!!**[/SIZE]

Thank you Pumalite!!!

The problem was in the BIOS, specifically the "Hard Disk Boot Priority"

The link that Pumalite provided:

 [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

had the info on how boot priority can cause this problem an how to change it in the BIOS...

Thanks again Pumalite for the link and to Herman at hermanzone!!!

---

