---
title: "No bootable sector found"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Cyclops_ on 2010-05-02
I just did an update to Lucid from Karmic a couple of days ago.  It broke my grub.  I *was* getting the whole "grub_puts_" symbol not found.  

Using the Ultimate Boot CD I could do nothing.  I could not boot into anything (it has on it the Super Grub Bootloader or whatever that's called as well as GAG and a host of other tools, none of which could help me).

I tried such things as booting up with a LiveCD and mounting the partition that I had updated on and doing things like uninstalling grub2 and installing grub, or reinstalling grub2, or doing the whole grub-install / update-grub / etc, or entering grub and doing the whole root(hdx,x) / setup (hdx,x),  ETC ETC....

I was finally able to get rid of the "grub_puts_" message...

but now it's saying:  "No boot sector found.  Reboot your computer".

Still can do nothing with the Ultimate Boot CD.

I'm pulling my hairs out....  :confused:

Here is a TON of information that I got from the boot_info_script that should help someone savvy enough to help me!

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => GAG is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda8 and 
                       looks at sector 988754953 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1       1,224,458,235 1,250,258,624    25,800,390   7 HPFS/NTFS
/dev/sda3    *             63   839,605,094   839,605,032  83 Linux
/dev/sda4         839,605,219 1,224,458,234   384,853,016   5 Extended
/dev/sda5         942,999,561   968,687,369    25,687,809  83 Linux
/dev/sda6       1,201,935,168 1,224,458,234    22,523,067  82 Linux swap / Solaris
/dev/sda7         968,687,433   988,222,409    19,534,977  83 Linux
/dev/sda8         988,222,473 1,086,700,859    98,478,387  83 Linux
/dev/sda9       1,180,456,263 1,201,935,104    21,478,842  83 Linux
/dev/sda10        839,605,221   921,536,594    81,931,374  83 Linux
/dev/sda11        921,536,658   942,999,434    21,462,777  83 Linux
/dev/sda12      1,086,700,923 1,180,456,199    93,755,277  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   146,560,994   146,560,932  83 Linux
/dev/sdb2         146,560,995   253,987,649   107,426,655  83 Linux
/dev/sdb3         253,987,650   275,466,554    21,478,905  83 Linux
/dev/sdb4         275,466,555   312,576,704    37,110,150  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9   ext4                                     
/dev/sda11       9debaceb-e23b-4caf-abef-4814039bf7a9   ext4                                     
/dev/sda12       0258ecd8-9f5d-4cbc-9ad5-3e8933322411   ext4                                     
/dev/sda1        582906F46FA0E2C1                       ntfs                                     
/dev/sda3        58640970-8d3e-4d2a-b0de-36e90d5421c4   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a   ext3                                     
/dev/sda6        77906b61-6512-4ef7-81b4-07699bf43d3f   swap                                     
/dev/sda7        74922787-c7b0-41c1-b235-95c2ff8d9016   ext3                                     
/dev/sda8        cf2256fb-f62a-453f-abc6-ff997d3e7f88   ext4                                     
/dev/sda9        3f7e5a34-2830-41df-90e0-c99552997bde   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2c372c43-17c8-46c1-a266-f4d3d07bc63f   ext3                                     
/dev/sdb2        2c0f5ea6-5338-408b-b62d-7c72293570c3   ext3                                     
/dev/sdb3        bdc361ba-fd60-468f-8f76-8c4d23107568   ext3                                     
/dev/sdb4        5a3ddc4d-f6bd-407a-b63b-f404c0c09044   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda8        /mnt/root                ext4       (rw)
/dev             /mnt/root/dev            none       (rw,bind)


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
# kopt=root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-server
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-16-server
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode)
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-16-server

