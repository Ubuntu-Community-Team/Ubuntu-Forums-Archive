---
title: "problems with grub - error 17"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by themusicalduck on 2008-10-26
Hey,

I'm having some major problems with grub since I tried to do a resizing of my linux partition and an install of windows XP on the same drive.

What I basically tried to do, was to resize the linux partition and install windows on the leftover space. Except it turns out I can't do that of course.

Another thing I did was to swap my hard drive to one of the 300Hz sata ports instead of the 150Hz one, but I'm thinking it's more likely related to the resizing.

I've tried reinstalling grub in numerous different ways. The install seems to work, but the boot doesn't.

I even tried installing another copy of linux onto another drive, hoping it would detect my other install and update grub for it, but it didn't make any difference. Same error.

I then changed my partition back to the size it was when things were working. This got me as far as the OS list, but nothing would boot. Booting my old linux install would bring up 'Failed to mount partition' and booting the new install would come up with something about a missing file.

I then thought I would try and reinstall grub from the live cd again, and now all I can get is error 17 again.

The only thing that will actually let me boot into anything, is if I install XP and overwrite the MBR with windows.

I can access all of my drives still from the live cd, and I have done disk scans of both linux partitions.

This is the contents of my menu.lst

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
timeout		20

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=09d608bc-aded-4e32-a140-179eefd78af0 ro

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
# howmany=2

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

title		Ubuntu 8.04.1, kernel 2.6.27
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27 root=UUID=09d608bc-aded-4e32-a140-179eefd78af0 ro quiet splash
initrd		/boot/initrd.img-2.6.27
quiet

title		Ubuntu 8.04.1, kernel 2.6.27 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27 root=UUID=09d608bc-aded-4e32-a140-179eefd78af0 ro single
initrd		/boot/initrd.img-2.6.27

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=09d608bc-aded-4e32-a140-179eefd78af0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=09d608bc-aded-4e32-a140-179eefd78af0 ro single
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title Windows Vista
rootnoverify (hd2,0)
chainloader +1
```

Windows XP and Windows Vista are entries for OSs which don't exist anymore.

Sorry for a long post, but I'm all out of ideas bar repartitioning everything and reinstalling everything.:confused:

---

### Post by themusicalduck on 2008-10-27
bump

---

### Post by Pumalite on 2008-10-27
Take a look at this:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
If you intend to do it in two separate drive; take a look at this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by caljohnsmith on 2008-10-27
Your Ubuntu entries in your menu.lst use (hd2), so that implies that you have 3 HDDs. How about posting:
```
sudo fdisk -lu
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/[COLOR="Red"]sdb[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/[COLOR="Red"]sdc[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
For each of the dd commands above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda above with the drives that previously returned "GRUB". Also please post:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
That will greatly clarify what your setup is like. :)

---

### Post by themusicalduck on 2008-10-27
Thanks for the replies :)

In the end it was down to my bios not seeing my hard drive after changing the cables around. I'm not really sure why, but disabling raid in the bios settings has fixed it. :)

cheers

---

### Post by aceofspades9963 on 2008-10-27
I have the same Problem I have raid0 with 2(250gb) drives and a slave 160 gb sata seen at the bottom. Will not boot windows vista anymore, in fact it will not show vista in the grub menu. I've tried booting from first disk and still no go, I get error 17. I disconnect the 160gb drive that contains ubuntu and I get grub error 21. I've tried everything I know and have ran out of ideas. I believe the raid 0 is what is giving me all the trouble. I don't want to disable my raid because I need that. So is there any other way I can get Vista back without loosing raid 0  


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60803   488394752    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37e237e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

---

### Post by Pumalite on 2008-10-27
Fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by caljohnsmith on 2008-10-27
Aceofspades9963, so you are able to get the Grub menu on start up, but you just haven't had any success booting Vista from the Grub menu? If that is true, how about booting into Ubuntu, and please post:
```
cat /boot/grub/menu.lst
```

---

