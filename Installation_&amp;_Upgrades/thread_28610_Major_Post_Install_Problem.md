---
title: "Major Post Install Problem"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by runt on 2005-04-20
Ok, I got my 120GB hard drive back from my dad tonight.  Put it in my computer and Ghosted my Windows XP install over to it so I could use my 80GB drive for ubuntu.  Installed ubuntu with no problem and I thought grub installed with no problem also.  Problem is, I cannot get ubuntu to boot no matter what I do.  My hard drives are arranged as follows, 120GB Primary Master, 80GB Primary Slave, 160GB Sata 1.  grub is installed on the MBR of the 80GB drive and I set my BIOS to boot from HD-1 (BIOS term).  I did this so I could still boot Windows XP in case of a problem.  I have had other Linux distros boot using this.  Only way I can get ubuntu to even attempt to boot is to specify root (hd0,0) in the command line part of it and then type the normal kernel stuff.  grub was setup to use (hd0,0) for my ubuntu root.  Also, if I type the proper commands to boot WIndows from grub using the modified hd stuff, it will not boot :(  How can I fix this?  Windows is really picky about being the first hard drive unless you install it on the second hard drive, and I do not want to reinstall Windows if I can help it.  As soon as I get my copy of the ubuntu live CD downloaded, I can post my grub.conf for you guys (still waiting for the CDs I ordered).

---

### Post by diebels on 2005-04-20
post /boot/grub/menu.lst and fdisk -l

---

### Post by runt on 2005-04-20
[QUOTE=diebels]post /boot/grub/menu.lst and fdisk -l[/QUOTE]

i will as soon as i get the live cd downloaded and burned.  as it is, i cannot get into ubuntu to do that.

---

### Post by DR_K13 on 2005-04-20
I wish I could help ya bro

---

### Post by runt on 2005-04-20
[QUOTE=DR_K13]I wish I could help ya bro[/QUOTE]
 it sucks, but sadly i have had all sorts of problems with ubuntu.  yet i only had problems installing Gentoo once :(

why is it that i have no problem with the difficult linux distros, and tons of problems with the easy ones?

---

### Post by runt on 2005-04-21
[QUOTE=diebels]post /boot/grub/menu.lst and fdisk -l[/QUOTE]

ok /boot/grub/menu.lst as created by the installed
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

and fdisk -l
```

root@ubuntu:/home/ubuntu # fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 6144 MB, 6144284672 bytes
255 heads, 63 sectors/track, 747 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           5       40131    0  Empty
/dev/sdb2   *           6         747     5960115    b  W95 FAT32

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9399    75497436   83  Linux
/dev/hdb2            9400        9729     2650725    5  Extended
/dev/hdb5            9400        9729     2650693+  82  Linux swap / Solaris

```

/dev/sdb is my iPod mini hooked up via firewire, /dev/sda is my SATA drive, /dev/hda is my windows drive, and /dev/hdb is my ubuntu drive.

---

### Post by runt on 2005-04-22
anyone got any ideas?

---

