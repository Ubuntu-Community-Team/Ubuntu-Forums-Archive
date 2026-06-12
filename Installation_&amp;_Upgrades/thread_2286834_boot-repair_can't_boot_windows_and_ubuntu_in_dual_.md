---
title: "boot-repair can't boot windows and ubuntu in dual boot here is boot summary"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by yogesh8 on 2015-07-14
[http://paste.ubuntu.com/11880698/](http://paste.ubuntu.com/11880698/)

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda6 
                       and looks at sector 1046957696 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub.
    Operating System:  Ubuntu 14.04.2 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf 
                       /boot/grub/i386-pc/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 1357274 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2    *        409,600   526,487,551   526,077,952   7 NTFS / exFAT / HPFS
/dev/sda3         526,489,598 1,205,286,911   678,797,314   f W95 Extended (LBA)
/dev/sda5         526,489,600   945,919,999   419,430,400   7 NTFS / exFAT / HPFS
/dev/sda6         945,922,048 1,205,286,911   259,364,864  83 Linux
/dev/sda4       1,205,286,912 1,250,050,047    44,763,136   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,266,815    31,266,784   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        703047243046F120                       ntfs       SYSTEM
/dev/sda2        96AC216DAC2148D7                       ntfs       
/dev/sda4        8C9E88AD9E8890FE                       ntfs       Recovery
/dev/sda5        A68C004E8C001C05                       ntfs       New Volume
/dev/sda6        a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0   ext4       
/dev/sdb1        F97E-8233                              vfat       
/dev/zram0       2bb4f806-6784-4159-a1c4-bdcceb971822   swap       
/dev/zram1       9cc7860d-8076-4f98-8828-d767f492a83c   swap       
/dev/zram2       a85a2766-fde3-458f-be93-1c330746828c   swap       
/dev/zram3       ee7b5414-3176-4d46-8175-d27e40dd1e6a   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 15 02:50 ata-Hitachi_HTS547564A9E384_J2180053DTX4LC -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 15 02:51 ata-Hitachi_HTS547564A9E384_J2180053DTX4LC-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 15 02:51 ata-Hitachi_HTS547564A9E384_J2180053DTX4LC-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 15 02:44 ata-Hitachi_HTS547564A9E384_J2180053DTX4LC-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul 15 02:51 ata-Hitachi_HTS547564A9E384_J2180053DTX4LC-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jul 15 02:51 ata-Hitachi_HTS547564A9E384_J2180053DTX4LC-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jul 15 02:44 ata-Hitachi_HTS547564A9E384_J2180053DTX4LC-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Jul 15 02:44 ata-hp_DVD_RW_AD-7760H_1013650L111 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 15 02:50 usb-SanDisk_Cruzer_Force_4C530008940513122563-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 15 02:44 usb-SanDisk_Cruzer_Force_4C530008940513122563-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jul 15 02:50 wwn-0x5000cca63ed96a13 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 15 02:51 wwn-0x5000cca63ed96a13-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 15 02:51 wwn-0x5000cca63ed96a13-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 15 02:44 wwn-0x5000cca63ed96a13-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul 15 02:51 wwn-0x5000cca63ed96a13-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jul 15 02:51 wwn-0x5000cca63ed96a13-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jul 15 02:44 wwn-0x5000cca63ed96a13-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
else
  search --no-floppy --fs-uuid --set=root a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
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
  set timeout=10
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
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
    else
      search --no-floppy --fs-uuid --set=root a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
    fi
    linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-30-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0' {
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        else
          search --no-floppy --fs-uuid --set=root a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        else
          search --no-floppy --fs-uuid --set=root a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-advanced-a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        else
          search --no-floppy --fs-uuid --set=root a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /boot/vmlinuz-3.13.0-57-generic root=UUID=a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-recovery-a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        else
          search --no-floppy --fs-uuid --set=root a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /boot/vmlinuz-3.13.0-57-generic root=UUID=a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-57-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

====================== sda6/boot/extlinux/extlinux.conf: =======================

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

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sdb1/boot/grub/grub.cfg: ===========================

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

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^64bit session (failsafe)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  e6 8d e2 5b fb 28 cc 20  25 74 0e 58 9f 9a 86 43  |...[.(. %t.X...C|
00000010  76 32 02 60 77 b1 b0 c5  b7 4e db ea 93 08 1f 75  |v2.`w....N.....u|
00000020  d1 d1 bf ab d4 94 9c da  a9 11 35 46 46 11 4e 3d  |..........5FF.N=|
00000030  d7 5c e0 81 41 eb 61 68  df cd 77 bc d8 ee c0 10  |.\..A.ah..w.....|
00000040  78 6a 3c e9 ab 20 5f 44  4b d3 52 c4 22 ee 28 07  |xj<.. _DK.R.".(.|
00000050  cc 77 5a cc a4 c0 91 5b  fe 53 8d 7c b4 da 9b 26  |.wZ....[.S.|...&|
00000060  b9 6b de ca 15 bf df cb  a4 3c 95 c0 80 f2 8b 68  |.k.......<.....h|
00000070  af 4f f6 e5 63 7a 13 ee  70 72 e6 a1 ab aa 5a e7  |.O..cz..pr....Z.|
00000080  ee c2 84 f2 64 84 63 eb  22 95 99 aa 0f 16 e8 90  |....d.c.".......|
00000090  ba 77 bb e1 38 8e 85 f9  ec 24 ed 2d 63 29 ca 5e  |.w..8....$.-c).^|
000000a0  1f bb 32 60 86 4d 3e 75  03 22 17 03 0b 4d 33 52  |..2`.M>u."...M3R|
000000b0  3a 6f 5b 2f 39 a9 1b c4  29 20 c5 9d 0f f4 9f 9a  |:o[/9...) ......|
000000c0  50 c5 dc 69 1e 10 c9 10  5f e6 5e 27 34 30 97 7c  |P..i...._.^'40.||
000000d0  8c 97 9d 65 27 9a 41 b1  b7 9b c4 92 cf a8 6b 13  |...e'.A.......k.|
000000e0  f9 15 9d e2 ca fd 59 aa  17 82 80 48 9b e8 5d 87  |......Y....H..].|
000000f0  a8 42 52 9f b7 8f 1b 03  2d 46 63 f5 b8 61 b2 a3  |.BR.....-Fc..a..|
00000100  20 13 e0 21 2f 14 3a 16  e0 59 76 3d 04 95 6a d5  | ..!/.:..Yv=..j.|
00000110  51 56 6f 9c fb 38 06 ed  6f 7d 6c cc ba 9a 77 98  |QVo..8..o}l...w.|
00000120  bd 93 70 57 bd 61 dd 7d  c7 64 a0 28 92 cf c9 0a  |..pW.a.}.d.(....|
00000130  79 23 95 a3 a4 ef e4 07  4e 21 15 15 9f 8f c4 d8  |y#......N!......|
00000140  39 c1 60 f1 b4 aa 9c 27  bd 1f 4a e1 27 96 b5 a9  |9.`....'..J.'...|
00000150  2e 28 90 bb e4 24 84 78  23 8c 9d f4 eb 2c 0a fa  |.(...$.x#....,..|
00000160  91 98 47 b3 69 00 9b be  b2 ca 58 60 c3 2c 9a e5  |..G.i.....X`.,..|
00000170  a4 ba 9a a6 a0 e9 5d c3  56 4d 88 59 34 dd f1 99  |......].VM.Y4...|
00000180  dd c8 30 35 63 14 ef 5f  80 25 a4 4e 98 b7 54 ea  |..05c.._.%.N..T.|
00000190  8c f0 15 bd cb 1b 81 9e  da 80 c6 5e e7 04 89 28  |...........^...(|
000001a0  df 35 bb 5e b3 d7 cf 29  43 cb 0a 31 86 f1 91 dd  |.5.^...)C..1....|
000001b0  32 60 73 52 63 46 1d 9d  1c 9c 2a 8b 1f 39 00 fe  |2`sRcF....*..9..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 00 00 19 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 00  00 19 00 a0 75 0f 00 00  |............u...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
hexdump: u: bad byte count
/usr/share/boot-sav/bis.sh: line 1746: [: -eq: unary operator expected
cat: write error: Broken pipe
File descriptor 9 (/proc/6291/mounts) leaked on lvs invocation. Parent PID 14429: bash
File descriptor 63 (pipe:[54621]) leaked on lvs invocation. Parent PID 14429: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2015-07-15__02h50 ===================
boot-info version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/6291/mounts) leaked on lvs invocation. Parent PID 7794: /bin/sh
No volume groups found
boot-info is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

=================== os-prober:
/dev/sda6:Ubuntu 14.04.2 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="703047243046F120" TYPE="ntfs"
/dev/sda2: UUID="96AC216DAC2148D7" TYPE="ntfs"
/dev/sda4: LABEL="Recovery" UUID="8C9E88AD9E8890FE" TYPE="ntfs"
/dev/sda5: LABEL="New Volume" UUID="A68C004E8C001C05" TYPE="ntfs"
/dev/sda6: UUID="a5c1bee5-4185-4c27-ac1d-9d33ce5da3b0" TYPE="ext4"
/dev/sdb1: UUID="F97E-8233" TYPE="vfat"
/dev/zram0: UUID="2bb4f806-6784-4159-a1c4-bdcceb971822" TYPE="swap"
/dev/zram1: UUID="9cc7860d-8076-4f98-8828-d767f492a83c" TYPE="swap"
/dev/zram2: UUID="a85a2766-fde3-458f-be93-1c330746828c" TYPE="swap"
/dev/zram3: UUID="ee7b5414-3176-4d46-8175-d27e40dd1e6a" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root        4096 Jul 15 02:15 grub.d
drwxr-xr-x  2 root root        4096 Jul 15 01:57 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 Jun 26 11:16 00_header
-rwxr-xr-x 1 root root  6058 May 13 14:51 05_debian_theme
-rwxr-xr-x 1 root root 11608 Jun 26 11:16 10_linux
-rwxr-xr-x 1 root root 10412 Jun 26 11:16 20_linux_xen
-rwxr-xr-x 1 root root 11692 Jun 26 11:16 30_os-prober
-rwxr-xr-x 1 root root  1416 Jun 26 11:16 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 26 11:16 40_custom
-rwxr-xr-x 1 root root   216 Jun 26 11:16 41_custom
-rw-r--r-- 1 root root   483 Jun 26 11:16 README




=================== sda6/etc/default/grub :

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




efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 2001,2002,2003
Boot0000* USB Hard Drive - SanDisk Cruzer Force    BIOS(7,500,0a).......................................................................
Boot0001* USB Hard Drive (UEFI) - SanDisk Cruzer Force    ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(2,0)HD(1,20,1dd17e0,00000000)RC
Boot0002* Notebook Hard Drive    BIOS(2,0,67).......................................................................
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
1      1049kB  210MB  209MB   primary   ntfs
2      210MB   270GB  269GB   primary   ntfs         boot
3      270GB   617GB  348GB   extended               lba
5      270GB   484GB  215GB   logical   ntfs
6      484GB   617GB  133GB   logical   ext4
4      617GB   640GB  22.9GB  primary   ntfs


Model: SanDisk Cruzer Force (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:640GB:scsi:512:4096:msdos:ATA Hitachi HTS54756;
1:1049kB:210MB:209MB:ntfs::;
2:210MB:270GB:269GB:ntfs::boot;
3:270GB:617GB:348GB:::lba;
5:270GB:484GB:215GB:ntfs::;
6:484GB:617GB:133GB:ext4::;
4:617GB:640GB:22.9GB:ntfs::;

BYT;
/dev/sdb:16.0GB:scsi:512:512:msdos:SanDisk Cruzer Force;
1:16.4kB:16.0GB:16.0GB:fat32::boot, lba;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fb1 fd freefall full fuse hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 37 06 00 00 00 00 00  |.........7......|
00000030  55 42 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |UB..............|
00000040  f6 00 00 00 01 00 00 00  20 f1 46 30 24 47 30 70  |........ .F0$G0p|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 06 00  |........?....@..|
00000020  00 00 00 00 80 00 80 00  ff 4f 5b 1f 00 00 00 00  |.........O[.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d7 48 21 ac 6d 21 ac 96  |.........H!.m!..|
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

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 d7 47  |........?....8.G|
00000020  00 00 00 00 80 00 80 00  ff 07 ab 02 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  fe 90 88 9e ad 88 9e 8c  |................|
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
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff ff 18 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  05 1c 00 8c 4e 00 8c a6  |............N...|
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

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.9G   34M  2.9G   2% /
udev           devtmpfs   2.9G   12K  2.9G   1% /dev
tmpfs          tmpfs      586M  1.2M  585M   1% /run
/dev/sdb1      vfat        15G  648M   15G   5% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      2.9G  1.9M  2.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      2.9G     0  2.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk    199M   29M  171M  15% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    251G  116G  136G  47% /mnt/boot-sav/sda2
/dev/sda4      fuseblk     22G   20G  2.4G  90% /mnt/boot-sav/sda4
/dev/sda5      fuseblk    200G   92M  200G   1% /mnt/boot-sav/sda5
/dev/sda6      ext4       122G  4.7G  111G   5% /mnt/boot-sav/sda6

=================== fdisk -l:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xed32b43f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2   *      409600   526487551   263038976    7  HPFS/NTFS/exFAT
/dev/sda3       526489598  1205286911   339398657    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4      1205286912  1250050047    22381568    7  HPFS/NTFS/exFAT
/dev/sda5       526489600   945919999   209715200    7  HPFS/NTFS/exFAT
/dev/sda6       945922048  1205286911   129682432   83  Linux

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31266815    15633392    c  W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda6 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2015-07-14
While you have UEFI capabile hardware, your Windows & Ubuntu are installed in CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

So do not boot Boot-Repair in UEFI mode, but in BIOS mode to make repairs.
You also have grub installed to the partition, but that will never be used and should not create issues. But do not install grub to partitions, just to MBR or first sector of hard drive.

Does Ubuntu boot?
If Ubuntu does boot run this from Ubuntu, not live installer.
sudo update-grub

That should add a Windows boot stanza to grub menu. But grub only boots working Windows. If Windows needs chkdsk which it does after partition size change or abnormal shutdown or is hibernated, then grub will not boot it. You then need a Windows repair CD or Flash drive to fix Windows. 
Linux tools can only fix minor Windows issues, and cannot run chkdsk.

      
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

