---
title: "[SOLVED] Cannot get Ibex to boot"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by gringopig on 2008-11-12
Hi all...

This describes my problem.

My system is:
Dual partition SATA drive with XP and Vista, active partition XP with Vista bootmgr on XP partition. This drive is the first BIOS sees and boots.
I have a Highpoint RAID card with 2 RAID0 drives and a SATA 'legacy' drive connected to it. This controller has been flashed with firmware to allow it to boot (Reallocate EDBA and init13 enabled).

I have installed Ibex to the latter drive, which was seen happily by the Live CD installer and chose to partition as (in order) 100GB ext3, 5GB swap and the remainder NTFS). I also chose to install grub to the Ubuntu partition and preserve the Windows MBR on the first drive (controlled by SATA mobo).
So, installation complete, I looked to linking the Vista bootmangler to grub on the bootsector of this other drive: firstly with EasyBCD and then by manually editing the BCD.

Could I get it to boot?? No chance.
With EasyBCD, I was left floating at a grub prompt on the first drive (EasyBCD uses a second instance of grub or neogrub, to chainload to the Ubuntu partition), with BCD editing I was left hanging also, with 'GRUB' top left of screen with a flashing cursor.
I have manually re-installed grub and am sure it is installed correctly on /dev/sdc1 (the installation partition) which is (hd2,0) in grub. The manual install completed successfully and I can see the relevant files and folders using the Live CD.

The menu.lst file has no root (hd2,0) entries but uses a UUID tag, identifying the drive. Perplexingly, this changes by one digit each time I re-install from scratch.

I'm about to give up on Ubuntu here, as I've NEVER had as much bother as this. Windows seems like a blessed relief in comparison!!!

Help me out folks - if Ubuntu (and Linux in general) seeks to rise above the 1% usage levels it HAS to work better than this.

Paul

---

### Post by linnuxnub on 2008-11-12
I agree with you that Windows(spit) is easier to use than linux in the begining but that's just beacause you are used to it, once you get into linux then you will never go back.

As for your booting problem I think you should try and set Grub as the main boot manager (you should be able to do this through your bios settings), Grub tends to be more neutral, by that I mean compared to a windows boot manager. Windows tends to be bias towards itself by only letting you boot into windows operating systems were as grub will let you boot into linux, windows, or anyother OS on your PC.

---

### Post by caljohnsmith on 2008-11-12
The reason you can't get the Vista boot loader to work by adding the Grub boot sector is because your Ubuntu installation is on a different HDD than Vista; you have to install Grub to the boot sector in a special way if you are going to move it to some other HDD and have that boot sector correctly point back to the Ubuntu drive. In other words, your Grub boot sector currently points to the Grub stage2 file on the same drive, so moving the Grub boot sector to another drive will cause it to hang when you boot it. 

How about first posting the full output of:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by gringopig on 2008-11-13
Thanks for the replies!!!
Fast response and a vibrant community here...

OK, the result of the fdisk:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4fe0905d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953230894   976615416    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16517a53

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc64f3c1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   195318269    97659103+  83  Linux
/dev/sdc2       195318270   205085789     4883760    5  Extended
/dev/sdc3       205086720  1953521663   874217472    7  HPFS/NTFS
/dev/sdc5       195318333   205085789     4883728+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   488375999   244187968+   7  HPFS/NTFS
/dev/sdd2       488376000   976751999   244188000    f  W95 Ext'd (LBA)
/dev/sdd5       488376063   976751999   244187968+   7  HPFS/NTFS


/dev/sda and /dev/sdb I believe to be my RAID0 drive controlled by a Highpoint RR2300 card.
/dev/sdc is the 1TB SATA drive I partitioned for use with Ubuntu. /dev/sdc1 is the ext3 Ubuntu partition and I chose to install grub there through the 'Advanced' option. I have a 5GB swap and the remainder is NTFS. The sdc1 partition is flagged as boot.
/dev/sdd is the Boot disk for BIOS and has XP on the active partition (with Vista's bootmanager). Vista is on the other half.

Here's the grub stage 1 result:

> grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,0)


and blkid:

> /dev/sdc1: UUID="cba60f34-687c-4eab-a92e-901b3b5aca7b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="30783792783755B6" LABEL="Icy Box" TYPE="ntfs" 
/dev/sdc5: UUID="905ac3ae-3ba2-4098-9410-3fa0426a7145" TYPE="swap" 
/dev/sdd1: UUID="044C77DB4C77C648" LABEL="XP" TYPE="ntfs" 
/dev/sdd5: UUID="C820A29720A28BCE" LABEL="Vista" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 


