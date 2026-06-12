---
title: "Grub2 ignores Win7 on second hard drive"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by seb_stein on 2014-01-02
I have two discs in my system, sda for Ubuntu and sdb for Win7. I can boot Win7 without problems if I put it as first boot option in my bios. If I put Ubuntu as first option, grub menu is shown, but it only has entries for Ubuntu (e.g. previous kernels). For some reason, grub can't find my Win7 and also creates no boot entry when running grub-update.

I think that grub should be able to detect my Windows install. So is there a way to do it? I don't want to create a manual entry with all the chain loader stuff if possible.

Here the output of the bootinfoscript. Note, I have encrypted my Linux root partition (sda3). The drive sdc is just a USB stick with the Live DVD version of Ubuntu.

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1840944 of /dev/sdc4 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

ubuntu-vg-root': _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unbekannter Dateisystemtyp &#8222;&#8220;

ubuntu-vg-swap_1': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unbekannter Dateisystemtyp &#8222;&#8220;
mount: unbekannter Dateisystemtyp &#8222;&#8220;

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 Köpfe, 63 Sektoren/Spur, 243201 Zylinder, zusammen 3907029168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       999,423       997,376 EFI System partition
/dev/sda2         999,424     1,499,135       499,712 Data partition (Linux)
/dev/sda3       1,499,136 3,907,028,991 3,905,529,856 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   488,392,703   488,185,856   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16001269760 bytes
255 Köpfe, 63 Sektoren/Spur, 1945 Zylinder, zusammen 31252480 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc4    *             63    31,252,416    31,252,354   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/sda3_crypt IyOLUZ-wbmu-SGVF-gp7e-6ofs-PXY4-g0H8fi LVM2_member 
/dev/mapper/ubuntu--vg-root 047de60d-a931-4b25-a025-788aa3d94764   ext4       
/dev/mapper/ubuntu--vg-swap_1 c294e95d-91c3-467b-ad5d-8a39b52c22f4   swap       
/dev/sda1        37F3-B48B                              vfat       
/dev/sda2        fc0793da-d08f-4b96-98d8-462c4e463bbd   ext2       
/dev/sda3        c6f67ba8-1b93-480f-a0d5-b4bdf546d809   crypto_LUKS 
/dev/sdb1        164E7AC84E7A9FE3                       ntfs       System-reserviert
/dev/sdb2        1CD07D12D07CF2FE                       ntfs       
/dev/sdc4        A65F-CB44                              vfat       KINGSTON

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sda3_crypt
ubuntu--vg-root
ubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/ubuntu--vg-root /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda2        /boot                    ext2       (rw)
/dev/sdb1        /media/steinchen/System-reserviert fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/steinchen/1CD07D12D07CF2FE fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


============================= sda2/grub/grub.cfg: ==============================

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
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  fc0793da-d08f-4b96-98d8-462c4e463bbd
else
  search --no-floppy --fs-uuid --set=root fc0793da-d08f-4b96-98d8-462c4e463bbd
fi
    font="/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=de_DE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
