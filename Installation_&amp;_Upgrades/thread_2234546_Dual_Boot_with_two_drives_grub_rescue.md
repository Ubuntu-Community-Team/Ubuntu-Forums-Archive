---
title: "Dual Boot with two drives grub rescue"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by sigend on 2014-07-15
Hello,

i have got on my laptop two HDDs.
The first one is an SSD which contains only Windows 7 (sda).
The second is connected to the sata interface where the DVD used to be.This one has a partition with ubuntu.(sdb)
The problem is after I installed ubuntu on the second HDD (windows were installed already) i cant boot.
I get an error 
No such device 22a3e1f4-e88b-4241-982f-515a316cb4b6 
grub rescue>

This device seems to be my sdb1-->ubuntu installation on the second HDD.


Actually i can boot only if I get into boot mode while the laptop starts and  select boot from Hard-Drives.
If i change the boot priority and select the second HDD as first boot priority nothing happens :/



I attach ,my pastebin from boot-repair.


thx guys :)

```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 59566424 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for .
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf 
                       /boot/grub/i386-pc/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......#..9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 2060304 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   234,135,488   234,133,441   7 NTFS / exFAT / HPFS
/dev/sda2         234,135,489   234,440,703       305,215   f W95 Extended (LBA)
/dev/sda5         234,135,552   234,440,703       305,152   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    74,220,797    74,218,750  83 Linux
/dev/sdb2          81,922,048   976,773,119   894,851,072   7 NTFS / exFAT / HPFS
/dev/sdb3          74,221,568    81,922,047     7,700,480  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16047407104 bytes
255 heads, 63 sectors/track, 1950 cylinders, total 31342592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    31,342,591    31,340,544   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        42A8169FA8169191                       ntfs       
/dev/sda5        5EBA10B4BA108B23                       ntfs       System Reserved
/dev/sdb1        22a3e1f4-e88b-4241-982f-515a316cb4b6   ext4       
/dev/sdb2        1C71747312C05CAC                       ntfs       data
/dev/sdb3        327b9ced-91ac-4219-b96e-5624b9f4091c   swap       
/dev/sdc1        765A-7F48                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/spyros/765A-7F48  vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
else
  search --no-floppy --fs-uuid --set=root 22a3e1f4-e88b-4241-982f-515a316cb4b6
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-22a3e1f4-e88b-4241-982f-515a316cb4b6' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
    else
      search --no-floppy --fs-uuid --set=root 22a3e1f4-e88b-4241-982f-515a316cb4b6
    fi
    linux    /boot/vmlinuz-3.13.0-30-generic root=UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-30-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-22a3e1f4-e88b-4241-982f-515a316cb4b6' {
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-advanced-22a3e1f4-e88b-4241-982f-515a316cb4b6' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        else
          search --no-floppy --fs-uuid --set=root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-recovery-22a3e1f4-e88b-4241-982f-515a316cb4b6' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        else
          search --no-floppy --fs-uuid --set=root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-22a3e1f4-e88b-4241-982f-515a316cb4b6' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        else
          search --no-floppy --fs-uuid --set=root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-22a3e1f4-e88b-4241-982f-515a316cb4b6' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        else
          search --no-floppy --fs-uuid --set=root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-42A8169FA8169191' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  42A8169FA8169191
    else
      search --no-floppy --fs-uuid --set=root 42A8169FA8169191
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda5)' --class windows --class os $menuentry_id_option 'osprober-chain-5EBA10B4BA108B23' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5EBA10B4BA108B23
    else
      search --no-floppy --fs-uuid --set=root 5EBA10B4BA108B23
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=327b9ced-91ac-4219-b96e-5624b9f4091c none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sdb1/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000010  00 00 00 00 00 00 00 00  ff 00 00 74 20 6d 65 74  |...........t met|
00000020  a0 63 4f be 14 7f 00 00  ff ff ff ff ff ff ff ff  |.cO.............|
00000030  08 00 00 00 00 00 00 00  f8 00 01 28 0d 00 00 00  |...........(....|
00000040  00 47 00 b4 14 7f 00 00  00 00 00 00 00 00 00 00  |.G..............|
00000050  07 00 00 00 00 00 00 00  f8 00 02 04 00 00 00 6c  |...............l|
00000060  70 63 4f be 14 7f 00 00  00 00 00 00 00 00 00 00  |pcO.............|
00000070  00 00 00 00 00 00 00 00  ff 00 01 73 75 04 00 00  |...........su...|
00000080  38 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |8...............|
00000090  80 8e 7c 01 00 00 00 00  00 3f 00 b4 14 7f 00 00  |..|......?......|
000000a0  05 00 00 00 0c 01 08 01  10 3d 00 b4 14 7f 00 00  |.........=......|
000000b0  50 3f 00 b4 14 7f 00 00  05 00 00 00 00 54 79 70  |P?...........Typ|
000000c0  38 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |8...............|
000000d0  50 f6 00 b4 14 7f 00 00  f0 f9 00 b4 14 7f 00 00  |P...............|
000000e0  05 00 00 00 00 00 00 00  20 f7 00 b4 14 7f 00 00  |........ .......|
000000f0  50 fa 00 b4 14 7f 00 00  05 00 00 00 6f 66 5f 73  |P...........of_s|
00000100  38 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |8...............|
00000110  80 08 01 b4 14 7f 00 00  e0 1f 01 b4 14 7f 00 00  |................|
00000120  05 00 00 00 00 00 00 00  20 f7 00 b4 14 7f 00 00  |........ .......|
00000130  20 20 01 b4 14 7f 00 00  05 00 00 00 75 09 00 00  |  ..........u...|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000170  40 23 76 01 00 00 00 00  79 75 03 00 00 00 6d 72  |@#v.....yu....mr|
00000180  38 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |8...............|
00000190  c0 fc 00 b4 14 7f 00 00  00 5b 01 b4 14 7f 00 00  |.........[......|
000001a0  05 00 00 00 00 00 00 00  50 f6 00 b4 14 7f 00 00  |........P.......|
000001b0  a0 15 01 b4 14 7f 00 00  05 00 00 00 06 01 00 fe  |................|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 00 a8 04 00 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-w1YHwA84/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-w1YHwA84/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-w1YHwA84/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-w1YHwA84/Tmp_Log: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-07-15__15h31 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in installed-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 ro quiet splash vt.handoff=7

=================== os-prober:
/dev/sdb1:The OS now in use - Ubuntu 14.04 LTS CurrentSession:linux
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Windows 7 (loader):Windows1:chain

=================== blkid:
/dev/sda1: UUID="42A8169FA8169191" TYPE="ntfs"
/dev/sda5: LABEL="System Reserved" UUID="5EBA10B4BA108B23" TYPE="ntfs"
/dev/sdb2: LABEL="data" UUID="1C71747312C05CAC" TYPE="ntfs"
/dev/sdb1: UUID="22a3e1f4-e88b-4241-982f-515a316cb4b6" TYPE="ext4"
/dev/sdb3: UUID="327b9ced-91ac-4219-b96e-5624b9f4091c" TYPE="swap"
/dev/sdc1: UUID="765A-7F48" TYPE="vfat"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 &#921;&#959;&#973;&#955; 15 15:00 grub.d
drwxr-xr-x  2 root root     4096 &#921;&#959;&#973;&#955; 15 14:24 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 &#913;&#960;&#961;  11 13:51 00_header
-rwxr-xr-x 1 root root  6058 &#913;&#960;&#961;  10 18:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 &#913;&#960;&#961;  11 13:51 10_linux
-rwxr-xr-x 1 root root 10412 &#913;&#960;&#961;  11 13:51 20_linux_xen
-rwxr-xr-x 1 root root 11692 &#913;&#960;&#961;  11 13:51 30_os-prober
-rwxr-xr-x 1 root root  1416 &#913;&#960;&#961;  11 13:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 &#913;&#960;&#961;  11 13:51 40_custom
-rwxr-xr-x 1 root root   216 &#913;&#960;&#961;  11 13:51 41_custom
-rw-r--r-- 1 root root   483 &#913;&#960;&#961;  11 13:51 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== No kernel in /media/spyros/765A-7F48/boot:
grub


=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/spyros/765A-7F48.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     liveusb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
1      1049kB  120GB  120GB  primary   ntfs         boot
2      120GB   120GB  156MB  extended               lba
5      120GB   120GB  156MB  logical   ntfs


Model: ATA TOSHIBA MK5076GS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      1049kB  38.0GB  38.0GB  primary  ext4            boot
3      38.0GB  41.9GB  3943MB  primary  linux-swap(v1)
2      41.9GB  500GB   458GB   primary  ntfs


Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  16.0GB  16.0GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA Samsung SSD 840;
1:1049kB:120GB:120GB:ntfs::boot;
2:120GB:120GB:156MB:::lba;
5:120GB:120GB:156MB:ntfs::;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA TOSHIBA MK5076GS;
1:1049kB:38.0GB:38.0GB:ext4::boot;
3:38.0GB:41.9GB:3943MB:linux-swap(v1)::;
2:41.9GB:500GB:458GB:ntfs::;

BYT;
/dev/sdc:16.0GB:scsi:512:512:msdos:Kingston DT 101 G2;
1:1049kB:16.0GB:16.0GB:fat32::boot, lba;


=================== mount:
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=spyros)
/dev/sdc1 on /media/spyros/765A-7F48 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdb2 sdb3 sdc sdc1 sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  bf 97 f4 0d 00 00 00 00  |................|
00000030  00 b8 af 00 00 00 00 00  e1 a5 93 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  91 91 16 a8 9f 16 a8 42  |...............B|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a0 f4 0d  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 a7 04 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  23 8b 10 ba b4 10 ba 5e  |........#......^|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 e2 04  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 56 35 00 00 00 00  |.........WV5....|
00000030  04 00 00 00 00 00 00 00  7f 65 55 03 00 00 00 00  |.........eU.....|
00000040  f6 00 00 00 01 00 00 00  ac 5c c0 12 73 74 71 1c  |...........stq.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200
ls: cannot access /boot/efi/efi: No such file or directory
ls /boot/efi/efi :

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 90 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 38 de 01 b8 3b 00 00  00 00 00 00 02 00 00 00  |.8...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 48 7f 5a 76 4e  4f 20 4e 41 4d 45 20 20  |..)H.ZvNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP....U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 10  70 1f 00 66 ba 00 00 00  |..E}.f..p..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4       35G  5.1G   28G  16% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  2.9G   12K  2.9G   1% /dev
tmpfs          tmpfs     588M  1.3M  587M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.9G  156K  2.9G   1% /run/shm
none           tmpfs     100M   36K  100M   1% /run/user
/dev/sdc1      vfat       15G  991M   14G   7% /media/spyros/765A-7F48
/dev/sda1      fuseblk   112G   92G   20G  83% /mnt/boot-sav/sda1
/dev/sda5      fuseblk   149M   25M  125M  17% /mnt/boot-sav/sda5
/dev/sdb2      fuseblk   427G   97G  331G  23% /mnt/boot-sav/sdb2

=================== fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7965

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234135488   117066720+   7  HPFS/NTFS/exFAT
/dev/sda2       234135489   234440703      152607+   f  W95 Ext'd (LBA)
/dev/sda5       234135552   234440703      152576    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4cac296

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    74220797    37109375   83  Linux
/dev/sdb2        81922048   976773119   447425536    7  HPFS/NTFS/exFAT
/dev/sdb3        74221568    81922047     3850240   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 16.0 GB, 16047407104 bytes
255 heads, 63 sectors/track, 1950 cylinders, total 31342592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2dfd4769

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    31342591    15670272    c  W95 FAT32 (LBA)


User choice: Is sdb (500GB) a removable disk? no
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sdb (500GB) disk!

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.

```

