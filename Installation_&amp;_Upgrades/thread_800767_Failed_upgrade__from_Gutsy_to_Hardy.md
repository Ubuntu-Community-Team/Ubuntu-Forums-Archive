---
title: "Failed upgrade  from Gutsy to Hardy"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by chromium72 on 2008-05-20
Hi everybody.
I recently upgraded from Gutsy to Hardy by using internal ubuntu updater, and everything messed up, I get an uuid error message at boot.
It's a well-known problem, that many users experienced an uuid related problem when booting after such upgrade, so I tried many solutions offered by this and ohter forums, but none solved my problem:

1) I tried to use ```
sudo vol_id /dev/hdc1
``` (hdc1 is my fs) in order to read the correct uuid of my disk and substitute it in menu.lst and  fstab. I checked and discovered that my uuid is already the "correct" one.

2) I tried ```
sudo update grub
```, no effects.

3) I searched /dev/disk/by-uuid for a different uuid, but this file does not exist in my fs, whilst in live CD ramdisk it contains two links:

```

5563b1c1-44a4-46cf-b2e8-73d54c1415a8 -> ../../hdc5
c954f1b0-0bb7-41f0-98cb-594bdd84d004 -> ../../hdc1

```

And now some output:

(when I boot with live CD my old fs is on /media/disk)

cat /media/disk/boot/grub/menu.lst

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
# kopt=root=UUID=c954f1b0-0bb7-41f0-98cb-594bdd84d004 ro

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

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c954f1b0-0bb7-41f0-98cb-594bdd84d004 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c954f1b0-0bb7-41f0-98cb-594bdd84d004 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c954f1b0-0bb7-41f0-98cb-594bdd84d004 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c954f1b0-0bb7-41f0-98cb-594bdd84d004 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```



cat /media/disk/etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=c954f1b0-0bb7-41f0-98cb-594bdd84d004 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=5563b1c1-44a4-46cf-b2e8-73d54c1415a8 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```



sudo fdisk -l

```

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf196f196

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2327    18691596   83  Linux
/dev/hdc2            2328        2434      859477+   5  Extended
/dev/hdc5            2328        2434      859446   82  Linux swap / Solaris

```


When I boot my pc, I get these errors:

on tty1:

```

[  213.772286] ata4.00: revalidation failed (errno=-5)


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [  228.77.32.58] ata4: SRST failed (errno=-16)
[  258.975122] ata4.00: revalidation failed (errno=-5)
[  269.760314] ata4: SRST failed (errno=-16)
[  269.928626] Buffer I/O error on device sda1, logical block 0

```
and then a lot of similar errors on sda1, sda2 and sda5, with logical block values from 0 to 3.


on tty6:

```

Check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/c954f1b0-0bb7-41f0-98cb-594bdd84d004 does not exist. Dropping to shell!

```

I manually tried to execute the commands above (cat /proc/cmdline and cat /proc/modules): if I run them on live CD ramdisk, I get a "normal" output (I can post it if it could be useful). If I run them on my old fs I get error, file not found.


I have to say that I already noticed that old Gutsy uncorrectly detected my hard disk, which is IDE, saying that it was sata and putting it on sda1. I now see that Hardy put it on hdc1, so I think that maybe Hardy corrected the detection error, but failed to update all of my system files, thus causing the crash.

What shall I do?
Thank you for any help.

---

### Post by dstew on 2008-05-20
The problem is not a uuid problem, that is only the symptom. The problem is that the driver software is having trouble reading the disk, so it cannot get the uuid value at all. The error "ata4: SRST failed (errno=-16)" is coming from the disk driver.

When you are having driver/hardware issues, sometimes kernel parameters will help. You add these to the kernel line in /boot/grub/menu.lst, or you can try them temporarily by pressing 'e' at the grub menu to edit the lines there. One kernel parameters to try is all_generic_ide. You can also try ide=nodma, and hdc=noprobe. If you can get it to boot, maybe you can upgrade it and then remove the parameters.

Another thing to try when driver/hardware issues are causing a problem is to change the BIOS settings for the affected hardware. There may be some modes that the Hardy driver is having trouble with.

---

### Post by BroadArrow on 2008-05-26
Thanks for the post, dstew.

I'm experiencing a similar problem. 

Booting from newly installed Heron I can't log in but (using ssh from another box) can see that it couldn't mount anything but the root partition. /dev/disk/by-uuid doesn't work.

Booting from a 7.10 live CD, /dev/disk/by-uuid works as it should and I confirmed that the UUIDs are correct in menu.lst for GRUB and in /etc/fstab. (I've had previous upgrades mess them up.)

So if it's a new driver not reading the disk are there any other parameters I should try in GRUB? I've tried the ones you posted but none worked.

---

### Post by BroadArrow on 2008-05-26
> **dstew said:**
> Another thing to try when driver/hardware issues are causing a problem is to change the BIOS settings for the affected hardware. There may be some modes that the Hardy driver is having trouble with.

Any ideas which settings might be causing problems? There's not a lot of IDE-related BIOS settings on my motherboard to play with!

---

### Post by BroadArrow on 2008-05-26
> **dstew said:**
> The problem is not a uuid problem, that is only the symptom. The problem is that the driver software is having trouble reading the disk, so it cannot get the uuid value at all. The error "ata4: SRST failed (errno=-16)" is coming from the disk driver.

What's the easiest way to see what driver is being used to compare what's used by the 7.10 Live CD and by my new install that doesn't work?

It's odd that it does manage to mount my root partition but can't mount any of the others...

---

### Post by chromium72 on 2008-07-11
Still with the same problem, didn't find any way to resolve it.
I tried all of dstew parameters at boot, but none worked.
Any new info about it?
I'm thinking about a complete format&reinstall...

---

