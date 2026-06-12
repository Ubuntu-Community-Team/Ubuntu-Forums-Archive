---
title: "GRUB autoloading Ubuntu"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by irfrausto on 2005-07-29
This is my first stab at Ubuntu (previously "got my feet wet" with SuSE). Install was a breeze. I had GRUB written to the MBR, but now when I boot-up, I see something about GRUB flash quickly and then it goes directly to Ubuntu. I can't get at my WinXP Pro partition. This is the fdisk -l output:

[b]Device      Boot      Start         End      Blocks   Id  System
/dev/hda1   *          22        1173     8709088+   7  HPFS/NTFS
/dev/hda2            1174        5170    30217320    f  W95 Ext'd (LBA)
/dev/hda3               1          21      158728+  83  Linux
/dev/hda5            1174        1986     6146248+  83  Linux
/dev/hda6            1987        2799     6146248+  83  Linux
/dev/hda7            2800        5061    17100688+   b  W95 FAT32
/dev/hda8            5062        5170      824008+  82  Linux swap / Solaris[/b]

hda3 is /boot and hda5 is /


This is in my menu.lst file (only the relevant stuff):

[b]title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/b]


Any help would be appreciated. :)

---

### Post by amohanty on 2005-07-30
in your 
/boot/grub/menu.lst

put the following line:

timeout 30

at the top.

This will wait 30 secs before autoloading the default. YOu can setup any amt of timeout in secs.

HTH
AM

---

### Post by irfrausto on 2005-07-30
I had already set it to 30 seconds. That didn't do anything. When I hit Pause Break on the GRUB screen all it shows is GRUB stage 1.5 is loading. Then I get the black screen, while I assume Ubuntu is booting up. After a minute or so I get to the Ubuntu login screen.

---

### Post by kvidell on 2005-07-30
[QUOTE=irfrausto]I had already set it to 30 seconds. That didn't do anything. When I hit Pause Break on the GRUB screen all it shows is GRUB stage 1.5 is loading. Then I get the black screen, while I assume Ubuntu is booting up. After a minute or so I get to the Ubuntu login screen.[/QUOTE]
 Is there an option for "hidden" or something like that?
I don't have any ubuntu boxes at my disposal at the moment so I don't know the exact option name...

You sure you don't get a screen that briefly states "Press ESC to get the GRUB Menu!" ? (This being the result of the "hidden" option)
- Kev

---

### Post by amohanty on 2005-07-30
'hidden' it is

---

### Post by irfrausto on 2005-07-30
"hidden" is commented out. Here is my entire menu.lst file contents:

[b]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/b]

---

### Post by irfrausto on 2005-07-30
bump

Sorry, I still need help with this. :|

---

### Post by amohanty on 2005-07-30
Heres my XP-Sp2 dual boot with Hoary grub menu.lst:

default         0
timeout         15
color blue/light-gray

memtest86=false

title           Ubuntu 5.0.4 [2.6.10-5 i386]
root            (hd0,1)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu 5.0.4 [2.6.10-5 i386] [SAFEMODE]
root            (hd0,1)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/sda5 ro single
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,1)
kernel          /memtest86+.bin
savedefault
boot


Compare, contrast and if it still does not work, post results of attempt to fix.

HTH

AM

---

### Post by jemt on 2005-07-30
Do you just get a blank screen while Ubuntu is booting? Sounds like you need to set a proper resolution. I only know how to do this for the Ubuntu boot process - not for grub. But as far as I know, Grub should always be running in 640 x 480 with 14 colors.

You may change resolution by adding 'vga=res' as a kernel parameter. Replace res with the wanted resolution. 0x318 provides you with the resolution 1024 x 768 @ 16 bit. You can find more resolutions [here](http://www.gentoo.org/doc/en/handbook/2005.0/handbook-x86.xml?part=1&chap=10)

Booting your kernel with 1024 x 768 in 16 bit colors looks like this :

kernel /vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash vga=0x318

But unfortunately I'm not sure this will solve your problem with Grub. Only the problem with the blank screen while booting.

---

### Post by irfrausto on 2005-07-31
I was able to figure it out. I added a splash screen. I guess my setup doesn't like using a CLI.

---

