---
title: "no such device: error from boot but Nautilus sees it OK"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by cpmman on 2010-12-22
I have an external usb disc which contains some operating systems and user data.  Having tried various methods from this forum and google followed by update-grub etc. the boot menu shows the os details but gives the following error messages when selected:

Natty
```
error: no such device: 5bca1844-fdc0-4a0d-8d26-1dd231a42d55.
error: hd1,msdos1 cannot get C/H/S values.
error: you need to load the kernel first.

Press any key to continue ...
```Maverick
```
error: no such device: 0b3e4853-09d2-49de-93ec-4ae00b35662f.
error: hd1,msdos6 cannot get C/H/S values.
error: you need to load the kernel first.

Press any key to continue ...
```The disc is mounted when logged in to the internal disc Maverick and I can access the files for read and write from there.

Here is the latest RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda3 has 0 
                       sectors.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    38,106,179    38,106,117   c W95 FAT32 (LBA)
/dev/sda2          38,106,180    48,822,976    10,716,797  83 Linux
/dev/sda3          58,589,055    58,605,119        16,065  1e Hidden W95 FAT16 (LBA)
/dev/sda4          48,824,318    58,587,135     9,762,818   5 Extended
/dev/sda5          48,824,320    58,587,135     9,762,816  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    20,964,824    20,964,762  83 Linux
/dev/sdb2         195,454,975   625,141,759   429,686,785   5 Extended
/dev/sdb5         195,454,976   432,534,683   237,079,708  83 Linux
/dev/sdb6         432,535,552   617,218,047   184,682,496  83 Linux
/dev/sdb7         617,220,096   625,141,759     7,921,664  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2629-16F0                              vfat       ACER                          
/dev/sda2        a552c2f1-288d-4f1b-ac4f-eb649d161b43   ext4                                     
/dev/sda3        3D4D-16F1                              vfat       ACER_SERVIC                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        53e3a404-913e-4485-a890-19518ae190e8   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5bca1844-fdc0-4a0d-8d26-1dd231a42d55   ext4       XMD1                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        b3b4c609-ac22-43d5-a131-5623827f6cf4   ext4                                     
/dev/sdb6        0b3e4853-09d2-49de-93ec-4ae00b356b2f   ext4                                     
/dev/sdb7        03a25ca9-4ac6-4a76-a7a0-bc7210aa7ff3   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sdb6        /media/0b3e4853-09d2-49de-93ec-4ae00b356b2f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/XMD1              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/b3b4c609-ac22-43d5-a131-5623827f6cf4 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set a552c2f1-288d-4f1b-ac4f-eb649d161b43
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set a552c2f1-288d-4f1b-ac4f-eb649d161b43
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a552c2f1-288d-4f1b-ac4f-eb649d161b43
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=a552c2f1-288d-4f1b-ac4f-eb649d161b43 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a552c2f1-288d-4f1b-ac4f-eb649d161b43
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=a552c2f1-288d-4f1b-ac4f-eb649d161b43 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a552c2f1-288d-4f1b-ac4f-eb649d161b43
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a552c2f1-288d-4f1b-ac4f-eb649d161b43
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a552c2f1-288d-4f1b-ac4f-eb649d161b43 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=53e3a404-913e-4485-a890-19518ae190e8 /home           ext4    defaults        0       2

=================== sda2: Location of files loaded by Grub: ===================


  22.2GB: boot/grub/core.img
  21.2GB: boot/grub/grub.cfg
  23.1GB: boot/initrd.img-2.6.35-24-generic
  23.1GB: boot/vmlinuz-2.6.35-24-generic
  23.1GB: initrd.img
  23.1GB: vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5bca1844-fdc0-4a0d-8d26-1dd231a42d55

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

title        Ubuntu natty (development branch), kernel 2.6.36-1-generic-pae
uuid        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/vmlinuz-2.6.36-1-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro quiet splash 
initrd        /boot/initrd.img-2.6.36-1-generic-pae

title        Ubuntu natty (development branch), kernel 2.6.36-1-generic-pae (recovery mode)
uuid        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/vmlinuz-2.6.36-1-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro  single
initrd        /boot/initrd.img-2.6.36-1-generic-pae

