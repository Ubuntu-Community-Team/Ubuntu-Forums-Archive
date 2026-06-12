---
title: "Dual Booting with ubuntu and XP Grub Error"
date: 2005-09-18
forum: Installation &amp; Upgrades
---

### Post by Flegg on 2005-09-18
Hiya all, I wonder if someone can help me please, I've just re-partitioned and wiped everything on my laptop to the following spec:

80GB hard drive:
50GB Windows NTFS
20GB ubuntu 5.04 now upgraded to 5.10
5GB swap partition
5GB FAT32 partition

I installed windows XP SP2 first, that was working all fine, then I installed ubuntu 5.04 onto the 2nd partition, this installed now problems, until GRUB was installed, GRUB detected that windows XP was installed and added it to the GRUB list of bootable partitions, but when I select Windows XP, it returned error 29 WRITE DISK ERROR or something along those lines, and I now cannot get into windows XP
    I have tried upgrading ubuntu via FTP to 5.10 to see if the updated kernel/GRUB would fix it but I still have the problem

Does anyone have any suggestions on how to get grub to correctly boot windows XP?

Hope someone can help!

Thanks

Flegg

---

### Post by Flegg on 2005-09-18
anyone got any suggestions for this? I have tried installing lilo and seem to have installed it but when I reboot grub is still there, so have uninstalled lilo again

anything I can post to help resolve this?

Thanks

Flegg

---

### Post by Flegg on 2005-09-18
just for whoever's reference this is grub's menu.lst file:

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
default		5

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title Ubuntu, kernel 2.6.12-8-686
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.12-8-686 root=/dev/hda5 ro quiet splash
	initrd /boot/initrd.img-2.6.12-8-686

title Ubuntu, kernel 2.6.12-8-686 (recovery mode)
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.12-8-686 root=/dev/hda5 ro single
	initrd /boot/initrd.img-2.6.12-8-686

title Ubuntu, kernel 2.6.10-5-686
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/hda5 ro quiet splash
	initrd /boot/initrd.img-2.6.10-5-686

title Ubuntu, kernel 2.6.10-5-686 (recovery mode)
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/hda5 ro single
	initrd /boot/initrd.img-2.6.10-5-686

title Ubuntu, memtest86+
	root (hd0,4)
	kernel /boot/memtest86+.bin 

title Microsoft Windows XP Professional
	rootnoverify (hd0,0)
	makeactive
	chainloader +1

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by seethru on 2005-09-18
why do you have windows xp twice? the second one looks like the one the installer made for you, is that the one thats giving you that error?

---

### Post by Flegg on 2005-09-29
I don't know, every time I removed it, it added it again, I found out what the error was in the end, BIOS protection was enabled when I disabled it, it booted into XP fine, there must be a one-time-BIOS-write the first time it does it

thanks alot all for your help anyway, hope this helps someone else in the future :)

Flegg

---

### Post by linuxNewb on 2005-12-02
I'm having th same problem. What exactly is 'bios protection', and how do I disable it? Thanks in advance.

---

### Post by dyrer on 2005-12-03
My Ubuntu 5.10 installation boots with root (0,0) and Windows dont start

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/hda5   *           2       11517    92502238+   7  HPFS/NTFS
/dev/hda6           11518       24321   102848098+   b  W95 FAT32

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12847   103193496    7  HPFS/NTFS
/dev/sda3           12848       24321    92164905    f  W95 Ext'd (LBA)
/dev/sda5           12848       24321    92164873+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29652   238179658+  83  Linux
/dev/sdb2           29653       30401     6016342+   5  Extended
/dev/sdb5           29653       30401     6016311   82  Linux swap / Solaris

My windows is installed to sda disk
What should I do to make Windows start?

---

### Post by elcu on 2006-01-06
I had the same problem.  In my case it was caused by the bootable flag being disabled on XP's partition.

- run 'sudo cfdisk <device>' (In my case, XP is installed on /dev/hda so <device> would be that)
- enable the bootable flag for the NTFS partition
- write changes
- quit
- reboot

Hopefully this fixes it for you.

---

### Post by Penquite on 2007-01-28
I too am having the Error 29 issue.

When I run 'sudo cfdisk /dev/hda1' , cfdisk responds with,

FATAL ERROR: Bad primary partition 0: Partition begins after end-of-disk

Thanks

Penquite

---

