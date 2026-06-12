---
title: "Please Help..Emergency - Grub Error 15"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by soham-c on 2008-06-29
Please help, Emergency!! GRUB problem - error 15
Hi,


I have a Dell latitude D600 with 40 GB hard drive laptop on which Windows XP SP2 is installed. There are two ntfs partitions here - c: drive is 21Gb and e: drive is 21GB; there is also a Cd\dvd COMBO drive d:

I also have a Samsung USB portable hard-drive of size 160 GB with FAT32 formatting.

I booted from the Ubuntu 8.04 Live installation CD and installed Ubuntu onto the portable hard-drive using the guided partition resizing(with the graphical slider bar) where I allocated around 11 GB for the Ubuntu installation leaving the remaining 138 GB as FAT32.

After installation was complete, I rebooted the computer with the portable hard-drive still attached and booted into the newly installed Ubuntu operating system. I then logged off and and shutdown the laptop. Then I detached the portable hard-drive and booted my laptop. By the way, in my BIOS booting options, the boot sequence is in this order -CD-> internal HD-> USB drive etc As soon as the boot sequence was complete the screen displayed -

Grub Stage 1.5....
Grub Error 15

So I'm not able to boot into my Windows XP despite the fact that I've not attached the portable drive where Ubuntu is installed. I rebooted again this time with the portable drive attached and was presented with the Grub choice menu of Ubuntu...memtest..Windows XP.

I selected Windows XP and logged in and it worked fine.
I again rebooted, this time I logged into Ubuntu.

The following mounted devices are being shown using Gparted
/dev/sda1 ntfs 19.53GB; boot
/dev/sda2 ntfs 17.72GB
unallocated 7.84MiB

//the Windows XP installation is on /dev/sda1

now for the USB portable device the partitions are as follows -

/dev/sdb1; fat32; media/HD-PFU2; 138.03GB; 14.09GB; 123.95GB; lba;

/dev/sdb2 extended; 11.02GB
/dev/sdb5; ext3; / ; 10.50GB
/dev/sdb6; linux-swap; ; 525.53Mib

I would like to know how I can boot into my Windows XP partition on my laptop hard-drive, as I had normally been doing so far, without connecting the portable hard-drive. I also don't want to have Ubuntu installed on the portable hard-drive. I had intended to make the portable USB hard-drive as a Live USB drive but it seems I have messed it up badly and I would like to restore it to the old system. Have I done something wrong with the partitioning process? What do I need to do here to be able to boot normally into XP without having to attach my USB drive.

Please help...This is an emergency...and I need to get it back as quickly as possible withing 2-3 hours.

Running sudo gedit/boot/grub/menu.lst I found the following

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=0d81843e-fa6d-4c3d-9324-3054faac50ae ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0d81843e-fa6d-4c3d-9324-3054faac50ae ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0d81843e-fa6d-4c3d-9324-3054faac50ae ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd1,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Pumalite on 2008-06-29
You can restore your Windows MBR with Super Grub or your installation disk. As for the restoration of your old system in the portable; only you know what you had there.

---

### Post by didac on 2008-06-30
You installed GRUB to the laptop hard disk, but the files needed by GRUB to boot are installed in the USB hard disk. GRUB needs them to continue booting. As you are in a hurry -- and this answer comes a bit late -- press any key when booting, to get the GRUB selection screen, drop to a command line pressing 'c' and enter the following lines one after another:

```

root (hd0,0)
makeactive
chainloader +1 

```

Then follow Pumalite's advice

---

