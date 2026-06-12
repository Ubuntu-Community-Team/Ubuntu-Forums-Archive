---
title: "Installed OpenSUSE 11.3 and can't boot Ubuntu - Error 15 : File not found"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by pariate369 on 2010-11-16
Hi

Decided I'd like to take a look at OpenSUSE and installed onto my desktop.  Already successfully dual booting Ubuntu 10.10 and Windows XP (which I keep purely for iTunes).  

When I start the PC the Ubuntu grub menu showing Ubuntu and Windows options has been replaced by a Suse-branded screen showing something that looks (to my untrained eye) like a grub menu.  Ubuntu and Suse are listed.  If I select Ubuntu I am shown a dos screen with "Error 15: file not found".  I am then taken to the old Ubuntu grub screen but trying to boot Ubuntu from that menu returns the same error.  

I know all the data is still there - I can mount the drive in Suse and view all my documents.  


I have searched the forums and tried to follow some of the instructions given in response to similar threads but I'm afraid I didn't get very far.  Please assume that I have NO PRIOR KNOWLEDGE of Linux!  I really know nothing about it and am only just getting to grips with basic terminal commands.  Goodness knows why I thought OpenSUSE would be a good idea... 

Any help would be greatly appreciated.

Thank you!


I found instructions for running Boot Info Script and these are the results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 439464928 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:      Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  
    Boot files/dirs:   
sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    51,199,999    51,199,937   7 HPFS/NTFS
/dev/sda2    *     51,202,046   488,392,064   437,190,019   5 Extended
/dev/sda5         278,759,943   433,640,944   154,881,002  83 Linux
/dev/sda6         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris
/dev/sda7          51,202,048   269,422,591   218,220,544  83 Linux
/dev/sda8         269,424,640   278,759,423     9,334,784  82 Linux swap / Solaris
/dev/sda9         433,641,472   453,144,575    19,503,104  83 Linux
/dev/sda10        453,146,624   482,381,823    29,235,200  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   321,669,494   321,669,432   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       06c20eb0-34db-4c7d-87db-f3388be8fdda   ext4                                     
/dev/sda1        33061DF03C2DC188                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1c4f25d2-361a-4809-921f-c4001d18cd75   ext3                                     
/dev/sda6        4e7ce2f6-151c-48e2-9826-7034f6a9d90c   swap                                     
/dev/sda7        4e21dbd0-7860-42fc-89b4-c0d33f31244f   ext4                                     
/dev/sda8        d5fe0d8f-7461-46b6-9ad2-9ea3ac76d578   swap                                     
/dev/sda9        28d996ae-a541-4212-971c-2c47714a900a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        02AA-04A2                              vfat       IOMEGA160GB                   
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,acl,user_xattr)
/dev/sda10       /home                    ext4       (rw,acl,user_xattr)
/dev/sda1        /windows/C               fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/1c4f25d2-361a-4809-921f-c4001d18cd75 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/4e21dbd0-7860-42fc-89b4-c0d33f31244f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /media/LXFDVDS23         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=100,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1        /media/IOMEGA160GB       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=100,shortname=mixed,dmask=0077,utf8=1,flush)


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
default         2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# kopt=root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1c4f25d2-361a-4809-921f-c4001d18cd75

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
# defoptions=splash vga=769

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
# howmany=8

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        1c4f25d2-361a-4809-921f-c4001d18cd75
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro splash vga=769 
initrd        /boot/initrd.img-2.6.35-22-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        1c4f25d2-361a-4809-921f-c4001d18cd75
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.32-24-generic
uuid        1c4f25d2-361a-4809-921f-c4001d18cd75
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro splash vga=769 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode)
uuid        1c4f25d2-361a-4809-921f-c4001d18cd75
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Chainload into GRUB 2
root        1c4f25d2-361a-4809-921f-c4001d18cd75
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        1c4f25d2-361a-4809-921f-c4001d18cd75
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
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
UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4e7ce2f6-151c-48e2-9826-7034f6a9d90c none            swap    sw              0       0
/dev/sr1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 182.4GB: boot/grub/core.img
 182.4GB: boot/grub/menu.lst
 182.4GB: boot/grub/stage2
 182.4GB: boot/initrd.img-2.6.32-24-generic
 182.3GB: boot/initrd.img-2.6.35-22-generic
 182.4GB: boot/vmlinuz-2.6.32-24-generic
 182.3GB: boot/vmlinuz-2.6.35-22-generic
 182.3GB: initrd.img
 182.3GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4e21dbd0-7860-42fc-89b4-c0d33f31244f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4e21dbd0-7860-42fc-89b4-c0d33f31244f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4e21dbd0-7860-42fc-89b4-c0d33f31244f
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10, 2.6.35-22-generic-pae (/dev/sda7)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4e21dbd0-7860-42fc-89b4-c0d33f31244f
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=4e21dbd0-7860-42fc-89b4-c0d33f31244f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Linux Mint 10, 2.6.35-22-generic-pae (/dev/sda7) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4e21dbd0-7860-42fc-89b4-c0d33f31244f
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=4e21dbd0-7860-42fc-89b4-c0d33f31244f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4e21dbd0-7860-42fc-89b4-c0d33f31244f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4e21dbd0-7860-42fc-89b4-c0d33f31244f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 33061df03c2dc188
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1c4f25d2-361a-4809-921f-c4001d18cd75
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro splash vga=769
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1c4f25d2-361a-4809-921f-c4001d18cd75
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.32-24-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1c4f25d2-361a-4809-921f-c4001d18cd75
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro splash vga=769
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1c4f25d2-361a-4809-921f-c4001d18cd75
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=1c4f25d2-361a-4809-921f-c4001d18cd75 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Chainload into GRUB 2 (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1c4f25d2-361a-4809-921f-c4001d18cd75
    linux /boot/grub/core.img 
}
menuentry "Ubuntu 10.10, memtest86+ (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1c4f25d2-361a-4809-921f-c4001d18cd75
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=4e21dbd0-7860-42fc-89b4-c0d33f31244f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d5fe0d8f-7461-46b6-9ad2-9ea3ac76d578 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  52.1GB: boot/grub/core.img
  73.7GB: boot/grub/grub.cfg
  26.8GB: boot/initrd.img-2.6.35-22-generic-pae
  52.1GB: boot/vmlinuz-2.6.35-22-generic-pae
  26.8GB: initrd.img
  52.1GB: vmlinuz

