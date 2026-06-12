---
title: "[SOLVED] Xubuntu Gutsy &amp;amp; WinXP dual boot GRUB errors"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by smacd on 2008-01-24
I am having problems getting my system set up to dual boot Xubuntu Gutsy and WinXP.

my system:
Athlon64 4000+
2GB RAM
nVidia 7800
4 hard drives:
  - 80GB with WinXP (IDE)
  - 120GB with Xubuntu (IDE)
  - 300GB data (IDE)
  - 500GB data (SATA)

The 80GB hard drive is divided into 2 partitions, the OS on the first one, and the second partition is just a data drive. The rest of the drives are all single partitions formatted to NTFS, except the 120 which is ext3 (the swap partition is also on the 120, set for 8MB)

WinXP has been setup for a long time, and I recently decided to set up a linux partition so that I can work on a few projects at home. I have some experience with Xubuntu, as its what I run on my laptop.

However, once I installed Xubuntu on the 120GB drive, I can no longer boot into any OS. When I got to GRUB, it would say "Error 22" and stop. Upon some research, I found that Error 22 is a "No partition found" error. One of the solutions I found was to change the order of hard drive priorities during boot in the BIOS. I moved the 120GB hard drive up to  the top, and now GRUB will load.

When I get into the GRUB menu now, I have the following options:
Xubuntu 7.10
Xubuntu 7.10 (recovery)
Xubuntu 7.10 (memtest86+)
Other OSes:
WinXP

When I choose any of the Xubuntu choices, GRUB says "Error 22: No Such Partition"
When I choose WinXP, GRUB says "Error 13: Invalid or Unsupported Executable Format"
(and for shitsngiggles, choosing Other OSes gave me "Error 11; Unrecognized Device String")

The only way I can seem to boot into anything is if I use the LiveCD. As for WinXP, I'm not sure if I may have damaged the MBR when I was attempting another solution to the original GRUB error. I had loaded into the LiveCD, opened a terminal, and typed the following:

```

> sudo grub

> find /boot/grub/stage1
(hd2,1)
> root (hd2,1)
> setup (hd2)
> setup (hd0)
> setup (hd1)
> setup (hd3)

```

I had added the last 3 setup commands because I read somewhere that it may be necessary to do that when you have multiple drives in the system.

Can anyone help me?

---

### Post by rsambuca on 2008-01-24
Can you post your menu.lst and fstab?
```

cat /boot/grub/menu.lst
cat /etc/fstab
```

---

### Post by smacd on 2008-01-24
/boot/grub/menu.lst
> ubuntu@ubuntu:/root$ cat ./boot/grub/menu.lst 
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
timeout         10

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
# kopt=root=UUID=f2b33cd2-84f8-435d-a79c-d30ae8c6b636 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f2b33cd2-84f8-435d-a79c-d30ae8c6b636 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f2b33cd2-84f8-435d-a79c-d30ae8c6b636 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


/etc/fstab
> ubuntu@ubuntu:/root$ cat ./etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd2
UUID=f2b33cd2-84f8-435d-a79c-d30ae8c6b636 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=D0F80FF4F80FD81C /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=D43412E33412C87E /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb1
UUID=D4E00B31E00B18FE /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=821C43D41C43C1C1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd1
UUID=1b5b7144-6009-4fc7-a379-0d7ec45b29ea none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by smacd on 2008-01-24
bump

anyone have any ideas how I can fix this? I really need to get my computer back up and running as soon as I can

---

### Post by logos34 on 2008-01-24
Boot to the grub menu, and on the highlighted main xubuntu kernel press 'e' to edit, 'e' again on the 'root' line...change to (hd**0**,1).  Press 'enter' and 'b' to boot.  If it works make the change permanent by editing menu.lst, correct 'groot' and root lines.

But since xubuntu/120 gb drive is first in the Bios hard disk order now, you'll have to change the windows stanza in menu.lst in order to boot XP on a [non-first hard drive]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by smacd on 2008-01-25
> **logos34 said:**
> Boot to the grub menu, and on the highlighted main xubuntu kernel press 'e' to edit, 'e' again on the 'root' line...change to (hd**0**,1).  Press 'enter' and 'b' to boot.  If it works make the change permanent by editing menu.lst, correct 'groot' and root lines.

But since xubuntu/120 gb drive is first in the Bios hard disk order now, you'll have to change the windows stanza in menu.lst in order to boot XP on a [non-first hard drive]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

I was assuming that in (hdX,Y), X was a physical location, not the boot order in BIOS. By physical location, I mean, for example lets say I have 1 hard drive on IDE0, 2 drives on IDE1, and 1 drive on my SATA line (which my computer calls IDE2). I figured that hd0 is the one on IDE0, hd1 is the master drive on IDE1, hd2 is the slave drive on IDE1, and hd3 is the SATA drive. so this assumption is incorrect?

Anyways, I will give that stuff a shot. thanks. hopefully it works.

---

### Post by logos34 on 2008-01-25
> **smacd said:**
> I figured that hd0 is the one on IDE0, hd1 is the master drive on IDE1, hd2 is the slave drive on IDE1, and hd3 is the SATA drive. so this assumption is incorrect?

hd0, hd1, etc. correspond to the boot order.  However, at least as far as IDE (PATA) disks are concerned, hda, hdb, hdc, hdd, etc. generally do reflect the physical location (IDE channel):

hda, hdb = Primary (IDE0) master and slave

hdc, hdd = Secondary (IDE1) master and slave

/dev/sda, /dev/hda, etc. is the way the OS (linux) and fdisk sees the disks.  The Bios and Grub see them as hd0, hd1, etc

---

### Post by smacd on 2008-01-25
logos34, you rock! thanks for the help, i managed to make both OSes load up using those modifications to the menu.lst. 

and that makes sense about the drives. i guess i was getting confused over the difference between hda and hd0, etc.

Thanks!

---

### Post by logos34 on 2008-01-25
> **smacd said:**
> logos34, you rock! thanks for the help, i managed to make both OSes load up using those modifications to the menu.lst. 

and that makes sense about the drives. i guess i was getting confused over the difference between hda and hd0, etc.

Thanks!

ok.  glad to hear.

yeah, the hda and hd0 business confuses a lot of people...whoever came up with those designations ought to be shot.

Mark thread as 'solved.' (>thread tools)

enjoy

---

