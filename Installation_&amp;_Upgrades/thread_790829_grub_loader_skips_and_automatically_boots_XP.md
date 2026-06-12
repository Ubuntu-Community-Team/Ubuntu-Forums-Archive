---
title: "grub loader skips and automatically boots XP"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by odingrey on 2008-05-11
I recently setup a dual boot XP, Ubuntu on my second hdd.  I had a dual boot on this machine before but it was XP on one hdd, ubuntu on the other, and I wanted the extra space to be in NTSF... long story short, that worked.

So I formatted the second hdd, reinstalled xp first, then installed ubuntu, now when I boot, it completely skips the grub loader and boots XP.  I've been fooling around with that problem for 2 days already and scoured google to no avail.  I've reinstalled the OS's 3 times already.

Anyone have some kind of a fix?

---

### Post by vorgusa on 2008-05-11
Not sure if this will help you fix your problem, but there is a GUI for Grub called QGrubEditor... this will make it easy to adjust options... I got annoyed with the 10 second wait and searched for something to easily change the settings and that is what popped up.  The main screen has a list of all the bootable OS's.. might help you find out what is going wrong

---

### Post by pro003 on 2008-05-11
did you reconfigure your /boot/grub/menu.list ?

---

### Post by odingrey on 2008-05-11
> **pro003 said:**
> did you reconfigure your /boot/grub/menu.list ?


Yea, but I am pretty lost in that file...

---

### Post by odingrey on 2008-05-11
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
# kopt=root=UUID=2ed959e5-8db2-4fbb-aede-edbcaa300e26 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2ed959e5-8db2-4fbb-aede-edbcaa300e26 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2ed959e5-8db2-4fbb-aede-edbcaa300e26 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by odingrey on 2008-05-11
> **vorgusa said:**
> Not sure if this will help you fix your problem, but there is a GUI for Grub called QGrubEditor... this will make it easy to adjust options... I got annoyed with the 10 second wait and searched for something to easily change the settings and that is what popped up.  The main screen has a list of all the bootable OS's.. might help you find out what is going wrong

My problem with that is I can't actually boot into ubuntu on my HDD, I can boot into it with the CD tho.

---

### Post by odingrey on 2008-05-11
bump*  Still way lost, can anyone see anything wrong with the menu.list file?

---

### Post by odingrey on 2008-05-11
k, for whatever reason I changed the HDD priority to try to boot from the blank HD first, and that loaded grub.  So it does seem to work now.

Thx guys who helped :)

---

### Post by pro003 on 2008-05-12
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout 10**
```

i thought this was problem these 10 sec they were maybe at 0, but anyway you found the way out... am glad you made it...:)

---

### Post by Cato2 on 2008-05-12
For anyone else with Grub problems, I really recommend two things:
[LIST=1]
[*][SuperGrubDisk]("http://www.supergrubdisk.org/") - bootable CD that is a menu-driven frontend to Grub - great to explore your disks, find a bootable file, restore your MBR (e.g. after XP has overwritten it), or simply to boot an otherwise unbootable system.  Does not require any command line skills!
[*][Hermanzone's GRUB pages]("http://users.bigpond.net.au/hermanzone/p15.htm") - by FAR the best Grub tutorial, this is good to help understand what Grub is doing, what the error messages mean, and so on.
[/LIST]

Grub is very powerful - once you understand a bit around it from the second link, it's much easier to quickly diagnose and solve boot problems.

---

