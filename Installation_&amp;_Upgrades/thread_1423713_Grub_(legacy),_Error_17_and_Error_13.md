---
title: "Grub (legacy), Error 17 and Error 13"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by 61811 on 2010-03-07
Background:
Two HDDs.
1) Ubuntu 8.x.x
2) WinXP
Replaced #2 drive since it crashed. Grub menu disappeared. Was able to bring it back after reading a lot of threads.

Problem:
(a) Grub menu appears but the links don't work. Errors mentioned above.
(b) Not able to get to original Ubuntu on HDD; only the one on LiveCD. However, able to mount both drives via LiveCD.

Here's the output of the BootInfoScript:

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   152,296,199   152,296,137  83 Linux
/dev/sda2    *    152,296,200   156,296,384     4,000,185  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        521abcab-1fa3-45ba-8c4a-89ee1d0d71c9   ext3                                     
/dev/sda2        ca87a5ff-37af-4336-870e-714834c7c461   swap                                     
/dev/sdb1                                               ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/bus/usb     /proc/bus/usb            none       (rw,bind)
/dev/sdb1        /media/disk              ntfs       (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1        /media/disk-1            ext3       (rw,noexec,nosuid,nodev)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-020D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=3814E9EF14E9AFD4 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=ca87a5ff-37af-4336-870e-714834c7c461 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.9GB: boot/grub/menu.lst
  47.8GB: boot/grub/stage2
  47.8GB: boot/initrd.img-2.6.20-16-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic.bak
  47.9GB: boot/initrd.img-2.6.24-16-generic
  47.7GB: boot/initrd.img-2.6.24-16-generic.bak
  47.8GB: boot/initrd.img-2.6.24-17-generic
  47.8GB: boot/initrd.img-2.6.24-17-generic.bak
  47.8GB: boot/initrd.img-2.6.24-18-generic
  47.8GB: boot/initrd.img-2.6.24-18-generic.bak
  47.9GB: boot/initrd.img-2.6.24-19-generic
  47.8GB: boot/initrd.img-2.6.24-19-generic.bak
  47.9GB: boot/initrd.img-2.6.24-21-generic
  47.9GB: boot/initrd.img-2.6.24-21-generic.bak
  47.9GB: boot/initrd.img-2.6.24-22-generic
  47.8GB: boot/initrd.img-2.6.24-22-generic.bak
  47.9GB: boot/initrd.img-2.6.24-23-generic
  47.9GB: boot/initrd.img-2.6.24-23-generic.bak
  47.9GB: boot/initrd.img-2.6.24-24-generic
  47.9GB: boot/initrd.img-2.6.24-24-generic.bak
  47.9GB: boot/initrd.img-2.6.24-25-generic
  47.9GB: boot/initrd.img-2.6.24-25-generic.bak
  54.1GB: boot/initrd.img-2.6.24-26-generic
  54.1GB: boot/initrd.img-2.6.24-26-generic.bak
  54.1GB: boot/initrd.img-2.6.24-27-generic
  54.2GB: boot/initrd.img-2.6.24-27-generic.bak
  47.8GB: boot/vmlinuz-2.6.20-16-generic
  47.8GB: boot/vmlinuz-2.6.22-14-generic
  47.8GB: boot/vmlinuz-2.6.24-16-generic
  47.8GB: boot/vmlinuz-2.6.24-17-generic
  47.8GB: boot/vmlinuz-2.6.24-18-generic
  47.7GB: boot/vmlinuz-2.6.24-19-generic
  47.7GB: boot/vmlinuz-2.6.24-21-generic
  47.7GB: boot/vmlinuz-2.6.24-22-generic
  47.9GB: boot/vmlinuz-2.6.24-23-generic
  54.0GB: boot/vmlinuz-2.6.24-24-generic
  47.9GB: boot/vmlinuz-2.6.24-25-generic
  47.9GB: boot/vmlinuz-2.6.24-26-generic
  54.2GB: boot/vmlinuz-2.6.24-27-generic
  54.1GB: initrd.img
  54.1GB: initrd.img.old
  54.2GB: vmlinuz
  47.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


================================ sdb1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


```


One thing that is confusing is that it indicates that Grub is in Partition 1 of sda; however, Drive Info indicates that sda2 is the boot partition. My knowledge is almost non-existent on Linux, so I may be wrong.

Please help!!

Thank you.

---

### Post by 61811 on 2010-03-07
Please help!!

Am not able to get into my HDD Ubuntu installation even though everything is intact there. The faulty GRUB is preventing me from doing so.

Some clarity:

* When trying to start Ubuntu from Grub, the fwg msg appears:
Error 17: Cannot mount selected partition 

* When trying to start WinXP from Grub, the fwg msg appears:
Error 13: Invalid or unsupported exectutable format

I am able to bypass the first HDD via BIOS and boot WinXP off the second HDD. However, cannot get to Ubuntu on the first HDD with both drives enabled.

Thank you.

---

### Post by cusinndzl on 2010-03-07
If I remember correctly error 17 is when the boot loader is not found or damaged. Reinstall GRUB to fix it.

---

### Post by oldfred on 2010-03-07
It looks like old grub did not see the windows on the second drive. This is one place where grub2 is better.

You need to add map commands as windows is on the second drive when booting thru grub and grub had to make windows think it is drive 0.

title        Microsoft Windows XP 
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

Be sure to follow the directions for installing grub legacy not grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Linux does not use the boot flag and some BIOS require a boot flag just to let the system boot. I would move the flag but it probably is not critical.

set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda

---

### Post by 61811 on 2010-03-07
Thank you for your prompt responses. Unfortunately, I am not good at Linux commands in the Terminal. Haven't used it in years. Request you to provide me directions assuming I am a newbie.

For example, to edit menu.lst in /boot/grub of sda1 to incorporate

title Microsoft Windows XP
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

I have forgotten how to change permission to be able to edit that file. I am operating off LiveCD, and when I try to Copy, Save As, etc. using GUI, "permission denied" message comes up.

Please also note that my 2nd HDD with WinXP has only one partition.

Preference:
(1) Try to get GRUB working;
(2) If that doesn't happen, remove GRUB, and be able to boot Ubuntu directly off my 1st HDD. (I rarely use my WinXP on the 2nd HDD; hence, I can disable 1st HDD in BIOS, thereby bypassing Ubuntu when I want to go straight to WinXP).

Please provide step-by-step instructions. Appreciate any help that can be provided.

Thank you!

---

### Post by oldfred on 2010-03-07
You may be working of the liveCd copies that you cannot edit. You have to mount the partition and add the mount to the commands. It would be easier to first repair your grub so you can boot into Ubuntu then repair the windows entry from the working Ubuntu.

This should be the same as the link to reinstall grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot from live CD
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,0)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,0)
setup (hd0)
quit

---

### Post by 61811 on 2010-03-07
oldfred, thank you for your patience and assistance.

I have already tried that twice:
sudo grub
find /boot/grub/stage1
root (hd0,0) [that's the result of find]
setup (hd0)
quit

Everything works like a charm in that SETUP command.

However, on rebooting w/o LiveCD, get the same menu as before and same broken link (i.e. Error 17 when trying to start Ubuntu off the HDD).

What should I try next?

Thank you.

---

### Post by 61811 on 2010-03-07
* Booted from LiveCD.
* Edited menu.lst per Msg #4 using *sudo nano*.
* Tried rebooting w/o LiveCD.
* Errors 17 and 11
[INDENT]* Error 17 on trying Ubuntu in the Menu ("Cannot mount selected partition").
* Error 11 on trying WinXP in the Menu ("Unrecognized device string").[/INDENT]

Is something wrong with this? (Why does it give "Unrecognized device string" error?)
[I]title Microsoft Windows XP
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/I]

Why doesn't anything need to be changed here? 
[I]title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
[/I]

---

### Post by 61811 on 2010-03-07
I have not been successful yet in solving this issue - please help!!

Cleaned up menu.lst somewhat. Here's the output of *bootloadscript*:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 93424863 
    of the same hard drive for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #1 for /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   152,296,199   152,296,137  83 Linux
/dev/sda2    *    152,296,200   156,296,384     4,000,185  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        521abcab-1fa3-45ba-8c4a-89ee1d0d71c9   ext3                                     
/dev/sda2        ca87a5ff-37af-4336-870e-714834c7c461   swap                                     
/dev/sdb1                                               ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/bus/usb     /proc/bus/usb            none       (rw,bind)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

[COLOR="DarkOrchid"]title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin[/COLOR]
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
[COLOR="DarkOrchid"]title		Microsoft Windows XP Home Edition
root    	(hd0,1)
savedefault
makeactive
chainloader	+1[/COLOR]


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-020D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=3814E9EF14E9AFD4 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=ca87a5ff-37af-4336-870e-714834c7c461 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.8GB: boot/grub/menu.lst
  47.8GB: boot/grub/stage2
  47.8GB: boot/initrd.img-2.6.20-16-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic.bak
  47.9GB: boot/initrd.img-2.6.24-16-generic
  47.7GB: boot/initrd.img-2.6.24-16-generic.bak
  47.8GB: boot/initrd.img-2.6.24-17-generic
  47.8GB: boot/initrd.img-2.6.24-17-generic.bak
  47.8GB: boot/initrd.img-2.6.24-18-generic
  47.8GB: boot/initrd.img-2.6.24-18-generic.bak
  47.9GB: boot/initrd.img-2.6.24-19-generic
  47.8GB: boot/initrd.img-2.6.24-19-generic.bak
  47.9GB: boot/initrd.img-2.6.24-21-generic
  47.9GB: boot/initrd.img-2.6.24-21-generic.bak
  47.9GB: boot/initrd.img-2.6.24-22-generic
  47.8GB: boot/initrd.img-2.6.24-22-generic.bak
  47.9GB: boot/initrd.img-2.6.24-23-generic
  47.9GB: boot/initrd.img-2.6.24-23-generic.bak
  47.9GB: boot/initrd.img-2.6.24-24-generic
  47.9GB: boot/initrd.img-2.6.24-24-generic.bak
  47.9GB: boot/initrd.img-2.6.24-25-generic
  47.9GB: boot/initrd.img-2.6.24-25-generic.bak
  54.1GB: boot/initrd.img-2.6.24-26-generic
  54.1GB: boot/initrd.img-2.6.24-26-generic.bak
  54.1GB: boot/initrd.img-2.6.24-27-generic
  54.2GB: boot/initrd.img-2.6.24-27-generic.bak
  47.8GB: boot/vmlinuz-2.6.20-16-generic
  47.8GB: boot/vmlinuz-2.6.22-14-generic
  47.8GB: boot/vmlinuz-2.6.24-16-generic
  47.8GB: boot/vmlinuz-2.6.24-17-generic
  47.8GB: boot/vmlinuz-2.6.24-18-generic
  47.7GB: boot/vmlinuz-2.6.24-19-generic
  47.7GB: boot/vmlinuz-2.6.24-21-generic
  47.7GB: boot/vmlinuz-2.6.24-22-generic
  47.9GB: boot/vmlinuz-2.6.24-23-generic
  54.0GB: boot/vmlinuz-2.6.24-24-generic
  47.9GB: boot/vmlinuz-2.6.24-25-generic
  47.9GB: boot/vmlinuz-2.6.24-26-generic
  54.2GB: boot/vmlinuz-2.6.24-27-generic
  54.1GB: initrd.img
  54.1GB: initrd.img.old
  54.2GB: vmlinuz
  47.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


================================ sdb1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

```

Logically, to my untrained eyes, the pointers to Ubuntu and Linux are swapped in the menu.lst file.

Thank you.

---

### Post by confused57 on 2010-03-07
Have you tried going into your bios and setting your HD with Windows as your 1st hard drive booted?  If this doesn't work, then you might try installing grub to (hd1), instead of (hd0):
root (hd0,0)
setup (hd1)

---

### Post by 61811 on 2010-03-07
_Response to #10_

I do not have the option in my BIOS to switch boot sequence between the same kind of (HD SATA) drives.

I tried your suggestion:
root (hd0,0)
setup (hd1)
Didn't resolve the issue.

Here's the output of *biosinfoscript*:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 93424863 
    of the same hard drive for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #1 for /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 93424863 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #1 for /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   152,296,199   152,296,137  83 Linux
/dev/sda2    *    152,296,200   156,296,384     4,000,185  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        521abcab-1fa3-45ba-8c4a-89ee1d0d71c9   ext3                                     
/dev/sda2        ca87a5ff-37af-4336-870e-714834c7c461   swap                                     
/dev/sdb1                                               ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/bus/usb     /proc/bus/usb            none       (rw,bind)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root    	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-020D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=3814E9EF14E9AFD4 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=ca87a5ff-37af-4336-870e-714834c7c461 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.8GB: boot/grub/menu.lst
  47.8GB: boot/grub/stage2
  47.8GB: boot/initrd.img-2.6.20-16-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic.bak
  47.9GB: boot/initrd.img-2.6.24-16-generic
  47.7GB: boot/initrd.img-2.6.24-16-generic.bak
  47.8GB: boot/initrd.img-2.6.24-17-generic
  47.8GB: boot/initrd.img-2.6.24-17-generic.bak
  47.8GB: boot/initrd.img-2.6.24-18-generic
  47.8GB: boot/initrd.img-2.6.24-18-generic.bak
  47.9GB: boot/initrd.img-2.6.24-19-generic
  47.8GB: boot/initrd.img-2.6.24-19-generic.bak
  47.9GB: boot/initrd.img-2.6.24-21-generic
  47.9GB: boot/initrd.img-2.6.24-21-generic.bak
  47.9GB: boot/initrd.img-2.6.24-22-generic
  47.8GB: boot/initrd.img-2.6.24-22-generic.bak
  47.9GB: boot/initrd.img-2.6.24-23-generic
  47.9GB: boot/initrd.img-2.6.24-23-generic.bak
  47.9GB: boot/initrd.img-2.6.24-24-generic
  47.9GB: boot/initrd.img-2.6.24-24-generic.bak
  47.9GB: boot/initrd.img-2.6.24-25-generic
  47.9GB: boot/initrd.img-2.6.24-25-generic.bak
  54.1GB: boot/initrd.img-2.6.24-26-generic
  54.1GB: boot/initrd.img-2.6.24-26-generic.bak
  54.1GB: boot/initrd.img-2.6.24-27-generic
  54.2GB: boot/initrd.img-2.6.24-27-generic.bak
  47.8GB: boot/vmlinuz-2.6.20-16-generic
  47.8GB: boot/vmlinuz-2.6.22-14-generic
  47.8GB: boot/vmlinuz-2.6.24-16-generic
  47.8GB: boot/vmlinuz-2.6.24-17-generic
  47.8GB: boot/vmlinuz-2.6.24-18-generic
  47.7GB: boot/vmlinuz-2.6.24-19-generic
  47.7GB: boot/vmlinuz-2.6.24-21-generic
  47.7GB: boot/vmlinuz-2.6.24-22-generic
  47.9GB: boot/vmlinuz-2.6.24-23-generic
  54.0GB: boot/vmlinuz-2.6.24-24-generic
  47.9GB: boot/vmlinuz-2.6.24-25-generic
  47.9GB: boot/vmlinuz-2.6.24-26-generic
  54.2GB: boot/vmlinuz-2.6.24-27-generic
  54.1GB: initrd.img
  54.1GB: initrd.img.old
  54.2GB: vmlinuz
  47.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


================================ sdb1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

```

Thank you.

---

### Post by 61811 on 2010-03-08
root (hd0,0)
setup (hd1)

These commands installed Grub 0.97 in the MBR of /dev/sdb, which is my 2nd HDD with WinXP.

Till now I was able to boot off the 2nd HDD into WinXP, by disabling HDD1 in BIOS.

Now WinXP cannot be booted.

Can I revert back one step; i.e. remove GRUB from sdb (WinXP drive)? Or, has that partition been screwed up and the only way is to install WinXP again?

Thank you.

---

### Post by oldfred on 2010-03-08
You can just reinstall  a windows boot loader to the MBR of sdb. I did not notice all your entries in menu.lst refer to hd(1,0) but drive is sda. Did you switch drive order master/slave or order plugged into SATA ports? It seems virtually all entries are reversed. 

I would try changing one entry to see if it works.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd1,0)

to
root       (hd0,0)

and boot from that entry:
If it works you can change all the entires or create a total new menu.lst and see if that works.

Also list this, did these entries get reversed?
cat /boot/grub/device.map

---

### Post by 61811 on 2010-03-08
Hello oldfred:

One major issue is resolved - thank you!!

I knew that the (hdX,Y) entries in menu.lst weren't right, and had tried swapping them. Mistakenly, instead of (hd0,0) I had used (hd0,1). With (hd0,0) Ubuntu is now booting perfectly via the GRUB menu.

Now to WinXP on the 2nd drive. Since I had lost boot capability yesterday while experimenting, I used Windows Recovery Console off the Windows CD and tried *fixmbr* and *fixboot*. Neither worked. Finally, SGD came to the rescue and fixed the Window boot loader. However, that works fine as long as the first drive is Off in the BIOS. If both drives are On, then Ubuntu now boots fine off the 1st drive, but WinXP still gives Error 15.

Here's the output of *cat /boot/grub/device.map*:

```
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Here's the latest *boot info script* result. Note that I have changed Windows root below to:
* title		Microsoft Windows XP Home Edition
* root    	[COLOR="Blue"](hd1,0)[/COLOR]
However, this doesn't work.

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 93424863 
    of the same hard drive for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #1 for /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004ba54

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   152,296,199   152,296,137  83 Linux
/dev/sda2    *    152,296,200   156,296,384     4,000,185  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e912e90

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        521abcab-1fa3-45ba-8c4a-89ee1d0d71c9   ext3                                     
/dev/sda2        ca87a5ff-37af-4336-870e-714834c7c461   swap                                     
/dev/sdb1        6ED40E47D40E11CF                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro)
/dev/sdb1        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root    	(hd1,0)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=521abcab-1fa3-45ba-8c4a-89ee1d0d71c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-020D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=3814E9EF14E9AFD4 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=ca87a5ff-37af-4336-870e-714834c7c461 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.8GB: boot/grub/menu.lst
  47.8GB: boot/grub/stage2
  47.8GB: boot/initrd.img-2.6.20-16-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic
  47.8GB: boot/initrd.img-2.6.22-14-generic.bak
  47.9GB: boot/initrd.img-2.6.24-16-generic
  47.7GB: boot/initrd.img-2.6.24-16-generic.bak
  47.8GB: boot/initrd.img-2.6.24-17-generic
  47.8GB: boot/initrd.img-2.6.24-17-generic.bak
  47.8GB: boot/initrd.img-2.6.24-18-generic
  47.8GB: boot/initrd.img-2.6.24-18-generic.bak
  47.9GB: boot/initrd.img-2.6.24-19-generic
  47.8GB: boot/initrd.img-2.6.24-19-generic.bak
  47.9GB: boot/initrd.img-2.6.24-21-generic
  47.9GB: boot/initrd.img-2.6.24-21-generic.bak
  47.9GB: boot/initrd.img-2.6.24-22-generic
  47.8GB: boot/initrd.img-2.6.24-22-generic.bak
  47.9GB: boot/initrd.img-2.6.24-23-generic
  47.9GB: boot/initrd.img-2.6.24-23-generic.bak
  47.9GB: boot/initrd.img-2.6.24-24-generic
  47.9GB: boot/initrd.img-2.6.24-24-generic.bak
  47.9GB: boot/initrd.img-2.6.24-25-generic
  47.9GB: boot/initrd.img-2.6.24-25-generic.bak
  54.1GB: boot/initrd.img-2.6.24-26-generic
  54.1GB: boot/initrd.img-2.6.24-26-generic.bak
  54.1GB: boot/initrd.img-2.6.24-27-generic
  54.2GB: boot/initrd.img-2.6.24-27-generic.bak
  47.8GB: boot/vmlinuz-2.6.20-16-generic
  47.8GB: boot/vmlinuz-2.6.22-14-generic
  47.8GB: boot/vmlinuz-2.6.24-16-generic
  47.8GB: boot/vmlinuz-2.6.24-17-generic
  47.8GB: boot/vmlinuz-2.6.24-18-generic
  47.7GB: boot/vmlinuz-2.6.24-19-generic
  47.7GB: boot/vmlinuz-2.6.24-21-generic
  47.7GB: boot/vmlinuz-2.6.24-22-generic
  47.9GB: boot/vmlinuz-2.6.24-23-generic
  54.0GB: boot/vmlinuz-2.6.24-24-generic
  47.9GB: boot/vmlinuz-2.6.24-25-generic
  47.9GB: boot/vmlinuz-2.6.24-26-generic
  54.2GB: boot/vmlinuz-2.6.24-27-generic
  54.1GB: initrd.img
  54.1GB: initrd.img.old
  54.2GB: vmlinuz
  47.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect
