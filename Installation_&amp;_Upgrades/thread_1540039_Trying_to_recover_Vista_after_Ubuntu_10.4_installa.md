---
title: "Trying to recover Vista after Ubuntu 10.4 installation"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by mumble83 on 2010-07-27
Hi,
after having installed Ubuntu 10.4 I cannot boot anymore in Vista, since I accidentally overwrite Windows bootloader, as you can see from the bootscript output:

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 593897347 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 593900323 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 593903299 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,467,712   323,074,047   302,606,336   6 FAT16
/dev/sda3         323,074,048   584,059,139   260,985,092   7 HPFS/NTFS
/dev/sda4         584,059,140   625,137,344    41,078,205   5 Extended
/dev/sda5         584,059,203   623,129,219    39,070,017  83 Linux
/dev/sda6         623,129,283   625,137,344     2,008,062  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3448D9F8E49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        DAE4F6C7E4F6A543                       ntfs       ACER                          
/dev/sda3        38924BB7924B7880                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b3489956-ea40-44c7-90d1-87cc4467e773   ext4                                     
/dev/sda6        a3e6263a-a328-4004-928d-ff53070ab028   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1                                               vfat       VERBATIM                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/VERBATIM_         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
set default="7"
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
search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
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
search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
set locale_dir=($root)/boot/grub/locale
set lang=it
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    echo    'Caricamento Linux 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-14-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    echo    'Caricamento Linux 2.6.31-14-generic...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3448d9f8e49bed2a
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set dae4f6c7e4f6a543
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=b3489956-ea40-44c7-90d1-87cc4467e773 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a3e6263a-a328-4004-928d-ff53070ab028 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#DIMT  mount DATA hard drive at startup 
/dev/sda3       /media/DATA   ntfs 0       0

=================== sda5: Location of files loaded by Grub: ===================


 299.3GB: boot/grub/core.img
 299.7GB: boot/grub/grub.cfg
 303.3GB: boot/initrd.img-2.6.31-14-generic
 300.0GB: boot/initrd.img-2.6.32-22-generic
 301.1GB: boot/vmlinuz-2.6.31-14-generic
 300.5GB: boot/vmlinuz-2.6.32-22-generic
 300.0GB: initrd.img
 303.3GB: initrd.img.old
 300.5GB: vmlinuz
 301.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

