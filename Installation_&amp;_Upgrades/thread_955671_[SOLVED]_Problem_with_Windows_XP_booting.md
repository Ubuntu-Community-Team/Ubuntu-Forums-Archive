---
title: "[SOLVED] Problem with Windows XP booting"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by mrmichael on 2008-10-22
Greetings!
I am new to linux and I have installed on my primary partition Ubuntu 8.04.
Today I resided my partition and installed Windows XP. Then I reinstalled grub but when I choose "Microsoft Windows XP" from the grub menu it shows a black screen with a "Starting Up" and nothing happens.

Should I edit some sort of file, and if yes what exactly should I do?

Cheers,
Mike

---

### Post by esmailgad on 2008-10-22
> **mrmichael said:**
> Greetings!
I am new to linux and I have installed on my primary partition Ubuntu 8.04.
Today I resided my partition and installed Windows XP. Then I reinstalled grub but when I choose "Microsoft Windows XP" from the grub menu it shows a black screen with a "Starting Up" and nothing happens.

Should I edit some sort of file, and if yes what exactly should I do?

Cheers,
Mike

Normaly we do it in the other direction. Windows does not like to have other operating systems with it. So I think you have to:
1-Install Windows and during installation delete other partitions.
2- Once widows startes, create new logical parition with the size you want from disk managment
3-restart and use the live CD of ubuntu
4-During installation use the option of installing ubuntu in the largest empty (free) space.
5-Once installation finishes restart and you will have the grub window working correctly

This is the safest method to have both operating systems together

---

### Post by mrmichael on 2008-10-22
Thanks for the quick reply esmailgad!
Is there any way to avoid the format and the re-install of ubuntu?
I would appreciate it!

Cheers,
Mike

---

### Post by caljohnsmith on 2008-10-22
If reinstalling everything is an option, then that may be a good way to avoid some troubleshooting. If you decide to do that, make sure you have all your partitions set up ahead of time, then make sure you install Windows before Ubuntu, and also be sure to install Windows to a primary partition (not a logical one). 

Or, if you're lucky, it may be that fixing Windows will be easy. If you want to go that route, please first post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And then boot your Windows XP Install CD, go to the Recovery Console, and run the following commands:
```
fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. Reboot, see if that changes anything. We can work from there if you want.

---

### Post by esmailgad on 2008-10-22
> **mrmichael said:**
> Thanks for the quick reply esmailgad!
Is there any way to avoid the format and the re-install of ubuntu?
I would appreciate it!

Cheers,
Mike

Formating will give a cleaner and more stable system for both operating systems. Also, it will be faster than trying to correct the problem. since you are new with ubuntu, this will avoid you from entring in the hasle of using linux commands. I am sorry at this stage I cann't advise you

---

### Post by mrmichael on 2008-10-22
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc69a59f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488397167   244198552+  42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x35ba35ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   219704939   109852438+  83  Linux
/dev/sdb2       219704940   303467849    41881455    7  HPFS/NTFS
/dev/sdb3       303467850   312576704     4554427+   5  Extended
/dev/sdb5       303467913   312576704     4554396   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05fbe43d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001   42  SFS


```

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
# root		(hd0,1)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,0)
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
# kopt=root=UUID=cdb72aae-c472-4f21-a50c-041ff895b884 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cdb72aae-c472-4f21-a50c-041ff895b884 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cdb72aae-c472-4f21-a50c-041ff895b884 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1


```

Thank you for your post caljohnsmith!
Here is my fdisk -lu and my menu.lst

Cheers,
Mike

---

### Post by caljohnsmith on 2008-10-22
Looks like you may be lucky, because correcting your Grub's menu.lst entry might be all it will take to get Win XP to boot OK. First do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom where it has your Win XP entry, replace it with:
```
title		Microsoft Windows XP Professional
root		(hd0,1)
makeactive
chainloader	+1
```
Reboot, try Windows, and let me know exactly what happens. :)

---

### Post by mrmichael on 2008-10-22
Yeap it worked!!!!
Thank you very much!!!!

---

### Post by caljohnsmith on 2008-10-22
No problem, cheers and have fun Ubuntu-ing. :)

---

