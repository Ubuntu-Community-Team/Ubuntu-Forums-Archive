---
title: "menu.lst Ubuntu 6.10 &amp; Fedora 6 kernel update"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by krzykwas on 2007-02-14
I decided to install both Ubuntu and Fedora on my computer. Both systems have their own partitions and there is also common swap as well as /boot. My /etc/fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=36fcf4be-6bbf-4fac-9fea-f32449076318 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=b5967583-24eb-4fa5-8ffc-6b55dcbd5feb /boot           ext3    defaults        0       2
# /dev/hda2
UUID=d2fe23e8-e4cd-40f2-8fe5-ba914e5efa87 /mnt/fedora     ext3    defaults        0       2
# /dev/hda4
UUID=e8e9ae1b-7579-4a1b-8714-9e293dd971b5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

``` To be able to boot both distributions I prepared such /boot/grub/menu.lst:```
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

## Color screen
splashimage=(hd0,2)/grub/splash.xpm.gz

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
# kopt=root=UUID=36fcf4be-6bbf-4fac-9fea-f32449076318 ro
# kopt_2_6=root=/dev/hda1 ro

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
# defoptions=quiet splash locale=pl_PL

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Ubuntu, kernel 2.6.18-1.2798.fc6
root            (hd0,2)
kernel          /vmlinuz-2.6.18-1.2798.fc6 root=/dev/hda1 ro quiet splash locale=pl_PL
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.18-1.2798.fc6 (recovery mode)
root            (hd0,2)
kernel          /vmlinuz-2.6.18-1.2798.fc6 root=/dev/hda1 ro single
boot

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash locale=pl_PL
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,2)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash locale=pl_PL
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

### FEDORA
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/hda2
#          initrd /initrd-version.img
#boot=/dev/hda

title Fedora Core (2.6.18-1.2798.fc6)
        root (hd0,2)
        kernel /vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=fedora rhgb quiet
        initrd /initrd-2.6.18-1.2798.fc6.img

``` It contains changes that where introduced while automatic Ubuntu kernel update. Ubuntu found in /boot Fedora's kernel that has a bigger version number and put additional entries into menu.lst. I pressume that it will happen each time the system is upgraded.

Is it possible to disable adding Ubuntu's entries with Fedora's kernels while automatic upgrades without editing menu.lst each time? How to do that?

PS I looked for the solution searching by the phrase "menu.lst Ubuntu Fedora". If the topic has already been discused, give me a clue how to find it, please.

---

### Post by louieb on 2007-02-14
I've tried putting /boot in its own partition and  sharing  it between different Linux distributions. That set up was a pain in the rear at  kernel update/upgrade time. 
I don't know how to keep the update program from stepping on menu.lst using the common /boot partition.

Check out the Dual Boot link in my signature. Herman shows 2 or 3 ways to configure multiple Linux distros on the same hard drive.

---

### Post by krzykwas on 2007-02-15
Thanks for your answer, louieb. The herman's advices are very coherent and describe Grub in each detail. Unfortunatelly, I haven't found the solution there. At the beginning I thought about dividing /boot partitions of Fedora and Ubuntu, but finally I resigned. Now I probably would have to re-install everything, wouldn't I?

Maybe my decision was not accurate and probably I will have to edit menu.lst on my own. On the other hand it is not an impossible effort and I am going to cope with it.:)

Anyway, thanks in advance for any idea you might have and share with me.;)

---

