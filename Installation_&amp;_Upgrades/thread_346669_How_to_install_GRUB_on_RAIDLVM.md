---
title: "How to install GRUB on RAID/LVM"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by abadr on 2007-01-26
After a recent K/Ubuntu 6.10 system update, Ubuntu no longer boots. From googling around I think that the problem is that GRUB points to the wrong boot device. However ](*,) I cannot figure out how to fix that since I have LVM over RAID. I tried booting from Ubuntu Live and Knoppix but those didn't recognize the RAID devices or the LVM.

I would appreciate any help.

-----------------------------------------
I have 4 drives with 3 raid devices, each mdX spans the 4 drives.
md0 - RAID1  /boot
md1 - RAID5 LVM Volume Group (pptVG)
md2 - RAID4 swap

The LVM contains the following Logical volumes
rootLV - / 
varLV - /var
homeLV - /home
and a couple others.
-----------------------------------------
The errors I get while booting.
```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```
CTRL+ALT+F1 gives me the following
```

Starting up ...
mdadm: /dev/md0 has been started with 4 drives.
mdadm: /dev/md1 has been started with 4 drives.
mdadm: /dev/md2 has been started with 4 drives.
  4 logical volume(s) in volume group "pptVG" now active
mount: Mounting /dev/mapper/pptVG-rootLV on /root failed: no such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```

Thanks.

---

### Post by abadr on 2007-01-28
Well, I figured out how to use Ubuntu Live to mount my /boot RAID only partition. The live cd doesn't load RAID support by default. So from the shell:

```

sudo apt-get install mdadm
cd /dev
sudo mdadm --assemble md0 sda1 sdb1 sdc1 sdd1
sudo mkdir /old-boot
sudo mount /dev/md0 /old-boot

```

Now I can go to old-boot/grub and read menu.lst. However I still cannot figure out what's wrong. I would apreciate an help.

My menu.lst
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
timeout		5


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
# kopt=root=/dev/mapper/pptVG-rootLV ro

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
kernel		/vmlinuz-2.6.17-10-386 root=/dev/mapper/pptVG-rootLV ro quiet splash
initrd		/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		hacked
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386 root=/dev/pptVG/rootLV ro quiet splash
initrd		/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386 root=/dev/mapper/pptVG-rootLV ro single
initrd		/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/mapper/pptVG-rootLV ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/mapper/pptVG-rootLV ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