=========================== sda9/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Tue Nov 16 17:32:28 GMT 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 1
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,8)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title GNU GRUB 2 -- openSUSE 11.3 - GNU GRUB 2
    kernel (hd0,8)/boot/grub2/core.img root=/dev/disk/by-id/ata-WDC_WD2500JS-55NCB1_WD-WCANK1418074-part9 resume=/dev/sda8 splash=silent quiet showopts vga=0x317

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.3
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.34-12-default root=/dev/sda9 resume=/dev/sda8 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.34-12-default

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 10.10, kernel 2.6.32-24-generic (/dev/sda5)###
title Ubuntu 10.10, kernel 2.6.32-24-generic (/dev/sda5)
    root (hd0,4)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.3
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.34-12-default root=/dev/sda9 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.34-12-default

=============================== sda9/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD2500JS-55NCB1_WD-WCANK1418074-part6 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD2500JS-55NCB1_WD-WCANK1418074-part8 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD2500JS-55NCB1_WD-WCANK1418074-part9 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD2500JS-55NCB1_WD-WCANK1418074-part10 /home                ext4       acl,user_xattr        1 2
/dev/disk/by-id/ata-WDC_WD2500JS-55NCB1_WD-WCANK1418074-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_GB.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda9: Location of files loaded by Grub: ===================


 224.3GB: boot/grub/menu.lst
 225.0GB: boot/grub/stage2
 225.1GB: boot/initrd
 225.1GB: boot/initrd-2.6.34-12-default
 224.9GB: boot/vmlinuz
 224.9GB: boot/vmlinuz-2.6.34-12-default
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

  /dev/sdb: open failed: No medium found
  No volume groups found
mdadm: No arrays found in config file or automatically

---

### Post by Rubi1200 on 2010-11-17
I see that you have not received any responses yet, so I am going to have a crack at it.

However, I would like to mention, in advance, that you have a rather odd setup and I suggest you wait for other opinions before proceeding.

First, some of the problems:
> Acer 3 is installed in the MBR of /dev/sdaI assume Windows can still boot normally or is it being controlled by the bootloader that was installed with OpenSuse?

sda2:
> Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 439464928 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.You say that OpenSuse offers you boot options, but I have never seen booting being done from an extended partition.

You also have Linux Mint installed; are you able to boot into this?

Ubuntu is installed on sda5, but I don't see where you are booting it from unless the OpenSuse install is picking it up.

Next, have you tried booting into OpenSuse and running the ```
sudo update-grub
``` command to pick up all the operating systems?

You also seem to have a mixture of GRUB-legacy and GRUB2 boot files (which is almost certainly a cause of problems) on the Ubuntu, Mint, and OpenSuse installs.

I recommend you make a decision as to which bootloader to use; GRUB-legacy or GRUB2.

Personally, I think that GRUB2 is the way to go because both Mint and Ubuntu use it.

The problem I have, which is why I advise you to wait for other opinions, is that I am not sure if you can simply purge and reinstall GRUB to the MBR without causing problems because of the boot files on the extended partition.

Sorry for the long-winded post, but I hope others will contribute and help you get things up and running the way you want.

---

