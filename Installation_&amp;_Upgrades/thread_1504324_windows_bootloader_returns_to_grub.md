---
title: "windows bootloader returns to grub"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by wrightsimmo80 on 2010-06-07
When I try to boot into windows through grub  it just returns to the grub menu.
also system recovery options from bios just end up in grub screen too. 

here is boot script.

From reading forums I think I need to get grub out of windows partition but I don't know how

Any ideas greatly appreciated.

cheers 

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 550147858 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #9 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 311. But according to the info from fdisk, 
                       sda6 starts at sector 365125632.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   233,617,229   233,617,167   7 HPFS/NTFS
/dev/sda2         233,617,230   757,994,894   524,377,665   5 Extended
/dev/sda5         233,617,293   365,125,319   131,508,027  83 Linux
/dev/sda6         365,125,632   549,084,114   183,958,483   7 HPFS/NTFS
/dev/sda7         729,865,143   740,050,289    10,185,147  82 Linux swap / Solaris
/dev/sda8         740,050,353   757,994,894    17,944,542  82 Linux swap / Solaris
/dev/sda9         549,085,698   722,410,919   173,325,222  83 Linux
/dev/sda10        722,410,983   729,865,079     7,454,097  82 Linux swap / Solaris
/dev/sda3         758,005,760   781,416,447    23,410,688   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       a19162fa-d817-417c-b043-5c25bebc8f24   swap                                     
/dev/sda1        163AD1B13AD18DDD                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1C306F0C306EEC68                       ntfs       RECOVERY                      
/dev/sda5        141d6948-3fa3-4dad-996d-c950fe939903   ext4                                     
/dev/sda6        583229C93229AD46                       ntfs                                     
/dev/sda7        0832728d-768f-4f61-8e33-decc46e3a794   swap                                     
/dev/sda8        5bf1db98-5975-4433-a03d-3cae5c0733ae   swap                                     
/dev/sda9        544fb618-8074-4c8c-9ee0-c11fc511a3c6   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

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
default        4

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
# kopt=root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=141d6948-3fa3-4dad-996d-c950fe939903

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 163ad1b13ad18ddd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1c306f0c306eec68
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=141d6948-3fa3-4dad-996d-c950fe939903 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5bf1db98-5975-4433-a03d-3cae5c0733ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 119.8GB: boot/grub/core.img
 126.6GB: boot/grub/grub.cfg
 120.4GB: boot/grub/menu.lst
 120.4GB: boot/initrd.img-2.6.31-14-generic
 124.0GB: boot/initrd.img-2.6.32-22-generic
 120.1GB: boot/vmlinuz-2.6.31-14-generic
 121.7GB: boot/vmlinuz-2.6.32-22-generic
 124.0GB: initrd.img
 120.4GB: initrd.img.old
 121.7GB: vmlinuz
 120.1GB: vmlinuz.old