```

Please indicate what could be wrong with the GRUB for WinXP (2nd drive).

Thank you.

---

### Post by oldfred on 2010-03-08
You also need the map commands back in. The boot.ini says windows is on  drive 0 partition 1. But it is sdb or drive 1. The map commands make it think it is drive0.

---

### Post by 61811 on 2010-03-09
Fred:

Would you be kind enough to list the actual script? I am almost clueless regarding Linux commands.

I had tried this before w/o success:

[I]title Microsoft Windows XP
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/I]


Thank you.

---

### Post by confused57 on 2010-03-09
> **61811 said:**
> Fred:

Would you be kind enough to list the actual script? I am almost clueless regarding Linux commands.

I had tried this before w/o success:

[I]title Microsoft Windows XP
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/I]


Thank you.

I apologize that "setup (hd1)" caused you problems...I gave you that suggestion without really knowing your actual setup.  You're in capable hands with oldfred...the above Windows entry should now work, with your current setup.

---

### Post by 61811 on 2010-03-10
Thank you oldfred and confused57. Problem finally resolved. Thanks for your patience and perseverance.

It was more due to my lack of knowledge; though still don't understand why SGD or something similar can't figure out the drives, OSes, partitions and create a correct menu.lst file.

An excellent, simple tutorial on GRUB for beginners is here - [http://www.dedoimedo.com/computers/grub.html]("http://www.dedoimedo.com/computers/grub.html")

Here's what I ended up with for WinXP in menu.lst:

[I]title Microsoft Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1[/I]

---

