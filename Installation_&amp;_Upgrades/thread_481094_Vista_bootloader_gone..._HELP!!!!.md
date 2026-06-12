---
title: "Vista bootloader gone... HELP!!!!"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by AriciU on 2007-06-22
I've wrote GRUB to the MBR replacing the Vista boot loader. I did that because i could not get Vista's bootloader to load Ubuntu.

I have 3 hard drives and 2 OS's, Vista and Ubuntu 7.04.

I've followed this guide ([http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)) to replace Vista's bootloader with GRUB.

Ubuntu loads up just fine now, no problems with it. The problem is that when i want to load Vista's bootloader to boot Vista i get this error:

> Error 18: Selected cylinder exceeds maximum suported by BIOS

I've done some research on that and found out that the error pops up because the BIOS has troubles booting a specific OS if it's not written on the first 8GB of the drive or something like that. It also said that new hardware (mobo, bios) is not supposed to have that problem.

My motherboard is a Gigabyte GA-K8NS-Ultra. Not new by recent standards but no dinosaur either...

I will attach below a copy of my GRUB menu.lst

> title		Windows Vista (loader)
root		(hd1,1)
savedefault
chainloader	+1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,3)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=1ea44946-645f-4375-bef1-262d2e21f2f0 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

............. etc etc etc

This is the output of "df -h" to see how my drives are setup:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              29G   11G   17G  40% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  132K  506M   1% /proc/bus/usb
udev                  506M  132K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sdb4             492M  170M  296M  37% /boot
/dev/disk/by-uuid/CA9C369A9C36814D
                      129G   87G   42G  68% /media/hdb1
/dev/disk/by-uuid/BCA83A94A83A4CE0
                       21G   19G  2.1G  91% /media/hdb2
/dev/disk/by-uuid/122983EA943B1179
                      179G  170G  9.2G  95% /media/sda1
/dev/disk/by-uuid/767C51E77C51A2A3
                      4.9G  4.5G  451M  91% /media/sda3
/dev/disk/by-uuid/DC0C43580C432CB8
                      3.0G  2.8G  162M  95% /media/sda5
/dev/disk/by-uuid/BA70867470863763
                      269G   76G  193G  29% /media/sdb1


Here's an output of "fdisk -l" :

> fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      371368   187169440+   7  HPFS/NTFS
/dev/sda2          381527      387621     3071880    f  W95 Ext'd (LBA)
/dev/sda3          371369      381526     5119632    7  HPFS/NTFS
/dev/sda5          381527      387621     3071848+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      266993   134564440+   7  HPFS/NTFS
/dev/hdb2          266994      310099    21725376    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37199   281224408+   7  HPFS/NTFS
/dev/sdb2   *       37200       41206    30292920   83  Linux
/dev/sdb3           41278       41345      514080   82  Linux swap / Solaris
/dev/sdb4           41207       41277      536760   83  Linux

Partition table entries are not in disk order
fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      371368   187169440+   7  HPFS/NTFS
/dev/sda2          381527      387621     3071880    f  W95 Ext'd (LBA)
/dev/sda3          371369      381526     5119632    7  HPFS/NTFS
/dev/sda5          381527      387621     3071848+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      266993   134564440+   7  HPFS/NTFS
/dev/hdb2          266994      310099    21725376    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37199   281224408+   7  HPFS/NTFS
/dev/sdb2   *       37200       41206    30292920   83  Linux
/dev/sdb3           41278       41345      514080   82  Linux swap / Solaris
/dev/sdb4           41207       41277      536760   83  Linux

Partition table entries are not in disk order

The Ubuntu boot partition is /DEV/SDB4 (HD2,3). The Vista partition is /DEV/HDB2 (HD0,1 or HD1,1 -> i've tried booting both by editing GRUB's menu.lst but still no go).

I noticed looking at the fdisk output that /dev/hdb2 (vista) is not set up as a "boot" partition (/dev/hdb1 is witch is just my other stuff, programs, etc partition).

Could this be it? I don't think so considering the GRUB error 18.

Hope you can help me fix this :)

---

