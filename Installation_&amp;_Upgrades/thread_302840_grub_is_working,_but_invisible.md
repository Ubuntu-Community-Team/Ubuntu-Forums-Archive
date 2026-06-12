---
title: "grub is working, but invisible"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by dukeleto on 2006-11-19
Hi everyone,
I just upgraded my laptop from dapper to edgy, and have a
symptom with grub that I haven't found described on the forums here.
I get the "loading grub stage 1.5" message, and then, instead of seeing the grub menu with 2 different kernels + my windows partition, I just have a black screen with a flashing cursor.
However, grub is still working, because I can choose any of the three boot options with the up/down arrows during the black screen.
Reinstalling grub hasn't solved the problem. Any other ideas?

Regards,

Olivier

---

### Post by deepclutch on 2006-11-19
scrutinize ur /boot/grub/menu.lst.sometimes splashscreen or color options are the culprits.
and if all fails try reinstalling drive from scratch,ie 
in CLI,
#grub
grub>root (hd0,x) where x is your root partn
then 
grub>setup (hd0)

---

### Post by Psquared on 2006-11-19
press esc when you see Grub loading; you should be able to see your choices then. yours just got set to invisible somehow.

if you want to change it permanently do this:

open a terminal and type

sudo gedit /boot/grub/menu.lst

find the entry that says "invisible" and comment it out with ##

---

### Post by manopb on 2006-11-19
I too am having the same problem. I have tried the recommended options listed here with no luck.
Edubutu 6.10

---

### Post by dukeleto on 2006-11-20
Thanks for the suggestions.
No luck so far with any of them; I'll get back if I sort it out.
Olivier

---

### Post by pallaire on 2007-10-29
I am having the same problem with Ubuntu 7.10. I made a fresh install.

When I boot from the CD, I am able to see the Boot Menu and it is working fine :
[IMG]http://www.ubuntugeek.com/images/lamp/1.png[/IMG]

Once the install finished, I was asked to remove the CD and reboot, which I did ! When rebooting I saw the Grub Menu only **ONCE** : 
[IMG]http://static.screencasts.ubuntu.com/20061204_installing_dual_boot.jpeg[/IMG]

Since then, the Grub menu is only black !!!! But it is still working !?!?! I I press down 4-5 times, then enter, I will boot my Windows Partition! Grub is only black ! No texts, No cursors.

The option to hide the menu is not enable in menu.lst. 


[Grub menu.lst : unmodified after the installation]
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
# kopt=root=UUID=3d80b09b-f63f-472f-af79-6e29d9ead098 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
# groot=(hd1,0)

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3d80b09b-f63f-472f-af79-6e29d9ead098 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3d80b09b-f63f-472f-af79-6e29d9ead098 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```



[fstab]
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                       <dump>  <pass>
proc            /proc           proc            defaults                        0       0

/dev/sdb1       /               ext3            defaults,errors=remount-ro      0       1
/dev/sdb5       /home           ext3            defaults                        0       2
/dev/sdb6       /media/data     ext3            defaults                        0       2

/dev/sda5       /media/winc     ntfs            defaults,umask=007,gid=46       0       1
/dev/sda2       /media/wind     ntfs            defaults,umask=007,gid=46       0       1

/dev/sdb2       none            swap            sw                              0       0
/dev/hdc        /media/cdrom0   udf,iso9660     user,noauto,exec                0       0

```


So, I dont know what is the problem ! But the menu.lst, looks fine to me and reinstalling Grub does not fix the problem !

---

### Post by pallaire on 2007-10-31
I may have found a solution !?!?

Last night, I was trying to enable some auto-wakeup for my computer. I want it to start everyday at 8h. I was not successfull, so I went into the BIOS to see if ACPI was enabled, it was NOT ! So I enabled it and rebooted, guess what ...

I saw my grub menu ! It was late, so I did not retry another reboot to confirm, I will do that tonight. But it can be one of two thing :
1) Enabling ACPI in the BIOS ... would be great since its easy
2) Just going into the BIOS ?????? that would not fix the problem.

---

### Post by pallaire on 2007-11-01
Finally, that did not fix the problem :confused:

---

