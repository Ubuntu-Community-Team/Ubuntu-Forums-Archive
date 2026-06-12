---
title: "Messed up triple boot system"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by Modreduk on 2010-07-18
Hey all, after finally biting the bullet and deciding to install both Ubuntu and Leopard on my PC I have run into a problem, namely that I can only boot into Ubuntu. I have Windows 7 on my primary HD and Leopard and Ubuntu on a 2nd HD with a mass of data on a third. I have attempted to boot from my Windows installation CD but it freezes at the splash page so no use there and when I try to boot from the boot menu I am getting a no such device error.

I rather think I have over complicated things by trying to use EasyBCD when I was in Windows and then getting the wrong setting when I re-installed Ubuntu to try and fix the boot issues.

Boot Info Script gives me this but now I have to defer to greater minds than mine for help, I'm stuck.

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1       409,639       409,639  ee GPT
/dev/sdb2             409,640   156,438,527   156,028,888  af HFS
/dev/sdb3         156,702,720   306,141,183   149,438,464   c W95 FAT32 (LBA)
/dev/sdb4         306,141,184   312,580,095     6,438,912  82 Linux swap / Solaris


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              40       409,639       409,600 System/Boot Partition
/dev/sdb2         409,640   156,438,527   156,028,888 HFS+
/dev/sdb3     156,700,672   156,702,719         2,048 Bios Boot Partition
/dev/sdb4     156,702,720   306,141,183   149,438,464 Linux or Data
/dev/sdb5     306,141,184   312,580,095     6,438,912 Linux Swap

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        381498061497C572                       ntfs       Windows                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3F3C-1AF6                              vfat       EFI                           
/dev/sdb2        7bf0a18c-f64b-3ec6-a25c-b20198d318c7   hfsplus    Leopard                       
/dev/sdb4        7e0f29ca-2289-44d1-8065-ac014bd4a25a   ext4                                     
/dev/sdb5        01dd2d4d-d6f5-4619-a95f-82889243697f   swap                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        A8F046A8F0467C96                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb4        /                        ext4       (rw,errors=remount-ro)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# [http://neosmart.net/wiki/display/EBCD/](http://neosmart.net/wiki/display/EBCD/) 
 

=========================== sdb4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=7e0f29ca-2289-44d1-8065-ac014bd4a25a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7e0f29ca-2289-44d1-8065-ac014bd4a25a

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic-pae
uuid        7e0f29ca-2289-44d1-8065-ac014bd4a25a
kernel        /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=7e0f29ca-2289-44d1-8065-ac014bd4a25a ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic-pae

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic-pae (recovery mode)
uuid        7e0f29ca-2289-44d1-8065-ac014bd4a25a
kernel        /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=7e0f29ca-2289-44d1-8065-ac014bd4a25a ro  single
initrd        /boot/initrd.img-2.6.32-23-generic-pae

title        Chainload into GRUB 2
root        7e0f29ca-2289-44d1-8065-ac014bd4a25a
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        7e0f29ca-2289-44d1-8065-ac014bd4a25a
kernel        /boot/memtest86+.bin

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title Windows 7
root (hd0,1)
savedefault
makeactive
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set 7e0f29ca-2289-44d1-8065-ac014bd4a25a
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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set 7e0f29ca-2289-44d1-8065-ac014bd4a25a
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set 7e0f29ca-2289-44d1-8065-ac014bd4a25a
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=7e0f29ca-2289-44d1-8065-ac014bd4a25a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set 7e0f29ca-2289-44d1-8065-ac014bd4a25a
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=7e0f29ca-2289-44d1-8065-ac014bd4a25a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set 7e0f29ca-2289-44d1-8065-ac014bd4a25a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set 7e0f29ca-2289-44d1-8065-ac014bd4a25a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 381498061497c572
    chainloader +1
}
menuentry "Mac OS X (32-bit) (on /dev/sdb2)" {
    insmod hfsplus
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 1fac5256d0835552
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 1fac5256d0835552 uuid
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
menuentry "Mac OS X (64-bit) (on /dev/sdb2)" {
    insmod hfsplus
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 1fac5256d0835552
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 1fac5256d0835552 uuid
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

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc4 during installation
UUID=7e0f29ca-2289-44d1-8065-ac014bd4a25a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=01dd2d4d-d6f5-4619-a95f-82889243697f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb4: Location of files loaded by Grub: ===================


  82.5GB: boot/grub/core.img
 140.5GB: boot/grub/grub.cfg
  82.5GB: boot/grub/menu.lst
  82.6GB: boot/initrd.img-2.6.32-23-generic-pae
  82.5GB: boot/vmlinuz-2.6.32-23-generic-pae
  82.6GB: initrd.img
  82.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh sdi 

---

### Post by Modreduk on 2010-07-18
Update.

I now have Ubuntu and Windows running and hopefully should get Leopard working soon although I do have a rather annoying second boot screen from grub after the windows boot options but hey, sure I'll find my way around it.

---

