---
title: "Configuring GRUB with menu.lst"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by Spinelli on 2006-05-25
I have a total of 3 hard drives. I have an 80.0GB Seagate IDE hard drive, which is /dev/hda. I have Ubuntu AMD64 5.10 installed on /dev/hda1 and I also have a swap partition on this drive. I use it as my primary OS, I do all of my work on it.
     I have have two 120.0GB Seagate SATA hard drives, which are /dev/sda and /dev/sdb. /dev/sdb1 is partitioned as ext3 and I use for backup. It takes up the entire disk. I would like to install multiple GNU/Linux distrobutions on /dev/sda.
     Today I installed Kubuntu AMD64 5.10 onto /dev/sda1. During installation I manually edited the partition table and deleted all of the partitions on /dev/sda. I created a new partion /dev/sda1 and used the following options:

Use As:                         ext3
Format the Partition:     yes, format it
mount point:                  /
mount options:              default
reserved blocks:            5%
typical usage:                standard
bootable flag:                on
size:                              24.0GB

I also created a 1.0GB logical swap partion on /dev/sda. When the installer asked about installing GRUB I choose not to install it because GRUB is already installed on the MBR of /dev/hda. I booted into Ubuntu on /dev/hda1 and edited /boot/grub/menu.lst. I read about GRUB and menu.lst at the following links:

