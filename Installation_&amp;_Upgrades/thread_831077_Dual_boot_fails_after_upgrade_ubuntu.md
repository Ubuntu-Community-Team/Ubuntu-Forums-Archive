---
title: "Dual boot fails after upgrade ubuntu"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2008-06-16
I have installed ubuntu 7.10, dual boot with windows xp.
After upgrade to ubuntu 8.04, I can still dual boot with windows xp.

But recently, i upgrade some security upgrades in ubuntu 8.04, i can no longer upgrade to windows xp.

Can you please tell me how can i fix my problem?

Thank you.

---

### Post by imneo on 2008-06-16
> I have installed ubuntu 7.10, dual boot with windows xp.
After upgrade to ubuntu 8.04, I can still dual boot with windows xp.

But recently, i upgrade some security upgrades in ubuntu 8.04, i can no longer upgrade to windows xp.

Can you please tell me how can i fix my problem?

Thank you.

i guess you mean you can't boot your xp.
if so you should edit your /boot/grub/menu.lst file
and make sure your xp is there.

---

### Post by tfl0w on 2008-06-16
wXP is can't boot, or just there is no it in GRUB menu?
if second - finde "Super Grub CD", burn and boot from it (or "with it", sorry for my english, please =\ ), and read HOWTO. 

unfortunately, i can't explain how to use it step by sep, it's dificulte for me in english.

---

### Post by yinglcs2 on 2008-06-21
Thanks. I do see the Windows XP in the  /boot/grub/menu.lst
but i just can't boot up windows when I select windows xp.

Again, it used to work. I have ubuntu 7.10 , it worked. And then upgrade to ubuntu 8.04, it still works. Until recently, I install some security upgrade (a new linux kernel) via the update manager,  it stops working.


```


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Windows NT/2000/XP
root		(hd1,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by hal8000 on 2008-06-21
> **yinglcs2 said:**
> Thanks. I do see the Windows XP in the  /boot/grub/menu.lst
but i just can't boot up windows when I select windows xp.

Again, it used to work. I have ubuntu 7.10 , it worked. And then upgrade to ubuntu 8.04, it still works. Until recently, I install some security upgrade (a new linux kernel) via the update manager,  it stops working.


```


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Windows NT/2000/XP
root		(hd1,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```



Not sure why you have mapping commands in your grub, this is possibly where the problem resides, you now need to tell us where you think windows is, but we'll see what your system says. Post the output of

sudo fdisk -l


The fix is modifying /boot/grub/menu.lst

With 2 hard drives grub calls the first had drive hd0 and the second hard drive hd1. Heres an extract from my menu.lst

cat /boot/grub/menu.lst
--snip--
title Ubuntu
# With libATA dev/sda is now /dev/sdb
kernel (hd1,4)/boot/vmlinuz root=/dev/sdb5 noresume ro splash
initrd (hd1,4)/boot/initrd.img


title PCBSD
root (hd0,2)
makeactive
chainloader +1

title DreamLinux
kernel (hd1,10)/boot/vmlinuz root=/dev/sda11 noresume ro splash
initrd (hd1,10)/boot/initrd.img

title Windows
root (hd0,0)
chainloader +1

--snip--


Windows always wants the first partition, so once you post the output of fdisk -l  we can see which partition has an NTFS. Chainloading is all thats necessary with windows (and FreeBSD come to think about it) with grub you can boot just about anything.

---

### Post by yinglcs2 on 2008-06-21
Thank you very much for your help.  I havn't touched the  /boot/grub/menu.lst before, so I don't know why it has the error you mentioned.

Here is the output of ' sudo fdisk -l':

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825       11576    62267940    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           11577       12161     4694760   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5            9665        9677      104391   83  Linux
/dev/sda6            9678       11576    15253686   83  Linux
/dev/sda7            3825        5651    14675314+  83  Linux
/dev/sda8            5652        5955     2441848+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44e4be6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         304     2441848+  82  Linux swap / Solaris
/dev/sdb2             305        4013    29792542+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6374    51199123+   b  W95 FAT32
/dev/sdc2            6375       12809    51689137+   b  W95 FAT32
/dev/sdc3           12810       19184    51207187+   f  W95 Ext'd (LBA)
/dev/sdc5           12810       19184    51207156    b  W95 FAT32



```

Here is my /boot/grub/menu.lst:

```

$ more /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=ee7b84cb-dbae-469a-a616-22e965ed56cc ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee7b84cb-dbae-469a-a61
6-22e965ed56cc ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Windows NT/2000/XP
root		(hd1,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cbe6046d-1f91-4588-9ea
6-a93b439d8526 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cbe6046d-1f91-4588-9ea
6-a93b439d8526 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu, memtest86+ (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/memtest86+.bin  
savedefault
boot



```
Thank you for any pointers.

---

