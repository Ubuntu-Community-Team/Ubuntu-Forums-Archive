---
title: "Dual boot stopped working"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Dilbert_ on 2010-08-17
I'm a huge fan of Linux (although still a noob) but require Windows for work.  I have a laptop for work on which I was dual-booting  XP and Ubuntu.  After a few boots, XP will no longer start.

Originally the notebook had a windows partition and a Dell Recovery partition.  I used gparted to carve out a partition for Ubuntu from the windows space and I made a dedicated GRUB partition right in the front of the disk because my BIOS couldn't boot from LBAs.  

Now, the computer boots into grub. From their I can either load the ubuntu kernel from its partition or I can chainload to the ubuntu partition which loads the local copy of grub. I even went so far as to make entries in the menu.lst files so that you can navigate back and forth between grub on the boot partition and grub on the ubuntu partition.  On the boot partitions grub, I also made an entry to chainload windows from its partition.  And then I edited the boot.ini in Windows to allow me to go back to the grub menu on the boot partition. (I need to create a bin image of the boot sector for that)

Anyway, I followed lots of instructions that I cobbled together from googling.  Everything was working fine for a few days. Seemed I could move back and forth between "boot grub", "ubuntu grub", and windows bootloader.  Both OS's were working fine.  Then, somehow, XP stopped working.

I tried using super grub disk, but this only gets me into Ubuntu.

Basically, Grub sets the root to the appropriate partition, chainloads, and then thats it.  Nothing.  It's like theirs no IPL on the windows partition. But I used testdisk to check the partition and it has a valid bootsector.  Also, I can still mount it in 
Ubuntu and look at my windows files.  Seems like NTloader never starts but I don't get any error messages. After the grub commands echo, I get nothing.

I've also made a bootable USB key with Windows Revovery Console on it.  I wanted to use it to fix the windows partition and make it bootable again. However, the recovery console never starts up. I get the blue screen of death and I think it's because it doesn't know what to make of the Ext formated partitions.

```

 fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ba14190

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  83  Linux
/dev/sda2   *           7       20762   166722570    7  HPFS/NTFS
/dev/sda3           20763       29944    73754415    f  W95 Ext'd (LBA)
/dev/sda4           29945       30401     3670852+   c  W95 FAT32 (LBA)
/dev/sda5           20763       29566    70718098+  83  Linux
/dev/sda6           29567       29944     3036253+  82  Linux swap / Solaris


``````
Relevent lines in grubs menu.lst

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Bootloader
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1
``````
Contents of Windows Boot.ini
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
c:\ubuntu_loader.bin="Go to Ubuntu GRUB Loader"
```I have spent countless hours trying to rectify this. I can see files on the XP partition but I can not boot it by any means. 

If anybody has any ideas, please help me, and thanks in advance.

---

### Post by presence1960 on 2010-08-17
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Dilbert_ on 2010-08-18
Here's the results file. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 28487 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_loader.bin looks at sector 
                       28487 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_boot.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_loader.bin looks at sector 
                       28487 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ba14190

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  83 Linux
/dev/sda2    *         96,390   333,541,529   333,445,140   7 HPFS/NTFS
/dev/sda3         333,541,530   481,050,359   147,508,830   f W95 Ext d (LBA)
/dev/sda5         333,541,593   474,977,789   141,436,197  83 Linux
/dev/sda6         474,977,853   481,050,359     6,072,507  82 Linux swap / Solaris
/dev/sda4         481,050,360   488,392,064     7,341,705   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2f7c5253-7c0c-4e26-ab81-5f70b05550d8   ext2       Boot                          
/dev/sda2        EC6CD86D6CD83454                       ntfs                                     
/dev/sda4        0000-0000                              vfat       DellRestore                   
/dev/sda5        b668adfe-9546-4d08-8df9-b1b4fd8f9b59   ext3                                     
/dev/sda6        3cd0725c-45c1-4bb7-8d3f-c6560425c855   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/Boot              ext2       (rw,nosuid,nodev,uhelper=hal)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        You are at /media/Boot/boot/grub/menu.lst
root

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-28-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Bootloader
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1
boot



