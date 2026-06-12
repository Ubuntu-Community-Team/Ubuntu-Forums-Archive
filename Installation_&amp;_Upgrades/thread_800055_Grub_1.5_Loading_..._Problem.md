---
title: "Grub 1.5 Loading ... Problem"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by marcon00 on 2008-05-19
Hello, Im not sure where im supposed to post it, so just move it in case :)

I know that there are many topics concerning Grub 1.5 stage freezes and such-alike problems, the thing is till now i did not find an answer. I tried with 7.04 and now with Hardy the same problem. What is the problem ?

I got dual bot,Vista,n Hardy. Since the release of Hardy i haven't been on vista since then :) The Problem is, when im on Linux and i reboot, everything loads fine, but if i choose to go to vista and then reboot, my laptop gets stuck on Grub stage 1.5 Loading .. i need to shut it down 3 times, exactly 3 times to get the boot menu back by the 4th time :S weird.. i Tried deleting stage 1.5 , with no success. Reinstalling - No success. 

Oh and i noticed if i keep any CD/DVD in my drive, it will stuck on Stage 1.5 as well, until i remove it so it will continue normally.

ANyone ?? :)

---

### Post by Marco7 on 2008-05-19
For my vista n' hardy system I have to select the second windows operating system in the list for it to boot, and my Acer laptop will hang in the BIOS on a hardy restart, so I always shutdown first.

---

### Post by Pumalite on 2008-05-19
Post:
sudo fdisk -l

---

### Post by meierfra. on 2008-05-19
I suggest to use EasyBCD (see my signature)

---

### Post by marcon00 on 2008-05-19
> **Pumalite said:**
> Post:
sudo fdisk -l

```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92be61fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3969    31880961    7  HPFS/NTFS
/dev/sda2            3970       10641    53592840    7  HPFS/NTFS
/dev/sda3           10642       14593    31744440    5  Extended
/dev/sda5           13931       14593     5325516   82  Linux swap / Solaris
/dev/sda6           10642       13930    26418829+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47474746

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    5  Extended
/dev/sdb5               1        2656    21334257    7  HPFS/NTFS
/dev/sdb6            2657        4058    11261533+  83  Linux
/dev/sdb7            4059       14593    84622356    7  HPFS/NTFS

```

---

### Post by Pumalite on 2008-05-19
Post:
cat /boot/grub/menu.lst

---

### Post by marcon00 on 2008-05-19
> **Pumalite said:**
> Post:
cat /boot/grub/menu.lst

```

cat /boot/grub/menu.lst
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
timeout		2

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
# kopt=root=UUID=f799b5b9-6e0e-491f-9375-2bc216014ee5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f799b5b9-6e0e-491f-9375-2bc216014ee5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f799b5b9-6e0e-491f-9375-2bc216014ee5 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f799b5b9-6e0e-491f-9375-2bc216014ee5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f799b5b9-6e0e-491f-9375-2bc216014ee5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by Pumalite on 2008-05-19
How did you partition when you installed Ubuntu?

---

### Post by marcon00 on 2008-05-19
> **Pumalite said:**
> How did you partition when you installed Ubuntu?

using Gparted from LiveCd with 7.04 ubuntu. manual setting for

Vista Partition
Temporary Downloads
Linux Ext3
Swap

///////

Archive
/home
BackUps

---

### Post by Pumalite on 2008-05-19
Sorry; but, bad news. If you want dual boot with Vista, you have to use the Vista partitioner to allocate space for Ubuntu first. You cannot partition with the Ubuntu CD.

---

### Post by marcon00 on 2008-05-19
> **Pumalite said:**
> Sorry; but, bad news. If you want dual boot with Vista, you have to use the Vista partitioner to allocate space for Ubuntu first. You cannot partition with the Ubuntu CD.

Possible :) well .. i will just wait till the next BSOD that is irreversible (probably matter of days) , or simply never boot into vista ( preferable ) 

Thanks ;):popcorn:

** EDIT: Any explanation for that ? **

---

### Post by Pumalite on 2008-05-19
You are welcome. Get rid of Vista. If you need Windows go with XP in a Virtual environment.

---

### Post by marcon00 on 2008-05-19
> **Pumalite said:**
> You are welcome. Get rid of Vista. If you need Windows go with XP in a Virtual environment.

 U think i didnt try ? I found it very difficult rebuilding and finding drivers for XP with my laptop ! i just use Vista for Itunes :$ i mean i know that there are some other managers, but frankly im still not convinced too much, not that flexible yet. And Wine is not supporting Itunes.

---

### Post by Pumalite on 2008-05-19
I'm talking VMware:
[http://www.vmware.com/](http://www.vmware.com/)

---

### Post by marcon00 on 2008-05-19
> **Pumalite said:**
> I'm talking VMware:
[http://www.vmware.com/](http://www.vmware.com/)

You mean like running Xp within linux ? :) but would that support USB for instance ? wouldnt it be creating conflict with the devices ? never tried it, heard of it, no idea about it.

---

### Post by Pumalite on 2008-05-20
Go ahead and learn.

---

