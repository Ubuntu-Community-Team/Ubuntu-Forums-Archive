---
title: "ubuntu 10.04 LTS upgrade problem"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by ivandarvin on 2010-09-27
Below is all I see on a black screen now. Cannot access ubuntu at all after upgrading and restart to ubuntu 10.04 LTS     My old ubuntu system is on a dedicated hard drive.   What do I need to do? ** I cannot enter my computer.**

   
  [COLOR=navy]Mount: mounting none on  /dev failed:  No such device udevd  [868]: error getting socket: invalid argument[/COLOR]
  
  [COLOR=navy]Error initializing netlink socket[/COLOR]
  [COLOR=navy]Udevd [868]: error initializing netlink socket[/COLOR]
  
  [COLOR=navy]Libudv:  udev_monitor_new_from_netlink: error getting socket:  Invalid argument[/COLOR]
  [COLOR=navy]Segmentation fault[/COLOR]
  [COLOR=navy]Gave up waiting for root device.   [/COLOR]
  
  [COLOR=navy]Common problems: [/COLOR]
  [COLOR=navy]Boot args  (cat  /proc/cmdline)  Check root delay= (did the system wait long enough?)  Check root=  (did the system wait for the right device?)[/COLOR]
  [COLOR=navy]Missing modules  (cat  /proc/modules; ls /dev)[/COLOR]
  [COLOR=navy]ALERT!  /dev/disk/by-uuid/16c2b2c3-6536-4f24-8eee-ac5b92b9b3de does not exist.  Dropping to a shell![/COLOR]
  
  [COLOR=navy]Busybox  v1.13.3  (ubuntu 1:1.13.3-1 ubuntu11  built in shell (ash)[/COLOR]
  
  [COLOR=navy]Enter &#8216;help&#8217; for a list of built-in commands.[/COLOR]
  
  [COLOR=navy](initramfs) _[/COLOR]

---

### Post by percyhahn on 2010-09-27
aaargh!!! i dont wanna see things like this, im updating as im typing [-o<

---

### Post by mörgæs on 2010-09-27
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by rbm0307 on 2010-09-27
Thanks for th pointer, morgaes,  

Unfortunately, as with the OP, I'm encountering similar upgrade errors after trying to move from 8.04LTS to 10.04LTS.  The system was operational before the upgrade except for Xorg occasionally pegging the CPU at 100% related to a linux kernel fix with which it disagreed.  After the upgrade (through the Upgrade tool), I encounter the following error at boot:
```
mount: mounting none on /dev failed: No such device
udevd[929]: error getting socket: Invalid argument

error initializing netlink socket
udevd[929]: error initializing netlink socket

libudev: udev_monitor_new_from_netlink:  error getting socket: Invalid argument
Segmentation fault
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
 - check rootdelay= (did the system wait long enough)
 - check root= (did the system wait for the right device?)
- missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a571e0e4-8835-4a1f-9845-11d58fdc687c does not exist. Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) builtin shell (ash)
Enter 'help' for a list of builtin commands.

(initramfs)

cat /proc/modules
raid10 26368 0 - Live 0xffffffff8806a000
raid456 131360 0 - Live 0xffffffff88048000
async_xor 6144 1 raid456, Live 0xffffffff8804500000-d000
async-memcpy 4608 1 raid456, Live 0xffffffff88042000
async-tx 10484 3 raid456,async_xor,async_memcpy, Live 0xffffffff8803e000
xor 7184 2 raid456,async_xor, Live 0xffffffff8803b000
raid1 26880 0 - Live 0xffffffff88033000
raid0 9472 0 - Live 0xffffffff8802f000
multipath 11008 0 - Live 0xffffffff8802b000
linear 7424 0 - Live 0xffffffff88028000
md_mod 88220 6 raid10,raid456,raid1,raid0,multipath,linear, Live 0xffffffff88011000
fuse 55984 1 - Live 0xffffffff88002000

ls /dev
console pts tty2 tty4 tty6
null tty1 tty3 tty5

cat /proc/cmdline
root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash


```
From this I gather I'm missing the proper modules to recognize my boot drive, a standard EIDE drive.  It recognizes my RAID array consisting of 6 SATA drives but not the boot disk.  Do I have the capability to install the missing modules if I drop into a standalone repair shell from the CD?  If so, how do I perform the recovery?

If I boot a recovery environment from CD, I am able to mount and see the boot drive.  everything seems to be intact at this point in time.

If recovery of this system is really difficult (my Ubuntu skills are moderate and questionable), and assuming I save all the important configuration files to USB drive, do I have to take special consideration for the RAID drive.  This is where my data lies and I don't want to loose it.  I am not adverse to rebuilding the system from scratch as suggested in the online guide just so long as I preserve the RAID contents.

Thanks in advance for any help.

---

### Post by garner_nc on 2010-09-27
Upgrading from 9.10 to 10.04 was no easy thing. I finally broke down and did a clean install. I'll never upgrade again. Doing a clean install was much more reliable and left my system without all the leftover baggage of previous versions. Sorry, I know this doesn't help now.

All the Best,
D. White

---

### Post by mörgæs on 2010-09-28
@rbm030: Sorry, I don't know anything of RAID.

---

### Post by rbm0307 on 2010-09-30
I've been doing some more research and experimenting.

1. Booted into Ubintu 10.04LTS LiveCD and ran the boot_info_script.sh.  These were the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    74,862,899    74,862,837  83 Linux
/dev/sdc2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdc5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   976,768,064   976,768,002  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 257 MB, 257949696 bytes
33 heads, 63 sectors/track, 242 cylinders, total 503808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  32       503,807       503,776   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        614a41ae-6136-9299-f04c-99b83fd94616   linux_raid_member                               
/dev/sda         63371503-dbb6-463f-ac99-ac6cb3187353   ext2                                     
/dev/sdb1        614a41ae-6136-9299-f04c-99b83fd94616   linux_raid_member                               
/dev/sdb         88fe4118-a087-48ff-843b-8a398a271e21   ext2                                     
/dev/sdc1        a571e0e4-8835-4a1f-9845-11d58fdc687c   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        1f9b24c9-45d6-4540-bf7f-c209d5aee2c9   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        614a41ae-6136-9299-f04c-99b83fd94616   linux_raid_member                               
/dev/sdd         243906bd-5bb2-40b4-a002-8cd673d30406   ext2                                     
/dev/sde1        614a41ae-6136-9299-f04c-99b83fd94616   linux_raid_member                               
/dev/sde         c1f3bc50-936a-4a05-9c24-263ee54eee37   ext2                                     
/dev/sdf1        684b905f-fe2e-4a74-99ff-25a1e583734e   xfs                                      
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        3040-A3CA                              vfat                                     
/dev/sdg: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/3040-A3CA         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-25-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-25-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-22-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-21-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 10.04.1 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1f9b24c9-45d6-4540-bf7f-c209d5aee2c9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/md0    /RAID    ext3    defaults    1    2

=================== sdc1: Location of files loaded by Grub: ===================


  16.9GB: boot/grub/menu.lst
  17.0GB: boot/grub/stage2
  16.9GB: boot/initrd.img-2.6.24-19-generic
  16.9GB: boot/initrd.img-2.6.24-19-generic.bak
  16.9GB: boot/initrd.img-2.6.24-21-generic
  16.9GB: boot/initrd.img-2.6.24-21-generic.bak
  17.0GB: boot/initrd.img-2.6.24-22-generic
  17.0GB: boot/initrd.img-2.6.24-22-generic.bak
  17.0GB: boot/initrd.img-2.6.24-23-generic
  16.9GB: boot/initrd.img-2.6.24-23-generic.bak
  17.0GB: boot/initrd.img-2.6.24-24-generic
  17.0GB: boot/initrd.img-2.6.24-24-generic.bak
  17.0GB: boot/initrd.img-2.6.24-25-generic
  17.0GB: boot/initrd.img-2.6.24-25-generic.bak
  17.0GB: boot/initrd.img-2.6.24-26-generic
  16.9GB: boot/initrd.img-2.6.24-26-generic.bak
  17.0GB: boot/initrd.img-2.6.24-27-generic
  17.0GB: boot/initrd.img-2.6.24-27-generic.bak
  16.9GB: boot/vmlinuz-2.6.24-19-generic
  16.9GB: boot/vmlinuz-2.6.24-21-generic
  17.0GB: boot/vmlinuz-2.6.24-22-generic
  16.9GB: boot/vmlinuz-2.6.24-23-generic
  17.0GB: boot/vmlinuz-2.6.24-24-generic
  17.0GB: boot/vmlinuz-2.6.24-25-generic
  16.9GB: boot/vmlinuz-2.6.24-26-generic
  16.9GB: boot/vmlinuz-2.6.24-27-generic
  17.0GB: initrd.img.old
  16.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  00 3d c0 03 01 3d c0 03  00 00 c0 03 fe 7e 00 20  |.=...=.......~. |
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  08 bd c0 03 09 bd c0 03  00 80 c0 03 fe 7e 00 20  |.............~. |
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  10 3d c1 03 11 3d c1 03  00 00 c1 03 fe 7e 00 20  |.=...=.......~. |
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  18 bd c1 03 19 bd c1 03  00 80 c1 03 fe 7e 00 20  |.............~. |
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  20 3d c2 03 21 3d c2 03  00 00 c2 03 fe 7e 00 20  | =..!=.......~. |
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  28 bd c2 03 29 bd c2 03  00 80 c2 03 fe 7e 00 20  |(...)........~. |
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  30 3d c3 03 31 3d c3 03  00 00 c3 03 fe 7e 00 20  |0=..1=.......~. |
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  38 bd c3 03 39 bd c3 03  00 80 c3 03 fe 7e 00 20  |8...9........~. |
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  40 3d c4 03 41 3d c4 03  00 00 c4 03 fe 7e 00 20  |@=..A=.......~. |
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  48 bd c4 03 49 bd c4 03  00 80 c4 03 fe 7e 00 20  |H...I........~. |
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  50 3d c5 03 51 3d c5 03  00 00 c5 03 fe 7e 00 20  |P=..Q=.......~. |
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  58 bd c5 03 59 bd c5 03  00 80 c5 03 fc 7e ff 1f  |X...Y........~..|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  60 3d c6 03 61 3d c6 03  00 00 c6 03 fe 7e 00 20  |`=..a=.......~. |
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  68 bd c6 03 69 bd c6 03  00 80 c6 03 00 17 d1 1f  |h...i...........|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  70 3d c7 03 71 3d c7 03  00 00 c7 03 d3 58 00 20  |p=..q=.......X. |
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  78 bd c7 03 79 bd c7 03  00 80 c7 03 fe 7e 00 20  |x...y........~. |
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdd1

00000000  00 7d c0 07 01 7d c0 07  00 00 c0 07 fe 7e 00 20  |.}...}.......~. |
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  08 fd c0 07 09 fd c0 07  00 80 c0 07 fe 7e 00 20  |.............~. |
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  10 7d c1 07 11 7d c1 07  00 00 c1 07 fe 7e 00 20  |.}...}.......~. |
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  18 fd c1 07 19 fd c1 07  00 80 c1 07 fe 7e 00 20  |.............~. |
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  20 7d c2 07 21 7d c2 07  00 00 c2 07 fe 7e 00 20  | }..!}.......~. |
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  28 fd c2 07 29 fd c2 07  00 80 c2 07 fe 7e 00 20  |(...)........~. |
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  30 7d c3 07 31 7d c3 07  00 00 c3 07 fe 7e 00 20  |0}..1}.......~. |
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  38 fd c3 07 39 fd c3 07  00 80 c3 07 fe 7e 00 20  |8...9........~. |
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  40 7d c4 07 41 7d c4 07  00 00 c4 07 fe 7e 00 20  |@}..A}.......~. |
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  48 fd c4 07 49 fd c4 07  00 80 c4 07 fe 7e 00 20  |H...I........~. |
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  50 7d c5 07 51 7d c5 07  00 00 c5 07 fe 7e 00 20  |P}..Q}.......~. |
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  58 fd c5 07 59 fd c5 07  00 80 c5 07 fe 7e 00 20  |X...Y........~. |
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  60 7d c6 07 61 7d c6 07  00 00 c6 07 fe 7e 00 20  |`}..a}.......~. |
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  68 fd c6 07 69 fd c6 07  00 80 c6 07 fe 7e 00 20  |h...i........~. |
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  70 7d c7 07 71 7d c7 07  00 00 c7 07 fe 7e 00 20  |p}..q}.......~. |
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  78 fd c7 07 79 fd c7 07  00 80 c7 07 fe 7e 00 20  |x...y........~. |
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sde1

