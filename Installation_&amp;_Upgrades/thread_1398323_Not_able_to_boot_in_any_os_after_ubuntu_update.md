---
title: "Not able to boot in any os after ubuntu update"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by captainapoorv on 2010-02-04
hI GUYS.......
today when i updated my ubuntu 9.10 it was about 44mb update and update manager was not able to download 13mb of files i clicked continue anyway. after that i shut down my pc and when i restarted it my old black and ordinary GRUB was gone and there was one with Debian symbol and blue background and everything and when i selected any OS ( i have 3 os 1 on my 80GB hard disk which is ubuntu and other 2 are debian and windows XP   which are on 20GB hard disk) and it said 

invalid character '+' 
file not found.

so i am now running on live cd. i am in terrible trouble. plz help!!!!

---

### Post by kansasnoob on 2010-02-04
> **captainapoorv said:**
> hI GUYS.......
today when i updated my ubuntu 9.10 it was about 44mb update and update manager was not able to download 13mb of files i clicked continue anyway. after that i shut down my pc and when i restarted it my old black and ordinary GRUB was gone and there was one with Debian symbol and blue background and everything and when i selected any OS ( i have 3 os 1 on my 80GB hard disk which is ubuntu and other 2 are debian and windows XP   which are on 20GB hard disk) and it said 

invalid character '+' 
file not found.

so i am now running on live cd. i am in terrible trouble. plz help!!!!

