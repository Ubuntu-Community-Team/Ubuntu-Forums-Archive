---
title: "error 21 with sata and pata disks"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by machinakias on 2008-08-21
hi all...im brand new in linux so i need some help..i have a pc with one sata and one ide disk.in the ide i installed win xp and on the sata ubuntu 8.04.the thing is that i get an error 21 and i cant boot my xp...tried to solve it but i cant get it done...any help pls? thanx all!

---

### Post by jerome1232 on 2008-08-21
Well first thing we are going to need is to see your partitions

```
sudo fdisk -l
```

second thing I can see as helpful would be to see your menu.lst assuming you are using gnome (Ubuntu)
```
sudo gedit /boot/grub/menu.lst
```

copy whatever is in gedit into a post.

be sure to put the results in [ code ] tags

edit: Welcome to the forums

---

### Post by machinakias on 2008-08-21
well here we are..
errikos@ZEUS:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x199b199a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e91a941

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9324    74894998+  83  Linux
/dev/sdb2            9325        9726     3229065    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris


and the other one..

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
# kopt=root=UUID=c5b0f1bf-f6a5-4ada-b46b-e9432176b772 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c5b0f1bf-f6a5-4ada-b46b-e9432176b772 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c5b0f1bf-f6a5-4ada-b46b-e9432176b772 ro single
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by jerome1232 on 2008-08-21
> **machinakias said:**
> well here we are..
errikos@ZEUS:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x199b199a

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]**/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS**[/COLOR]

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e91a941

   Device Boot      Start         End      Blocks   Id  System
[COLOR="DarkOrange"]**/dev/sdb1               1        9324    74894998+  83  Linux**[/COLOR]
/dev/sdb2            9325        9726     3229065    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
[COLOR="DarkOrange"]**root		(hd1,0)**[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c5b0f1bf-f6a5-4ada-b46b-e9432176b772 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c5b0f1bf-f6a5-4ada-b46b-e9432176b772 ro single
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
title		Microsoft Windows XP Professional
[COLOR="Red"]**root		(hd0,0)**[/COLOR]
savedefault
makeactive
chainloader	+1

That's just nifty okay let me break this down, in red I highlighted windows, in orange Ubuntu. Error 21, means drive doesn't exist.
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name
refers to a disk or BIOS device that is not present or not recognized by the
BIOS in the system.

Windows is on partition sda1 which is first drive, first partition. Grub starts counting at zero so for grub that means drive 0, partition 0. Hence we get hd(0,0) which is correct.

Ubuntu, is on sdb1, or second drive, first partition, in grub speak, hd(1,0). Which is correct.

It looks like sda is flagged as a bootable disk, which means that's where grub resides, I don't get why this doesn't work.

---

### Post by Iceman99one on 2008-08-21
I had a similar problem with my dual boot with two hard drives. Went trying to boot into windows I kept on getting error 21.

It turned out that my dell desktop had a utility wired in somewhere that controlled the IDE channels. So I went in right at startup and switched my secondary on and... tadaa I'm now successfully booting both into win xp and ubuntu.

Im not sure but it might be that certain channels are not turned on in your computer.

Just an idea...

Good luck!

---

### Post by machinakias on 2008-08-22
tried different things like changing the boot sequence in bios and reinstalling ubuntu putting grub to another disk but still no luck...let me tell you that my xp is installed on my ide disk and ubuntu in a sata...any one else who can help? thanx folks for your advances!!!

---

### Post by DavidTangye on 2008-08-22
How did the Windows partition get set up? by the Windows installer, or something like Partition Magic?

---

### Post by machinakias on 2008-08-22
> **DavidTangye said:**
> How did the Windows partition get set up? by the Windows installer, or something like Partition Magic?
as usual from the xp setup...last thing i tried is to put the grub in the windows hd...but still error 21...got some idea?

---

### Post by DavidTangye on 2008-08-22
Check out [http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm), especially the section on '[SIZE=2]Having Grub Do Your Research For You'[/SIZE]

---

