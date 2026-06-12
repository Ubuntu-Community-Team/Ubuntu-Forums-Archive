---
title: "Lost my Windows in dual-boot"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Yuri_Kenobi on 2008-10-09
Howdy!
I installed Windows XP some time ago with the intent of running dual-boot. However now that I've installed the boot loader from the Ubuntu Live CD, I can't boot Windows XP any more?

What do I have to do?:confused:

---

### Post by WWSmith36 on 2008-10-09
Please provide the output of the following commands

sudo fdisk -lu
cat /boot/grub/menu.lst

Thank you

---

### Post by Yuri_Kenobi on 2008-10-09
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7a695750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     9767519     4883728+  83  Linux
/dev/sda2         9767520   173823299    82027890    5  Extended
/dev/sda3   *   173823300   312560639    69368670    7  HPFS/NTFS
/dev/sda5         9767583   166015709    78124063+  83  Linux
/dev/sda6       166015773   173823299     3903763+  82  Linux swap / Solaris

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
# kopt=root=UUID=116c44c5-3913-46de-abfa-8bde601084ef ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=116c44c5-3913-46de-abfa-8bde601084ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=116c44c5-3913-46de-abfa-8bde601084ef ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=116c44c5-3913-46de-abfa-8bde601084ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=116c44c5-3913-46de-abfa-8bde601084ef ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=116c44c5-3913-46de-abfa-8bde601084ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=116c44c5-3913-46de-abfa-8bde601084ef ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

# on /dev/sda3
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1
marius@Reckoner:~$ 

```

The two last entries there are failed attempts of my doing. :P

---

### Post by jerome1232 on 2008-10-09
Windows is in an extended partition, I don't think Windows is very happy about that. It likes to be on a Primary partition, it has an ego I guess. :)

edit: WWSmith36 is right I didn't read the output of fdisk close enough.

---

### Post by thepizzaman on 2008-10-09
have you tried super grub disk?

---

### Post by WWSmith36 on 2008-10-09
> Windows is in an extended partition, I don't think Windows is very happy about that. It likes to be on a Primary partition, it has an ego I guess

In the case windows is actually installed on a primary partition because it is on /dev/sda3.  Extended partitions or found on /dev/sda5 or greater.

You need to edit you menu.lst file.  Open a terminal and type

gksudo gedit /boot/grub/menu.lst

Change this section at the end

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

# on /dev/sda3
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1


To this because your root command is pointing to the wrong partition 

# on /dev/sda3
title		Windows XP
root		(hd0,2)
makeactive
chainloader	+1

---

### Post by lumilanis on 2008-10-10
Bro, just use fixmbr under XP recovery console, and if needed after that run grub installer again, and edit grub as explained earlier...

---

### Post by Yuri_Kenobi on 2008-10-11
> **WWSmith36 said:**
> In the case windows is actually installed on a primary partition because it is on /dev/sda3.  Extended partitions or found on /dev/sda5 or greater.

You need to edit you menu.lst file.  Open a terminal and type

gksudo gedit /boot/grub/menu.lst

Change this section at the end



To this because your root command is pointing to the wrong partition 

# on /dev/sda3
title		Windows XP
root		(hd0,2)
makeactive
chainloader	+1
That worked perfectly! Thanks!:guitar:

---