title        Ubuntu natty (development branch), kernel 2.6.35-22-generic-pae
uuid        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic-pae

title        Ubuntu natty (development branch), kernel 2.6.35-22-generic-pae (recovery mode)
uuid        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic-pae

title        Ubuntu natty (development branch), kernel 2.6.32-24-generic-pae
uuid        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic-pae

title        Ubuntu natty (development branch), kernel 2.6.32-24-generic-pae (recovery mode)
uuid        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic-pae

title        Chainload into GRUB 2
root        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/grub/core.img

title        Ubuntu natty (development branch), memtest86+
uuid        5bca1844-fdc0-4a0d-8d26-1dd231a42d55
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b61ca5f21ca5ae35
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2a7214917214643b
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bdbbbedb-fce4-4f79-8b7e-ad8769991b36
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=bdbbbedb-fce4-4f79-8b7e-ad8769991b36 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bdbbbedb-fce4-4f79-8b7e-ad8769991b36
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=bdbbbedb-fce4-4f79-8b7e-ad8769991b36 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bdbbbedb-fce4-4f79-8b7e-ad8769991b36
    linux /boot/vmlinuz-2.6.32-17-generic root=UUID=bdbbbedb-fce4-4f79-8b7e-ad8769991b36 ro quiet splash
    initrd /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bdbbbedb-fce4-4f79-8b7e-ad8769991b36
    linux /boot/vmlinuz-2.6.32-17-generic root=UUID=bdbbbedb-fce4-4f79-8b7e-ad8769991b36 ro single
    initrd /boot/initrd.img-2.6.32-17-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=b3b4c609-ac22-43d5-a131-5623827f6cf4 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=bb5ab24b-17ad-44c5-9951-62a1a5338559 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=08e90eee-2b02-456c-8305-e218893ca439 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
   9.2GB: boot/grub/grub.cfg
   9.3GB: boot/grub/menu.lst
   1.4GB: boot/initrd.img-2.6.32-24-generic-pae
   2.5GB: boot/initrd.img-2.6.35-22-generic-pae
   1.5GB: boot/initrd.img-2.6.36-1-generic-pae
   2.4GB: boot/vmlinuz-2.6.32-24-generic-pae
   2.8GB: boot/vmlinuz-2.6.35-22-generic-pae
   2.9GB: boot/vmlinuz-2.6.36-1-generic-pae
   1.5GB: initrd.img
   2.5GB: initrd.img.old
   2.9GB: vmlinuz
   2.8GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0b3e4853-09d2-49de-93ec-4ae00b356b2f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0b3e4853-09d2-49de-93ec-4ae00b356b2f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0b3e4853-09d2-49de-93ec-4ae00b356b2f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0b3e4853-09d2-49de-93ec-4ae00b356b2f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0b3e4853-09d2-49de-93ec-4ae00b356b2f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu natty (development branch), kernel 2.6.36-1-generic-pae (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux /boot/vmlinuz-2.6.36-1-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro quiet splash
    initrd /boot/initrd.img-2.6.36-1-generic-pae
}
menuentry "Ubuntu natty (development branch), kernel 2.6.36-1-generic-pae (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux /boot/vmlinuz-2.6.36-1-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro single
    initrd /boot/initrd.img-2.6.36-1-generic-pae
}
menuentry "Ubuntu natty (development branch), kernel 2.6.35-22-generic-pae (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu natty (development branch), kernel 2.6.35-22-generic-pae (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro single
    initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu natty (development branch), kernel 2.6.32-24-generic-pae (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu natty (development branch), kernel 2.6.32-24-generic-pae (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5bca1844-fdc0-4a0d-8d26-1dd231a42d55 ro single
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Chainload into GRUB 2 (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
    linux /boot/grub/core.img 
}
menuentry "Ubuntu natty (development branch), memtest86+ (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5bca1844-fdc0-4a0d-8d26-1dd231a42d55
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=0b3e4853-09d2-49de-93ec-4ae00b356b2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=03a25ca9-4ac6-4a76-a7a0-bc7210aa7ff3 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 262.4GB: boot/grub/core.img
 284.5GB: boot/grub/grub.cfg
 222.7GB: boot/initrd.img-2.6.32-26-generic
 222.9GB: boot/initrd.img-2.6.35-23-generic
 262.4GB: boot/vmlinuz-2.6.32-26-generic
 262.5GB: boot/vmlinuz-2.6.35-23-generic
 222.9GB: initrd.img
 222.7GB: initrd.img.old
 262.5GB: vmlinuz
 262.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 02 01 00  |.<.MSWIN4.1.....|
00000010  02 00 02 c1 3e f8 20 00  3f 00 ff 00 7f ff 7d 03  |....>. .?.....}.|
00000020  00 00 00 00 80 00 29 f1  16 4d 3d 41 43 45 52 5f  |......)..M=ACER_|
00000030  53 45 52 56 49 43 46 41  54 31 36 20 20 20 33 c9  |SERVICFAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200

