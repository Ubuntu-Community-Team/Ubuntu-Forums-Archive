---
title: "Help with XP/Feisty Dual Boot"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by aliendisaster on 2007-05-12
I installed Feisty on a Dual Boot with Windows XP.  Everything works good with Ubuntu (I'm on it now and haven't even wanted to go back into XP for about a month now).  I now need to go into XP to export some registry keys for Wine (trying to setting up Macromedia Flash 8 ).  When I attempt to boot to XP, I recieve:

A disk error has occurred.

On the initial install, there was an error where grub was setup to boot to the wrong hard drive (I have a SATA drive with windows/ubuntu installed and an IDE drive with files).  I fixed that in a grub config file (can't remember where right now though - I believe it was /boot/grub/device.map).  I checked the grub settings and it is attempting to boot to the correct partition for XP.  I saw the problem with XP then but didn't worry about it because I figured I could just mount the drive and pull the files off (which for the most part I can).  However, I have no clue how to pull the registry keys out without regedit.

My question(s):

Does it sound like I destroyed part of my windows partition?  I can still see all the files when I mount the partition in Ubuntu.

Is there a way to pull out the reigstry keys without booting into windows?

---

### Post by bulldog on 2007-05-12
You can try to repair a broken windows from it's install disk.
Maybe you even can run chkdsk.exe from the install disk,but I'm not sure about that.

How to get to the registry without booting windows,I can't tell you,never have the need to do such a thing.

---

### Post by aliendisaster on 2007-05-12
Thanks for the reply.  I attempted repairing the disk with the XP cd and running chkdsk but, unfortunately, this was in vain.  Any other ideas I could try before destroying it and re-installing (then reinstalling my apps just to get the regkeys)?

Anyone else know how I might be able to pull the registry keys out without booting to windows?

---

### Post by confused57 on 2007-05-12
Probably won't help, but here's a thread about hard disk error:
[http://ubuntuforums.org/showthread.php?t=363355](http://ubuntuforums.org/showthread.php?t=363355)

You might want to post your menu.lst & fdisk:
```
gedit /boot/grub/menu.lst
sudo fdisk -l
```

and your device.map:
```
gedit /boot/grub/device.map
```

I don't have much experience with troubleshooting Window's problems, so I can't help you if that's the case...grub or configuration problem, someone may see a solution.

Added: You might want to try the Super Grub Disk to boot your Windows:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by aliendisaster on 2007-05-12
I'm starting to think its an error on the windows side.  I setup VMware to attempt to boot the partition as a "hey it might work" thing but I get the same thing with that.  It also appears that I may have setup grub on my windows partition so that may have messed up some configuration (I'm not too familiar with grub).

fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sdb2            4865        4988      996030   82  Linux swap / Solaris
/dev/sdb3            4989        9726    38057985   83  Linux

```

menu.lst:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=fab553d2-675d-48cb-b5c5-3979e048c085 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=fab553d2-675d-48cb-b5c5-3979e048c085 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=fab553d2-675d-48cb-b5c5-3979e048c085 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

device.map:
```

(hd1)   /dev/sda
(hd0)   /dev/sdb

```

boot.ini:
```

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Thanks for all help.

---

### Post by confused57 on 2007-05-12
When you tried to repair your Windows from the recovery console, using the Window's install cd, did you run FIXBOOT?...this might repair & overwrite grub if it's installed to your Window's partition.  If you ran FIXMBR from the recovery console, this would overwrite grub, which could be reinstalled using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Also, you shouldn't need the mapping commands to boot Windows:
```
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1
```

Added:  Try this Window's entry first, before attempting to repair Windows.

---

### Post by aliendisaster on 2007-05-13
> **confused57 said:**
> When you tried to repair your Windows from the recovery console, using the Window's install cd, did you run FIXBOOT?...this might repair & overwrite grub if it's installed to your Window's partition.  If you ran FIXMBR from the recovery console, this would overwrite grub, which could be reinstalled using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Also, you shouldn't need the mapping commands to boot Windows:
```
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1
```

Added:  Try this Window's entry first, before attempting to repair Windows.

Thanks for your help.  The problem was with the mapping.  When I first installed Ubuntu, GRUB saw the wrong drive as the first hard drive.  I did some research on grub last night and saw the mapping was only needed when windows was not on the first hard drive.  When I removed this, I was able to boot into windows.  

Thanks again for all your help.

---

