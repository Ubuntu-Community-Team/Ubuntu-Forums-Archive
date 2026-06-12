---
title: "dual boot Ubuntu 6&amp;7Grub Error 15 file not found when trying to boot 2nd HD sdb."
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by bumbu on 2007-05-13
dual boot ubuntu 6&7Grub Error 15 file not found when trying to boot 2nd HD sdb.

Dear Ubuntu users,

I am experiencing a problem when trying to boot Ubuntu 7.04 from my 2nd hd. Here is what i did:

I have got 2 hard disk's in the troubled PC the idea is, i use one Linux installation on the first hard disk and one Linux installation on the second hard disk. This is done because installing a new OS takes a while and this way i can take a few hours/evenings/weeks/years to complete the installation while not destroying the working installation. First i had Ubuntu 6.06 on the first hd and Fedora4 on the second hard disk this worked fine and while i could use the spare moments to complete the install on one hard disk i could always return to the older installation to use a program yet not installed on the new installation. Today i decided to remove Fedora from the second hd and install Ubuntu 7.04 on it.
The installation went fine and i got 7.04 installed on the second hd. But when i tried to boot, grub give's me the following error: 

Error 15: File not found

first i will give some more info and then i will tell you what i did to try to solve the problem


so here is some info that might be usefull:
this is the menu.lst:

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
# kopt=root=/dev/mapper/sda160gig-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##


title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/mapper/sda160gig-root ro quiet splash
initrd		/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/mapper/sda160gig-root ro single
initrd		/initrd.img-2.6.15-28-386
boot





title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


###om Ubuntu 7.04 
title		Ubuntu, Kernel 2.6.20-15-generic (On 300 GIG SATA)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/VolGroup00/ROOT ro noquit
initrd		/boot/initrd.img-2.6.20-15-generic
boot


#old  Fedora4 used to work before i installed Ubuntu 7.04
#title Fedora Core (300 gig )
#	root (hd1,0)
#	kernel /vmlinuz-2.6.12-1.1447_FC4 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
#	initrd /initrd-2.6.12-1.1447_FC4.img



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1











~$ sudo lvscan
Password:
  ACTIVE            '/dev/VolGroup00/LogVol01' [1.94 GB] inherit
  ACTIVE            '/dev/VolGroup00/data' [238.34 GB] inherit
  ACTIVE            '/dev/VolGroup00/HOME' [20.00 GB] inherit
  ACTIVE            '/dev/VolGroup00/ROOT' [19.06 GB] inherit
  ACTIVE            '/dev/sda160gig/root' [20.00 GB] inherit
  ACTIVE            '/dev/sda160gig/Home' [20.00 GB] inherit
  ACTIVE            '/dev/sda160gig/swap' [1.00 GB] inherit
  ACTIVE            '/dev/sda160gig/muziek_VMware' [91.95 GB] inherit





~$ sudo fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2   *        2551        2574      192780   83  Linux
/dev/sda3            2575       19929   139404037+  8e  Linux LVM

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14       36483   292945275   8e  Linux LVM



-The kernel 2.6.15-28-386 works fine. 
-Fedora did work fine also but then there was one logical volume for both the home and the root partition and i didn't like that so i did split them up.
- when installing Ubuntu 7.04 it advised me to install lilo on the partition that is not marked active, so i did. Was this wrong?
-I tried the grub file with and withouth /boot in the text like this:
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/VolGroup00/ROOT ro noquit
and
kernel		/vmlinuz-2.6.20-15-generic root=/dev/VolGroup00/ROOT ro noquit
-afther mounting the 7.04 partition i checked if the file's are there:

$ ls /mnt/Ubuntu704/boot
abi-2.6.20-15-generic  config-2.6.20-15-generic  initrd.img-2.6.20-15-generic  sarge.bmp                     vmlinuz-2.6.20-15-generic
boot.0812              debian.bmp                map                           sid.bmp
coffee.bmp             debianlilo.bmp            memtest86+.bin                System.map-2.6.20-15-generic

that looks fine also....
I am a little puzzled what i should try to do next could annyone please help me out?  The Error 15 is displayed right after this sentence:
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/VolGroup00/ROOT ro noquit
i hope you can help me out! Thanx in advance, if you need any information i have left  out just ask.
Thanx!!

---

