---
title: "Windows 7 not recognized and NTLDR is missing"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by timstone on 2010-03-22
Finally got Ubuntu installed on my machine and now I can not get windows to boot from GRUB.  My windows partition is located at /dev/sda2 and here is my menu.lst file.


```

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
# title		Windows 7
# root		(hd0,0)


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
# kopt=root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f1d1b6c-171b-4522-a065-b41651e45dd8

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
uuid		9f1d1b6c-171b-4522-a065-b41651e45dd8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9f1d1b6c-171b-4522-a065-b41651e45dd8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9f1d1b6c-171b-4522-a065-b41651e45dd8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic vga=792 root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows
root	(hd0,1)
savedefault
makeactive
chainloader	+1


```


What appears to be wrong?


EDIT:  Forgot the rest of the information.... When I reboot my computer GRUB will not load.  It always gives me Error 21.  The only way to get it to run is to turn the computer off and then back on. 

When selecting Windows 7 from the boot list the first time or two it will just send me back to the list after a brief blank screen then around the 3rd time I select it, it tells me NTLDR is missing.

---

### Post by wilee-nilee on 2010-03-22
So what your saying is that you have a dual boot, (not wubi) and neither W7 or Ubuntu will boot. If this is the case then what do you have for tools do you have a restore disc for W7 and a bootable Ubuntu Live setup.

Also in what order was this stuff installed and what exactly is it which Ubuntu.

Edit: I see now that it is Jaunty legacy grub or grub2 it is hard to tell for me.

---

### Post by timstone on 2010-03-22
> **wilee-nilee said:**
> So what your saying is that you have a dual boot, (not wubi) and neither W7 or Ubuntu will boot. If this is the case then what do you have for tools do you have a restore disc for W7 and a bootable Ubuntu Live setup.

Also in what order was this stuff installed and what exactly is it which Ubuntu.

Edit: I see now that it is Jaunty legacy grub or grub2 it is hard to tell for me.

Windows 7 is installed on the primary hard drive...which is an internal drive.  It is split into 2 partitions..one for the OS and another partition used for file storage.  Ubuntu is on an external drive which is currently partitioned with Ubuntu using about 20GB and the rest (around 460GB set as NTFS for file storage)

Ubuntu will boot fine but once the computer restarts it has to be turned off or the GRUB menu won't appear it just gives me Error 21...but once it is turned off then back on the menu appears without a problem.

I just want to know if I need to map it differently for my Windows 7 to load.  Currently I've tried using both hd(0,0) and hd(0,1)  Neither have worked.  And as I said in the OP...my Windows boot partition is located on /dev/sda2

Oh right...and W7 was installed first...Ubuntu was put on the external drive just last night.

---

### Post by oldfred on 2010-03-22
Most users forget to install grub to the external drive when installing Ubuntu to it. Grub installs to the default boot drive so unless the external was set as default before install grub probably overwrote the windows boot loader in the internal MBR.

So we can see your configuration, with the external on.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by timstone on 2010-03-22
> **oldfred said:**
> Most users forget to install grub to the external drive when installing Ubuntu to it. Grub installs to the default boot drive so unless the external was set as default before install grub probably overwrote the windows boot loader in the internal MBR.

So we can see your configuration, with the external on.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.



