---
title: "[SOLVED] No grub after install.? WTF!"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by Plasma_NZ on 2007-10-17
Ok here's the problem...

Have x1 80gb SATA drive, chopped into segments, 30gb windows, 30gb ubuntu 7.04 - rest is swap ...

I installed windows xp first, went fine, continued to install ubuntu 7.04 - install went fine..... after install 

finished cd was removed like it tells u too, rebooted..... damn POS loaded straight to windows, didnt even 

see a grub screen @ all.....   

So i thought wtf, and tried another method as others have stated....  Installed linux first, worked fine, 

grub loaded etc giving me the boot options...  so i thought YAY! spoke too soon, i procceded to load XP 

onto the remaining partition, install went well etc...... reboot, and what do ya know...... Same problem 

as above, loaded windows straight up, no grub screen...

So i tried the windows XP repair method for FIXMBR etc, did jack squat, still have same problem...  All 

the guides on here doesnt make any sense nor work for this setup.....

... the strange thing is, i had this setup running fine when it was all on a IDE hdd... but as soon as i 

baught this new SATA hdd, these roblems have occured, and no, the IDE drive is not in the pc 

anymore..  

Idea's?          :confused:

---

### Post by Pumalite on 2007-10-17
Maybe all you need is reinstall Grub:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
See if you can boot Live CD and post:
sudo fdisk -lu

---

### Post by Plasma_NZ on 2007-10-17
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   586067264   293025600    f  W95 Ext'd (LBA)
/dev/sda5           16128   586067264   293025568+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   488392064   244188000    f  W95 Ext'd (LBA)
/dev/sdb5           16128   488392064   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    58589054    29294496   83  Linux
/dev/sdc2        58589055    60581114      996030   82  Linux swap / Solaris
/dev/sdc3   *    60581115   156280319    47849602+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 



Here's my grub menu.lst aswell

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
# kopt=root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Plasma_NZ on 2007-10-17
Ok i tried reinstalling GRUB according to the link u posted, and there was no joy, booted straight into 

windows again without showing grub etc....

ignore the 300gb and 250gb - they have only just been plugged in..

---

### Post by Pumalite on 2007-10-17
Let's see if we can make Grub show up first; change this:
title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

To this:
title Ubuntu, kernel 2.6.20-16-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Save, exit and reboot
(backup your menu.lst first: sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back)
(to edit: gksudo gedit /boot/grub/menu.lst)
(will add Windows later)

---

### Post by Plasma_NZ on 2007-10-17
Well guess what, im in windows AGAIN lol, did what u said, grub was a noshow AGAIN, went straight into 

windows...

I removed the following fromt he grub menu.lst 

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=d33c6cf5-04c0-4e89-abbf-286ee525a027 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

And replaced it with your modified one ...

didnt do jack apparently :(

---

### Post by Plasma_NZ on 2007-10-17
Not that this will help, but i'll post it all anyhow...


Motherboard : ASUS M2N-X

Graphic's       : ASUS PCI-E EN8500GT

C P U             : AM2 X2 Athlon 64bit 4800+

HDD               : Hitachi 80gb SATA 

Monitor          : LCD SamSung 19" Syncmaster 931bw 2ms response

---

### Post by Pumalite on 2007-10-17
Change the boot order of your hard drives and see if Grub shows up in one of them.

---

### Post by Plasma_NZ on 2007-10-17
I've already tried that, i've disconnected EVERYTHING bar the 1 hdd (being the SATA) and it still boots 

straight to windows, even tried the BBS popups option, still the same thing....  Im feelin heated :O

---

### Post by Pumalite on 2007-10-17
Did you install Ubuntu with only that drive connected?

---

### Post by Plasma_NZ on 2007-10-17
Yep, i always make it a point to install any OS with all other device's apart from ROM un-plugged.... 

I mean i was using ubuntu fine untill i decided to upgrade the HDD, but that was a IDE HDD..


Am smokin too much over this... gonna get some heavy lung-cancer lol.

---

### Post by Pumalite on 2007-10-18
Disconnect other hard drives. Live the SATA where you installed Ubuntu and Grub in your computer alone. Change back to original menu.lst (hd0,0). Try ro boot again.

---

### Post by Plasma_NZ on 2007-10-18
Tried that a few times, still boots straight to windows...... tried pritt much everything... im starting to 

believe its a problem between my mobo and pci raid card (despite there being no drives on it), i will 

attempt a clean install later of both OS's with the PCI-Raid card removed altogether... But im pritty

sure thats gonna make a difference..

---

### Post by Plasma_NZ on 2007-10-20
Ok, now getting error 15 and 21 and sometimes 22... - followed all grub fix's and reinstall's same thing again.... the only difference this time round was linux was installed first, i updated it, rebooted, worked fine, installed windows, no op would start due to the Grub ERROR's..

grrr

---

### Post by Plasma_NZ on 2007-10-21
Problem's been solved...


Seems that the 7.04 grub and install has issues with SATA/scsi drive's etc....  downloaded and installed 7.10 - whamo - no problems, grubs working letting me choose which os i want to boot....

Chur Chur..  :guitar:

---

