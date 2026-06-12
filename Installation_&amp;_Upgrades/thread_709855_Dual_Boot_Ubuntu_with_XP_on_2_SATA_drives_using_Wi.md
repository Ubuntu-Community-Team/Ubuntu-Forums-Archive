---
title: "Dual Boot Ubuntu with XP on 2 SATA drives using Windows Boot Loader"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by latin_l3oi on 2008-02-27
Hi there,

I'm new to Ubuntu and I would like to dual boot ubuntu with windows xp using the windows boot loader (if thats possible).

I have 3 SATA hard drives,

One is for Windows XP divided into many paritions
Second one is for Backup
and Third one is for Ubuntu, which I divided into 3 partitions:

ext3 = 50GB
swap = 5GB
fat32 = 25GB

I tried installing it yesterday and during the installation setup I changed the boot loader option and I think I set it incorrectly eg: hd(1,0) (I didn't know what that meant at that time), when I rebooted it will load windows straightup and I wasn't sure how to boot to ubuntu.

I thus booted the live CD and set the ext3 as boot but this made a message display during bootup: "Error loading operating system".

Therefore I removed the "boot" flag from the ext3 partition and windows loads fine.

So what I have done now is I formatted the ext3, swap and fat32 partitions, whiping ubuntu out, and I would like to start again with help and advise :)

To recap, I'm trying to dual boot Windows XP and Ubuntu (preferably using windows boot loader) on 2 seperate SATA hard disks.

Any advise and suggestions would be greatly apprceciated.

Cheers,

latin_l3oi

---

### Post by logos34 on 2008-02-27
You don't need to use windows to boot ubuntu.  If it's a matter of not wanting grub to overwrite the windows bootloader, then reinstall it to the **mbr** of the ubuntu drive and set it in the bios as the boot drive.  (sounds like you wrote it to the ubuntu root partition with hd1,0).  Then simply edit the [windows entry in menu.lst to boot XP on the second drive.]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")  (make sure the windows drive is second in the bios hard disk boot order).

Set ubuntu as the boot disk.  Boot from the [live cd and reinstall grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351").

Boot from the hard drive.  Select ubunu on the grub menu and press 'e' to edit, and 'e' again to edit the 'root' line.  Change to (hd0,0).  Once booted into ubuntu make the change permanent:

gksudo gedit /boot/grub/menu.lst

Change the root and 'groot' line (the latter is near the top) to hd0,0.

Add map commands to windows entry at the bottom.

You may have to change /boot/grub/device.map to match new arrangement.

The boot flag usually only matters to windows (and only sometimes at that.  Doesn't make a diff to mine I've found).  If you still can't boot XP, use gparted to switch flag to windows partition.

---

### Post by confused57 on 2008-02-27
If you can set your bios to boot first to the Ubuntu drive, I would recommend using grub to boot Windows & Ubuntu...just set Ubuntu drive as the first hard drive booted in bios, then install Ubuntu...make a note of how the install/partitioner recognizes your Ubuntu drive(sda,sdb, or sdc), then near the end of the installation, there should be an "Advanced" button in the lower right section of the screen.  Click on this and type /dev/sdc(or however your Ubuntu drive is recognized) in place of the default (hd0) as the location to install grub.
I've never done so myself, but it is possible to boot Ubuntu from Windows bootloader, but it's much easier to boot Windows from grub.

Added:  logos34 beat me to it, and explained it much better.

---

### Post by logos34 on 2008-02-27
> **confused57 said:**
> ...just set Ubuntu drive as the first hard drive booted in bios, then install Ubuntu...

hey there confused57...come to think of it, reinstalling as you suggested may actually be faster.

latin_l3oi,

one more thing I noticed: why the 5 gb swap? You only need 1-2 gb max.

---

### Post by latin_l3oi on 2008-02-28
hello,

Ubuntu is now working! :) Thanks

Though now I can't get Windows XP to boot. lol If it's not one it's the other.

I reinstalled Ubuntu following the steps logos34 and confused57 gave and I was able to get Ubuntu up and running.

I changed the Ubuntu drive to be the one to boot via the BIOS and I did the gksudo gedit /boot/grub/menu.lst thing, though now at the boot screen, when I try to boot windows xp, I get an error message saying: 

NTLDR is missing
Press ctrl + alt + delete to restart

I don't know what could be wrong... 

I've also tried setting the windows xp drive to be the one to boot via BIOS but the same error message gets displayed. :S

---

### Post by confused57 on 2008-02-28
> **latin_l3oi said:**
> hello,

