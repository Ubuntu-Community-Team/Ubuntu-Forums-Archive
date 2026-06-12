---
title: "upgrade to 10.04 hangs"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by DawgMan on 2010-11-22
Just upgraded to 10.04 from 9.10. upgraded from update manager. System would not boot.

Booted live cd and used the 9.10 menu.lst. Now boots but takes a long time.

what exactly happens on boot?  Step by Step?

I don't know much about the kernel. I assume they are listed in the /boot directory and are called by menu.lst (dual boot w/ XP) (btw: I am ready to get rid of XP once I get tis fixed).

9.10 appears to use 2.6.31-20-generic, therefore, I assume 10.04 uses 2.6.32-25-generic.

Any help would be great.

---

### Post by sikander3786 on 2010-11-23
Can you please list some more details regarding your hardware specs including RAM, graphics card and CPU.

How much time does it take to boot exactly? Is it slow on the desktop also?

And do you get any errors while booting?

> Booted live cd and used the 9.10 menu.lst. Now boots but takes a long time.

After reading that, I suggest that you please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us more details about you current boot setup and therefore let us advise accordingly.

Thanks.

---

### Post by DawgMan on 2010-11-23
Sorry for the bad quote.

Meant to say: booted live a live CD (SUSE) and edited the menu.lst to include the 9.10 kernel.  So now my grub menu lists:

```

title		Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854	
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

```

When I boot from Ubuntu 10.04 LTS, kernel 2.6.32-25-generic I get:

Error 15: File not found

Press any key to continue.

When I boot from Ubuntu 9.10, kernel 2.6.31-20-generic I get:

Mount: mounting none on /dev failed: No such device61f538854
Starting up ...

This takes about 15 - 20 seconds then the system boots with a 10.04 splash screen.

Note: the device61f538854 is the last part of the UUID for the disk.  I assume that grub is corrupted.

See results.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   976,768,064   771,971,445   5 Extended
/dev/sda5         204,796,683   964,847,834   760,051,152  83 Linux
/dev/sda6         964,847,898   976,768,064    11,920,167  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        266C51FD6C51C867                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cd0c7441-38d1-4e1f-a206-b161f7538854   ext3                                     
/dev/sda6        6e553533-d163-46f3-b633-deb66deb8210   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
timeout		5

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
# kopt=root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd0c7441-38d1-4e1f-a206-b161f7538854

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854	
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=6e553533-d163-46f3-b633-deb66deb8210 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sda1 /media/Disk2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 362.9GB: boot/grub/menu.lst
 362.8GB: boot/grub/stage2
 366.9GB: boot/initrd.img-2.6.28-16-generic
 367.4GB: boot/initrd.img-2.6.31-20-generic
 367.4GB: boot/initrd.img-2.6.32-25-generic
 362.8GB: boot/vmlinuz-2.6.28-16-generic
 374.7GB: boot/vmlinuz-2.6.31-20-generic
 362.9GB: boot/vmlinuz-2.6.32-25-generic
 367.4GB: initrd.img
 362.9GB: vmlinuz

```

---

### Post by DawgMan on 2010-11-26
I tried to re-install grub via:

```

https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD

```

I used method 1 and now I boot to the grub> prompt.

I tried method 2 to fix method 1 but still no boot.

See output from fdisk:

Why does /dev/sda2 seem to contain both /dev/sda5 and /dev/sda6?

```

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   976,768,064   771,971,445   5 Extended
/dev/sda5         204,796,683   964,847,834   760,051,152  83 Linux
/dev/sda6         964,847,898   976,768,064    11,920,167  82 Linux swap / Solaris

```

I am trying to boot to /dev/sda5. Is that correct?

---

