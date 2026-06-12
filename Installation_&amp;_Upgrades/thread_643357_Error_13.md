---
title: "Error 13"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by mckinneycm on 2007-12-17
I have a single HD with Windows XP installed.  I used Partition Manager to resize the partition so that I could install 7.10 as well.  After resizing the partition, I rebooted and verified that Windows is still working.  I then booted the LiveCD, created root and swap partitions, and installed 7.10.  After that, I edited the menu.lst file to include the Windows install and when I try to load Windows now, I'm getting the following error:

Error 13: Invalid or unsupported executable format

Here is my menu.lst file:

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
# kopt=root=UUID=15d220f8-1981-4dd4-aa61-18ca34e133df ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Microsoft Windows XP
root		(hd0,0)
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=15d220f8-1981-4dd4-aa61-18ca34e133df ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=15d220f8-1981-4dd4-aa61-18ca34e133df ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Can anyone help??? Please!!!

---

### Post by mckinneycm on 2007-12-17
bump

---

### Post by Partyboi2 on 2007-12-17
If you have a windows disk, try booting into recovery and use the fixboot command and see if that works. You can also read more about it here
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

---

### Post by mckinneycm on 2007-12-18
> **Partyboi2 said:**
> If you have a windows disk, try booting into recovery and use the fixboot command and see if that works. You can also read more about it here
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

That fixed the Error 13 issue.  But now it's saying NTLDR missing.  Do you know how to fix that?

---

### Post by Partyboi2 on 2007-12-18
here is some info to get you started on how to fix it.
[http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to](http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to)
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