Unknown BootLoader  on sda4

00000000  0a 3c 55 38 43 46 42 3e  0a 3c 55 38 44 37 34 3e  |.<U8CFB>.<U8D74>|
00000010  0a 3c 55 38 44 42 41 3e  0a 3c 55 39 30 45 38 3e  |.<U8DBA>.<U90E8>|
00000020  0a 3c 55 39 31 44 43 3e  0a 3c 55 39 36 31 43 3e  |.<U91DC>.<U961C>|
00000030  0a 3c 55 39 36 34 34 3e  0a 3c 55 39 39 44 39 3e  |.<U9644>.<U99D9>|
00000040  0a 3c 55 39 43 45 37 3e  0a 3c 55 35 33 31 37 3e  |.<U9CE7>.<U5317>|
00000050  0a 3c 55 35 32 30 36 3e  0a 3c 55 35 34 32 39 3e  |.<U5206>.<U5429>|
00000060  0a 3c 55 35 36 37 34 3e  0a 3c 55 35 38 42 33 3e  |.<U5674>.<U58B3>|
00000070  0a 3c 55 35 39 35 34 3e  0a 3c 55 35 39 36 45 3e  |.<U5954>.<U596E>|
00000080  0a 3c 55 35 46 46 46 3e  0a 3c 55 36 31 41 34 3e  |.<U5FFF>.<U61A4>|
00000090  0a 3c 55 36 32 36 45 3e  0a 3c 55 36 36 31 30 3e  |.<U626E>.<U6610>|
000000a0  0a 3c 55 36 43 37 45 3e  0a 3c 55 37 31 31 41 3e  |.<U6C7E>.<U711A>|
000000b0  0a 3c 55 37 36 43 36 3e  0a 3c 55 37 43 38 39 3e  |.<U76C6>.<U7C89>|
000000c0  0a 3c 55 37 43 44 45 3e  0a 3c 55 37 44 31 42 3e  |.<U7CDE>.<U7D1B>|
000000d0  0a 3c 55 38 32 41 43 3e  0a 3c 55 38 43 43 31 3e  |.<U82AC>.<U8CC1>|
000000e0  0a 3c 55 39 36 46 30 3e  0a 3c 55 46 39 36 37 3e  |.<U96F0>.<UF967>|
000000f0  0a 3c 55 34 46 35 42 3e  0a 3c 55 35 46 31 37 3e  |.<U4F5B>.<U5F17>|
00000100  0a 3c 55 35 46 37 46 3e  0a 3c 55 36 32 43 32 3e  |.<U5F7F>.<U62C2>|
00000110  0a 3c 55 35 44 32 39 3e  0a 3c 55 36 37 30 42 3e  |.<U5D29>.<U670B>|
00000120  0a 3c 55 36 38 44 41 3e  0a 3c 55 37 38 37 43 3e  |.<U68DA>.<U787C>|
00000130  0a 3c 55 37 45 34 33 3e  0a 3c 55 39 44 36 43 3e  |.<U7E43>.<U9D6C>|
00000140  0a 3c 55 34 45 31 35 3e  0a 3c 55 35 30 39 39 3e  |.<U4E15>.<U5099>|
00000150  0a 3c 55 35 33 31 35 3e  0a 3c 55 35 33 32 41 3e  |.<U5315>.<U532A>|
00000160  0a 3c 55 35 33 35 31 3e  0a 3c 55 35 39 38 33 3e  |.<U5351>.<U5983>|
00000170  0a 3c 55 35 41 36 32 3e  0a 3c 55 35 45 38 37 3e  |.<U5A62>.<U5E87>|
00000180  0a 3c 55 36 30 42 32 3e  0a 3c 55 36 31 38 41 3e  |.<U60B2>.<U618A>|
00000190  0a 3c 55 36 32 34 39 3e  0a 3c 55 36 32 37 39 3e  |.<U6249>.<U6279>|
000001a0  0a 3c 55 36 35 39 30 3e  0a 3c 55 36 37 38 37 3e  |.<U6590>.<U6787>|
000001b0  0a 3c 55 36 39 41 37 3e  0a 3c 55 36 42 44 00 fe  |.<U69A7>.<U6BD..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f8 94 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```It may be in a peculiar state after my abortive attempts to resolve this.

I shall be grateful for advice which enables me to boot into the external disc os(s).

---

### Post by cpmman on 2010-12-26
Anyone?

---

### Post by efflandt on 2010-12-26
I still don't know why, but my new desktop has trouble with grub2 trying to boot a partition farther out on a 500 GB USB hard drive (which boots fine on different laptops from 2006), even though the desktop boots Ubuntu fine from the far end of its 1 TB internal drive.  Although, the error I got in the past from grub rescue was: unknown filesystem (for ext3 or ext4). The desktop works fine booting Ubuntu on a partition closer to the beginning an identical 500 GB USB hd (or anywhere on 160 GB USB hd), but I don't know where the cutoff point is that works. Note:

=================== sdb6: Location of files loaded by Grub: ===================


 262.4GB: boot/grub/core.img
 284.5GB: boot/grub/grub.cfg
 222.7GB: boot/initrd.img-2.6.32-26-generic
 222.9GB: boot/initrd.img-2.6.35-23-generic
 262.4GB: boot/vmlinuz-2.6.32-26-generic
 262.5GB: boot/vmlinuz-2.6.35-23-generic
 222.9GB: initrd.img
 222.7GB: initrd.img.old
 262.5GB: vmlinuz
 262.4GB: vmlinuz.old

Maybe it would help to have a separate /boot partition at the beginning of the drive.  Was Maverick able to boot from USB before installing Natty?

But you also have older kernels than current kernels in Natty, so not sure if that is an issue.  Although, I use 64-bit, so my current **uname -a** is: Linux natty-ssd **2.6.37-11-generic #25**-Ubuntu SMP Tue Dec 21 23:42:56 UTC 2010 x86_64 GNU/Linux

I don't have Natty on USB hard drive, but I did have Natty on 8 GB USB stick, and now have Kubuntu Natty regular install on that stick.  I currently boot Natty from internal SSD with grub2 on that /dev/sdb as boot drive (Win7 & Maverick are on 1 TB hda).

---

### Post by kansasnoob on 2010-12-26
From what you've posted so far I assume you can boot the 10.10 on sda2, eh? If so the very first thing I'd do is boot into it and run:

```
sudo update-grub
```

Wait for it to say done and see what happens. If the Natty on sdb1 and 10.10 on sdb6 still fail to boot read on.

I see your drives are as follows:

Disk /dev/sda: 30.0 GB
Disk /dev/sdb: 320.1 GB

And the MBR's are assigned as follows:

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

So the next thing I'd try is changing the hard drive boot order in BIOS and see if either sdb1 or sdb6 will boot.

If things are still a no-go on both sdb1 and sdb6 I'd like to see the output of:

```
sudo parted -l
```

I should also mention that you appear to have mixed grub2 and legacy grub files on Natty, but I'd not worry about that until we can get the 10.10 on sdb6 booting ;)

---

### Post by cpmman on 2010-12-27
> **kansasnoob said:**
> From what you've posted so far I assume you can boot the 10.10 on sda2, eh? If so the very first thing I'd do is boot into it and run:

```
sudo update-grub
```Wait for it to say done and see what happens. If the Natty on sdb1 and 10.10 on sdb6 still fail to boot read on.

Yes 10.10 on sda boots as did the sdb installs prior to the last two updates to 10.10 on sda. No change from sudo update-grub.

> **kansasnoob said:**
>  I see your drives are as follows:

Disk /dev/sda: 30.0 GB
Disk /dev/sdb: 320.1 GB

And the MBR's are assigned as follows:



So the next thing I'd try is changing the hard drive boot order in BIOS and see if either sdb1 or sdb6 will boot.

The Acer is eight years old and only offers Hard Disk, CD/DVD, Floppy Disk and Networks boot options - it does not have a USB Disk option.

> **kansasnoob said:**
>  If things are still a no-go on both sdb1 and sdb6 I'd like to see the output of:

```
sudo parted -l
```I should also mention that you appear to have mixed grub2 and legacy grub files on Natty, but I'd not worry about that until we can get the 10.10 on sdb6 booting ;)
```

