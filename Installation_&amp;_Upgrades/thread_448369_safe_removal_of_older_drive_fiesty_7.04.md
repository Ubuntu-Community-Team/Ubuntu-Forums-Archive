---
title: "safe removal of older drive fiesty 7.04"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by flawedprefect on 2007-05-19
I am running a dual boot system with XP and Ubuntu Fiesty. XP runs off a master IDE drive; Ubuntu 32Bit 7.04 runs off a SATA drive.

Therefore I got the SATA drive and installed 7.04 32bit, I had a slave IDE drive and installed Feisty AMD64 bit - just to try it out. I was a bit dissatisfied with using workarounds for 32bit supported plugins such as Flash, Java, etc - hence why I decided to just go 32bit.

Anyways - my problem is this: I want to safely remove the slave IDE drive (with 64bit Feisty) without it impacting on the system. I am afraid that if I just format the drive, GRUB will give me an Error21.

I currently default boot into the 32bit Feisty (SATA). I've even edited the GRUB menu list to remove the 63bit entry (it showed up under "other operating systems detected). If I simply unplug the HDD from the IDE cable and power, i get Error21 when I boot up.

Will I continue to get this error if I format the IDE slave drive?

---

### Post by confused57 on 2007-05-19
> **flawedprefect said:**
> I am running a dual boot system with XP and Ubuntu Fiesty. XP runs off a master IDE drive; Ubuntu 32Bit 7.04 runs off a SATA drive.

Therefore I got the SATA drive and installed 7.04 32bit, I had a slave IDE drive and installed Feisty AMD64 bit - just to try it out. I was a bit dissatisfied with using workarounds for 32bit supported plugins such as Flash, Java, etc - hence why I decided to just go 32bit.

Anyways - my problem is this: I want to safely remove the slave IDE drive (with 64bit Feisty) without it impacting on the system. I am afraid that if I just format the drive, GRUB will give me an Error21.

I currently default boot into the 32bit Feisty (SATA). I've even edited the GRUB menu list to remove the 63bit entry (it showed up under "other operating systems detected). If I simply unplug the HDD from the IDE cable and power, i get Error21 when I boot up.

Will I continue to get this error if I format the IDE slave drive?

You might want to open a terminal and post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"
and
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

It would probably be a good idea to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD should be able to boot your Ubuntu install...in fact, you might try removing your IDE slave drive, boot up with the SGD & see if it'll boot your SATA drive with 32bit Feisty.  It's not necessary to do this, but it'll let you know if SGD is capable of booting your SATA drive with the IDE slave drive removed in case SGD is needed.

I'm guessing that your device.map is:
(hd0) /dev/sda  <------Win XP, IDE master
(hd1) /dev/sdb  <------Feisty 64-bit, IDE slave
(hd2) /dev/sdc  <------Feisty 32-bit, SATA drive

I believe that when you remove your IDE slave drive, your SATA would actually be (hd1), however grub is looking for root (hd2,x), when it probably should be (hd1,x) with the IDE slave drive removed?  You might want to wait for someone else to confirm this, but I don't believe just reformatting your IDE slave drive would give you the error 21, since it would be (hd1) and your SATA drive would remain (hd2).

This is my thinking on what's happening with your system and it might give you some ideas...I've been wrong before, but it's my 2 cents.

---

### Post by flawedprefect on 2007-05-19
thankyou for your suggestions, confused57. Here is the output of sudo fdisk -l:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38548   309636778+  83  Linux
/dev/sda2           38549       38913     2931862+   5  Extended
/dev/sda5           38549       38913     2931831   82  Linux swap / Solaris

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris


output of gedit /boot/grub/menu.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		30

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
# kopt=root=UUID=613e8432-7461-4536-8d95-ef376743f6af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=613e8432-7461-4536-8d95-ef376743f6af ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=613e8432-7461-4536-8d95-ef376743f6af ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


output of gedit /boot/grub/device.map:

> (hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda


SO yeah - pretty spot on on guessing which drive is which. I will try supergrub, but will refrain from formatting IDE just yet.

---

### Post by confused57 on 2007-05-19
Yes, the output(s) look pretty much as I expected...you must have installed Feisty 32-bit Herd5 & ran daily updates to the current version, since your IDE drives are designated as hda & hdb.  When I installed Feisty Herd5, my IDE drive was hda and the SATA was sda, even after applying daily updates to the final release.  Did a fresh install of Feisty & my hard drives were sda(former hda) and sdb(former sda)...doesn't really matter, since UUID's are used in fstab.

Be interesting to see if SGD can boot your SATA drive with the IDE slave drive disconnected.

---

### Post by flawedprefect on 2007-05-20
..that's a negative. Super Grub only seemed to detect the grub menu already written to the hda partition... I disconnected hdb to see if SG would have a menu item to fix the boot record... it didn't (or I couldn't find it). When I hooked up hdb again, the PC would stall on the motherboard splash screen. I could hit DEL or F8 to try to get into BIOS or Boot menu, but it wouldn't load either - it just hung. So I disconnected hdb, and I could get boot menu to load up then... I used my install disk (Feisty 32bit alternative) to try and repair GRUB... it did to a certain extent, stopping of 50%when I tried to reinstall GRUB to /dev/hda

The PC would then boot up with the options to boot Ubuntu and detected windows, but when I selected Ubuntu to boot, I got ERROR21 - hdb1 does not exist.

I assume GRUB is looking for another IDE drive instead of the SATA drive?

I can boot into window alright, and I even ahve a utility that allows me to see the linux SATA drive (Explore2fs). It appears as though I may have to reinstall Linux on the SATA drive again?

So at present, I am stuck with: IDE Master drive (hda) with windows XP, with GRUB in its MBR that seems to detect ubuntu and XP, but incorrectly detects what type of drive ubuntu is on. I have removed the slave IDE altogether.

Does anyone have any suggestion as to how I can get GRUB to recognise the linux SATA partition so I can boot into ubuntu?

---

### Post by confused57 on 2007-05-20
If you have a live cd, you can try reinstalling grub to your hda mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The Super Grub Disk should be able to reinstall grub to hda.

Before trying to reinstall grub with the live cd, you could try highlighting your Ubuntu entry in your boot grub menu, press "e", then change root from (hd2,0) to (hd1,0), & change root in the kernel line to root=/dev/sda1, then press "b" to boot...if root=/dev/sda1 doesn't work you could try typing the kernel line from your previous post & you'll probably need to change the initrd kernel:
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=613e8432-7461-4536-8d95-ef376743f6af ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

Your grub error 21 with hdb1 doesn't exist leads me to believe that you "might"  have installed your Feisty 64bit grub to the mbr & that could be causing the error.

Added:  There is a possibility that when you remove your hdb, you might need to turn the hard drive controller "off" in bios...with my Dell  I have to turn the slave drive controller "off" in order to boot a single hard drive connected as primary master.  I would still recommend using a live cd to reinstall grub to the mbr:
root (hd2,0)
setup (hd0)
using the above link

A live cd can also be used to mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

