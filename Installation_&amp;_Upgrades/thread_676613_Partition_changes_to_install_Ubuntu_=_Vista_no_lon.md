---
title: "Partition changes to install Ubuntu = Vista no longer boots?!"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Zorlin on 2008-01-23
Hello, I've recently installed Ubuntu 7.10 on a friend's laptop, and regrettably managed to kill Vista in the process.

As much as I hate the operating system, my friend wants Vista to be working again, so yeah.

Basically, I did the following things.

1) Resized the Vista partition using Vista's partition manager.
2) Tried to make the partitions, then realised I couldn't because of the evil recovery disk partitions etc etc pushing it over the 4 partition limit.
3) Tried to install to an extended partition instead, didn't work.
4) Got permission and erased the recovery partitions, then made Vista take up the room that was freed up, bar 10GB that is reserved for Ubuntu.
5) Made a 512MB swap file partition.
6) Made a 128MB /boot partition
7) Rest of the 10GB went to Ubuntu.

Note: One of the recovery partitions was positioned *before* vista, and I moved Vista to partition #1 :(

Everything appeared to be fine, but when I rebooted back into Vista, the boot loader failed, claiming it couldn't find C:\windows\system32\winload.exe; and I assume what has happened is that since the partition numbers are different now, BCD cannot boot Vista [because it cannot find it].

One solution I think might work for me would be to free a little space at the front of the partition table and create a very small blank/useless partition there, thus pushing Vista to partition #2, and probably solving the problem =) I've tried doing this in Ubuntu, but as soon as I unmount /dev/sda2 GParted can no longer read the contents of the NTFS filesystem =/

At this stage, I'm looking for a tool that will allow me to edit the BCD settings etc from within Linux, or using another Windows machine (Windows XP, not Vista) thus just editing it to recognize Vista as being on Partition 1, not 2.
or -
A partition editor tool that can resize Windows Vista safely.

Or if any of you have a better solutions, please post them!

Install however, went smoothly, and aside from sound issues, Ubuntu is running nicely.
Keep on rocking :guitar:

EDIT:
A user from #ubuntu on FreeNode.org suggested I try the official GParted LiveCD, I'll try this. Back in 5 minutes.

EDIT2:
Used a GParted LiveCD to move the Vista partition forward, and made the new /boot partition the first partition, thus pushing Vista back to #2 on the partition table. However, BCD still cannot boot Vista.

Does anyone know of a BCD editor for Linux/XP?
Seeing as this is an odd situation, I imagine not =(

EDIT3:

ITSSSS... ALIIIIIIIIIIIIIIIVE!

I finally managed to get Vista to boot back up, as much as I *despise* it.

How did I fix it?
Well, the problem can be fixed with a Vista install disk, OR (and this is the option I used):

Google "Vista Recovery neosmart" and download the ISO, burn it to disk [120MB], boot the disk, run through the steps, and when presented with a huge "install" button, look in the bottom left for the far less huge repair button.
Press repair, run through the steps, and when finished and you have Vista running, dispose of the disk :)

The 120MB recovery disk from NeoSmart is a far better option than hunting down a Vista install DVD or downloading a Vista ISO off the internet, so I'd recommend it :)

Problem solved!

---

### Post by Gannin on 2008-01-24
Is there any particular reason you want to use BCD to boot instead of Grub?

---

### Post by Zorlin on 2008-01-25
I'm using GRUB to boot Ubuntu, and also to *attempt* to boot Vista. To boot Vista, grub needs to load BCD which then loads Vista.

---

### Post by Gannin on 2008-01-25
What does your Grub menu.lst look like?

---

### Post by Zorlin on 2008-01-25
My /boot/grub/menu.lst file: 
:popcorn:
```

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
# kopt=root=UUID=14bf2481-82e2-4c25-be9e-3035e8479e5e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=14bf2481-82e2-4c25-be9e-3035e8479e5e ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=14bf2481-82e2-4c25-be9e-3035e8479e5e ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

