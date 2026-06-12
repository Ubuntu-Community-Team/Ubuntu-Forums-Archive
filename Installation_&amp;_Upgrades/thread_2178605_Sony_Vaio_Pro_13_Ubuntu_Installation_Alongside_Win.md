---
title: "Sony Vaio Pro 13 Ubuntu Installation Alongside Windows 8 Trouble"
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by kreo2 on 2013-10-04
I have the notebook Sony Vaio Pro 13 SVP1321X9R with 128GB SSD and preinstalled Windows 8. The default BIOS mode is EFI. I need dual boot system (Windows and Ubuntu). According to several recommendations ([this one]("https://spicious.com/sony-vaio-pro-11-with-ubuntu.html") and [this one]("http://simon.schllng.de/2013/08/10/ubuntu-auf-dem-sony-vaio-pro-13/?lang=en")) I have switched BIOS mode to the Legacy. Next Ubuntu has been installed normally from USB flash. But while direct boot (without external device) I've got **Operation System Not Found**. Next I have used **bootinfoscript** utility according [this thread]("http://ubuntuforums.org/showthread.php?t=1758469"). So the dump is below. Dear experts please help to bring the dual boot system up! It is too much important for me. Thanks before.
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    149450752 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 94 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/ubuntu/grubx64.efi /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu Saucy Salamander 
                       (development branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1812528 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   250,069,679   250,069,679  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       534,527       532,480 -
/dev/sda2         534,528     3,553,279     3,018,752 Windows Recovery Environment (Windows)
/dev/sda3       3,553,280     4,085,759       532,480 EFI System partition
/dev/sda4       4,085,760     4,347,903       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,347,904   149,449,777   145,101,874 Data partition (Windows/Linux)
/dev/sda6     228,020,224   250,068,991    22,048,768 Windows Recovery Environment (Windows)
/dev/sda7     149,450,752   149,452,799         2,048 BIOS Boot partition
/dev/sda8     149,452,800   211,435,519    61,982,720 Data partition (Linux)
/dev/sda9     211,435,520   228,020,223    16,584,704 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2030 MB, 2030043136 bytes
63 heads, 62 sectors/track, 1015 cylinders, total 3964928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,964,589     3,964,528   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F421-C224                              vfat       SONYSYS
/dev/sda2        0274DF2A74DF1EEB                       ntfs       Windows RE tools
/dev/sda3        C657-1C80                              vfat       
/dev/sda5        3E245A55245A106F                       ntfs       
/dev/sda6        C4866D2F866D22E2                       ntfs       Recovery
/dev/sda8        a3de726f-38dc-4a29-b00b-894bf8dd226b   ext4       
/dev/sda9        7350d2a9-5d5a-4d93-95e9-c7163b995972   swap       
/dev/sdb1        9087-79E9                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="0"

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
insmod part_gpt
insmod ext2
set root='hd0,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  a3de726f-38dc-4a29-b00b-894bf8dd226b
else
  search --no-floppy --fs-uuid --set=root a3de726f-38dc-4a29-b00b-894bf8dd226b
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
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a3de726f-38dc-4a29-b00b-894bf8dd226b' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  a3de726f-38dc-4a29-b00b-894bf8dd226b
    else
      search --no-floppy --fs-uuid --set=root a3de726f-38dc-4a29-b00b-894bf8dd226b
    fi
    linux    /boot/vmlinuz-3.11.0-8-generic root=UUID=a3de726f-38dc-4a29-b00b-894bf8dd226b ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-8-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a3de726f-38dc-4a29-b00b-894bf8dd226b' {
    menuentry 'Ubuntu, with Linux 3.11.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-8-generic-advanced-a3de726f-38dc-4a29-b00b-894bf8dd226b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  a3de726f-38dc-4a29-b00b-894bf8dd226b
        else
          search --no-floppy --fs-uuid --set=root a3de726f-38dc-4a29-b00b-894bf8dd226b
        fi
        echo    'Loading Linux 3.11.0-8-generic ...'
        linux    /boot/vmlinuz-3.11.0-8-generic root=UUID=a3de726f-38dc-4a29-b00b-894bf8dd226b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-8-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-8-generic-recovery-a3de726f-38dc-4a29-b00b-894bf8dd226b' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  a3de726f-38dc-4a29-b00b-894bf8dd226b
        else
          search --no-floppy --fs-uuid --set=root a3de726f-38dc-4a29-b00b-894bf8dd226b
        fi
        echo    'Loading Linux 3.11.0-8-generic ...'
        linux    /boot/vmlinuz-3.11.0-8-generic root=UUID=a3de726f-38dc-4a29-b00b-894bf8dd226b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-8-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  a3de726f-38dc-4a29-b00b-894bf8dd226b
    else
      search --no-floppy --fs-uuid --set=root a3de726f-38dc-4a29-b00b-894bf8dd226b
    fi
    linux16    /boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  a3de726f-38dc-4a29-b00b-894bf8dd226b
    else
      search --no-floppy --fs-uuid --set=root a3de726f-38dc-4a29-b00b-894bf8dd226b
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-0274DF2A74DF1EEB' {
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0274DF2A74DF1EEB
    else
      search --no-floppy --fs-uuid --set=root 0274DF2A74DF1EEB
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 8 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-C657-1C80' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  C657-1C80
    else
      search --no-floppy --fs-uuid --set=root C657-1C80
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=a3de726f-38dc-4a29-b00b-894bf8dd226b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=7350d2a9-5d5a-4d93-95e9-c7163b995972 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
329701f46e06124e8273346c5641494f
Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 24 c2 21 f4 4e  4f 20 4e 41 4d 45 20 20  |..)$.!.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda3

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 01 7e 20  |.X.MSDOS5.0...~ |
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 36 00  |........?....86.|
00000020  00 20 08 00 c1 0f 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 80 1c 57 c6 4e  4f 20 4e 41 4d 45 20 20  |..)..W.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-x1EczfiJ/Tmp_Log: No such file or directory
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-x1EczfiJ/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-x1EczfiJ/Tmp_Log: No such file or directory
  No volume groups found