title		Ubuntu 9.10, memtest86+
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-22-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a /               ext3    relatime,errors=remount-ro 0       1
# /storage/lin/storage was on /dev/sdb3 during installation
UUID=58640970-8d3e-4d2a-b0de-36e90d5421c4 /storage/lin/storage ext3    relatime        0       2
# /storage/var/www was on /dev/sda3 during installation
UUID=bdc361ba-fd60-468f-8f76-8c4d23107568 /storage/var/www ext3    relatime        0       2
# /storage/win/storage was on /dev/sdb1 during installation
UUID=582906F46FA0E2C1 /storage/win/storage ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /home was on /dev/sda2 during installation
UUID=2c0f5ea6-5338-408b-b62d-7c72293570c3 /home           ext3    relatime        0       2
# /old was on /dev/sda1 during installation
UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f /old            ext3    relatime        0       2
# /old/var/www was on /dev/sda4 during installation
UUID=5a3ddc4d-f6bd-407a-b63b-f404c0c09044 /old/var/www    ext3    relatime        0       2
# /var/www was on /dev/sdb7 during installation
UUID=74922787-c7b0-41c1-b235-95c2ff8d9016 /var/www        ext3    relatime        0       2
# swap was on /dev/sdb6 during installation
UUID=77906b61-6512-4ef7-81b4-07699bf43d3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 483.7GB: boot/grub/menu.lst
 483.8GB: boot/grub/stage2
 495.5GB: boot/initrd.img-2.6.28-16-server
 495.6GB: boot/initrd.img-2.6.31-14-generic
 495.8GB: boot/vmlinuz-2.6.28-16-server
 495.5GB: boot/vmlinuz-2.6.31-14-generic
 495.6GB: initrd.img
 495.5GB: initrd.img.old
 495.5GB: vmlinuz
 495.8GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cf2256fb-f62a-453f-abc6-ff997d3e7f88

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

title		Chainload into GRUB 2
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/grub/core.img

title		&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
root

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro quiet splash
initrd		/boot/initrd.img-2.6.32-21-generic-pae
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae (recovery mode)
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single
initrd		/boot/initrd.img-2.6.32-21-generic-pae

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic-pae
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic-pae
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic-pae (recovery mode)
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single
initrd		/boot/initrd.img-2.6.31-21-generic-pae

