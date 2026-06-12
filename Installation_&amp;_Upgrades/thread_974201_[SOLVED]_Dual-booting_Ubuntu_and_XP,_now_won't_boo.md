---
title: "[SOLVED] Dual-booting Ubuntu and XP, now won't boot"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by TheJimtasticOne on 2008-11-07
My set up is Windows XP and Ubuntu (8.10 AMD64) booting from separate partitions. I installed XP first, then ubuntu, with grub overwriting the windows MBR. Grub was booting into ubuntu fine, but when I tried booting into XP, the following messages came up:
"Starting up...
GRUB loading stage2"

I thought maybe grub hadn't installed correctly, so I booted a livecd and used a terminal to reinstall grub. Nothing changed. Then I tried using the XP install disk to rewrite the MBR ("FIXMBR" in the recovery console). Now when my machine boots, all it says is "GRUB" at the top of the screen. Then the only thing I can do is reboot. Has anyone got any idea how I can fix this?

---

### Post by oilchangeguy on 2008-11-07
the correct way to fix windows boot record is as follows:
boot from the windows cd, enter the recovery console, at the prompt type fixboot and press enter, then type fixmbr and press enter, then type exit and press enter. it should boot into windows.

---

### Post by TheJimtasticOne on 2008-11-07
OK thanks, I'll try that.

---

### Post by TheJimtasticOne on 2008-11-07
Well, I'm back to where I started now. fixboot and fixmbr restored the boot sector to the way it was before I installed ubuntu, so windows  just loaded up normally. Then I tried to reinstall grub, and I'm back to where I started: I boot up, grub menu appears, select windows, this message comes up:
"Starting up ...
GRUB Loading stage2 .."
and nothing else happens.

Ubuntu loads as normal.

What I'm thinking is that the starting up... message usually comes from windows (I think?) and the gRUB message is obviously from GRUB, so maybe the two bootloaders got mixed up with each other?

---

### Post by caljohnsmith on 2008-11-07
When you are in Ubuntu, how about posting the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there.

---

### Post by TheJimtasticOne on 2008-11-07
Hokeydokey, sudo fdisk -lu gives:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000dc7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2        83891430   167782859    41945715   83  Linux
/dev/sda3       167782860   251674289    41945715   83  Linux
/dev/sda4       251674290   488392064   118358887+   5  Extended
/dev/sda5       251674353   477901619   113113633+  83  Linux
/dev/sda6       477901683   488392064     5245191   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ba14fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1        51199155    96116894    22458870   83  Linux
/dev/sdb2        96116895   160071659    31977382+   5  Extended
/dev/sdb5        96116958   155878694    29880868+  83  Linux
/dev/sdb6       155878758   160071659     2096451   82  Linux swap / Solaris


And cat /boot/grub/menu.lst gives all this lovely stuff:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/green red/black

#A splash image for the menu
#splashimage=/boot/grub/splashimages/86703-ubuntu_colors.xpm.gz

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
# kopt=root=UUID=ecdb2c3f-56e1-41a0-a01c-76881d0bacb6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ecdb2c3f-56e1-41a0-a01c-76881d0bacb6

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
# defoptions=quiet splash vga=769

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ecdb2c3f-56e1-41a0-a01c-76881d0bacb6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ecdb2c3f-56e1-41a0-a01c-76881d0bacb6 ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ecdb2c3f-56e1-41a0-a01c-76881d0bacb6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ecdb2c3f-56e1-41a0-a01c-76881d0bacb6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ecdb2c3f-56e1-41a0-a01c-76881d0bacb6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dba55e87-acb2-40de-bb16-da94a6742e66 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dba55e87-acb2-40de-bb16-da94a6742e66 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dba55e87-acb2-40de-bb16-da94a6742e66 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dba55e87-acb2-40de-bb16-da94a6742e66 ro single 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
Did I paste that right, or is there a scrolly thing you can use so it takes up less space?

By the way, /dev/sda is a 250GB SATA hard drive, and /dev/sdb is an 80GB IDE. You may find they're swapped around in menu.lst, there was some way of getting them to swap round but I don't think menu.lst has that.

---

### Post by caljohnsmith on 2008-11-07
OK, so if Windows is on the same drive as Ubuntu, you just need a slightly different entry for Windows in your menu.lst. Begin by opening the menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom of the file, replace the existing Windows entry with:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Give that a shot and let me know exactly what happens when you choose Windows from your Grub menu. :)

---

### Post by TheJimtasticOne on 2008-11-07
Boots up windows like nothing ever happened apart from one thing: it doesn't respond to moving the mouse, clicking or typing on the keyboard (not even Ctrl+Alt+Del). Only thing it responded to was pressing the power button. I don't know if this was related, could you shed some light on it?

I think I know what happened with the booting, though, because the 80gb IDE drive used to have ubuntu and windows on it, so the new grub was probably trying to load the old bootloader instead of windows on the new drive.

---

### Post by caljohnsmith on 2008-11-07
> **TheJimtasticOne said:**
> Well, I'm back to where I started now. fixboot and fixmbr restored the boot sector to the way it was before I installed ubuntu, so windows  just loaded up normally.
You mentioned the above previously; so when you booted directly into Windows, did the keyboard and mouse work?

---

### Post by TheJimtasticOne on 2008-11-07
Yes, but that was with the windows bootloader. Should I try again and see if they work properly this time? I think one of the commands I deleted from menu.lst - perhaps savedefault - might have been responsible for this. But it may have just been anomalous.

---

### Post by caljohnsmith on 2008-11-07
> **TheJimtasticOne said:**
> Yes, but that was with the windows bootloader. Should I try again and see if they work properly this time? I think one of the commands I deleted from menu.lst - perhaps savedefault - might have been responsible for this. But it may have just been anomalous.
The "savedefault" line only sets it so Grub will default to booting Windows next time on start up, and it only works if you have "# savedefault=true" in your menu.lst. If it's not too much trouble, yes, please try again with the Windows MBR (using "fixmbr") to see whether there really is a difference.

---

### Post by TheJimtasticOne on 2008-11-07
I tried it again (with grub) and it works fine now. I don't know what happened but if it's not going to happen again that's fine by me :) thanks guys.

---

### Post by caljohnsmith on 2008-11-07
Glad to hear it's working. Cheers and have fun. :)

---

### Post by meierfra. on 2008-11-07
[QUOTE=caljohnsmith]The "savedefault" line only sets it so Grub will default to booting Windows next time on start up, and it only works if you have "# savedefault=true" in your menu.[/QUOTE]

Not quite right. "savedefault"  only works if you have "default saved" in menu.lst.  
"savedefault=true" tells "update-grub" to add "savedefault" to  the  ubuntu items in menu.lst.

---

### Post by caljohnsmith on 2008-11-07
> **meierfra. said:**
> Not quite right. "savedefault"  only works if you have "default saved" in menu.lst.  
"savedefault=true" tells "update-grub" to add "savedefault" to  the  ubuntu items in menu.lst.
You're right, I wasn't remembering correctly. Thanks for clarifying that.

---

