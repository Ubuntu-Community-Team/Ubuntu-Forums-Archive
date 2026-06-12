---
title: "install fails every time. (newb)"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by pcjunkie on 2007-11-15
I have tried over 4 nights now to install Xubuntu.

I have an ASUS Nforce 4 with 2 IDE DVD R/W
and 3 SATA Drives. 
Each drive is partitioned roughly 50% of 80GB each 

If I leave all 3 drives Grub Never finds the MBR.
If I remove all other drives leaving 1 (C: in windows sda-1 with  sda -2 as ext3 ) and have a partition of 40GB xubuntu manages to find the MBR and mounts properly so I can start the system/s but always makes a 2GB partition for the system....When the thing updates it crashes and runs out of space.....

Its now asking me to configure something with gibberish command line on something I know nothing about and have no idea what it even does...

I have tried using the partition editor but my access is denied..
I see in other forums, "Unmount" the partition but when I do the Partitioner crashes.....
I cannot partition to make bigger
I cannot access anything in the partitioner without using sudo gtparted and even then it still crashed.

Apart from that Xubuntu is running fine on another system that uses 2 IDE drives and even has installed with a full 40GB if space to play in....I guess this thing hates SATA systems? Why? Its based on a freaking server yes?

Its very nimble anyway, and If I can work it properly and begin to understand it all, it will definately make the heart of my workplace server, desctop and file system. It runs MYOB just fine in WINE, that's all I needed.

---

### Post by wheredidrealitygo on 2007-11-15
Have you tried partitioning with the Gparted livecd?

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

I find it works better for me sometimes than the Gparted included with the (K/X/Edu/U)buntu livecds.

---

### Post by bulldog on 2007-11-15
Okay,we need some info first.
Boot the live cd and open a terminal,post the output of the command to the forum please.
```
sudo fdisk -l
``` it's a small L not a one.

---

### Post by ericdsr on 2007-11-15
I seem to recall having a similar issue before. My workaroung was to leave all drives enabled but go int bios and play with the order the drives boot. I *think* the drive with win on it should be 1st but I'm not sure. Check [here for more info.]("http://users.bigpond.net.au/hermanzone/p15.htm#22")

---

### Post by pcjunkie on 2007-11-15
> **ericdsr said:**
> I seem to recall having a similar issue before. My workaroung was to leave all drives enabled but go int bios and play with the order the drives boot. I *think* the drive with win on it should be 1st but I'm not sure. Check [here for more info.]("http://users.bigpond.net.au/hermanzone/p15.htm#22")

It might work someway but I have to say.
The DVD is 1
The second disk is sda (c:...)
after that it should not matter.....


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa562a562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        6610    53081055    7  HPFS/NTFS
/dev/sda2            6611        9729    25053367+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa537a537

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2        4913    39455640    5  Extended
/dev/sdb5               2        4913    39455608+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x060b060a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sdc2            4845        9442    36933435   83  Linux
/dev/sdc3            9443        9708     2136645   83  Linux
/dev/sdc4            9709        9729      168682+   5  Extended
/dev/sdc5            9709        9729      168651   82  Linux swap / Solar


its stating E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repo

---

### Post by bulldog on 2007-11-15
> **pcjunkie said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa562a562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        6610    53081055    7  HPFS/NTFS
/dev/sda2            6611        9729    25053367+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa537a537

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2        4913    39455640    5  Extended
/dev/sdb5               2        4913    39455608+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x060b060a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sdc2            4845        9442    36933435   83  Linux
/dev/sdc3            9443        9708     2136645   83  Linux
/dev/sdc4            9709        9729      168682+   5  Extended
/dev/sdc5            9709        9729      168651   82  Linux swap / Solar

Yuo have windows boot able on all your hdd's?
Which hdd you want to use ubuntu?

---

### Post by pcjunkie on 2007-11-16
Win has 3 partitions ( 1 is a light version for games =low latency the other 2 are in use, one is a backup build (ghosted install) that I am building on, Vet AV blocked any torrent files, I can't even download Ubuntu! Back to NOD32~)
These last 2 were not present during this install only sda was present. I gave up on the first night trying to get grub into MBR with more than 1 HDD present...
It only worked with 1 SATA drive present. Xubuntu is going into sda partition 2. 

[INDENT]dev/sda1 * 2 6610 53081055 7 HPFS/NTFS
/dev/sda2 6611 9729 25053367+ 83 Linux[/INDENT]


The other partitions are the mess Kubuntu left behind...same problems though I did get to see it running...all gone now...


I ran dpkg --configure -a'

dpkg: failed to write status record about `gnome-accessibility-themes' to `/var/lib/dpkg/status': No space left on device


{edit}
Wiped, could not BF. 
Tried new install with a WHOLE hdd dedicated.. (removed sdb and replaced with another SATA drive)
Nope
Grub error 22

What I get in fdisk

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa562a562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        6610    53081055    7  HPFS/NTFS
/dev/sda2            6611        9729    25053367+   5  Extended
/dev/sda5            6611        9729    25053336    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa537a537

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x060b060a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sdc2            4845        9729    39238762+   5  Extended
/dev/sdc5            4845        9729    39238731    7  HPFS/NTFS


What I get in grub 

> (hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

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
#      password --xxx
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
# kopt=root=UUID=xxx ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=xxx ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=xxxa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1




Physical loading

SATA slot1 C: / F:  drive sda 1/2 (win 16 process)
SATA Slot 2  H: = sdb = entire drive Xubuntu (79gb and it used all thank god)
SATA slot 3 I: K: =sdc = Win XP and Win XP ghost drive....(ZIpped silent and protected but only to Windows)


[IMG]http://img212.imageshack.us/img212/7716/disksvv7.png[/IMG]

---

### Post by pcjunkie on 2007-11-16
NM I will use an IDE PATA drive....

---

