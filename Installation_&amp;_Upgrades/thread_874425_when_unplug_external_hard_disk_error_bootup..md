---
title: "when unplug external hard disk error bootup."
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by K2002 on 2008-07-29
I am newbie just try to install ubuntu 8.04 in my external hard drive.

I have a problem. When unplug external hard drive from usb
the error says as following:

Grub loading stage1.5
Grub loading, please wait...
Error 21

When I plug in the external hard disk again. It will run and having a selection as the following:

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86 +
Other Operating systems:
Windows NT/2000/XP
Microsoft Windows XP Home Edition 

My boot sequence when I install the first priority boot is using cd-rom
but after that i change my sequence as the following:

Boot priority order:

1: IDE0: HTS541010G9SA00IDES
2: IDE2: PIONEER DVD-RW DVR-K06RS
3: IDE1: 
4: Network Boot: MBA V8.2.6 Slot 0400
5: USB CD-ROM
6: USB HDD Generic HD8-SU2-IN-(USB2

I want it to be when i unplug usb it will go straight to windows
When I plug in usb I can boot into UBUNTU.

Below is the command I type in the terminal to get the hard disk information:
sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf8550f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         509     4088511   12  Compaq diagnostics
/dev/sda2   *         510        6303    46540305    c  W95 FAT32 (LBA)
/dev/sda3            6304       12161    47054385    c  W95 FAT32 (LBA)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19080   153260068+  83  Linux
/dev/sdb2           19081       19457     3028252+   5  Extended
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris


And this is my menu.lst I dont know what is this but I just include this hope can give more details about my system. (I am not sure what to change to make sure my first boot is in my windows. When i plug in the external hard disk it will boot the UBUNTU operating system.)

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
# kopt=root=UUID=59be44a1-6e42-47da-b4e9-5450522207f9 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=59be44a1-6e42-47da-b4e9-5450522207f9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=59be44a1-6e42-47da-b4e9-5450522207f9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1



Please Help Me :(

---

### Post by K2002 on 2008-07-29
I can select Microsoft Windows XP Home Edition

but after i get in unplug the USB hard disk the next PC restart it will still have error as the following:

Grub loading stage1.5
Grub loading, please wait...
Error 21

I want to get rid of this error and go straight to my windows

and the last thing is I did not change any boot sequence in my windows
this is my boot.ini content as the following: 

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by K2002 on 2008-07-31
Anyone can please answer me :( please help me? any good chance to get rid of GRUB. or change my MBR back to normal windows version so that it can find the boot.ini file?

---

### Post by confused57 on 2008-07-31
Here's several ways to restore your internal drive's Windows boot:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you can boot first to USB, you can install grub to the mbr of the external drive:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
it would be something like:
```
root (hd1,y)
setup (hd1)
quit
```
y means leave this value as "find /boot/grub/stage1" shows

Boot first to your external drive, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,y) to (hd0,y), press "enter", then "b" to boot.  This is temporary, but you can make it permanent in your menu.lst.

---

