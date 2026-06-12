---
title: "Dual Boot Conundrum - another crack at it"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-12-05
Hi,

I've been running Linux steady for over a year now (currently Edgy). However I've still got XP on the same machine, but I haven't been able to get it to dual boot properly since I upgraded from Breezy to Dapper months ago. I still have a couple of things I need XP for and the situation occasionally rears its ugly head. Here, as briefly as I can state it, is my situation:

I have two 160GB physical hard drives on the machine laid out as follows:

```
hdb:

/dev/hdb1  ntfs  /media/hdb1  (My Windows C Drive 108GB)
/dev/hdb2  ext3  /home        (My Linux Home partition 42GB) 


sda:

/dev/sda1  ntfs  /media/sda1  (Another Windows Data Partition 120GB)
/dev/sda2  ext3  /            (linux root partition 18GB)
/dev/sda3  extended - which contains
/dev/sda5  linux-swap         (swap partition 2GB)
/dev/sda6  fat32 /osshare     (a partition to txfer between XP and Linux)

```

As a bit of necessary background, I used to have the dual boot working fine back in Breezy. But I had to use the Windows multiboot to do it. I would hit that bootloader, choose Linux which would then launch GRUB, which would then finally launch Linux. A workaround for sure, but fine with me. It was the only way I could do it (something about having the Windows C Drive on a SATA drive or something). I went through that business about generating a LINUX.LNX file placed on my C Drive and modifying the boot.ini file there. All that stuff was regenerated when I upgraded to Dapper (but didn't work) and is still in place on the C-Drive.

Currently, the machine boots up, goes to GRUB and upon choosing the default Linux kernel, boots into Ubuntu Linux no problem.

If however, I choose the Windows XP Home option, the machine gives a 'NTLOADER missing' message.

Upon rebooting again it brings me to the Multiboot manager for windows (and never even gets to GRUB) which shows only two choices (XP home or Linux). Choosing XP Home gives an 'Autochk error' message and stalls, and choosing Linux just goes to a black screen with flashing cursor.

This forces me into a situation where I have to do the following:

1. Reboot with my System Rescue CD
2. Run QTParted from the Rescue CD
3. Modify the sda drive so that the root partition is active and the ntfs partition is HIDDEN. It's no good just to make the /root partition active, if I don't hide the Windows partition I can't boot to linux at all.

So after doing this, I reboot again (without the CD of course) and it goes to GRUB and I can run Linux fine again.

This has forced me to forego running XP at all (knowing that if I do, I have to go through the previous steps with the Rescue CD). And while many here would rejoice at that fact (me as well most of the time), there are still a couple of things I need in XP. One is work-related (AutoCAD) and the other is a slideshow program. (BTW If anybody can recommend an app for linux that has the capabilities and simplicity of MS-Photostory - basically the Ken Burns effect and music soundtrack - I'd be eager to hear about it. I've tried DVD-Slideshow with SLCreator but it's so awkward and seems dead slow to render mpegs :( )

Apologies for the long-winded description, but I've tried to be as complete as possible.

Here is my current menu.lst file. Sorry for the huge amount of kernel choices, the upgrade to Edgy seemed to add so many and I haven't pruned it yet:

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro splash vga=795
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro splash vga=795
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro splash vga=795
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro splash vga=795
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro splash vga=795
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro splash vga=795
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro splash vga=795
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
makeactive
chainloader	+1
map		(hd0) (hd1)
map		(hd1) (hd0)

```

Suffice it to say, I love running Linux. I hate booting into XP, but I still need that capability (without resorting to manually modifying active and hidden hard drive flags each time). If anybody has an ideas that might help, I'd greatly appreciate it.

PS - Would the behaviour be any different if I used some other 3rd party bootloader instead of GRUB?

---

### Post by bulldog on 2006-12-05
Grub should do fine.
Just tell me from which hard disk you boot and where GRUB is.

If I'm guessing right,you boot from the sda disk because ubuntu starts fine.
If so you have to make the windows boot entry like (HD1,0) because ubuntu is on disk 0 [and grub] so windows is on disk 1.

---

### Post by richardq on 2006-12-05
> **bulldog said:**
> Grub should do fine.
Just tell me from which hard disk you boot and where GRUB is.

I boot from the sda drive and GRUB is in the / partition on that drive.

---

### Post by bulldog on 2006-12-05
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1  <--------
title		Microsoft Windows XP Home Edition
rootnoverify    (hd1,0) <--------
map		(hd0) (hd1)
map		(hd1) (hd0)
makeactive
chainloader	+1
```
Change your menu.lst according this and try again.

---

### Post by richardq on 2006-12-05
Thanks for the help. I will try this tonight when I get home and report back then.

---

### Post by bulldog on 2006-12-05
No problem,I should read about it tomorrow,because I live in the Netherlands.
So if I not reply it's because I sleep or being at work :D 

Good Luck anyway.

---

### Post by richardq on 2006-12-05
I made the change you suggested. When I chose the 'XP-Home' option in GRUB it gave me an "NTLDR Missing" message and stopped (which is what it did before). But it is a step in the right direction because when I rebooted the machine it brought me back to GRUB again and let me boot into Linux no problem. (instead of putting me into the windows multiboot problem like before).

I see in GParted that the ntfs partition (the one with the Windows C Drive) is flagged as 'hidden'. The only way I can seem to get XP to boot is to make this partition 'UN-hidden' - with the RescueCD. Is there a way to do that from within the menu.lst file?

I don't think making it 'active' is the same as 'unhiding' it.

---

### Post by bulldog on 2006-12-06
Well the hide and un-hide options is something I'm not familiar with.
So can't help you with that one,can tell you that the make active option is the boot flag so your partition is bootable.

Think you have to un-hide all the hidden partitions,because it should work normally without hiding any partition.
This option is as far as I know,not an option inside GRUB,you have to use the program where you hide them with.

Try this if you can and let me know how it goes.

---