```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 954252268 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    13,815,899    13,815,837  83 Linux
/dev/sda2    *     13,815,900   106,077,194    92,261,295   7 HPFS/NTFS
/dev/sda3         106,077,195   156,248,189    50,170,995   f W95 Ext d (LBA)
/dev/sda5         106,077,258   129,949,784    23,872,527   7 HPFS/NTFS
/dev/sda6         150,191,748   156,248,189     6,056,442  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fd13d78

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    42,443,729    42,443,667  83 Linux
/dev/sdb2         954,228,870   976,768,064    22,539,195   5 Extended
/dev/sdb5         964,703,313   976,768,064    12,064,752  82 Linux swap / Solaris
/dev/sdb6         959,466,186   964,349,819     4,883,634  83 Linux
/dev/sdb7         964,349,883   964,703,249       353,367  82 Linux swap / Solaris
/dev/sdb8         954,228,996   959,112,629     4,883,634  83 Linux
/dev/sdb9         959,112,693   959,466,059       353,367  82 Linux swap / Solaris
/dev/sdb3          42,443,730   954,228,869   911,785,140   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c7990ec2-60ff-4949-98e8-6cedcfefe942   ext3                                     
/dev/sda5        427A05E97A05DB15                       ntfs       Storage                       
/dev/sda6        2dca1c6b-7550-4d45-863a-ef01086f1894   swap                                     
/dev/sdb1        e9592193-47dc-4a07-9cec-6c2b025cb05f   ext4                                     
/dev/sdb3        7AF52B260C61F95F                       ntfs                                     
/dev/sdb5        7c9c26af-dcbd-4dba-8e2e-381ac0d1d765   swap                                     
/dev/sdb6        9f1d1b6c-171b-4522-a065-b41651e45dd8   ext3                                     
/dev/sdb7        683a8eac-1663-448b-9972-45233f248e2a   swap                                     
/dev/sdb8        890a5247-0255-4cf5-8aac-c452b1b4416e   ext3                                     
/dev/sdb9        732803ce-d8bf-4e81-afa3-f8a4d9d79bd2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb8        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb6        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1        /media/disk-2            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb3        /media/disk-3            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		7

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
# kopt=root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic vga=792 root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd1,1)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=2dca1c6b-7550-4d45-863a-ef01086f1894 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb2 /media/XP ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda1: Location of files loaded by Grub: ===================


   1.5GB: boot/grub/menu.lst
   4.0GB: boot/grub/stage2
   3.8GB: boot/initrd.img-2.6.24-21-generic
   3.9GB: boot/initrd.img-2.6.24-21-generic.bak
   3.8GB: boot/initrd.img-2.6.27-14-generic
   4.9GB: boot/initrd.img-2.6.28-11-generic
   1.5GB: boot/initrd.img-2.6.28-12-generic
   1.5GB: boot/initrd.img-2.6.28-13-generic
   3.9GB: boot/vmlinuz-2.6.24-21-generic
   3.8GB: boot/vmlinuz-2.6.27-14-generic
   3.7GB: boot/vmlinuz-2.6.28-11-generic
   1.3GB: boot/vmlinuz-2.6.28-12-generic
   1.5GB: boot/vmlinuz-2.6.28-13-generic
   1.5GB: initrd.img
   1.5GB: initrd.img.old
   1.5GB: vmlinuz
   1.3GB: vmlinuz.old

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e9592193-47dc-4a07-9cec-6c2b025cb05f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=7c9c26af-dcbd-4dba-8e2e-381ac0d1d765 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sdb6/boot/grub/menu.lst: ===========================

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
# title		Windows 7
# root		(hd0,0)


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
# kopt=root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f1d1b6c-171b-4522-a065-b41651e45dd8

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
uuid		9f1d1b6c-171b-4522-a065-b41651e45dd8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9f1d1b6c-171b-4522-a065-b41651e45dd8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9f1d1b6c-171b-4522-a065-b41651e45dd8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic vga=792 root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows 7
root (hd0,0)
savedefault
makeactive
chainloader +1

title Microsoft Windows 7
root (hd0,1)
savedefault
makeactive
chainloader +1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=683a8eac-1663-448b-9972-45233f248e2a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 491.9GB: boot/grub/menu.lst
 492.8GB: boot/grub/stage2
 492.9GB: boot/initrd.img-2.6.28-11-generic
 492.6GB: boot/vmlinuz-2.6.28-11-generic
 492.9GB: initrd.img
 492.6GB: vmlinuz

=========================== sdb8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=890a5247-0255-4cf5-8aac-c452b1b4416e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=890a5247-0255-4cf5-8aac-c452b1b4416e

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
uuid		890a5247-0255-4cf5-8aac-c452b1b4416e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=890a5247-0255-4cf5-8aac-c452b1b4416e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		890a5247-0255-4cf5-8aac-c452b1b4416e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=890a5247-0255-4cf5-8aac-c452b1b4416e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		890a5247-0255-4cf5-8aac-c452b1b4416e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic vga=792 root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows 7
root (hd0,2)
savedefault
makeactive
chainloader +1 


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f1d1b6c-171b-4522-a065-b41651e45dd8 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=890a5247-0255-4cf5-8aac-c452b1b4416e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=732803ce-d8bf-4e81-afa3-f8a4d9d79bd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


 489.2GB: boot/grub/menu.lst
 488.5GB: boot/grub/stage2
 490.0GB: boot/initrd.img-2.6.28-11-generic
 490.0GB: boot/vmlinuz-2.6.28-11-generic
 490.0GB: initrd.img
 490.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```


Wasn't really sure what exactly you wanted me to bold so I just left it as is so I didn't make anyone confused.  Also...I'm adding the output of my fdisk -l command in case you might need that.

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         860     6907918+  83  Linux
/dev/sda2   *         861        6603    46130647+   7  HPFS/NTFS
/dev/sda3            6604        9726    25085497+   f  W95 Ext'd (LBA)
/dev/sda5            6604        8089    11936263+   7  HPFS/NTFS
/dev/sda6            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fd13d78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2642    21221833+  83  Linux
/dev/sdb2           59399       60801    11269597+   5  Extended
/dev/sdb3            2643       59398   455892570    7  HPFS/NTFS
/dev/sdb5           60051       60801     6032376   82  Linux swap / Solaris
/dev/sdb6           59725       60028     2441817   83  Linux
/dev/sdb7           60029       60050      176683+  82  Linux swap / Solaris
/dev/sdb8           59399       59702     2441817   83  Linux
/dev/sdb9           59703       59724      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by timstone on 2010-03-22
bump -  reinstalled 9.04 and now Windows doesn't even appear in Grub at all.  Going to go ahead and do the upgrade to 9.10 still.

