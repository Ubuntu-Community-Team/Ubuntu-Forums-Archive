---
title: "PC Jammed after installation with GRUB GRUB GRUB screen"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by marcopolo73 on 2007-09-24
I have bought a new (branded) computer and when I have installed Ubuntu 7.04 the PC starts up and looks jammed with a screen full of "GRUB GRUB GRUB..." writings.

When I start the PC with the Ubuntu CD there are no problem, but I tried to install again and again and always the same result.

Moreover I have noticed that after installation, if I restart the computer all partitions are lost. So the PC ask me to do the partitions again.

I tried to install Ubuntu and then check Grub before restarting and just noticed that after fdisk -l command there is no asterisk in the boot column, although I setted a dedicated /boot partition. The grub command find /boot/grub/stage1 replies with something like "file not found".

At last I am no longer able to access the BIOS of the machine...

Has anybody an idea about what happened? Any suggestion about how come out to this situation and be able to use Ubuntu from HD finally? Do you think that installing Windows XP would help me?

In fact previously there was a Windows XP installation made by the shopkeeper. But as I want just an Ubuntu machine, I cancelled it... Are all these problems with Ubuntu a Windows revenge??? ;-)

Thank you  very much for the help!

Marcopolo

---

### Post by Pumalite on 2007-09-24
Sounds like a Micro$%& conspiracy. Is this a laptop? Post specs.

---

### Post by marcopolo73 on 2007-09-25
It is a desktop, not a laptop. It has a Pentium D processor, 512 MB memory, 160 GB HD.

If you need more info, let me know!

Ciao!

Marcopolo

---

### Post by Pumalite on 2007-09-25
DBan the Drive: [http://dban.sourceforge.net/;](http://dban.sourceforge.net/;) after that use Gparted:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Make one large partition out of your whole drive, format ext3, then install>Guided>Use Entire Disk

---

### Post by marcopolo73 on 2007-09-26
Dear Pumalite,

Thank you very much for your suggestion!!!!!

After using DBan and GParted I am able again to access the BIOS and I have no longer experienced the "GRUB GRUB GRUB ..." writings on the screen. And this makes me feel better!!! ;-)

By the way I am still not able to use Ubuntu... The system says: 

GRUB loading stage 1.5

GRUB loading, please wait. .... 

So it looks like the system is once again jammed. Have you other suggestions (or has anybody reading this Thread)?

Thank you!

Marcopolo

---

### Post by logos34 on 2007-09-26
> **marcopolo73 said:**
> I setted a dedicated /boot partition. The grub command find /boot/grub/stage1 replies with something like "file not found".

If it's a separate /boot partition, then you should have entered 

find /grub/stage1

> GRUB loading stage 1.5

GRUB loading, please wait. ....

So it looks like the system is once again jammed. Have you other suggestions (or has anybody reading this Thread)?

When you reinstalled did you create a dedicated /boot again?  Boot the live cd, mount root or /boot and check that the paths in menu.lst are correct. (feel free to post it).  If you need to add a boot flag use Gparted (right-click on root or /boot>manage flags>check 'boot' box)

Check the hard disk detect settings in the Bios.  Should be set for 'auto'.  If you have raid, make sure it's disabled.  

Try [reinstalling grub]("http://ubuntuforums.org/showthread.php?t=224351").

Did you check the [md5sum]("https://help.ubuntu.com/community/BurningIsoHowto") of the downloaded .iso?  Cd integrity check?  I'm just thinking maybe a tiny error crept in somewhere.

---

### Post by marcopolo73 on 2007-09-27
I tried to do what you said, but no results.

This is my menu.lst file:

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
# kopt=root=UUID=3008a461-12b5-4862-96c3-c63c2fbb71c5 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3008a461-12b5-4862-96c3-c63c2fbb71c5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3008a461-12b5-4862-96c3-c63c2fbb71c5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

I just could start the system with Ubuntu using Super Grub and doing Grub step by step, but still not working in a normal way... What do you think that could be???

Thank you! ;-)

Ciao,

Marcopolo

---

### Post by logos34 on 2007-09-27
Is /boot on a separate partition?

Post you fdisk if you could.

---

### Post by marcopolo73 on 2007-09-28
No, I made a big partition /. Then there is of course a /swap partition. Mainly I followed the former Pumalite suggestions. By the way I noticed in the manual installation that the mounting point was /dev/hda. So I changed in /.

Thank you!

Ciao,

Marcopolo

---

### Post by Pumalite on 2007-09-28
Post:

sudo fdisk -lu

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

---

