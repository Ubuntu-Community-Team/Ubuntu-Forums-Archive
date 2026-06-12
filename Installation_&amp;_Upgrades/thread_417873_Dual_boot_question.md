---
title: "Dual boot question"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Darrell262 on 2007-04-21
Ok, been at it for a bit now. 

Dual booting Vista and Ubuntu on 2 seperate hd's 

I heard about gparted, ran that on the live cd to delete the boot option flag from vista and rebooted. to my suprise Grub booted. (YA!!!) 

I chose to boot up ubuntu off the hard drive. and It worked fine. 

Then restarted booted up windows (there was 2 options to load windows, only 1 worked (I have been screwing around alot) 

Windows loaded up fine, then I goto restart, and I lost my grub again and windows is auto booting. 

So my only guess is boot back up the live cd and run gparted again set the boot flag off for vista again and I'll get into grub. 

My question is how do I stop winblows from setting the boot flag to boot windows. Or can I use windows dual boot program some how..

---

### Post by BoneKracker on 2007-04-22
Could you post here your file  /boot/grub/menu.lst?

---

### Post by Darrell262 on 2007-04-22
Ok ok, sorry, I am new to this, but a fast learner, I figured out how to get to that dir.

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
# kopt=root=UUID=304d281c-a4bc-410c-8ba9-e4e859a57d4e ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=304d281c-a4bc-410c-8ba9-e4e859a57d4e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=304d281c-a4bc-410c-8ba9-e4e859a57d4e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Windows Vista/Longhorn (loader)
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

---

### Post by BoneKracker on 2007-04-22
It looks like you have Ubuntu on your master drive (/dev/hda) and Vista on your slave drive (/dev/hdb), is that correct?

If so, one thing you can do is delete the redundant entry in menu.lst for booting Windows.  It looks to me like the last one is redundant.

---

### Post by Darrell262 on 2007-04-22
Ok, still having problems. :-)

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      620178   312569680+   7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

Ok, as you can see, my first drive (This is booted on the live cd) shows
74gig sda, my first drive with ubuntu installed and my swap drive
74gig sdb is my Vista install on my other drive
320gig stc is my 320 gig data drive for vista (just data crap)
320gig std is my other 320 gig data drive for vista


guessing sda is hdd0 (bios) and sdb is hdd1 etc..
looking at my grub booter program, if I select the first vista boot (root (1,0)
I get missing ndtl or something and windows doesnt boot.
if I choose the second vista boot option, it boots but then I cant get grub back.

I know somethings screwy here, but I have installed a few times so I think that is causing it. How do I edit my menus.lst file so I can boot vista and ubuntu and keep grub booting as well?

---

### Post by Darrell262 on 2007-04-22
bump

---

### Post by BoneKracker on 2007-04-22
Okay.  Now we get another relevant piece of information.  You do indeed have four drives and Windows is on the fourth one.  That means I was wrong last time, it was the other Windows entry that was redundant.

> guessing sda is hdd0 (bios) and sdb is hdd1 etc..
looking at my grub booter program, if I select the first vista boot (root (1,0)
I get missing ndtl or something and windows doesnt boot.
if I choose the second vista boot option, it boots but then I cant get grub back.

First of all, relax.  Yes, this it is quite possible for them to coexist nicely.  You just have to get the bootloader configured properly.  GRUB (and other bootloaders) can be quite confusing for people.  This is almost a rite of passage to becoming a Linux user.  So don't feel too frustrated -- you and a hundred other people are having similar problems tonight.  :)   I'll try to explain a couple of the confusing points, then if you still have questions, feel free to ask.

**I)** First, it's important to understand that Linux uses one set of names for devices, and GRUB uses another different one.

a) In Linux, everything is a file. Accordingly, it has a path that shows its location.  

Devices (like disks, sound cards, cameras, and everything else) are files too.  Device files are stored in a directory called /dev  and they all look like /dev/something.  Frequently they have a letter and or number to help distinguish them.  The normal nomenclature for an ide disk is /dev/hd<someletter>.  The two disks on the first ide controller are /dev/hda and /dev/hdb.  The two disks on the second ide controller are /dev/hdc and /dev/hdd.

Similarly, if you have scsi disks (and sata disks are treated like scsi disks) they have device names like /dev/sda or /dev/sdb or /dev/sdc .... etc.

Now, disks have partitions.  So Linux adds these to the device names of the disks to create a device for each partition.  Each partition is a device.  /dev/sda1  or /dev/sdd9  are devices that are partitions on sata or scsi disks.  Note that the partition numbers start at 1 (with 1 being "the first partition").

Normally, anything in Unix that gets numbered starts at zero (zero being the first thing).  For some reason, disk partitions do not follow this rule in the Linux device naming scheme.

2) Now, we also have a naming scheme in GRUB:

GRUB actually gets used on different systems besides Linux.  It uses it's own disk/partition naming convention to talk to itself, and it uses the language of the system to talk to the system.  So it uses GRUB-talk if you will to talk to its own program, and it uses the Linux conventions for devices to talk to Linux.  

GRUB indicates disks and partitions like this:  (hd#,partition#).  Example: (hd0,0) is the first partition on the first disk.  Note that GRUB counts from 0 like a good program should.  It doesn't matter if it's an ide disk, a scsi disk, or what.  It's referred to as a hard disk (hd).  So the fourth partition on the 3rd disk would be (hd2,3).  The 9th disk's second partition would be (hd8,1).

So compare the two methods of referring to the first partition on the first disk:
[INDENT]
Linux: /dev/sda1
GRUB: (hd0,0)[/INDENT]

**II)** Second, it's important to understand what is meant by "root".  We have the "GRUB root" and the "Linux Root" and they are two different things.
[B]
a)[/B] When GRUB is talking to itself, "root" means (where is the Master Boot Record?).  This is traditionally on the MBR of the first partition on the first disk.  Since GRUB is talking to itself (not Linux) this is the line that says "root (hd0,0)".   Nowadays, you can go into the BIOS and change which disk is the "boot disk".  So this doesn't have to be (hd0,0) anymore.  Also, you can chainload one bootloader from another.  For example, you can install the GRUB root to your fourth disk (hd3,0), then change your BIOS to make that the boot disk, and include an entry in menu.lst that chainloads the Windows bootloader (located back on the first disk).

**b)** But what _Linux_ wants to know from GRUB is "where in the midst of all this crap is my root partition?".  So part of the "bootline" or "image" specifies the location of the Linux root.  That's in Linux-speak and it looks like "root=/dev/sdd3" or something.

An alternate means of specifying a device in Linux is to use a sort of serial number that it gets assigned when it's created.  This number (the UUID) uniquely identifies it.  Without this method, any disk hooked up to that connector would be treated as /dev/sdd.  So this helps keep track of devices.  If you want, you can change this in your grub menu to the standard /dev/blah format or stick with the uuid format, which seems to be Ubuntu's new default method.

To edit the file, you open it in editor:
sudo nano /boot/grub/menu.lst

ctrl+o     is save
ctrl+x     is exit





So that should take a lot of the mystery out of this for you.

---

### Post by Malac on 2007-06-05
Sorry for the late reply but only just stumbled across this thread.
The line "makeactive" in your menu.lst file is the one that is telling GRUB to make that partition the bootable(active) one. If you comment out that line (by placing a # sign in front of it) or delete it, you should be good to go.

Hope this helps.

---

