---
title: "Dual boot: Vista + Ubuntu 7.10 reboot crash"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Chimmy2 on 2008-03-15
I've recently attempted an Ubuntu 7.10 x64 dual boot with Vista x64. At initial install I have to get over several roadblocks due to 8800gt card. However, this is not the problem. Ubuntu 7.10 works amazingly upon initial install. I am able to reboot and still keep my current display settings. Problem arises when I boot back into Vista for the first time after a clean Ubuntu install. When I reboot into Ubuntu I am forced into "Low graphics mode," my HDD are missing from "places" as well as my desktop, and my network adapter doesn't work. On one attempt /boot/grub/menu.lst on boot showed "Debian" not "Ubuntu" as boot option. GDM was changed completely to a Debian install without me doing anything. 

Note: this is only after rebooting into Ubuntu after shutting down Vista for the first time.

I'm using the stock Grub with Vista installed first. I've followed several guides exactly, all with the same eventual downfall. The only solution I've been able to procure for now is to fresh install Ubuntu every time I use Vista. I'd really like to be able to use both without boot problems.
My guess: perhaps Grub isn't loading kernel correctly? Maybe Vista is overwriting an important Ubuntu start file?

I've installed Ubuntu 7.10 on both a /swap, /boot, root combo as well as just a /swap, root set up. The initial having Grub rooted to /boot. Same outcome after shutting down in Vista. Will EasyBCD solve this problem? How can I fix this? 

Any response would be greatly appreciated. Thanks.

---

### Post by Chimmy2 on 2008-03-17
40+ views and no comments?

I'd really like to get Ubuntu running so that I can program in a more stable environment for my coursework. Any help really would be appreciated. Any at all?

Friend said today that it could be HAL. Anyone know much about this or if this could be the case? /reinstall number 8.

>.>

---

### Post by Darkchef on 2008-03-17
hmmmm interesting. Theres obviously a strange driver problem going on here. I would suggest maybe looking to see if your ubuntu installation completes successfully or it maybe due to the fact you are using a 64bit operating system. Sorry, i cannot help you much.

---

### Post by Darkchef on 2008-03-17
hmmmm i dont think deleting sda2 will help as this is the partition used to store vista and all my programs installed. i have no idea what sda1 is ?? i want to keep vista intact.

---

### Post by dstew on 2008-03-17
This is a very strange problem. It is worth investigating.> When I reboot into Ubuntu I am forced into "Low graphics mode," my HDD are missing from "places" as well as my desktop, and my network adapter doesn't workThis sort of behavior can happen if Vista is installing some firmware into these devices (like the network adapter) or changing settings that are stored the devices (like the drive controller).> Maybe Vista is overwriting an important Ubuntu start file?This I doubt, since VIsta probably ignores the ext3 partition completely. But the grub menu having "Debian" as a choice is odd. Can you post the output of ```
suto fdisk -l
```and```
cat /boot/grub/menu.lst
```

---

### Post by Chimmy2 on 2008-03-18
This is what I got from sudo fdisk -l
[INDENT]Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d030d03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7891    63381703+   7  HPFS/NTFS
/dev/sda2            7892        7953      498015   82  Linux swap / Solaris
/dev/sda3            7954        9039     8723295   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x7bfb130a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      969018   488385040+   7  HPFS/NTFS[/INDENT]

In terminal cat /boot/grub/menu.lst returned

[INDENT]# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
# kopt=root=UUID=2fde91a4-3604-45c9-b200-71dd9468cc2c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2fde91a4-3604-45c9-b200-71dd9468cc2c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2fde91a4-3604-45c9-b200-71dd9468cc2c ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1[/INDENT]

Thank you both for your comments. I was beginning to think my posts had been lost. Lewl. I hope this info inspires you dstew.

---

### Post by dstew on 2008-03-18
The grub menu seems to be set up properly. One last thing to check is if the UUID value in the kernel lines is correct. For that, do```
vol_id /dev/sda3
```

If the UUID matches, I am mostly out of ideas. However, one thought is to install the 32-bit version of Ubuntu instead of the 64-bit. Even if you have a 64-bit processor, there is very little performance advantage to the 64-bit version, and the drivers for the 64-bit Ubuntu are more troublesome than those for the 32-bit version.

---

### Post by Chimmy2 on 2008-03-18
Heh. I can't punch the command and receive a response because it's currently not detecting my HDDs again. I'll try again later though.

---

### Post by Arthur Archnix on 2008-03-18
How did you install Ubuntu?

Live, alternate, or Wubi?

---

### Post by Chimmy2 on 2008-03-19
I installed Ubuntu 7.10 using the Live CD. Why?

---

### Post by kushykush on 2008-03-21
The problem is not with GRUB.  Windows Vista has a new boot control device (BCD) which will  not share the MBR with any other system like GRUB.  So you can install GRUB in the same MBR but it will make Vista inoperable.  It will not boot or mess up your other systems.

I am facing a similar problem.  I had Windows Vista already installed on my first SATA (0,0), which had two almost equal partition (about 76 MB each).  I installed UBUNTU in the second partition (0,1) of the same drive.  It installed fine as did GRUB.  When started GRUB comes up and rightly identifies other Operating Systems (including Freespire on the Second SATA drive).  

However, only Ubuntu boots properly.  Vista will not boot through GRUB.  Its BCD is corrupted.

I have tried to research this problem (how to properly install GRUB where Vista is present and how to keep Vista's boot alive).  I have not found a solution.  Now, even after repair and a rebuild of boot through Windows Vista bootrec.exe, I still cannot fix Vista.  

It is clear that Vista will not co-exist with a system like GRUB.  However, there has to be a solution.  Commercially available disk/boot management systems such as ACRONIS can do the job if one is willing to pay $50.00.  There has to be a free workable solution.

---

### Post by dstew on 2008-03-21
BCD stands for "Boot Configuration Data", and it is part of the Vista boot system. It consists of files on the Vista system partition that contain boot data. You can repair/replace the active BCD store using the Vista recovery tools in the bootrec.exe program. To repair your Vista boot, completely delete and rebuild the system BCD store using the directions [here]("http://support.microsoft.com/kb/927392"). Then, do bootrec /FixBoot. Make sure you are in the correct partition when you do this. Do not do /FixMbr, since that is where grub needs to be. Then, you might have to edit the grub menu.lst file to get Vista to boot. There is nothing in Vista that should prevent grub from booting it, if it is all configured correctly.

---

### Post by Chimmy2 on 2008-03-25
6 days, no response?

---

### Post by Arthur Archnix on 2008-03-25
I ask because Wubi is the only thing that could possibly explain what's occuring. Even then...

You'll have to give more information. It's not possible for you to install, reboot and all is well. Boot into Vista, do nothing more than use vista and suddenly find that the graphics are messed up and the grub entry has been changed from Ubuntu to Debian.

The simply can't just happen from what you've described, though I can imagine other ways it would come about. Maybe someone is messing with you.

Check out usplash entries in synaptic. Uninstall the debian ones, and make sure the ubuntu one is installed. Just to be safe, reinstall it.

---

### Post by Chimmy2 on 2008-03-27
Gah. It can't be easy can it? Just routine problem that has a solution. No...I have to get one that no one knows what's going on. Not sure who could be messing with me. My computer is secure and in a physically secure environment, all iso files were grabbed from ubuntu website. Could it be the fact that it's 64bit that's messing this whole thing up?

---

