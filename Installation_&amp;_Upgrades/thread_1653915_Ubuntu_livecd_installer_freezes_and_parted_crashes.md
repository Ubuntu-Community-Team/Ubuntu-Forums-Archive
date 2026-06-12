---
title: "Ubuntu livecd installer freezes and parted crashes. How can I install?"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by sirspazzolot on 2010-12-27
I was trying to fix gparted (it was crashing whenever it started) and then when I would type my password in the login screen, the screen would flash back and then the login screen would come back. If I logged in in a terminal and then did startx, it would just show a black screen. I figured it was broken. I made an Ubuntu 10.10 liveCD and booted it up and clicked on the installer thing and then it froze and an error thing popped up saying Parted crashed.

Essentially what I need to do is install Ubuntu without using the partition GUI. Any recommendations? Can I try to find a thing that will let me make an empty EXT4 partition and then a thing to let me install Ubuntu to it?

thanks in advance

---

### Post by Quackers on 2010-12-27
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sirspazzolot on 2010-12-27
Running Gparted from the gparted livecd crashes. It crashes in Parted Magic, too. I'm remaking my ubuntu livecd so I'll have the output of that boot script in a few minutes. Thanks for the response.

---

### Post by sirspazzolot on 2010-12-27
Let the record show that I have some experience. I know code tags and running a bash script and such.

Here's the output of the script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 4655000 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   125,467,649   125,467,587  83 Linux
/dev/sda2         295,788,544   312,580,095    16,791,552  82 Linux swap / Solaris
/dev/sda3         230,500,620   295,772,714    65,272,095  83 Linux
/dev/sda4    *    125,470,720   230,486,015   105,015,296  af HFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     7,826,383     7,826,322   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b1e092ca-7db1-4e65-9235-349403e3f6f7   ext4                                     
/dev/sda2        2c542775-53d6-4d1d-8ed0-4a7f74c19bc1   swap                                     
/dev/sda3        459cf1a7-4838-4d24-8d8f-c1812c736c9d   ext3                                     
/dev/sda4        19786a77-d7ba-3be4-a5f3-670a3cd021d0   hfsplus    OS X                          
/dev/sda: PTTYPE="dos" 
/dev/sdc1        4D19-2CDB                              vfat       àœŽàœ&#130;àœŠàŒ                   
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
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

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 459cf1a7-4838-4d24-8d8f-c1812c736c9d
    linux /boot/vmlinuz-2.6.30.9 root=UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d ro quiet splash
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 459cf1a7-4838-4d24-8d8f-c1812c736c9d
    linux /boot/vmlinuz-2.6.30.9 root=UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d ro single
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 459cf1a7-4838-4d24-8d8f-c1812c736c9d
    linux /boot/memtest86+.bin 
}
menuentry "Mac OS X (32-bit) (on /dev/sda4)" {
    insmod part_msdos
    insmod hfsplus
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2c748d7a27d0db4c
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 2c748d7a27d0db4c uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda4)" {
    insmod part_msdos
    insmod hfsplus
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2c748d7a27d0db4c
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 2c748d7a27d0db4c uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1bea47ae-c243-455e-9ea7-29e5d6ea0022 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
  18.1GB: boot/initrd.img-2.6.35-23-generic
   3.8GB: boot/initrd.img-2.6.35-24-generic
   2.5GB: boot/vmlinuz-2.6.35-22-generic
   3.2GB: boot/vmlinuz-2.6.35-23-generic
   2.8GB: boot/vmlinuz-2.6.35-24-generic
   3.8GB: initrd.img
  18.1GB: initrd.img.old
   2.8GB: vmlinuz
   3.2GB: vmlinuz.old

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
# kopt=root=UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=459cf1a7-4838-4d24-8d8f-c1812c736c9d

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=459cf1a7-4838-4d24-8d8f-c1812c736c9d/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9
uuid        459cf1a7-4838-4d24-8d8f-c1812c736c9d
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        459cf1a7-4838-4d24-8d8f-c1812c736c9d
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        459cf1a7-4838-4d24-8d8f-c1812c736c9d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro single 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=ef7d2855-e06b-4f37-86bf-43768483f0fa none swap sw 0 0

