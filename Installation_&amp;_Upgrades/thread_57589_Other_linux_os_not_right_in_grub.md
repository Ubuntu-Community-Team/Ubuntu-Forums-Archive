---
title: "Other linux os not right in grub?"
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by kbarz on 2005-08-17
Heard about ubuntu by word-of-mouth and just installed it tonight.  Grub picked up my WinXP and my Redhat 9 ok, however while the WinXP works just fine, the Redhat 9 can't seem to boot properly without interference from ubuntu.  I tried adding the grub command lines from my previous grub, but Redhat 9 will still not boot (I keep seeing lines talking about Hoary Hedgehog.  Then it asks to troubleshoot, but answering yes doesn't do anything.)  I would assume that my Redhat is still intact as I didn't install to that drive, so is there something else I need to do in grub?  The first group that follows is what I added that used to work in grub, the next two are what ubuntu's grub added.
Thanks,
Ken

title		Red Hat Linux 9
root		(hd1,0)
kernel		/vmlinuz-2.4.20-31.9 ro root=LABEL=/ hdd=ide=scsi
initrd 		/initrd-2.4.20-31.9.img

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdf2.
title		Red Hat Linux (2.4.20-31.9smp) (on /dev/hdf2)
root		(hd1,0)
kernel		/vmlinuz-2.4.20-31.9smp ro root=LABEL=/ 
initrd		/initrd-2.4.20-31.9smp.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdf2.
title		Red Hat Linux (2.4.20-31.9) (on /dev/hdf2)
root		(hd1,0)
kernel		/vmlinuz-2.4.20-31.9 ro root=LABEL=/ 
initrd		/initrd-2.4.20-31.9.img
savedefault
boot

---

### Post by rmrf on 2005-08-17
can you post your whole grub conf file?

---

### Post by kbarz on 2005-08-17
Hmmm.  Dont see a grub.conf per se.  What I was editing was the menu.lst.  Everything (even the Solaris!) works except any of the Redhats:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		05

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdg1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdg1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdg1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Red Hat Linux 9
root		(hd1,0)
kernel		/vmlinuz-2.4.20-31.9 ro root=LABEL=/ hdd=ide-scsi
initrd 		/initrd-2.4.20-31.9.img

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdf2.
title		Red Hat Linux (2.4.20-31.9smp) (on /dev/hdf2)
root		(hd1,0)
kernel		/vmlinuz-2.4.20-31.9smp ro root=LABEL=/ 
initrd		/initrd-2.4.20-31.9smp.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdf2.
title		Red Hat Linux (2.4.20-31.9) (on /dev/hdf2)
root		(hd1,0)
kernel		/vmlinuz-2.4.20-31.9 ro root=LABEL=/ 
initrd		/initrd-2.4.20-31.9.img
savedefault
boot

title 		Solaris 10
map		(hd3) (hd0)
rootnoverify    (hd3,0)
makeactive
chainloader	+1

---

