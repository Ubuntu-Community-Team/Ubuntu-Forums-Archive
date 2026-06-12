---
title: "update manager bug"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Idiens on 2010-07-02
I hit the upgrade button on the 9.10 update manager. After much down loading, the upgrade to 10.04 LTS started but returned many missing file errors before crashing.  Now the computer will not boot under Linux at all. I guess I have lost everything.

Any advice?

---

### Post by dino99 on 2010-07-02
a clean install might be the choice now

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Rubi1200 on 2010-07-02
> **Idiens said:**
> I hit the upgrade button on the 9.10 update manager. After much down loading, the upgrade to 10.04 LTS started but returned many missing file errors before crashing.  Now the computer will not boot under Linux at all. I guess I have lost everything.

Any advice?

Use the Ubuntu CD and boot into live mode (in other words try not install) and see a) if you can save any of your files etc. and 2) click on the link at the bottom of my post and follow the instructions before posting back here. Who knows, maybe something could still be saved.

Good luck!

---

### Post by Idiens on 2010-07-03
Thanks Guys,

I managed to run your script Rudi, from an 8.10 version locked in the machine after installing 9.10, here are the results (I hope as an attachment).

---

### Post by Rubi1200 on 2010-07-03
Ok, here is the text for all to see:

           ```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       369,494       369,432  de Dell Utility
/dev/sda2             370,688    31,827,967    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,827,968   241,709,409   209,881,442   7 HPFS/NTFS
/dev/sda4         241,713,990   488,392,064   246,678,075   5 Extended
/dev/sda5         483,171,003   488,038,634     4,867,632  83 Linux
/dev/sda6         488,038,698   488,392,064       353,367  82 Linux swap / Solaris
/dev/sda7         241,714,116   473,274,899   231,560,784  83 Linux
/dev/sda8         473,274,963   483,170,939     9,895,977  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   6262-3236                              vfat                                     
/dev/sda1        07D9-051D                              vfat       DellUtility                   
/dev/sda2        14FAEB96FAEB7282                       ntfs       RECOVERY                      
/dev/sda3        8CFAEEC4FAEEAA22                       ntfs       OS                            
/dev/sda5        ee74b83e-9ab5-43b4-b611-9923b97f9a25   ext3                                     
/dev/sda6        cb761207-14ee-496f-be58-3229671a4566   swap                                     
/dev/sda7        04be1d80-b2ef-4cb0-a818-4e5817460fb0   ext3                                     
/dev/sda8        031bef12-56ad-4d68-94bf-cf124aa0dac5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/scd1        /media/SFR               iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/mmcblk0p1   /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
# kopt=root=UUID=ee74b83e-9ab5-43b4-b611-9923b97f9a25 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ee74b83e-9ab5-43b4-b611-9923b97f9a25

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        ee74b83e-9ab5-43b4-b611-9923b97f9a25
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ee74b83e-9ab5-43b4-b611-9923b97f9a25 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        ee74b83e-9ab5-43b4-b611-9923b97f9a25
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ee74b83e-9ab5-43b4-b611-9923b97f9a25 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        ee74b83e-9ab5-43b4-b611-9923b97f9a25
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
chainloader    +1


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
UUID=ee74b83e-9ab5-43b4-b611-9923b97f9a25 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cb761207-14ee-496f-be58-3229671a4566 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 249.2GB: boot/grub/menu.lst
 248.2GB: boot/grub/stage2
 249.5GB: boot/initrd.img-2.6.27-7-generic
 249.5GB: boot/vmlinuz-2.6.27-7-generic
 249.5GB: initrd.img
 249.5GB: vmlinuz

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
# kopt=root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=04be1d80-b2ef-4cb0-a818-4e5817460fb0

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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, memtest86+
uuid        04be1d80-b2ef-4cb0-a818-4e5817460fb0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ee74b83e-9ab5-43b4-b611-9923b97f9a25 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ee74b83e-9ab5-43b4-b611-9923b97f9a25 ro single 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=04be1d80-b2ef-4cb0-a818-4e5817460fb0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=031bef12-56ad-4d68-94bf-cf124aa0dac5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 146.9GB: boot/grub/menu.lst
 146.9GB: boot/grub/stage2
 146.9GB: boot/initrd.img-2.6.31-17-generic
 146.9GB: boot/initrd.img-2.6.31-19-generic
 147.6GB: boot/initrd.img-2.6.31-20-generic
 147.6GB: boot/initrd.img-2.6.31-21-generic
 146.9GB: boot/initrd.img-2.6.31-22-generic
 146.8GB: boot/vmlinuz-2.6.31-17-generic
 146.9GB: boot/vmlinuz-2.6.31-19-generic
 147.6GB: boot/vmlinuz-2.6.31-20-generic
 147.2GB: boot/vmlinuz-2.6.31-21-generic
 146.8GB: boot/vmlinuz-2.6.31-22-generic
 146.9GB: boot/vmlinuz-2.6.32-23-generic
 146.9GB: initrd.img
 147.6GB: initrd.img.old
 146.8GB: vmlinuz
 147.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Rubi1200 on 2010-07-03
The problem here is that 10.04 uses GRUB2 whereas 8.10 uses GRUB-legacy.

```
Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
```

Under normal circumstances I would recommend reinstalling GRUB to the MBR.
However, I have no experience dealing with situations where there is a recovery utility on sda1.

I suggest you wait until one of the more experienced members comes along with a suggestion.

And, to answer your initial question; no, I do not think everything is lost.

Hang in there please.

:)

---

### Post by Idiens on 2010-07-05
Thanks for the encouragement and help Rubi.  :popcorn:

---

