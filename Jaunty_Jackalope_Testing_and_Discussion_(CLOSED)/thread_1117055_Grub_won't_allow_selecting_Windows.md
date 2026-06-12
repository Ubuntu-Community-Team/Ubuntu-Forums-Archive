---
title: "Grub won't allow selecting Windows"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by 4Orbs on 2009-04-05
This happens often, but not always. When I boot up or restart, at the Grub screen the keyboard lights are flashing and I can't use the arrow keys to select any other option. I'm thinking that by adding a few seconds to the grub auto-timer that maybe the keyboard will become enabled before auto-boot to Ubuntu engages.

---

### Post by kansasnoob on 2009-04-05
Would you post the output of:

```
sudo fdisk -l
```

And also:

```
cat /boot/grub/menu.lst
```

Maybe we can see a problem.

---

### Post by 4Orbs on 2009-04-05
OK. Here's the fdisk output:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         646     4883728+  12  Compaq diagnostics
/dev/sda2   *         647        7170    49321440    7  HPFS/NTFS
/dev/sda3            7171        7294      937440   82  Linux swap / Solaris
/dev/sda4            7295       15505    62075160    5  Extended
/dev/sda5            7295        8459     8807368+  83  Linux
/dev/sda6            8460       14401    44921488+  83  Linux
/dev/sda7           14402       15505     8346208+   b  W95 FAT32

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x270ffb71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661    7  HPFS/NTFS
```

And here is the grub output:
```
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
# kopt=root=UUID=2ed70c54-d512-4841-b830-7298b0be8735 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2ed70c54-d512-4841-b830-7298b0be8735

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		2ed70c54-d512-4841-b830-7298b0be8735
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2ed70c54-d512-4841-b830-7298b0be8735 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		2ed70c54-d512-4841-b830-7298b0be8735
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2ed70c54-d512-4841-b830-7298b0be8735 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		2ed70c54-d512-4841-b830-7298b0be8735
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows Whistler Personal
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by kansasnoob on 2009-04-05
I don't see anything wrong.

If you want to play with the timeout which is by default 10 seconds the simplest way is to install startupmanager either from Synaptic or:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration ....

Or you could of course open /boot/grub/menu.lst with Xubuntu's text editor (in Ubuntu it's gedit so):

```
sudo gedit /boot/grub/menu.lst
```

And change the actual number of seconds here:

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		10**

Sorry I can't recall if Xubuntu uses gedit or vim or nano for a text editor. I'm thinking nano!

More about Startup manager here:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

### Post by kansasnoob on 2009-04-05
Oh, if you wanted the timeout to be infinite and just wait forever until you choose you can comment out the "timeout" line like this:

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**#timeout		10**

Or just untick the "use timeout in bootloader" option using Startup manager.

I do that because sometimes I get interrupted just as I'm rebooting to get to another OS.

---

### Post by 4Orbs on 2009-04-05
I'll try extending the countdown time. This isn't really a critical issue, I'm more curious as to why sometimes the keyboard is disabled during the grub screen. Other times it is active immediately.

---

