---
title: "Dual Boot &quot;starting up...&quot; message"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Shininggg on 2008-06-06
[B][COLOR="Red"]I had windows installed on my desktop, i decided to install ubuntu HArdy 8,04 in a dual boot config. 

I ran Defragmentation tool a couple of time and resize the partition to make place for the new OS using gparted form the live cd.

Now when i turn the pc on i see Ubuntu and windows xp pro. Ubuntu is fine but when i choose windows xp i get a black screen with "Starting up..." 
[/COLOR][/B]
Disque /dev/sda: 200.0 Go, 200049647616 octets
255 heads, 63 sectors/track, 24321 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xd148d148

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        6421    51576651    7  HPFS/NTFS
/dev/sda2            6422       12158    46082452+  83  Linux
/dev/sda3           12159       12413     2048287+  82  Linux swap / Solaris
/dev/sda4           12414       24321    95651010    b  W95 FAT32

Disque /dev/sdb: 500.1 Go, 500107862016 octets
240 heads, 63 sectors/track, 64601 cylinders
Units = cylindres of 15120 * 512 = 7741440 bytes
Identifiant disque: 0xbd2c5c34

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1       64601   488383528+   7  HPFS/NTFS

Disque /dev/sdc: 495 Mo, 495452160 octets
16 heads, 63 sectors/track, 960 cylinders
Units = cylindres of 1008 * 512 = 516096 bytes
Identifiant disque: 0x0ccb0cca

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1               1         960      483719+   6  FAT16

 [B][COLOR="Red"]Please note that i have 2 hard drive (sata) one 200 go where both OS are  installed and one 500go that i only use for media library

When i am in Ubuntu i can browse through the partition used for the Windows installation and access any file i want. NTDETECT, NTLDR and BOOT.INI are all at the root of the windows partition. 
[/COLOR][/B]
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
# kopt=root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b16e2e86-2e24-42c3-a04a-b13284ecbb71 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professionnel
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1


[B][COLOR="Red"]anybody has a hint of what went wrong here?

Any help appreciated[/COLOR][/B]

---

### Post by Pumalite on 2008-06-06
See if you can boot XP with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by Shininggg on 2008-06-06
ok i gave SGD a try but no go. Not sure i used the thing correctly though...

i tried the !WIN! option but wouldn't boot

---

### Post by Pumalite on 2008-06-06
Your Windows might be corrupted. I'm not a Windows use, but I think there is a way to repair the XP file system with the Installation CD.

---

### Post by Herman on 2008-06-06
:) Have you unplugged your sata hard drive cables recently? (Such as possibly when you added a new hard drive or if you had to unplug the cables for room to maneuver some other hardware item into place inside your computer case).
If you can remember doing that, are you sure you plugged the cables back into the same ports on the motherboard.

The reason why I am asking this is because the last person to report this error when trying to boot Windows solved it by replugging the sata drive cable of the Windows hard drive back into the motherboard ports where it was originally.
Here is a link, [Starting up...]("http://users.bigpond.net.au/hermanzone/p15.htm#Starting_up...")

Rather than opening your computer case if this might be the problem, I'm not sure, but possibly this can be solved by checking that your hard disks are properly detected and set up in your BIOS.

Regards, Herman :)

---

### Post by Shininggg on 2008-06-06
Yeah i read about that, and yes i unplugged my Sata cable recently but i don't think this is the problem here. In Fact i didn't unplug any cable i just plugged in the new hard drive, which was well detected, formated and recognized.It was and still is used as a media library and contain only video and music which i can still access with Ubuntu.

The window partition is in fact on the other HDD(200go) as well as the linux OS.

I read this post before posting here but i think it is pure coincidence in my opinion.

!!SPECIAL UPDATE!!

Well, i backed up everything i had in my windows partition (SDA1) and decided to reformat the whole thing to see if windows was corrupted. Turns out while installing after the first reboot, weird colored character (such as @#&) appeared in a black screen and now i can't even reinstall windows in the partition...

---

### Post by Shininggg on 2008-06-07
Ubuntu works like a charm, but is it normal that i can't reinstall window in the same partition it was before? 

i formatted then tried to reinstall using xp boot cd but after the first reboot after all the installation file have been copied to the partition i get Disk error CTRL-ALT-DEL to restart?

seriously any help appreciated here 

thanks

---

### Post by Herman on 2008-06-07
I was trying to remember when that happened to me, but it was a while ago and my memory doesn't seem to be serving me as well as I would like. Maybe try deleting the file system in that partition so that you have just an empty partition, and let your Windows disk format it, I think that's how to get past that error, but I was hoping someone else might have posted by now.

---

### Post by Herman on 2008-06-07
If that doesn't work, maybe Windows is being greedy as usual and refuses to install unless it can claim the entire hard disk for itself. If your Ubuntu install is new and you haven't put very much work into customizing and personalizing it already, you might try deleting Ubuntu and re-installing it after you get Windows installed.
You can make a backup of your entire Ubuntu OS with partimage if think that will be faster than re-installing and if you have spent some time customizing and personalizing Ubuntu. Aysiu has the best web page about how to use partimage, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage").

Is that the exact error? I have seen that somewhere, but I still can't remember where or how to get past it for sure. 
If you can supply the exact error then maybe something I can find with google will refresh my memory enough to be more helpful.

---

### Post by Shininggg on 2008-06-08
Sorry for the delay here. 

Turns out you were right i wiped everything clean and did a clean install and now it works like a charm. Good thing i had everything backed up. 

I think the mess started with the resize option in the first place. Resizing the partition must have corrupted the window installation like pumalite said. 


Thanks to all for your great help

---