=================== sda3: Location of files loaded by Grub: ===================


 122.5GB: boot/grub/menu.lst
 122.5GB: boot/grub/stage2
 122.1GB: boot/initrd.img-2.6.30.9
 122.5GB: boot/vmlinuz-2.6.30.9
 122.1GB: initrd.img
 122.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb 7f 03 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

My goal right now is to get gparted to work. If gparted works, then the Ubuntu installer should work. Gparted works on my BackTrack linux installation but that's and old version and an old kernel, so it doesn't recognise ext4.
I don't know if the script gave this, but I have an EXT4 partition that boots to Ubuntu, an HFS+ partition with OS X installed, a linux swap partition and an ext3 BackTrack installation (I think that's the order) sda is my hard drive and sdc is currently my USB drive that I'm using as a livecd.

---

### Post by sirspazzolot on 2010-12-27
Does anybody have any idea what's wrong with gparted? It's been broken for months. The version on the LiveCD is broken. The latest gparted livecd is also broken for me. All I want to do is reinstall Ubuntu. I have a 10.10 desktop ISO and an ext4 Ubuntu partition that I would like to overwrite. Can I reformat the partition to ext4 to wipe it clean and then install to that partition through a terminal? The GUI installer freezes and gparted crashes, but I'm not sure if it's just the GUI of gparted that isn't working, and I'm not sure if you can install to a specific premade partition through a command line. Please help me out, somebody.

---

### Post by sirspazzolot on 2010-12-27
Please help.

---

### Post by Quackers on 2010-12-27
Hi sirspazzolot, I've woken up :-)
The script looks ok except for something I notice in etc/fstab
```
=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d / ext3 relatime,errors=remount-ro 0 1
[COLOR="Red"]# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=ef7d2855-e06b-4f37-86bf-43768483f0fa none swap sw 0 0[/COLOR]
```

I'm not sure this is the cause of gparted crashing, but it doesn't look good.
From the rest of the script it looks like you've only got one swap partition, but the above entry seems to say different - or it thinks there's another swap, at least.

---

### Post by sirspazzolot on 2010-12-27
YAY. I love you. Welcome back. What do you suggest I do? I made one swap partition, and it's 8GB. That may be a bit excessive, but it's all in one chunk. However, bearing in mind how my computer has been behaving in the past few months, I wouldn't be surprised in the slightest if it went and tried to make another swap space without me noticing :P. I guess it's possible that that's what's tripping gparted up, but I don't really know what to do about it haha
I was considering copying my Backtrack installation to my external hard drive and then reformatting my whole hard drive if the Disk Utility doesn't crash, then trying to install ubuntu. That would be the most inconvenient way to fix this because I'd have to reinstall OS X and Backtrack, but at least I think it would work.

---

### Post by sirspazzolot on 2010-12-27
If it's suggesting that /dev/sda3 is a swap space, it's not. That's my BackTrack installation and I can mount and use it. Definitely not swap space. I think it's got a really old kernel though so perhaps that would somehow affect how it's seen?

---

### Post by Quackers on 2010-12-27
Hmm, not really sure :-)
I think what I'd do in a similar situation is to backup whatever I needed in Backtrack and then delete sda3 partition completely (try using Disk Utility rather than gparted). If neither Disk Utility nor gparted can see the partition I would try downloading Gparted Live cd and burn it to disc and boot from it. If that can't see it, or crashes, we'll have to think of something else.
NB If you can manage to delete sda3 you must run ```
sudo update-grub
``` from a terminal or nothing will boot afterwards!

I don't think it's saying sda3 is a swap space, but I think it's saying it holds a swap space -maybe!
The point is at least part of sda3 appears to be an "UNKNOWN DEVICE"

---

