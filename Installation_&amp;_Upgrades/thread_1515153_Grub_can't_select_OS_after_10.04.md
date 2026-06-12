---
title: "Grub can't select OS after 10.04"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by Alpinist on 2010-06-21
Searched around but have not found this problem listed.  I have upgraded my 9.04 installation by doing a new install of 10.04 and keeping my /home partition.  I have a dual boot system with Win XP and an older version of ubuntu on another partition.

The problem is that when I get the grub menu I cannot select anything other than the top option.  Arrowing down it just keeps popping back up to the top option. I can hold the arrow key and it will go down through all the selections but just pops back up to the top if I let go.

If I press "e" to try and edit in order to manually select a drive to boot to the editor comes up and I can select up and down the lines but if I try to move the cursor to the right it just snaps back to the beginning of the line.

So I can't select windows XP or my old Ubuntu install, I can only boot to the new 10.04.

$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu6)

Any advice on how to get grub to let me select another entry would be appreciated.

---

### Post by Don Barzini on 2010-06-21
10.04 uses GRUB2 and is a whole different ballgame than the older version of GRUB.

Check this link below for everything you need to know to get familiar with configuring GRUB2...

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You might want to run the following again first from a terminal window in 10.04...

```
sudo update-grub
```

---

### Post by Alpinist on 2010-06-22
Thanks for the response.  I have looked through the community documentation and run the update-grub several times.  Same behavior.  I'll see if I can find anything else.

I went ahead and burned a copy of supergrub boot disk to CD and am able to boot to all my partitions so I have a work around but it is a lot preferable to actually have a working boot menu.

Currently my impressions of grub2 are very negative.  The old grub worked and didn't have these kind of problems.  Worst case is that I will give up on grub2 and try to use the supergrub disk to reinstall legacy grub.

---

### Post by wilee-nilee on 2010-06-22
Your problem probably is the grub-legacy in Jaunty and the Grub2 in Lucid.
Post the script in my sig with code tags.

---

### Post by Don Barzini on 2010-06-22
Your answer lies within your GRUB configuration files. I know GRUB2 can be annoying at first, but eventually you will get used to it.

Take a look at your current **/boot/grub/grub.cfg** file. It will contain entries for your menu and references to the configuration files within the **/etc/grub.d** directory that created those entries.

The partition numbering is different than that of GRUB legacy. One of your config files is confusing your /home partition for something else.

The link I posted also had instructions for reinstalling GRUB2 from the LiveCD and also for removing GRUB2 and installing legacy GRUB from directly within 10.04..... if that is the way you want to go.

Have you tried renaming your **/boot/grub/grub.cfg** file to something else (e.g. **/boot/grub/grub.cfg.old**) and then re-running **sudo update-grub**?

---

### Post by Alpinist on 2010-06-22
Ok, here is the output of the bootinfo

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       20972616 sectors, but according to the info from 
                       fdisk, it has 20980818 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,980,881    20,980,819   7 HPFS/NTFS
/dev/sda2          20,980,882   230,693,399   209,712,518   b W95 FAT32
/dev/sda3         232,508,745   390,716,864   158,208,120  83 Linux
/dev/sda4         230,693,400   232,508,744     1,815,345  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   100,004,624   100,004,562  83 Linux
/dev/sdb2         100,004,625 1,250,258,624 1,150,254,000   5 Extended
/dev/sdb5         100,004,688 1,250,258,624 1,150,253,937  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6C4452FE4452CA8A                       ntfs                                     
/dev/sda2        643A-4E8D                              vfat                                     
/dev/sda3        78b6f28a-e237-494e-9168-a3c6b3e3e1df   ext3                                     
/dev/sda4        ab109ed7-cc23-4fc5-8cbc-c4a38c90a70a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        da116537-e88f-4030-8699-f171575e7f6a   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        76b1d0fd-2f52-4649-95b4-512901fd0e9a   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df ro

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
# defoptions=quiet splash noapic

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
# howmany=1

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda1 :
UUID=6C4452FE4452CA8A /media/sda1 ntfs-3g defaults,locale=en_CA.UTF-8 0 1
# Entry for /dev/sda2 :
/dev/sda2 /media/sda2 vfat iocharset=utf8,umask=000 0 0
# defaults,locale=en_CA.UTF-8 0 1
# Entry for /dev/sda4 :
UUID=ab109ed7-cc23-4fc5-8cbc-c4a38c90a70a none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
usbfs /proc/bus/usb usbfs devgid=1000,devmode=664 0 0

