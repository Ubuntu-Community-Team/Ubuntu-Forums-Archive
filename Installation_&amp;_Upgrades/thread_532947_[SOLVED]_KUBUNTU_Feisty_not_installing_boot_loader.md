---
title: "[SOLVED] KUBUNTU Feisty not installing boot loader"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by glasswalkerny on 2007-08-23
Hi,

   I'm relatively new to UBUNTU but managed to install a server and set up LAMP and Email (postfix/courier) by following great tutorials in the forums.. I've also installed Feisty on a COMPAQ PC but I've recently decided to dump Vista from my gaming rig because i loathe Microsoft and 90% of the games I've been playing run fine from Cedega now.

My problem is i can't get KUBUNTU to boot after install.. i never see it run a grub install phase during install and it never seems to install a boot loader. At first i was trying to set up dual boot with VISTA but decided to get rid of it to eliminate a possible complication. Then I tried installing '/' on sda1 (sata drive) and /home on sda2 but that didn't work.. i then noticed that my bios detects the drives in a different order from Linux' numbering scheme so i tried installing '/' on sdb1 (sata again) and that still is not working.. i have the following setup

ASUS A8N-E motherboard
AMD 64 3500+
2gb ram
Chaintech Apogee AE78GT (NVIDIA 7800GT) (hope to get dual monitors working off this)
Soundblaster X-FI Extreme Gamer
Memorex 52x CDROM / Generic Lightscribe DL DVD/CDR/RW drive (snagged outta that compaq)
2 - Maxtor 200gb hdd (primary sata 1 and secondary sata 1 in bios)
1 - Maxtor 250gb hdd (primart sata 2 in bios)
(i'll edit in model numbers when i reboot again)

here's the output from my fdisk -l and menu.lst (which proves it installs grub to /boot)

```

ubuntu@ubuntu:/proc$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         249     2000061   82  Linux swap / Solaris

```

Menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=377af3a7-4f46-45b8-9724-7fd5624682a3 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=377af3a7-4f46-45b8-9724-7fd5624682a3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=377af3a7-4f46-45b8-9724-7fd5624682a3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Pumalite on 2007-08-23
Use Super Grub to find out what's going on with your system and re-install Grub if necessary: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If you prefer, you can follow these guidelines to re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by glasswalkerny on 2007-08-23
Thanks for the quick reply.. burning the Supergrub cd and will try that now

---

### Post by glasswalkerny on 2007-08-23
ok i tried both of your suggestions... i'm not sure if i did the right things with the SuperGrub cd but in any case i found out that grub is installing to SDC's MBR.. this makes no real sense.. is there a way i can determine the Bios to Linux mapping for the drives? they're obviously not coming up the same way in both or there's something really wierd about my system.. BTW windows sees my drives in the right order (first sata drive was C and so on)

---

### Post by Pumalite on 2007-08-23
/boot/grub/device.map
Your SATA drives in BIOS have to be totally independent from each other

---

### Post by glasswalkerny on 2007-08-23
ok i missed your last reply (thanks btw)
I got it working by following the instructions here [Fake Raid Howto]("https://help.ubuntu.com/community/FakeRaidHowto")

I thought if i could eliminate the confusion of 2 identical drives (make/model/size) that i would have a better time so i set the 2 200gb drives as mirrored. 

[COLOR="Silver"]So i'm booting to a KDE login but it won't let me login with the user i set up in that Howto... 
it didn't have me set groups and such is that what's wrong?[/COLOR]

Well for some reason it's letting me log in now.. i know what i did wasn't entirely the right way to fix this.. is this a known issue that sata drives are detected differently in linux than in the bios?

---

### Post by Pumalite on 2007-08-23
If you had started your thread by saying 'Want to install Kubuntu in Raid Array' we would have saved much time.

---

### Post by glasswalkerny on 2007-08-23
Initially i wasn't going to do the Raid.. but it seemed to help with whatever wierdness i was running into.. thanks for trying to help!

---