=========================== sda9/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,9)
search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 163ad1b13ad18ddd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 1c306f0c306eec68
    chainloader +1
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.04 LTS, memtest86+ (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=a19162fa-d817-417c-b043-5c25bebc8f24 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 281.6GB: boot/grub/core.img
 284.3GB: boot/grub/grub.cfg
 281.6GB: boot/initrd.img-2.6.31-14-generic
 281.6GB: boot/vmlinuz-2.6.31-14-generic
 281.6GB: initrd.img
 281.6GB: vmlinuz
```

---

### Post by bcbc on 2010-06-07
See this link [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Try testdisk first. It works best.

---

### Post by wrightsimmo80 on 2010-06-07
ok going backwards here

I just followed a fix from 

'http://soundforge.net/apps/mediawik...ms:boot sector' to 'BackupBS' 
then 
sudo update-grub

the symptoms and cause seemed to fit my situation but now  I don't even get into grub -I just get a black screen with flashing cursor.
I have a vista lite  disc and live ubuntu  , or super grub disk to get in to edit if need be.

I've done another boot info script after the 'fix'

I just seem to be going round in circles here
hope it helps 
```
[HTML]Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary:  ==============================

 => Windows is installed in the MBR of /dev/sda

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda2:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg  /etc/fstab 
                       /boot/grub/core.img

sda6:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6  starts 
                       at sector 311. But according to the info from  fdisk, 
                       sda6 starts at sector 365125632.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sda10:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   233,617,229   233,617,167   7 HPFS/NTFS
/dev/sda2         233,617,230   757,994,894   524,377,665   5 Extended
/dev/sda5         233,617,293   365,125,319   131,508,027  83 Linux
/dev/sda6         365,125,632   549,084,114   183,958,483   7 HPFS/NTFS
/dev/sda7         729,865,143   740,050,289    10,185,147  82 Linux swap  / Solaris
/dev/sda8         740,050,353   757,994,894    17,944,542  82 Linux swap  / Solaris
/dev/sda9         549,085,698   722,410,919   173,325,222  83 Linux
/dev/sda10        722,410,983   729,865,079     7,454,097  82 Linux swap  / Solaris
/dev/sda3         758,005,760   781,416,447    23,410,688   7 HPFS/NTFS


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE       LABEL                          

/dev/sda10       a19162fa-d817-417c-b043-5c25bebc8f24   swap                                      
/dev/sda1        163AD1B13AD18DDD                       ntfs                                      
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1C306F0C306EEC68                       ntfs        RECOVERY                      
/dev/sda5        141d6948-3fa3-4dad-996d-c950fe939903   ext4                                      
/dev/sda6        583229C93229AD46                       ntfs                                      
/dev/sda7        0832728d-768f-4f61-8e33-decc46e3a794   swap                                      
/dev/sda8        5bf1db98-5975-4433-a03d-3cae5c0733ae   swap                                      
/dev/sda9        544fb618-8074-4c8c-9ee0-c11fc511a3c6   ext4                                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4        (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst:  ===========================

# menu.lst - See: grub(8), info grub,  update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from  0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default  entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the  default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive  editing
# control (menu entry editor and command-line)  and entries protected by  the
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
# kopt=root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=141d6948-3fa3-4dad-996d-c950fe939903

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with  the
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
## update-grub will ignore non-xen kernels when running in domU and vice  versa
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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.32-22-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.32-22-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.31-14-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.31-14-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 163ad1b13ad18ddd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1c306f0c306eec68
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set  544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on  /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set  544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=141d6948-3fa3-4dad-996d-c950fe939903 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5bf1db98-5975-4433-a03d-3cae5c0733ae none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0

=================== sda5: Location of files loaded by Grub:  ===================


 119.8GB: boot/grub/core.img
 126.6GB: boot/grub/grub.cfg
 120.6GB: boot/grub/menu.lst
 120.4GB: boot/initrd.img-2.6.31-14-generic
 124.0GB: boot/initrd.img-2.6.32-22-generic
 120.1GB: boot/vmlinuz-2.6.31-14-generic
 121.7GB: boot/vmlinuz-2.6.32-22-generic
 124.0GB: initrd.img
 120.4GB: initrd.img.old
 121.7GB: vmlinuz
 120.1GB: vmlinuz.old

=========================== sda9/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
insmod ext2
set root=(hd0,9)
search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set  544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set  544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 163ad1b13ad18ddd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 1c306f0c306eec68
    chainloader +1
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.32-22-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)  (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.32-22-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)  (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.04 LTS, memtest86+ (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=a19162fa-d817-417c-b043-5c25bebc8f24 none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0

=================== sda9: Location of files loaded by Grub:  ===================


 281.6GB: boot/grub/core.img
 284.3GB: boot/grub/grub.cfg
 281.6GB: boot/initrd.img-2.6.31-14-generic
 281.6GB: boot/vmlinuz-2.6.31-14-generic
 281.6GB: initrd.img
 281.6GB: vmlinuz[/HTML]
```

---

### Post by bcbc on 2010-06-07
Well, you have the windows bootloader in the MBR. So I'm not sure how you got a grub prompt in the first place (I just noticed it in your first bootinfoscript results). But that should be booting the partition marked active, sda1, which contains windows and now doesn't contain grub2 (so that's a positive), but obviously something else is wrong with your windows.

You can either focus on getting windows fixed, i.e. leave the windows bootloader in place, or you can get grub2 back in the MBR and boot your 10.04 ubuntu on /dev/sda5. 

For the first, try this link: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

For the second, boot from live cd, mount your 10.04 partition, resintall grub2 to mbr:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

PS for readability, please edit your previous posts, click on Go Advanced, select the entire bootinfoscript results and click on the # button above. Or insert the results inbetween [[SIZE="1"] [/SIZE]CODE][/CODE] tags (same thing). Thanks

---

### Post by wrightsimmo80 on 2010-06-08
1st step - Will try the bootrec.exe again though I think I have already tried this option. when I actually had grub loading. When I selected windows it just sat in black screen flashing cursor....will post result soon 

2nd step -

 When I entered
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
I got:

grub-probe: error: Cannot stat 'dev/sda
Invalid device 'dev/sda'


Thanks for the reply and edit tip was wondering how to do that :).

---

### Post by oldfred on 2010-06-08
Do you have a BIOS that locks the MBR? Some have a setting for allowing MBR updates.

---

### Post by bcbc on 2010-06-08
You have to use */dev/sda* not *dev/sda*

Regarding windows. I do not know why, but some people get the bootsector thing fixed first time without any hassle. Unfortunately the ones that have issues, often don't get them resolved. I don't know why, whether it's a failed repair job or some other variable involved. 

All I can recommend is you try the advice on the MS site. Some say you have to run repair 3 times. Some have to rebuild their bcd menu. Some do the "bootrec.exe /nt60 all /force" thing. It's hard to know from afar what's really going on so I can't recommend anything other than going to the microsoft site and following their advice.

---

### Post by wrightsimmo80 on 2010-06-08
[QUOTE=bcbc;9428120]You have to use */dev/sda* not *dev/sda*

yes thanks that worked 

So I can boot with out using a disc again - however  - now 'Grub loading' flicks up for a second then proceeds to boot ubuntu from sda5 with out going to grub menu.

---

### Post by wrightsimmo80 on 2010-06-08
> **oldfred said:**
> Do you have a BIOS that locks the MBR? Some have a setting for allowing MBR updates.


My bios version is F.14  on HP pavillion Dv5 but looking through the bios options I don't see anything regarding MBR updates. (InsydeH20 Setup utility) rev .3.5   if that helps any???

---

### Post by bcbc on 2010-06-08
> **wrightsimmo80 said:**
> 
yes thanks that worked 

So I can boot with out using a disc again - however  - now 'Grub loading' flicks up for a second then proceeds to boot ubuntu from sda5 with out going to grub menu.

Normally grub2 will find windows automatically. To regenerate the menu run```
sudo update-grub
```
Or hold down the shift key when booting to see the menu.

---

### Post by wrightsimmo80 on 2010-06-08
> **bcbc said:**
> Normally grub2 will find windows automatically. To regenerate the menu run```
sudo update-grub
```Or hold down the shift key when booting to see the menu.

Grub update runs ok but still getting an error stopping grub from booting up after half a second or so.
just loads into my partition ubuntu 10.04

Still, main issue is with the windows not booting. will have to follow up with a vista forum as multiple attempts with bootrec, fixboot,fixmbr ...etc have not cleared that problem..

any suggestions as to best site /forum for vista specific non booting issues,

thanks for your replies.

---

### Post by bcbc on 2010-06-08
> **wrightsimmo80 said:**
> Grub update runs ok but still getting an error stopping grub from booting up after half a second or so.
just loads into my partition ubuntu 10.04

Still, main issue is with the windows not booting. will have to follow up with a vista forum as multiple attempts with bootrec, fixboot,fixmbr ...etc have not cleared that problem..

any suggestions as to best site /forum for vista specific non booting issues,

thanks for your replies.

[This site]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") has worked for some.

Edit: you've probably tried the first steps already, but there are more advanced techniques at the bottom of the page.

---

### Post by wrightsimmo80 on 2010-06-09
> **bcbc said:**
> [This site]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") has worked for some.

Edit: you've probably tried the first steps already, but there are more advanced techniques at the bottom of the page.


Yes I had tried the first couple which had no effect, then dug a bunker ready for 
[B]'Step Four: Nuclear Holocaust'  all steps seemed to complete ok but
[/B]

...this didn't crack it either... 
My main aim at the moment is to get into windows to do full recovery via partition, however after my first couple of vista installs failed to boot, I have formatted the 1st partition and installed a clean vista onto there. This did boot ok but now as it was not the original vista disc for the hp laptop there is no hp recovery console (f11 recovery option did not activate) 
I went into disk maintenance to set the recovery partition to active and when I did the restart ....... back to blinking screen .

Now doing partition 1 format and install again to try ... something else ???

---

### Post by darkod on 2010-06-09
If you don't mind me asking, why do you have 3 swap partition with a total of 17GB?

Why do you care about accessing the recovery partition? In fact, if you have another way to install vista, that's preferred. The recovery partition would usually wipe your hdd and create factory layout. Why would you want to wipe your data simply because windows broke down?

---

### Post by wrightsimmo80 on 2010-06-09
> **darkod said:**
> If you don't mind me asking, why do you have 3 swap partition with a total of 17GB?

Why do you care about accessing the recovery partition? In fact, if you have another way to install vista, that's preferred. The recovery partition would usually wipe your hdd and create factory layout. Why would you want to wipe your data simply because windows broke down?

I wanted to get to the recovery partition to burn the original back up (that I should have done before I began dabbling...) I actually have nothing on the HDD so I am not worried about loosing any data just wanted to start from scratch, plus the vista that I have just installed is a lite version from an iso I downloaded (no office /recovery software). I would hope that the recovered vista os would be more suited (drivers, software etc).
As for the 3 swap partitions, I can only guess as I'm pretty new to linux but I did quite a few installs from ubuntu live cd while trying to fix the grub problem listed earlier in post. 
That was another reason for wanting to do a full recovery, so I can start with a clean vista and the install just 1 ubuntu from live cd.

---

### Post by darkod on 2010-06-09
I am not sure starting the recovery partition offers possibility to create DVDs. I think you would have the option only from vista. But as you said, you can do the restore, then make the DVDs.

You could try to kick off the recovery partition on /dev/sda3 like this:

If you don't have grub2 on the MBR right now, reinstall it from live mode with:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If you have grub2 loading when you start, skip that.

Once grub2 loads, press 'c' for command line (I think it works for grub2 too). When the grub command prompt loads, try to start /dev/sda3 with:

insmod ntfs
set root=(hd0,3)
makeactive
chainloader /bootmgr

See if that fires it up. Unless I got the commands wrong, never tried this before.

---

### Post by wrightsimmo80 on 2010-06-09
> **darkod said:**
> I am not sure starting the recovery partition offers possibility to create DVDs. I think you would have the option only from vista. But as you said, you can do the restore, then make the DVDs.

You could try to kick off the recovery partition on /dev/sda3 like this:

If you don't have grub2 on the MBR right now, reinstall it from live mode with:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If you have grub2 loading when you start, skip that.

Once grub2 loads, press 'c' for command line (I think it works for grub2 too). When the grub command prompt loads, try to start /dev/sda3 with:

insmod ntfs
set root=(hd0,3)
makeactive
chainloader /bootmgr

See if that fires it up. Unless I got the commands wrong, never tried this before.
This looked like it was going to work, but it came back to older problem when 'grub loading' flashes up for half a second then displays 'error file not found', then runs a quick bunch of script before booting straight into ubuntu 10,04.

can I issue the above command for (hd0,3) from ubuntu terminal or does it have to be from grub?

sim

---

### Post by darkod on 2010-06-09
> **wrightsimmo80 said:**
> This looked like it was going to work, but it came back to older problem when 'grub loading' flashes up for half a second then displays 'error file not found', then runs a quick bunch of script before booting straight into ubuntu 10,04.

can I issue the above command for (hd0,3) from ubuntu terminal or does it have to be from grub?

sim

Once ubuntu loads, you can't start windows or the recovery partition.

I'm out of ideas. :(

I suggest you drop the silly recovery partition, it's worthless for recovery anyway because as I said, usually they wipe the whole hdd losing all data in the process.
Just make a new vista install, or keep the current one if it's OK, reinstall ubuntu or just the grub2 bootloader if needed, and that's it.

You can always use free tools for backup and recovery even of windows partitions. This is just one example:
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

---

### Post by wrightsimmo80 on 2010-06-09
> **darkod said:**
> Once ubuntu loads, you can't start windows or the recovery partition.

I'm out of ideas. :(

I suggest you drop the silly recovery partition, it's worthless for recovery anyway because as I said, usually they wipe the whole hdd losing all data in the process.
Just make a new vista install, or keep the current one if it's OK, reinstall ubuntu or just the grub2 bootloader if needed, and that's it.

You can always use free tools for backup and recovery even of windows partitions. This is just one example:
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

hmm, sorry maybe I wasn't quite clear in my last post,  I didn't get to actually try your command in grub as it isn't booting properly. It just comes flashes up grub loading then comes up with an error.
How can I get to normal grub menu?

---

### Post by darkod on 2010-06-09
> **wrightsimmo80 said:**
> hmm, sorry maybe I wasn't quite clear in my last post,  I didn't get to actually try your command in grub as it isn't booting properly. It just comes flashes up grub loading then comes up with an error.
How can I get to normal grub menu?

Depending at which point it fails (whether before or after starting to load ubuntu), you can start hitting Shift to get to see the menu. In case it doesn't show menu, if it can't detect another OS.

---

### Post by bcbc on 2010-06-09
For grub2 hold down the SHIFT key during the boot.
For grub-legacy hold down the ESC key. 

The only reason I mention grub legacy is I noticed a menu.lst file and since you're having strange problems.

Try them both (don't tap, hold them down). EDIT: I mean try each one separately, don't press them at the same time.

---

### Post by wrightsimmo80 on 2010-06-09
During boot  I have tried pressing and holding down shift but this does not change error, for grub legacy idea (hold esc) this during first stage of boot (HP screen) gets me into menu (select system info, start up test, bios settings) but if I begin pressing esc straight away after hp screen disappears  I just get a long system beep.

the actual error message I get message I am getting  is after HP opening screen
grub loading comes up ( for half a second)

then this comes up 

error  file not found
linux-bzimage, setup 0x3400, size 0x3d4860
--this message comes up for a fraction of a second so I had to restart about 15 times to copy this error message down. so may not be entirely accurate but  Ihope someone can make sense of it?
Cheers

---

### Post by wrightsimmo80 on 2010-06-09
> **darkod said:**
> I am not sure starting the recovery partition offers possibility to create DVDs. I think you would have the option only from vista. But as you said, you can do the restore, then make the DVDs.

You could try to kick off the recovery partition on /dev/sda3 like this:

If you don't have grub2 on the MBR right now, reinstall it from live mode with:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If you have grub2 loading when you start, skip that.

Once grub2 loads, press 'c' for command line (I think it works for grub2 too). When the grub command prompt loads, try to start /dev/sda3 with:

insmod ntfs
set root=(hd0,3)
makeactive
chainloader /bootmgr

See if that fires it up. Unless I got the commands wrong, never tried this before.

Since I can't get into my own grub I ran super grub disc and tried to enter the above stepts (insmod...etc)
1st two lines seemed ok but the 'makeactive' command said:
error: unkown command 'makeactive'

also from super grub disc when I select detect any OS and selected 
'windows vista bootmgr' the first one just came up with a black screen and restart with flashing cursor under it. when I select the second entry of 
'windows vista bootmgr' this loads in to the vista lite that I installed recently.

---

### Post by bcbc on 2010-06-09
> **wrightsimmo80 said:**
> During boot  I have tried pressing and holding down shift but this does not change error, for grub legacy idea (hold esc) this during first stage of boot (HP screen) gets me into menu (select system info, start up test, bios settings) but if I begin pressing esc straight away after hp screen disappears  I just get a long system beep.

the actual error message I get message I am getting  is after HP opening screen
grub loading comes up ( for half a second)

then this comes up 

error  file not found
linux-bzimage, setup 0x3400, size 0x3d4860
--this message comes up for a fraction of a second so I had to restart about 15 times to copy this error message down. so may not be entirely accurate but  Ihope someone can make sense of it?
Cheers

This error comes up in the [grub2 community docs]("https://help.ubuntu.com/community/Grub2#Using CLI to Boot") (scroll down a bit), but it's in the context of manually booting from grub cli - which you can't even get to. It says > If a "file not found" or similar error message occurs, either the device/partition/file does not exist or GRUB 2 is not looking at the correct drive, partition and/or directory.
This would indicate some error with the grub-install.

I am at a loss to explain this - I would try reinstalling grub and use the --recheck parameter, but my intuition says there is an underlying issue we haven't identified.

If you still have a mix of grub legacy (if there's a menu.lst in /boot/grub) I'd recommend trying to completely purge and reinstall grub:
```
sudo apt-get purge grub grub-common grub-pc
sudo mv /boot/grub /boot/grubbackup
sudo apt-get install grub-pc grub-common
```

I guess I don't need to say: make sure you install grub only to /dev/sda (no partitions)

---

### Post by darkod on 2010-06-09
How about contacting the manufacturer and asking for vista install dvd, or your computer restore dvd?

---

### Post by wrightsimmo80 on 2010-06-09
> **bcbc said:**
> This error comes up in the [grub2 community docs]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot") (scroll down a bit), but it's in the context of manually booting from grub cli - which you can't even get to. It says 
This would indicate some error with the grub-install.

I am at a loss to explain this - I would try reinstalling grub and use the --recheck parameter, but my intuition says there is an underlying issue we haven't identified.

If you still have a mix of grub legacy (if there's a menu.lst in /boot/grub) I'd recommend trying to completely purge and reinstall grub:
```
sudo apt-get purge grub grub-common grub-pc
sudo mv /boot/grub /boot/grubbackup
sudo apt-get install grub-pc grub-common
```I guess I don't need to say: make sure you install grub only to /dev/sda (no partitions)

Ok there was grub installed n partitions 1 3 and 5 son I unchecked them and installed just into /dev/sda 
This time on reboot it didn't even give the flash of grub loading just went straight into loading ubuntu???
thanks again for your help with this one(-:

---

### Post by bcbc on 2010-06-09
> **wrightsimmo80 said:**
> Ok there was grub installed n partitions 1 3 and 5 son I unchecked them and installed just into /dev/sda 
This time on reboot it didn't even give the flash of grub loading just went straight into loading ubuntu???
thanks again for your help with this one(-:

Is it possible you have grub back in your windows bootsector? 
Can you run the output of the bootinfoscript again?
Does the SHIFT key now at least stop the booting and get you to the grub menu?

---

### Post by wrightsimmo80 on 2010-06-09
here is new script info

             ```
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 311. But according to the info from fdisk, 
                       sda6 starts at sector 365125632.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   233,617,229   233,617,167   7 HPFS/NTFS
/dev/sda2         233,617,230   757,994,894   524,377,665   5 Extended
/dev/sda5         233,617,293   365,125,319   131,508,027  83 Linux
/dev/sda6         365,125,632   549,084,114   183,958,483   7 HPFS/NTFS
/dev/sda7         549,085,698   722,410,919   173,325,222  83 Linux
/dev/sda8         722,410,983   729,865,079     7,454,097  82 Linux swap / Solaris
/dev/sda9         729,865,143   740,050,289    10,185,147  82 Linux swap / Solaris
/dev/sda10        740,050,353   757,994,894    17,944,542  82 Linux swap / Solaris
/dev/sda3         758,005,760   781,416,447    23,410,688   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   596C-4840                              vfat       CANON_DC                      
/dev/sda10       5bf1db98-5975-4433-a03d-3cae5c0733ae   swap                                     
/dev/sda1        BC1058BC10587F78                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1C306F0C306EEC68                       ntfs       RECOVERY                      
/dev/sda5        141d6948-3fa3-4dad-996d-c950fe939903   ext4                                     
/dev/sda6        583229C93229AD46                       ntfs                                     
/dev/sda7        544fb618-8074-4c8c-9ee0-c11fc511a3c6   ext4                                     
/dev/sda8        a19162fa-d817-417c-b043-5c25bebc8f24   swap                                     
/dev/sda9        0832728d-768f-4f61-8e33-decc46e3a794   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/mmcblk0p1   /media/CANON_DC          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bc1058bc10587f78
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1c306f0c306eec68
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=141d6948-3fa3-4dad-996d-c950fe939903 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5bf1db98-5975-4433-a03d-3cae5c0733ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 119.7GB: boot/grub/core.img
 151.9GB: boot/grub/grub.cfg
 120.4GB: boot/initrd.img-2.6.31-14-generic
 124.0GB: boot/initrd.img-2.6.32-22-generic
 120.1GB: boot/vmlinuz-2.6.31-14-generic
 121.7GB: boot/vmlinuz-2.6.32-22-generic
 124.0GB: initrd.img
 120.4GB: initrd.img.old
 121.7GB: vmlinuz
 120.1GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,9)
search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 544fb618-8074-4c8c-9ee0-c11fc511a3c6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 163ad1b13ad18ddd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 1c306f0c306eec68
    chainloader +1
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.04 LTS, memtest86+ (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=544fb618-8074-4c8c-9ee0-c11fc511a3c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=a19162fa-d817-417c-b043-5c25bebc8f24 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 281.6GB: boot/grub/core.img
 284.3GB: boot/grub/grub.cfg
 281.6GB: boot/initrd.img-2.6.31-14-generic
 281.6GB: boot/vmlinuz-2.6.31-14-generic
 281.6GB: initrd.img
 281.6GB: vmlinuz
```

---

### Post by darkod on 2010-06-09
I just noticed it, is that /dev/mmc device a memory card? Get it out while troubleshooting, they create issues sometimes. Has it been plugged in all this time?

And do you have two Vista installs, on /dev/sda1 and /dev/sda6?

---

### Post by wrightsimmo80 on 2010-06-09
> **darkod said:**
> I just noticed it, is that /dev/mmc device a memory card? Get it out while troubleshooting, they create issues sometimes. Has it been plugged in all this time?
 
And do you have two Vista installs, on /dev/sda1 and /dev/sda6?
 yes memory card was in since last night ...oops!! It just has a few photos on it however, i'll take it out and retry.
yes I installed the vista lite a few times in a few places when I was trying to get it to boot before i formatted partition 1 and installed it on there. 
can this cause the error?

---

### Post by darkod on 2010-06-10
> **wrightsimmo80 said:**
> 
yes I installed the vista lite a few times in a few places when I was trying to get it to boot before i formatted partition 1 and installed it on there. 
can this cause the error?

I'm not sure, I was just wondering what sda6 is.

If you don't use vista from sda6 and you don't have any data in that partition, I would open Gparted and just reformat /dev/sda6 as ntfs. That should wipe everything including grub2 on the partition boot sector.

Also, if any of the vista references are to this old sda6 vista, and we think they are from sda1, it will show once sda6 is formatted and might clear the picture.

---

### Post by wrightsimmo80 on 2010-06-10
I have formatted sda6 to ntfs re tried the purge grub that was suggested and this time grub menu loads so I can select OS which are all working... just not my recovery partition to get the original vista back on.
(thanks to you both for getting me this far.)


Tried the following command to boot recovery partition from grub  menu (then pressing c for command)

[QUOTE=

Once grub2 loads, press 'c' for command line (I think it works for grub2 too). When the grub command prompt loads, try to start /dev/sda3 with:

insmod ntfs
set root=(hd0,3)
makeactive
chainloader /bootmgr

[/QUOTE]

at the end of each command there is no apparent result it just goes to a new line (is that normal?)
and when I try 'makeactive' it tells me this is an unknown command.

---

### Post by darkod on 2010-06-10
> **wrightsimmo80 said:**
> I have formatted sda6 to ntfs re tried the purge grub that was suggested and this time grub menu loads so I can select OS which are all working... just not my recovery partition to get the original vista back on.
(thanks to you both for getting me this far.)


Tried the following command to boot recovery partition from grub  menu (then pressing c for command)



at the end of each command there is no apparent result it just goes to a new line (is that normal?)
and when I try 'makeactive' it tells me this is an unknown command.

I am still confused whether makeactive is needed for grub2, it was in grub1 I think. Drop it, and at the end if it just goes to new line try boot. So it would be like:

insmod ntfs
set root=(hd0,3)
chainloader /bootmgr
boot

PS. If the above doesn't work, another alternate is using chainloader +1, not /bootmgr. But I am trying to call the bootmgr loader directly.

It's all a learning experience for some of us too.

---

### Post by wrightsimmo80 on 2010-06-10
'I am still confused whether makeactive is needed for grub2, it was in  grub1 I think. Drop it, and at the end if it just goes to new line try  boot. So it would be like:

insmod ntfs
set root=(hd0,3)
chainloader /bootmgr
boot

PS. If the above doesn't work, another alternate is using chainloader  +1, not /bootmgr. But I am trying to call the bootmgr loader directly.

It's all a learning experience for some of us too.'

 tried the above commands 
chainloader /bootmgr did not work it gave me 'error: invalid signature"
but with chainloader + 1 this worked then at boot command 
it rebooted and ended back at grub screen. Am I right in thinking you can not just boot recovery partition through selecting it in grub? If I select sda3 from grub it just goes to blinking cursor. 
I think the final piece to the puzzle will be getting a recovery console installed onto this copy of vista so I can recover then re set up the dual boot without all the extra partitions  I have currently splattered everywhere.
What do you think?

cheers

---

