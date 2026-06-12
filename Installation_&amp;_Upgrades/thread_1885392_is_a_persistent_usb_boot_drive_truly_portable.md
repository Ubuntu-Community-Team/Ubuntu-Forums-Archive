---
title: "is a persistent usb boot drive truly portable"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by sudodus on 2011-11-23
Hi everybody,

I know about usb boot drives and that they can be made persistent with a r/w file system. But what happens if I travel with the usb stick and want to use it somewhere else? Will it

- boot nicely?
- find the personal files?
- run whatever tweaks or software is on the r/w file system?

In other words, is a persistent usb boot drive truly portable?

---

### Post by An Sanct on 2011-11-23
Welcome to the forums!

The general answer is yes.

The USB will boot just like at your machine and bring up the desktop you left behind since the last use. Browser bookmarks, cookies history and saved passwords will be preserved. Most settings you applied will be preserved. Any installed software will be present.

I personally use the 32bit version, so there are no conflicts. You cannot run 64bit Live OS on a non-64bit machine (!) So use 32bits for maximum compatibility.

Do not enable any additional hardware drivers, that need proprietary downloads/installs (mostly GPU and networking)

PS. Offcourse, if you have a fast machine like a quad core i5 or better and then run the Live session on a 1Ghz single core processor, everything will run slower (obviously).

PS2. I have my "work desk" on such an USB, LAMP, MySQL*, different browsers, ...

---

### Post by sudodus on 2011-11-23
Great news :KS

I'll go ahead to make and test it

---

### Post by An Sanct on 2011-11-23
Hint: 
Never update system components on a Live Session USB, most updates will break the system or fail. 
Installs can take a while, but normally they complete okay, if they fail the first time, the second time they wont. :)

Anyhow :) a Live USB is a nice playground for testing ;) can't break anything :)

---

### Post by sudodus on 2011-12-18
Thanks for the tips!

Now I am running a live USB flash drive with Lubuntu. It works in standard volatile mode as well as in persistent mode.

The 16 GB drive is partitioned with Gparted. The first partition is used as a data partition because Windows can read it. (At least older Windows systems can only read the first partition on a USB drive.) See the attached picture.

I used the method in
_[COLOR=RoyalBlue][http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)[/COLOR]_
to make a 4 GB casper-rw file, that should be in the root directory of the second partition (that will be mounted to /cdrom during the live session).