=================== sda3: Location of files loaded by Grub: ===================


 173.0GB: boot/grub/menu.lst
 173.0GB: boot/grub/stage2
 173.0GB: boot/initrd.img-2.6.20-16-generic
 173.0GB: boot/initrd.img-2.6.20-16-generic.bak
 174.2GB: boot/initrd.img-2.6.22-14-generic
 174.2GB: boot/initrd.img-2.6.22-14-generic.bak
 143.5GB: boot/initrd.img-2.6.24-22-generic
 182.1GB: boot/initrd.img-2.6.24-22-generic.bak
 144.1GB: boot/initrd.img-2.6.27-9-generic
 173.0GB: boot/vmlinuz-2.6.20-16-generic
 174.1GB: boot/vmlinuz-2.6.22-14-generic
 143.5GB: boot/vmlinuz-2.6.24-22-generic
 176.2GB: boot/vmlinuz-2.6.27-9-generic
 144.1GB: initrd.img
 143.5GB: initrd.img.old
 176.2GB: vmlinuz
 143.5GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

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
default		20

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
# kopt=root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=da116537-e88f-4030-8699-f171575e7f6a

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-19-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-17-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-17-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-14-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-14-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-13-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-13-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		da116537-e88f-4030-8699-f171575e7f6a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-19-generic ...'
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-18-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-18-generic ...'
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-17-generic ...'
	linux	/boot/vmlinuz-2.6.28-17-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-16-generic ...'
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-15-generic ...'
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-14-generic ...'
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-13-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-13-generic ...'
	linux	/boot/vmlinuz-2.6.28-13-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	echo	'Loading Linux 2.6.28-11-generic ...'
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=da116537-e88f-4030-8699-f171575e7f6a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set da116537-e88f-4030-8699-f171575e7f6a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6c4452fe4452ca8a
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 78b6f28a-e237-494e-9168-a3c6b3e3e1df
	linux /boot/vmlinuz-2.6.27-9-generic root=UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df ro quiet splash noapic
	initrd /boot/initrd.img-2.6.27-9-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 78b6f28a-e237-494e-9168-a3c6b3e3e1df
	linux /boot/vmlinuz-2.6.27-9-generic root=UUID=78b6f28a-e237-494e-9168-a3c6b3e3e1df ro single
	initrd /boot/initrd.img-2.6.27-9-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 78b6f28a-e237-494e-9168-a3c6b3e3e1df
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=da116537-e88f-4030-8699-f171575e7f6a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=76b1d0fd-2f52-4649-95b4-512901fd0e9a /home           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=ab109ed7-cc23-4fc5-8cbc-c4a38c90a70a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
  15.5GB: boot/grub/menu.lst
   6.6GB: boot/initrd.img-2.6.28-11-generic
   1.5GB: boot/initrd.img-2.6.28-13-generic
  24.0GB: boot/initrd.img-2.6.28-14-generic
   5.3GB: boot/initrd.img-2.6.28-15-generic
   5.4GB: boot/initrd.img-2.6.28-16-generic
   5.8GB: boot/initrd.img-2.6.28-17-generic
  10.7GB: boot/initrd.img-2.6.28-18-generic
  17.3GB: boot/initrd.img-2.6.28-19-generic
    .6GB: boot/initrd.img-2.6.32-21-generic
    .7GB: boot/initrd.img-2.6.32-22-generic
   6.5GB: boot/vmlinuz-2.6.28-11-generic
   3.8GB: boot/vmlinuz-2.6.28-13-generic
   8.4GB: boot/vmlinuz-2.6.28-14-generic
   4.9GB: boot/vmlinuz-2.6.28-15-generic
   4.9GB: boot/vmlinuz-2.6.28-16-generic
   6.2GB: boot/vmlinuz-2.6.28-17-generic
   6.3GB: boot/vmlinuz-2.6.28-18-generic
   7.6GB: boot/vmlinuz-2.6.28-19-generic
    .2GB: boot/vmlinuz-2.6.32-21-generic
   1.9GB: boot/vmlinuz-2.6.32-22-generic
    .7GB: initrd.img
    .6GB: initrd.img.old
   1.9GB: vmlinuz
    .2GB: vmlinuz.old
