---
title: "&quot;Error loading operating system&quot;"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by soulmatic09 on 2007-11-03
i am currently adding ubuntu to an XP system.

i backed up my XP to a slave harddrive with partimage.

then, i downloaded the livecd, and verified it. I burned the cd, and verified that too.

I made an ext3 partition on the master drive, and installed the new OS.


the installation went through with no problems, however when i reboot, the computer gives a "Error loading operating system" message before the dual boot screen comes on. so now i can't access either OS.

i tried to restore the old partition, but whenever i type in the path of the image file, partimage crashes.


i've reinstalled the OS 3 times, and i keep getting the same result. i also switched the BIOS setting to LBA from Auto. what am i doing wrong?

any advice would be a **huge** help.

thanks

---

### Post by zvacet on 2007-11-04
Maybe tis will be helpfull 

[http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by soulmatic09 on 2007-11-04
thanks, i'll give it a look.

---

### Post by soulmatic09 on 2007-11-04
ok, i looked through those links, and i had already done most of it to no avail.

one of those links was new, and i typed in the code. turns out that code deleted my entire MBR!

i downloaded fdisk, and did the fdisk /mbr command, which didn't do anything.

so, i downloaded supergrub. at least now, i get the option of booting xp or ubuntu.


when i try to boot into xp, it says it can't find the drive.

when i try boot into ubuntu, i get "Error 21: selected disk does not exist"

so now what?

TIA

---

### Post by soulmatic09 on 2007-11-04
here's the menu file, if that helps:

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
# kopt=root=UUID=46da8a10-b444-46b0-97cc-17d007c0429c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=46da8a10-b444-46b0-97cc-17d007c0429c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=46da8a10-b444-46b0-97cc-17d007c0429c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by soulmatic09 on 2007-11-04
so after i reboot, of course, it doesn't work.

i tried a couple more things....

i get nothing.


i reboot again.


but by accident, i hit the 'e' button in the GRUB boot screen. (i think i was trying to type 'reboot' but i missed the 'r' key)

and from out of the blue i get this 'EDIT' screen, which i've never seen before. it was showing the 'hd2,0' info from my menu file i showed you earlier.

so in desperation, i start messing with it. i got nothing to lose right?

i try hd0,0.

nothing.


hd1,0.

nothing.


hd1,1.

nothing.


hd0,1 (or something)

"Starting Linux..."


0_0

i'm like, "wha?"

i can't believe it.

i made it work by making a typo!

ain't that something?

wow.

I wish i knew what I actually typed in, but for whatever reason it worked. i guess it was pointing to the wrong hard drive.

---

