---
title: "Grub doesn't recognize HDD format"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by Hg80 on 2006-08-29
Ok after having to restall windows and getting grub to work im having problems getting grub to load into windows the HDD in question is HDD 0,0 and it trys to load and then comes back with something along the lines as "Grub was unable to recognize drive format"
Any ideas?

---

### Post by Original Brownster on 2006-08-29
Hi,
Have I got this right, you cannot boot windows now? 
Grub will not recognise the ntfs partition of windows (if that is what it is) you need an entry in your grub configuration file (/boot/grub/menu.lst) that uses chainloader so it passes control of the boot process back to the normal windows loader, an entry like:

title           Microsoft Windows XP
rootnoverify    (hd0,0)
chainloader     +1

HTH

> **Hg80 said:**
> Ok after having to restall windows and getting grub to work im having problems getting grub to load into windows the HDD in question is HDD 0,0 and it trys to load and then comes back with something along the lines as "Grub was unable to recognize drive format"
Any ideas?

---

### Post by Hg80 on 2006-08-29
didnt work and yes its NTFS

---

### Post by caiman64 on 2006-08-29
I have the same problem.... does this work with SATA disks? what do I have to change to that menu.lst file??

Thank you,
Carlos   ](*,)

---

### Post by confused57 on 2006-08-29
Could you post the output of:
```
sudo fdisk -l
```
The -l is a small "L"

This will show your partition tables and may help to determine what your grub entry should be to boot Windows.

---

### Post by Hg80 on 2006-08-29
as requested
```
hg@hg80:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26363   211760766    7  HPFS/NTFS
/dev/sdb2           26364       30026    29423047+  83  Linux
/dev/sdb3           30027       30401     3012187+   5  Extended
/dev/sdb5           30027       30401     3012156   82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30400   244187968+   c  W95 FAT32 (LBA)

Disk /dev/sdf: 1027 MB, 1027604480 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         125     1003488+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(123, 254, 63) logical=(124, 237, 49)
hg@hg80:~$

```

---

### Post by Original Brownster on 2006-08-29
> **Hg80 said:**
> didnt work and yes its NTFS

Plz post the contents of your /boot/grub/menu.lst file

Thanks.

---

### Post by Hg80 on 2006-08-30
Menu.list as asked for
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
# kopt=root=/dev/sdb2 ro

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

splashimage=(hd0,1)/boot/grub/blu.xpm.gz

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-25-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-25-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Shitty Windows:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
rootnoverify (hd0,0)
chainloader +1




```

---

### Post by confused57 on 2006-08-30
Sorry, but could you post one more thing?:

```
cat /boot/grub/device.map
```

I don't know if adding the "makeactive" line would make a difference:
```
title		Windows 
root		(hd0,0)
makeactive
chainloader	+1
```

Usually when you reinstall, the Windows mbr overwrites grub so that you can't boot Ubuntu...Did you reinstall Windows to sdb1?

---

### Post by Hg80 on 2006-08-30
```
hg@hg80:~$ cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdd
(hd3)   /dev/sde
hg@hg80:~$

```

No i reinstalled windows to the 80GB HDD

---

### Post by randell6564 on 2006-08-30
Here is a little something about Raid Devices that might help.,

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by Original Brownster on 2006-08-30
Hi, Try removing the extra lines  you have for 
title and root, this might be messing up the boot loader.
you might also try the 'makeactive' option as confused57 suggested, though I think your partition is active anyway.

I cannot see what else is wrong.


> **Hg80 said:**
> Menu.list as asked for
```
# menu.lst - See: grub(8), info grub, update-grub(8)

<--snip.....................................................
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Shitty Windows:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
rootnoverify (hd0,0)
chainloader +1


```

---

### Post by randell6564 on 2006-08-30
You are running S-ATA Raid devices. I strongly suggest that you read the link that I provided.

---

### Post by Hg80 on 2006-08-31
Ok i seen the link, but that still doesnt answer the question,
I mean Ubuntu is installed to a SATA drive and that loads fine

---

### Post by confused57 on 2006-08-31
I'm surprised Ubuntu boots with the root set as (hd0,1), if this is the case...out of curiosity, try this entry to boot Windows:

```
title                  Windows XP
rootnoverify       (hd1,0)
savedefault
makeactive
map                  (hd0) (hd1)
map                  (hd1) (hd0)
chainloader        +1
```

---

### Post by randell6564 on 2006-08-31
> **Hg80 said:**
> Ok i seen the link, but that still doesnt answer the question,
I mean Ubuntu is installed to a SATA drive and that loads fine

Yes but NOW you are trying to dual boot.  HMMM, I wonder WHY grub is unable to "recognize drive format"!

---

### Post by Hg80 on 2006-09-01
> **confused57 said:**
> I'm surprised Ubuntu boots with the root set as (hd0,1), if this is the case...out of curiosity, try this entry to boot Windows:

```
title                  Windows XP
rootnoverify       (hd1,0)
savedefault
makeactive
map                  (hd0) (hd1)
map                  (hd1) (hd0)
chainloader        +1
```


Cheers that worked!!!

---

