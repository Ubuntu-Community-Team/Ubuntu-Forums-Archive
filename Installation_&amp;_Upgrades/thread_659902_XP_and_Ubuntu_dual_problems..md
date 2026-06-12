---
title: "XP and Ubuntu dual problems."
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by gofes on 2008-01-06
Hello,

I installed Ubuntu on my laptop, along with XP, for about the past year. Since then I have been happily using Ubuntu, never booting into XP.

Recently I tried booting XP, it wouldn't load giving the message
> this is not a bootable disk
So I just reinstalled XP on it's partition. The computer then booted strait into XP, with the usual GRUB options.
After look around the internet I used SuperGrub to give me the usual Grub options and boot to Ubuntu .

But now I'm unable to boot into Windows, with the
> this is not a bootable disk
message back.

Does anyone have any pointers on what I'm doing wrong? Bellow is my partitions.

>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+  83  Linux
/dev/hda2   *        1913        6042    33174225    b  W95 FAT32
/dev/hda3            6043        6992     7630875    7  HPFS/NTFS
/dev/hda4            6993        7296     2441880   82  Linux swap / Solaris


With Ubuntu installed at /dev/hda1 
and XP at /dev/hda3 
Not sure why the fat 32 partition is set to boot.
Does windows need to be in the first partition?

---

### Post by PmDematagoda on 2008-01-06
Post the result of:-
```
cat /boot/grub/menu.lst
```

---

### Post by gofes on 2008-01-06
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=732c6976-0378-42dd-b059-d85fbba30a15 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=732c6976-0378-42dd-b059-d85fbba30a15 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=732c6976-0378-42dd-b059-d85fbba30a15 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=732c6976-0378-42dd-b059-d85fbba30a15 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=732c6976-0378-42dd-b059-d85fbba30a15 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Cheers

---

### Post by PmDematagoda on 2008-01-06
Open the menu.lst file for editing using:-
```
gksudo /boot/grub/menu.lst
```
then edit the last lines from this:-
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows XP Home Edition
[COLOR="Red"]**root (hd0,1)**[/COLOR]
savedefault
makeactive
chainloader +1
```
to this:-
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows XP Home Edition
[COLOR="Red"]**root (hd0,2)**[/COLOR]
savedefault
makeactive
chainloader +1
```
save the file and then try booting Windows again.

---

### Post by gofes on 2008-01-06
Cheers.

Thanks for that. Both Ubuntu and XP loads now.

---

