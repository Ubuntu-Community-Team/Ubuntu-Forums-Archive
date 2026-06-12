---
title: "boot error - cannot mount specified partition"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by charonred on 2008-06-26
Ubuntu 8.04 LTS runs fine from the Live CD, but after I install it to a hard drive, and then try to boot it, I get the the message
'error 17 - cannot mount specified partition'

I've installed it both from live CD desktop, and direct from CD. 

I got the install iso from a PC magazine DVD here in Australia, so I also downloaded from Ubuntu both the x86 and 64bit desktop versions, and installed from them with the same boot error problem.

My system is about 4 months old; has  Gigabyte GA-MA790FX DS5 m/board, AMD 5600+ 2.8Ghz DC, 2GB Ram, 512MB Asus EAH2600 Pro video. 

I have a 500GB sata for XP Pro plus 2 other 500GB sata drives as storage, and a 500GB pata (data disc from my old pc); and installed a 640GB sata just for Ubuntu and set that as the default boot disc prior to install. 

It goes through the install process fine, but keeps giving me the same old boot error.

Any suggestions to fix this :confused:

---

### Post by charonred on 2008-06-26
reading through other files it seems that Grub may be at fault



the XP OS is on /dev/sda1 and is normally default boot, but for the Ubuntu installation I set the 640GB drive as default boot

Ubuntu is on /dev/sdb1

below is the menu.lst which has Ubuntu on /dev/hdc - I tried editing it in 'text editor' but I didn't have permissions; where is Nautilus

what do I change and how ?


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
# kopt=root=UUID=1c1f78b3-a1cc-4084-96ac-6993d2af40ea ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1c1f78b3-a1cc-4084-96ac-6993d2af40ea ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1c1f78b3-a1cc-4084-96ac-6993d2af40ea ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
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
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

:confused:

---

### Post by charonred on 2008-07-04
I've been underwhelmed by the response to my question; anyhow, I fixed my install and load problem.

GRUB just couldn't get it right no matter what options & editing I tried - GRUB is indeed a 'grubby' boot loader!

The simple solution was unplug all other hard drives from my mainboard and install Ubuntu 8.0.4 to the one remaining drive - GRUB couldn't get 'confused' then.

Hooked up all other drives again; if I want to use Ubuntu, then I just tap tap F12 while my PC is booting (Gigabyte mainboard) and select the drive with Ubuntu installed.

Considering that many new PCs are coming out with more than one drive, GRUB's 'confusion' is of no help to newbies; and certainly doesn't help the cause of making Linux acceptable to the general public - why not use LILO instead?

---

### Post by upchucky on 2008-07-04
Gratz, u found a solution in the time it took me to search and go to post it for you.

anyway grub is a much better loader than lilo as it is more configurable than lilo, especially with so many new systems out there.

it is common to have that error and the fix is to edit the menu file like u tried but u needed to use nano or vi editors as nautilus and gedit need to have xserver running to work, you had not gotten that far yet.

the solution you found was a bit radical but it worked, and you still have to edit the file for the rest of your sys.

doing ```
sudo fdisk -l 
``` would have told you what u needed to put into menu.lst to make it work.

again gratz, and please be patient there are many that will help when they are on and are not busy already helping others.

---

### Post by charonred on 2008-07-04
Thanks Upchucky, 
yeah I'm normally a bit more patient with forum requests, but it's been one of those weeks - computer and car problems at same time (arghh - my XP system is bogging down and is in need of a re-install after only 4 months)

I'll have a look at what you suggested, cause it looks like I might have to re-install Ubuntu again.

ATI Catalyst Control Centre is there, and system is running across 2  x 19" monitors, but since last night effects have ceased working, and have lost all sound (no card ?) 

I got VirtualBox running after a lot of stuffing around, and installed XP SP3. Also have KDE and KDE 4.0 installed, and I think that may have stuffed up the Display and sound, though they all worked last night

FYI 
 
System:
Mainboard - Gigabyte MA790FX DS5
CPU - Athlon XP Dual Core 5600+ 2.8Ghz
RAM - 2GB kit 800Mhz DDR2 KVR800D2N5K2/G
Video - Asus ATI HD 2600 Pro 512MB

Monitors:
Viewsonic VA912 19" LCD
Chimei CMV945A 19" LCD

Drives:
1 x 500GB WD pata (old PC drive in removable bay)
3 x 500GB WD sata (XP OS and 2 storage one in removable bay)
1 x 640GB WD sata (Ubuntu 8.0.4 in removable bay)
1 x Pioneer 20x DVD burner
1 x LG 20x DVD burner

---

