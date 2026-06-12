---
title: "Windows won't boot after Ubuntu 8.04.1 install"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by del025 on 2008-07-19
Hi All.

I'm new to Linux and running into a boot problem

After installing Ubuntu Ubuntu boots fine and Windows XP Home appears in the boot loader.  If you select Windows XP Home however you receive a Disk Read error and are advised to press Ctl, Alt, Del, to reboot computer.  Don't want to loose my XP install - is there any way to get XP to boot again?

Thanks for any suggestions

del025

---

### Post by Pumalite on 2008-07-19
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by del025 on 2008-07-19
Received the following after running from terminal: ??

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

paul@paul-ubuntu:~$ sudo fdisk -lu
[sudo] password for paul: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27262726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   104663474    52331706    7  HPFS/NTFS
/dev/sda2       104663475   156296384    25816455    5  Extended
/dev/sda5       104663538   154063349    24699906   83  Linux
/dev/sda6       154063413   156296384     1116486   82  Linux swap / Solaris
paul@paul-ubuntu:~$ cat/boot/grub/menu.lst
bash: cat/boot/grub/menu.lst: No such file or directory
paul@paul-ubuntu:~$

---

### Post by del025 on 2008-07-19
Whoops!

Sorry recognized my mistake after sending - entered command on same line and terminal excepted it.  Rebooted system but still showed same error "disk read error" and forces a reboot (CTL, ALT, DeL) 

Any help is greatly appreciated..

Sorry I am new to Linux and trying to learn.

Del025

---

### Post by Pumalite on 2008-07-19
You have respect the spaces. Copy and paste the command in the Terminal. I need menu.lst to help you.

---

### Post by del025 on 2008-07-19
Thanks for your patience:  I think this is the listing your looking for.

paul@paul-ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27262726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   104663474    52331706    7  HPFS/NTFS
/dev/sda2       104663475   156296384    25816455    5  Extended
/dev/sda5       104663538   154063349    24699906   83  Linux
/dev/sda6       154063413   156296384     1116486   82  Linux swap / Solaris
paul@paul-ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=e246332b-0cba-4437-9a26-dc02c8348ea3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e246332b-0cba-4437-9a26-dc02c8348ea3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e246332b-0cba-4437-9a26-dc02c8348ea3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

paul@paul-ubuntu:~$

---

### Post by Pumalite on 2008-07-19
Get Super Grub and see if you can boot your Windows:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by del025 on 2008-07-19
ok will try!  Again Thank you!

---

### Post by del025 on 2008-07-20
Burned the supergrub iso to a cd and rebooted from the cd.  Super Grub came up but same error message occurred while attempting to load windows. 

I appreciate your thoughts & help

Del025

---

### Post by Pumalite on 2008-07-20
You are welocome. Sorry, but it seems your Windows is corrupted if you are using Super Grub well. When you install Ubuntu, having Vista; you have to allocate space for Ubuntu with the Vista partitioner first. You cannot partition with the Ubuntu CD.

---

### Post by karatekid on 2008-07-20
i too am encountering a similar problem.
[http://ubuntuforums.org/showthread.php?t=860914]("http://ubuntuforums.org/showthread.php?t=860914")
though i do get the same error message when i try to boot from my windows partition however  i  was able to get  a workaround for   getting my old windows installation.
{mentioned in post no 9 of the above thread}

---

### Post by del025 on 2008-07-21
Thanks for replies:

I managed to again boot to Windows XP from the following:

Booting to a GParted Live CD & running Test Disk.  On examining the windows partition it was not listed as the default or bootable.  I altered the partition to both the default and making it bootable.  On restarting the system I received the Grub Error 22 (as expected) but now when I Place the Super Grub CD in and reboot I am able to access Win XP just fine. 

My plan is to now image my Win XP (which I should have done before installing Ubuntu) and then try removing just the default setting from the Windows Partition and see if I can get Grub to boot and load windows.  If not I will try installing another Boot manager such as GAG or the one referred by Karate Kid (thank you!) in the previous post.   

I will advise how it all turns out but if anyone else has some other suggestions I would love to hear them.  I am not used to working with Partitions and the Master boot record so I don't have a solid foundation there, any suggestions are greatly appreciated!

---

### Post by karatekid on 2008-07-21
this page might help
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by del025 on 2008-07-21
Karate Kid:

I checked out the link and yes it looks like it may help with my problem.  Will be working on it later tonight.  - Thank you for your time.

Del025

---

