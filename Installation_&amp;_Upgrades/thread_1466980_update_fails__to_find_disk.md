---
title: "update fails  to find disk"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2010-04-30
after the update , a reboot fails to find  the correct HD although it finds the grub menu.FWIW it boots into Windows
 
ive booted into a liveCD and mount /dev/sdb1 to get access to menu.1st

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00077c8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

this is the menu.1st its constructed 

title           Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid            b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel          /boot/vmlinuz-2.6.32-21-generic root=UUID=b19d7391-b6d5-468e-87$
initrd          /boot/initrd.img-2.6.32-21-generic
quiet

title           Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid            b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel          /boot/vmlinuz-2.6.32-21-generic root=UUID=b19d7391-b6d5-468e-87$
initrd          /boot/initrd.img-2.6.32-21-generic

title           Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid            b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=b19d7391-b6d5-468e-87$
initrd          /boot/initrd.img-2.6.31-20-generic
quiet

title           Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid            b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=b19d7391-b6d5-468e-87$
initrd          /boot/initrd.img-2.6.31-20-generic

title           Ubuntu 10.04 LTS, memtest86+
uuid            b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1

 which ive changed to 

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
root 		(hd1,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
root 		(hd1,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1  ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

 and it still fails

---

### Post by pdc124 on 2010-05-03
this is really messed up , i think 
 
ls  + tab completion gives the files on the disk, so  I can navigate to /boot  ( and other directories)  

its booting to  grub . Im not sure if the various grub config utilities will  improve things or not

I can list and cat  the files but there is no obvious editor 
 
so do i need to rewrite the whole of grub ( if so , how ?)
If I go into the grub  editor, add a line root (hd1,1) and then hit 'b' (boot)
it comes up with a root (hd1,0) uuid........

so i cant see how to tell it to boot from  hd1,1 ( on the new numbering)
i ve also tried booting into th grub command line and tried  grub-mkconfig ( according to GRUB2) but its an Error27 : unrecognized command.


So the only thing i can get to is the windows disk

bit of a mess really.

---

### Post by pdc124 on 2010-05-03
so i can boot into a liveCD and mount /dev/sdb1 on /mnt/sdb1

Ive got 

root@ubuntu:/mnt/sdb1/boot/grub# ls -la
total 232
drwxr-xr-x 2 root root   4096 2010-04-30 15:16 .
drwxr-xr-x 3 root root   4096 2010-04-30 15:18 ..
-rw-r--r-- 1 root root    197 2009-08-12 07:27 default
-rw-r--r-- 1 root root     30 2009-08-12 07:27 device.map
-rw-r--r-- 1 root root   8288 2009-08-12 07:27 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-08-12 07:27 fat_stage1_5
-rw-r--r-- 1 root root   1024 2010-04-30 13:58 grubenv
-rw-r--r-- 1 root root     16 2009-08-12 07:27 installed-version
-rw-r--r-- 1 root root   8712 2009-08-12 07:27 jfs_stage1_5
-rw-r--r-- 1 root root   5470 2010-05-02 14:10 menu.lst
-rw-r--r-- 1 root root   5872 2010-04-30 15:16 menu.lst~
-rw-r--r-- 1 root root   7352 2009-08-12 07:27 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-08-12 07:27 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-08-12 07:27 stage1
-rw-r--r-- 1 root root 121740 2009-08-12 07:27 stage2
-rw-r--r-- 1 root root   9556 2009-08-12 07:27 xfs_stage1_5
root@ubuntu:/mnt/sdb1/boot/grub# 

no grub.cfg 

Ive looked at [http://grub.enbug.org/Manual#GrubShell](http://grub.enbug.org/Manual#GrubShell)

I haven't got /etc/default/grub 

hmmmmm

---

### Post by frantid on 2010-05-03
you have grub-legacy installed not grub2.  Which do you want to keep?

---

### Post by pdc124 on 2010-05-03
whichever gives me a working system the soonest !

---

### Post by frantid on 2010-05-03
can you try this one line at a time in your grub.i.e. get to the command prompt in grub

root 		(hd1,0)
kernel		/boot/vmlinuz-2.6.32-21-generic  root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
boot

If it complains about file not found, try it without the "/boot"

---

### Post by pdc124 on 2010-05-04
i could boot form the grub command line utility 
using the autocomplete , grub finds (hda1,0)

usign the autocomplete the kernel option kernel 2.6.31-20-generic  is th only one that is found 
So if I use that, I can start it up 
if i reboot and choose this option from the grub menu, it boots .

So what are the files  listed as .......2.6.31-21-generic
grub doesn't identify them on autocompletion..

---

### Post by frantid on 2010-05-04
did it really list it as (hda1,0) ?

those are supposed to be older kernels and initrd.img.  Do they actually exist, can you see them in nautilus?  If not it's just old entries in your menu.lst

---

### Post by pdc124 on 2010-05-04
oops (hd1,0)

paul@zimmy-desktop:/boot$ ls -la
total 27984
drwxr-xr-x  3 root root    4096 2010-04-30 16:18 .
drwxr-xr-x 23 root root    4096 2010-05-04 16:26 ..
-rw-r--r--  1 root root  629742 2010-03-12 08:35 abi-2.6.31-20-generic
-rw-r--r--  1 root root  640617 2010-04-16 14:01 abi-2.6.32-21-generic
-rw-r--r--  1 root root  111382 2010-03-12 08:35 config-2.6.31-20-generic
-rw-r--r--  1 root root  115847 2010-04-16 14:01 config-2.6.32-21-generic
drwxr-xr-x  2 root root    4096 2010-04-30 16:16 grub
-rw-r--r--  1 root root 7646362 2010-04-30 07:35 initrd.img-2.6.31-20-generic
-rw-r--r--  1 root root 7970701 2010-04-30 16:18 initrd.img-2.6.32-21-generic
-rw-r--r--  1 root root  160280 2010-03-23 09:37 memtest86+.bin
-rw-r--r--  1 root root 1666793 2010-03-12 08:35 System.map-2.6.31-20-generic
-rw-r--r--  1 root root 1687378 2010-04-16 14:01 System.map-2.6.32-21-generic
-rw-r--r--  1 root root    1196 2010-03-12 08:37 vmcoreinfo-2.6.31-20-generic
-rw-r--r--  1 root root    1196 2010-04-16 14:03 vmcoreinfo-2.6.32-21-generic
-rw-r--r--  1 root root 3898528 2010-03-12 08:35 vmlinuz-2.6.31-20-generic
-rw-r--r--  1 root root 4029792 2010-04-16 14:01 vmlinuz-2.6.32-21-generic
paul@zimmy-desktop:/boot$ 

paul@zimmy-desktop:/boot$ uname -a 
Linux zimmy-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
paul@zimmy-desktop:/boot$

---

### Post by kansasnoob on 2010-05-04
We really need to see the full output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by frantid on 2010-05-04
have you tried fsck

---

### Post by pdc124 on 2010-05-04
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20015856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,000,924    20,000,862   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    74,862,899    74,862,837  83 Linux
/dev/sdb2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdb5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CCC0CEDCC0CB35E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b19d7391-b6d5-468e-87b9-634b6f16e46e   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        841f00c1-7ca1-4efc-8ad0-778d00d57000   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b19d7391-b6d5-468e-87b9-634b6f16e46e

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
root 		(hd1,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1  ro quiet splash 
#kernel         /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1  ro quiet splash

initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=841f00c1-7ca1-4efc-8ad0-778d00d57000 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  13.9GB: boot/grub/menu.lst
  13.9GB: boot/grub/stage2
  26.7GB: boot/initrd.img-2.6.31-20-generic
  14.6GB: boot/initrd.img-2.6.32-21-generic
  14.5GB: boot/vmlinuz-2.6.31-20-generic
  30.8GB: boot/vmlinuz-2.6.32-21-generic
  14.6GB: initrd.img
  26.7GB: initrd.img.old
  30.8GB: vmlinuz
  14.5GB: vmlinuz.old

---

### Post by frantid on 2010-05-04
since the 2.6.31-20 works for you.  I would go into synaptics reapply the 2.6.32-21 kernel packages.

On my clean install I don't have the older kernel that you are booting off of..

---

### Post by kansasnoob on 2010-05-05
I'm curious how this ended up?

I don't see much wrong with the menu.lst other than the edits you've made. I agree with Frantid about reinstalling the 2.6.32-21 kernel packages using Synaptic.

Since you've messed with the menu.lst I'd just boot into the older kernel, reinstall the updates, then I'd generate a new menu.lst by renaming/moving the old one:

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst_OLD
```

Then update grub:

```
sudo update-grub
```

Don't worry about the new grub2 differences, you don't even have it installed.

---

### Post by pdc124 on 2010-05-14
Ive removed and re-written menu.1st  - and its missed off my windows disk 


## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b19d7391-b6d5-468e-87b9-634b6f16e46e ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
paul@zimmy-desktop:~$ 


the only kernel I can boot into is 2.6.31-20-generic  
for the other2 , I recovery mode  i get 
"giving up waiting for root device common problems: 34b6f162462e"
in recovery mode it 
says 
"ata2:link is slow to respond
SRST failed errno=-16"

several times and then drops to the busybox shell.

in 2.6.31-20-generic  recovery mode i get the same message but it seems to wait a bit longer and then start up

---

### Post by pdc124 on 2010-05-20
it still wont boot into the kernels  > 2.6.31-20-generic
Ive tried adding rootdelay , but the kernel  still wont  start. 


title           Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid            b19d7391-b6d5-468e-87b9-634b6f16e46e
kernel          /boot/vmlinuz-2.6.32-22-generic root=UUID=b19d7391-b6d5-468e-87b
9-634b6f16e46e ro quiet splash 
rootdelay=40
initrd          /boot/initrd.img-2.6.32-22-generic
quiet


but I can still  boot into  2.6.31-20-generic

so am I consigned to using this kernel for ever ?

---

