---
title: "Dual boot = fail"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Suckapuncha on 2008-05-24
I just installed 8.04 on a system with Win XP Home on it also. I used the guided partition in the install to create a Linux partition on the 500GB HDD. Everything installed ok...

The problem is, I did this once before and it used to ask me which OS I wanted to boot into. Now, it just boots directly into Win XP whenever the computer is restarted.

Also, I setup 200GB for Linux, so my HDD only shows it has 300GB left on it, and I can't seemed to figure out how to erase the Linux partition and get it back to recognizing the full 500GB. If I try to go through the install again, it only shows a 300GB HDD on the system, and tries to partition that further.

Any ideas would be great, thanks.

---

### Post by Pumalite on 2008-05-24
Boot your Live CD and post:
sudo fdisk -l

---

### Post by jeffus_il on 2008-05-24
Do you have a grub menu soon after booting bios, maybe "press Esc to see the menu" and the does it display "Starting..." or something to that effect??

---

### Post by Suckapuncha on 2008-05-24
here is my sudo fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xecd4ecd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36913   296503641    7  HPFS/NTFS
/dev/sda2           36914       60801   191880360    5  Extended
/dev/sda5           36914       60044   185799726   83  Linux
/dev/sda6           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06950695

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18700   150207718+  83  Linux
/dev/hda2           18701       19457     6080602+   5  Extended
/dev/hda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07104092

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4998    40146403+   7  HPFS/NTFS


and no, I do not have a Grub menu after BIOS, and if I hit Esc, nothing happens, it just boots into Win XP.

Also, when I installed it on the 160GB HDD, it would give me the dual boot menu and ask which OS I wanted to boot into. However, if I selected WIN XP, it would not work because Win XP is on a different HDD, so it told me it couldn't find it.

Also, if there is a better way to boot to either by having them on separate drives, I'm all for it. But even if I do that, I need to get that 200GB partition back on my Win XP drive.

---

### Post by Pumalite on 2008-05-24
Mount your partition:
sudo mkdir/media/hda1
sudo mount -t ext3 /dev/hda1 /media/hda1
Post:
cat /media/hda1/boot/grub/menu.lst

---

### Post by Suckapuncha on 2008-05-24
sudo mkdir/media/hda1
sudo: mkdir/media/hda1: command not found

---

### Post by Pumalite on 2008-05-24
left a space behind:
sudo mkdir /media/hda1
(better copy and paste in the Konsole (Terminal)

---

### Post by Suckapuncha on 2008-05-24
ok here it is:

> # menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=UUID=9e4d3ce0-5226-4676-aa95-00561b62b8a6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e4d3ce0-5226-4676-aa95-00561b62b8a6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e4d3ce0-5226-4676-aa95-00561b62b8a6 ro single
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
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


Thanks for all the help btw... this is my first try at Linux and I'm really wanting to get away from Windows eventually. So it is much appreciated.

*Edit: i spaced the () out around the 8's because it was making them 8)'s

---

### Post by Pumalite on 2008-05-24
Looks like you have a mix of IDE and SATA. Change the boot order in BIOS (for hard drives) and see if you can boot Ubuntu that way.

---

### Post by Suckapuncha on 2008-05-24
I changed the boot order to boot from the SATA drive which has both OS's, but it just boots directly into Win XP and I don't get any menu that asks which OS I want.

Also, I had Ubuntu installed on my Primary Master IDE Drive, and it was working fine, I just couldn't boot into Win XP without restarting and going into the BIOS and selecting to boot from the SATA drive, which was really annoying. That's why I tried to install Ubuntu on the same SATA drive that Win XP is on. Now though, if I restart and change the BIOS to boot to the IDE Primary Master, the grub starts, but now I get Error 22, so I can't boot into it on the separate drive anymore.

---

### Post by Pumalite on 2008-05-24
Change the boot order to what it was and try reinstalling Grub to the master MBR:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Suckapuncha on 2008-05-24
yeah that didnt work either...

well i guess ill delete the partitions and just keep Win XP and Ubuntu on separate drives for now and switch the boot drive in BIOS when I want to change OS... :/

i reinstalled Ubuntu back onto the 160GB drive and it is working fine. Oh well. Thanks for the help though.

---

### Post by jeffus_il on 2008-05-24
Download supergrubdisk, burn it and boot from it. it should fix your problem.

---

### Post by Pumalite on 2008-05-24
> **Suckapuncha said:**
> yeah that didnt work either...

well i guess ill delete the partitions and just keep Win XP and Ubuntu on separate drives for now and switch the boot drive in BIOS when I want to change OS... :/

i reinstalled Ubuntu back onto the 160GB drive and it is working fine. Oh well. Thanks for the help though.

Glad you got it working. Good luck.

---

### Post by Suckapuncha on 2008-05-24
um, i deleted the linux partitions from my SATA drive, but Win XP still says the drive is only 300GB...

how do i get those 200GB back and make sure all the linux stuff is removed. It wont let me delete the Partition "Extended" from Terminal also.

---

### Post by Pumalite on 2008-05-24
Use Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by Suckapuncha on 2008-05-24
Man, I'm bad at this already lol.

Thanks for all the help.

---

