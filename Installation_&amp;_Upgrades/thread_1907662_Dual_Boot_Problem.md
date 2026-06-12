---
title: "Dual Boot Problem"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by lrobinson378 on 2012-01-11
I have been running a win XP/Ubuntu system for several years and never had a problem with dualbooting. I recently updated my Ubuntu 11.04 system and I saw I could upgrade to 11.10, so I did. All went well until I restarted the system and when I got the boot menu Windows XP was gone. What do I have to do to get it back? How do I figure out where Windows is located? I don't remember how it was called from the menu.
Thanks,
Lee

---

### Post by leclerc65 on 2012-01-11
Try running
 sudo update-grub

---

### Post by adityamagadi on 2012-01-11
try holding down the shift key or keep pressing the down arrow as soon as u boot ur system ..

---

### Post by Mark Phelps on 2012-01-12
You don't need to know where Windows is installed anymore.

Post #2 provided you the command to run.  It will scan your PC for Linux kernels and other (Windows) OSs and regenerate the GRUB default menu to include entries for those.

When the command runs, you can see it finding such items.

When you reboot, you will automatically get a new GRUB menu.

---

### Post by lrobinson378 on 2012-01-12
Hi, I ran "sudo update-grub" and watched find several versions of linux and memtest but it didn't find win XP. I ran GParted and found two NTFS partitions one of which has a boot flag. it is located at /dev/sda1. My guess is that is where Windows is or was. A little of half of the 43.27gb of the partition is used. Any suggestions? :(

---

### Post by darkod on 2012-01-12
Lets not guess. Follow the link in my signature and run the boot info script. Post the results as explained. It will show more details.

---

### Post by lrobinson378 on 2012-01-13
I agree, let's not guess. I've been doing that to no avail. Here are the results from the boot script:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for .
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  
    Operating System:  Ubuntu 6.06.1 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    90,735,119    90,735,057   7 NTFS / exFAT / HPFS
/dev/sda2          90,735,181   349,526,204   258,791,024   f W95 Extended (LBA)
/dev/sda5          90,735,183   346,457,789   255,722,607   7 NTFS / exFAT / HPFS
/dev/sda6         346,457,853   349,526,204     3,068,352  82 Linux swap / Solaris
/dev/sda3         419,055,525   490,223,474    71,167,950   c W95 FAT32 (LBA)
/dev/sda4         349,526,205   419,055,524    69,529,320  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    72,629,864    72,629,802   7 NTFS / exFAT / HPFS
/dev/sdb2          72,629,865   103,297,949    30,668,085  83 Linux
/dev/sdb3         103,378,275   103,587,119       208,845  83 Linux
/dev/sdb4         103,587,181   234,440,703   130,853,523   f W95 Extended (LBA)
/dev/sdb5         103,587,183   166,231,777    62,644,595  82 Linux swap / Solaris
/dev/sdb6         166,232,064   231,544,831    65,312,768  83 Linux
/dev/sdb7         231,546,880   234,440,703     2,893,824  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        88FC1BEDFC1BD472                       ntfs       
/dev/sda3        D727-D727                              vfat       NEW_OS
/dev/sda4        230256d1-3582-4952-820b-3e32528884e9   ext3       
/dev/sda5        F070AEA170AE6E52                       ntfs       
/dev/sda6        e8b161b1-c375-419a-82aa-65c7d02eda4c   swap       
/dev/sdb1        E850A0CE50A0A532                       ntfs       Linux
/dev/sdb2        c23003df-c599-432c-97c1-2cdee532cb9d   ext2       
/dev/sdb3        27d0d4b0-1acd-42a6-9a81-d1df5649f327   ext2       
/dev/sdb5        9552c7d2-1a5a-4bbb-aae3-5707f8ef679d   swap       
/dev/sdb6        c33175a6-1875-430e-bafe-0b4f1981c38f   ext4       
/dev/sdb7        ae759eeb-10ef-41b3-9847-8de2569b7a24   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda4/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
timeout		20

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
# kopt=root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
initrd		/boot/initrd.img-2.6.24-26-generic


# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-25-generic
# quiet

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
# initrd		/boot/initrd.img-2.6.24-25-generic

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-24-generic
# quiet

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
# initrd		/boot/initrd.img-2.6.24-24-generic

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-23-generic
# quiet

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
# initrd		/boot/initrd.img-2.6.24-23-generic

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-22-generic
# quiet

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
# initrd		/boot/initrd.img-2.6.24-22-generic

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-21-generic
# quiet

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
# initrd		/boot/initrd.img-2.6.24-21-generic

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-19-generic
# quiet

# title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
# initrd		/boot/initrd.img-2.6.24-19-generic

# title		Ubuntu 8.04.3 LTS, kernel 2.6.22-15-generic
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
# initrd		/boot/initrd.img-2.6.22-15-generic
# quiet

# title		Ubuntu 8.04.3 LTS, kernel 2.6.22-15-generic (recovery mode)
# root		(hd0,3)
# kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
# initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-29-386 (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash 
## initrd		/boot/initrd.img-2.6.15-29-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single 
## initrd		/boot/initrd.img-2.6.15-29-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash 
## initrd		/boot/initrd.img-2.6.15-28-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single 
## initrd		/boot/initrd.img-2.6.15-28-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-27-386 (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash 
## initrd		/boot/initrd.img-2.6.15-27-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single 
## initrd		/boot/initrd.img-2.6.15-27-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-26-386 (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash 
## initrd		/boot/initrd.img-2.6.15-26-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single 
## initrd		/boot/initrd.img-2.6.15-26-386
## savedefault
## boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
## title		Ubuntu, memtest86+ (on /dev/sdb2)
## root		(hd1,1)
## kernel		/boot/memtest86+.bin  
## savedefault
## boot

--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=230256d1-3582-4952-820b-3e32528884e9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=e8b161b1-c375-419a-82aa-65c7d02eda4c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.22-15-generic              3
               =                boot/initrd.img-2.6.22-15-generic.bak          3
               =                boot/initrd.img-2.6.24-19-generic              3
               =                boot/initrd.img-2.6.24-19-generic.bak          4
               =                boot/initrd.img-2.6.24-21-generic              7
               =                boot/initrd.img-2.6.24-21-generic.bak          3
               =                boot/initrd.img-2.6.24-22-generic              4
               =                boot/initrd.img-2.6.24-22-generic.bak          4
               =                boot/initrd.img-2.6.24-23-generic              5
               =                boot/initrd.img-2.6.24-23-generic.bak          4
               =                boot/initrd.img-2.6.24-24-generic              5
               =                boot/initrd.img-2.6.24-24-generic.bak          8
               =                boot/initrd.img-2.6.24-25-generic              4
               =                boot/initrd.img-2.6.24-25-generic.bak          5
               =                boot/initrd.img-2.6.24-26-generic              4
               =                boot/initrd.img-2.6.24-26-generic.bak         11
               =                boot/initrd.img-2.6.24-27-generic              3
               =                boot/initrd.img-2.6.24-27-generic.bak          5
               =                boot/initrd.img-2.6.24-28-generic              5
               =                boot/initrd.img-2.6.24-28-generic.bak          9
               =                boot/vmlinuz-2.6.22-15-generic                 2
               =                boot/vmlinuz-2.6.24-19-generic                 2
               =                boot/vmlinuz-2.6.24-21-generic                 3
               =                boot/vmlinuz-2.6.24-22-generic                 3
               =                boot/vmlinuz-2.6.24-23-generic                 3
               =                boot/vmlinuz-2.6.24-24-generic                 2
               =                boot/vmlinuz-2.6.24-25-generic                 4
               =                boot/vmlinuz-2.6.24-26-generic                 3
               =                boot/vmlinuz-2.6.24-27-generic                 7
               =                boot/vmlinuz-2.6.24-28-generic                 5
               =                initrd.img                                     5
               =                initrd.img.old                                 3
               =                vmlinuz                                        5
               =                vmlinuz.old                                    7

