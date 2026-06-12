---
title: "Upgrade to 23.1 kernel breaks boot?"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by dennis_k85 on 2007-12-20
I recently did the upgrade to the 23.1 kernel and it caused my system not to boot. In Grub it could not find the root file system. So I modified /boot/grub/menu.lst to point5 to the previous kernel and everything worked fine. I am running on an older Toshiba laptop on an IDE hard drive. 

Is there anything I can do to make the 23.1 kernel work on this machine? Will I have problems with future kernels?

---

### Post by cyberdork33 on 2007-12-20
can you post your menu.lst?

---

### Post by igknighted on 2007-12-20
Sounds like you didn't compile in support for the filesystem on your / partition, or perhaps included them as modules and not directly built in.  Another possibility is that you left out support for your disk controllers.  I would try again and make sure you have enabled everything that could relate to your hardware/system.  I do not think it is an issue with the kernel itself (although if you try multiple configurations without success, you could try submitting a bug).

---

### Post by dennis_k85 on 2007-12-20
I did not build this kernel myself. It came as one of the Ubuntu updates that I applied yesterday. Sorry about the misunderstanding.

---

### Post by dennis_k85 on 2007-12-20
Here is my menu.lst 

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
default		4

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
# kopt=root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro

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

title		Ubuntu 7.10, kernel 2.6.23.1 Default
root		(hd0,0)
kernel		/boot/vmlinuz root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
quiet

title		Ubuntu 7.10, kernel 2.6.23.1 Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single

title		Ubuntu 7.10, kernel 2.6.23.1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.23.1 root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
quiet

title		Ubuntu 7.10, kernel 2.6.23.1 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.23.1 root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, kernel 2.6.20-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu 7.10, kernel 2.6.20-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-13-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-13-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-13-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single
initrd		/boot/initrd.img-2.6.20-13-generic

title		Ubuntu 7.10, kernel 2.6.20-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=8db7100f-0b49-418c-95d8-b67912a030a9 ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by igknighted on 2007-12-20
Are you on hardy?  Gutsy should not have upgraded like that...  If it is Hardy, file a bug report with Ubuntu.  Remember, Hardy is in early alpha stages, breakages will happen.

I might try eliminating the UUIDs from grub and using the appropriate block devices.  Shouldn't cause an issue, but I'm always suspicious of the things, so it could be worth a shot.

---

### Post by dennis_k85 on 2007-12-20
I am on Gutsy.

---

### Post by igknighted on 2007-12-20
> **dennis_k85 said:**
> I am on Gutsy.

What repo did that update come from?  I don't see a 2.6.23.1 kernel in the gutsy repo's or gutsy-backports... if it came from a third party repo that is likely your problem.  Try posting your /etc/apt/sources.list file so we can see what repo's you are pulling from.

---

### Post by dennis_k85 on 2007-12-20
Here is sources.lst

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by igknighted on 2007-12-20
Hmm, you seem to have a few feisty repo's still, but I don't think that's the issue.

I am betting that the kernel came from gutsy-proposed (I can't check that repo at packages.ubuntu.com and I can't search it with apt cause I'm stuck on windows at work).  I would be careful with anything in gutsy-proposed, as to my knowledge that is a repo of beta-quality packages for testers.  I cannot confirm this, however.  Does anyone else have the 2.6.23.1 update and if so, do you know where it came from?

ps, for future reference, when posting a long file like menu.lst or sources.list, try putting them in code tags (the # button in the thread toolbar, or [code] [ /code] tags).  It just keeps threads tidier and easier to read through.

---

### Post by cyberdork33 on 2007-12-20
2.6.23 is not available in the Ubuntu repos that I know of.

---

### Post by svivian on 2007-12-20
I think I may have a similar problem. I followed the tutorial at [https://help.ubuntu.com/community/QtGnome](https://help.ubuntu.com/community/QtGnome) and added the "hoary" repo to the sources file:
```
deb http://www.informatik.tu-cottbus.de/~mkrause/debian sarge main
```

A bunch of updates came through not long after this, which I installed. After restarting, my boot list had gone back to the default ubuntu one without my Windows partition listed (luckily I had a backup). And now the display is fuzzy in places and there are artefacts all voer the shop.

*How do I revert the updates I made?!*

---

### Post by svivian on 2007-12-20
bump

anyone?

---

### Post by svivian on 2007-12-21
bump

---

### Post by svivian on 2007-12-21
Oh my bad, it was the bootloader. Overwriting menu.lst with an older version is not a good idea! All systems returning to normal. Meltdown averted.

---

