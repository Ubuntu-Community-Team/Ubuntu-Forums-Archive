---
title: "Boot problems"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by Soldner on 2008-10-07
I just installed Ubuntu in a dual boot with an already existing XP installation. I set grub to be installed on the same boot drive as XP. Now when I try to boot XP from grub it simply says that it's missing NTloader and gives a ctrl+alt+del prompt. Any clues? I'd rather not have to reinstall XP.

---

### Post by abhilashm86 on 2008-10-07
u need to have different disk drives for two separate operating system.............uninstall windows xp and install in other drive...............even i faced a same problem as u:)

---

### Post by Soldner on 2008-10-07
XP and Ubuntu are on completely different hdds. My xp was on my first priority boot drive, so I installed grub on that drive. Now I'm unable to start XP, I've never had this problem before in the last 3 times I've installed Ubuntu on a pc.

---

### Post by semitone36 on 2008-10-07
> **abhilashm86 said:**
> u need to have different disk drives for two separate operating system

....What? 
No you dont.  Thats the whole point of "dual" booting.  

Anyways for the OT could you post the output of these commands to better help us get a handle on your problem:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2008-10-07
Can you boot into Ubuntu OK? If you can, open a terminal (applications > accessories > terminal), and please post the following:
```
sudo fdisk -lu

```
Also, find which partition is your Windows XP (it will be "NTFS" under "system"), and mount it with:
```
sudo mount /dev/sdX /mnt
```
Where "/dev/sdX" is your Windows partition. Next post the output of:
```
ls -l /mnt
cat /boot/grub/menu.lst
```
And we can work from there. :)

---

### Post by Soldner on 2008-10-07
fdisk -lu
> Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   736258949   368129443+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11c311c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdb2       204796620  1953520064   874361722+   7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000afbf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     4096574     2048256   82  Linux swap / Solaris
/dev/sdc2         4096575   208893194   102398310   83  Linux
/dev/sdc3       208893195  1465144064   628125435    7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6170997d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    20482874    10241406    7  HPFS/NTFS
/dev/sdd2        20482875   390716864   185116995    7  HPFS/NTFS



sudo mount /dev/sdX /mnt
Just gives me as follows
> mount: you must specify the filesystem type


ls -l /mnt
just outputs
> total 0

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
timeout		3

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
# kopt=root=UUID=752ea811-150f-43bb-b2b4-380b33716f09 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=752ea811-150f-43bb-b2b4-380b33716f09 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=752ea811-150f-43bb-b2b4-380b33716f09 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=752ea811-150f-43bb-b2b4-380b33716f09 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=752ea811-150f-43bb-b2b4-380b33716f09 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by caljohnsmith on 2008-10-07
Probably your menu.lst entry for Windows just needs to be changed to use the correct drive. First open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst

```
And then at the bottom of that file, replace your existing Windows entry with the following three entries:
```
title Microsoft Windows XP Professional (hd2)
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

title Microsoft Windows XP Professional (hd3)
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1

title Microsoft Windows XP Professional (hd4)
root (hd4,0)
map (hd0) (hd4)
map (hd4) (hd0)
chainloader +1
```
Reboot, and try each of Windows entries, and most likely one of them will work. When you figure out which one works, you can delete the others from your menu.lst. Let me know how it goes or if you run into problems.

---

### Post by Soldner on 2008-10-07
> Reboot, and try each of Windows entries, and most likely one of them will work. When you figure out which one works, you can delete the others from your menu.lst. Let me know how it goes or if you run into problems.


No luck

---

### Post by caljohnsmith on 2008-10-07
Can you be more specific? What exactly happens when you try each of the Windows entries in the Grub menu?

---

### Post by Soldner on 2008-10-07
Nothing

The original entry had the correct hdd/partition selected according to grub's device list. Any time I try to boot into XP, it gives a NTLDR is missing message and I'm unable to mount the partition that XP is on.

---

### Post by caljohnsmith on 2008-10-07
So which drive and partition is Windows on? When you say you can't mount it, does that mean you can't do:
```
sudo mount /dev/sdX /mnt
ls -l /mnt
```
Where /dev/sdX is your Windows partition. Does that return an error?

---

### Post by semitone36 on 2008-10-07
> **caljohnsmith said:**
> 
Where /dev/sdX is your Windows partition. Does that return an error?

Be sure to replace "sdX" with the partitcion Windows is on.  For you it looks like its on sdb1 but I could be wrong...

---

### Post by Dervheid on 2008-10-07
You might want to look here;
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
or look at some of the other advice related to windows boot problems, and use of the recovery console.
I had this issue when I cloned my HDD to a larger drive for my laptop. I have to say, I tried just about all the stuff I could find, including using the XP disk to access the Recovery Console and copying over the BOOT.ini NTLDR and NTDETECT.com files, and going through all the processes to try and make the drive 'active', but to no avail. As a last resort, I did what I had planned to do, and partitioned the new drive to dual boot with Ubuntu, and now I CAN access XP from the Grub boot screen.
I'm no expert, by any means, but it all sounded horribly familiar to me.

---