```I found some instructions to recover Windows bootloader and try them on a backup hard drive where I copied only sda2 partition.
Now the bootloader seems to be ok, but the file system is not recognized. 

```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4096 MB, 4096253952 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8000496 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdefef196

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     8,000,369     8,000,307  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xecbe071e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   322,328,159   322,328,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3f50260f-2415-49bb-8e77-dc6531a17e6b   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,noatime,errors=remount-ro)
/dev/bus/usb     /proc/bus/usb            usbfs      (rw)


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
default        2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# kopt=root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=ht=on acpi=force reboot=a

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpia
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpia root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro ht=off acpi=force reboot=a
initrd        /boot/initrd.img-2.6.24-24-lpia
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpia (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpia root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro single
initrd        /boot/initrd.img-2.6.24-24-lpia

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpiacustom
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpiacustom root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro ht=on acpi=force reboot=a quiet 
initrd        /boot/initrd.img-2.6.24-24-lpiacustom
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpiacustom (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpiacustom root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro single
initrd        /boot/initrd.img-2.6.24-24-lpiacustom

### END DEBIAN AUTOMAGIC KERNELS LIST

========================== sda1/boot/grub/grub.conf: ==========================

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
timeout        5

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
# kopt=root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=ht=on acpi=force reboot=a

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpia
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpia root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro ht=off acpi=force reboot=a
initrd        /boot/initrd.img-2.6.24-24-lpia
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpia (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpia root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro single
initrd        /boot/initrd.img-2.6.24-24-lpia

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpiacustom
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpiacustom root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro ht=on acpi=force reboot=a quiet
initrd        /boot/initrd.img-2.6.24-24-lpiacustom
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-lpiacustom (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-lpiacustom root=UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b ro single
initrd        /boot/initrd.img-2.6.24-24-lpiacustom

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# UNCONFIGURED FSTAB FOR BASE SYSTEM
UUID=3f50260f-2415-49bb-8e77-dc6531a17e6b    /    ext3    norelatime,noatime,errors=remount-ro    0    1
proc        /proc        proc        defaults        0    0
devpts        /dev/pts    devpts        defaults        0    0
/dev/bus/usb    /proc/bus/usb    usbfs         defaults    0    0

=================== sda1: Location of files loaded by Grub: ===================


   1.4GB: boot/grub/grub.conf
   1.5GB: boot/grub/menu.lst
   1.5GB: boot/grub/stage2
   1.5GB: boot/initrd.img-2.6.24-24-lpia
   1.5GB: boot/initrd.img-2.6.24-24-lpiacustom
   1.5GB: boot/initrd.img-2.6.24-24-lpiacustom.bak
   1.5GB: boot/vmlinuz
   1.6GB: boot/vmlinuz-2.6.24-24-lpia
   1.5GB: boot/vmlinuz-2.6.24-24-lpiacustom
   1.5GB: initrd.img
   1.5GB: initrd.img.old
   1.5GB: vmlinuz
   1.6GB: vmlinuz.old


```How can I test if the file system is really corrupted? 
Do you have any other suggestion to recover the Vista partition?
Thanks

---

### Post by bcbc on 2010-07-27
You've installed grub2 to the windows partition - overwriting the windows boot sector. You'll need to get it fixed before vista will work. see here [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The testdisk fix is the best (it seems), and note that if you opt with the windows repair 'bootrect' should be 'bootrec'

Note: you need grub2 in the drive MBR to dual boot - replacing this with the windows bootloader means you'll only boot windows (and only after you fix the boot sector).

---

### Post by mumble83 on 2010-07-27
Do you mean that I didn't solve the problem looking at the second output? Here for sdb1 (the backuped partition) I see again Vista bootloader (instead of grub2 as in the first one).
I tried the "testdisk" method but I don't have the "BackupBS" option in the 6th screen, and then I applied the "bootrec" method.
However I cannot boot on Vista yet. Do I need also the partition sda1 of the original hard drive to boot? This was not corresponding to C: partition (which is sda2), hence I thought I could use only sda2

---

### Post by bcbc on 2010-07-27
> **mumble83 said:**
> Do you mean that I didn't solve the problem looking at the second output? Here for sdb1 (the backuped partition) I see again Vista bootloader (instead of grub2 as in the first one).
I tried the "testdisk" method but I don't have the "BackupBS" option in the 6th screen, and then I applied the "bootrec" method.
However I cannot boot on Vista yet. Do I need also the partition sda1 of the original hard drive to boot? This was not corresponding to C: partition (which is sda2), hence I thought I could use only sda2

I was focusing on the first results. Your second results on the test system says that the windows partition is 'unknown filesystem type'. I don't think that the copy worked. So did you want to fix the original computer or the one with the copy?

---

### Post by bcbc on 2010-07-27
Another thing, fdisk is seeing /dev/sda2 as FAT16 and it should be ntfs. You might need to correct this before testdisk can recover the boot sector.

---

### Post by mumble83 on 2010-07-27
My goal is to bring again the original to work, but I tried first on a copy.
How can I test if the copy is actually corrupted? With testdisk and fdisk -l is recognized as HPFS-NTFS type.

---

### Post by bcbc on 2010-07-27
> **mumble83 said:**
> My goal is to bring again the original to work, but I tried first on a copy.
How can I test if the copy is actually corrupted? With testdisk and fdisk -l is recognized as HPFS-NTFS type.

I don't know how you copied it, but I'm pretty sure that win7 is aware of it's partition and won't work like this - unless you've cloned the entire drive.

The bootsector fix in testdisk just looks for the existence of a different backup boot sector and replaces the current boot sector with it. It won't affect anything else, and since your current boot sector is junk - I would say - just fix it. If testdisk doesn't work, go for windows repair.

This problem happened to many, many people when 10.04 was released.

---

### Post by mumble83 on 2010-07-27
I copied it with Partimage. 
I didn't succeed using "testdisk" also in the original hard drive (no BackupBS option).
What would you suggest me? Try to correct sda2 to NTFS in the original drive? Do you know how to do it?

---

### Post by bcbc on 2010-07-27
> **mumble83 said:**
> I copied it with Partimage. 
I didn't succeed using "testdisk" also in the original hard drive (no BackupBS option).
What would you suggest me? Try to correct sda2 to NTFS in the original drive? Do you know how to do it?
There was one thread where the poster solved it by changing the drive back to ntfs, and then testdisk found the backup boot sector ([http://ubuntuforums.org/showthread.php?t=1491780](http://ubuntuforums.org/showthread.php?t=1491780)). But you said that testdisk already sees it as ntfs so this may not work for you.

I can't advise on how to change the file system type - I've never done it and don't want to speculate.

---