#set_background_image "images/tile.png";

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
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
menuentry 'Kubuntu' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-047de60d-a931-4b25-a025-788aa3d94764' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  fc0793da-d08f-4b96-98d8-462c4e463bbd
    else
      search --no-floppy --fs-uuid --set=root fc0793da-d08f-4b96-98d8-462c4e463bbd
    fi
    linux    /vmlinuz-3.11.0-14-generic root=/dev/mapper/ubuntu--vg-root ro   
    initrd    /initrd.img-3.11.0-14-generic
}
submenu 'Erweiterte Optionen für Kubuntu' $menuentry_id_option 'gnulinux-advanced-047de60d-a931-4b25-a025-788aa3d94764' {
    menuentry 'Kubuntu, mit Linux 3.11.0-14-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-14-generic-advanced-047de60d-a931-4b25-a025-788aa3d94764' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  fc0793da-d08f-4b96-98d8-462c4e463bbd
        else
          search --no-floppy --fs-uuid --set=root fc0793da-d08f-4b96-98d8-462c4e463bbd
        fi
        echo    'Linux 3.11.0-14-generic wird geladen &#8230;'
        linux    /vmlinuz-3.11.0-14-generic root=/dev/mapper/ubuntu--vg-root ro   
        echo    'Initiale Ramdisk wird geladen &#8230;'
        initrd    /initrd.img-3.11.0-14-generic
    }
    menuentry 'Kubuntu, mit Linux 3.11.0-14-generic (Wiederherstellungsmodus)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-14-generic-recovery-047de60d-a931-4b25-a025-788aa3d94764' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  fc0793da-d08f-4b96-98d8-462c4e463bbd
        else
          search --no-floppy --fs-uuid --set=root fc0793da-d08f-4b96-98d8-462c4e463bbd
        fi
        echo    'Linux 3.11.0-14-generic wird geladen &#8230;'
        linux    /vmlinuz-3.11.0-14-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Initiale Ramdisk wird geladen &#8230;'
        initrd    /initrd.img-3.11.0-14-generic
    }
    menuentry 'Kubuntu, mit Linux 3.11.0-13-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-13-generic-advanced-047de60d-a931-4b25-a025-788aa3d94764' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  fc0793da-d08f-4b96-98d8-462c4e463bbd
        else
          search --no-floppy --fs-uuid --set=root fc0793da-d08f-4b96-98d8-462c4e463bbd
        fi
        echo    'Linux 3.11.0-13-generic wird geladen &#8230;'
        linux    /vmlinuz-3.11.0-13-generic root=/dev/mapper/ubuntu--vg-root ro   
        echo    'Initiale Ramdisk wird geladen &#8230;'
        initrd    /initrd.img-3.11.0-13-generic
    }
    menuentry 'Kubuntu, mit Linux 3.11.0-13-generic (Wiederherstellungsmodus)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-13-generic-recovery-047de60d-a931-4b25-a025-788aa3d94764' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  fc0793da-d08f-4b96-98d8-462c4e463bbd
        else
          search --no-floppy --fs-uuid --set=root fc0793da-d08f-4b96-98d8-462c4e463bbd
        fi
        echo    'Linux 3.11.0-13-generic wird geladen &#8230;'
        linux    /vmlinuz-3.11.0-13-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Initiale Ramdisk wird geladen &#8230;'
        initrd    /initrd.img-3.11.0-13-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdc4/boot/grub/grub.cfg: ===========================

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

