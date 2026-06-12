---
title: "Cannot boot XP in GRUB"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by bpalyshka on 2008-07-13
Hi someone help me look at this and tell me what im doing wrong.

this is my fdisk

> satan@Lucifer:~$ fdisk -l
satan@Lucifer:~$ sudo fdisk -l
[sudo] password for satan:

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa67b51e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdb5               2        9729    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb393e80b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    c  W95 FAT32 (LBA)

Which states i have 4 hard drives a 10GB for Linux a 40 GB for windows a 80GB slave and the other is a 250GB external hard drive.

Ok, windows is installed on the 40 and i just installed and upgraded kbuntu on the 10GB.  When i get to my GRUB boot loader is states Win XP is there but gives me a error when i try to boot into it.

here is what my /boot/grub/menu.lst looks like:

>  menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=e80d190f-6804-4e95-9f4d-704038fc826d ro

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
ss## alternative kernel options
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

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e80d190f-6804-4e95-9f4d-704038fc826d ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e80d190f-6804-4e95-9f4d-704038fc826d ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.22-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=e80d190f-6804-4e95-9f4d-704038fc826d ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=e80d190f-6804-4e95-9f4d-704038fc826d ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd1) (hd0)
map             (hd0) (hd1)
chainloader     +1





Suggestions?:confused:   i added this and changed it to this:> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd2) (hd0)
map             (hd0) (hd2)
chainloader     +1

And is said that its missing a file NTLDR

ideas?  should i run my xp cd for a recovery?

---

### Post by logos34 on 2008-07-13
that's what I'd have done--tried '(hd2,0)'....The 'makeactive' command should be enough, but you could also mark it with boot (*) flag:

sudo cfdisk /dev/sdc

highlight sdc1>Flags>mark 'Boot'>Esc>quit

or use gparted>sdc1>right-click>manage flags>boot

---

### Post by bpalyshka on 2008-07-13
> **logos34 said:**
> that's what I'd have done--tried '(hd2,0)'....The 'makeactive' command should be enough, but you could also mark it with boot (*) flag:

sudo cfdisk /dev/sdc

highlight sdc1>Flags>mark 'Boot'>Esc>quit

or use gparted>sdc1>right-click>manage flags>boot



ok changed it to bootable but i still get the same error, does this mean i need to change something on my windows drive to make it bootable. install grub on that drive maybe.

Help

---

### Post by logos34 on 2008-07-13
Can you boot directly to windows using it's own bootloader?  Change the windows drive to first place in the Bios hard disk boot priority.  If still no go, see this page:
[http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

---

### Post by sandysandy on 2008-07-13
there is a utility called Super Grub ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

which u can download and burn a bootable CD.

with the Super Grub Disk u can try and do some trouble shooting / booting.

regards

---