[http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html]("http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html")
[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")
[http://www.gnu.org/software/grub/grub-legacy-faq.en.html]("http://www.gnu.org/software/grub/grub-legacy-faq.en.html")
[https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29]("https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29")
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")
[http://www.openbg.net/sto/os/xml/grub.html#menu]("http://www.openbg.net/sto/os/xml/grub.html#menu")
[http://www.troubleshooters.com/linux/grub/grub.htm]("http://www.troubleshooters.com/linux/grub/grub.htm")
[http://www.troubleshooters.com/linux/grub/grubpartition.htm]("http://www.troubleshooters.com/linux/grub/grubpartition.htm")
[http://ubuntuforums.org/showthread.php?t=179087&highlight=grub]("http://ubuntuforums.org/showthread.php?t=179087&highlight=grub")
[http://ubuntuforums.org/showthread.php?t=167269&highlight=grub]("http://ubuntuforums.org/showthread.php?t=167269&highlight=grub")

There is a copy of /boot/grub/menu.lst:
[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout 	10	

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hda1 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous 
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hda1 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title	Kubuntu
root	(hd1,0)
kernel	/boot/vmlinuz root=/dev/sda1
initrd	/boot/initrd.img
boot
[/PHP]
Please note the entry at the very bottom. When I enter the GRUB menu and select the last entry titled Kubuntu all I get is a black screen with this:

Booting 'Kubuntu'
root (hd1,0)
Filesystem type is ext2fs partition type 0x83
kernel /boot/vmlinuz root=/dev/sda1

Why doesn't Kubuntu boot? Any help or suggestions would be greatly apprecitated.

---

### Post by Jose Catre-Vandis on 2006-05-25
You will need to add the full vmlinuz filename and probably the full initrd file name like so: (my filenames are just examples)

```
title    Kubuntu
root    (hd1,0)
kernel    /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1
initrd    /boot/initrd.img-2.6.15-23-386
boot  
```

The files you need are in the root directory of your /dev/sda1

---

### Post by Spinelli on 2006-05-25
[QUOTE=Jose Catre-Vandis]You will need to add the full vmlinuz filename and probably the full initrd file name like so: (my filenames are just examples)

```
title    Kubuntu
root    (hd1,0)
kernel    /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1
initrd    /boot/initrd.img-2.6.15-23-386
boot  
```

The files you need are in the root directory of your /dev/sda1[/QUOTE]

I made the changes to my menu.lst file, and it still didn't work. My Kubuntu entry looks like this now:

title	Kubuntu
root	(hd1,0)
kernel	/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1
initrd	/boot/initrd.img-2.6.12-9-amd64-generic
boot

The contents of /boot on /dev/sda1 are:

abi-2.6.12-9-amd64-generic
memtest86+.bin
config-2.6.12-9-amd64-generic
System.map-2.6.12-9-amd64-generic
initrd.img
vmlinuz
initrd.img-2.6.12-9-amd64-generic  
vmlinuz-2.6.12-9-amd64-generic

initrd.img and vmlinuz are both symbolic links.

Any further ideas, help, or suggestions would be greatly appreciated. Thank you.

---

### Post by Sutekh on 2006-05-25
[quote=Spinelli]I made the changes to my menu.lst file, and it still didn't work. My Kubuntu entry looks like this now:

title    Kubuntu
root    (hd1,0)
kernel    /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1
initrd    /boot/initrd.img-2.6.12-9-amd64-generic
boot

The contents of /boot on /dev/sda1 are:

abi-2.6.12-9-amd64-generic
memtest86+.bin
config-2.6.12-9-amd64-generic
System.map-2.6.12-9-amd64-generic
initrd.img
vmlinuz
initrd.img-2.6.12-9-amd64-generic  
vmlinuz-2.6.12-9-amd64-generic

initrd.img and vmlinuz are both symbolic links.[/quote] Which is why you don't actually need to specify the kernel image (vmlinuz) or initial ramdisc (initrd). The symlinks point to the most current ones.

Anyway, the *only thing* I can think of is the difference between your Ubuntu install on hda1```
title          Ubuntu, kernel 2.6.12-10-amd64-generic Default  
root           (hd0,0)  
kernel         /boot/vmlinuz root=/dev/hda1 **ro quiet splash**  
initrd         /boot/initrd.img 
savedefault 
boot 
```  and the one on sda1
 ```
 title     Kubuntu
 root      (hd1,0)
 kernel    /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1 
 initrd    /boot/initrd.img-2.6.12-9-amd64-generic
 boot
``` Try adding the bold text to the sda1 menu entry.

---

### Post by Spinelli on 2006-05-25
[QUOTE=Sutekh]Which is why you don't actually need to specify the kernel image (vmlinuz) or initial ramdisc (initrd). The symlinks point to the most current ones.

Anyway, the *only thing* I can think of is the difference between your Ubuntu install on hda1```
title          Ubuntu, kernel 2.6.12-10-amd64-generic Default  
root           (hd0,0)  
kernel         /boot/vmlinuz root=/dev/hda1 **ro quiet splash**  
initrd         /boot/initrd.img 
savedefault 
boot 
```  and the one on sda1
 ```
 title     Kubuntu
 root      (hd1,0)
 kernel    /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1 
 initrd    /boot/initrd.img-2.6.12-9-amd64-generic
 boot
``` Try adding the bold text to the sda1 menu entry.[/QUOTE]

It tried your sugestion, but it did not work. All I got was a black screen with this:

Booting 'Kubuntu'
root (hd1, 0)
Filesystme type is ext2fs partition type 0x83
kernel /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1 ro quiet splash

My Kubuntu entry looks like this now:

title   Kubuntu
root    (hd1,0)
kernel  /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1 ro quiet splash
initrd  /boot/initrd.img-2.6.12-9-amd64-generic

Any further suggestions would be greatly apprecitated. Thank You.

---

### Post by Spinelli on 2006-05-25
Here is summary of what I have tried for my Kubuntu entry in menu.lst:

```
title   Kubuntu
root  (hd1,0)
kernel /boot/vmlinuz root=/dev/sda1
initrd /boot/initrd.img
boot
```
```
title  Kubuntu
root  (hd1,0)
kernel  /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1
initrd /boot/initrd.img-2.6.12-9-amd64-generic
boot
```
```
title Kubuntu
root  (hd1,0)
kernel  /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1 ro quiet splash
initrd  /boot/initrd.img-2.6.12-9-amd64-generic
boot
```
What does ro quiet splash mean?
```
title Kubuntu
root  (hd1,0)
kernel  /boot/vmlinuz root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img
boot
```
After trying all of these and rebooting my computer a bunch of time I decided to use the command line  in GRUB. I entered into the GRUB menu and pressed 'c' to go to the command line. This is what I typed:
```
grub> root (hd1,0) <enter>
```
It printed this information on the screen:
Filesystem type is ext2fs, partition type 0x83
```
grub> find /boot/v <tab>
```
It completely froze. I tried pressing tab a bunch of times. I tried hitting esc, enter, and every other button on the keyboard. Nothing happened. Any advice would be greatly appreciated. Thank You.

---

### Post by Jose Catre-Vandis on 2006-05-26
Should you have installed grub to the sda partition?

e.g. 3 options

Install grub to mbr on hd1   <- "No" ?
Install grub to install partition on sda1  <- "Yes" ?
Do not install grub at all <- "No"?

Sutekh probably has the wise answer, as my knowledge is clearly deficient!

---

### Post by R3linquish3r on 2006-05-28
You have a good sized hard drive for your Ubuntu install... Why not just install Kubuntu ontop of Ubuntu so you can switch between the two as you like so there is less configuration you have to do for each. For example, I have a 160GB drive that I have Ubuntu+Gnome, Kubuntu+KDE, and Fluxbox installed on, which I used KDM as my display manager. I can switch between each desktop as I prefer, plus I get all of gnome and KDE's appications in one bunch which I tend to switch between alot. I.E. I use GAIM and Amarok. Just to give you an idea, my drive has only used 14GB out of 160 for all this.

---

### Post by Spinelli on 2006-05-31
I finally figured out what was wrong. Both of my SATA hard drives (/dev/sda and /dev/sdb) were plugged into the same RAID controller. I had the drives set up in a RAID 0 array in the BIOS. All I had to do was destroy the RAID array using the  BIOS. I reinstalled Kubuntu AMD64 on /dev/sda1 and the following entry booted into it...
```
title Kubutnu 5.10 AMD64
root (hd1,0)
kernel /boot/vmlinuz root=/dev/sda1
initrd /boot/initrd.img
boot
```
I would like to thank everyone for their help!

---

