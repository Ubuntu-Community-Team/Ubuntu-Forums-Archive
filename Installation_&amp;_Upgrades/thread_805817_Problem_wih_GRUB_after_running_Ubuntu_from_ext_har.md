---
title: "Problem wih GRUB after running Ubuntu from ext hard drive"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by raul_ocfonseca on 2008-05-24
Dear All,

I have just installed Hardy Heron on an external hard drive to run it in my laptop. It all works fine except that I can only run Vista (yes I know it is bad but I would like to keep it) if I have the external hard drive plugged in, since GRUB displays error 21 (or something like that) and does not let me choose the OS I want to boot. I presume that GRUB is present mostly in the external hard drive or something. Can anybody help me solve this issue? I would like to be able to load windows even if the ext hard drive is not plugged in.

Many thanks in advance,

Raúl

---

### Post by Rallg on 2008-05-24
Edit: Meierfra's post (below) is more useful that what I wrote here originally, so I removed my original response.

---

### Post by meierfra. on 2008-05-24
I wrote a howto for that situation. Click on Dual in my signature. If you use ubuntu 8.04  you should also look at post 14 and 15 in that thread.

---

### Post by raul_ocfonseca on 2008-05-24
I have tried it with no success. Now I cannot access Ubuntu at all (I guess i can restore the original grub file) and I still need the external hard drive to boot vista. I tried to use mbrfix to restore my vistas's mbr but vista tells me the file is in use by a process and cannot complete the operation. Any ideas?

---

### Post by meierfra. on 2008-05-24
You should be able to boot int Ubuntu, by selecting "ubuntu" at the grub menu. But do not press enter, press "e" instead. Press "e" again to edit the first line. Change "root (hd?,?)" back to what is was (probably you just have to change the first number from "0" to "1")  Press enter and then "esc" This gets you back to the grub menu and you should be able to boot into ubuntu. 
If this does not work, boot from the Ubuntu LiveCD.

In any case  post your menu.lst and  the output of

```
sudo fdisk -l
```

Did you get any error messages? Does the grub menu appear when your try to  boot  from the external drive? 

Alternatively, you could try EasyBCD. Its a nice bootloader for Vista, which  lets you add Ubuntu to the Vista Boot menu. See my signature.

---

### Post by raul_ocfonseca on 2008-05-25
Here is my menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# root		(hd1,1)
# map(hd0)(hd1)
# map(hd1)(hd0)
# savedefault
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
# kopt=root=UUID=8edcb79a-6376-4117-93af-24a40d8e5b9a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8edcb79a-6376-4117-93af-24a40d8e5b9a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8edcb79a-6376-4117-93af-24a40d8e5b9a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


The way it was before is:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=8edcb79a-6376-4117-93af-24a40d8e5b9a ro

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8edcb79a-6376-4117-93af-24a40d8e5b9a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8edcb79a-6376-4117-93af-24a40d8e5b9a ro single
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
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


I will try what you suggested and get back to you shortly.

Thanks heaps,

Raul

---

### Post by raul_ocfonseca on 2008-05-25
As long as the ext drive is connected i can access Vista. I actually have two Vista/Longhorn partitions and I can only boot up from the second one. I tried the solution you suggested and I can now access my ubuntu installation. Thanks for that! I haven't worked on linux form almost a year so I am incredibly rusty. 

Here is the result of the <sudo fdisk -l> command:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         893     7168000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         893       16094   122098688    7  HPFS/NTFS
/dev/sda3           16094       30402   114930688    f  W95 Ext'd (LBA)
/dev/sda5           16094       30402   114929664    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5d64e26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         240     1927768+   c  W95 FAT32 (LBA)
/dev/sdb2             241       24321   193430632+   5  Extended
/dev/sdb5             241       23564   187349998+  83  Linux
/dev/sdb6           23565       24321     6080571   82  Linux swap / Solaris


again any help is appreciated.

Cheers,

Raúl

---

### Post by raul_ocfonseca on 2008-05-25
Okay i used ms-sys to restore Vista's mbr. I assume that I can now fix my ubuntu install using liveCD? I had to restore Vista's mbr because I am using a work laptop and I wanted to restore it to what it was before.

Thanks in advance,

Raul

---

### Post by meierfra. on 2008-05-25
Your menu.lst looks fine (except for the Windows Item, but we'll work on that later)

So you should be able to solve you problem by reinstalling  Grub and booting of your external drive:

Boot from the ubuntu  livecd. Open a terminal and type

```
sudo grub
```

at the "grub>" prompt

```

find /boot/grub/menu.lst
```

This should return (hd1,4). If it did :

```
root (hd1,4)
setup (hd1)
quit
```


(If "find /boot/grub/menu.lst" returned  "(hd0,4)" do  

root (hd0,4) 
setup (hd0) 
quit

 instead)


Reboot and make sure to change the boot order in the bios. The external drive needs to be first.

---

### Post by raul_ocfonseca on 2008-05-26
Thanks will try as soon as I can and let you know.

Cheers,

Raúl

---

