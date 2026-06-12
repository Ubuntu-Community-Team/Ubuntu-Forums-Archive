---
title: "Dual boot: Ubuntu and Windows 2000"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by taidur on 2005-10-30
1.) New PC with one hdd.
2.) I installed Ubuntu
3.) Installed Win 2000. After that it was not possible to log into the Ubuntu.
4.) I restored grub into the MBR via Ubuntu Live CD. Now I can boot into the Ubuntu but not into the Win2K.
5.) What should I do to make it work correctly? I want grub to ask me which OS to boot.

Current menu.lst :

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot



fdsik -l :

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4863    39062016   83  Linux
/dev/sda2   *        4864        9962    40957717+   7  HPFS/NTFS

---

### Post by bunced on 2005-10-30
Is that all you have in menu.lst - there should be some more than that?

---

### Post by taidur on 2005-10-30
[QUOTE=bunced]Is that all you have in menu.lst - there should be some more than that?[/QUOTE]

Yes there is some more it does not seem to be too important :)



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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

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
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##



and here comes the part I already posted in the first thread.

---

### Post by al7kz on 2005-10-30
Reboot the computer and at the grub menu type c to get the grub command line, then type in the commands:
>rootnoverify (hd0,1)
>makeactive
>chainloader +1
>boot

If that boots win2k then add those commands to menu.lst under Title win2k

---