### Post by cwgpress on 2007-06-22
If you backed up the mbr before replacing it, restore it and see if you can boot into Windows. If that works, try editing the boot.ini file on the root of that disk. Add an entry for Ubuntu, or better yet for a loader, e.g., grldr which is a version of grub. Or, after Windows works normally, restart to the Ubuntu installation and repeat the end steps, being very careful not to delete the Vista loader or access to it!

I found an article that looks pretty good but I haven't done this so I can't guarantee it:

[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why#GRLDR_-_A_Simpler_Approach](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why#GRLDR_-_A_Simpler_Approach)

On my single-disk system, I'm dual-booting Vista and Ubuntu using grub. The installation took care of it for me (although I made sure it had the Vista loader listed before I allowed it to write to the MBR!)

Good luck!

---

### Post by AriciU on 2007-06-22
Can you post a copy of your menu.lst please? Specially the vista bootloader part. Thanks

There's no boot.ini for Vista btw. I got into this situation because my XP HDD died on me and i had to remove it completly. Everything worked perfect once i had it... Main boot loader was Vista's bootloader (witch i couldn't get to load Ubuntu this morning) and they all booted fine (xp, vista, ubuntu).

---

### Post by cwgpress on 2007-06-22
Forgot a couple of things.

First, an apology: I'm a newbie and I'm giving advice to somebody with 7 operating systems! But I do have a dual-boot working with Vista, on a Dell E521 that had Vista preloaded, so maybe I know a little bit about it...

Second: I talked about boot.ini but in Vista the equivalent file is in the BCD store. BCD in this case is not the inefficient mapping of decimal numbers into 16 bits, but the Boot Configuration Data. Here's a Microsoft resource about it:

[http://technet2.microsoft.com/WindowsVista/en/library/85cd5efe-c349-427c-b035-c2719d4af7781033.mspx?mfr=true](http://technet2.microsoft.com/WindowsVista/en/library/85cd5efe-c349-427c-b035-c2719d4af7781033.mspx?mfr=true) 

Chuck

---

### Post by AriciU on 2007-06-22
Yeah but BCD is kindof a pain to edit like the good old boot.ini. No idea why they had to change something that was working so good.

Anyway, do you have GRUB written on the MBR or do you start Ubuntu with the default Vista boot loader?

Can you please copy paste here the contents of you /boot/grub/menu.lst so i can have a look at your setup.

I'm afraid that when i followed that guide to write grub to the MBR it deleted Vista's bootloader all together :( I hope i won't have to resort to restoring Vista's bootloader to the MBR instead of Grub...

---

### Post by AriciU on 2007-06-22
LMAO. I'm an idiot :)

1. Windows can't boot if the boot loader is setup on the second partiton of a drive. It must be on the first partition.

2. I had root (hd0,1) in grub's menu.lst because that's where i had the Windows Vista installation (2nd partition of the HDD)

3. I forgot that the boot loader was installed by default on the 1st partition.

So...

One 

> root (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)

later and Vista booted fine :D

---

### Post by cwgpress on 2007-06-22
I can see I have a lot to learn about grub. As I understand it, you changed the root partition, and swapped drives? Cool!

In the better late than never category, here's some info:

A text copy of the menu.lst file:

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
default		7

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
# kopt=root=UUID=d56428e3-ba46-4a32-9c3f-fe4e7fad474b ro
# kopt_2_6=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

===========================
a text copy produced by bcdedit:


Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {572bcd55-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {7fdd6ac6-70be-11db-ba26-a0b016378059}
nx                      OptOut

===========================================

You'll note I haven't got around to following your advice on the default selection.

I hope this will help someone down the line.

Chuck

---

### Post by Ultra Magnus on 2007-06-22
add something like this to the bottom of your /boot/grub/menu.lst file

title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

where it says (hd0,1) you need to identify which partition windows is on:
code: sudo fdisk -l
windows is the one formatted as ntfs

note: sda and hda are interchangeable
in the menu/last file, partition numbers start with 0, so if your windows partition is sda1 then write (hd0,0) 
sdb1 - hd1,0
sdb,2 - hd1,1

---