My menu.lst from the boot/grub folder:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=cba60f34-687c-4eab-a92e-901b3b5aca7b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cba60f34-687c-4eab-a92e-901b3b5aca7b

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cba60f34-687c-4eab-a92e-901b3b5aca7b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cba60f34-687c-4eab-a92e-901b3b5aca7b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cba60f34-687c-4eab-a92e-901b3b5aca7b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cba60f34-687c-4eab-a92e-901b3b5aca7b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cba60f34-687c-4eab-a92e-901b3b5aca7b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Windows Vista/Longhorn (loader)
root		(hd3,0)
savedefault
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


Device map:

> (hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

Thanks again and I'm looking forward to yr input on this! I want to get Ubuntu going as I've heard so much about it!!!

Paul

---

### Post by caljohnsmith on 2008-11-13
Since your Ubuntu sdc drive is not part of your RAID setup, can you change your BIOS to boot from it on start up instead of your Windows sdd drive? It would be really easy to add an entry for Vista/XP in your Grub menu, and then you could boot all your OSes from one menu; if you use Vista's boot loader, you will have to go through two boot menus to boot Ubuntu. If you can boot from the Ubuntu sdc drive and would like to go that route, just do:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
And you should be able to boot your Ubuntu drive just fine. Once you can confirm that's working, I can give you the Grub entries to boot Vista/XP in case the one in your current menu.lst doesn't work (it may or may not depending on where the Vista/XP drive is in your boot order when you boot the Ubuntu drive). 

Or if you are really set on booting Ubuntu from Vista's boot loader, let me know, and I can give directions for doing that too; please let me know though which drive sdc is in the BIOS boot order if you can.

---

### Post by gringopig on 2008-11-13
Hi again!

I'm not going to use grub to boot. It's ugly and makes me wince with aesthetic displeasure! LOL!!

I'm going to get grub working with The Vista bootmanager if I can.
Windows is my main OS and it will take a holographic 3D desktop and ACTUAL dancing girls stroking my fevered brow to change it...

So, I've actually tried changing the boot order of the drive, or actually the whole array - since the card is seen as a device. There are 3 drives attached to it and only one is set active.
The error is a confusing "cannot find bootmgr". Eh???
No boot. I have the drive set after the SATA drive my 2 Windows OSs are at.
If you can help me to add the grub entry manually through bcdedit, I would be grateful.
It failed everytime I did it but I could have messed it up.

If this doesn't work, then I have to assume grub is not being installed properly due to the hardware configuration and give up or reformat & re-partition my current boot drive in 3 and Ghost the images back on, restore MBR and repair Vista's non boot with the install disk - then use EasyBCD to re-add XP and try Ubuntu again!

Can you see anything amiss with the current config from the Linux side?

Cheers, Paul

---

### Post by caljohnsmith on 2008-11-13
OK, since I don't know which drive Ubuntu is in your BIOS boot order, there are three possibilities (or only two if your RAID array is seen as one drive by your BIOS), so you will have to try each one to see which works:
```
sudo grub
grub> device (hd1) /dev/sdc
grub> device (hd0) /dev/sdc
grub> root (hd1,0)
grub> setup (hd0,0)
grub> quit
```
And then use EasyBCD to copy the boot sector of sdc1. If that doesn't work to boot Ubuntu, next try:
```
sudo grub
grub> device (hd2) /dev/sdc
grub> device (hd0) /dev/sdc
grub> root (hd2,0)
grub> setup (hd0,0)
grub> quit
```
I think most likely one of the above attempts should work, but if not, the last possibility would be:
```
sudo grub
grub> device (hd3) /dev/sdc
grub> device (hd0) /dev/sdc
grub> root (hd3,0)
grub> setup (hd0,0)
grub> quit
```
Let me know how it goes, or if you run into problems, be sure to give a detailed description. :)

---

### Post by gringopig on 2008-11-13
Hey caljohnsmith!!  :)

I'm replying in Ubuntu! YAAAYYYY!!!!

The problem was simple to overcome. I used EasyBCD to Add an Entry for Ubuntu but did not use the Neogrub option which didn't work despite all I tried.
The solution was to use the grub option, seklecting the ext3 partition but NOT to tick the box labelled 'GRUB isn't installed to the bootsector'.

Sounds perverse eh?

I think the EasyBCD folks should update the documentation on this for those who want to boot off a second hard drive.

Anyway - I hope to learn more about Linux through this exercise and my recent problems have given me a head start...:biggrin::biggrin::biggrin:

Thanks once again!

Paul

---

### Post by caljohnsmith on 2008-11-13
Glad to hear you have it working. Cheers and have fun with your new Ubuntu install. :)

---

