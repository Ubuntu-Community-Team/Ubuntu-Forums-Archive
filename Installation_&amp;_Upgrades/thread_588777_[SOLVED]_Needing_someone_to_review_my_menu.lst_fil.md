---
title: "[SOLVED] Needing someone to review my menu.lst file"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by schneider707 on 2007-10-23
Ok, so here is the deal. I disconnected my Win XP drive (SATA) when I installed Ubuntu-Fiesty (IDE) cause I figured I could just edit the grub.conf and everything would work. However, the lines I added don't really seem to do much...they give me an error (the number escapes me). Sooo now I just have to disconnect either one of the hard drives depending on which OS i want to use. 
I looked around a bit and I think these 2 outputs might help you guys help me fix it up a bit.

sudo fdisk -lu

```
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   154770209    77385073+  83  Linux
/dev/hda2       154770210   160826714     3028252+   5  Extended
/dev/hda5       154770273   160826714     3028221   82  Linux swap / Solaris

```

and then 
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
# kopt=root=UUID=6407682b-10fc-4657-85d5-1f57bb9a3a08 ro

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
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6407682b-10fc-4657-85d5-1f57bb9a3a08 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet

[COLOR="Red"]title Windows XP sucks
root (sd0,0)
makeactive
chainloader +1
savedefault[/COLOR]


title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6407682b-10fc-4657-85d5-1f57bb9a3a08 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

So, I highlighted the XP part I added in...do you think the location is right (its on an SATA drive)?
Or should it be more like:

title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1
savedefault


I'm just kinda confused about the whole naming thing I suppose....o and grub is installed on the drive with ubuntu if that could clear anything up.

I started linux with learning Gentoo (2005.1 ....before that crappy installer) and their manual only showed me how to write in the lines for other linux distros...so xp confuses me a ton

---

### Post by Pumalite on 2007-10-23
The output of your sudo fdisk -lu shows only one drive.??? If we are going to be able to help you you should post the output of sudo fdisk -lu with both drives connected.

---

### Post by schneider707 on 2007-10-23
well ya cause if i leave both connected at the same time it just instantly goes to XP...which now makes me think I set XP and priority boot in BIOS....ok im an idiot. But besides that, I still don't think my menu.lst is correct.

---

### Post by Pumalite on 2007-10-23
Can you boot Ubuntu if you change the boot order in BIOS with both drives connected?

---

### Post by schneider707 on 2007-10-23
lemme check real quick...ill edit it to this reply

EDIT: Ok so I switched the boot priority of the 2 hard drives so Ubuntu now boots with both drives connected.

This is sudo fdisk -lu again :
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125001764    62500851    7  HPFS/NTFS
/dev/sda2       125001765   488392064   181695150    f  W95 Ext'd (LBA)
/dev/sda5       125001828   488392064   181695118+   7  HPFS/NTFS

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   154770209    77385073+  83  Linux
/dev/hda2       154770210   160826714     3028252+   5  Extended
/dev/hda5       154770273   160826714     3028221   82  Linux swap / Solaris

```

---

### Post by Pumalite on 2007-10-23
Add this to your menu.lst:

title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
savedefault

Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
Save, exit and reboot

---

### Post by schneider707 on 2007-10-23
Hey it worked...thanks much. 

Now 2 questions. One is what do the map lines do? And second question is should I mark this thread with Solved or nah?

---

### Post by Pumalite on 2007-10-23
You are welcome. Map tells Grub where to find things. Use 'Thread Tools' to mark this thread as SOLVED.

---