---

### Post by oldfred on 2010-03-22
IF you look in the boot script the fdisk listing is in there along with many other commands and some probes of the MBR to see what is in them. 

As I suspected you installed grub to the internal drive and your install is on the external. You also show 3 swaps? Have you tried installing multiple times and not reused the partitions created the first time?
If these are aborted installs you should delete them and reinstall once.  We can give you the commands to boot windows for menu.lst with old grub but if you are installing Karmic with grub2 it is much better at finding other operating systems.

Your menu.lst showed windows installs in sda1 which now has Ubuntu and sda2 has grub in the boot partition and the script cannot read the rest of the partition, but fdisk says it is NTFS. You seem to have some partition problem. If the size of sda2 is correct then make sure it is ntfs and flagged as the boot partiton.

---

### Post by timstone on 2010-03-23
I now have Karmic installed and it even made a new grub menu file and did not list any Windows OS at all.  When I boot into Karmic it doesn't even have any other drives mounted on the desktop like it normally would....I don't know what's going on and I'm not experienced enough to figure this out on my own.  So right now I just used gparted and switched sda2 to boot.  Will try this out and see what happens.  Also having problems with my wireless drivers with Karmic and since my Windows OS aren't mounted I can't find and install the windows wireless drivers.  Go figure!  Well...one step at a time I guess.




EDIT:  Nope...switching that to the boot didn't do anything.  I'm still getting Error 21 when Grub tries to load unless I do a complete shut down.  Can you just help me with getting back into Windows from where I'm at now so that I can at least do something on this thing?  I've got some stuff that needs to be done and I can't do it on Ubuntu right now.

---

### Post by oldfred on 2010-03-23
You need to do the windows repair on the sda2 partition if the windows install is still there.  You cannot have the grub in the PBR or boot sector.

I do not know which MBR you are using to boot. If it is still sda your windows repair will probablly overwrite the MBR and you will have to reinstall grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:    # this will overwrite grub in the MBR if grub is there.
FIXBOOT  C:     #This will fix the grub that should not be in the PBR
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by timstone on 2010-03-23
If I can get Windows to overwrite the MBR and be able to boot into Windows that will be fine too...I don't absolutely need to use grub...I can always use the Windows loader and save myself headaches.  The Windows install is still there and is on sda...I honestly can't tell you how the linux partition that is 6GB ended up on that drive cause I don't remember ever putting it there and grub shouldn't be that large.

I downloaded a Win7 recovery disk iso just now and I will try that to restore the Windows loader...I hope it works.  If it does that should be the end of my problems as long as I can get Ubuntu onto the Windows loader

I'll report back with what happens.

---

### Post by timstone on 2010-03-23
Ok so the recovery disc doesn't work.......just leaves me at a blank screen after everything loads.

I tried a few other things and this is the result....not sure if it might even help at all...

```

tim@tim-desktop:~$ sudo /bin/bash
root@tim-desktop:~# mount -t ntfs-3g /dev/sda2 /media/disk -o force
Unexpected clusters per mft record (-127).
Failed to mount '/dev/sda2': Invalid argument
[B]The device '/dev/sda2' doesn't seem to have a valid NTFS.
[/B]Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@tim-desktop:~# 

```

Not sure why that is happening because that is where my Windows install is located.  I can do the same with /dev/sda3 and it says that it wasn't exited within windows properly but it fixes the problem and mounts that partition just fine.

---

### Post by oldfred on 2010-03-23
I do not know testdisk but if there is a partition problem it seems to be the one most recommended.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by timstone on 2010-03-23
> **oldfred said:**
> I do not know testdisk but if there is a partition problem it seems to be the one most recommended.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

testdisk says

```

Disk /dev/sda - 80 GB / 74 GiB - CHS 9727 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1   859 254 63   13815837
P HPFS - NTFS            860   0  1  6602 254 63   92261295
L HPFS - NTFS           6603   1  1  8088 254 63   23872527 [Storage]
L Linux Swap            9349   1  1  9725 254 63    6056442









Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 47 GB / 43 GiB



```

But when I type P to list files it says "Can not open file system.  File system seems to be damaged.


**EDIT:  Ok I did some more fiddling with testdisk and now Ubuntu is finally at least recognizing the NTFS partition......so......from here what do I need to add into my menu.lst to get Windows to load from grub?**