### Post by sirspazzolot on 2010-12-28
I tried to delete it and disk manager said
> Sorry, the program "udisks-helper-delete-partition" closed unexpectedly
So I don't think that'll work. Instead, I reformatted it to FAT. Now that that's been done I re-ran the script and now that gives:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 4655000 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 230500620.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   125,467,649   125,467,587  83 Linux
/dev/sda2         295,788,544   312,580,095    16,791,552  82 Linux swap / Solaris
/dev/sda3         230,500,620   295,772,714    65,272,095  83 Linux
/dev/sda4    *    125,470,720   230,486,015   105,015,296  af HFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     7,826,383     7,826,322   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b1e092ca-7db1-4e65-9235-349403e3f6f7   ext4                                     
/dev/sda2        2c542775-53d6-4d1d-8ed0-4a7f74c19bc1   swap                                     
/dev/sda3        090B-4968                              vfat       Thing                         
/dev/sda4        19786a77-d7ba-3be4-a5f3-670a3cd021d0   hfsplus    OS X                          
/dev/sda: PTTYPE="dos" 
/dev/sdc1        4D19-2CDB                              vfat       à&#339;&#381;à&#339;‚à&#339;&#352;à&#338;                   
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
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

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1e092ca-7db1-4e65-9235-349403e3f6f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 459cf1a7-4838-4d24-8d8f-c1812c736c9d
    linux /boot/vmlinuz-2.6.30.9 root=UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d ro quiet splash
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 459cf1a7-4838-4d24-8d8f-c1812c736c9d
    linux /boot/vmlinuz-2.6.30.9 root=UUID=459cf1a7-4838-4d24-8d8f-c1812c736c9d ro single
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 459cf1a7-4838-4d24-8d8f-c1812c736c9d
    linux /boot/memtest86+.bin 
}
menuentry "Mac OS X (32-bit) (on /dev/sda4)" {
    insmod part_msdos
    insmod hfsplus
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2c748d7a27d0db4c
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 2c748d7a27d0db4c uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda4)" {
    insmod part_msdos
    insmod hfsplus
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 2c748d7a27d0db4c
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 2c748d7a27d0db4c uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=b1e092ca-7db1-4e65-9235-349403e3f6f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1bea47ae-c243-455e-9ea7-29e5d6ea0022 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
  18.1GB: boot/initrd.img-2.6.35-23-generic
   3.8GB: boot/initrd.img-2.6.35-24-generic
   2.5GB: boot/vmlinuz-2.6.35-22-generic
   3.2GB: boot/vmlinuz-2.6.35-23-generic
   2.8GB: boot/vmlinuz-2.6.35-24-generic
   3.8GB: initrd.img
  18.1GB: initrd.img.old
   2.8GB: vmlinuz
   3.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb 7f 03 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```
sudo update-grub gave 
```
 /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
```
The unknown stuff appears to be gone. I'll try GParted now. *crosses fingers*

---

### Post by sirspazzolot on 2010-12-28
crashed. rats

---

### Post by Quackers on 2010-12-28
What system are you booted into now?

---

### Post by sirspazzolot on 2010-12-28
Ubuntu LiveCD

---

### Post by sirspazzolot on 2010-12-28
Should I just reformat the whole damn drive to ext4 and then try to install Ubuntu? I really don't know.

---

### Post by Quackers on 2010-12-28
I thought you were booted into Ubuntu. oops
Try these commands, one at a time in the terminal
```
sudo mkdir /mnt/temp
sudo mount /dev/sda1 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

At this point your terminal prompt should change from ubuntu@ubuntu to root@ubuntu - if things went well :-)
type in ```
update-grub
``` and hit enter. Then, after it's finished, try rebooting into your proper system.

---

### Post by sirspazzolot on 2010-12-28
Okay. GRUB updated. I'll try to restart into Ubuntu but the reason all of this crazy crap started happening is because Ubuntu was stuck in an infinite loop at the log-in screen. Entering my password would make the screen go black and then bring the log-in screen back up. Logging in through a terminal and then doing startx made it just go to a black screen.

---

### Post by Quackers on 2010-12-28
I honestly don't know whether that will be any different, but I would suspect and hope that you can now re-install, at least.
Have you tried a separate thread with just that question? Maybe if it still doesn't boot you could try that and see if anything is offered as a solution to that. There are many extremely knowledgable Ubuntuists here :-)

---

### Post by sirspazzolot on 2010-12-28
I made a thread about that initially and got no responses. I suppose I'll try again. Thanks for all your assistance!

---

### Post by Quackers on 2010-12-28
Ah, ok. I hope things have improved :-)
You're welcome.

---

