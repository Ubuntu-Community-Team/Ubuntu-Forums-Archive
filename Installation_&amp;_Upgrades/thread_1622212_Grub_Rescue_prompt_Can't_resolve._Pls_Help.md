---
title: "Grub Rescue prompt: Can't resolve. Pls Help"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by seanbw on 2010-11-15
I have 2 partitions on my Acer laptop. One is on 138 GB (sda1) and the  other 15GB (sda5). Both are Ubuntu 10.04 LTS and I use sda5 to test  stuff before I install it on my main partition. So in that spirit, I  upgraded sda5 to 10.10 to see if I liked it. Big Mistake as now when I  restarted, all I get is a grub rescue prompt and I have no idea how to  fix it.
It appears that sda5 is on Grub2 and I thought that sda1 was  as well but it looks as if it is not. However by upgrading the sda5  partition, I seem to have messed up my ability to boot up and as now if I  boot, all I get a grub rescue prompt. I have attempted to follow the  various tips found on the forums but my problem is which do I reinstall?  I can't access my main partition and I don't know how to resolve it.
Is there anybody out here that can advice?

I tried following the advice given on this thread:
[HTML] http://ubuntuforums.org/showthread.php?t=1326788&page=3  [/HTML]
 but I don't know which of the sdaX to use to replace the sda5 in the following code:

```
  sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo chroot  /mnt  
``` 
Is it 1 or 6?
This is the result of the boot_info_script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 269235064 of the same hard drive for 
                       core.img, but core.img can not be found  at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,895,969   268,895,907  83 Linux
/dev/sda2         268,896,033   312,576,704    43,680,672   f W95 Ext d (LBA)
/dev/sda5         268,896,096   299,146,364    30,250,269  83 Linux
/dev/sda6         299,146,428   300,560,084     1,413,657  82 Linux swap / Solaris
/dev/sda7         300,560,148   312,576,704    12,016,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a956fe0d-0d24-4d45-9e31-8aaa2325facc   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6aec84a1-f6f8-4dbe-a5b6-bdb382508775   ext4                                     
/dev/sda6        4f0bc13a-bde8-433f-b818-b6444f1fd7a3   swap                                     
/dev/sda7        0c709687-fadd-48dc-b327-5451936c4872   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/a956fe0d-0d24-4d45-9e31-8aaa2325facc ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/6aec84a1-f6f8-4dbe-a5b6-bdb382508775 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/light-gray yellow/red

#A splash image for the menu
splashimage=/boot/grub/splashimages/gentleblue.xpm.gz

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
# kopt=root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a956fe0d-0d24-4d45-9e31-8aaa2325facc

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
# defoptions=splash vga=791

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
# howmany=2

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid        a956fe0d-0d24-4d45-9e31-8aaa2325facc
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro splash vga=791 
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid        a956fe0d-0d24-4d45-9e31-8aaa2325facc
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        a956fe0d-0d24-4d45-9e31-8aaa2325facc
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro splash vga=791 
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        a956fe0d-0d24-4d45-9e31-8aaa2325facc
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Chainload into GRUB 2
root        a956fe0d-0d24-4d45-9e31-8aaa2325facc
kernel        /boot/grub/core.img

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        a956fe0d-0d24-4d45-9e31-8aaa2325facc
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro single 
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda1 :
UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc    /    ext4    errors=remount-ro,    0    1
#Entry for /dev/sdb1 :
UUID=3E027FB3027F6F31    /media/MyBook500GB    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=16467BE21E725E9B    /media/Ubuntu    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8        0
UUID=6AFE84832426F75F    /media/ACER_BACKUP    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
UUID=C6031AAEE01DB9C2    /media/FREECOM40GB    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=0c709687-fadd-48dc-b327-5451936c4872    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0



