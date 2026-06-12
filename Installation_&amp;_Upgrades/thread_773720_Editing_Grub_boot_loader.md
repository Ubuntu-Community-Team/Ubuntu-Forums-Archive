---
title: "Editing Grub boot loader"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by willthebold on 2008-04-29
So here's the deal: I had 2 harddrives we'll call A and B. I originally had XP on HD A and then installed Ubuntu 8 on HD B. But then HD A crashed and I bought a new one, C. So I installed XP on HD C but can't get the boot loader to go into XP. The only way I can do it right now is to go into the BIOS and change the HD boot order. There is still the option for XP in the boot loader, but when I pick it nothing happens. It just says "Starting Up" and sits there not doing anything. I checked the line in the menu.lst and made sure it was pointing to the right drive and partition, and I think I did it all right but it's not working. I guess this is because this HD and XP install weren't there when I installed Ubuntu originally. How do I fix this? Thanks in advance.

Forgot to add, GRUB is installed on HD B along with Ubuntu.

---

### Post by iaculallad on 2008-04-29
From my experience with window$ xp, you have to install it first (xp) followed by Ubuntu. Ubuntu installation would automatically detect any existing OS and configure it on its GRUB. Seems like window$ OS doesn't like going in second.

---

### Post by forestpixie on 2008-04-29
CAn you open a terminal - paste these commands and post the outouts here please.

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by willthebold on 2008-04-29
sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008f3c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f7ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS
feng@feng-desktop:~$ cat /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=f0e50a54-3170-46ac-8721-eeb72712a06f ro

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f0e50a54-3170-46ac-8721-eeb72712a06f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f0e50a54-3170-46ac-8721-eeb72712a06f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by ssican on 2008-04-29
This Tutorial,also, will help: Dualboot Two Hard Drives:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

EDIT:
Another thread about Two Hard drives:
[http://ubuntuforums.org/showthread.php?t=769916](http://ubuntuforums.org/showthread.php?t=769916)

---

### Post by forestpixie on 2008-04-29
This might help you, it might be necessary to insert the map command in the XP lines.

Open the file from the terminal for editing after backing it up.

```
sudo cp   /boot/grub/menu.lst /boot/grub/menu.lst.2904
sudo nano /boot/grub/menu.lst
```

You're file is now open in the terminal for editing, don't change anything you don't want to, to save the file after you've finished Ctrl+O and enter, to close the editor Ctrl +X.

Add the changes in red to the winXP section at the end of the file.

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
[COLOR="Red"]map                (hd0) (hd1)
map                (hd1) (hd0)[/COLOR]
chainloader +1

---

### Post by willthebold on 2008-04-29
Okay, I made those changes to menu.lst, but now when I try to boot XP, I get a message saying something like "error 23. error while parsing number".

---

### Post by forestpixie on 2008-04-29
I'm not sure then - you could try swapping them so they read 

map (hd1) (hd0)
map (hd0) (hd1)

but I wasn't totally sure to start with. If you change the menu.lst and still have a problem you will need to restore the backup.

The error you are getting is this one - from

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)


> 
Quoted from the GNU/GRUB manual

    23 : Error while parsing number
        This error is returned if GRUB was expecting to read a number and encountered bad data. 

For example, this error can be reproduced in CLI mode GRUB by typing 'root (hdO)' insetad of  'root (hd0)'.

The '0' in  '(hd0)' is a number zero, not a capital letter 'O'. If you type a capital letter 'O' in pace of a number '0' in this context, you will receive this error message.

I try to make sure there is no confusion between the number 0 and letter O in my web pages by using bitstream vera sans mono font wherever I think of it, that way the number 0 has a dot in the middle of it like terminal font.
For example, you can see that 0 is different from O.

---

### Post by willthebold on 2008-04-29
Awesome! I got it working now. When I went back and looked I had accidentally put an o instead of 0 on the first line. I guess that's what I get for trying to type too fast... Thanks again! How do I thank people on here and mark this solved? The "Mark thread as solved" option isn't in the thread tools.

---

### Post by forestpixie on 2008-04-30
See you've worked out the thanks - thank you for that - for the moment the mark thread solved tool is missing - but you can edit the thread title - go to your first thread and edit it.

Glad we got there.

---

