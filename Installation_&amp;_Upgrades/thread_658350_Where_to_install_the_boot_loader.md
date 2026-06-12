---
title: "Where to install the boot loader"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by HellishER on 2008-01-04
I'm trying to install Ubuntu 7.10 32bit Desktop on my computer. I have winXP installed already on a sata drive. Which i have selected in the BIOS to be the primary boot drive.

I have 2 IDE drives and 4 SATA drives in this computer. The thing is that Ubuntu wants to install the boot loader to hd0 that i suspects is hda and thats the master-IDE drive. But i don´t want it there, i have like i wrote selected a SATA drive as the primary boot drive.

The SATA drive looks like this:
sda,1 = NTFS = winxp
sda,2 = EXT3 = /   Ubuntu
sda,3 = SWAP
sda,4 = FAT32

So in the "advanced" options in the final stage of the installation of Ubuntu, what should i write there the default is (hd0)..?
 I have tried (sd0) and (sd0,1) but that gives me an error when installing.
First installation i forgot the advanced option and installed to (hd0), so of course after the reboot i got right into winxp.

---

### Post by logos34 on 2008-01-04
> **HellishER said:**
> So in the "advanced" options in the final stage of the installation of Ubuntu, what should i write there the default is (hd0)..?.

type

> **/dev/sda**

or whichever sata you want it on

---

### Post by Pumalite on 2008-01-04
/dev/sda1

---

### Post by logos34 on 2008-01-04
> **Pumalite said:**
> /dev/sda1

If he does that it will overwrite the windows boot files and he won't be able to chainload XP!


/dev/sda 

will put grub on the MBR

---

### Post by Pumalite on 2008-01-04
You are right. My mistake.

---

### Post by HellishER on 2008-01-04
Thanks, got GRUB installed.. But now i when i select Ubuntu in the boot menu i get:
Error 22: No Such Partition.
WinXP will not both either.. ntdllr could not be found.. Or something similar..
Gonna do some searches and see if i can find a solution.

Edit: Manage to fix so i can boot to ubuntu sofar.. Edited GRUB menu list. Changed root (hd2) too (hd0). :)

---

### Post by Pumalite on 2008-01-04
Post:
sudo fdisk -lu
And I'll help you chainload XP

---

### Post by logos34 on 2008-01-04
> **HellishER said:**
> 
WinXP will not both either.. ntdllr could not be found.. Or something similar..

Edit: Manage to fix so i can boot to ubuntu sofar.. Edited GRUB menu list. Changed root (hd2) too (hd0). :)

I should've remembered to mention having to change ubuntu root to (hd0,1).

> sda,1 = NTFS = winxp
sda,2 = EXT3 = / Ubuntu

If windows is first partition as in the above, then you probably just need to change XP root to (hd[COLOR="Red"]0[/COLOR],0) to get it to boot

---

### Post by HellishER on 2008-01-04
I did get into ubuntu and apply all updates and installed gfx-drivers.. After the reboot i got the same GRUB error as before.. used live cd to change the menu.lst file.. But now i still get the error, and the file is changed..

Heres the fdisk lines:
```

ubuntu@ubuntu:/$ sudo fdisk -lu

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5f42942f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   625137344   312568641    7  HPFS/NTFS

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01b301b2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   586083329   293041633+   7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbea7bea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   409593239   204796588+   7  HPFS/NTFS
/dev/sda2       409593240   808953074   199679917+  83  Linux
/dev/sda3       808953075   809949104      498015   82  Linux swap / Solaris
/dev/sda4       809949105   976768064    83409480    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x96021186

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b338a09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   321669494   160834716    7  HPFS/NTFS

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11714a0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1465144064   732572001    7  HPFS/NTFS


```

GRUB menu.lst
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
# kopt=root=UUID=15cc044a-20c8-4074-b464-0b70695497b6 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=15cc044a-20c8-4074-b464-0b70695497b6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=15cc044a-20c8-4074-b464-0b70695497b6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
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
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

---

### Post by logos34 on 2008-01-04
you forgot 'groot' line (that's why update messed it up)

> # groot=(hd[COLOR="Red"]0[/COLOR],1)

take out the map commands in XP:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
[COLOR="Red"]makeactive[/COLOR]
savedefault
chainloader	+1

---

### Post by HellishER on 2008-01-04
Thanks, got into Ubuntu again. :)

I Wonder why i had to do "all" this to get it to work this time. I have had Ubuntu 7.04 and 7.10 installed on this computer before. But got a harddrive crash on my system disc yesterday so i was force to reinstall everything and buy a new harddrive. :(

---

### Post by logos34 on 2008-01-04
maybe you just got lucky before.  But mixing sata and ide really muddies the waters, grub-wise.  Grub is hard-wired to look for the ide channels first and it always thinks those must  be the boot drives, regardless of the actual bios hard disk boot order or where ubuntu/linux is installed.

So can you boot XP?  And did you by any chance reinstall grub after changing menu.lst, or did the change alone allow you to boot back into ubuntu (either the first time or just now)?

---

### Post by HellishER on 2008-01-04
XP works fine. :)
Have not reinstalled grub that i are aware of.. I'm still a Linux newbie. ;)

First time change to menu.lst worked.. Second time i changed it after the 125 Ubuntu updates it didn´t work for some unknown reason. (At least to me)

But when i applied your changes i worked again. Hope it still works tomorrow. Time for bed now.
Thanks again.

---

### Post by logos34 on 2008-01-04
ok, glad everything's in order.

---

