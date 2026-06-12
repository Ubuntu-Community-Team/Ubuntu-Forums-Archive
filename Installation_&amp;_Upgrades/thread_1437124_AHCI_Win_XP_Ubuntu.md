---
title: "AHCI /Win XP/ Ubuntu"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by pip601 on 2010-03-23
Okay, here is what I did. Installed XP in AHCI mode, everything worked like a champ. then installed Ubuntu 9.1, split the disk in 1/2, used GRUB as bootloader, and upgraded Ubuntu to 9.2 before going back to check and to see if windows will still boot. 
It won't....in AHCI mode, grub loads, and boots ubuntu just fine. If I choose Windows, it starts, but then automatically reboots. None of the choices work (safe mode or other). 

If i change to non-ahci, grub doesn't load, gives a no valid disks found. 

I have done this before on these Optiplex 755 without a problem...what did I do wrong this time and can I fix it without starting over?
Thanks in advance -Pip

---

### Post by King_Ragger on 2010-03-23
Did you repartition your hdd into two separate partitions before installing? If you didn't resizing partitions can cause a lot of problems with existing data.

When I install my WinXP and Ubuntu side by side I completely repartition my drive. I create my XP partition and leave the rest of the drive blank for my Ubuntu install. I haven't had any problem with this method yet.

---

### Post by pip601 on 2010-03-23
I did not, i used the ubuntu installer to shrink the windows partition, but I have done this numerous times this way without a problem

> **King_Ragger said:**
> Did you repartition your hdd into two separate partitions before installing? If you didn't resizing partitions can cause a lot of problems with existing data.

When I install my WinXP and Ubuntu side by side I completely repartition my drive. I create my XP partition and leave the rest of the drive blank for my Ubuntu install. I haven't had any problem with this method yet.

---

### Post by prodigy_ on 2010-03-23
D/l and run [bootinfo script](http://bootinfoscript.sourceforge.net/) and post its complete output.

---

### Post by pip601 on 2010-03-25
> **prodigy_ said:**
> D/l and run [bootinfo script]("http://bootinfoscript.sourceforge.net/") and post its complete output.
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650   243,416,879   243,256,230   7 HPFS/NTFS
/dev/sda3         243,416,880   488,279,609   244,862,730   5 Extended
/dev/sda5         243,416,943   478,238,984   234,822,042  83 Linux
/dev/sda6         478,239,048   488,279,609    10,040,562  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07DA-0115                              vfat       DellUtility                   
/dev/sda2        CE30B2EA30B2D923                       ntfs                                     
/dev/sda5        2847c070-9e28-4610-9255-720a72cde7e5   ext3                                     
/dev/sda6        be1669c1-2d20-4be2-8e2a-963f920ec471   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=2847c070-9e28-4610-9255-720a72cde7e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2847c070-9e28-4610-9255-720a72cde7e5

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        2847c070-9e28-4610-9255-720a72cde7e5
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=2847c070-9e28-4610-9255-720a72cde7e5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        2847c070-9e28-4610-9255-720a72cde7e5
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=2847c070-9e28-4610-9255-720a72cde7e5 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        2847c070-9e28-4610-9255-720a72cde7e5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2847c070-9e28-4610-9255-720a72cde7e5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        2847c070-9e28-4610-9255-720a72cde7e5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2847c070-9e28-4610-9255-720a72cde7e5 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        2847c070-9e28-4610-9255-720a72cde7e5
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
rootnoverify    (hd0,1)
savedefault
makeactive
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
UUID=2847c070-9e28-4610-9255-720a72cde7e5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=be1669c1-2d20-4be2-8e2a-963f920ec471 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 213.2GB: boot/grub/menu.lst
 213.2GB: boot/grub/stage2
 213.2GB: boot/initrd.img-2.6.28-11-generic
 213.2GB: boot/initrd.img-2.6.31-20-generic
 213.2GB: boot/vmlinuz-2.6.28-11-generic
 213.2GB: boot/vmlinuz-2.6.31-20-generic
 213.2GB: initrd.img
 213.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by pip601 on 2010-03-30
Anybody have any suggestions based on the results?

---

### Post by prodigy_ on 2010-03-31
I see no problem with the Grub config. The fact that you can boot into Ubuntu indicates that something is wrong with your Windows partition. Did you resize it? Anyway, first of all, try this:

1. Boot from your XP installation CD into recovery console.

2. Use the following command:
```
FIXBOOT C:
```

---

### Post by pip601 on 2010-03-31
Thanks prodigy_, but that did not help. 
Here is where there is a conflict:
Bios setting is AHCI- windows tries to boot but immediately restarts about 2 seconds into xp splash screen. Ubuntu loads without a problem
Bios setting is ata- no boot device found. 

I'm thinking i am going to have to start over with windows in ata mode- ?

---

### Post by prodigy_ on 2010-04-02
If fixboot didn't help, I suggest you to reinstall Windows. **In the long run** it's the least painful option.

(Sorry for not replying sooner.)

---

### Post by pip601 on 2010-04-05
Well...i did that, no go. I started from scratch again..made sure the BIOS was in ATA mode for the XP isntallation. Installed XP without a problem, then installed Ubuntu. Upon reboot, I get the No boot device availale- this is before GRUB. I have again attached the most current results.txt file from bootinfoscript.
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650   244,878,794   244,718,145   7 HPFS/NTFS
/dev/sda3         244,878,795   488,279,609   243,400,815   5 Extended
/dev/sda5         244,878,858   478,303,244   233,424,387  83 Linux
/dev/sda6         478,303,308   488,279,609     9,976,302  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07DA-0115                              vfat       DellUtility                   
/dev/sda2        6CAC5DB7AC5D7C90                       ntfs                                     
/dev/sda5        a7bd7c13-5478-4888-8d96-d4d06982af52   ext3                                     
/dev/sda6        b96c53f6-9950-4b37-9ce2-17527ab7566d   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=a7bd7c13-5478-4888-8d96-d4d06982af52 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a7bd7c13-5478-4888-8d96-d4d06982af52

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a7bd7c13-5478-4888-8d96-d4d06982af52
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a7bd7c13-5478-4888-8d96-d4d06982af52 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a7bd7c13-5478-4888-8d96-d4d06982af52
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a7bd7c13-5478-4888-8d96-d4d06982af52 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a7bd7c13-5478-4888-8d96-d4d06982af52
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
rootnoverify    (hd0,1)
savedefault
makeactive
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
UUID=a7bd7c13-5478-4888-8d96-d4d06982af52 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b96c53f6-9950-4b37-9ce2-17527ab7566d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 173.8GB: boot/grub/menu.lst
 173.8GB: boot/grub/stage2
 173.7GB: boot/initrd.img-2.6.28-11-generic
 173.7GB: boot/vmlinuz-2.6.28-11-generic
 173.7GB: initrd.img
 173.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