Here is the output of my fdisk -l and menu.lst

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         860     6907918+  83  Linux
/dev/sda2   *         861        6603    46130647+   7  HPFS/NTFS
/dev/sda3            6604        9726    25085497+   f  W95 Ext'd (LBA)
/dev/sda5            6604        8089    11936263+   7  HPFS/NTFS
/dev/sda6            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fd13d78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60050   482351593+  83  Linux
/dev/sdb2           60051       60801     6032407+   5  Extended
/dev/sdb5           60051       60801     6032376   82  Linux swap / Solaris

```

```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		293de122-96c4-4826-913a-f36d0deaa1c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=293de122-96c4-4826-913a-f36d0deaa1c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		293de122-96c4-4826-913a-f36d0deaa1c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=293de122-96c4-4826-913a-f36d0deaa1c7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		293de122-96c4-4826-913a-f36d0deaa1c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic vga=792 root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c7990ec2-60ff-4949-98e8-6cedcfefe942 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by sendblink23 on 2010-03-23
Next Time....

if you are going to Install Ubuntu on ANOTHER HARD RRIVE.. make sure to UNPLUG all other Hard Drives.... then boot your computer and Install Ubuntu.. the way you wanted.

That way you woudl have never had any issues...since the boot grup etc.. everything related to Ubuntu/Linux was installed only to the other hard drive and it didn't touch your main * HD...  and you simply needed to reconnect everything and just boot computer with Boot options to choose what hard drive to boot either OS


Anyways.... I hope Windows Recovery.. didn't kill your Windows 7...  you simply need to Recover the MBR....  I have no clue if its still the same as before... this is what i used to recover XP MBR...   Boot with Ubuntu Live CD... open up Applications > Accessories > Terminal

run this command: sudo lilo -M /dev/sda mbr

If it doesn't give any errors.. it probably worked.. reboot and you could have back your original Windows boot up...  

If it worked....  then I would suggest Reinstall ubuntu again... BUT DO as I mentioned FIRST - UNPLUG all Hard Drives.. and only have connected the Hard Drive you only want to use for installing Ubuntu...  then you would be fine... after installing.. reconnect everything. 

If it didn't work.. I mean recovering the MBR for Windows (since yours is Windows 7)... well crap sorry I have no other ideas... I only used that command for recovering the MBR for Windows XP

---

### Post by timstone on 2010-03-23
> **sendblink23 said:**
> Next Time....

if you are going to Install Ubuntu on ANOTHER HARD RRIVE.. make sure to UNPLUG all other Hard Drives.... then boot your computer and Install Ubuntu.. the way you wanted.

That way you woudl have never had any issues...since the boot grup etc.. everything related to Ubuntu/Linux was installed only to the other hard drive and it didn't touch your main * HD...  and you simply needed to reconnect everything and just boot computer with Boot options to choose what hard drive to boot either OS


Anyways.... I hope Windows Recovery.. didn't kill your Windows 7...  you simply need to Recover the MBR....  I have no clue if its still the same as before... this is what i used to recover XP MBR...   Boot with Ubuntu Live CD... open up Applications > Accessories > Terminal

run this command: sudo lilo -M /dev/sda mbr

If it doesn't give any errors.. it probably worked.. reboot and you could have back your original Windows boot up...  

If it worked....  then I would suggest Reinstall ubuntu again... BUT DO as I mentioned FIRST - UNPLUG all Hard Drives.. and only have connected the Hard Drive you only want to use for installing Ubuntu...  then you would be fine... after installing.. reconnect everything. 

If it didn't work.. I mean recovering the MBR for Windows (since yours is Windows 7)... well crap sorry I have no other ideas... I only used that command for recovering the MBR for Windows XP

I used sudo lilo -M /dev/sda mbr last night and it completely wiped out grub and didn't give me my windows MBR back which made me have to reinstall Ubuntu again

---

### Post by sendblink23 on 2010-03-23
> **timstone said:**
> I used sudo lilo -M /dev/sda mbr last night and it completely wiped out grub and didn't give me my windows MBR back which made me have to reinstall Ubuntu again

Yes exactly it wipes Grubs boot loader... that is what its meant to do recover Windows Boot Loader... but perfectly you gave me what i needed to know it doesn't work for Windows 7, pretty certain Vista as well(won't work)... its probably only for XP.

I hope some GURU appears to help out, I certainly want to know the new command for Recovering Windows 7 MBR

---

### Post by timstone on 2010-03-23
Well I didn't come in here looking for how to recover the windows loader....I just said that if I happen to recover it, I will just use it instead of grub.  I posted my menu.lst and fdisk info hoping someone could help me map out the Win7 partition now that it appears I have it fixed since Ubuntu is finally recognizing and mounting it.  I can't seem to figure it out....I'm also pretty much unfamiliar with modifying the menu.lst file and basically understanding how to figure out the mapping.

---

### Post by oldfred on 2010-03-23
This is the offical windows way:

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