=================== sda1: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/core.img
   3.2GB: boot/grub/grub.cfg
  28.7GB: boot/grub/menu.lst
 113.3GB: boot/initrd.img-2.6.32-24-generic
   7.2GB: boot/initrd.img-2.6.32-25-generic
   6.9GB: boot/vmlinuz-2.6.32-24-generic
   7.1GB: boot/vmlinuz-2.6.32-25-generic
   7.2GB: initrd.img
 113.3GB: initrd.img.old
   7.1GB: vmlinuz
   6.9GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
    search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=6aec84a1-f6f8-4dbe-a5b6-bdb382508775 ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=6aec84a1-f6f8-4dbe-a5b6-bdb382508775 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6aec84a1-f6f8-4dbe-a5b6-bdb382508775 ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6aec84a1-f6f8-4dbe-a5b6-bdb382508775 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6aec84a1-f6f8-4dbe-a5b6-bdb382508775 ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6aec84a1-f6f8-4dbe-a5b6-bdb382508775
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6aec84a1-f6f8-4dbe-a5b6-bdb382508775 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro splash vga=791
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro splash vga=791
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Chainload into GRUB 2 (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
    linux /boot/grub/core.img 
}
menuentry "Ubuntu 10.04.1 LTS, memtest86+ (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a956fe0d-0d24-4d45-9e31-8aaa2325facc
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=6aec84a1-f6f8-4dbe-a5b6-bdb382508775 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4f0bc13a-bde8-433f-b818-b6444f1fd7a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 137.8GB: boot/grub/core.img
 145.2GB: boot/grub/grub.cfg
 148.9GB: boot/initrd.img-2.6.32-24-generic
 150.9GB: boot/initrd.img-2.6.32-25-generic
 151.6GB: boot/initrd.img-2.6.35-23-generic
 145.3GB: boot/vmlinuz-2.6.32-24-generic
 148.0GB: boot/vmlinuz-2.6.32-25-generic
 149.3GB: boot/vmlinuz-2.6.35-23-generic
 151.6GB: initrd.img
 150.9GB: initrd.img.old
 149.3GB: vmlinuz
 148.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  46 fa 8d 48 74 14 0e f7  77 05 7d 77 88 90 81 44  |F..Ht...w.}w...D|