```


Any insight that this may bring is appreciated.

---

### Post by Alpinist on 2010-06-22
Don, tried your suggestion of renaming the grub.cfg and running the update again but no go.  The problem isn't that there are incorrect entries in the list, it is that I cannot move the cursor to select anything.  It just keeps popping back up to the top.

---

### Post by Don Barzini on 2010-06-22
> **Alpinist said:**
> Don, tried your suggestion of renaming the grub.cfg and running the update again but no go.  The problem isn't that there are incorrect entries in the list, it is that I cannot move the cursor to select anything.  It just keeps popping back up to the top.

You have a USB keyboard? Is this correct?

Have you tried adjusting or looking at the USB settings in your system BIOS? If you have an option for USB legacy support.... try "enabling" that and see if it works.

I originally mistook your problem for something else. I did a quick Google search for "Grub2 keyboard problem" and the results are mixed. They vary from BIOS settings.... to changing back to a PS/2 keyboard..... to dumping GRUB2 and installing legacy GRUB.

Maybe also shut off your machine and change the USB ports for your keyboard and mouse. I had a weird problem with another OS (FreeBSD 8.0) and their new USB stack that prevented the OS from loading. I know it is weird, but changing the USB ports for the input devices worked for that particular problem.

Good Luck.

---

### Post by Alpinist on 2010-06-22
Not using a USB keyboard, it is PS2.  I had found a post similar to what you mention about the bios but not my issue as not only is it not USB but works perfectly with the old grub and the windows bootloader.
I'm not against using legacy grub but that would mean that grub2 is a buggy unstable failure.  I'm hoping I can get the newer technology to work.

---

### Post by Don Barzini on 2010-06-22
> **Alpinist said:**
> I'm not against using legacy grub but that would mean that grub2 is a buggy unstable failure.  I'm hoping I can get the newer technology to work.

Reverting back to Legacy GRUB would probably solve your problem.

Keep backup copies of your current grub.cfg and the old menu.lst files. You also have the info here if you need it for reference.

Legacy GRUB is still a great boot loader. Sometimes the older girl at the party is the better dance partner. :)

Good Luck Alpinist.

---

### Post by Alpinist on 2010-06-23
I tried a little more with grub2, reinstall, reconfigure, and getting the same problem every time.  Cannot select anything except the top option in the menu.

Followed the instructions to reinstall grub legacy and it works exactly as expected.

I have a solution that works and I am happy with it but I am not going to mark this as solved.

The Rant:  I think grub2 is broken.  I have been using Ubuntu for three years, since 2007, and Linux a couple years prior to that.  I have used both Lilo and Grub and until this grub2 experience have not had any issues with boot loaders at all.
The most important feature of a bootloader is that it is reliable and stable, that it boots your operating systems.  All other features are fluff and completely secondary to reliability and stability.  I fully support trying to add new features and make if more powerful but only if it is a rock solid product. This is the very basis of being able to run your OS.  I believe it was a huge mistake for Canonical to choose this obviously not well tested product to put into production.  I know at this point they will say we have made our decision and are sticking with it and that is a stupid decision.  Stability and reliability are necessities in boot loaders.
I have not found my exact issue in searches, though I have found a lot of posts of people with other issues with grub2.  My problem would only be noticed by people who dual boot or have a reason to boot into other versions of the kernel (such as having a real time kernel) so it is very likely the problem is more widespread than just one person.

Anyway, I do appreciate the advice I've received and do have other options that work for me so this isn't a major issue.  I just think certain types of updates need to be a lot more carefully assessed than others.  Boot loader is a lot more important than what version of window manager you are going to use, even though that will receive a lot more feedback.

---

### Post by oldfred on 2010-06-24
Do not assume it is not a BIOS issue just because windows or Ubuntu work. Grub2 as an update reads the BIOS that old grub did not. So it may be complying with the BIOS settings that you have set even though all the other applications are not. 

I had that problem but with a USB keyboard & mouse about a year ago when I installed a new motherboard and it was the BIOS settings.

---

### Post by armyofgayunicorns on 2011-01-19
It's beginning to bother me just how much time I'm having to spend working with the terminal in ubuntu. I don't personally mind using a terminal rather than a gui, but the whole point of ubuntu is that it's supposed to "just work", that it should be working towards being a viable alternative to windows or mac os that anyone can use.

I've convinced quite a few people to start using ubuntu when they've told me about problems with their computer, explained that these are problems with windows rather than the computer itself, and for gods sake no, don't go and buy a new computer, you're going to get an even more badly made version of windows with it and you'll be paying for a load of technology you'll never need.

Thankfully none of the people I've helped set up ubuntu so far have been gamers, as I would've configured a dual boot for them so they still had a windows partition to run games easily, I can guarantee a less experienced computer user faced with this problem would've simply given up, stuck their restore disk in the drive and gone back to using windows.

If I wasn't the only user of this computer I would have already started using a more versatile linux distro and built it specifically for my needs, by my girlfriend also uses it and her daughter is going to be using it more often now under supervision, this is why I have stuck with ubuntu, as it's intended to be the most user friendly linux distro for everyday computer users.

If I'm going to have to spend so much time manually fixing things through the command terminal, I may as well switch to the basic distribution of debian and build the os myself from the ground up, this version of grub should not have been packaged with ubuntu until it was thoroughly tested to ensure this sort of thing doesn't happen.

In case you couldn't tell, I've just realised after a fresh install that I now can't move through the OS selections on grub either, which means that rather than chilling out playing burnout paradise for a bit with some death metal cranked up so loud my deaf neighbour will be able to tell what band it is from the vibrations in his kneecaps, I now have to try and fix this.

Rant over, this is the first time anything about ubuntu has pissed me off to the extent of actually complaining about it online, though it would be nice if support for my tuner card (dm1105 chipset) would be sorted out, as it was trying to get that working that led to me needing to resort to a fresh install to begin with.

Don't mean to be too harsh, I realise ubuntu is community maintained and issues can only be ironed out as and when they are reported, and if I had the time in my life to learn a bit about coding I would make more of a contribution myself. Keep up the good work, peace.

---

### Post by armyofgayunicorns on 2011-01-19
-

---

### Post by armyofgayunicorns on 2011-01-19
erm, might have to partially apologise for some of my rant there, while  there may well be issues with grub2, i noticed just now when i was  showing a friend how to boot ubuntu from a cd so she could bypass the  absurdly restrictive filters at her local library that i couldn't do  anything with my bios at all.

 I then checked and found that the keyboard was plugged into the mouse  port, so ubuntu was happy to recognise it as a keyboard but the bios and  grub didn't. I'd unplugged everything intending to take the tower apart  to put thermal paste inbetween the processor and heatsink, got  distracted by something else, and my girlfriend plugged everything in  again. Not her fault cos it was me who told her it's basically  impossible to plug things into the wrong port cos they'll be the wrong  shape to fit in to it, everything that is except the keyboard and mouse ports.

So yeah, maybe if you have problems with your bootloader, make sure your keyboard is plugged into the right port?

It's always good to have an old ps2 keyboard kicking around anyway, just  in case something goes wrong and your bios won't recognise a usb  keyboard, so you can actually get into the bios to fix it.

---