========================= sdc4/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdc4: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdc4: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 40  |...............@|
00000070  1a ca 56 10 42 9a a9 2f  48 d5 44 cb 0d 7a 5b 9d  |..V.B../H.D..z[.|
00000080  1a d2 79 32 d8 25 14 bc  21 82 c6 2f b4 1d 15 e6  |..y2.%..!../....|
00000090  e7 a2 f6 01 1e f5 e2 27  9f cf 77 19 51 4e ff 35  |.......'..w.QN.5|
000000a0  bc 62 4a d4 00 00 d3 ea  63 36 66 36 37 62 61 38  |.bJ.....c6f67ba8|
000000b0  2d 31 62 39 33 2d 34 38  30 66 2d 61 30 64 35 2d  |-1b93-480f-a0d5-|
000000c0  62 34 62 64 66 35 34 36  64 38 30 39 00 00 00 00  |b4bdf546d809....|
000000d0  00 ac 71 f3 00 03 51 0e  7a bf 2b 1a 06 a4 86 91  |..q...Q.z.+.....|
000000e0  8f a5 c2 00 3d ee e8 2f  98 bd ba 48 6e f9 64 75  |....=../...Hn.du|
000000f0  e2 65 86 a5 93 b5 e0 27  00 00 00 08 00 00 0f a0  |.e.....'........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 02 00 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 03 f8 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 05 f0 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 07 e8 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 09 e0 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on ubuntu-vg-root'


Unknown BootLoader on ubuntu-vg-swap_1'



=============================== StdErr Messages: ===============================

xz: (stdin): Komprimierte Daten sind korrupt
cat: /tmp/BootInfo-4Q9yA4qO/Tmp_Log: Datei oder Verzeichnis nicht gefunden
cat: /tmp/BootInfo-4Q9yA4qO/Tmp_Log: Datei oder Verzeichnis nicht gefunden
cat: /tmp/BootInfo-4Q9yA4qO/Tmp_Log: Datei oder Verzeichnis nicht gefunden
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'
  Volume group name ubuntu-vg-root' has invalid characters
  Skipping volume group ubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'
  Volume group name ubuntu-vg-root' has invalid characters
  Skipping volume group ubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'
  Volume group name ubuntu-vg-root' has invalid characters
  Skipping volume group ubuntu-vg-root'
hexdump: /dev/mapper/ubuntu-vg-root': Datei oder Verzeichnis nicht gefunden
hexdump: /dev/mapper/ubuntu-vg-root': Datei oder Verzeichnis nicht gefunden
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'
  Volume group name ubuntu-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'
  Volume group name ubuntu-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'
  Volume group name ubuntu-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-vg-swap_1'
hexdump: /dev/mapper/ubuntu-vg-swap_1': Datei oder Verzeichnis nicht gefunden
hexdump: /dev/mapper/ubuntu-vg-swap_1': Datei oder Verzeichnis nicht gefunden

```

---

### Post by fantab on 2014-01-02
What happens when you run:
```
sudo update-grub
```

Post the output of:
```
sudo parted -l
sudo fdisk -l
```

Is your Windows installed in UEFI mode?

---

### Post by seb_stein on 2014-01-02
> **fantab said:**
> What happens when you run:
```
sudo update-grub
```


It adds the entries for the kernels:

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
done

```

> 
Post the output of:
```
sudo parted -l
sudo fdisk -l
```


parted:

```

Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  512MB   511MB   fat32              boot
 2      512MB   768MB   256MB   ext2
 3      768MB   2000GB  2000GB


Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   250GB  250GB  primary  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 1982GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1982GB  1982GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 17.2GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  17.2GB  17.2GB  linux-swap(v1)


Error: /dev/mapper/sda3_crypt: unrecognised disk label

```

fdisk:

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6c2c6c2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   488392703   244092928    7  HPFS/NTFS/exFAT

Disk /dev/mapper/sda3_crypt: 1999.6 GB, 1999629189120 bytes
255 heads, 63 sectors/track, 243107 cylinders, total 3905525760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda3_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 1982.5 GB, 1982467145728 bytes
255 heads, 63 sectors/track, 241021 cylinders, total 3872006144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 17.2 GB, 17158897664 bytes
255 heads, 63 sectors/track, 2086 cylinders, total 33513472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

```

> Is your Windows installed in UEFI mode?

That's the part I'm unsure about and also where I don't know how to check it. Windows has this boot partition and its ordinary partition.

---

### Post by fantab on 2014-01-02
You have your /dev/sda or first HDD formatted as 'GPT', and Ubuntu is installed either in UEFI mode with its own EFI partition **or** is booting in 'legacy' mode from the second ext2 partition.
But your /dev/sdb or second HDD is formatted as 'msdos' and Windows is installed in 'Legacy/CSM/MBR' mode.

To fix the issue permanently and to be able to boot both OS from GRUB you'll have to re-install Windows in UEFI mode. (Both OS must be installed in same boot mode).

To boot Windows in EFI mode you have to re-format your second HDD or /dev/sdb or on which Win is currently installed with GUID Partition Table [GPT].
After formatting it with GPT you will have to make your first partition (/dev/sdb1) as EFI System Partition [ESP], formatted with FAT32 and flagged as 'boot'.
Windows boots in UEFI from GPT disks only.
To install Windows7 in UEFI mode: [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

After successfully installing Windows boot into Ubuntu and run 'update-grub'.

It will be a good idea to see the '**BootInfo Summary**' which **[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")** creates to get the full picture of your boot. It generates a LINK save it and post the LINK here.

---

### Post by oldfred on 2014-01-02
You have to slightly modify a Windows 7 install DVD, by copying it to flash drive and making a few changes so it can be a UEFI installer.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Or you can convert Ubuntu install to BIOS boot. Ubuntu will boot with BIOS boot mode on gpt partitioned drive, where Windows only boots UEFI with gpt or from gpt only with UEFI.
You have to create a tiny 1 or 2MB unformatted partition any where on drive with the bios_grub boot flag with gparted and then with Boot-Repair boot in BIOS mode and use it to convert. It uninstalls grub-efi(UEFI) and installs grub-pc (BIOS). If you leave efi partition on drive you later can convert back to UEFI if desired.

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

UEFI and BIOS are not really compatible, so once you start booting in one mode you cannot change to the other mode, or grub cannot dual boot.

---

### Post by seb_stein on 2014-01-03
Ok, so I think I will try to convert my Ubuntu install to BIOS boot as I don't want to waste my time re-installing Windows. But it seems to rely on the assumption that I boot a live USB stick in BIOS mode first, otherwise it will fail. I will have to investigate how to ensure that. Is there some command I can issue in a running Linux system to see whether it was booted via BIOS or UEFI?

---

### Post by oldfred on 2014-01-04
From UEFI menu, you should have two entries for flash drive. Many are not really clear but one should be UEFI and the other BIOS.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

