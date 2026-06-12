---
title: "Help with grub plz"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by wootwoot123 on 2006-02-19
This weekend I installed Ubuntu 5.10 and after installation I was getting a grub error 17. I read somewhere that if I changed my hard drive setting in the bios it might fix my problem. I have 2 hard drives, hda and hdd. Ubuntu is the first partition on the 2nd drive. I switched the bios from auto detect hdd to LBA addressing. This fixed things and grub came up like normal and things were good again. The problem comes when I boot back into windows. When I am accessing that drive I get random reboots. The strange thing is that when I had gentoo on my hard drive it never gave me any grub errors but ubuntu does. So I am wondering if I can upgrade to a newer version of grub so that I dont have to make a change in the bios? Anyways here are some of my grub files so if you guys see anything wrong please let me know, I really need to have both OS's working fine, thx.

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdd1 ro

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

title           Ubuntu, kernel 2.6.12-9-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1




---

### Post by wootwoot123 on 2006-02-20
Cmon someone has to know. There seem to be a ton of grub problems in this forum, where can I go to learn more about fixing this?

---

### Post by wootwoot123 on 2006-02-21
Well I changed my bios back to auto and did and a fixmbr, no more ubuntu for me. It was cool while it lasted but I cant give up windows yet. If anyone has advice so I can dualboot that would be great, thx.

---

### Post by Schmic on 2006-02-22
Do you still have ubuntu installed?

If so you should try reinstalling grub if you haven't already tried. It's fairly easy, just put your ubuntu install disc in and start the install, go throught the first part and get your keyboard, language, etc setup but stop before installing the files. You can skip down to the Installing bootloader section and just configure it again like you did the first time and exit out of it. It will spit up a few errors about installation fail because files were not installed but thats fine.

Reboot and grub should be running again like new and hopefully without the errors.

Do a search in the forums and you should find better instructions, i am trying do do this from memory:-k 

I hope this helps

---