00000000  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 40 00 04 00 40 00 04  00 00 00 04 02 00 ff 3f  |.@...@.........?|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 40 00 04 00 40 00 04  00 00 00 04 fe 69 d1 3f  |.@...@.......i.?|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 40 00 04 00 40 00 04  00 00 00 04 2d 26 00 00  |.@...@......-&..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 40 00 04 00 40 00 04  00 00 00 04 00 00 00 00  |.@...@..........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

```
Boot_info_script identifies the boot drive as sdc and correctly finds the missing UUID on sdc1, my former root partition.  What is weird is that sdc should be sda.

2. Rebooted the computer several time to try different kernels residing on the boot drve.  By holding the Shift key during grub2 booting, I got the kernek menu.  Selecting an earlier kernel got me further along.  The system still fails to load properly.  I was dropped into a maintenance shell where I could confirm the UUID of the boot drive.

What I noticed was that as a result of the upgrade from 8.04 to 10.04, the disks have been reordered on /dev.  What was /dev/sda in 8.04 is now /dev/sdf in 10.04.  This might account for Grub2 complaining about not being able to find the UUID for the root partition.  Examined the files in /boot/grub as well.  The file, device.map, maps (hd0) to /dev/sda.  As can be seen from grub.lst, the "root" statements for each of the bootable kernel images is refering to (hd0,0).  This is obviously wrong if /dev/sda is now /dev/sdf. 

 I have not gone so far as to re-install Grub2 as suggested by some poeple in other posts because I want to make sure I don't trash my RAID drive.

If any knowledgable people can chime in and give some advice at this point, I would really appreciate the help.  I am especially seeking confirmation that reloading Grub2 will be a relatively safe operation at this point.

TIA.

---

### Post by rbm0307 on 2010-10-04
I managed to solve my ubuntu problem detailed above.

The solution was to install the most current Linux kernel and rebuild grub.

Steps:
1. I discovered that legacy grub was installed and not updated to Grub2.  Booted the 10.04 64-bit server CD (the machine is an AMD64 processor) and ran "Repair a broken system".  Chose the option to select a partition and run a shell in that partition.  This caused the partition to be mounted to the root.
2. Installed Grub2 using apt-get.
3. Noticed that the linux-image being booted was also legacy 8.04 (linux-image-2.6.23). This needed to be updated.
4. After installing Grub2, I ran apt-get update, apt-get upgrade and apt-get dist-upgrade.  These commands updated tons of programs on the disk that had failed to upgrade previously.
5. Ran aptitude and selected linux-image-2.6.32 for installation.
6. After all this installation activity, I rebooted and low-and-behold, the system booted into server mode.

Whew!!!

This was not easy but luckily, all my data was intact as were the configurations of all the previous software.

Hope this helps others who might be caught in the same situation as was I.  Cheers.

---

### Post by mörgæs on 2010-10-04
Good. Please mark the thread 'solved' in the 'thread tools' menu.

---

### Post by rbm0307 on 2010-10-04
I would have marked the thread solved but, since I'm not the Original Poster, it is not my place to do so.  I solved my problem but not theirs.  My solution is a guide for the OP to try.  If my solution works for him/her, then the OP can update the subject.

---

### Post by mörgæs on 2010-10-04
Sorry, I didn't notice that.

---

