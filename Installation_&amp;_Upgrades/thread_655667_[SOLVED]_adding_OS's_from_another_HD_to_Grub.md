---
title: "[SOLVED] adding OS's from another HD to Grub"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by hotrod6657 on 2008-01-01
Ok here's the situation, i have a laptop that i use an external hard drive with.  The internal hard drive in the laptop has XP on it and i would really rather leave that alone.  My external drive has a few linux distros on it, both gusty right now, with plans for upgrading the one to the alpha release of Hardy.

So, when i installed linux on the external drive i had to remove my laptop's internal hard drive because i was having trouble specifying where i wanted grub installed using the advanced options in the installer.  Now, if i start my laptop up with the external drive off it boots windows just fine, but with the drive on i only get my linux options (the ones installed on that drive).

how would i go about adding the options for Windows that are on the other drive?  Is there some way to tell grub where to look for it, or has anyone done this before?

If it helps here's the output of fdsk -l:
[SIZE="1"]
[B]Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12243    92557048+   7  HPFS/NTFS
/dev/sda2           12244       12921     5125680   12  Compaq diagnostics

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a85b6a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37509   301291011    b  W95 FAT32
/dev/sdb2           37510       38197     5526360   83  Linux
/dev/sdb3           38839       38913      602437+   5  Extended
/dev/sdb4   *       38198       38838     5148832+  83  Linux
/dev/sdb5           38839       38913      602406   82  Linux swap / Solaris[/B][/SIZE]

Here's my menu.lst file as well:

[B][SIZE="1"]# menu.lst - See: grub(8), info grub, update-grub(8)
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=a85a1b43-0cb1-4aa9-bb24-087416f35961 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet splash vga=795

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a85a1b43-0cb1-4aa9-bb24-087416f35961 ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a85a1b43-0cb1-4aa9-bb24-087416f35961 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=a85a1b43-0cb1-4aa9-bb24-087416f35961 ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=a85a1b43-0cb1-4aa9-bb24-087416f35961 ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac0f8435-570a-4fa4-aef8-7ca23e9cfa6b ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac0f8435-570a-4fa4-aef8-7ca23e9cfa6b ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 7.10, kernel 2.6.22-12-generic (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=ac0f8435-570a-4fa4-aef8-7ca23e9cfa6b ro quiet splash 
initrd		/boot/initrd.img-2.6.22-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode) (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=ac0f8435-570a-4fa4-aef8-7ca23e9cfa6b ro single 
initrd		/boot/initrd.img-2.6.22-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 7.10, memtest86+ (on /dev/sda4)
root		(hd0,3)
kernel		/boot/memtest86+.bin  
savedefault
boot[/SIZE]
[/SIZE]
[/B]

Sorry about the length...

Any ideas, or other commands i should run to revel more information?

Thanks in advance.

Hotrod

PS.
one think i've noticed is that since my external drive was the only drive present upon install it's called hd0, eventhough my internal should be that i would think.  I wanted to specify a different location for grub like hd1 but that did work, i just gave me errors and wouldn't start.  hope that helps.

---

### Post by confused57 on 2008-01-01
I believe the Windows entry in this thread may boot your internal drive's Windows:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
You might want to put the Windows entry at the very bottom of your menu.lst.

---

### Post by hotrod6657 on 2008-01-01
if i do that and it doesn't work, like the thread talked about, will that stop me from booting any of my OS's, or just the windows one until i fix it?  I just don't want to do that and be stuck if it doesn't work.  Or, i guess, if it didn't work, how would i modify menu.lst without being able to boot the operating system?

---

### Post by confused57 on 2008-01-01
> **hotrod6657 said:**
> if i do that and it doesn't work, like the thread talked about, will that stop me from booting any of my OS's, or just the windows one until i fix it?  I just don't want to do that and be stuck if it doesn't work.  Or, i guess, if it didn't work, how would i modify menu.lst without being able to boot the operating system?

If you add the Windows entry to the very bottom(after ###END DEBIAN AUTOMATIC LIST) of your menu.lst, it shouldn't affect your ability to boot any of your distros on your external drive

---

### Post by hotrod6657 on 2008-01-01
okay cool, that was what i was hoping for.  I'll give that a shot as soon as i can reboot, i've got to finish a few downloads first.

---

### Post by hotrod6657 on 2008-01-02
real quick, does any one know the answer to this:

I have several distributions, 3 now, on this external hard drive.  they each have their own menu.lst file, which one should i modify, or should i modify all three?

---

### Post by confused57 on 2008-01-02
> **hotrod6657 said:**
> real quick, does any one know the answer to this:

I have several distributions, 3 now, on this external hard drive.  they each have their own menu.lst file, which one should i modify, or should i modify all three?
It would be whichever distros grub is installed to the external hard drive's mbr...it would probably be the first one listed in your grub boot menu.  Even if you add it to the wrong menu.lst, it wouldn't hurt anything, especially if you add your Windows entry to the very bottom of your menu.lst.

---

### Post by hotrod6657 on 2008-01-02
Okay, that's what i figured, but i figured i would ask.  Thanks in advance, i'll give that a shot in the morning.

---

### Post by hotrod6657 on 2008-01-03
Just tried the fix and ... beautiful!!!  Worked like a charm.  Also, the menu.lst that is used is appairently (thought it makes sense) the one for the last OS installed.

Thanks a lot for your advice confused57!!!

---

