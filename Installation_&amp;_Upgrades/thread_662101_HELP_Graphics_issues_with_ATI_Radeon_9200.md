---
title: "HELP: Graphics issues with ATI Radeon 9200"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by radiocognition on 2008-01-08
Hi Everybody:

I just got done setting up my system in a reasonable manner, and I moved on to properly installing my graphics card.  I could never boot the Ubuntu GUI from either the live cd or my own installation when I enabled the card (ATI Radeon 9200) from the BIOS.  The system always hanged at "Running local boot scripts (/etc/rc.local)   [ OK ]".  Just before the system hangs though, the screen flickers four times before coming to a halt.  I can reach a terminal and I can also boot into recovery mode.

First some information about my system:

Ubuntu 7.10 - 64 Gutsy Gibbon
AMD-64 Processor
ATI Radeon 9200

I have a few questions that maybe one of you could answer for me.  I know that the driver I should be using with the card is called fglrx, but shouldnt xserver-xorg be able to identify the card automatically (I think its pretty common).  Also, I've heard of many people using my card who were able to launch the Ubuntu GUI without any problems.  Does this have something to do with my architecture (64-bit), or does it suggest that there is something wrong with my card?

What I have done so far is this:

When the system hangs at boot, I can reach a terminal with alt-F2.  After logging in, I checked to see if the latest and greatest fglrx drivers were installed (they were).  I launched xserver-xorg with:
```
sudo dpkg-reconfigure xserver-xorg
```
I then picked the fglrx driver and set the card name to ATI RADEON 9200.  I completed the reconfiguration, then restarted the graphics with:
```
sudo /etc/init.d/gdm restart
```
The GNOME stops, restarts, and then the screen flickers again as it did in the beginning.  Frustrating stuff.  What is going on, not quite sure where to go from here.

---

### Post by Pumalite on 2008-01-08
Post your specs. Did you use the Alternate CD?

---

### Post by radiocognition on 2008-01-08
not sure if I can get to my specs from where im at now.  I know there are some unix commands that can list out my motherboard and all of the fine details but i seem to have forgotten it.  This is what I remember

AMD 64 Processor
2 GB Memory 
MSI K9VGM-V Motherboard
System Drive 40 GM SCSI
120 SCSI & 80 SATA linked by a MDADM RAID
Floppy
DVD-Drive

---

### Post by radiocognition on 2008-01-08
Bah tried lshw command but I cant scroll up to the top to see everything that it listed (funky keyboard)

---

### Post by Pumalite on 2008-01-08
Your problem might be your Raid:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by radiocognition on 2008-01-08
it might be, but im pretty sure that there is something else wrong too.  I tried to start the graphics card before I started the RAID and ran into the exact same problem.  The actual system is on a hardrive that is not part of any RAID, if that helps

---

### Post by Pumalite on 2008-01-08
'I tried to start the graphics card before I started the RAID '

Could you explain this better?

---

### Post by radiocognition on 2008-01-08
Weeks ago I went to the BIOS, specified that I wanted to use the graphics card and started Ubuntu.  Ubuntu stopped during the boot process at the same point.  I opened a terminal and reconfigured xserver-xorg just as I described earlier.  I noticed the same behavior, the graphics card didnt work.

A few days later I started the software RAID.  Now I am trying agin to reconfigure the graphics card and am noticing the same problems.  Maybe there are issues because of the RAID, but I think that there might be something else going on

---

### Post by Pumalite on 2008-01-08
If you configured a Raid AFTER you installed Ubuntu,; there is your problem. Boot your Live CD and post:
sudo fdisk -lu

---

### Post by radiocognition on 2008-01-09
I burned and booted the live CD until I realized that the RAID wasnt listed on the live installation
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb342ae80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   160826714    80413326   83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdad4f39a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    76903154    38451546   83  Linux
/dev/hdb2        76903155    80292869     1694857+   5  Extended
/dev/hdb5        76903218    80292869     1694826   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00bc8a9d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1              63   234436544   117218241   83  Linux
```

booting back into graphics safe mode on my own install allowed me to see the software RAID that I had set up.  Its strange that fdisk said that the RAID doesnt have a valid partition table - ive been having no problems reading and writing data to the RAID.
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb342ae80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   160826714    80413326   83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdad4f39a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    76903154    38451546   83  Linux
/dev/hdb2        76903155    80292869     1694857+   5  Extended
/dev/hdb5        76903218    80292869     1694826   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00bc8a9d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1              63   234436544   117218241   83  Linux

Disk /dev/md0: 202.3 GB, 202374578176 bytes
2 heads, 4 sectors/track, 49407856 cylinders, total 395262848 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

---

### Post by Pumalite on 2008-01-09
Your boot flag is in hdb1. See if you can post your menu.lst:
cat /boot/grub/menu.lst

---

### Post by radiocognition on 2008-01-09
```
$ cat /boot/grub/menu.lst
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
timeout         3

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
# kopt=root=UUID=23e8d84e-c1b4-40a4-a937-049a13520794 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=23e8d84e-c1b4-40a4-a937-049a13520794 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=23e8d84e-c1b4-40a4-a937-049a13520794 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Pumalite on 2008-01-09
Backup your file first:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

gksudo gedit /boot/grub/menu.lst

Change (hd0,0) to (hd1,0) 

Save, exit and reboot.

---