Unetbootin was used to make the USB flash drive a live system from an iso file (in this case lubuntu-11.10-desktop-i386.iso).
```

ubuntu@ubuntu:~$ [COLOR=RoyalBlue]sudo fdisk -lu[/COLOR]

Disk /dev/sdb: 16.0 GB, 16028794368 bytes
255 heads, 63 sectors/track, 1948 cylinders, total 31306239 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25bf25be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    17607239     8803588+   b  W95 FAT32
/dev/sdb2   *    17607240    28097684     5245222+   c  W95 FAT32 (LBA)
/dev/sdb3        28097685    30202199     1052257+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ [COLOR=RoyalBlue]df[/COLOR]
Filesystem           1K-blocks      Used Available Use% Mounted on
/cow                   1808104     70412   1737692   4% /
udev                   1800780         4   1800776   1% /dev
tmpfs                   723244       852    722392   1% /run
/dev/sdb2              5234980   4885160    349820  94% /cdrom
/dev/loop0              624512    624512         0 100% /rofs
tmpfs                  1808104        12   1808092   1% /tmp
none                      5120         0      5120   0% /run/lock
none                   1808104         0   1808104   0% /run/shm
/dev/sdb1              8794976   3601712   5193264  41% /media/USB-DATA
/dev/sr1                  6828      6828         0 100% /media/U3 System
ubuntu@ubuntu:~$ [COLOR=RoyalBlue]sudo blkid[/COLOR]
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="USB-DATA" UUID="5921-6A05" TYPE="vfat" 
/dev/sdb2: LABEL="USB-OS" UUID="5939-AF2D" TYPE="vfat" 
/dev/sdb3: UUID="3379d9fb-860b-41c3-9102-2c36d5640f12" TYPE="swap" 
ubuntu@ubuntu:~$ [COLOR=RoyalBlue]ls -lha /cdrom[/COLOR]
total 4.1G
drwxr-xr-x 11 root root 4.0K 1970-01-01 00:00 .
drwxr-xr-x  1 root root  220 2011-12-18 10:50 ..
-rwxr-xr-x  1 root root  144 2011-10-12 18:04 autorun.inf
drwxr-xr-x  3 root root 4.0K 2011-12-16 21:07 boot
drwxr-xr-x  2 root root 4.0K 2011-12-16 22:59 casper
-rwxr-xr-x  1 root root 4.0G 2011-12-17 04:49 casper-rw
drwxr-xr-x  2 root root 4.0K 2011-12-16 21:07 .disk
drwxr-xr-x  3 root root 4.0K 2011-12-16 21:07 dists
drwxr-xr-x  2 root root 4.0K 2011-12-16 21:12 install
drwxr-xr-x  2 root root  12K 2011-12-16 21:12 isolinux
-r-xr-xr-x  1 root root  15K 2011-12-16 21:12 ldlinux.sys
-rwxr-xr-x  1 root root 5.6K 2011-10-12 18:04 md5sum.txt
drwxr-xr-x  2 root root 4.0K 2011-12-16 21:12 pics
drwxr-xr-x  6 root root 4.0K 2011-12-16 21:07 pool
drwxr-xr-x  2 root root 4.0K 2011-12-16 21:12 preseed
-rwxr-xr-x  1 root root  226 2011-10-12 18:04 README.diskdefines
-rwxr-xr-x  1 root root 1.3K 2011-12-16 21:35 syslinux.cfg
-rwxr-xr-x  1 root root 5.1K 2011-12-16 21:12 ubnfilel.txt
-rwxr-xr-x  1 root root  14M 2011-10-12 18:04 ubninit
-rwxr-xr-x  1 root root 4.5M 2011-10-12 18:04 ubnkern
-rwxr-xr-x  1 root root 1.2K 2011-12-16 21:07 ubnpathl.txt
-rwxr-xr-x  1 root root 142K 2011-12-16 21:13 vesamenu.c32
-rwxr-xr-x  1 root root 2.4M 2011-10-12 18:04 wubi.exe
```Finally I edited the file syslinux.cfg (the red test in two lines) to make the system use the casper-rw file.
```
ubuntu@ubuntu:~$  [COLOR=RoyalBlue]cat /cdrom/syslinux.cfg [/COLOR]
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default[COLOR=Red] Lubuntu 11.10 *persistent*[/COLOR]
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash [COLOR=Red]persistent[/COLOR] --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Lubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Lubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label ^Back..
kernel /ubnkern
append initrd=/ubninit 

label ubnentry7
menu label menu
kernel /isolinux/vesamenu.c32
append initrd=/ubninit 

label ubnentry8
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true

ubuntu@ubuntu:~$ 

```The mounted ***persistent*** file system:
```
ubuntu@ubuntu:~$ [COLOR=RoyalBlue]df[/COLOR]
Filesystem           1K-blocks      Used Available Use% Mounted on
/cow                   4127424    770640   3147120  20% /
udev                   1800772         4   1800768   1% /dev
tmpfs                   723244       852    722392   1% /run
/dev/sdb2              5234980   4885160    349820  94% /cdrom
/dev/loop0              624512    624512         0 100% /rofs
tmpfs                  1808104         4   1808100   1% /tmp
none                      5120         0      5120   0% /run/lock
none                   1808104         0   1808104   0% /run/shm
/dev/sdb1              8794976   3601776   5193200  41% /media/USB-DATA
/dev/sr1                  6828      6828         0 100% /media/U3 System
ubuntu@ubuntu:~$ 

```I have installed some favourite software and updated the system
```
sudo apt-get update
sudo apt-get upgrade
```and selected locale (language and keyboard).

It works quite well and it is truly portable :-)

---

