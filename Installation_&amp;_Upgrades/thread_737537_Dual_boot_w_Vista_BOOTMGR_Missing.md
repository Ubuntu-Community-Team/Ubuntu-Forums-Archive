---
title: "Dual boot w/ Vista: BOOTMGR Missing"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by Auax on 2008-03-27
I used to have 2 Vista Partitions on my laptop (don't really know why, I was just fooling around). I decided to put Ubuntu 7.04 on the one I don't use, and it installed fine, however there was no entry for Vista in the GRUB menu. I manually edited the GRUB file and added an entry for Windows, but now when I boot, I get a "BOOTMGR is missing" message.

If it helps, this is my partition table:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         365     2931831   82  Linux swap / Solaris
/dev/sda2   *        7903       14594    53741568    7  HPFS/NTFS
/dev/sda3             366        7902    60540952+  83  Linux

```

---

### Post by Rocket2DMn on 2008-03-27
Nobody else seems to have an answer for you, so I would suggest that you boot from your Vista cd and enter the recovery console, then run
```
fixmbr
``` (or whatever the vista equivilant of resetting the MBR is).  Or maybe just use the repair option.  Then you can reinstall GRUB once vista works.
Because I don't know exactly how vista will behave, it is always smart to backup any important data you have before proceeding (who knows, it might just try to reinstall itself over the whole disk!).

---

### Post by bluewraith on 2008-03-27
Future reference:
[http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

That site helped me quite a bit with my dual-boot issues. Shows how to reinstall grub and everything. A+ IMHO. It does require a copy of GParted... but thats just as free as Ubuntu. :) (actually, its Ubuntu based if I remember correctly)

---

### Post by Auax on 2008-03-27
> **Rocket2DMn said:**
> Nobody else seems to have an answer for you, so I would suggest that you boot from your Vista cd and enter the recovery console, then run
```
fixmbr
``` (or whatever the vista equivilant of resetting the MBR is).  Or maybe just use the repair option.  Then you can reinstall GRUB once vista works.
Because I don't know exactly how vista will behave, it is always smart to backup any important data you have before proceeding (who knows, it might just try to reinstall itself over the whole disk!).I forgot to mention, the Vista CD doesn't detect that I have Vista installed. =\

---

### Post by Auax on 2008-03-27
> **bluewraith said:**
> Future reference:
[http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

That site helped me quite a bit with my dual-boot issues. Shows how to reinstall grub and everything. A+ IMHO. It does require a copy of GParted... but thats just as free as Ubuntu. :) (actually, its Ubuntu based if I remember correctly)
I actually followed that guide to get the point I'm at. Haha.

---

### Post by Rocket2DMn on 2008-03-27
> **Auax said:**
> I forgot to mention, the Vista CD doesn't detect that I have Vista installed. =\

Can you please post the grub menu.lst file:
```
cat /boot/grub/menu.lst
```

---

### Post by Auax on 2008-03-27
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
# kopt=root=UUID=93ed6823-6922-4ba7-a2b9-3a1c126825a5 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=93ed6823-6922-4ba7-a2b9-3a1c126825a5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=93ed6823-6922-4ba7-a2b9-3a1c126825a5 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title   Windows Vista Home Premium
root   (hd0,1)
makeactive
chainloader +1

```

---

### Post by Rocket2DMn on 2008-03-27
Hrmm, it does look OK (I figured it would be, but it doesn't hurt to check).  Were you ever able to get to a recovery console from the vista cd to try and run "fixmbr"?  If that doesn't work, I really don't know what else there is to do :( - you can try googling that error message, there must be some way to fix it from the vista cd, probably from the recovery console.
I imagine you can declare there where vista is on the hard drive and have it repair itself...

---

### Post by Auax on 2008-03-27
I've been looking around, I just don't know anything about the recovery console. I'm not really that Backdoor-Windows Saavy.

---

### Post by Rocket2DMn on 2008-03-27
I've never actually booted from a vista cd, but it should be similar to xp where you have the option of entering either a repair mode or what they call the recovery console which just drops you at a type of DOS prompt.  Sorry I don't have any more for you.

---

### Post by Auax on 2008-03-27
Yeah, there is. The recovery stuff wont do anything, and I don't know how to use the DOS thing.

---

### Post by Rocket2DMn on 2008-03-27
That is where you run
```
fixmbr
```
Then you will have to reinstall GRUB later to get back into Ubuntu.

---

### Post by Auax on 2008-03-27
Ooooh, ok.

I'll try it as soon as my updates are done.

---