Well it's never a good idea to do a partial upgrade, especially if it's due to a disc/partition space problem. Regardless lets get a better look at things using the Boot Info script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by captainapoorv on 2010-02-12
hey sorry about replying so late!!! my internet was out of order.......... by the way i did as instructed on that site [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and the result was



============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.1 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c377c37

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,349,829     9,349,767   b W95 FAT32
/dev/sda2           9,349,830    19,599,299    10,249,470   f W95 Ext d (LBA)
/dev/sda5           9,349,893    15,502,724     6,152,832   b W95 FAT32
/dev/sda6          15,502,788    19,599,299     4,096,512   b W95 FAT32
/dev/sda3          19,599,300    21,639,554     2,040,255  82 Linux swap / Solaris
/dev/sda4          21,639,555    39,166,469    17,526,915  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42caf1a0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    39,086,144    39,086,082   c W95 FAT32 (LBA)
/dev/sdb2          39,086,145   144,520,739   105,434,595   f W95 Ext d (LBA)
/dev/sdb5          39,086,208    78,011,639    38,925,432   b W95 FAT32
/dev/sdb6          78,011,703    94,397,939    16,386,237   b W95 FAT32
/dev/sdb7          94,398,003   114,880,814    20,482,812   b W95 FAT32
/dev/sdb8         114,880,878   131,251,049    16,370,172   b W95 FAT32
/dev/sdb9         131,251,113   144,520,739    13,269,627   b W95 FAT32
/dev/sdb3         144,520,740   156,296,384    11,775,645  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        2C63-6DDF                              vfat                                     
/dev/sda3                                               swap                                     
/dev/sda4        4e594c83-83e8-4013-b530-1ebf23663a79   ext3                                     
/dev/sda5        48BE-9464                              vfat       e                             
/dev/sda6        48BE-9466                              vfat       f                             
/dev/sdb1        3A56-17E4                              vfat       VIDEO1                        
/dev/sdb3        dd6e00a8-ce5e-4034-8a94-6c7e35d84e74   ext3                                     
/dev/sdb5        0854-17EB                              vfat       VIDEO2                        
/dev/sdb6        1A4F-17EE                              vfat       APOORV                        
/dev/sdb7        2D3E-17F1                              vfat       IMAGES                        
/dev/sdb8        3E61-17F4                              vfat       DVDWRITER                     
/dev/sdb9        393A-17F7                              vfat       MISC                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb3        /media/dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ext3       (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda4/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-486
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro quiet
initrd        /boot/initrd.img-2.6.26-2-486

title        Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.26-2-486

title        Debian GNU/Linux, kernel 2.6.26-1-486
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro quiet
initrd        /boot/initrd.img-2.6.26-1-486

title        Debian GNU/Linux, kernel 2.6.26-1-486 (single-user mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.26-1-486

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda4: Location of files loaded by Grub: ===================


  11.0GB: boot/grub/menu.lst
  11.0GB: boot/grub/stage2
  11.0GB: boot/initrd.img-2.6.26-1-486
  11.0GB: boot/initrd.img-2.6.26-2-486
  11.0GB: boot/initrd.img-2.6.26-2-486.bak
  11.0GB: boot/vmlinuz-2.6.26-1-486
  11.0GB: boot/vmlinuz-2.6.26-2-486
  11.0GB: initrd.img
  11.0GB: initrd.img.old
  11.0GB: vmlinuz
  11.0GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
  insmod ext2
  set root=(hd1,3)
  search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
  insmod gfxmenu
  set theme=($root)/boot/grub/debian-theme/theme.txt
  set menuviewer=gfxmenu
fi
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
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
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
insmod png
loadfont /boot/grub/dejavu_sans_10.pf2
loadfont /boot/grub/dejavu_sans_12.pf2
loadfont /boot/grub/dejavu_sans_bold_14.pf2
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.31-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-16-generic ...
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-16-generic ...
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2c63-6ddf
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-486 (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro quiet
    initrd /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro single
    initrd /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-1-486 (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro quiet
    initrd /boot/initrd.img-2.6.26-1-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-1-486 (single-user mode) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro single
    initrd /boot/initrd.img-2.6.26-1-486
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 /               ext3    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  73.9GB: boot/grub/core.img
  73.9GB: boot/grub/grub.cfg
  73.9GB: boot/initrd.img-2.6.31-14-generic
  73.9GB: boot/initrd.img-2.6.31-16-generic
  73.9GB: boot/initrd.img-2.6.31-17-generic
  73.9GB: boot/vmlinuz-2.6.31-14-generic
  73.9GB: boot/vmlinuz-2.6.31-16-generic
  73.9GB: boot/vmlinuz-2.6.31-17-generic
  73.9GB: initrd.img
  73.9GB: initrd.img.old
  73.9GB: vmlinuz
  73.9GB: vmlinuz.old













but i wanted to start my windows so what i did was i put the old dvd of Debian lenny and repaired the grub so i got my old grub ( the one which i had when i had only windows and debian) back but now i have a new problem UBUNTU IS NOT THERE IN MY OLD GRUB!!!!!!! help me with this!!!!!!

---

### Post by captainapoorv on 2010-02-12
by the way i forgot to tell that now i can boot in windows and Debian!!!!

---

### Post by darkod on 2010-02-12
> **captainapoorv said:**
> 

but i wanted to start my windows so what i did was i put the old dvd of Debian lenny and repaired the grub so i got my old grub ( the one which i had when i had only windows and debian) back but now i have a new problem UBUNTU IS NOT THERE IN MY OLD GRUB!!!!!!! help me with this!!!!!!

You didn't repair grub, you FULLY INSTALLED Lenny. Why didn't you just use the ubuntu cd to repair grub? Further more, it seems Lenny installed grub1, not grub2.

If you want to keep using Lenny grub, you need to manually add ubuntu to /boot/grub/menu.lst. If you don't want to keep using Lenny at all, I suggest just reinstalling grub2 from karmic, as you should have done.

Can you run the boot info script again and post the results? Something seems funny. Also when posting the results try to put them in CODE tags for easier reading. You can do this if you select the whole text that you copied and click the # button in the toolbar above while writing your post.

---

### Post by kansasnoob on 2010-02-12
I assume that you ran the Boot Info Script before you restored Debian's grub because of this:

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #3 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb

Although that doesn't quite make sense either because XP is on sda1, Lenny is on sda4, and Karmic is on sdb3. 

I almost wonder if there might be a bug in the Boot Info Script? I'll give Meierfra a shout later on.

Anyway you have two options. You could add Ubuntu to the Debian menu.lst by booting into Lenny and first backing up the menu.lst (BTW that's a lower case L in "lst"):

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Then if you're using the Gnome desktop environment just run:

```
gksudo gedit /boot/grub/menu.lst
```

And at the very bottom, below the Windows entry add:

```
# Added by me for Karmic
title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro quiet splash
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic
```

Be sure to click on Save, then File > Quit.

One caveat is that kernel updates will have to be added to the menu.lst manually, ie:

```
# Added by me for Karmic
title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro quiet splash
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

# Added by me for Karmic
title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro quiet splash
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic
```

Notice there I just used copy-n-paste to add another copy of the 2.6.31-17 kernel below the existing entry and then changed the "17" to "19" in the two entries for boot and recovery above.

The other option is to get grub2 working and I think that would be preferable, but I don't see why it didn't work to begin with.

As Darkod said download the Boot Info Script again (Meiefra frequently makes changes) and then run it again and post the new output.

---

### Post by kansasnoob on 2010-02-12
> You didn't repair grub, you FULLY INSTALLED Lenny.

Darko,

He already had Lenny installed, but did you notice the oddities I pointed out?

Puzzling!!!!!!!!!!!

---

### Post by darkod on 2010-02-12
> **kansasnoob said:**
> Darko,

He already had Lenny installed, but did you notice the oddities I pointed out?

Puzzling!!!!!!!!!!!

I wasn't sure about Lenny. Yeah, that's why I said "something seems funny".
First grub2 is reported on /dev/sda looking at partition #3 and /dev/sda3 is swap.
On the other hand, ubuntu root is /dev/sdb3 but grub2 says it's on /dev/sda. Hmmm...

On another thread the script seems to run short with only small pieces of info. It seems the current version of the script might have an issue.

---

### Post by darkod on 2010-02-12
> **darkod said:**
> You didn't repair grub, you FULLY INSTALLED Lenny. 

Sorry, I missed the part of the first post saying you have 3 OSs. I thought Lenny got installed by mistake while doing the repair.

---

### Post by oldfred on 2010-02-12
I just got info back from meierfra that he has reverted ver 52 back to ver51 since it will take him a bit to update and correct the script. So anyone that downloaded the ver52 script that has partial results should download again.

I also recommend installing grub2 as the best solution to solving the OP's issues. It does seem very strange how grub is mixed up. I wonder if it is a device.map issue also?

---

### Post by kansasnoob on 2010-02-12
> **oldfred said:**
> I just got info back from meierfra that he has reverted ver 52 back to ver51 since it will take him a bit to update and correct the script. So anyone that downloaded the ver52 script that has partial results should download again.

I also recommend installing grub2 as the best solution to solving the OP's issues. It does seem very strange how grub is mixed up. I wonder if it is a device.map issue also?

Karmic's grub has been giving me fits, just as an example this is a Lucid grub2 entry:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-13-generic" {
        recordfail
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 9c10b8f7-89d3-4a72-a0ab-e89d061653b0
	linux	/boot/vmlinuz-2.6.32-13-generic root=UUID=9c10b8f7-89d3-4a72-a0ab-e89d061653b0 ro splash quiet  quiet
	initrd	/boot/initrd.img-2.6.32-13-generic
}
```

This is a Karmic entry:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,11)
	search --no-floppy --fs-uuid --set 33b90c3d-da7e-4671-b78a-5adafb0a927d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
```

The differences are real obvious if you paste them both into a blank gedit page. They're both auto-generated with no tweaks at all.

When my Karmic updated to kernel 2.6.31-19 and things stopped working I just reverted it to legacy grub and then handed boot back to Lucid because I was short on both time and patience. That happens when you get old :)

Anyway I haven't tried the latest Lucid grub2 packages (grub-pc and grub-common) in Karmic yet but I tried some changes earlier:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

FYI I'm Erick there.

OTOH I think Meierfra has all of the fixes here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

---

### Post by captainapoorv on 2010-02-21
i just pasted that code in menu.lst and now i am restarting system!!!

---

### Post by captainapoorv on 2010-02-21
hey no luck there i pasted that code in menu.lst but when i selected it from GRUB list it said 

file not found

so now i am running that boot info script again................
i will post it here!!!

---

### Post by captainapoorv on 2010-02-21
hey for information i have 2 hard disks on 1 there is Debian and Windows XP and on other There is Ubuntu..................

by the way here is result of new boot info script




    ```
           Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/hdc

hda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   

hdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c377c37

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63     9,349,829     9,349,767   b W95 FAT32
/dev/hda2           9,349,830    19,599,299    10,249,470   f W95 Ext d (LBA)
/dev/hda5           9,349,893    15,502,724     6,152,832   b W95 FAT32
/dev/hda6          15,502,788    19,599,299     4,096,512   b W95 FAT32
/dev/hda3          19,599,300    21,639,554     2,040,255  82 Linux swap / Solaris
/dev/hda4          21,639,555    39,166,469    17,526,915  83 Linux


Drive: hdc ___________________ _____________________________________________________

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42caf1a0

Partition  Boot         Start           End          Size  Id System

/dev/hdc1                  63    39,086,144    39,086,082   c W95 FAT32 (LBA)
/dev/hdc2          39,086,145   144,520,739   105,434,595   f W95 Ext d (LBA)
/dev/hdc5          39,086,208    78,011,639    38,925,432   b W95 FAT32
/dev/hdc6          78,011,703    94,397,939    16,386,237   b W95 FAT32
/dev/hdc7          94,398,003   114,880,814    20,482,812   b W95 FAT32
/dev/hdc8         114,880,878   131,251,049    16,370,172   b W95 FAT32
/dev/hdc9         131,251,113   144,520,739    13,269,627   b W95 FAT32
/dev/hdc3         144,520,740   156,296,384    11,775,645  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        2C63-6DDF                              vfat                                     
/dev/hda3                                               swap                                     
/dev/hda4        4e594c83-83e8-4013-b530-1ebf23663a79   ext3                                     
/dev/hda5        48BE-9464                              vfat       e                             
/dev/hda6        48BE-9466                              vfat       f                             
/dev/hdc1        3A56-17E4                              vfat       VIDEO1                        
/dev/hdc3        dd6e00a8-ce5e-4034-8a94-6c7e35d84e74   ext3                                     
/dev/hdc5        0854-17EB                              vfat       VIDEO2                        
/dev/hdc6        1A4F-17EE                              vfat       APOORV                        
/dev/hdc7        2D3E-17F1                              vfat       IMAGES                        
/dev/hdc8        3E61-17F4                              vfat       DVDWRITER                     
/dev/hdc9        393A-17F7                              vfat       MISC                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/hda4        /                        ext3       (rw,errors=remount-ro)


================================ hda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== hda4/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-486
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro quiet
initrd        /boot/initrd.img-2.6.26-2-486

title        Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.26-2-486

title        Debian GNU/Linux, kernel 2.6.26-1-486
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro quiet
initrd        /boot/initrd.img-2.6.26-1-486

title        Debian GNU/Linux, kernel 2.6.26-1-486 (single-user mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.26-1-486

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# Added by me for Karmic
title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro quiet splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic


=============================== hda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== hda4: Location of files loaded by Grub: ===================


  16.1GB: boot/grub/menu.lst
  16.1GB: boot/grub/stage2
  13.0GB: boot/initrd.img-2.6.26-1-486
  13.0GB: boot/initrd.img-2.6.26-2-486
  13.3GB: boot/initrd.img-2.6.26-2-486.bak
  13.0GB: boot/vmlinuz-2.6.26-1-486
  17.1GB: boot/vmlinuz-2.6.26-2-486
  13.0GB: initrd.img
  13.0GB: initrd.img.old
  17.1GB: vmlinuz
  13.0GB: vmlinuz.old

=========================== hdc3/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
  insmod ext2
  set root=(hd1,3)
  search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
  insmod gfxmenu
  set theme=($root)/boot/grub/debian-theme/theme.txt
  set menuviewer=gfxmenu
fi
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
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
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
insmod png
loadfont /boot/grub/dejavu_sans_10.pf2
loadfont /boot/grub/dejavu_sans_12.pf2
loadfont /boot/grub/dejavu_sans_bold_14.pf2
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.31-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-16-generic ...
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-16-generic ...
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2c63-6ddf
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-486 (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro quiet
    initrd /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro single
    initrd /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-1-486 (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro quiet
    initrd /boot/initrd.img-2.6.26-1-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-1-486 (single-user mode) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro single
    initrd /boot/initrd.img-2.6.26-1-486
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== hdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 /               ext3    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== hdc3: Location of files loaded by Grub: ===================


  76.2GB: boot/grub/core.img
  76.1GB: boot/grub/grub.cfg
  76.1GB: boot/initrd.img-2.6.31-14-generic
  76.2GB: boot/initrd.img-2.6.31-16-generic
  76.2GB: boot/initrd.img-2.6.31-17-generic
  76.2GB: boot/vmlinuz-2.6.31-14-generic
  76.1GB: boot/vmlinuz-2.6.31-16-generic
  76.2GB: boot/vmlinuz-2.6.31-17-generic
  76.2GB: initrd.img
  76.2GB: initrd.img.old
  76.2GB: vmlinuz
  76.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

hdb hdd 
```

---

### Post by darkod on 2010-02-21
Which code exactly did you paste?
First of all, you need to be sure you are running grub1.
If you are, simply pasting those entries from kansasnoob won't work because they are from grub2. For example, in grub2 the entry starts with menuentry and in grub1 with title. The rest of the commands are slightly different too.

In grub1 you should be able to boot karmic with:

title Karmic
root (hd0,4)
kernel /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic

Under the assumption you have karmic on /dev/sda5 on your only hdd. And you haven't removed the original -14 kernel.

If you post your
sudo fdisk -l

from your current situation, I can check if those commands need adjustment.

EDIT: I just saw your latest post with the results, hold on.

---

### Post by darkod on 2010-02-21
Change the karmic entries to:

title Ubuntu 9.10, kernel 2.6.31-17-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.31-17-generic root=/dev/hdc3 ro quiet splash
initrd /boot/initrd.img-2.6.31-17-generic

That should do it.

---

### Post by captainapoorv on 2010-02-23
i did paste that code given by darkod

title Ubuntu 9.10, kernel 2.6.31-17-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.31-17-generic root=/dev/hdc3 ro quiet splash
initrd /boot/initrd.img-2.6.31-17-generic


and then rebooted and it showed up in grub menu and then i selected ubuntu and many lines flashed...............
and then that white ubuntu logo came and some things started coming under it!!! 
and first 5 to 6 where ok....
and then came "searching for root" or something and then this showed up!!!

ALERT! /dev/hdc3 does not exist. Dropping to shell

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1 ubuntu7) built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs)

---

### Post by darkod on 2010-02-23
[COLOR=Red]/dev/hdc3[/COLOR]         144,520,740   156,296,384    11,775,645  83 Linux

It does exist as per your latest results file. However I did notice that there is no hdb in the results so hdc might have become hdb. Depending if there were any changes.

Can you post current results content and lets see.

---

### Post by captainapoorv on 2010-02-26
i installed GRUB2 from synaptic in debian and chain loaded it from grub so now grub also starts and first there is option for chain load it and then below it there usual grub menu with debian and windows.
So i chain loaded it and in grub2 menu there was only debian and no sign of windows or ubuntu!
by the way here are current results of boot info script


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/hdc

hda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

hdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   

hdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c377c37

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63     9,349,829     9,349,767   b W95 FAT32
/dev/hda2           9,349,830    19,599,299    10,249,470   f W95 Ext d (LBA)
/dev/hda5           9,349,893    15,502,724     6,152,832   b W95 FAT32
/dev/hda6          15,502,788    19,599,299     4,096,512   b W95 FAT32
/dev/hda3          19,599,300    21,639,554     2,040,255  82 Linux swap / Solaris
/dev/hda4          21,639,555    39,166,469    17,526,915  83 Linux


Drive: hdc ___________________ _____________________________________________________

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42caf1a0

Partition  Boot         Start           End          Size  Id System

/dev/hdc1                  63    39,086,144    39,086,082   c W95 FAT32 (LBA)
/dev/hdc2          39,086,145   144,520,739   105,434,595   f W95 Ext d (LBA)
/dev/hdc5          39,086,208    78,011,639    38,925,432   b W95 FAT32
/dev/hdc6          78,011,703    94,397,939    16,386,237   b W95 FAT32
/dev/hdc7          94,398,003   114,880,814    20,482,812   b W95 FAT32
/dev/hdc8         114,880,878   131,251,049    16,370,172   b W95 FAT32
/dev/hdc9         131,251,113   144,520,739    13,269,627   b W95 FAT32
/dev/hdc3         144,520,740   156,296,384    11,775,645  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        2C63-6DDF                              vfat                                     
/dev/hda3                                               swap                                     
/dev/hda4        4e594c83-83e8-4013-b530-1ebf23663a79   ext3                                     
/dev/hda5        48BE-9464                              vfat       e                             
/dev/hda6        48BE-9466                              vfat       f                             
/dev/hdc1        3A56-17E4                              vfat       VIDEO1                        
/dev/hdc3        dd6e00a8-ce5e-4034-8a94-6c7e35d84e74   ext3                                     
/dev/hdc5        0854-17EB                              vfat       VIDEO2                        
/dev/hdc6        1A4F-17EE                              vfat       APOORV                        
/dev/hdc7        2D3E-17F1                              vfat       IMAGES                        
/dev/hdc8        3E61-17F4                              vfat       DVDWRITER                     
/dev/hdc9        393A-17F7                              vfat       MISC                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/hda4        /                        ext3       (rw,errors=remount-ro)


================================ hda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== hda4/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Chainload into GRUB 2
root        (hd0,3)
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Debian GNU/Linux, kernel 2.6.26-2-486
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro quiet
initrd        /boot/initrd.img-2.6.26-2-486

title        Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.26-2-486

title        Debian GNU/Linux, kernel 2.6.26-1-486
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro quiet
initrd        /boot/initrd.img-2.6.26-1-486

title        Debian GNU/Linux, kernel 2.6.26-1-486 (single-user mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.26-1-486

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1



=========================== hda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,4)
search --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd0,4)
search --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Debian GNU/Linux, linux 2.6.26-2-486" {
    set root=(hd0,4)
    search --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux    /boot/vmlinuz-2.6.26-2-486 root=UUID=4e594c83-83e8-4013-b530-1ebf23663a79 ro  
    initrd    /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, linux 2.6.26-2-486 (single-user mode)" {
    set root=(hd0,4)
    search --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux    /boot/vmlinuz-2.6.26-2-486 root=UUID=4e594c83-83e8-4013-b530-1ebf23663a79 ro single 
    initrd    /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, linux 2.6.26-1-486" {
    set root=(hd0,4)
    search --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux    /boot/vmlinuz-2.6.26-1-486 root=UUID=4e594c83-83e8-4013-b530-1ebf23663a79 ro  
    initrd    /boot/initrd.img-2.6.26-1-486
}
menuentry "Debian GNU/Linux, linux 2.6.26-1-486 (single-user mode)" {
    set root=(hd0,4)
    search --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux    /boot/vmlinuz-2.6.26-1-486 root=UUID=4e594c83-83e8-4013-b530-1ebf23663a79 ro single 
    initrd    /boot/initrd.img-2.6.26-1-486
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== hda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== hda4: Location of files loaded by Grub: ===================


  16.0GB: boot/grub/core.img
  16.1GB: boot/grub/grub.cfg
  16.1GB: boot/grub/menu.lst
  16.1GB: boot/grub/stage2
  13.0GB: boot/initrd.img-2.6.26-1-486
  13.0GB: boot/initrd.img-2.6.26-2-486
  13.3GB: boot/initrd.img-2.6.26-2-486.bak
  13.0GB: boot/vmlinuz-2.6.26-1-486
  17.1GB: boot/vmlinuz-2.6.26-2-486
  13.0GB: initrd.img
  13.0GB: initrd.img.old
  17.1GB: vmlinuz
  13.0GB: vmlinuz.old

=========================== hdc3/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
  insmod ext2
  set root=(hd1,3)
  search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
  insmod gfxmenu
  set theme=($root)/boot/grub/debian-theme/theme.txt
  set menuviewer=gfxmenu
fi
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
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
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
insmod png
loadfont /boot/grub/dejavu_sans_10.pf2
loadfont /boot/grub/dejavu_sans_12.pf2
loadfont /boot/grub/dejavu_sans_bold_14.pf2
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.31-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-16-generic ...
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-16-generic ...
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set dd6e00a8-ce5e-4034-8a94-6c7e35d84e74
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 ro single 
    echo    Loading initial ramdisk ...
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2c63-6ddf
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-486 (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro quiet
    initrd /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-2-486 root=/dev/hda4 ro single
    initrd /boot/initrd.img-2.6.26-2-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-1-486 (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro quiet
    initrd /boot/initrd.img-2.6.26-1-486
}
menuentry "Debian GNU/Linux, kernel 2.6.26-1-486 (single-user mode) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 4e594c83-83e8-4013-b530-1ebf23663a79
    linux /boot/vmlinuz-2.6.26-1-486 root=/dev/hda4 ro single
    initrd /boot/initrd.img-2.6.26-1-486
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== hdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=dd6e00a8-ce5e-4034-8a94-6c7e35d84e74 /               ext3    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== hdc3: Location of files loaded by Grub: ===================


  76.2GB: boot/grub/core.img
  76.1GB: boot/grub/grub.cfg
  76.1GB: boot/initrd.img-2.6.31-14-generic
  76.2GB: boot/initrd.img-2.6.31-16-generic
  76.2GB: boot/initrd.img-2.6.31-17-generic
  76.2GB: boot/vmlinuz-2.6.31-14-generic
  76.1GB: boot/vmlinuz-2.6.31-16-generic
  76.2GB: boot/vmlinuz-2.6.31-17-generic
  76.2GB: initrd.img
  76.2GB: initrd.img.old
  76.2GB: vmlinuz
  76.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

hdb hdd 
```

---

### Post by oldfred on 2010-02-26
Your chainload entry is for testing of grub2 in Debian and chainloads just to the grub2 version of grub.cfg for Debian not to the Ubuntu install. If you still want to chain load you can install grub or grub2 to the MBR of sdc from Ubuntu and chainload to that.

Perhaps the grub2 in Debian will work like grub2 for Ubuntu and sudo update-grub will add the extra entries?

---

### Post by captainapoorv on 2010-02-27
:D:D:D hi guys i am writing from ubuntu now!!!!!!!!!!
 i just read about GRUB2 at [www.dedoimedo.com](www.dedoimedo.com).......................................................
and then i ran update-grub commend hoping that it will run the 30_os-prober script but it doesnt then i googled it a bit and came to know that to run that script i should have os-prober package first!!!!!!
i installed it from synaptic and then ran update-grub and................................... WOOOOOOOOOOW it was there!!!!!!!!!!!!!!!!!!!!!!!:D:D:D:D:D
THANKS EVERYONE FOR HELPING ME!!!!!
THANKS DARKOD, OLDFRED, KANSASNOOB!!!!!!
GUYS REALLY THANKS!!!!!

---

