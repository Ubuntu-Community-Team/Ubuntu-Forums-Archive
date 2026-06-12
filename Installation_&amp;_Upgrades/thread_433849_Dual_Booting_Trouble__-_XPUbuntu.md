---
title: "Dual Booting Trouble  - XP/Ubuntu"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Joshsterm on 2007-05-05
I have a dell inspiron 1505 that had XP already installed.  I decided to try out ubuntu, so I got a Dapper Drake live CD and installed it.  It only has 1 hard drive, so i had to put the two OSs on the same one.  I made a partition for ubuntu that came right after my ubuntu partition. After a lot of configuration and figuring out the ATI drives, It installed fine, and then I upgraded all the way to Feisty. 

 I didn't notice it then, but the GRUB menu does not have Windows anywhere on it.  The windows partition wasn't lost, I can see it in Ubuntu, it just can't be booted.   I've looked around the internet a lot for help, and even tried a few things (modifying the grub config file to add windows) but nothing has worked.  I pretty new to linux and everything, so a lot of the instructions I've seen have been really confusing.  Can anyone explain how to do this simply?  My goal is to easily dual boot the two.  Thanks a lot!

---

### Post by aysiu on 2007-05-05
Can you post the output of these [terminal](http://www.psychocats.net/ubuntu/terminal) commands? ```
cat /boot/grub/menu.lst
sudo fdisk -l
```

Just copy and paste the commands into the terminal and copy and paste the output back here.

---

### Post by Joshsterm on 2007-05-05
**Yeah, the output of cat /boot/grub/menu.lst is:**

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=a6c00dfc-87f0-4d02-ad2e-0ff3ac7031a0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=a6c00dfc-87f0-4d02-ad2e-0ff3ac7031a0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
savedefault

title           Windows XP
                rootnoverify (hd0,1)
                chainloader +1

title           Windows XP try 2
                rootnoverify (hd0,0)
                chainloader +1


title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=a6c00dfc-87f0-4d02-ad2e-0ff3ac7031a0 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=a6c00dfc-87f0-4d02-ad2e-0ff3ac7031a0 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=a6c00dfc-87f0-4d02-ad2e-0ff3ac7031a0 ro single
initrd          /boot/initrd.img-2.6.17-11-386

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=a6c00dfc-87f0-4d02-ad2e-0ff3ac7031a0 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=a6c00dfc-87f0-4d02-ad2e-0ff3ac7031a0 ro single
initrd          /boot/initrd.img-2.6.15-26-386

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

**and the output of sudo fdisk -l was:**

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        5968    47889765    f  W95 Ext'd (LBA)
/dev/sda3   *        5969       11581    45086422+  83  Linux
/dev/sda4           11582       11978     3188902+  82  Linux swap / Solaris
/dev/sda5               7        5968    47889733+   7  HPFS/NTFS

---

### Post by aysiu on 2007-05-05
> **Joshsterm said:**
> ```
title           Windows XP
                rootnoverify (hd0,1)
                chainloader +1

title           Windows XP try 2
                rootnoverify (hd0,0)
                chainloader +1
``` ```
/dev/sda5               7        5968    47889733+   7  HPFS/NTFS
``` Hm. That's weird. There's a kind of half entry for XP and then a "try 2" half entry for it. The "try 2" one specifies (hd0,0) or /dev/sda1, but  Windows is actually on /dev/sda5. It looks as if maybe Ubuntu is trying to dual boot to the Dell utility partition?

The Windows entry on my laptop looks like this: ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1
``` So maybe you can try something like ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,4)
savedefault
makeactive
chainloader     +1
```

---

### Post by bulldog on 2007-05-05
Did see this many times now.
In my understanding,it's almost impossible to boot windows from a logical partition.
There seems to be a way,however,it's in this topic.

[http://ubuntuforums.org/showthread.php?t=429805](http://ubuntuforums.org/showthread.php?t=429805)

But it won't be without some risks.

Better solution would be,if I may say so,to mount your windows and copy your valuable data.
And reinstall windows in a primary partition,preferable the first one.

---

