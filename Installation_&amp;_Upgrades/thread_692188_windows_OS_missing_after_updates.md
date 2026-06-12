---
title: "windows OS missing after updates"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by freefallcard on 2008-02-09
the next day after installing updates my windows OS was missing from the GRUB boot menu. I opened the boot.lst and my windows OS has been replaced by:

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

how can i get my windows back? Thanks in advance for any help

---

### Post by buntu_Geek on 2008-02-09
Post here the result of the command:

cat /boot/grub/menu.lst

---

### Post by freefallcard on 2008-02-09
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
default         6

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
# kopt=root=UUID=015501fe-a4a4-43cd-b3e2-6d28f17f143b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
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

# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1[/B]

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=015501fe-a4a4-43cd-b3e2-6d28f17f143b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=015501fe-a4a4-43cd-b3e2-6d28f17f143b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


i was able to add the windows option (between the 2 "should update" in the list. I read some other posts that said i could copy it from the examples above, but it didnt fix the problem, it still doesnt show on boot. also, how do i get permission to edit the list, sometimes it lets me most of the time it doesnt.
Thanks

---

### Post by sandysandy on 2008-02-09
to edit menu.lst the command is

gksudo gedit  /boot/grub/menu.lst 

but be careful while editing menu.lst. also take a backup.

regards

---

### Post by SunnyRabbiera on 2008-02-09
Well for starters if you need to edit these kinds of files you need to have root privileges, to do this you need to go to a terminal and type in sudo then your password to get your root privileges working.
Now I cannot help you officially as I never did what you have to do, but i can give you a place to start.

---

### Post by freefallcard on 2008-02-09
Many thanks to all that replied. after a few hours of searching i found another post with the same problem, the poster posted the changes they made and i was able to copy them into my menu.lst. as a bonus i was able to change the boot order and got to know my ubuntu a little better. i will post my changes for the benefit of others next time Im on ubuntu. THANKS!!!

---

### Post by freefallcard on 2008-02-09
ok, heres a fix that should fix the problem if it happens to anyone else

in terminal enter gksudo gedit /boot/grub/menu.lst
scroll to:

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

and replace it with

title    MS Windows XP
root     (hd0,1)
savedefault
makeactive
chainloader    +1

of course backup menu.lst before making changes.... just in case.
thanks to all who helped and i hope this helps others.

---

