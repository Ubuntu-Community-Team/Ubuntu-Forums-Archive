---
title: "[SOLVED] Dual Boot 6.06 and 7.10"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by SneakPeak on 2007-12-27
Hi

I am in the process of upgrading from 6.06 to 7.10.  (Dapper to Gutsy).  I currently run a dual boot with Windows XP.  (My wife has to have XP for work Agghhhh!!!).  

I didn't want to give up my working Dapper until I had Gutsy working as required.  I therefore wanted to go to a tri-boot.  XP, Dapper and Gutsy.  I shrank the XP partition to make space for Gutsy.  I then ran the Gutsy installation CD which I had downloaded and burnt.  All went well and I was told my installation was successful.  

Unfortunately Grub only gives me the option to boot XP and Dapper, not Gutsy.  I don't know how to fix this.  My hard drive setup is as follows:

/dev/sda1 is my XP partition.  It is "mounted" on /XP
/dev/sda2 is my Dapper partition.  It is "mounted" on /
/dev/sda3 is my Gutsy partition.  It is not mounted and I don't know how to!!
/dev/sda4 is my Swap partition (for Ubunutu).

I would be greatful if someone could explain to me how I get Gutsy to boot.

Thanks

SneakPeak:confused:

---

### Post by Pumalite on 2007-12-27
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by SneakPeak on 2007-12-27
sudo fdisk -lu gives:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2       122881185   152199809    14659312+  83  Linux
/dev/sda3        81915435   122881184    20482875   83  Linux
/dev/sda4       154240065   156296384     1028160   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdc: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63    16498754     8249346   83  Linux

cat /boot/grub/menu.lst gives:

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
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-29-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-29-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-29-386
boot

#title          Ubuntu, kernel 2.6.15-28-386
#root           (hd0,1)
#kernel         /boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-28-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-28-386 (recovery mode)
#root           (hd0,1)
#kernel         /boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single
#initrd         /boot/initrd.img-2.6.15-28-386
#boot

#title          Ubuntu, kernel 2.6.15-23-386
#root           (hd0,1)
#kernel         /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root           (hd0,1)
#kernel         /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
#initrd         /boot/initrd.img-2.6.15-23-386
#boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1


Sneak Peak

---

### Post by Pumalite on 2007-12-28
Where is sdb? or What is sdb?

---

### Post by LaRoza on 2007-12-28
> **Pumalite said:**
> Where is sdb? or What is sdb?

There is no sdb in that file or output?

The OP appears to have one disk with 4 partitions.

Try adding:

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=dfe3da47-7d95-4a9d-ba72-687c9d781be3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet


```

Use the Dapper install to make sure the kernel is 2.6.22-13-generic for Feisty. Change the entry if it is not.

Replace the UUID with your own.
```

ls /dev/disk/by-uuid -lah

```

---

### Post by Pumalite on 2007-12-28
It's probably a mix of SATA and IDE:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by SneakPeak on 2008-01-03
Thanks for the help folks and sorry for the slow response.  I have been away on a few days  holiday.

I have solved my problem.  What I did:

1. I mounted the disk / partition where I had installed the 7.10 version of Ubuntu from the disk / partition where 6.06 was installed. (I could boot to 6.06 but not to 7.10.)

2. I browsed to /NewUbuntu/boot/grub where /NewUbuntu was my mount point for the 7.10 disk / paritition.

3. I opened the menu.lst file and copied the sections for the 7.10 boot.  

4. I then went to /boot/grub on my 6.06 partition and pasted the 7.10 boot entries into the menu.lst file located there.

5. I then re-booted and was able to choose my 7.10 from the gurb menu and 7.10 booted.  

6. Grub is still looking at my 6.06 partition for the menu.lst file and my next step is to change this so that it looks at the 7.10 menu.lst file.  I can then get rid of my 6.06 installation.

Thanks again for the help

SneakPeak

---

