---
title: "Help: I can't boot into Vista with a dual boot"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by leenane on 2007-08-07
Please help!
I installed Feisty Fawn on Linux partition that I'd created earlier on my hard drive. When I boot up, I can get into Ubuntu without any problems from the GRUB menu, but it just seems to loop back to restart GRUB when I try to load Vista. What should I do? 

Ubuntu is the first Linux that I've tried, and I have moderate windows skills.
Thanks for your help.
Leenane

---

### Post by merlinus on 2007-08-07
Post results of these commands run in a terminal:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

-merlin

---

### Post by leenane on 2007-08-07
Hi Merlin,
Is this the information you need?

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       17652   135492210    7  HPFS/NTFS
/dev/sda3           17653       29522    95345775   83  Linux
/dev/sda4           29523       30401     7060567+  82  Linux swap / Solaris
leenane@leenane-desktop:~$ cat /boot/grub/menu.lst
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
timeout         10

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
# kopt=root=UUID=d2b2caf0-faa7-4705-9640-d01e2f01b413 ro

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d2b2caf0-faa7-4705-9640-d01e2f01b413 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d2b2caf0-faa7-4705-9640-d01e2f01b413 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d2b2caf0-faa7-4705-9640-d01e2f01b413 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d2b2caf0-faa7-4705-9640-d01e2f01b413 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Thanks!

---

### Post by leenane on 2007-08-07
a

---

### Post by merlinus on 2007-08-07
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
rootnoverify            (hd0,1)
savedefault
makeactive
chainloader     +1


Try deleting the first paragraph (stanza).  It is inapplicable.  And make the one change in the second from root to rootnoverify.

Restart and see what happens.

-merlin

---

### Post by leenane on 2007-08-07
Hi Merlin,
I don't know how to delete that stanza. I'm not familiar with Linux Terminal commands. I'm pretty sure it refers to my factory restore partition. The machine was originally XP. I'm reluctant to delete it. Any other suggestions?
Leenane

---

### Post by merlinus on 2007-08-08
```

gksduo gedit /boot/grub/menu.lst

```

You can comment out the lines by placing a # in front of them, so they can be easily restored if need be.

But you do not want to be booting into a recovery partition, so the second windows stanza seems to be the correct one, based upon sudo fdisk -l

What are the choices in the grub startup menu currently?

-merlin

---

### Post by leenane on 2007-08-08
Hi, Thanks for sticking with me :)

Here are the startup options from Grub:

Ubuntu, kernel 2.6.20-16 generic
Ubuntu, kernel 2.6.20-16 generic
Ubuntu, kernel 2.6.20-15 generic
Ubuntu, kernel 2.6.20-15 generic
Other Operating systems
Windows NT/2000/XP
Windows Vista/Longhorn (loader)

I tried that command you mentioned in terminal and get the following:
bash: gksduo: command not found

Any more suggestions?

Leenane

---

### Post by merlinus on 2007-08-08
Yeah, I spelled it wrong.  :(

gksudo gedit /boot/grub/menu.lst

-merlin

---

### Post by leenane on 2007-08-09
Hi Merlin,
I put the # symbols in front of the first stanza, as you suggested. The option Windows NT/2000/XP no longer shows up on GRUB, but alas, Windows Vista/Longhorn (Loader) still does not work. Does it have anything to do with GRUB referring to that partition as hda, whereas when I'm looking at it from within Ubuntu, it is referred to as sda?
I also tried the supergrub CD, but no joy either.
Leenane

---

### Post by merlinus on 2007-08-09
No, (hd0) simply refers to your first hard disk.

It may be a vista problem, so hopefully someone with that knowledge will chime in.  I remember a fairly recent post about using grub to load the vista boot loader.  Perhaps a forum search will help.

Good luck!

-merlin

---

### Post by confused57 on 2007-08-09
I don't recall seeing any solution for Vista or XP rebooting when trying to boot from grub, so I can't really help you resolve that issue.
If you have a Vista install DVD, you can restore Vista's IPL to the mbr using "bootrec /fixmbr":
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

It's possible to boot Linux from Vista, using EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

For this to work, grub has to be installed to the root partition, but this can easily be done with the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by leenane on 2007-08-10
Thank you!!!
I'm back in business with Vista - I do like Ubuntu - the philosophy, community and the OS, and want to explore it more, so I'll set up the dual boot the way you recommend. 
Thank you again,
Peace!
Leenane

---