Ubuntu is now working! :) Thanks

Though now I can't get Windows XP to boot. lol If it's not one it's the other.

I reinstalled Ubuntu following the steps logos34 and confused57 gave and I was able to get Ubuntu up and running.

I changed the Ubuntu drive to be the one to boot via the BIOS and I did the gksudo gedit /boot/grub/menu.lst thing, though now at the boot screen, when I try to boot windows xp, I get an error message saying: 

NTLDR is missing
Press ctrl + alt + delete to restart

I don't know what could be wrong... 

I've also tried setting the windows xp drive to be the one to boot via BIOS but the same error message gets displayed. :S
From a terminal(Applications---Accessories---Terminal), please post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

and your grub menu.lst file:
```
gedit /boot/grub/menu.lst
```

I would also recommend you to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it has an option(among many others) of "Fix Boot of Windows" or you can use a Windows install cd(not a recovery one), boot it, press "r", then FIXMBR.

Here are different ways to restore your Window's IPL(Initial Program Loader) to the Windows drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
I know it says "Uninstall Page", which you don't want to do, it  "should" enable you to boot into Windows by changing your hard drive boot order in the unlikely event your Ubuntu drive won't boot.

---

### Post by latin_l3oi on 2008-02-28
"sudo fdisk -l" Output:
==============

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb0f6f2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104864256    7  HPFS/NTFS
/dev/sda2           13056       48641   285844545    f  W95 Ext'd (LBA)
/dev/sda5           13056       14361    10490413+   7  HPFS/NTFS
/dev/sda6           14362       16972    20972826    7  HPFS/NTFS
/dev/sda7           16973       17234     2104483+   7  HPFS/NTFS
/dev/sda8           17235       19845    20972826    7  HPFS/NTFS
/dev/sda9           19846       48565   230693368+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1197

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13054   104856223+  83  Linux
/dev/sdb2           13055       13707     5245222+  82  Linux swap / Solaris
/dev/sdb3           13708       20234    52428127+   b  W95 FAT32

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001268e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       48641   390708801    7  HPFS/NTFS

===========================================
===========================================

"gedit /boot/grub/menu.lst" Output: (I'm not sure I edited this correctly...)
======================

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
# kopt=root=UUID=4dbff41e-a8f8-44e9-afe3-e290dc8d23cc ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4dbff41e-a8f8-44e9-afe3-e290dc8d23cc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4dbff41e-a8f8-44e9-afe3-e290dc8d23cc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+file:///usr/share/ubuntu-artwork/home/index.html
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader	+1

=====================================================
=====================================================

---

### Post by piotrwoj on 2008-02-28
other metod:
Loader - NT
dd if=/dev/sdaX of=/bootsect.lin bs=512 count=1
repair winnt from console fixboot, fixmbr
totalcmd and ext3/reiserfs plugin - bootsect.lin copy to boot win32 partition and wirite to booi.ini example:
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\BootSect.DOS="Microsoft Windows 98 SE"
C:\BootSect.lin="LINUX Debian - UBUNTU kernel 2.6.xx"
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

---

### Post by confused57 on 2008-02-28
Since you have 3 hard drives, grub may recognize your Windows drive as (hd2):
```
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

You can find out by checking the output of:
```
gedit /boot/grub/device.map
```

---

### Post by latin_l3oi on 2008-02-29
> Since you have 3 hard drives, grub may recognize your Windows drive as (hd2):
Code:

title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1



YEAH! Thank You! :D

Windows XP boots now :)

I would like to know one more thing relating to the bootloader:

How could I get Windows XP to be the default option to boot?
Change the name of the OS (eg: instead of Ubuntu 7.10 #### etc...., just say: Ubuntu)?
And also lower the timer?

Cheers,

latin_l3oi

---

### Post by confused57 on 2008-02-29
Glad it worked...here's how I have my system set up:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Also, see the grub section on Herman's(a forum member) website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by lha on 2008-02-29
> **latin_l3oi said:**
> YEAH! Thank You! :D

Windows XP boots now :)

I would like to know one more thing relating to the bootloader:

How could I get Windows XP to be the default option to boot?
Change the name of the OS (eg: instead of Ubuntu 7.10 #### etc...., just say: Ubuntu)?
And also lower the timer?

Cheers,

latin_l3oi

See [http://ubuntuforums.org/showthread.php?t=704589&page=2]("http://ubuntuforums.org/showthread.php?t=704589&page=2") for a hack that changes Ubuntu 7.10 #### etc to just Ubuntu.

---

