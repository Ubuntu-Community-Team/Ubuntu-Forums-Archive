---
title: "Fresh install Ubuntu and now Windows partition missing!"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by DilfATX on 2007-09-23
I installed Ubuntu Fiesty on my desktop.  I currently had WinXp on it and have two drives.. my idea was to have one drive "C" for my Winxp  which it is by default.. and make the other drive dedicated for Ubuntu..I have done this before on another computer..simply select the drive while doing the Ubuntu installation and it worked fine.. I did this on a new computer.. and everything looked great.. I selected Ubuntu to be installed on its own on a different drive when I went to restart the computer I noticed that GRUB took few seconds and went to the Ubuntu start up.. Ubuntu loaded up just fine. I got concerned thought because I didn't see the options to select WinXp when starting up the computer.. I did another restart and pressed ESC and noticed that on the options there is no WINXP partition..though when I get into UBUNTU all my files are on the C drive just as they would be if I had WINXP running on it. 

I would like to have both running and this is the first time this has happenedto me doing thsi process.. 

Please any suggestions would be help full.. thanks guys!

---

### Post by Pumalite on 2007-09-23
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by DilfATX on 2007-09-23
Here is the output of the command that you requested "Pumalite" btw... I just realized that I actually used the Ubuntu GG 7.10 Tribe 5 disk.. never the less.. this shouldn't happen I wouldn't think..

rey@rey-desktop:~$ sudo fdisk -lu
[sudo] password for rey:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92fd92fd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x021253db

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    74862899    37431418+  83  Linux
/dev/hdb2        74862900    78156224     1646662+   5  Extended
/dev/hdb5        74862963    78156224     1646631   82  Linux swap / Solaris
rey@rey-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=91dcdf6c-b5d6-4b63-a405-477c6f0be7bb ro

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

title           Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=91dcdf6c-b5d6-4b63-a405-477c6f0be7bb ro quiet splash
initrd          /boot/initrd.img-2.6.22-12-generic
quiet

title           Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=91dcdf6c-b5d6-4b63-a405-477c6f0be7bb ro single
initrd          /boot/initrd.img-2.6.22-12-generic

title           Ubuntu gutsy (development branch), kernel 2.6.22-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=91dcdf6c-b5d6-4b63-a405-477c6f0be7bb ro quiet splash
initrd          /boot/initrd.img-2.6.22-10-generic
quiet

title           Ubuntu gutsy (development branch), kernel 2.6.22-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=91dcdf6c-b5d6-4b63-a405-477c6f0be7bb ro single
initrd          /boot/initrd.img-2.6.22-10-generic

title           Ubuntu gutsy (development branch), memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
rey@rey-desktop:~$

---

### Post by Pumalite on 2007-09-23
We'll edit your menu.lst
First backup. sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
Add this to the end ( before AUTOMAGIC...):

title Windows 
rootnoverify (hd0,0)
makeactive
chainloader +1

Save, exit and reboot. Let's see how it goes.

---

### Post by DilfATX on 2007-09-23
Pumalite, I'm now using the Windows side.. thank you so kindly! :)

---

### Post by Pumalite on 2007-09-23
You are most welcome. Happy Ubuntuing!

---

### Post by DilfATX on 2007-09-29
One thing I have noticed.. when ever there is an update for GG the option on the partition for Windows goes away.. and I have to do this trick again to see it.  How can i fix this?

---

