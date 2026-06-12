---
title: "Editing Grub, Removing Secondary Install..."
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by robelliott2125 on 2008-04-29
Hi all,

Over the weekend i had some issues with my Gutsy, so I decided to reinstall, which messed up my grub (I think it was down to using an external dvdrw to install from the disk.

Now, because each time I booted, it kept saying a grub issue, I decided to install an IDE cdrw drive to retry, but before reinstalling, I completely wiped my old XP partition and decided to install there, leaving two installs of Ubuntu on the system.

Now my problem is this...

As i'm a n00b, I don't want to mess up my grub, but I also want to remove the secondary install.

Can someone possibly help me with this?

If you let me know what you need, and how to do it, I'll happily provide the info.

Thank you,

---

### Post by robelliott2125 on 2008-04-29
Also, sorry about asking two seperate questions, but when I installed over the XP partition, as it was such a small partition, i didn't know how to create the swap partition...

Since I'm moving data about, and formatting NTFS to EXT3, can I move the Ubuntu partition slightly, to create a swap partition?  Or doesn't it matter too much?  Is it necessary?  *Also goes in search of info on the swap drive does...

Sorry, just wanting to learn as much as I can.

---

### Post by Moop on 2008-04-29
You should be able to delete your old install without it affecting grub because the newest install is the one controlling grub. You can boot from a live cd and use the partition editor to delete the partition that has your old install. You can either keep the old swap partition which your new install is probably already using or create a new one from the free space. 

To delete the old boot options from grub you just need to edit the boot menu
```
gksudo gedit /boot/grub/menu.lst
```and delete the entries for your old install. Save and close.

---

### Post by robelliott2125 on 2008-04-29
> **Moop said:**
> You should be able to delete your old install without it affecting grub because the newest install is the one controlling grub. You can boot from a live cd and use the partition editor to delete the partition that has your old install. You can either keep the old swap partition which your new install is probably already using or create a new one from the free space. 

To delete the old boot options from grub you just need to edit the boot menu
```
gksudo gedit /boot/grub/menu.lst
```and delete the entries for your old install. Save and close.

What would I be deleting though?

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
# kopt=root=UUID=9b1f4f01-e98a-4c15-858d-56898709b6fa ro

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
## e.g. defoptions=vga=795 resume=/dev/hda5
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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9b1f4f01-e98a-4c15-858d-56898709b6fa ro quiet splash 'vga=795'
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9b1f4f01-e98a-4c15-858d-56898709b6fa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=556a9210-925d-49a8-8b68-2852a2101636 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=556a9210-925d-49a8-8b68-2852a2101636 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, memtest86+ (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

Would it be under this header?

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=556a9210-925d-49a8-8b68-2852a2101636 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=556a9210-925d-49a8-8b68-2852a2101636 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, memtest86+ (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

Just want to be correct, especially with the main boot files...

I've used partition magic to remove the partition of the secondary installation, extended the partition so I could start moving data about and formatting into EXT3 FS, but starting to have probs with that too now...

Thank you, and looking forward to your reply.

---

### Post by JMorg on 2008-04-30
> **robelliott2125 said:**
> What would I be deleting though?

Would it be under this header?

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=556a9210-925d-49a8-8b68-2852a2101636 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=556a9210-925d-49a8-8b68-2852a2101636 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 7.10, memtest86+ (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

Just want to be correct, especially with the main boot files...

I've used partition magic to remove the partition of the secondary installation, extended the partition so I could start moving data about and formatting into EXT3 FS, but starting to have probs with that too now...

Thank you, and looking forward to your reply.


Yes by editing the text in that field it should correct your issue, but just to be safe I would wait for a second reply to back my opinion. To my knowledge the menu.lst works exactly like the boot.ini within windows as far as dealing with the initial post-bios startup selections. ( IE: If for some reason a user has 2 Windows XP selections at startup, editing the boot.ini file in windows and cleaning out one of the lines will correct the issue. )

---

### Post by robelliott2125 on 2008-04-30
> **JMorg said:**
> Yes by editing the text in that field it should correct your issue, but just to be safe I would wait for a second reply to back my opinion. To my knowledge the menu.lst works exactly like the boot.ini within windows as far as dealing with the initial post-bios startup selections. ( IE: If for some reason a user has 2 Windows XP selections at startup, editing the boot.ini file in windows and cleaning out one of the lines will correct the issue. )

Hi there JMorg,

Thank you for your reply.

You've just backed up someone's reply via PM.
I was given this link:
[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

Which I've just done, and i'm hoping thats it sorted now.
Just wanting to know if i'm going to be asked to select which kernal to load each time it gets to the grub, or does it boot similar to what Winbloze does, where when I need Safe / Recovery mode, i press something to load, else it continues to load into the full version?

Thank you,

---