=========================== sdb2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       /media/hda3     ext2    defaults        0       2
/dev/hdb1       /media/hdb1     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,unmask-000  0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.15-26-386                  4
               =                boot/initrd.img-2.6.15-27-386                  3
               =                boot/initrd.img-2.6.15-28-386                 15
               =                boot/initrd.img-2.6.15-29-386                 23
               =                boot/vmlinuz-2.6.15-26-386                     2
               =                boot/vmlinuz-2.6.15-27-386                    10
               =                boot/vmlinuz-2.6.15-28-386                    10
               =                boot/vmlinuz-2.6.15-29-386                     2
               =                initrd.img                                    23
               =                initrd.img.old                                15
               =                vmlinuz                                        2
               =                vmlinuz.old                                   10

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos6)'
  search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 230256d1-3582-4952-820b-3e32528884e9
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 230256d1-3582-4952-820b-3e32528884e9
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 230256d1-3582-4952-820b-3e32528884e9
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-28-386
}
menuentry "Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-28-386
}
menuentry "Ubuntu, kernel 2.6.15-27-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-26-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-26-386
}
menuentry "Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-26-386
}
menuentry "Ubuntu, memtest86+ (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=c33175a6-1875-430e-bafe-0b4f1981c38f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=ae759eeb-10ef-41b3-9847-8de2569b7a24 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-13-generic              2
               =                boot/initrd.img-3.0.0-14-generic               3
               =                boot/vmlinuz-2.6.38-13-generic                 1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     3
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  5e ff 77 ff 96 ff b4 ff  d3 ff e6 ff fb ff 13 00  |^.w.............|
00000010  30 00 44 00 52 00 5d 00  67 00 75 00 7c 00 84 00  |0.D.R.].g.u.|...|
00000020  86 00 8a 00 87 00 84 00  80 00 76 00 70 00 65 00  |..........v.p.e.|
00000030  5a 00 56 00 44 00 33 00  21 00 11 00 02 00 f2 ff  |Z.V.D.3.!.......|
00000040  de ff ca ff b2 ff a4 ff  92 ff 84 ff 79 ff 66 ff  |............y.f.|
00000050  56 ff 4c ff 42 ff 39 ff  34 ff 33 ff 30 ff 34 ff  |V.L.B.9.4.3.0.4.|
00000060  3c ff 41 ff 47 ff 52 ff  5e ff 72 ff 87 ff 93 ff  |<.A.G.R.^.r.....|
00000070  a4 ff b1 ff c2 ff d4 ff  e6 ff fe ff 0e 00 21 00  |..............!.|
00000080  32 00 43 00 4b 00 57 00  64 00 6d 00 73 00 79 00  |2.C.K.W.d.m.s.y.|
00000090  79 00 7b 00 81 00 87 00  87 00 87 00 83 00 7e 00  |y.{...........~.|
000000a0  75 00 6d 00 68 00 60 00  52 00 48 00 36 00 2c 00  |u.m.h.`.R.H.6.,.|
000000b0  1c 00 09 00 fb ff ed ff  d8 ff c8 ff b4 ff a4 ff  |................|
000000c0  96 ff 8a ff 7f ff 77 ff  66 ff 60 ff 55 ff 55 ff  |......w.f.`.U.U.|
000000d0  50 ff 56 ff 55 ff 60 ff  61 ff 77 ff 7f ff 93 ff  |P.V.U.`.a.w.....|
000000e0  ca ff 56 00 df ff c1 00  9f 00 ca 00 7f 01 ec 01  |..V.............|
000000f0  d3 01 43 02 d6 02 76 02  27 03 48 03 46 03 0a 03  |..C...v.'.H.F...|
00000100  d2 03 0a 03 20 03 04 03  9e 02 4a 02 5d 02 ec 01  |.... .....J.]...|
00000110  69 01 47 01 b8 00 95 00  5d 00 14 00 e4 ff b1 ff  |i.G.....].......|
00000120  44 ff 63 ff 12 ff 1d ff  d8 fe e5 fe 92 fe 88 fe  |D.c.............|
00000130  6c fe 29 fe 0a fe b6 fd  9d fd 4c fd 31 fd 82 fc  |l.).......L.1...|
00000140  8c fc 12 fc e8 fb b3 fb  8f fb 0b fb e7 fa 01 fb  |................|
00000150  ac fa c3 fa b2 fa ba fa  be fa ea fa 06 fb 38 fb  |..............8.|
00000160  39 fb cd fb d0 fb 4d fc  6d fc cf fc 0a fd 5e fd  |9.....M.m.....^.|
00000170  dc fd 1b fe 81 fe c6 fe  37 ff 47 ff 22 00 2c 00  |........7.G.".,.|
00000180  be 00 01 01 6a 01 b2 01  2a 02 8a 02 b6 02 31 03  |....j...*.....1.|
00000190  51 03 c1 03 d1 03 0a 04  03 04 30 04 44 04 38 04  |Q.........0.D.8.|
000001a0  23 04 f6 03 a8 03 a1 03  61 03 16 03 c8 02 6e 02  |#.......a.....n.|
000001b0  17 02 ba 01 7d 01 12 01  d7 00 6d 00 4e 00 00 01  |....}.....m.N...|
000001c0  c1 fe 07 fe ff ff 02 00  00 00 6f 04 3e 0f 00 fe  |..........o.>...|
000001d0  ff ff 05 fe ff ff 71 04  3e 0f ff d1 2e 00 00 00  |......q.>.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda3

00000000  eb 58 90 4f 45 4d 4e 41  4d 45 20 00 02 20 20 00  |.X.OEMNAME ..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 a5 47 fa 18  |........?....G..|
00000020  ce ef 3d 04 d7 43 00 00  00 00 00 00 02 00 00 00  |..=..C..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 27 d7 27 d7 4e  45 57 5f 4f 53 20 20 20  |..)'.'.NEW_OS   |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb4

00000000  e8 ee 8f f3 12 c0 0a 78  76 c2 f3 c3 40 ec 2b 59  |.......xv...@.+Y|
00000010  62 47 40 fe 8c 8e 71 c4  a0 25 ab 74 18 cc 35 e1  |bG@...q..%.t..5.|
00000020  41 06 f8 20 dd cc 38 85  b6 1a 9d bc 8c 87 59 f0  |A.. ..8.......Y.|
00000030  1a 18 13 6e b0 f9 9a 1a  82 4e ef 83 53 2e 74 fa  |...n.....N..S.t.|
00000040  4d 55 41 b7 8d d7 d8 6c  53 d3 3b 41 a7 62 e8 5f  |MUA....lS.;A.b._|
00000050  bf 9c e7 7b b1 e9 e5 a0  db 7f c0 ed 18 ba 29 41  |...{..........)A|
00000060  b7 63 e0 76 b2 c8 f7 a2  77 8d 70 88 bd ca 23 7a  |.c.v....w.p...#z|
00000070  1f 63 2a 2a 73 5b 83 c6  86 72 9a 91 e8 7f e3 dc  |.c**s[...r......|
00000080  fc 24 a6 b2 32 af 8f 99  17 45 af 03 e8 35 54 b8  |.$..2....E...5T.|
00000090  ff 10 21 06 c9 97 1b 7a  bb 91 5e ef 4d c3 eb 86  |..!....z..^.M...|
000000a0  15 c0 4e 8f 47 21 3b 95  7a 72 89 be 24 fb 95 74  |..N.G!;.zr..$..t|
000000b0  09 02 b6 e0 b6 73 3e b4  e2 87 13 3e ff 5b 08 cb  |.....s>....>.[..|
000000c0  95 0e 62 6a 1b ed de 1d  a5 5c 33 fd ca c4 ed 8b  |..bj.....\3.....|
000000d0  ed c5 65 a6 a6 33 20 2f  bd a7 02 36 b1 5c 55 0d  |..e..3 /...6.\U.|
000000e0  59 b8 fb b5 41 99 77 42  99 77 4a 99 77 46 99 47  |Y...A.wB.wJ.wF.G|
000000f0  3b 6c bc 8b bf 27 c8 0c  ad cc 26 4d d4 a6 72 94  |;l...'....&M..r.|
00000100  4c e1 5e 95 a9 ea 12 89  03 fa 74 2e 9f d9 f4 87  |L.^.......t.....|
00000110  de 5a c6 19 3f 00 09 1a  88 37 74 30 70 04 3c 7f  |.Z..?....7t0p.<.|
00000120  82 a7 12 9e a3 f0 fc 08  4f e7 21 29 d2 ba 21 3c  |........O.!)..!<|
00000130  cc 51 e1 fe 8d f8 f6 3f  cd 43 b8 2a 18 01 02 70  |.Q.....?.C.*...p|
00000140  74 84 a3 0f 2b cf 36 da  70 05 97 07 a9 d8 dd b7  |t...+.6.p.......|
00000150  bd 0d 98 e1 75 7e 5a 9f  7e ec e3 7b 37 99 4f dd  |....u~Z.~..{7.O.|
00000160  73 e0 f3 b4 f0 79 ea 3c  d3 00 fc 7e ef a3 df 4a  |s....y.<...~...J|
00000170  0d 0e 2b ce a0 f7 7a c4  09 af 1e fa c8 d9 10 14  |..+...z.........|
00000180  65 18 6c bc 40 91 0d 9d  2e a8 37 a8 7b 09 ef e5  |e.l.@.....7.{...|
00000190  20 c9 9a 06 32 2c a7 d8  dc 3d 1a fb 99 7c 4a f8  | ...2,...=...|J.|
000001a0  6e 81 86 da 64 64 07 6e  d1 73 0c 33 1f 23 fc 86  |n...dd.n.s.3.#..|
000001b0  21 e2 16 a1 ff de 7d 4e  55 07 c7 c8 e1 d0 00 fe  |!.....}NU.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 73 e1 bb 03 00 fe  |..........s.....|
000001d0  ff ff 05 fe ff ff 75 e1  bb 03 1e 99 e4 03 00 00  |......u.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

I thought grub.cfg might be useful as well so here it is:
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos6)'
  search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=c33175a6-1875-430e-bafe-0b4f1981c38f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root c33175a6-1875-430e-bafe-0b4f1981c38f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 230256d1-3582-4952-820b-3e32528884e9
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro quiet splash
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 230256d1-3582-4952-820b-3e32528884e9
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=230256d1-3582-4952-820b-3e32528884e9 ro single
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 230256d1-3582-4952-820b-3e32528884e9
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-28-386
}
menuentry "Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-28-386
}
menuentry "Ubuntu, kernel 2.6.15-27-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-27-386
}
menuentry "Ubuntu, kernel 2.6.15-26-386 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.15-26-386
}
menuentry "Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.15-26-386
}
menuentry "Ubuntu, memtest86+ (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root c23003df-c599-432c-97c1-2cdee532cb9d
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

Thanks for your help,
Lee

---

### Post by darkod on 2012-01-13
```

sda1: __________________________________________________  ________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ntldr /NTDETECT.COM

```

You are missing the boot.ini file for XP. Since you have XP on the first partition on the first disk, a generic boot.ini should do the job.

Look at this post and there is an attached archive with all three XP boot files. Extract them and copy only boot.ini to /dev/sda1.
[http://ubuntuforums.org/showpost.php?p=5082723&postcount=1](http://ubuntuforums.org/showpost.php?p=5082723&postcount=1)

Run sudo update-grub after that and see if it finds it, and if it can boot it.

---

### Post by lrobinson378 on 2012-01-14
:popcorn:YEAH!! That solved the problem. Thank you so much for your help.
Lee :D

---

