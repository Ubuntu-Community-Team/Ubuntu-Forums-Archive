---
title: "gub configuration- i can`t load a new kernel"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by mateusz16 on 2007-11-27
ok. Its probably my secound post so please be nice:D

After 4 days i succesful install a new kernel:D i need them to play games on my graphics kard. I installed and compiled kernel without problems. Finaly when i want run new kernel its return that bug

its my grub config file - menu.lst

```

mateusz@admin:~/Download/Muzyka$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=3e96c08e-1389-4a84-91dc-0f838f7a79af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title           Ubuntu 7.10, kernel 2.6.23.8
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.23.8
initrd

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3e96c08e-1389-4a84-91dc-0f838f7a79af ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3e96c08e-1389-4a84-91dc-0f838f7a79af ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

and everything what i have got in folder /boot
```

abi-2.6.22-14-generic memtest86+.bin
config System.map
config-2.6.22-14-generic System.map-2.6.22-14-generic
config-2.6.23.8 System.map-2.6.23.8
grub vmlinuz
initrd.img-2.6.22-14-generic vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak vmlinuz-2.6.23.8

```
can you help me?? it`s really important after 3 mounths of use ubuntu its last chance to play anything:P

---

### Post by mike^_^ on 2007-11-28
try specifying a root device 

kernel          /boot/vmlinuz-2.6.23.8 root=/dev/somenamehere ro

for example

---

### Post by hogwartsnigel on 2007-11-28
would adding such a line help me with my problem. I have a multi disc/ multi partitioned system. Currently running Ubuntu on hdo,2 and I have asabayon installed without its own grub on hda,5.

Scared to hell about messing too much with the grub

Thanks for any comment

Nigel

---

### Post by logos34 on 2007-11-28
> **hogwartsnigel said:**
> would adding such a line help me with my problem. I have a multi disc/ multi partitioned system. Currently running Ubuntu on hdo,2 and I have asabayon installed without its own grub on hda,5.l

Try adding a[ configfile entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") to ubuntu grub for sabayon.

(you may have to run 'grub-install /dev/hda5'--or is it hda6?--to generate the menu.lst and install grub bootloader on the sabayon root partition)

---

