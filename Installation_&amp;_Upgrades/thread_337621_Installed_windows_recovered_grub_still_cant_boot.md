---
title: "Installed windows *recovered grub* still cant boot"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Kirky_D on 2007-01-13
So i installed windows after kubuntu, i then used super grub disk to repair my grub menu which worked proceed to boot into kubuntu I saw the progress bar thingy that loads on boot up but after a few seconds it gives me the following error:

```

Busy Box v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built in shell (ash)

Enter 'help' for a list of built in commands.

/bin/sh: Can't access tty: job control turned off 
(initramfs)

```

I tried typing in help but the screen was frozen

I can boot into windows by changing the boot order of my hard drives in bios

Can anybody help me boot back into kubuntu with a fully working grub?

---

### Post by bulldog on 2007-01-13
Post the output of the following commands,
```
sudo fdisk -l
gksudo gedit /boot/grub/menu.lst
gksudo gedit /etc/fstab
cat /boot/grub/device.map
```

---

### Post by Kirky_D on 2007-01-13
I assume this is in the livecd terminal?

I will have a look

---

### Post by bulldog on 2007-01-13
To use the live cd for this you have to mount your ubuntu and put the path in the all the commands,only the fdisk command will work without the mount path.

---

### Post by Kirky_D on 2007-01-13
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1824    14651248+  83  Linux
/dev/sdb2            1825       24255   180177007+  83  Linux
/dev/sdb3           24256       24321      530145   82  Linux swap / Solaris

```

this is my grub menu.lst

(i mounted the hard drive with this command: sudo mount -t ext3 /dev/sdb1 /mnt/ubuntu
which allowed me access to my hard drive

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
# kopt=root=UUID=086f7fe1-3ab8-4b89-b666-2b35e0664cb6 ro
# kopt_2_6=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

my fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=086f7fe1-3ab8-4b89-b666-2b35e0664cb6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=b35ca083-999d-41ea-8886-c789bc3d42ca /home           ext3    defaults        0       2
# /dev/sda3
UUID=e02b6599-6f95-4681-ab62-2451dea9058e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

ubuntu@ubuntu:~$ cat /mnt/ubuntu/boot/grub/device.map
(hd0)   /dev/sda

```

---

### Post by Kirky_D on 2007-01-13
Got it sorted!

I was getting an error code 17 in grub when trying to boot the various options in grub, so i had a look round and apparently what happened is when i installed my new hard drive and windows my device names got mucked about.

My old hda became hdb when i installed the new hard drive.

So i edited /boot/grub/device.map and menu.lst and changed the references to hda1 to hdb1

sorted.

---

### Post by bulldog on 2007-01-13
Nice you sorted it out.

---