cpm@TM-292:~$ sudo parted -l
Model: ATA IC25N030ATMR04-0 (scsi)
Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  19.5GB  19.5GB  primary   fat32        boot, lba
 2      19.5GB  25.0GB  5487MB  primary   ext4
 4      25.0GB  30.0GB  4999MB  extended
 5      25.0GB  30.0GB  4999MB  logical   ext4
 3      30.0GB  30.0GB  8225kB  primary   fat16        hidden, lba


Model: WDC WD32 00BEVT-22ZCT0 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.7GB  10.7GB  primary   ext4            boot
 2      10.7GB  320GB   309GB   extended
 8      10.7GB  21.0GB  10.2GB  logical   ext4
 5      100GB   221GB   121GB   logical   ext4
 6      221GB   316GB   94.6GB  logical   ext4
 7      316GB   320GB   4056MB  logical   linux-swap(v1)


cpm@TM-292:~$ 
```Since my first post I installed another 10.10 in sdb8 (10Gb of 90 Gb that I use for additional installs or attempted repairs) in the hope it might sort it for me but no change.

---

### Post by cpmman on 2011-01-02
bump

---

### Post by robsoles on 2011-01-07
I am no expert regarding grub2, Linux or anything in particular :)

Perhaps a tenable temporary workaround could be to roll back the updates to grub2 and post a bug report ( [https://help.ubuntu.com/community/SynapticHowto#How%20to%20force%20the%20installation%20of%20a%20package%20version](https://help.ubuntu.com/community/SynapticHowto#How%20to%20force%20the%20installation%20of%20a%20package%20version) [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) - no doubt you knew exactly where these are :))


I haven't researched, I'm guessing that you can access it in nautilus because a module for the kernel that takes care of USB storage in older PCs, where the BIOS doesn't take care of USB storage access, is being loaded as it ought and perhaps they've dropped similar functionality (ie., a similar module(/part of) grub2 has been dropped) rendering the loader blind to your USB storage till a kernel is up and running with it's module - if I'm right then it will never boot off a USB device using that(/these) version(s) of grub2 in a PC that doesn't 'connect' USB storage in BIOS(/low level).

Being accessible once a kernel is actually booted, 'update-grub' and similar utilities can 'see' the USB storage and so can happily have it/them listed in the boot menu but if grub2 has been treated/borked as I've guessed then it cannot 'see' them.


I decided to at least check the changelog for grub2 under 10.10 before posting ;) it is attached, I found the odd entry that made me wonder if that was what borked it for you, but I didn't come across an entry that made me think that my guess is right for sure.


(I have subscribed this thread)

---

### Post by cpmman on 2011-01-08
@robsoles - reply as per pm.

Only current version of grub2 available - cannot -force earlier version - same in Lucid.

Grub2 amends replaces device.map with probe which may miss usb disks when bios hasn't the option to boot from usb.

---

### Post by robsoles on 2011-01-08
Just in case you missed this step: The instructions regarding rolling back packages that I linked to previously mention "reloading" the updates so Synaptic is 'aware' of updates so as to roll them back.

---

### Post by cpmman on 2011-01-08
Yes I did reload but force version greyed out for Maverick and for Lucid so I guess the older versions are no longer in the repositories.

edit: server for United Kingdom

---

### Post by robsoles on 2011-01-08
> **cpmman said:**
> Yes I did reload but force version greyed out for Maverick and for Lucid so I guess the older versions are no longer in the repositories.

edit: server for United Kingdom

Is it the same result if you switch to the 'main' server for a check?

---

### Post by robsoles on 2011-01-08
I wonder if you could use the LiveCD to boot into your USB bound OSes. The LiveCD's boot process can be interrupted for parameters and grub-rescue stuff and it should have a nice (at least slightly) older grub2 loader :)

---

### Post by cpmman on 2011-01-08
Shall try those when I come back this afternoon - I am going to the shops in twenty minutes (10:15 local) for the first time since before Christmas with a neighbour.

---

### Post by cpmman on 2011-01-09
Several reinstalls of 10.04 and 10.10 to sda2 - with combinations of with/out internet update, locking grub versions, changing to main and AU repositories, copy sdb device.map to sda and reinstalling grub2 followed by grub-update, interrupting live cd with parameters.  No success.

As observed the grub process does not seem to be able to recognise the usb disk and as the bios does not it cannot boot from there even though Nautilus automounts sda1,sdb1,sdb5 and sdb6 and the symlinks to each of those works perfectly so Nautilus accepts it as a disk and grub can have it in the menu but is blind to it when booting.

Like a politician I am tired and emotional again so shall investigate the separate /boot partition methods tomorrow.

Thanks for all your pm'd help and advice robsoles.

---

### Post by robsoles on 2011-01-09
Sorry to hear frustration remains by your side.

Did you try the methodology shown at [https://help.ubuntu.com/community/GrubHowto#Manually boot into a Linux OS](https://help.ubuntu.com/community/GrubHowto#Manually boot into a Linux OS)?

If the older grub-pc/grub2 off the 10.04 LTS can 'see' your USB drive (which I think it ought be able) then you want something like root=(hd1,0) to indicate sdb1.

Any good? (sorry if it's something you've pressed through and it still didn't work!)

---

### Post by cpmman on 2011-01-10
Another 10.04 reinstall to sda2 without internet and a lock version of the earlier grub2 - not before and not after an internet update will it get past ```
set root=(hdX,Y)
``` with X = 1 and Y = 1 or 0, the following```
 linux /vmlinuz root=/dev/sdXY ro