```

---

### Post by sid5291 on 2013-10-10
+1 to this problem , Have the Sony VAIO pro 13 128 gb model tried every method possible even wiped my windows to install ubuntu still get the "operating system no found" Ubuntu 13.10 form usb runs perfectly but doesnt seem work from the SSD. Thank you for your help.

---

### Post by akbarrkhan on 2013-10-10
i had the same problem with my system i installed 13.04 from live cd and the experts told me a way that was about grub, as i am really a new user and that command line was really difficult for me, so my advice go for the grub repair thing if u r good with commands on terminal if not try to install 12.04 it will solve the dual boot problem as it did for me.

---

### Post by sid5291 on 2013-10-11
Hey Akbar when I try with the 13.04 or 12.04 live cd  it doesn't seem to boot for the USB. it gets stuck on a blank screen. Can you please let me know what i should do ? did you boot it in Legacy mode ?

---

### Post by akbarrkhan on 2013-10-11
> **sid5291 said:**
> Hey Akbar when I try with the 13.04 or 12.04 live cd  it doesn't seem to boot for the USB. it gets stuck on a blank screen. Can you please let me know what i should do ? did you boot it in Legacy mode ?

ya i used legacy mode boot

Use live CD it will solve ur problem, USB boot will not work

---

### Post by pkinnaird on 2013-10-15
Try using the 'assist' boot, navigating around the bios menu, then exiting back to the assist menu. Choose 'exit and restart to windows' and it should reboot you to grub. Magically it might work!

I've solved this problem this way a bunch of times. Never would have thought of it except that someone suggested the same solution to a different problem I used to have: sometimes the keyboard hardware wouldn't be detected correctly and the mappings would be off. This solution solves that problem too. Unfortunately, it seems to have been happening more frequently. Currently compiling kernel 3.12 rc5 to see if that improves anything with this problem.

---