=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.24-26-generic
    .0GB: boot/initrd.img-2.6.24-27-generic
    .0GB: boot/initrd.img-2.6.24-28-generic
    .0GB: boot/vmlinuz-2.6.24-26-generic
    .0GB: boot/vmlinuz-2.6.24-27-generic
    .0GB: boot/vmlinuz-2.6.24-28-generic

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
c:\ubuntu_loader.bin="Go to Ubuntu GRUB Loader"


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
default        saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=splash

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
# howmany=3

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro splash
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-28-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
root        (hd0,1)
savedefault
chainloader    +1
boot



=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3cd0725c-45c1-4bb7-8d3f-c6560425c855 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 224.8GB: boot/grub/menu.lst
 224.8GB: boot/grub/stage2
 224.7GB: boot/initrd.img-2.6.24-26-generic
 224.7GB: boot/initrd.img-2.6.24-27-generic
 224.8GB: boot/initrd.img-2.6.24-27-generic.bak
 224.7GB: boot/initrd.img-2.6.24-28-generic
 224.7GB: boot/initrd.img-2.6.24-28-generic.bak
 224.7GB: boot/vmlinuz-2.6.24-26-generic
 224.7GB: boot/vmlinuz-2.6.24-27-generic
 224.8GB: boot/vmlinuz-2.6.24-28-generic
 224.7GB: initrd.img
 224.7GB: initrd.img.old
 224.8GB: vmlinuz
 224.7GB: vmlinuz.old

```

---

### Post by oldfred on 2010-08-18
You still have to keep the windows boot loader in the windows partition.

sda2: ___

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     [COLOR=Red]Grub 0.97 in the file [/COLOR]/ubuntu.bin 

You can have grub legacy in all the other partitions and chainload but windows has essential files in its boot sector (PBR)

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If the backup is still vaild you can use this to restore the boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If not you will have to use the windows XP disk and run fixboot.

Grub2 does not like to be installed to partitions, so with your current method I would not suggest upgrading to grub2. Grub2 I still think is better but requires changes in how you boot and in your case some extra planning.

---

### Post by Dilbert_ on 2010-08-18
Yep, we are on the same page. But my problems not solved.
 
I have been assuming (although now it's verified) that the problem was with the Windows boot loader.  But I've already used testdisk. I've had it rebuild the boot sector. (And the backup matches.) So my problem is not just the first sector where all the boot parameters are, it seems to be the rest of the bootloader.  I'm afraid to mess with the next sectors because I believe that's where the partition and file location information is. Right now, I can still see my files, and I don't want to screw that up.
 
The boot info script is detecting ubuntu.bin as the bootloader but I don't believe that is entirely correct.  If you look in the boot.ini, you can see an option there to go back to the grub bootloader from windows bootloader.  This requires making a bin file of the bootsector and pointing to it in the ini. The boot info script is detecting the bin files (I made more than one) I made of the linux boot sector. Right now, I'm wishing I had made one for windows too. (Although, I have compared the first 512 bytes and its a perfect match for a defacto NTFS boot sector.  Only the pertinent information regarding my specific harddrive is adjusted.)
 
Anyway, when I run the XP recover console from USB key or from DVD I starts up normally but crashes on the blue screen of death when it scans the HDD for OS's.
 
If I could get to a prompt to run Fixboot, I'd be okay. You seem to know readily what took me days to research, so if you have any more ideas I'd love to here them. I appreciate your help.

---

### Post by oldfred on 2010-08-18
If you used testdisk to rebuild the boot sector for windows it should not be showing grub in the PBR. Or did you do that after running the boot info script.


I do not understand why you cannot at least get a windows repair CD or USB to boot. Are they set up correctly? Have you tried them on another computer as a test?

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this command .

FIXBOOT  C:

---

### Post by Dilbert_ on 2010-08-18
Okay. I don't think grub is in the boot sector of the windows partition. Please look closely at the results of the boot info script. I copied the boot sector of my linux partitions to bin files so that I could reference them in the windows boot.ini file. This lets the windows bootloader chainload grub.
 
In blue: ubuntu.bin chainloads grub on partition 5 which is my Ubuntu.
In purple: ubuntu_loader.bin chainloads grub on partition 1 which is my dedicated grub boot partition.
In green: the required windows boot files
 
```
sda2: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     [COLOR=blue]Grub 0.97 in the file /ubuntu.bin looks at sector [/COLOR]
[COLOR=blue]                      439120089 of the same hard drive for the stage2 file. [/COLOR]
[COLOR=blue]                      A stage2 file is at this location on /dev/sda. Stage2 [/COLOR]
[COLOR=blue]                      looks on partition #5 for /boot/grub/menu.lst.[/COLOR] [COLOR=purple]Grub [/COLOR]
[COLOR=purple]                      0.97 in the file /ubuntu_loader.bin looks at sector [/COLOR]
[COLOR=purple]                      28487 of the same hard drive for the stage2 file. A [/COLOR]
[COLOR=purple]                      stage2 file is at this location on /dev/sda. Stage2 [/COLOR]
[COLOR=purple]                      looks on partition #1 for /boot/grub/menu.lst.[/COLOR]
    Operating System:  
    Boot files/dirs:   **[COLOR=seagreen]/BOOT.INI /NTLDR /NTDETECT.COM[/COLOR]**
 

