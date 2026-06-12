---
title: "GRUB Error 17 on multi drive install"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by jgemelli on 2008-09-28
I have been playing with this for a while but am pressed for time.

I have read other threads like this to no avail.  

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6649a872

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24790   199125643+  83  Linux

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b3a0f85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2811    22579326   83  Linux
/dev/sdc3            2812        2940     1036192+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sdc4            2941        9963    56412247+  83  Linux
Partition 4 does not end on cylinder boundary.

Disk /dev/sdd: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004dfec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9732    78172258+  83  Linux

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d38e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       30024   241167748+  83  Linux
/dev/sde2           30025       30401     3028252+   5  Extended
/dev/sde5           30025       30401     3028221   82  Linux swap / Solaris
```

The installation wend to the 80GB drive sdd1 so mount and check grub below

```
ubuntu@ubuntu:~$ sudo mount /dev/sdd1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=45192d44-744b-4fac-8941-12feafee9923 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=45192d44-744b-4fac-8941-12feafee9923 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=45192d44-744b-4fac-8941-12feafee9923 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sde1)

initrd		/boot/initrd.img-2.6.22-15-generic
# This entry automatically added by the Debian installer for an existing
boot
ubuntu@ubuntu:~$ 

```

This machine has 5 drives and 1 DVD.  I made sure that the OS is not on the raid card so I can boot from it.  I have checked to see that the 80GB drive is set to boot in the bios.

Any ideas?

Thanks!

---

### Post by jgemelli on 2008-09-28
Oh I forgot to mention GRUB is less than happy

```
grub> find /boot/grub/stage1

Error 15: File not found


```

---

### Post by unutbu on 2008-09-28
Boot from the LiveCD.
Open a terminal and type
```

sudo mount /dev/sdd1 /mnt
ls -l /mnt/boot
ls -l /mnt/boot/grub
```

Please post the output.

---

### Post by jgemelli on 2008-09-28
sdd1 was already mounted I show this below with the mount command

```
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 17616
-rw-r--r-- 1 root root  422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x 2 root root    4096 2008-09-28 15:33 grub
-rw-r--r-- 1 root root 7490184 2008-09-28 06:54 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7055536 2008-09-28 06:25 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic
ubuntu@ubuntu:~$ ls -l /mnt/boot/grub
total 196
-rw-r--r-- 1 root root    197 2008-09-28 06:54 default
-rw-r--r-- 1 root root     75 2008-09-28 06:54 device.map
-rw-r--r-- 1 root root   8056 2008-09-28 06:54 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-09-28 06:54 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-09-28 06:54 installed-version
-rw-r--r-- 1 root root   8608 2008-09-28 06:54 jfs_stage1_5
-rw-r--r-- 1 root root   4687 2008-09-28 15:33 menu.lst
-rw-r--r-- 1 root root   7324 2008-09-28 06:54 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-09-28 06:54 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-09-28 06:54 stage1
-rw-r--r-- 1 root root 108356 2008-09-28 06:54 stage2
-rw-r--r-- 1 root root   9276 2008-09-28 06:54 xfs_stage1_5
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /mnt type ext3 (rw)

```

---

### Post by unutbu on 2008-09-28
Ok, let's try this:

```
sudo grub
```
At the grub> prompt type
```

geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
geometry (hd4)
```

Please post the output.

By the way, when you try to boot normally, which drive have you set in the BIOS to boot first?

---

### Post by jgemelli on 2008-09-28
Thanks for the help see below.

```
grub> geometry (hd0)
drive 0x80: C/H/S = 25665/255/63, The number of sectors = 1465149168, /dev/sda

grub> geometry (hd1)
drive 0x81: C/H/S = 24792/255/63, The number of sectors = 398297088, /dev/sdb
   Partition num: 0,  Filesystem type is reiserfs, partition type 0x83

grub> geometry (hd2)
drive 0x82: C/H/S = 9964/255/63, The number of sectors = 160086528, /dev/sdc
   Partition num: 0,  Filesystem type is reiserfs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82
   Partition num: 3,  Filesystem type is reiserfs, partition type 0x83

grub> geometry (hd3)
drive 0x83: C/H/S = 9733/255/63, The number of sectors = 156368016, /dev/sdd
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83

grub> geometry (hd4)
drive 0x84: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sde
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> 

```

Oh and the bios only has the choice of the 250GB and the 80GB drive the 80GB seagate is the selected boot drive.

---

### Post by caljohnsmith on 2008-09-28
Jgemelli, so when you get the Grub error 17, is it before you get a Grub menu, or after you get the Grub menu and select Ubuntu? If it is after selecting Ubuntu, then you need to modify your Grub's menu.lst. So from the Live CD, while sdd1 is mounted on /mnt, do:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And change the #groot line to:
```
#groot=(hd0,0)
```
And also change all the Ubuntu entries to use (hd0,0) instead of (hd3,0). Save, reboot, and let us know what happens.

---

### Post by jgemelli on 2008-09-28
The problem comes up before I get to choose an OS.  I did try that hd0.0 change but it didn't help which makes sense.  It appears grub never has a chance to load anything.  

I am now re-checking my drive configuration and will let you know what happens.

Thanks

---

### Post by caljohnsmith on 2008-09-28
OK, it sounds like you need to at least reinstall Grub to the MBR of your 80 GB sdd drive, and make sure Grub points to the correct partition for its system files; this could be the reason you are getting the Grub error before even seeing a Grub menu.

From the Live CD:
```
sudo grub
grub> find /boot/grub/stage1

```
The above command should return your Ubuntu partition as (hd3,0), if it does then proceed with that:
```

grub> root (hd3,0)
grub> setup (hd3)
grub> quit
```
Reboot, and let us know exactly what happens on start up.

---

### Post by jgemelli on 2008-09-28
found interesting issue with that

```
grub> find /boot/grub/stage1
 (hd3,0)
 (hd4,0)

grub> setup (hd3)

Error 12: Invalid device requested

grub> setup (hd3,0)

Error 12: Invalid device requested

grub> 


```

---

### Post by unutbu on 2008-09-28
jgemelli, did you run
```

root (hd3,0)
```

before 
```

setup (hd3)

```
?

---

