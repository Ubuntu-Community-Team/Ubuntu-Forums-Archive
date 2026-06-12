---
title: "IDE and SATA Grub Ubuntu and XP Woes"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by flummoxed on 2007-09-02
Okay, so...

I installed windows on a SATA disk. I then installed ubuntu on an IDE disk. GRUB didn't automatically recognize my windows partition. I've read that windows should be the first partition on the first disk, and that will make sure that GRUB doesnt give you headaches. This is what I ask: What exactly IS the first hard disk? I tried setting the hard disk order in the BIOS for the windows hdd to be #1 and the ubuntu hdd to be #2, and then reinstalled ubuntu, but it still won't recognize my windows partition. How do I specify?

Thanks

---

### Post by Pumalite on 2007-09-02
Post: 
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by wolfen69 on 2007-09-02
to avoid grub headaches, you should have unplugged one drive while installing the other OS. then you can choose which drive to boot to at startup via the quickboot option most bios's have. grub isnt needed when you have seperate hard drives.

---

### Post by rsambuca on 2007-09-02
> **wolfen69 said:**
> to avoid grub headaches, you should have unplugged one drive while installing the other OS. then you can choose which drive to boot to at startup via the quickboot option most bios's have. grub isnt needed when you have seperate hard drives.

I think that is a rather inconvenient method myself.  Make sure that the boot order of the drives is set properly, and then if you post the output of the commands that Pumalite gave you, it should be an easy fix.  One of the problems is that grub has to guess the drive order, and it usually puts IDE first, SATA second.

---

### Post by flummoxed on 2007-09-02
fdisk -lu

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63      385559      192748+  83  Linux
/dev/hda2          385560    19920599     9767520   83  Linux
/dev/hda3        19920600   152344394    66211897+  83  Linux
/dev/hda4       152344395   156296384     1975995   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   163846934    81923436    7  HPFS/NTFS
/dev/sda2       163846935   488375999   162264532+   f  W95 Ext'd (LBA)
/dev/sda5       163846998   488375999   162264501    e  W95 FAT16 (LBA)

```

cat /boot/grub/menu.lst

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
# kopt=root=UUID=18e5e488-e6ca-4b21-a186-b9f7a6a85c9d ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=18e5e488-e6ca-4b21-a186-b9f7a6a85c9d ro quiet splash
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=18e5e488-e6ca-4b21-a186-b9f7a6a85c9d ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

So what exactly do I edit in the menu.lst to set it straight? I see that it has the IDE drive down as hd0...

---

### Post by Pumalite on 2007-09-02
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back (copy and paste)
gksudo gedit /boot/grub/menu.lst
Add at the end:

title         Windows 95/98/NT/2000
rootnoverify          (hd1,0)
makeactive
chainloader   +1

---

### Post by flummoxed on 2007-09-02
no dice. when i select windows xp from the list, it says "Starting up..." and then hangs.

---

### Post by Pumalite on 2007-09-02
Then fix Widows MBR first:
boot from XP CD:
'r' for Recovery>FIXMBR>FIXBOOT
Then re-install Grub with this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by flummoxed on 2007-09-02
thanks, ill try that in the morning and tell you how it goes.

---

### Post by Pumalite on 2007-09-02
You are welcome. I hope it goes well.

---

### Post by lightstream on 2007-09-02
> **flummoxed said:**
> no dice. when i select windows xp from the list, it says "Starting up..." and then hangs.

This happened to me - the cause in my case was that I told grub to install to a specific partition eg setup (hd1,1), make sure you don't do that next time, just use **setup (hd1)**.

It's an easy enough mistake to make, cos when you do find /boot/grub/stage1 it tells you the partition, and you need to give the partition when you do root (hd1, 1).

---

