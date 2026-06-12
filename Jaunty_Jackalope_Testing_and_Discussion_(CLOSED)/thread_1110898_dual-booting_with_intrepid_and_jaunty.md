---
title: "dual-booting with intrepid and jaunty"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vanadium101 on 2009-03-30
I've installed a second install of Intrepid and keep the original grub for my first install.
I added the second install to menu.lst and updated and upgraded the second install to jaunty with "update-manager -d" which was successful. I edited menu.lst again and now I can't boot the 2.6.28-11-generic kernel but I can boot jaunty with the 2.6.27-11-generic kernel

how can i boot the new kernel with the first intrepid's grub?

---

### Post by ronacc on 2009-03-30
post your menu.lst

---

### Post by vanadium101 on 2009-03-30
here is menu.lst

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
timeout		4

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
# kopt=root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b7b8303f-8d33-4e87-957a-f46451111af2

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		b7b8303f-8d33-4e87-957a-f46451111af2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b7b8303f-8d33-4e87-957a-f46451111af2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

##title		Ubuntu 8.10, kernel 2.6.27-7-generic
##uuid		b7b8303f-8d33-4e87-957a-f46451111af2
##kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro quiet splash 
##initrd		/boot/initrd.img-2.6.27-7-generic
##quiet

##title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##uuid		b7b8303f-8d33-4e87-957a-f46451111af2
##kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro  single
##initrd		/boot/initrd.img-2.6.27-7-generic

##title		Ubuntu 8.10, memtest86+
##uuid		b7b8303f-8d33-4e87-957a-f46451111af2
##kernel		/boot/memtest86+.bin
##quiet

title		Ubuntu 9.04
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
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
title		HP Recovery
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

when i try boot the 2.6.8-11-generic kernel i comes up with a grub error saying that a file is not found

---

### Post by vanadium101 on 2009-03-31
i removed lilo and installed grub in jaunty which made no difference 

when trying to boot the new kernel i get error 15: file not found

---

### Post by uidb4056 on 2009-03-31
> **vanadium101 said:**
> here is menu.lst

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        4

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b7b8303f-8d33-4e87-957a-f46451111af2

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        b7b8303f-8d33-4e87-957a-f46451111af2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        b7b8303f-8d33-4e87-957a-f46451111af2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

##title        Ubuntu 8.10, kernel 2.6.27-7-generic
##uuid        b7b8303f-8d33-4e87-957a-f46451111af2
##kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro quiet splash 
##initrd        /boot/initrd.img-2.6.27-7-generic
##quiet

##title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##uuid        b7b8303f-8d33-4e87-957a-f46451111af2
##kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b7b8303f-8d33-4e87-957a-f46451111af2 ro  single
##initrd        /boot/initrd.img-2.6.27-7-generic

##title        Ubuntu 8.10, memtest86+
##uuid        b7b8303f-8d33-4e87-957a-f46451111af2
##kernel        /boot/memtest86+.bin
##quiet

title        Ubuntu 9.04
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-11-generic root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        HP Recovery
root        (hd0,1)
savedefault
makeactive
chainloader    +1

```when i try boot the 2.6.8-11-generic kernel i comes up with a grub error saying that a file is not found

I would suggest that you try to change 'root    (hd0,2)' by 'root   (hd0,3)' may be you have your swap partition on (hd0,2) and that is the reason of file not found.

Alternately you can change the root (hd0,2) by the uuid as you have for 8.10 in menu.lst, to know what is the uuid you can run in terminal 'sudo blkid'.

Edit: Looking at your menu.lst there is an inconsistency between the root (hd0,2) and the next line where you have root=/dev/sda7, how many partitions you have?, plase post the output of sudo blkid and sudo fdisk -l

---

### Post by cariboo on 2009-03-31
From the looks of your /boot/grub/menu.lst at one point you tell grub root is at /dev/sda3 and in the kernel line you say root is on /dev/sda7

I would use the configfile option to boot jaunty eg:

```
title    Jaunty Beta
root  (hd0,6)
configfle    /boot/grub/menu.lst
```

You may want to boot from the LiveCD to find out where /boot/grub actually is, in a terminal type:

```
sudo grub
```

then at the grub prompt type:

```
find /boot/grub/stage1
```

and note the results you get. Use what the find command comes up with.

Jim

---

### Post by loomsen on 2009-03-31
Maybe it helps to mention that the disk GRUB calls (hd0,0) is actually /dev/sda1...

hd[color=red]0[/color],[color=green]0[/color] = sd[color=red]a[/color][color=green]1[/color]

First 0 stands for the first detected disk, the 2nd 0 for the first partition on it. <=> hd0 = sda <=> (hd0,0) = sda1

Then u can specify, for instance 
root (hd0,5) 
if your desired boot device was sda6 for instance, or 
(hd1,2) for /dev/sdb3

(You device maybe called /dev/hda, doesnt matter, same story)


> 
title        Ubuntu 9.04
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-11-generic root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet


There you go, either (hd0,2) is wrong and should be (hd0,6), or /dev/sda7 should be /dev/sda3

---

### Post by vanadium101 on 2009-03-31
```
michael@michael-laptop:~$ blkid
/dev/sda1: UUID="09D8B1672C2466E4" TYPE="ntfs" 
/dev/sda2: UUID="0810D71A10D70D96" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="b7b8303f-8d33-4e87-957a-f46451111af2" TYPE="ext3" 
/dev/sda5: UUID="93b52638-5bf4-4809-ae69-d7969a0353fe" TYPE="swap" 
/dev/sda6: UUID="a0e0d3c4-d2ea-49a9-b1f1-5cc12ceeabc8" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
michael@michael-laptop:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd0eb661

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7581    60889048    7  HPFS/NTFS
/dev/sda2           37661       38913    10060800    7  HPFS/NTFS
/dev/sda3            7582        9074    11992522+  83  Linux
/dev/sda4            9075       37660   229617045    5  Extended
/dev/sda5           37412       37660     2000092+  82  Linux swap / Solaris
/dev/sda6            9075       35543   212612179+  83  Linux
/dev/sda7           35544       37326    14321916   83  Linux
/dev/sda8           37327       37410      674698+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

here is a screen shot of gparted to help get an idea of how the partitions are
[IMG]http://i122.photobucket.com/albums/o255/vanadium101/gparted.png[/IMG]

---

### Post by rplantz on 2009-03-31
When grub give you the file not found error, you can go into grub's edit mode and temporarily change the (hd0,0) to some of the other suggested values here and see which one works. Once you have figured it out, don't forget to change your menu.lst to make this a permanent change.

---

### Post by vanadium101 on 2009-04-01
i feel so stupid ](*,) i needed (hd0,6) not (hd0,2)

thanks for all the help

---

### Post by loomsen on 2009-04-01
Dont we all sometimes :D

[Good book bttw, kinda matching :)](http://en.wikipedia.org/wiki/The_Discovery_of_Slowness)

---

### Post by rplantz on 2009-04-02
> **vanadium101 said:**
> i feel so stupid ](*,) i needed (hd0,6) not (hd0,2)

Ah, yes, the most common user error. (You need paper and pencil to see how this works.)

The error code is:

ID <write ten in numeral format here> T

Done it many times myself.

---

### Post by loomsen on 2009-04-02
> **rplantz said:**
> Ah, yes, the most common user error. (You need paper and pencil to see how this works.)

The error code is:

ID <write ten in numeral format here> T

Done it many times myself.

Or you can simply read my post prior to this one ^^

---

