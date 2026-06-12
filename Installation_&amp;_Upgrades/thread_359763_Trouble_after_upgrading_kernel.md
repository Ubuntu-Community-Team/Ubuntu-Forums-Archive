---
title: "Trouble after upgrading kernel"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Muppeteer on 2007-02-12
I've been using Edgy for a couple of months and really like it...Though a month or so ago, i decided to upgrade from kernel 2.6.17-10, to 2.6.19.1. I followed a guide in the forum, can't remember where it is now...

Since upgrading, i can't start with the new kernel. I get an error message saying something like:
```
/bin/sh: Can't access tty; Job control turned off (initramfs)
```

When i press Ctrl+Alt+F1 i get the following
```
/dev/sda3 does not exist
```

Here is my menu.lst
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
# kopt=root=UUID=edfd5f72-49af-4244-bf57-b51666859b2d ro
# kopt_2_6=root=/dev/sda3 ro

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

title		Ubuntu, kernel 2.6.19.1
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.19.1 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.19.1
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.19.1 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.19.1 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.19.1
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I can boot up the old kernel ok, but i can't do any updates. If i type:
sudo apt-get update - everything is fine, no errors

sudo apt-get upgrade - i get the following
```
Get: 1 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy/main Translation-en_GB
Get: 2 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_GB
Ign http://archive.ubuntu.com edgy/restricted Translation-en_GB
Get: 3 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_GB
Ign http://security.ubuntu.com edgy-security/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_GB
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_GB
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_GB
Get: 4 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]
Hit http://security.ubuntu.com edgy-security Release
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_GB
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_GB
Get: 5 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Hit http://security.ubuntu.com edgy-security/universe Packages
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_GB
Hit http://security.ubuntu.com edgy-security/main Packages
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_GB
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_GB
Hit http://archive.ubuntu.com edgy Release     
Hit http://security.ubuntu.com edgy-security/restricted Packages    
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-proposed Release
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-proposed/universe Packages
Hit http://archive.ubuntu.com edgy-proposed/main Packages
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Fetched 5B in 1s (3B/s)  
Reading package lists... Done
graham@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.19.1 needs to be reinstalled, but I can't find an archive for it.

```

So why's it asking me to reinstall the kernel? Can't i just remove the updated kernel and stick with the one that works? I've found some people with the same problem about can't access tty, but anything i seem to change in the menu.lst and fstab don't make a difference.

Here's my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=edfd5f72-49af-4244-bf57-b51666859b2d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bfc33410-0eae-4ede-bbbd-3cc1140e52a4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc1       /media/linux 	vfat   iocharset=utf8,umask=000  
0       0
```

If i can get the new kernel working, great but right now it's just a headache that i can't seem to find a cure for....:(

---

### Post by mikewhatever on 2007-02-12
Hi,
I have no idea how to fix the problem with the newer kernel. In fact, the necessity of the upgrade is quite beyond my understanding.
If the older kernel still works, in other words you can boot into it, and you do not urgently need the newer one, you can use the older kernel for now. You can also remove the newer kernel from synaptic. Use the search button with word 'kernel modules' or similar. You can also lock the older kernel in synaptic to prevent any further upgrades. 
Lots of options to choose from, you decide.

---

### Post by JamieC on 2007-02-12
What is the output of the following:
```

sudo fdisk -l

```

You may need to update the boot parameters (specifically the root line).

---

### Post by Muppeteer on 2007-02-12
Here's the output

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913       33760   255819060    7  HPFS/NTFS
/dev/sda3           33761       38700    39680550   83  Linux
/dev/sda4           38701       38913     1710922+   f  W95 Ext'd (LBA)
/dev/sda5           38701       38913     1710891   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/sdd: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9729    78148161    7  HPFS/NTFS
```

MIke, i just upgraded to try and learn something along the way...Since i haven't been using linux very long...

---

### Post by mikewhatever on 2007-02-12
> **Muppeteer said:**
> 
MIke, i just upgraded to try and learn something along the way...Since i haven't been using linux very long...

Well, so did I. It was kind of find to try to solve it. I haven't realised that I rebooted about 20 times on Saturday. One good thing had come out of this, I discovered envy, the program for installing nvidia driver by Alberto Milone. Really impressive.

---

### Post by Muppeteer on 2007-02-12
I can't remove the newer kernel from synaptic, it just comes up saying 

```
E: The package linux-image-2.6.19.1 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

It doesn't list anything in synaptic, so it's pretty useless at the minute...

Ok well, i reinstalled the new kernel and removed it, now synaptic is working fine.....Think i'll have to do a bit more research before attempting a kernel upgrade again :)

---