``` gives```
 unable to get C/H/S values for ...
```So I have reinstalled 10.10 with updates and dropping to grub on livecd still gives me the C/H/S error.

I am content to remain with the sda2 10.10 boot with auto mount sda1,sdb1,sdb5 and sdb6 with functional symlinks utilising the usb as an external storage until my new laptop arrives when I can resume natty testing.

Thanks for all your help robsoles and as pm'd I have other priorities at the moment so shall leave this thread open in case either I find time to try the floppy boot method (I have a usb floppy drive but fear that may also be a "not recognised until after boot" device).  There is also a "floppy to cd" which may be worth a look

I am fairly sure that something in the grub2 update changed the sdb so there is a chance that the floppy may be seen at boot.  It is also possible that a later update to grub2 may resolve the problem (there are 307 items on launchpad relating to grub2 and "no such device" problems).

Mañana sounds a bit too rushed for me!

---

### Post by cpmman on 2011-01-14
Posting in the games forum I spotted yetiman64's sig with [_***Illustrated dual boot site***_]("http://members.iinet.net/%7Eherman546/index.html") which led to rescatux and I am now posting from the natty install on my sdb1!

Thank you robsoles for your advice to "chill out" and play games for a while - it has led to being able to boot again from my external usb disk.  I shall now go and play some more games and let my uber/sub consciousness work out how to make this permanent but for now this is an acceptable workaround.

---

### Post by cpmman on 2011-01-16
Semi-permanent solution - at least until the grub2 can find usb disks that the bios cannot is to use [_***Plop***_]("http://www.plop.at/") with a plpbt.bin file in /boot and a 40_custom menu entry in /etc/grub.d - which will survive any kernel update-grub changes.

---

