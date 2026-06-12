---
title: "No boot manager after installing Ubuntu 7.04"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by etech1 on 2007-07-10
Hello,

After installing earlier Ubuntu/kubuntu OS's on several systems dual booting with WinXP without a hitch I decided to try it on my personal system that was dual booting XP and Vista RC1. XP is installed on the First C: drive which also contains a data partition. About 2G of free space on this drive was used for the Ubuntu swap partition. A second drive had a Vista OS partition along with a data partition. The Vista partition was removed using the XP disk management console. The Vista Bootloader was removed using fixmbr/fixboot in the recovery console. Now XP boots automaticly as it did before the Vista installation.

Now I install Ubuntu 7.04 from the live CD choosing the manual disk placement option as I want to create the Ubuntu partition in the free space left by the Vista partition removal. The swap was created on the first drive as described above, the ext3 Ubuntu partition used all the free space left from the Vista removal, I use the "/" option for the mountpoint in the dropdown box but am unsure if this is the correct option. Ubuntu starts to install, strangly, the migraton wizard gives the option of saving files from doc and settings Windows Vista-Longhorn (approx. wording). Thinking it calls my XP installation Vista -Longhorn I choose to migrate alll the files and the installation completes sucessfully but there is no Ubuntu boot menu after rebooting, XP just boots as it always had. The Ubuntu files and folders are there and everything seems like it should. I tried fixmbr/fixboot and reinstalling Ubuntu this time not migrating any files with the same result.

Tried to boot Ubuntu using a "Super Grub" bootable CD, got an "error 13 - invalid or unsupported executable format" when choosing the Ubuntu partition.

If there's no way to enable the boot loader, is it possible to boot Ubuntu using a boot disk. I remember Kubuntu or an earlier linux OS had the option of starting in that fashion.

Thanks for any help with this!

Here's the output of the menu 1st file if it will help

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c8b4dea0-6174-4aa6-b597-82876e72346d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-15-generic
root (hd3,3)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=c8b4dea0-6174-4aa6-b597-82876e72346d ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd3,3)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=c8b4dea0-6174-4aa6-b597-82876e72346d ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd3,3)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Windows Vista/Longhorn (loader)
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by confused57 on 2007-07-10
You might want to install grub to the Ubuntu drive's mbr(if you can boot to it first in bios), using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Follow the directions in the thread, and elect to "setup (hd3)", if "find /boot/grub/stage1 results in "root (hd3,3)"...then boot first to your drive with Ubuntu...if you get a grub boot menu, highlight the Ubuntu entry, press "e" to edit, then change root from (hd3,3) to (hd0,3), then press "b" to boot...Note: you'll need to press "e" again after highlighting your root line to edit....this change is temporary, but you can make it permanent(if it works).

---