00000010  f4 f5 80 e5 45 ae 1a d9  8b 71 40 26 44 59 68 31  |....E....q@&DYh1|
00000020  ed 6e 49 c4 a8 84 6a 8a  97 1e 71 e1 b2 fc da e4  |.nI...j...q.....|
00000030  bb b1 82 25 0c 94 aa 90  fe 81 69 e9 07 fc e3 05  |...%......i.....|
00000040  65 e2 78 dc f1 40 1b 49  6c 47 cf fe 51 3c d3 b2  |e.x..@.IlG..Q<..|
00000050  00 b6 39 c4 73 61 15 cc  24 f0 62 be 22 ed b5 19  |..9.sa..$.b."...|
00000060  8f e0 7e 6e 0c 65 d3 65  3e 83 86 38 ed f4 f9 98  |..~n.e.e>..8....|
00000070  22 68 63 03 9a 93 2f 37  5d d3 93 42 8d 59 74 fb  |"hc.../7]..B.Yt.|
00000080  a9 52 44 c7 0c 0c ee b6  db b7 f9 69 0a 18 ab db  |.RD........i....|
00000090  fb 10 81 97 f5 80 50 6d  68 66 6c ba 50 58 02 1b  |......Pmhfl.PX..|
000000a0  48 c6 1d 55 9f 41 de 89  95 15 88 7c 13 23 21 a7  |H..U.A.....|.#!.|
000000b0  0e 10 50 3c d4 0a ec 05  33 c6 2a c4 bf df 45 45  |..P<....3.*...EE|
000000c0  4a 02 60 6e f7 fa b2 3b  c5 ef 85 18 41 6b 2c a0  |J.`n...;....Ak,.|
000000d0  34 4a a8 02 b1 69 18 df  b0 c9 9d 1a df 98 98 18  |4J...i..........|
000000e0  41 7b 0b 93 c0 81 6a 02  b6 9e be 62 42 29 00 28  |A{....j....bB).(|
000000f0  3f 25 33 70 89 44 60 50  57 11 2d 04 b4 fa 5c b9  |?%3p.D`PW.-...\.|
00000100  78 38 80 8f 04 09 f0 5b  2b a5 02 f9 40 ad d0 0b  |x8.....[+...@...|
00000110  48 47 2b 35 7e 49 98 73  89 e3 09 88 8f b7 14 89  |HG+5~I.s........|
00000120  49 83 80 ff bc 24 3e 18  00 1a e0 58 60 00 20 02  |I....$>....X`. .|
00000130  c3 5a 07 44 00 18 fc d9  0a 38 ed fc 6d 5e 20 0f  |.Z.D.....8..m^ .|
00000140  b5 34 2d 0a 40 64 00 de  00 58 ae 00 97 1d 58 7d  |.4-.@d...X....X}|
00000150  86 80 69 ed e0 79 b3 d1  20 60 00 43 6b bb 12 77  |..i..y.. `.Ck..w|
00000160  5e 01 de b5 43 03 9f a8  05 f9 7e 4c 79 07 2b 1f  |^...C.....~Ly.+.|
00000170  df 8a c2 b6 ed 8b b8 97  cb 97 10 dc 47 0f f9 a8  |............G...|
00000180  2d 60 e8 72 89 09 46 52  5b 14 cc 77 1a 29 2c 86  |-`.r..FR[..w.),.|
00000190  49 a0 c5 ee 1b ab f8 40  44 9c 8d 61 56 0d b9 46  |I......@D..aV..F|
000001a0  70 19 25 72 3e 52 d0 9e  a6 24 ec fa 07 80 90 59  |p.%r>R...$.....Y|
000001b0  04 2d b2 bc 00 93 b0 55  63 31 e8 5c 48 c7 00 fe  |.-.....Uc1.\H...|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 1d 95 cd 01 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff 5c 95  cd 01 58 92 15 00 00 00  |......\...X.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Is there anybody that can help?
PLEASE

---

### Post by dino99 on 2010-11-15
follow this command:

sudo grub-install --root-directory=/media/????? /dev/sda

where /media/???? is the partition label

******** Note:
you should not have menu.lst: its grub (legacy) not grub2 and they are not good friends. So remove/purge everything about grub & menu.lst first (only grub-pc need to be installed and grub-common)

---

### Post by drs305 on 2010-11-15
Grub was installed on the sda Ubuntu partition (sda1), which is not a good idea. It should be installed in the MBR instead.

Boot the LiveCD. Open a terminal and use these commands to restore grub to sda1. Do not use the partition number in the second command:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

I also notice you have two swap partitions (sda6, sda7). You only need one, which you can use for all your distros as long as they point to it.

---

### Post by seanbw on 2010-11-15
> **drs305 said:**
> Grub was installed on the sda Ubuntu partition (sda1), which is not a good idea. It should be installed in the MBR instead.

Boot the LiveCD. Open a terminal and use these commands to restore grub to sda1. Do not use the partition number in the second command:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```I also notice you have two swap partitions (sda6, sda7). You only need one, which you can use for all your distros as long as they point to it.
Thank you. Its worked. Many many many thanks for this.

So how do I install grub2 to both partitions.
After that how do I point both distros to the one swap partition?

---

### Post by drs305 on 2010-11-15
> **seanbw said:**
> Thank you. Its worked. Many many many thanks for this.

So how do I install grub2 to both partitions.
After that how do I point both distros to the one swap partition?

The way Grub2 works is that it is installed once on the MBR. You can have separate grub.cfg files in each partition's /boot/grub folder but only one will be used by Grub. This will be the one that the MBR points to (currently sda1). 

If you would prefer it use sda5, you would boot into that Ubuntu and run "sudo grub-install /dev/sda". At that point, it would use the sda5 grub.cfg.

If you are on your sda1 Ubuntu but want it to boot your sda5 grub.cfg:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Do not confuse this with which Ubuntu you want to boot! The above determines which grub.cfg you use, not which Ubuntu is your default OS. (I know, I'm confusing.)

 You can boot to either OS by setting the default value in /etc/default/grub. There are instructions on how to set the default OS in the link in my signature line: G2-Tasks.

For using one swap, just change the swap location in /etc/fstab to point to the correct partition. Right now, your sda1 and sda5 fstab's may point to different partitions. Pick the one you want to keep and just make the other fstab swap entry the same.

---

### Post by seanbw on 2010-11-16
Thanks for this. I now have grub2 in MBR but it appears it is still not pointing properly. I use sda1 (ubuntu) mainly but it appears that the system is still looking for something but I don't know what.
```


============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    [U][COLOR=Sienna]Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 269235064 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/U]
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

```
I am worried that the core.img its looking for may cause a problem when I upgrade sda1 to 10.10. Will this message disappear when I upgrade sda1 to 10.10?

> : For using one swap, just change the swap location in /etc/fstab to point  to the correct partition. Right now, your sda1 and sda5_ fstab's _may  point to different partitions. Pick the one you want to keep and just  make the other fstab swap entry the same.

Am I allowed to run gksudo gedit /etc/fstab and point to the same swap? I am asking because I know I can't amend some documents and I am still learning to know what and what I can't do.
Many thanks for resolving this issue. It appears to be a common difficulty.

---

### Post by drs305 on 2010-11-16
> **seanbw said:**
> Thanks for this. I now have grub2 in MBR but it appears it is still not pointing properly. **I use sda1 (ubuntu) mainly** 
```

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in **partition #5** for (,msdos5)/boot/grub.

```

Since you use mainly sda1, it would be best to have Grub2 boot to that Ubuntu and use it's grub.cfg. The reason is so the grub menu you see at boot is the one you are most likely to edit/update. You could use sda5's grub to boot, but if you want to make changes to your grub menu you would have to chroot or boot to the sda5 Ubuntu to make any changes. 

To change it so Grub looks at sda1, boot into your sda1 Ubuntu, then:
```
sudo grub-install /dev/sda
```
Now you will see your sda1 grub.cfg menu when you boot.



> 
Am I allowed to run gksudo gedit /etc/fstab and point to the same swap? I am asking because I know I can't amend some documents and I am still learning to know what and what I can't do.

Yes, you can do this, but you have to edit the file as 'root'. Open /etc/fstab as root ( gksu gedit /etc/fstab )  and make the change. You will also have to do this in your other Ubuntu /etc/fstab as well the next time you boot into that OS. 

After making the change and saving fstab, run this to update initrd:
```
sudo update-initramfs -u
```
> 
Grub 2 is installed in the boot sector of sda1 and looks at sector 269235064 of the same hard drive for core.img, but core.img can not be found at this location.


This currently isn't causing any problems. At one time G2 was installed on the partition - actually, it still is, but isn't being used. You can make things look a bit nicer by removing it. If you wish to do, you can use *testdisk* to write to the partition to remove the G2 message:
```
sudo apt-get install testdisk
sudo testdisk /dev/sda**1**
```
It's important to open only sda1. After testdisk opens look at the first page and make sure it says sda2 in the highlighted 'Disk' line.
From the first testdisk screen:
Proceed > Intel > MBR Code > Y > Y > OK > Quit > Quit

---

### Post by seanbw on 2010-11-16
OK. Thank you. One final (!!!) question. What do I do in etc/fstab. I was expecting a link that says swap but that only happens in sda5 and even then, it does not refer to any partition.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda1 :
UUID=a956fe0d-0d24-4d45-9e31-8aaa2325facc    /    ext4    errors=remount-ro,    0    1
#Entry for /dev/sdb1 :
UUID=3E027FB3027F6F31    /media/MyBook500GB    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=16467BE21E725E9B    /media/Ubuntu    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8        0
UUID=6AFE84832426F75F    /media/ACER_BACKUP    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
UUID=C6031AAEE01DB9C2    /media/FREECOM40GB    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=0c709687-fadd-48dc-b327-5451936c4872    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0

```

Many thanks for your assistance and patience.
I remember having referred to your HOW TO before when I wanted to  limit the  number of entries in my grub. It was easy to follow.

---

### Post by seanbw on 2010-11-16
Sorry: You said this:-
```
 It's important to open only sda1. After testdisk opens look at the first  page and make sure it says sda2 in the highlighted 'Disk' line. From the first testdisk screen: 
```
You mean this dont you?
```
 make sure it says _**sda1**_ in the highlighted 'Disk' line 
``` because it does say _**sda1**_ and not sda2 and there is no mention of sda2 at all.

---

### Post by dino99 on 2010-11-16
here is mine:

proc /proc proc defaults 0 2
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523 /home ext3 defaults,relatime 0 2
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16 none swap sw 0 0

of course, set it with your uuids, so only /home & swap

---

### Post by drs305 on 2010-11-16
> **seanbw said:**
> OK. Thank you. One final (!!!) question. What do I do in etc/fstab. I was expecting a link that says swap but that only happens in sda5 and even then, it does not refer to any partition.

```

#Entry for /dev/sda5 :
UUID=0c709687-fadd-48dc-b327-5451936c4872    none    swap    sw    0    0

```


This is your swap listing in /etc/fstab. Note that the comment about sda5 really doesn't mean a lot. It was created when you installed Ubuntu and never changes. If you changed partitions (create, delete) that device designation may not be correct. Don't trust what it says. Run "sudo fdisk -l" to see your current partitions.

To be clear, you don't *have* to change anything with your swap settings. You can have two swaps if you want - you just don't *need* two of them.

If you wanted to change the swap setting in the above, first check the UUIDs of your existing swap partitions:
```
sudo blkid -c /dev/null | grep "swap"
```
If it lists more than one, decide which one you want to use and change the UUID in fstab (if necessary). Save the file. If you did change the UUID, also run the following to update your initrd image:
```
sudo update-initramfs -u
```

---

### Post by seanbw on 2010-11-16
If I don't respond, it's bcos I've gone to pick up daughter. Otherwise couch 2night.

---

### Post by seanbw on 2010-11-16
Many thanks all. Done. Will now upgrade to 10.10 - I think I will wait. 
Will now mark this as solved.
Many many thanks.

---

