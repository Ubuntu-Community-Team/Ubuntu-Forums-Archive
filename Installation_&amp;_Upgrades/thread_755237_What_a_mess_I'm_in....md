---
title: "What a mess I'm in..."
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by brodae on 2008-04-14
Well, here I go.

I tried to install Ubuntu 7.10 on my external hard drive. I've looked around and found that installing an operating system on an external hard drive should be able to work. However, I also learned that my BIOS (Also GRUB?) needs to be able to recognize USB and/or FireWire 400 devices when searching for OS's.

Well, I tried. A few different times, and a few different ways. At first I was using FireWire, but then I switched my drive to a USB connection. It's a WD 320 GB My Book. It has eSATA capabilities but my motherboard doesn't have eSATA ports. The most recent install was as follows: I made three partitions. The "/" partition, the "/home" partition, and the swap partition. 8 GBs for the "/" partition, 20 GBs for the "/home" partition, and 4GBs for the swap partition. Before I switched to USB, I had a different error, but after the switch I now get the infamous Error 21 "Unknown Reason" with GRUB. I think my BIOS doesn't recognize FireWire, but it might not recognize USB either. In the meantime, I can only boot with the Live CD. :(

So, how can I solve the problem? My preference is to have Ubuntu and XP Professional coexisting happily, but if they can't resolve their differences I'll just stick with XP. However, that means Mr. GRUB will need to be "retired." (Pardon the Blade Runner reference.)

The specs that I'm familiar with are as follows:

XP Professional
2 GB DDR 3200
PCIe nVidia 7300 GS
Sound Blaster 24 bit 5.1
Pentium 4 3.0 Ghz w/ Hyperthreading

I don't know what kind of motherboard I have, which really is frustrating.

Help me Obi Wan Kenobi, you're my only hope.

---

### Post by Pumalite on 2008-04-14
You can restore XP's MBR with Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Next time you install to external drive, at step 8 press 'Advanced Tab' and change (hd0) to /dev/xxx
xxx is whatever corresponds to your USB.

---

### Post by brodae on 2008-04-14
Thanks. I'll give it a shot and post back the results.

---

### Post by brodae on 2008-04-14
One more thing, do I need to specify the partition?

Like "/sdf2"?

---

### Post by Pumalite on 2008-04-14
Generally /dev/hdb or something like that.
You can find out running:
sudo fdisk -lu at the Terminal while having the external plugged in.

---

### Post by brodae on 2008-04-14
I'm sorry, I'm new...

What I mean is:

Do I need to specify the exactly partition by adding a number to the end?

I know that my external drive is /dev/sdf/

It's just that I have sdf1, sdf2, sdf3, and sdf4.

Which one do I specify? Or, do I just type sdf?

Again, I'm sorry I'm new.

I've just ran into so many problems and I'm trying to get my computer working so I can continue my online schooling.

My lesson is: Don't try installing an OS on a priority machine. lol.

Though, I still want to...

---

### Post by Pumalite on 2008-04-14
No. Grub is supposed to get installed to the very beginning of your drive.
So, /dev/sdf is enough.

---

### Post by brodae on 2008-04-14
Ok. Thanks. :) I'll give it a try.

---

### Post by brodae on 2008-04-18
Well, my Windows isn't working anymore, and Linux can't even be found with Super GRUB... : (

I'm really confused. I can't even use system recovery. So, the only thing I can do, literally, is use this preview cd. It's nice, but I want my windows back. I'm ready to give up on Linux for good. It seemed nice and all, but it's just frustrating me.

So, I need a miracle. How can I fix Windows and/or Linux.

With windows, I get a system fatal error, and with Linux, it can't be found.

S.O.S.

---

### Post by Pumalite on 2008-04-19
Super Grub can fix your Windows MBR.

---

### Post by brodae on 2008-04-20
My MBR is fine, I my windows automatically goes to system recovery, and freezes with a system error. It automatically boots into Windows, but just the recovery where windows freezes. Super GRUB doesn't detect Linux either.

---

### Post by Pumalite on 2008-04-20
Can you boot a Live CD?

---

### Post by brodae on 2008-04-21
Yes, and that's the only thing I can do... I talked to a family member and he said his thought was to get an OEM of Windows and reinstall it that way since I don't have a recovery disc. I'm not for sure with that, but yes, I can run a Live CD, that's I'm doing as we speak... er... type.

---

### Post by Pumalite on 2008-04-21
With your external plugged. post:
sudo fdisk -l

---

### Post by brodae on 2008-04-21
Will that format the drive? Because, I NEED everything on that drive. I really was an idiot for trying under these circumstances.

---

### Post by Pumalite on 2008-04-21
sudo fdisk -l
Will not format your drive. Will just let me know your drives/partitions.

---

### Post by brodae on 2008-04-21
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8760b932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         784     6297448+  12  Compaq diagnostics
/dev/sda2             785       24321   189060952+   7  HPFS/NTFS

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       15450   124102093+   c  W95 FAT32 (LBA)
/dev/sdf2   *       15451       16446     8000370   83  Linux
/dev/sdf3           38416       38788     2996122+  82  Linux swap / Solaris
/dev/sdf4           16447       18936    20000925   83  Linux

Partition table entries are not in disk order

---

### Post by Pumalite on 2008-04-21
Mount the partition:
sudo mkdir /media/sdf2
sudo mount -t ext3 /dev/sdf2 /media/sdf2
Post:
cat /media/sdf2/boot/grub/menu.lst

---

### Post by brodae on 2008-04-22
This is what I did:

ubuntu@ubuntu:~$ sudo mkdir /media/sdf2
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdf2 /media/sdf2
ubuntu@ubuntu:~$ cat /media/sdf2/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=e2fa8579-1355-44eb-b2e6-03d34e4659ac ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e2fa8579-1355-44eb-b2e6-03d34e4659ac ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e2fa8579-1355-44eb-b2e6-03d34e4659ac ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
chainloader     +1

What does that all mean?

---

### Post by brodae on 2008-04-24
Well, I've got Ubuntu working. I went with my gut and gave up trying to get it to work on my External. My motherboard just wouldn't recognize emulate SCSI drives. So, I edited the main partition on my main drive (risky, I know) and put Ubuntu on there. So, now Windows is working too. I've got a problem with downloading updates and drivers, but I'll look on the forums and/or start my post if I need to for that problem. Thanks for the help you provided.

B

---

### Post by Nathanmoyer21 on 2008-04-24
Brodae-
I know I wasen't involved in this convorsation..But I think now that you have your Windows OS up and running, it would be a GOOD time to backup ALL the data you couldn't risk before to a DVD or pen drive or something..Considering how you were afraid to lose everything before, you never know..I lost 3 years of family pictures and videos figuring out ubuntu and xp dual-booting..So yea..

---