title		Ubuntu 10.04 LTS, memtest86+
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	echo	'Loading Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 /               ext4    errors=remount-ro 0       1
# /storage/lin/storage was on /dev/sdb3 during installation
UUID=58640970-8d3e-4d2a-b0de-36e90d5421c4 /storage/lin/storage ext3    defaults        0       2
# /storage/var/www was on /dev/sdb7 during installation
UUID=74922787-c7b0-41c1-b235-95c2ff8d9016 /storage/var/www ext3    defaults        0       2
# /old was on /dev/sdb5 during installation
UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a /old            ext3    defaults        0       2
# /old/storage/var/www was on /dev/sda3 during installation
UUID=bdc361ba-fd60-468f-8f76-8c4d23107568 /old/storage/var/www ext3    defaults        0       2
# /old/home was on /dev/sda2 during installation
UUID=2c0f5ea6-5338-408b-b62d-7c72293570c3 /old/home       ext3    defaults        0       2
# /old/old was on /dev/sda1 during installation
UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f /old/old        ext3    defaults        0       2
# /old/var/www was on /dev/sda4 during installation
UUID=5a3ddc4d-f6bd-407a-b63b-f404c0c09044 /old/var/www    ext3    defaults        0       2
# /var/www was on /dev/sdb9 during installation
UUID=3f7e5a34-2830-41df-90e0-c99552997bde /var/www        ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=77906b61-6512-4ef7-81b4-07699bf43d3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 506.1GB: boot/grub/core.img
 506.7GB: boot/grub/grub.cfg
 510.5GB: boot/grub/menu.lst
 506.2GB: boot/grub/stage2
 513.3GB: boot/initrd.img-2.6.31-21-generic-pae
 529.3GB: boot/initrd.img-2.6.32-21-generic-pae
 549.0GB: boot/vmlinuz-2.6.31-21-generic-pae
 524.3GB: boot/vmlinuz-2.6.32-21-generic-pae
 529.3GB: initrd.img
 513.3GB: initrd.img.old
 524.3GB: vmlinuz
 549.0GB: vmlinuz.old

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic-pae (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	initrd /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic-pae (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	initrd /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 /               ext4    errors=remount-ro 0       1
# /storage/lin/storage was on /dev/sda3 during installation
UUID=58640970-8d3e-4d2a-b0de-36e90d5421c4 /storage/lin/storage ext3    defaults        0       2
# /storage/var/www was on /dev/sda7 during installation
UUID=74922787-c7b0-41c1-b235-95c2ff8d9016 /storage/var/www ext3    defaults        0       2
# /storage/win/storage was on /dev/sda1 during installation
UUID=582906F46FA0E2C1 /storage/win/storage ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /home was on /dev/sda12 during installation
UUID=0258ecd8-9f5d-4cbc-9ad5-3e8933322411 /home           ext4    defaults        0       2
# /old was on /dev/sda5 during installation
UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a /old            ext3    defaults        0       2
# /old/old2 was on /dev/sda8 during installation
UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 /old/old2       ext4    defaults        0       2
# /old/var/www2 was on /dev/sda9 during installation
UUID=3f7e5a34-2830-41df-90e0-c99552997bde /old/var/www2   ext4    defaults        0       2
# /var/www was on /dev/sda11 during installation
UUID=9debaceb-e23b-4caf-abef-4814039bf7a9 /var/www        ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=77906b61-6512-4ef7-81b4-07699bf43d3f none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 447.2GB: boot/grub/core.img
 443.2GB: boot/grub/grub.cfg
 447.3GB: boot/initrd.img-2.6.32-21-generic
 447.2GB: boot/vmlinuz-2.6.32-21-generic
 447.3GB: initrd.img
 447.2GB: vmlinuz

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=bdc361ba-fd60-468f-8f76-8c4d23107568 /storage/var/www ext3    relatime        0       2
# /dev/sdb1
UUID=582906F46FA0E2C1 /storage/win/storage ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2c0f5ea6-5338-408b-b62d-7c72293570c3 /home           ext3    relatime        0       2
# /dev/sda4
UUID=5a3ddc4d-f6bd-407a-b63b-f404c0c09044 /var/www        ext3    relatime        0       2
# /dev/sdb2
UUID=84d2ce24-e81f-4a3d-9a75-6313392b3deb none            swap    sw              0       0
# ADDED BY ME... 23 Jul 2008
/dev/sdb3   /storage/lin/storage ext3    relatime    0   2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#ADDED BY ME... 18 Aug 2008
none /proc/bus/usb mruser devgid=1000,devmode=660 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  50.5GB: boot/grub/menu.lst
  50.4GB: boot/grub/stage2
  50.6GB: boot/initrd.img-2.6.24-16-generic
  50.4GB: boot/initrd.img-2.6.24-16-generic.bak
  50.5GB: boot/initrd.img-2.6.24-19-generic
  50.5GB: boot/initrd.img-2.6.24-19-generic.bak
  50.6GB: boot/initrd.img-2.6.24-21-generic
  50.5GB: boot/initrd.img-2.6.24-21-generic.bak
  50.5GB: boot/initrd.img-2.6.24-22-generic
  50.5GB: boot/initrd.img-2.6.24-22-generic.bak
  50.5GB: boot/initrd.img-2.6.24-23-generic
  50.5GB: boot/initrd.img-2.6.24-23-generic.bak
  50.4GB: boot/initrd.img-2.6.27-11-generic
  50.5GB: boot/initrd.img-2.6.28-11-generic
  50.6GB: boot/initrd.img-2.6.28-13-generic
  50.4GB: boot/vmlinuz-2.6.24-16-generic
  50.6GB: boot/vmlinuz-2.6.24-19-generic
  50.5GB: boot/vmlinuz-2.6.24-21-generic
  50.4GB: boot/vmlinuz-2.6.24-22-generic
  50.5GB: boot/vmlinuz-2.6.24-23-generic
  50.4GB: boot/vmlinuz-2.6.27-11-generic
  50.5GB: boot/vmlinuz-2.6.28-11-generic
  50.4GB: boot/vmlinuz-2.6.28-13-generic
  50.6GB: initrd.img
  50.5GB: initrd.img.old
  50.4GB: vmlinuz
  50.5GB: vmlinuz.old

```

If you have ANY suggestions or thoughts or ANYTHING, PLEASE PLEASE PLEASE help!!!!    I can't do any work or anything until I get this back up and running!

THANK YOU!

---

### Post by frantid on 2010-05-02
You've got a mixture of grub-legacy and grub2 on your system.  grub2 in the mbr of sda, but grub 0.97 in the partition of sda8.

You've got more linux distros on your system, than I'm familiar with.  I hope some one with more knowledge will jump in.

---

### Post by Cyclops_ on 2010-05-02
Hey frantid,

Thanks for replying.

I think that I made a mess of things with all my trying to fix it.

All I really care about is getting sda8 and sda10 bootable.  They both have Lucid on them.  As a matter of technicality, all I really need is sda8 bootable.  If you can walk me through it, I will remove all instances of grub except for the one(s) needed to boot sda8.  I do not have any Windows partitions (just an NTFS that I was keeping around in case I need it for some reason or other, but I can get rid of that also).

sda10-12 are expendable as well as that NTFS partition.

The only thing that I can boot with right now is a Kubuntu Lucid disc that I made last night.

If you know how I can get rid of all grub, and then reinstall such that all I have is what I need to boot sda8, I would be MOST grateful!!!

Thank you!

---

### Post by frantid on 2010-05-02
I'll try.  So let's shoot for getting grub on sda10 working.  Then cleanup sda8

There's a good how-to here.  Use the from livecd instructions.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#How_To_Re-install_GRUB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#How_To_Re-install_GRUB)

make sure you use /dev/sda to put grub in the MBR and -d /media/mount-name-of-sda8/boot/grub to make it use the files in your lucid on sda8.

---

### Post by frantid on 2010-05-02
I've got to head out.  Hopefully, after that you will reboot and see the grub menu from sda10.  You should be able to use the menu item to get to sda8 lucid.  Once you're in sda8 lucid, booted into it, use synaptic to remove all grub items from that lucid.  Make sure you're in sda8 version of lucid.  

Easy way is to check in disk utility to see which partition is mounted as /   

Otherwise it might mess up after an update on the kernel.

Once sda8 is clean, I would move /boot/grub to /boot/grubold
then install grub2 from synaptic again.  Then you could boot off of the grub menu in sda8.

good luck, be back tomorrow

---

### Post by Cyclops_ on 2010-05-02
OK.  Did that.  What's next?

(Still getting "No bootable sector found").

Thanks :)

---

### Post by kansasnoob on 2010-05-02
I'm studying :D

Go ahead and boot your Kubuntu Live CD to the Live Desktop and I'll be back directly.

---

### Post by frantid on 2010-05-02
ok run the script again

---

### Post by Cyclops_ on 2010-05-02
Oops, I had just done the first thing that you mentioned.  I just saw your next post...  Give me one second and I will post the script results again.

---

### Post by Cyclops_ on 2010-05-02
Here it is:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => GAG is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda8 and 
                       looks at sector 988754953 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1       1,224,458,235 1,250,258,624    25,800,390   7 HPFS/NTFS
/dev/sda3    *             63   839,605,094   839,605,032  83 Linux
/dev/sda4         839,605,219 1,224,458,234   384,853,016   5 Extended
/dev/sda5         942,999,561   968,687,369    25,687,809  83 Linux
/dev/sda6       1,201,935,168 1,224,458,234    22,523,067  82 Linux swap / Solaris
/dev/sda7         968,687,433   988,222,409    19,534,977  83 Linux
/dev/sda8         988,222,473 1,086,700,859    98,478,387  83 Linux
/dev/sda9       1,180,456,263 1,201,935,104    21,478,842  83 Linux
/dev/sda10        839,605,221   921,536,594    81,931,374  83 Linux
/dev/sda11        921,536,658   942,999,434    21,462,777  83 Linux
/dev/sda12      1,086,700,923 1,180,456,199    93,755,277  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   146,560,994   146,560,932  83 Linux
/dev/sdb2         146,560,995   253,987,649   107,426,655  83 Linux
/dev/sdb3         253,987,650   275,466,554    21,478,905  83 Linux
/dev/sdb4         275,466,555   312,576,704    37,110,150  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9   ext4       kubuntu                       
/dev/sda11       9debaceb-e23b-4caf-abef-4814039bf7a9   ext4       kubuntu_var_ww                
/dev/sda12       0258ecd8-9f5d-4cbc-9ad5-3e8933322411   ext4       kubuntu_home                  
/dev/sda1        582906F46FA0E2C1                       ntfs                                     
/dev/sda3        58640970-8d3e-4d2a-b0de-36e90d5421c4   ext3       storage                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a   ext3       old_root                      
/dev/sda6        77906b61-6512-4ef7-81b4-07699bf43d3f   swap                                     
/dev/sda7        74922787-c7b0-41c1-b235-95c2ff8d9016   ext3       old_var_www                   
/dev/sda8        cf2256fb-f62a-453f-abc6-ff997d3e7f88   ext4       root                          
/dev/sda9        3f7e5a34-2830-41df-90e0-c99552997bde   ext4       var_www                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2c372c43-17c8-46c1-a266-f4d3d07bc63f   ext3       old_old_root                  
/dev/sdb2        2c0f5ea6-5338-408b-b62d-7c72293570c3   ext3       old_home                      
/dev/sdb3        bdc361ba-fd60-468f-8f76-8c4d23107568   ext3       old_storage                   
/dev/sdb4        5a3ddc4d-f6bd-407a-b63b-f404c0c09044   ext3       old_var_www                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/storage           ext3       (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-server
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-16-server
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode)
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-16-server

title		Ubuntu 9.10, memtest86+
uuid		0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-22-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a /               ext3    relatime,errors=remount-ro 0       1
# /bahnmiller/lin/storage was on /dev/sdb3 during installation
UUID=58640970-8d3e-4d2a-b0de-36e90d5421c4 /bahnmiller/lin/storage ext3    relatime        0       2
# /bahnmiller/var/www was on /dev/sda3 during installation
UUID=bdc361ba-fd60-468f-8f76-8c4d23107568 /bahnmiller/var/www ext3    relatime        0       2
# /bahnmiller/win/storage was on /dev/sdb1 during installation
UUID=582906F46FA0E2C1 /bahnmiller/win/storage ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /home was on /dev/sda2 during installation
UUID=2c0f5ea6-5338-408b-b62d-7c72293570c3 /home           ext3    relatime        0       2
# /old was on /dev/sda1 during installation
UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f /old            ext3    relatime        0       2
# /old/var/www was on /dev/sda4 during installation
UUID=5a3ddc4d-f6bd-407a-b63b-f404c0c09044 /old/var/www    ext3    relatime        0       2
# /var/www was on /dev/sdb7 during installation
UUID=74922787-c7b0-41c1-b235-95c2ff8d9016 /var/www        ext3    relatime        0       2
# swap was on /dev/sdb6 during installation
UUID=77906b61-6512-4ef7-81b4-07699bf43d3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 483.7GB: boot/grub/menu.lst
 483.8GB: boot/grub/stage2
 495.5GB: boot/initrd.img-2.6.28-16-server
 495.6GB: boot/initrd.img-2.6.31-14-generic
 495.8GB: boot/vmlinuz-2.6.28-16-server
 495.5GB: boot/vmlinuz-2.6.31-14-generic
 495.6GB: initrd.img
 495.5GB: initrd.img.old
 495.5GB: vmlinuz
 495.8GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cf2256fb-f62a-453f-abc6-ff997d3e7f88

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

title		Chainload into GRUB 2
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/grub/core.img

title		&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
root

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro quiet splash
initrd		/boot/initrd.img-2.6.32-21-generic-pae
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae (recovery mode)
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single
initrd		/boot/initrd.img-2.6.32-21-generic-pae

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic-pae
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic-pae
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic-pae (recovery mode)
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single
initrd		/boot/initrd.img-2.6.31-21-generic-pae

title		Ubuntu 10.04 LTS, memtest86+
uuid		cf2256fb-f62a-453f-abc6-ff997d3e7f88
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	echo	'Loading Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 /               ext4    errors=remount-ro 0       1
# /bahnmiller/lin/storage was on /dev/sdb3 during installation
UUID=58640970-8d3e-4d2a-b0de-36e90d5421c4 /bahnmiller/lin/storage ext3    defaults        0       2
# /bahnmiller/var/www was on /dev/sdb7 during installation
UUID=74922787-c7b0-41c1-b235-95c2ff8d9016 /bahnmiller/var/www ext3    defaults        0       2
# /old was on /dev/sdb5 during installation
UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a /old            ext3    defaults        0       2
# /old/bahnmiller/var/www was on /dev/sda3 during installation
UUID=bdc361ba-fd60-468f-8f76-8c4d23107568 /old/bahnmiller/var/www ext3    defaults        0       2
# /old/home was on /dev/sda2 during installation
UUID=2c0f5ea6-5338-408b-b62d-7c72293570c3 /old/home       ext3    defaults        0       2
# /old/old was on /dev/sda1 during installation
UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f /old/old        ext3    defaults        0       2
# /old/var/www was on /dev/sda4 during installation
UUID=5a3ddc4d-f6bd-407a-b63b-f404c0c09044 /old/var/www    ext3    defaults        0       2
# /var/www was on /dev/sdb9 during installation
UUID=3f7e5a34-2830-41df-90e0-c99552997bde /var/www        ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=77906b61-6512-4ef7-81b4-07699bf43d3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 506.1GB: boot/grub/core.img
 506.7GB: boot/grub/grub.cfg
 510.5GB: boot/grub/menu.lst
 506.2GB: boot/grub/stage2
 513.3GB: boot/initrd.img-2.6.31-21-generic-pae
 529.3GB: boot/initrd.img-2.6.32-21-generic-pae
 549.0GB: boot/vmlinuz-2.6.31-21-generic-pae
 524.3GB: boot/vmlinuz-2.6.32-21-generic-pae
 529.3GB: initrd.img
 513.3GB: initrd.img.old
 524.3GB: vmlinuz
 549.0GB: vmlinuz.old

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa quiet splash
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a ro xforcevesa single
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic-pae (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	initrd /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic-pae (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set cf2256fb-f62a-453f-abc6-ff997d3e7f88
	linux /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro single splash
	initrd /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro single
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c372c43-17c8-46c1-a266-f4d3d07bc63f
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=64f5bae6-cf3f-4d1b-a097-ead5c9dd19b9 /               ext4    errors=remount-ro 0       1
# /bahnmiller/lin/storage was on /dev/sda3 during installation
UUID=58640970-8d3e-4d2a-b0de-36e90d5421c4 /bahnmiller/lin/storage ext3    defaults        0       2
# /bahnmiller/var/www was on /dev/sda7 during installation
UUID=74922787-c7b0-41c1-b235-95c2ff8d9016 /bahnmiller/var/www ext3    defaults        0       2
# /bahnmiller/win/storage was on /dev/sda1 during installation
UUID=582906F46FA0E2C1 /bahnmiller/win/storage ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /home was on /dev/sda12 during installation
UUID=0258ecd8-9f5d-4cbc-9ad5-3e8933322411 /home           ext4    defaults        0       2
# /old was on /dev/sda5 during installation
UUID=0dec96cd-cfe3-416a-8a29-9a0d5bc8aa2a /old            ext3    defaults        0       2
# /old/old2 was on /dev/sda8 during installation
UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 /old/old2       ext4    defaults        0       2
# /old/var/www2 was on /dev/sda9 during installation
UUID=3f7e5a34-2830-41df-90e0-c99552997bde /old/var/www2   ext4    defaults        0       2
# /var/www was on /dev/sda11 during installation
UUID=9debaceb-e23b-4caf-abef-4814039bf7a9 /var/www        ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=77906b61-6512-4ef7-81b4-07699bf43d3f none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 447.2GB: boot/grub/core.img
 443.2GB: boot/grub/grub.cfg
 447.3GB: boot/initrd.img-2.6.32-21-generic
 447.2GB: boot/vmlinuz-2.6.32-21-generic
 447.3GB: initrd.img
 447.2GB: vmlinuz

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2c372c43-17c8-46c1-a266-f4d3d07bc63f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=bdc361ba-fd60-468f-8f76-8c4d23107568 /bahnmiller/var/www ext3    relatime        0       2
# /dev/sdb1
UUID=582906F46FA0E2C1 /bahnmiller/win/storage ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2c0f5ea6-5338-408b-b62d-7c72293570c3 /home           ext3    relatime        0       2
# /dev/sda4
UUID=5a3ddc4d-f6bd-407a-b63b-f404c0c09044 /var/www        ext3    relatime        0       2
# /dev/sdb2
UUID=84d2ce24-e81f-4a3d-9a75-6313392b3deb none            swap    sw              0       0
# ADDED BY MJB 23 Jul 2008
/dev/sdb3   /bahnmiller/lin/storage ext3    relatime    0   2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#ADDED BY MJB 18 Aug 2008
none /proc/bus/usb haven devgid=1000,devmode=660 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  50.5GB: boot/grub/menu.lst
  50.4GB: boot/grub/stage2
  50.6GB: boot/initrd.img-2.6.24-16-generic
  50.4GB: boot/initrd.img-2.6.24-16-generic.bak
  50.5GB: boot/initrd.img-2.6.24-19-generic
  50.5GB: boot/initrd.img-2.6.24-19-generic.bak
  50.6GB: boot/initrd.img-2.6.24-21-generic
  50.5GB: boot/initrd.img-2.6.24-21-generic.bak
  50.5GB: boot/initrd.img-2.6.24-22-generic
  50.5GB: boot/initrd.img-2.6.24-22-generic.bak
  50.5GB: boot/initrd.img-2.6.24-23-generic
  50.5GB: boot/initrd.img-2.6.24-23-generic.bak
  50.4GB: boot/initrd.img-2.6.27-11-generic
  50.5GB: boot/initrd.img-2.6.28-11-generic
  50.6GB: boot/initrd.img-2.6.28-13-generic
  50.4GB: boot/vmlinuz-2.6.24-16-generic
  50.6GB: boot/vmlinuz-2.6.24-19-generic
  50.5GB: boot/vmlinuz-2.6.24-21-generic
  50.4GB: boot/vmlinuz-2.6.24-22-generic
  50.5GB: boot/vmlinuz-2.6.24-23-generic
  50.4GB: boot/vmlinuz-2.6.27-11-generic
  50.5GB: boot/vmlinuz-2.6.28-11-generic
  50.4GB: boot/vmlinuz-2.6.28-13-generic
  50.6GB: initrd.img
  50.5GB: initrd.img.old
  50.4GB: vmlinuz
  50.5GB: vmlinuz.old

```

---

### Post by frantid on 2010-05-02
did you get any errors running grub-setup?

try this from the terminal:

```
sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by kansasnoob on 2010-05-02
Since you want sda8 working the worst that's where we'll start. Please copy-n-paste these commands because some are ridiculously long:

```
sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub
```

If it says "not installed so not removed that's OK, just continue:

```
apt-get --purge remove grub-common
```

```
apt-get update
```

```
apt-get install --reinstall grub-pc
```

I know that will reinstall grub-common also, that's OK, just continue:

```
update-grub
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Hopefully that'll get the Lucid on sda8 booting :D

If you're curious what we're doing look here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

And at Appendix #2 here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

If anything appears to fail the full terminal output is essential!

---

### Post by oldfred on 2010-05-02
I think you will have to chroot into sda8 and possibly sda10 separately to get it to fully uninstall grub legacy and grub2 (grub-pc) and then cleanly reinstall grub2.

Do not copy any thing with #

sudo -i
mount /dev/sda8 /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /usr/ /mnt/usr
chroot /mnt
sudo -i
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
# possibly this also
dpkg-reconfigure grub-pc
#Exit by pressing CTRL-d.
umount /mnt/dev /mnt/proc /mnt/sys /mnt/usr
umount /mnt
#Reboot & run:
sudo update-grub

---

### Post by frantid on 2010-05-02
sweet -- you're in good hands -- I'm off 

good luck.

---

### Post by kansasnoob on 2010-05-02
OldFred's thinking the same as me we just use different spices in our chile :D

---

### Post by oldfred on 2010-05-02
kansasnoob's is easier to copy as he did it all on one line. Only if you have problems as he says do you have to do it line by line. 

I just converted mine to a bash file and copied it to my USB so if I ever need it I have it.

---

### Post by Cyclops_ on 2010-05-02
LOL.  You guys are great.

Two things while following kansasnoob's:

First was in the new installation of grub, it said something about "the following" being a command that it was supposed to have lifted from somewhere (some file or 'kopt' or something, but there was no command in there, so I just said OK.  I can restart the instructions if you don't know what I am talking about and get the exact message.

Second is this (what do I do about it?):
```

The grub-pc package is being upgraded.  This menu allows you to select which devices you'd like grub-install to be automatically run for, if any.                                                      &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; It is recommended that you do this in most situations, to prevent the installed GRUB from getting out of sync with other components such as grub.cfg or with newer Linux images it will have to load.  &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.                                                                         &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; Note: It is possible to install GRUB to partition boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.      &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; GRUB install devices:                                                                                                                                                                                  &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474;    [ ] /dev/sda (640135 MB, WDC_WD6400AAKS-00A7B0)                                                                                                                                                     &#9474;            
            &#9474;    [ ] - /dev/sda1 (13209 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda10 (41948 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda11 (10988 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda12 (48002 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda3 (429877 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda4 (0 MB)                                                                                                                                                                              &#9474;            
            &#9474;    [ ] - /dev/sda5 (13152 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda6 (11531 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda7 (10001 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda8 (50420 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda9 (10997 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] /dev/sdb (160041 MB, ST3160811AS)                                                                                                                                                               &#9474;            
            &#9474;    [ ] - /dev/sdb1 (75039 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sdb2 (55002 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sdb3 (10997 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sdb4 (19000 MB)                             

```

---

### Post by kansasnoob on 2010-05-02
> **Cyclops_ said:**
> LOL.  You guys are great.

Two things while following kansasnoob's:

First was in the new installation of grub, it said something about "the following" being a command that it was supposed to have lifted from somewhere (some file or 'kopt' or something, but there was no command in there, so I just said OK.  I can restart the instructions if you don't know what I am talking about and get the exact message.

Second is this (what do I do about it?):
```

The grub-pc package is being upgraded.  This menu allows you to select which devices you'd like grub-install to be automatically run for, if any.                                                      &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; It is recommended that you do this in most situations, to prevent the installed GRUB from getting out of sync with other components such as grub.cfg or with newer Linux images it will have to load.  &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.                                                                         &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; Note: It is possible to install GRUB to partition boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.      &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474; GRUB install devices:                                                                                                                                                                                  &#9474;            
            &#9474;                                                                                                                                                                                                        &#9474;            
            &#9474;    [ ] /dev/sda (640135 MB, WDC_WD6400AAKS-00A7B0)                                                                                                                                                     &#9474;            
            &#9474;    [ ] - /dev/sda1 (13209 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda10 (41948 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda11 (10988 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda12 (48002 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda3 (429877 MB)                                                                                                                                                                         &#9474;            
            &#9474;    [ ] - /dev/sda4 (0 MB)                                                                                                                                                                              &#9474;            
            &#9474;    [ ] - /dev/sda5 (13152 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda6 (11531 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda7 (10001 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda8 (50420 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sda9 (10997 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] /dev/sdb (160041 MB, ST3160811AS)                                                                                                                                                               &#9474;            
            &#9474;    [ ] - /dev/sdb1 (75039 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sdb2 (55002 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sdb3 (10997 MB)                                                                                                                                                                          &#9474;            
            &#9474;    [ ] - /dev/sdb4 (19000 MB)                             

```

Install to /dev/sda and /dev/sdb but no partitions!

Drives are designated sda = drive #1, sdb = drive #2, etc.

Partitions are like sda1 = drive #1/partition #1, sdb3 = drive #2/partition #3, etc.

That's why I included the commands:

grub-install /dev/sda
grub-install /dev/sdb

That's definitely something we need to take up with the devs during 10.10!

Edit: sorry my response took so long, I was putting away yard equipment. I've been cleaning up from a somewhat bad storm. Not one of those killer storms though.

---

### Post by kansasnoob on 2010-05-02
@ oldfred, did you realize this carried over from Karmic to Lucid:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](http://www.ubuntu.com/getubuntu/releasenotes/1004#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)

It can be a real gob-stopper to updating packages and such.

---

### Post by Cyclops_ on 2010-05-02
Wahoo!  Guys...  that did it!   I am now into my fresh update!

Now to start figuring out what all these other issues are all about.  Like for some reason I can only use one monitor (though all three come up), and when I move my mouse to one of the others it starts dancing and doesn't let me control it.

But anyway, that's a message for another forum.

THANK YOU THANK YOU VERY MUCH for the help!!!

---

### Post by oldfred on 2010-05-02
Kansas thanks for the update on upstart problem.

With Karmic they said do not install grub2 to partitions due to blocklists and now they want everyone to install it everywhere!!!

No wonder we have having so many users with issues.

---