---

### Post by yancek on 2014-07-15
Use the Ubuntu installation medium, open a terminal and run:  blkid, you may need sudo blkid.  Check to see if sdb1 is:  22a3e1f4-e88b-4241-982f-515a316cb4b6

---

### Post by oldfred on 2014-07-15
Please use code tags for long text to preserve formatting & make it easier to review.
You can easily add code tags in Advanced Editor with # icon in edit menu.

I do not like Boot-Repair's auto fix when you have more than one drive. It always installs grub to the MBR of every drive. Best to leave a Windows boot loader in sda, so you can directly boot it. You can use Boot-Repair to add a Windows type boot loader to sda with its advanced mode where you select a system and select which drive to install boot loader.

But you could be an exception. Can you boot from sdb from BIOS? Some with convertible DVD, make a hard drive data only and you cannot boot from that drive. Does BIOS system give an option to boot from drive that is sdb?

Also do not install grub to a partition like sdb1. But it is space on a drive's partition that is not used normally so does not really matter.

---

### Post by sigend on 2014-07-16
Thx for the tip with the code tags!

@[[COLOR=#C61919]oldfred[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")

I have the option to boot from cd/DVD , where HDD is now installed, but then nothing happens.Again rescue mode.


@[[COLOR=#000000]yancek[/COLOR]]("http://ubuntuforums.org/member.php?u=1928724")[COLOR=#000000] 

[/COLOR]Yes,sdb1 is that device!

I attach below the new export from boot-repair.
I belive what will solve the problem is to make Grub on sdb1 look for the .img at the sector 1 of the second HDD.
Because now "Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the **same hard drive [COLOR=#AA22FF]for [/COLOR]core.img**. core.img is at this location and looks 
    in partition 112 [COLOR=#AA22FF]**for**[/COLOR] ."
But i dont know if that will work for sure and also dont know how to do it!

Thx again for your help! :)



```

Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 23Dec2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 112 [COLOR=#AA22FF]**for**[/COLOR] .
 [COLOR=#666666]=[/COLOR]> Grub Legacy [COLOR=#666666]([/COLOR]v0.97[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition [COLOR=#008800]*#1 for /boot/grub/stage2 and /boot/grub/menu.lst.*[/COLOR]

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR]
    Boot sector info:  Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR] is installed in the boot sector of 
                       sdb1 and looks at sector 59566424 of the same hard 
                       drive [COLOR=#AA22FF]**for **[/COLOR]core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf 
                       /boot/grub/i386-pc/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,048   234,135,488   234,133,441   7 NTFS / exFAT / HPFS
/dev/sda2         234,135,489   234,440,703       305,215   f W95 Extended [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]
/dev/sda5         234,135,552   234,440,703       305,152   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1    *          2,048    74,220,797    74,218,750  83 Linux
/dev/sdb2          81,922,048   976,773,119   894,851,072   7 NTFS / exFAT / HPFS
/dev/sdb3          74,221,568    81,922,047     7,700,480  82 Linux swap / Solaris


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        42A8169FA8169191                       ntfs       
/dev/sda5        5EBA10B4BA108B23                       ntfs       System Reserved
/dev/sdb1        22a3e1f4-e88b-4241-982f-515a316cb4b6   ext4       
/dev/sdb2        1C71747312C05CAC                       ntfs       data
/dev/sdb3        327b9ced-91ac-4219-b96e-5624b9f4091c   [COLOR=#B8860B]swap[/COLOR]       

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sdb1/boot/grub/menu.lst: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# menu.lst - See: grub(8), info grub, update-grub(8)*[/COLOR]
[COLOR=#008800]*#            grub-install(8), grub-floppy(8),*[/COLOR]
[COLOR=#008800]*#            grub-md5-crypt, /usr/share/doc/grub*[/COLOR]
[COLOR=#008800]*#            and /usr/share/doc/grub-legacy-doc/.*[/COLOR]

[COLOR=#008800]*## default num*[/COLOR]
[COLOR=#008800]*# Set the default entry to the entry number NUM. Numbering starts from 0, and*[/COLOR]
[COLOR=#008800]*# the entry number 0 is the default if the command is not used.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# You can specify 'saved' instead of a number. In this case, the default entry*[/COLOR]
[COLOR=#008800]*# is the entry saved with the command 'savedefault'.*[/COLOR]
[COLOR=#008800]*# WARNING: If you are using dmraid do not use 'savedefault' or your*[/COLOR]
[COLOR=#008800]*# array will desync and will not let you boot your system.*[/COLOR]
default        0

[COLOR=#008800]*## timeout sec*[/COLOR]
[COLOR=#008800]*# Set a timeout, in SEC seconds, before automatically booting the default entry*[/COLOR]
[COLOR=#008800]*# (normally the first entry defined).*[/COLOR]
timeout        3

[COLOR=#008800]*## hiddenmenu*[/COLOR]
[COLOR=#008800]*# Hides the menu by default (press ESC to see the menu)*[/COLOR]
hiddenmenu

[COLOR=#008800]*# Pretty colours*[/COLOR]
[COLOR=#008800]*#color cyan/blue white/blue*[/COLOR]

[COLOR=#008800]*## password ['--md5'] passwd*[/COLOR]
[COLOR=#008800]*# If used in the first section of a menu file, disable all interactive editing*[/COLOR]
[COLOR=#008800]*# control (menu entry editor and command-line)  and entries protected by the*[/COLOR]
[COLOR=#008800]*# command 'lock'*[/COLOR]
[COLOR=#008800]*# e.g. password topsecret*[/COLOR]
[COLOR=#008800]*#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/*[/COLOR]
[COLOR=#008800]*# password topsecret*[/COLOR]

[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# examples*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# title        Windows 95/98/NT/2000*[/COLOR]
[COLOR=#008800]*# root        (hd0,0)*[/COLOR]
[COLOR=#008800]*# makeactive*[/COLOR]
[COLOR=#008800]*# chainloader    +1*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# title        Linux*[/COLOR]
[COLOR=#008800]*# root        (hd0,1)*[/COLOR]
[COLOR=#008800]*# kernel    /vmlinuz root=/dev/hda2 ro*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST*[/COLOR]

[COLOR=#008800]*### BEGIN AUTOMAGIC KERNELS LIST*[/COLOR]
[COLOR=#008800]*## lines between the AUTOMAGIC KERNELS LIST markers will be modified*[/COLOR]
[COLOR=#008800]*## by the debian update-grub script except for the default options below*[/COLOR]

[COLOR=#008800]*## DO NOT UNCOMMENT THEM, Just edit them to your needs*[/COLOR]

[COLOR=#008800]*## ## Start Default Options ##*[/COLOR]
[COLOR=#008800]*## default kernel options*[/COLOR]
[COLOR=#008800]*## default kernel options for automagic boot options*[/COLOR]
[COLOR=#008800]*## If you want special options for specific kernels use kopt_x_y_z*[/COLOR]
[COLOR=#008800]*## where x.y.z is kernel version. Minor versions can be omitted.*[/COLOR]
[COLOR=#008800]*## e.g. kopt=root=/dev/hda1 ro*[/COLOR]
[COLOR=#008800]*##      kopt_2_6_8=root=/dev/hdc1 ro*[/COLOR]
[COLOR=#008800]*##      kopt_2_6_8_2_686=root=/dev/hdc2 ro*[/COLOR]
[COLOR=#008800]*# kopt=root=UUID=22a3e1f4-e88b-4241-982f-515a316cb4b6 ro*[/COLOR]

[COLOR=#008800]*## default grub root device*[/COLOR]
[COLOR=#008800]*## e.g. groot=(hd0,0)*[/COLOR]
[COLOR=#008800]*# groot=22a3e1f4-e88b-4241-982f-515a316cb4b6*[/COLOR]

[COLOR=#008800]*## should update-grub create alternative automagic boot options*[/COLOR]
[COLOR=#008800]*## e.g. alternative=true*[/COLOR]
[COLOR=#008800]*##      alternative=false*[/COLOR]
[COLOR=#008800]*# alternative=true*[/COLOR]

[COLOR=#008800]*## should update-grub lock alternative automagic boot options*[/COLOR]
[COLOR=#008800]*## e.g. lockalternative=true*[/COLOR]
[COLOR=#008800]*##      lockalternative=false*[/COLOR]
[COLOR=#008800]*# lockalternative=false*[/COLOR]

[COLOR=#008800]*## additional options to use with the default boot option, but not with the*[/COLOR]
[COLOR=#008800]*## alternatives*[/COLOR]
[COLOR=#008800]*## e.g. defoptions=vga=791 resume=/dev/hda5*[/COLOR]
[COLOR=#008800]*# defoptions=quiet splash*[/COLOR]

[COLOR=#008800]*## should update-grub lock old automagic boot options*[/COLOR]
[COLOR=#008800]*## e.g. lockold=false*[/COLOR]
[COLOR=#008800]*##      lockold=true*[/COLOR]
[COLOR=#008800]*# lockold=false*[/COLOR]

[COLOR=#008800]*## Xen hypervisor options to use with the default Xen boot option*[/COLOR]
[COLOR=#008800]*# xenhopt=*[/COLOR]

[COLOR=#008800]*## Xen Linux kernel options to use with the default Xen boot option*[/COLOR]
[COLOR=#008800]*# xenkopt=console=tty0*[/COLOR]

[COLOR=#008800]*## altoption boot targets option*[/COLOR]
[COLOR=#008800]*## multiple altoptions lines are allowed*[/COLOR]
[COLOR=#008800]*## e.g. altoptions=(extra menu suffix) extra boot options*[/COLOR]
[COLOR=#008800]*##      altoptions=(recovery) single*[/COLOR]
[COLOR=#008800]*# altoptions=(recovery mode) single*[/COLOR]

[COLOR=#008800]*## controls how many kernels should be put into the menu.lst*[/COLOR]
[COLOR=#008800]*## only counts the first occurence of a kernel, not the*[/COLOR]
[COLOR=#008800]*## alternative kernel options*[/COLOR]
[COLOR=#008800]*## e.g. howmany=all*[/COLOR]
[COLOR=#008800]*##      howmany=7*[/COLOR]
[COLOR=#008800]*# howmany=all*[/COLOR]

[COLOR=#008800]*## specify if running in Xen domU or have grub detect automatically*[/COLOR]
[COLOR=#008800]*## update-grub will ignore non-xen kernels when running in domU and vice versa*[/COLOR]
[COLOR=#008800]*## e.g. indomU=detect*[/COLOR]
[COLOR=#008800]*##      indomU=true*[/COLOR]
[COLOR=#008800]*##      indomU=false*[/COLOR]
[COLOR=#008800]*# indomU=detect*[/COLOR]

[COLOR=#008800]*## should update-grub create memtest86 boot option*[/COLOR]
[COLOR=#008800]*## e.g. memtest86=true*[/COLOR]
[COLOR=#008800]*##      memtest86=false*[/COLOR]
[COLOR=#008800]*# memtest86=true*[/COLOR]

[COLOR=#008800]*## should update-grub adjust the value of the default booted system*[/COLOR]
[COLOR=#008800]*## can be true or false*[/COLOR]
[COLOR=#008800]*# updatedefaultentry=false*[/COLOR]

[COLOR=#008800]*## should update-grub add savedefault to the default options*[/COLOR]
[COLOR=#008800]*## can be true or false*[/COLOR]
[COLOR=#008800]*# savedefault=false*[/COLOR]

[COLOR=#008800]*## ## End Default Options ##*[/COLOR]

title        Ubuntu 14.04 LTS, kernel 3.13.0-30-generic
uuid        22a3e1f4-e88b-4241-982f-515a316cb4b6
kernel        /boot/vmlinuz-3.13.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro quiet splash 
initrd        /boot/initrd.img-3.13.0-30-generic
quiet

title        Ubuntu 14.04 LTS, kernel 3.13.0-30-generic [COLOR=#666666]([/COLOR]recovery mode[COLOR=#666666])[/COLOR]
uuid        22a3e1f4-e88b-4241-982f-515a316cb4b6
kernel        /boot/vmlinuz-3.13.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  single
initrd        /boot/initrd.img-3.13.0-30-generic

title        Ubuntu 14.04 LTS, kernel 3.13.0-24-generic
uuid        22a3e1f4-e88b-4241-982f-515a316cb4b6
kernel        /boot/vmlinuz-3.13.0-24-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro quiet splash 
initrd        /boot/initrd.img-3.13.0-24-generic
quiet

title        Ubuntu 14.04 LTS, kernel 3.13.0-24-generic [COLOR=#666666]([/COLOR]recovery mode[COLOR=#666666])[/COLOR]
uuid        22a3e1f4-e88b-4241-982f-515a316cb4b6
kernel        /boot/vmlinuz-3.13.0-24-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  single
initrd        /boot/initrd.img-3.13.0-24-generic

title        Ubuntu 14.04 LTS, memtest86+
uuid        22a3e1f4-e88b-4241-982f-515a316cb4b6
kernel        /boot/memtest86+.bin
quiet

[COLOR=#008800]*### END DEBIAN AUTOMAGIC KERNELS LIST*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===========================[/COLOR] sdb1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${next_entry}"[/COLOR] [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${next_entry}"[/COLOR]
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]next_entry[/COLOR][COLOR=#666666]=[/COLOR]
   save_env next_entry
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#BB4444]"${feature_menuentry_id}"[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"--id"[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]export [/COLOR]menuentry_id_option

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -n [COLOR=#BB4444]"${have_grubenv}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]save_env recordfail; [COLOR=#AA22FF]**fi**[/COLOR]; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_all_video_module[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
insmod all_video
  [COLOR=#AA22FF]**else**[/COLOR]
insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_default_font_path[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR]unicode
[COLOR=#AA22FF]**else**[/COLOR]
insmod part_msdos
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos1'[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
[COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 22a3e1f4-e88b-4241-982f-515a316cb4b6
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"/usr/share/grub/unicode.pf2"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if **[/COLOR]loadfont [COLOR=#B8860B]$font[/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
  load_video
  insmod gfxterm
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]$prefix[/COLOR]/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]en_US
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_timeout_style[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]menu
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#008800]*# Fallback normal timeout code in case the timeout_style feature is*[/COLOR]
  [COLOR=#008800]*# unavailable.*[/COLOR]
  [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/00_header ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/05_debian_theme ###*[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray
[COLOR=#AA22FF]**if **[/COLOR]background_color 44,0,30; [COLOR=#AA22FF]**then**[/COLOR]
clear
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/05_debian_theme ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/10_linux ###*[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]gfxmode [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${1}"[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${1}"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
menuentry [COLOR=#BB4444]'Ubuntu'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-simple-22a3e1f4-e88b-4241-982f-515a316cb4b6'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
    load_video
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos1'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 22a3e1f4-e88b-4241-982f-515a316cb4b6
    [COLOR=#AA22FF]**fi**[/COLOR]
linux    /boot/vmlinuz-3.13.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.13.0-30-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]'Advanced options for Ubuntu'[/COLOR] [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-advanced-22a3e1f4-e88b-4241-982f-515a316cb4b6'[/COLOR] [COLOR=#666666]{[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-30-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-30-generic-advanced-22a3e1f4-e88b-4241-982f-515a316cb4b6'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos1'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.13.0-30-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.13.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.13.0-30-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-30-generic-recovery-22a3e1f4-e88b-4241-982f-515a316cb4b6'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos1'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.13.0-30-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.13.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.13.0-30-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-24-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-24-generic-advanced-22a3e1f4-e88b-4241-982f-515a316cb4b6'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos1'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.13.0-24-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.13.0-24-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro  quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.13.0-24-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-24-generic-recovery-22a3e1f4-e88b-4241-982f-515a316cb4b6'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos1'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci1,msdos1  22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 22a3e1f4-e88b-4241-982f-515a316cb4b6
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.13.0-24-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.13.0-24-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.13.0-24-generic
    [COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
menuentry [COLOR=#BB4444]'Windows 7 (loader) (on /dev/sda1)'[/COLOR] --class windows --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'osprober-chain-42A8169FA8169191'[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ntfs
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  42A8169FA8169191
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 42A8169FA8169191
    [COLOR=#AA22FF]**fi**[/COLOR]
parttool [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR] hidden-
    chainloader +1
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Windows 7 (loader) (on /dev/sda5)'[/COLOR] --class windows --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'osprober-chain-5EBA10B4BA108B23'[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ntfs
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos5'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos5 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos5 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos5  5EBA10B4BA108B23
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 5EBA10B4BA108B23
    [COLOR=#AA22FF]**fi**[/COLOR]
parttool [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR] hidden-
    chainloader +1
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]menu
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${timeout}"[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_uefi-firmware ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg
[COLOR=#AA22FF]**elif**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${config_directory}"[/COLOR] -a -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sdb1/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/sdb1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# swap was on /dev/sdb3 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]327b9ced-91ac-4219-b96e-5624b9f4091c none            swap    sw              0       0
--------------------------------------------------------------------------------

[COLOR=#666666]======================[/COLOR] sdb1/boot/extlinux/extlinux.conf: [COLOR=#666666]=======================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*## /boot/extlinux/extlinux.conf*[/COLOR]
[COLOR=#008800]*##*[/COLOR]
[COLOR=#008800]*## IMPORTANT WARNING*[/COLOR]
[COLOR=#008800]*##*[/COLOR]
[COLOR=#008800]*## The configuration of this file is generated automatically.*[/COLOR]
[COLOR=#008800]*## Do not edit this file manually, use: extlinux-update*[/COLOR]


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sdb1: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]=================[/COLOR] sdb1: Location of files loaded by Syslinux: [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]==============[/COLOR] sdb1: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by Syslinux: [COLOR=#666666]===============[/COLOR]

 boot/extlinux/chain.c32            :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sda2

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000010  00 00 00 00 00 00 00 00  ff 00 00 74 20 6d 65 74  |...........t met|
00000020  a0 63 4f be 14 7f 00 00  ff ff ff ff ff ff ff ff  |.cO.............|
00000030  08 00 00 00 00 00 00 00  f8 00 01 28 0d 00 00 00  |...........[COLOR=#666666]([/COLOR]....|
00000040  00 47 00 b4 14 7f 00 00  00 00 00 00 00 00 00 00  |.G..............|
00000050  07 00 00 00 00 00 00 00  f8 00 02 04 00 00 00 6c  |...............l|
00000060  70 63 4f be 14 7f 00 00  00 00 00 00 00 00 00 00  |pcO.............|
00000070  00 00 00 00 00 00 00 00  ff 00 01 73 75 04 00 00  |...........su...|
00000080  38 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |8...............|
00000090  80 8e 7c 01 00 00 00 00  00 3f 00 b4 14 7f 00 00  |..|......?......|
000000a0  05 00 00 00 0c 01 08 01  10 3d 00 b4 14 7f 00 00  |.........[COLOR=#666666]=[/COLOR]......|
000000b0  50 3f 00 b4 14 7f 00 00  05 00 00 00 00 54 79 70  |P?...........Typ|
000000c0  38 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |8...............|
000000d0  50 f6 00 b4 14 7f 00 00  f0 f9 00 b4 14 7f 00 00  |P...............|
000000e0  05 00 00 00 00 00 00 00  20 f7 00 b4 14 7f 00 00  |........ .......|
000000f0  50 fa 00 b4 14 7f 00 00  05 00 00 00 6f 66 5f 73  |P...........of_s|
00000100  38 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |8...............|
00000110  80 08 01 b4 14 7f 00 00  e0 1f 01 b4 14 7f 00 00  |................|
00000120  05 00 00 00 00 00 00 00  20 f7 00 b4 14 7f 00 00  |........ .......|
00000130  20 20 01 b4 14 7f 00 00  05 00 00 00 75 09 00 00  |  ..........u...|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000170  40 23 76 01 00 00 00 00  79 75 03 00 00 00 6d 72  |@#v.....yu....mr|
00000180  38 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |8...............|
00000190  c0 [COLOR=#AA22FF]fc [/COLOR]00 b4 14 7f 00 00  00 5b 01 b4 14 7f 00 00  |.........[COLOR=#666666][[/COLOR]......|
000001a0  05 00 00 00 00 00 00 00  50 f6 00 b4 14 7f 00 00  |........P.......|
000001b0  a0 15 01 b4 14 7f 00 00  05 00 00 00 06 01 00 fe  |................|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 00 a8 04 00 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]


[COLOR=#666666]===============================[/COLOR] StdErr Messages: [COLOR=#666666]===============================[/COLOR]

cat: write error: Broken pipe
cat: /tmp/BootInfo-TleBzjOa/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-TleBzjOa/Tmp_Log: No such file or directory

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2014-07-16__13h05 [COLOR=#666666]===================[/COLOR]
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in installed-session [COLOR=#666666]([/COLOR]Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64[COLOR=#666666])[/COLOR]
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]BOOT_IMAGE[/COLOR][COLOR=#666666]=[/COLOR]/boot/vmlinuz-3.13.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]22a3e1f4-e88b-4241-982f-515a316cb4b6 ro quiet splash vt.handoff[COLOR=#666666]=[/COLOR][COLOR=#B8860B]7[/COLOR]

[COLOR=#666666]===================[/COLOR] os-prober:
/dev/sdb1:The OS now in use - Ubuntu 14.04 LTS CurrentSession:linux
/dev/sda1:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows:chain
/dev/sda5:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows1:chain

[COLOR=#666666]===================[/COLOR] blkid:
/dev/sda1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"42A8169FA8169191"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda5: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"System Reserved"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"5EBA10B4BA108B23"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sdb1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"22a3e1f4-e88b-4241-982f-515a316cb4b6"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext4"[/COLOR]
/dev/sdb2: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"data"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"1C71747312C05CAC"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sdb3: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"327b9ced-91ac-4219-b96e-5624b9f4091c"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

[COLOR=#666666]===================[/COLOR] /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 &#921;&#959;&#973;&#955; 15 15:00 grub.d
drwxr-xr-x  2 root root     4096 &#921;&#959;&#973;&#955; 15 14:24 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 &#913;&#960;&#961;  11 13:51 00_header
-rwxr-xr-x 1 root root  6058 &#913;&#960;&#961;  10 18:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 &#913;&#960;&#961;  11 13:51 10_linux
-rwxr-xr-x 1 root root 10412 &#913;&#960;&#961;  11 13:51 20_linux_xen
-rwxr-xr-x 1 root root 11692 &#913;&#960;&#961;  11 13:51 30_os-prober
-rwxr-xr-x 1 root root  1416 &#913;&#960;&#961;  11 13:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 &#913;&#960;&#961;  11 13:51 40_custom
-rwxr-xr-x 1 root root   216 &#913;&#960;&#961;  11 13:51 41_custom
-rw-r--r-- 1 root root   483 &#913;&#960;&#961;  11 13:51 [COLOR=#B8860B]README[/COLOR]




[COLOR=#666666]===================[/COLOR] /etc/default/grub :

[COLOR=#008800]*# If you change this file, run 'update-grub' afterwards to update*[/COLOR]
[COLOR=#008800]*# /boot/grub/grub.cfg.*[/COLOR]
[COLOR=#008800]*# For full documentation of the options in this file, see:*[/COLOR]
[COLOR=#008800]*#   info -f grub -n 'Simple configuration'*[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#008800]*#GRUB_HIDDEN_TIMEOUT=0*[/COLOR]
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT_QUIET[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s 2> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo [/COLOR]Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#008800]*# Uncomment to enable BadRAM filtering, modify to suit your needs*[/COLOR]
[COLOR=#008800]*# This works with Linux (no patch required) and with any kernel that obtains*[/COLOR]
[COLOR=#008800]*# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)*[/COLOR]
[COLOR=#008800]*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*[/COLOR]

[COLOR=#008800]*# Uncomment to disable graphical terminal (grub-pc only)*[/COLOR]
[COLOR=#008800]*#GRUB_TERMINAL=console*[/COLOR]

[COLOR=#008800]*# The resolution used on graphical terminal*[/COLOR]
[COLOR=#008800]*# note that you can use only modes which your graphic card supports via VBE*[/COLOR]
[COLOR=#008800]*# you can see them in real GRUB with the command `vbeinfo'*[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]



[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub1 grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA Samsung SSD 840 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 120GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
1      1049kB  120GB  120GB  primary   ntfs         boot
2      120GB   120GB  156MB  extended               lba
5      120GB   120GB  156MB  logical   ntfs


Model: ATA TOSHIBA MK5076GS [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 500GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      1049kB  38.0GB  38.0GB  primary  ext4            boot
3      38.0GB  41.9GB  3943MB  primary  linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]
2      41.9GB  500GB   458GB   primary  [COLOR=#B8860B]ntfs[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA Samsung SSD 840;
1:1049kB:120GB:120GB:ntfs::boot;
2:120GB:120GB:156MB:::lba;
5:120GB:120GB:156MB:ntfs::;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA TOSHIBA MK5076GS;
1:1049kB:38.0GB:38.0GB:ext4::boot;
3:38.0GB:41.9GB:3943MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
2:41.9GB:500GB:458GB:ntfs::;


[COLOR=#666666]===================[/COLOR] mount:
/dev/sdb1 on / [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/user [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]104857600,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /sys/fs/pstore [COLOR=#AA22FF]type [/COLOR]pstore [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
systemd on /sys/fs/cgroup/systemd [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,none,name[COLOR=#666666]=[/COLOR]systemd[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/1000/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]spyros[COLOR=#666666])[/COLOR]
/dev/sda1 on /mnt/boot-sav/sda1 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda5 on /mnt/boot-sav/sda5 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sdb2 on /mnt/boot-sav/sdb2 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdb2 sdb3 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  bf 97 f4 0d 00 00 00 00  |................|
00000030  00 b8 af 00 00 00 00 00  e1 a5 93 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  91 91 16 a8 9f 16 a8 42  |...............B|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk [COLOR=#AA22FF]read [/COLOR]error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a0 f4 0d  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 a7 04 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  23 8b 10 ba b4 10 ba 5e  |........#......^|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk [COLOR=#AA22FF]read [/COLOR]error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sdb2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 e2 04  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 56 35 00 00 00 00  |.........WV5....|
00000030  04 00 00 00 00 00 00 00  7f 65 55 03 00 00 00 00  |.........eU.....|
00000040  f6 00 00 00 01 00 00 00  ac 5c c0 12 73 74 71 1c  |...........stq.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f[COLOR=#BB4444]`[/COLOR]..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66 59 5b 5a  |.B..........fY[COLOR=#666666][[/COLOR]Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk [COLOR=#AA22FF]read [/COLOR]er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4       35G  5.9G   28G  18% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  2.9G   12K  2.9G   1% /dev
tmpfs          tmpfs     588M  1.2M  587M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.9G   13M  2.9G   1% /run/shm
none           tmpfs     100M   32K  100M   1% /run/user
/dev/sda1      fuseblk   112G   93G   20G  83% /mnt/boot-sav/sda1
/dev/sda5      fuseblk   149M   25M  125M  17% /mnt/boot-sav/sda5
/dev/sdb2      fuseblk   427G   97G  331G  23% /mnt/boot-sav/sdb2

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x000b7965

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234135488   117066720+   7  HPFS/NTFS/exFAT
/dev/sda2       234135489   234440703      152607+   f  W95 Ext[COLOR=#BB4444]'d (LBA)[/COLOR]
[COLOR=#BB4444]/dev/sda5       234135552   234440703      152576    7  HPFS/NTFS/exFAT[/COLOR]

[COLOR=#BB4444]Disk /dev/sdb: 500.1 GB, 500107862016 bytes[/COLOR]
[COLOR=#BB4444]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors[/COLOR]
[COLOR=#BB4444]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]Disk identifier: 0xf4cac296[/COLOR]

[COLOR=#BB4444]Device Boot      Start         End      Blocks   Id  System[/COLOR]
[COLOR=#BB4444]/dev/sdb1   *        2048    74220797    37109375   83  Linux[/COLOR]
[COLOR=#BB4444]/dev/sdb2        81922048   976773119   447425536    7  HPFS/NTFS/exFAT[/COLOR]
[COLOR=#BB4444]/dev/sdb3        74221568    81922047     3850240   82  Linux swap / Solaris[/COLOR]

[COLOR=#BB4444]Partition table entries are not in disk order[/COLOR]


[COLOR=#BB4444]User choice: Is sdb (500GB) a removable disk? no[/COLOR]

[COLOR=#BB4444]=================== Default settings[/COLOR]
[COLOR=#BB4444]Recommended-Repair[/COLOR]
[COLOR=#BB4444]This setting would reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).[/COLOR]
[COLOR=#BB4444]Additional repair would be performed: unhide-bootmenu-10s[/COLOR]

[COLOR=#BB4444]=================== Settings chosen by the user[/COLOR]
[COLOR=#BB4444]Custom-Repair[/COLOR]
[COLOR=#BB4444]This setting will reinstall the grub2 of sdb1 into the MBR of sdb.[/COLOR]
[COLOR=#BB4444]Additional repair will be performed: unhide-bootmenu-10s[/COLOR]



[COLOR=#BB4444]*******lspci -nnk | grep -iA3 vga[/COLOR]
[COLOR=#BB4444]00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)[/COLOR]
[COLOR=#BB4444]Subsystem: Dell Device [1028:04ca][/COLOR]
[COLOR=#BB4444]Kernel driver in use: i915[/COLOR]
[COLOR=#BB4444]00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)[/COLOR]
[COLOR=#BB4444]--[/COLOR]
[COLOR=#BB4444]01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (rev ff)[/COLOR]
[COLOR=#BB4444]Kernel driver in use: radeon[/COLOR]
[COLOR=#BB4444]05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)[/COLOR]
[COLOR=#BB4444]Subsystem: Dell Device [1028:04b0][/COLOR]
[COLOR=#BB4444]*******[/COLOR]

[COLOR=#BB4444]grub-install (GNU GRUB 0.97),grub-install (GNU GRUB 0.[/COLOR]
[COLOR=#BB4444]Wrong GRUB version detected. Please report this message to boot.repair@gmail.com[/COLOR]

[COLOR=#BB4444]Reinstall the GRUB of sdb1 into the MBR of sdb[/COLOR]
[COLOR=#BB4444]Probing devices to guess BIOS drives. This may take a long time.[/COLOR]
[COLOR=#BB4444]Searching for GRUB installation directory ... found: /boot/grub[/COLOR]
[COLOR=#BB4444]grub-install /dev/sdb: Installing GRUB to /dev/sdb as (hd1)...[/COLOR]
[COLOR=#BB4444]Installation finished. No error reported.[/COLOR]
[COLOR=#BB4444]This is the contents of the device map /boot/grub/device.map.[/COLOR]
[COLOR=#BB4444]Check if this is correct or not. If any of the lines is incorrect,[/COLOR]
[COLOR=#BB4444]fix it and re-run the script `grub-install'[/COLOR].

[COLOR=#666666]([/COLOR]fd0[COLOR=#666666])[/COLOR]    /dev/fd0
[COLOR=#666666]([/COLOR]hd0[COLOR=#666666])[/COLOR]    /dev/sda
[COLOR=#666666]([/COLOR]hd1[COLOR=#666666])[/COLOR]    /dev/sdb
[COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sdb:0
Probing devices to guess BIOS drives. This may take a long time.
Searching [COLOR=#AA22FF]**for **[/COLOR]GRUB installation directory ... found: /boot/grub
grub-install --recheck /dev/sdb: Installing GRUB to /dev/sdb as [COLOR=#666666]([/COLOR]hd1[COLOR=#666666])[/COLOR]...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check [COLOR=#AA22FF]**if **[/COLOR]this is correct or not. If any of the lines is incorrect,
fix it and re-run the script [COLOR=#BB4444]`[/COLOR]grub-install'.

[COLOR=#666666]([/COLOR]fd0[COLOR=#666666])[/COLOR]    /dev/fd0
[COLOR=#666666]([/COLOR]hd0[COLOR=#666666])[/COLOR]    /dev/sda
[COLOR=#666666]([/COLOR]hd1[COLOR=#666666])[/COLOR]    /dev/sdb
[COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sdb:0

update-grub -y
debconf: unable to initialize frontend: Dialog
debconf: [COLOR=#666666]([/COLOR]Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.[COLOR=#666666])[/COLOR]
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: [COLOR=#666666]([/COLOR]This frontend requires a controlling tty.[COLOR=#666666])[/COLOR]
debconf: falling back to frontend: Teletype
Searching [COLOR=#AA22FF]**for **[/COLOR]GRUB installation directory ... found: /boot/grub
Searching [COLOR=#AA22FF]**for **[/COLOR]default file ... found: /boot/grub/default
Testing [COLOR=#AA22FF]**for **[/COLOR]an existing GRUB menu.lst file ...

Could not find /boot/grub/menu.lst file.
Generating /boot/grub/menu.lst
Searching [COLOR=#AA22FF]**for **[/COLOR]splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-3.13.0-30-generic
Found kernel: /boot/vmlinuz-3.13.0-24-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... [COLOR=#AA22FF]**done**[/COLOR]


An error occurred during the repair.

You can now reboot your computer.
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sdb [COLOR=#666666]([/COLOR]500GB[COLOR=#666666])[/COLOR] disk!
```

---

### Post by yancek on 2014-07-16
Go to the site below which offers several methods of trying to repair the bootloader on Ubuntu.  The boot repair may work, if not you can try from the Live CD.  The surest method is the chroot option which unfortunately, is also the most complicated for a new user.  Read carefully.

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by oldfred on 2014-07-16
You would have to have a second hard drive boot entry in the choices of drives to boot to be able to directly boot hard drive. My flash drives in USB ports are seen as another hard drive boot item.

If reinstall of grub to sda does not work to boot sdb, then you may have to create a /boot partition on sda of about 300MB (if you clean it periodically) and then you will boot from sda, but rest of system then should work from sdb.

---

