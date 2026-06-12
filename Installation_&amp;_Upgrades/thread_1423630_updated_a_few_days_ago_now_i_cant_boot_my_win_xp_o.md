---
title: "updated a few days ago now i cant boot my win xp or win 7"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by aussietazza on 2010-03-06
My 9.10 updated a few days ago now i cant boot my win xp or win 7
it says ERROR : Invalid Signature IT was Fine Before the update
Please Help

---

### Post by Phylax Aranatis on 2010-03-06
Hi there,

you may want to consider the followind Thread: [http://ubuntuforums.org/showthread.php?t=1264151](http://ubuntuforums.org/showthread.php?t=1264151)

Posting your /boot/grub/menu.lst and the output of "sudo blkid" should also be helpful

greetz from Bavaria

Phylax

---

### Post by aussietazza on 2010-03-06
here are my results

---

### Post by aussietazza on 2010-03-06
[LEFT]```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7e61057

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   390,443,759   390,443,697   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006c1e9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,575,759   312,575,697   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006275e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdc2         204,797,952   414,760,070   209,962,119   7 HPFS/NTFS
/dev/sdc3         414,766,170   625,137,344   210,371,175   5 Extended
/dev/sdc5         414,766,233   616,494,374   201,728,142  83 Linux
/dev/sdc6         616,494,438   625,137,344     8,642,907  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00f65bfe

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8C374AC4A186F941                       ntfs       IDE 200                       
/dev/sdb1        EED7CB88191A4024                       ntfs       150                           
/dev/sdc1        D67CAFF67CAFD013                       ntfs                                     
/dev/sdc2        4A306FE6306FD789                       ntfs                                     
/dev/sdc5        9958fc32-278a-4867-b29f-99adb5dbecb5   ext4                                     
/dev/sdc6        f1f0bdaf-244e-42fa-a7ac-4db7e28eb952   swap                                     
/dev/sdd1        B84857CA485785D2                       ntfs       1TB                           

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext4       (rw,errors=remount-ro)
/dev/sdd1        /media/1TB               fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/150               fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/IDE 200           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /media/D67CAFF67CAFD013  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc2        /media/4A306FE6306FD789  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sdc1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdc5/boot/grub/menu.lst: ===========================

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
timeout        3

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
# kopt=root=UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9958fc32-278a-4867-b29f-99adb5dbecb5

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
uuid        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        9958fc32-278a-4867-b29f-99adb5dbecb5
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdc5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdc5 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-19-generic root=/dev/sdc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-19-generic root=/dev/sdc5 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=9958fc32-278a-4867-b29f-99adb5dbecb5 /               ext4    errors=remount-ro 0       1
UUID=f1f0bdaf-244e-42fa-a7ac-4db7e28eb952 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 225.4GB: boot/grub/core.img
 217.3GB: boot/grub/grub.cfg
 216.2GB: boot/grub/menu.lst
 212.9GB: boot/initrd.img-2.6.31-14-generic
 214.2GB: boot/initrd.img-2.6.31-19-generic
 216.3GB: boot/initrd.img-2.6.31-20-generic
 212.8GB: boot/vmlinuz-2.6.31-14-generic
 212.9GB: boot/vmlinuz-2.6.31-19-generic
 214.4GB: boot/vmlinuz-2.6.31-20-generic
 216.3GB: initrd.img
 214.2GB: initrd.img.old
 214.4GB: vmlinuz
 212.9GB: vmlinuz.old
```[/LEFT]

---

### Post by lidex on 2010-03-07
It's worth a try running these commands:
```
sudo grub-mkdevicemap
sudo update-grub
```

Those are terminal commands: "Applications>Accessories>Terminal"

Now reboot.

---

### Post by aussietazza on 2010-03-07
thanks but still not booting windows

---

### Post by oldfred on 2010-03-07
If windows was on sda the simple chainboot may work, but it is on sdc so you need to map the drive in grub. grub2 normally does this, did you edit it?

Add this to /etc/grub.d/40_custom
then do:
sudo update-grub

menuentry "Windows XP/7 on sdc1" {
       insmod ntfs
       set root=(hd2,1)
       search --no-floppy --fs-uuid --set D67CAFF67CAFD013
       drivemap -s (hd0) ${root}
       chainloader +1
}

---

