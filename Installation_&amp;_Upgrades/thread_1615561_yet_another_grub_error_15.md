---
title: "yet another grub error 15"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by riccardante on 2010-11-07
I need help for a grub error 15.

I have a Sony Vaio laptop, 250GB HD with the following partitions:

/dev/sda1  ntfs windows recovery
/dev/sda2  ntfs win Vista  
/dev/sda5  ext3 swap
/dev/sda6  ext3 Ubuntu 8.04
/dev/sda7  ext3 for /data 
/dev/sda8  testing Ubuntu 10.10   

I'm installing Ubuntu 10.10 (specify partitions manually)
in partition /dev/sda8 as ext4, mount point /
and /dev/sda5 as swap area
device for boot loader installation  /dev/sda8  (is this correct?)

after installation the result is:

```

GRUB Loading stage 1.5

Grub loading, please wait...
Error 15

```

here is the RESULTS.txt of the botinfoscript

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1               2,048    21,129,215    21,127,168  27 Hidden HPFS/NTFS
/dev/sda2    *     21,129,216   123,644,263   102,515,048   7 HPFS/NTFS
/dev/sda3         123,652,366   488,392,064   364,739,699   5 Extended
/dev/sda5         123,652,368   127,845,269     4,192,902  82 Linux swap / Solaris
/dev/sda6         127,845,333   295,612,064   167,766,732  83 Linux
/dev/sda7         295,612,128   473,869,304   178,257,177  83 Linux
/dev/sda8         473,869,368   488,392,064    14,522,697  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,250,015    31,249,953   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9E7EAA077EA9D7F3                       ntfs       Recovery                      
/dev/sda2        2ED87344D873097B                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        282fac68-bbf0-4588-88bc-324f51b1119e   swap                                     
/dev/sda6        454b83f9-9198-4daf-93dd-a1c9fb4c9eed   ext3                                     
/dev/sda7        8361bc46-1a67-4c7f-9ee3-1b39e3e4addc   ext3                                     
/dev/sda8        8c948be6-49ac-4ab6-a75f-718c93d5a419   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        54A449CAA449AEF4                       ntfs       RICCARDO                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/RICCARDO          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title        Ubuntu 8.04.1, kernel 2.6.24-21-server
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-server
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-server (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
initrd        /boot/initrd.img-2.6.24-21-server

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-server
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-server
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
initrd        /boot/initrd.img-2.6.24-19-server

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (strumenti di ripristino)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8361bc46-1a67-4c7f-9ee3-1b39e3e4addc /dati           ext3    relatime        0       2
# /dev/sda5
UUID=282fac68-bbf0-4588-88bc-324f51b1119e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  68.2GB: boot/grub/menu.lst
  68.2GB: boot/grub/stage2
  68.2GB: boot/initrd.img-2.6.24-16-generic
  68.2GB: boot/initrd.img-2.6.24-16-generic.bak
  68.2GB: boot/initrd.img-2.6.24-19-generic
  68.2GB: boot/initrd.img-2.6.24-19-generic.bak
  68.2GB: boot/initrd.img-2.6.24-19-server
  68.2GB: boot/initrd.img-2.6.24-19-server.bak
  68.2GB: boot/initrd.img-2.6.24-21-generic
  68.2GB: boot/initrd.img-2.6.24-21-generic.bak
  68.2GB: boot/initrd.img-2.6.24-21-server
  68.1GB: boot/initrd.img-2.6.24-21-server.bak
  68.2GB: boot/vmlinuz-2.6.24-16-generic
  68.1GB: boot/vmlinuz-2.6.24-19-generic
  68.2GB: boot/vmlinuz-2.6.24-19-server
  68.2GB: boot/vmlinuz-2.6.24-21-generic
  68.2GB: boot/vmlinuz-2.6.24-21-server
  68.2GB: initrd.img
  68.2GB: initrd.img.old
  68.2GB: vmlinuz
  68.2GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 8c948be6-49ac-4ab6-a75f-718c93d5a419
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 8c948be6-49ac-4ab6-a75f-718c93d5a419
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8c948be6-49ac-4ab6-a75f-718c93d5a419
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=8c948be6-49ac-4ab6-a75f-718c93d5a419 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8c948be6-49ac-4ab6-a75f-718c93d5a419
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=8c948be6-49ac-4ab6-a75f-718c93d5a419 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8c948be6-49ac-4ab6-a75f-718c93d5a419
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 8c948be6-49ac-4ab6-a75f-718c93d5a419
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7eaa077ea9d7f3
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ed87344d873097b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-21-server (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-21-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
    initrd /boot/initrd.img-2.6.24-21-server
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-21-server (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-21-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
    initrd /boot/initrd.img-2.6.24-21-server
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-21-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
    initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-21-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
    initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-19-server (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-19-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
    initrd /boot/initrd.img-2.6.24-19-server
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-19-server root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
    initrd /boot/initrd.img-2.6.24-19-server
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-19-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
    initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-19-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
    initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-16-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro quiet splash
    initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
    linux /boot/vmlinuz-2.6.24-16-generic root=UUID=454b83f9-9198-4daf-93dd-a1c9fb4c9eed ro single
    initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 8.04.1, memtest86+ (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 454b83f9-9198-4daf-93dd-a1c9fb4c9eed
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=282fac68-bbf0-4588-88bc-324f51b1119e none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 243.4GB: boot/grub/core.img
 247.4GB: boot/grub/grub.cfg
 249.9GB: boot/initrd.img-2.6.35-22-generic-pae
 243.5GB: boot/vmlinuz-2.6.35-22-generic-pae
 249.9GB: initrd.img
 243.5GB: vmlinuz

```

Can someone help me?
Thanks
r

---

### Post by garvinrick4 on 2010-11-07
You have got grub legacy in sda6 and grub2 in sda8
We are going to put grub2 from 10.10 in mbr (master boot record)
In live Cd open a terminal and copy and paste:

```
sudo mkdir /media/root
``````
sudo mount /dev/sda8 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
```boot into Hard drive to ubuntu 10.10 and 
```
sudo update-grub
```This will put windows in your boot menu and the grub config also.
grub legacy and grub2 do not quite work together well.
If for any reason they conflict we will have to purge grub legacy
and reinstall grub2 just in case.

---

### Post by riccardante on 2010-11-07
Thank you so much!
riccardante

---

### Post by garvinrick4 on 2010-11-07
You are welcome enjoy your Ubuntu

---

