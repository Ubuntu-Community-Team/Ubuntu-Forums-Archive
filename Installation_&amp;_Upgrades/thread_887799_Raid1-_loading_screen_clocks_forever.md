---
title: "Raid1- loading screen clocks forever"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by vonce8 on 2008-08-12
**Background:** 
I have a shuttle PC (which I bought as a bare bones system) with two drives configured as a single Raid1 volume. There is an existing WindowsXP installation (which I need to keep). Windows is using the on board intel ich9r ahci/raid controller. To install ubuntu, I booted into a 8.04.1 x86_64 live CD, and followed the [FakeRaidHowto](http://ubuntuforums.org/showthread.php?t=886912&highlight=raid). There is no separate /boot partition, / is ext3, there's 512MB of swap (which doesn't appear here for some reason - possibly because it is active as I booted to the live CD to write this posts?), Windows is the first partition on the drive and is NTFS.

**Problem:** 
Grub loads, I choose Ubuntu 8.04, it shows the ubuntu loading screen, but it clocks forever- the bar just bounces back and forth indefinitely. It never goes into the left to right loading stage. No errors.

I suspect it's a misconfigured fstab but I'm not an expert, so I'll dump everything that might be relevant. Thanks in advance for everyone who takes the time to ponder and/or respond.


**Notes:**
I've already attempted to install Windows to its own mirrored volume (managed via the onboard controller) and leave the second half of each disk untouched by the onboard raid. My thought was that Linux could use its own Raid software. I found that I couldn't boot directly into the second volume regardless of how I set the boot flags/mbr. There is no way to set a particular volume as the boot though the embeded intel configuration utility.

This is what it shows when I attempt to boot into recovery mode:
[[IMG]http://img291.imageshack.us/img291/5866/recoverymodekm7.th.jpg[/IMG]](http://img291.imageshack.us/my.php?image=recoverymodekm7.jpg)

**Configuration information dump:**
```
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_cgfieahjb_Volume0" already active  
RAID set "isw_cgfieahjb_Volume01" already active 
//02 is swap (I'm running in the liveCD atm)//
RAID set "isw_cgfieahjb_Volume03" already active
```

I think when booting into the live cd it auto-mounted my swap area so that isn't showing up.

```
ubuntu@ubuntu:~$ sudo fdisk /dev/mapper/isw_cgfieahjb_Volume0

The number of cylinders for this disk is set to 60800.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/isw_cgfieahjb_Volume0: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa64ba64b

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfieahjb_Volume0p1               1       39161   314560701    7  HPFS/NTFS
/dev/mapper/isw_cgfieahjb_Volume0p3   *       39225       60800   173309220   83  Linux

Command (m for help): 

```

```
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdb: isw, "isw_cgfieahjb", GROUP, ok, 976773166 sectors, data@ 0
/dev/sda: isw, "isw_cgfieahjb", GROUP, ok, 976773166 sectors, data@ 0
```
```

//mounted linux / as /target
//sudo chroot /target
root@ubuntu:/# cat etc/mtab
/dev/mapper/isw_cgfieahjb_Volume03 / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noatime,relatime 0 0
tmpfs /lib/modules/2.6.24-19-generic/volatile tmpfs rw,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0

```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/isw_cgfieahjb_Volume03
UUID=f1799843-ff1f-4fe5-9ce7-55dddf1d30a8 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


(I'm aware I have XP twice :))
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
timeout		3

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
# kopt=root=/dev/mapper/isw_cgfieahjb ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title            WindowsXP
rootnoverify     (hd0,0)
chainloader +1


title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)

kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/mapper/isw_cgfieahjb_Volume03 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/mapper/isw_cgfieahjb_Volume03 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


title WindowsXP
rootnoverify (hd0,0)
chainloader +1
```


I probably made some mistakes in terminology and reasoning but you get the idea. Thanks for the help in advance.

---

### Post by vonce8 on 2008-08-28
Bump. I'd really like to get ubuntu working

---

