---
title: "XP savedefault dual boot, single time next boot ubuntu?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by jeffk on 2006-06-18
I've set up a few dual boot Windows XP / Ubuntu 6.06 machines at the desks of office users who might occasionally try Ubunutu.

Since they are deployed in Windows XP shops, the only savedefault grub menu.lst entry is the detected XP. This is the last entry, per detection default behavoir. 

I have a separate interest in preventing new ubuntu kernels from getting savedefault in their automagic menu.lst entries, but that's for another thread.

I have remote (vnc) access to these XP machines, and from time to time I would like to reboot the machine to the first Ubuntu menu.lst entry. This is to do some maintenance, package updates, SMB configuration, etc. The intent is to keep the Ubuntu install as polished as possible, so it makes the best possible impression if the user decides to take it for a spin at some random time.

The partitions are 1 NTFS partition with XP, then ubuntu installed on ext3 and swap partions in the free space, as per installer defaults.

Is there a simple, free utility or technique for XP that would allow me to reboot XP with a different parameter, selecting a nondefault GRUB entry for one-time booting?

I'd prefer something less involved than an ext3 filesystem IFS driver. I'm hoping for something like the utilities that (it seemed) could hotload a linux kernel from a running Windows 9x instance. Just a one-shot 'boot linux next time, and next time only' function for maintenance work.

Thanks for any tips.

---

### Post by catlett on 2006-06-18
I can't really tell what you want, buI'll take a stab in the dark. You can go into grub's menu list from windows with ext2fs driver and changed the default boot#. This way when you reboot it will boot the entry you just selected via the default value. 
For example if I wanted to boot the  2.6.15-23-386 kernel. I would change the default from 0 to 2 (grub uses 0 so 3 down is 2 to grub). Here is my menu now before I would go in and make a change via the ext2fs driver.
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		0[/COLOR]

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
# kopt=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot
[COLOR="Lime"]
title		Ubuntu, kernel 2.6.15-23-386[/COLOR]
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot
```
My menu after the edit from windows would be this. (actually you could do one more thing to make the transition even faster. Change the timeout from 10 to 1. Since you know that you want it to boot to the default, why wait 10 seconds, Change it to 1 so the boot starts right away)

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		2[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		1[/COLOR]

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
``` If this doesn't pertain to what you want, disregard. Even if it is what you want I know it isn't that elegant but it is a way to do it.

About the kernel issue. You can deselect them when the update manager offers them. You don't have to get them. Many linux people compile their own custom kernels and never replace them with a distro's updated kernel.


I don't know of any other way to change the boot order other than selecting a different entry at startup from the grubn menu. Good luck

---