```
 
If you check the Boot.ini file, you can see that the windows bootloader gives the user 2 choices. "Microsoft Windows XP Professional" and "Go to Ubuntu GRUB Loader". The ladder choice chainloads ubuntu_loader.bin which takes you to the grub menu on the boot partition. The other bin file is not used. It's left over from testing/learning.
 
```
================================ sda2/BOOT.INI: ================================
 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
c:\ubuntu_loader.bin="Go to Ubuntu GRUB Loader"

```
 
Other than the two ubuntu*.bin files, should something else be showing in the "Boot file info:" from the boot info script? I get the impression your expecting to see something else there.
 
As for Recovery Console, I get the failure as described below. However, I get it on multiple computers which leads me to question the integrity of my recovery console ISO. Anybody know a good download link?
 
```
 
I get a boot message followed by 
"Setup is inpecting your computers hardware configuration"
 
This quickly switches to the blue "Windows setup" screen and it 
shows lots of files being loaded in the white status bar at the bottom.  
 
Then it says "Setup is Starting Windows" and viola, blue screen of death.
 
A problem has been detected and windows has been shut down
 to prevent damage to your computer.
 
If this is the first time you've seen this Stop error screen, restart 
your computer. If this screen appears again, follow these steps:
 
Check for viruses on your computer. Remove any newly installed 
hard drives or hard drive controllers. Check your hard drive to 
make sure it is properly configured and terminated.  
Run CHKDSK /F to check for hard drive corruption, and then 
restart your computer.
 
Technical Information:
*** STOP: 0x0000007B (0xF7C8263C,0xC0000034,0x00000000,0x00000000)

```

---

### Post by oldfred on 2010-08-18
Go back to my link to multibooters to understand how windows boots. You have to have a windows boot loader in the PBR or boot sector as that is what calls the loading of the boot files.

It should look like mine:

sda1: _______________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


Windows may see the grub in the PBR as a virus:
[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

---

### Post by presence1960 on 2010-08-18
I agree with oldfred. 

In my opinion there is no need to have all that acrobatic stuff you did to get windows & ubuntu to boot. If you needed a separate boot partition to boot ubuntu because of a limitation of your BIOS reading the disk past a certain point- that is fine. But all that other crap you did is unnecessary. A simple install of GRUB Legacy 0.97 and possibly an edit of the menu.lst to add/fix a windows entry is all that is necessary. In the very wise words of 12 step groups: Keep it simple!

---

