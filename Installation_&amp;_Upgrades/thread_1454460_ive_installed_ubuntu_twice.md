---
title: "ive installed ubuntu twice"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2010-04-14
i have a dual boot system, vista ubuntu
i have installed ubuntu 2 times
ver 9.04
id like to uninstall 1 of the ubuntu`s
is there a program that i could use to copy and paste the partition info into this forum 
{ive got gparted} on disk
so that i could ask some one here on which partitions i should delete

ubuntu is great!!!!!!

---

### Post by wilee-nilee on 2010-04-14
> **jimbean said:**
> i have a dual boot system, vista ubuntu
i have installed ubuntu 2 times
ver 9.04
id like to uninstall 1 of the ubuntu`s
is there a program that i could use to copy and paste the partition info into this forum 
{ive got gparted} on disk
so that i could ask some one here on which partitions i should delete

ubuntu is great!!!!!!

There is a boot script that is helpful.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You might start with sudo fdisk -l in the terminal and post that and maybe a screenshot of gparted showing your setup.

---

### Post by jimbean on 2010-04-14
yeah the first time i installed ubuntu it was way to small and i tried to fix it and now ive got 2 ubuntu`s any help please



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   505,508,474   505,508,412   7 HPFS/NTFS
/dev/sda2         513,228,555   976,768,064   463,539,510   5 Extended
/dev/sda5         971,530,938   976,414,634     4,883,697  83 Linux
/dev/sda6         976,414,698   976,768,064       353,367  82 Linux swap / Solaris
/dev/sda7         513,228,681   959,466,059   446,237,379  83 Linux
/dev/sda8         959,466,123   971,530,874    12,064,752  82 Linux swap / Solaris
/dev/sda3         505,517,355   513,228,554     7,711,200  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C0D018D6D018D48E                       ntfs                                     
/dev/sda3        90020087-6964-4bb0-95a8-4c93f80c4eac   ext3                                     
/dev/sda5        5f1c3aa5-1065-4088-8031-861b77614eac   ext3                                     
/dev/sda6        795a9b89-e182-42d6-83dd-6fd28a3dca44   swap                                     
/dev/sda7        dd2b8014-1028-457b-a671-cb250c014e0d   ext3                                     
/dev/sda8        f97ac123-d471-4894-99ac-dbbe2018e1c5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5f1c3aa5-1065-4088-8031-861b77614eac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f1c3aa5-1065-4088-8031-861b77614eac

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		5f1c3aa5-1065-4088-8031-861b77614eac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f1c3aa5-1065-4088-8031-861b77614eac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		5f1c3aa5-1065-4088-8031-861b77614eac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f1c3aa5-1065-4088-8031-861b77614eac ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5f1c3aa5-1065-4088-8031-861b77614eac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=5f1c3aa5-1065-4088-8031-861b77614eac /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=795a9b89-e182-42d6-83dd-6fd28a3dca44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 498.8GB: boot/grub/menu.lst
 498.8GB: boot/grub/stage2
 497.7GB: boot/initrd.img-2.6.28-11-generic
 498.1GB: boot/vmlinuz-2.6.28-11-generic
 497.7GB: initrd.img
 498.1GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dd2b8014-1028-457b-a671-cb250c014e0d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd2b8014-1028-457b-a671-cb250c014e0d

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		dd2b8014-1028-457b-a671-cb250c014e0d
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=dd2b8014-1028-457b-a671-cb250c014e0d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		dd2b8014-1028-457b-a671-cb250c014e0d
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=dd2b8014-1028-457b-a671-cb250c014e0d ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		dd2b8014-1028-457b-a671-cb250c014e0d
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd2b8014-1028-457b-a671-cb250c014e0d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		dd2b8014-1028-457b-a671-cb250c014e0d
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd2b8014-1028-457b-a671-cb250c014e0d ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd2b8014-1028-457b-a671-cb250c014e0d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd2b8014-1028-457b-a671-cb250c014e0d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dd2b8014-1028-457b-a671-cb250c014e0d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd2b8014-1028-457b-a671-cb250c014e0d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd2b8014-1028-457b-a671-cb250c014e0d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f1c3aa5-1065-4088-8031-861b77614eac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f1c3aa5-1065-4088-8031-861b77614eac ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=dd2b8014-1028-457b-a671-cb250c014e0d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=f97ac123-d471-4894-99ac-dbbe2018e1c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 433.6GB: boot/grub/menu.lst
 433.7GB: boot/grub/stage2
 433.6GB: boot/initrd.img-2.6.28-11-generic
 433.7GB: boot/initrd.img-2.6.28-14-generic
 433.7GB: boot/initrd.img-2.6.28-18-generic
 433.6GB: boot/vmlinuz-2.6.28-11-generic
 433.7GB: boot/vmlinuz-2.6.28-14-generic
 433.6GB: boot/vmlinuz-2.6.28-18-generic
 433.7GB: initrd.img
 433.7GB: initrd.img.old
 433.6GB: vmlinuz
 433.7GB: vmlinuz.old

---

### Post by jimbean on 2010-04-14
some more info 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31467   252754206    7  HPFS/NTFS
/dev/sda2           31948       60801   231769755    5  Extended
/dev/sda3           31468       31947     3855600   83  Linux
/dev/sda5           60476       60779     2441848+  83  Linux
/dev/sda6           60780       60801      176683+  82  Linux swap / Solaris
/dev/sda7           31948       59724   223118689+  83  Linux
/dev/sda8           59725       60475     6032376   82  Linux swap / Solaris

---

### Post by ajgreeny on 2010-04-14
As you might have expected from the partition numbers, sda7 appears to be your most recent and therefore, largest ubuntu installation.

You appear to have allowed now half of the disk for all the ubuntu partitions, which are a bit confusing.  sda3 would appear to be the first ubuntu you installed, and sda2 is the extended partition that originally contained only your swap, I imagine.

I assume you enlarged that extended partition and added the new ubuntu install to it, rather than simply enlarging your first ubuntu partition, but whichever you did, the new ubuntu is sda7, with about 6GB swap in sda8, by the look of things.  You also have a tiny swap partition, sda6.  I would suggest you make sure you have backed up all your personal files from the first ubuntu installation (sda3) and copy them to your new one, and then delete the partitions you don't need.

I am a bit confused about which partition is which, however, as you seem to have more than just the two ubuntu installs you mention, as fdisk shows sda3 (~3GB), sda5 (~2.5GB) and sda7 (~230GB) as linux partitions.  Any idea why three?

---

### Post by wilee-nilee on 2010-04-14
For me a screenshot of gparted would help, I'm not really efficient or qualified to look at the boot script and advise, although there are others who are, so it is great that you posted it.

---

### Post by jimbean on 2010-04-14
a ??? thats the problem as you stated if it was ntfs id know a little more but ubuntu linux is still in learning
i installed ubuntu without thinking usually problem free 
ive got no idea what i did i thought it was just the 2 installs
i resized the partition after the first install thinking it would overwrite the first 
any of that make sense
so you would suggest???
deleting any partitions or just editing the grub boot menu list
in 2 or 3 years am i going to have corruption problems???

---

### Post by jimbean on 2010-04-14
i grab a screenshot from gparted bootdisk but it saved in my root folder which i accessed with nautilus {root folder} but the screenshot is not there

---

### Post by wilee-nilee on 2010-04-14
> **jimbean said:**
> i grab a screenshot from gparted bootdisk but it saved in my root folder which i accessed with nautilus {root folder} but the screenshot is not there

If your making a screenshot in a regular setup it should not go to root, choose where it goes when the gui is shown.

---

### Post by jimbean on 2010-04-16
screenshot ill try again

---

