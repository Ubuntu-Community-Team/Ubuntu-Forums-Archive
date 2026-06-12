---
title: "Issue booting new install on i7 Asus Zenbook"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by mrcapone on 2017-02-23
Hey guys, this cry out for help comes after much searching online and trial \ error testing. (Error being the predominant result for me) ... I'd like to point out to start that I am not a Linux guru (far from) but have used Debian for some years and am quite familiar with the basics ... 

So, why am I pulling my hair out and begging here for a little assistance? 

Well I've brought a new laptop. It is a Asus Zenbook i7 Intel chipset UX360UAK <Model 

At first I wanted to stick with Debian but the install of Jessie 8 failed miserably with no mouse pad working and WiFi off and screen resolution a mess. So I abandoned that. 

Upon research I found that I should be using mint or ubuntu (as others had successfully used these on this machine) so off I went and got the latest Ubuntu on a USB live stick. 

The live stick boots perfectly and its a great user experience. So I wiped the 512GB SSD internal drive using "disks" with an ext4 format. Then proceeded to install from the live USB. 

The install seems successful, and I apply encryption during the install. (Although upon the following issues I have tried without the encryption too, to no avail) 

After the install, the laptop reboots and just hangs on the loading front page where I enter the key. I get a message "cryptsetup: sda3 set up successfully" 

But that's it, no further... I'm pulling my hair out... So I started a live session again and ran boot-repair from ppa:yannubuntu\boot-repair 

This following mess is my output... (It still didn't solve anything) 

I hope someone here can point me in the right direction. I would REALLLLLLLY appreciate any help :( 

Thanks in advance guys
```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 is already mounted or /mnt/BootInfo/sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 14432. According to the info in 
                       the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 is already mounted or /mnt/BootInfo/sdb1 busy
mount: /dev/sdb2 is already mounted or /mnt/BootInfo/sdb2 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       999,423       997,376  83 Linux
/dev/sda2           1,001,470 1,000,214,527   999,213,058   5 Extended
/dev/sda5           1,001,472 1,000,214,527   999,213,056  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 14.6 GiB, 15610576896 bytes, 30489408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     3,035,519     3,035,520   0 Empty
/dev/sdb2              14,432        19,295         4,864  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1   +  R              0     3,035,463     3,035,464 Data partition (Windows/Linux)
/dev/sdb2   +  R         14,432        19,295         4,864 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3f81bc56-9c80-4fe4-bd85-707246ed409a   ext2       
/dev/sda5        48ac72cd-2e96-40de-a67b-c63de76bcfa6   crypto_LUKS 
/dev/sdb1        2017-02-15-21-44-13-00                 iso9660    Ubuntu 16.04.2 LTS amd64
/dev/sdb2        E561-C446                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb 24 00:43 ata-MTFDDAV512TBN_162613EA43BC -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 24 00:43 ata-MTFDDAV512TBN_162613EA43BC-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 24 00:43 ata-MTFDDAV512TBN_162613EA43BC-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 24 00:43 ata-MTFDDAV512TBN_162613EA43BC-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Feb 24 00:44 usb-Kingston_DataTraveler_2.0_C86000BDB9EAEE609A2F0154-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 24 00:44 usb-Kingston_DataTraveler_2.0_C86000BDB9EAEE609A2F0154-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Feb 24 00:44 usb-Kingston_DataTraveler_2.0_C86000BDB9EAEE609A2F0154-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Feb 24 00:43 wwn-0x500a075113ea43bc -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 24 00:43 wwn-0x500a075113ea43bc-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 24 00:43 wwn-0x500a075113ea43bc-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 24 00:43 wwn-0x500a075113ea43bc-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3f81bc56-9c80-4fe4-bd85-707246ed409a
else
  search --no-floppy --fs-uuid --set=root 3f81bc56-9c80-4fe4-bd85-707246ed409a
fi
    font="/grub/unicode.pf2"
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
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e33f0a27-997b-4dcd-b36c-514fbe1f456d' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3f81bc56-9c80-4fe4-bd85-707246ed409a
    else
      search --no-floppy --fs-uuid --set=root 3f81bc56-9c80-4fe4-bd85-707246ed409a
    fi
    linux    /vmlinuz-4.8.0-36-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
    initrd    /initrd.img-4.8.0-36-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e33f0a27-997b-4dcd-b36c-514fbe1f456d' {
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-advanced-e33f0a27-997b-4dcd-b36c-514fbe1f456d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3f81bc56-9c80-4fe4-bd85-707246ed409a
        else
          search --no-floppy --fs-uuid --set=root 3f81bc56-9c80-4fe4-bd85-707246ed409a
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /vmlinuz-4.8.0-36-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-init-upstart-e33f0a27-997b-4dcd-b36c-514fbe1f456d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3f81bc56-9c80-4fe4-bd85-707246ed409a
        else
          search --no-floppy --fs-uuid --set=root 3f81bc56-9c80-4fe4-bd85-707246ed409a
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /vmlinuz-4.8.0-36-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-recovery-e33f0a27-997b-4dcd-b36c-514fbe1f456d' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3f81bc56-9c80-4fe4-bd85-707246ed409a
        else
          search --no-floppy --fs-uuid --set=root 3f81bc56-9c80-4fe4-bd85-707246ed409a
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /vmlinuz-4.8.0-36-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.8.0-36-generic
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

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.005342484 = 0.005736448    grub/grub.cfg                                  7
   0.180962563 = 0.194307072    grub/i386-pc/core.img                          2
   0.066367149 = 0.071261184    vmlinuz-4.8.0-36-generic                      10
   0.239776611 = 0.257458176    initrd.img-4.8.0-36-generic                   15

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  58 03 00 00 00 00 00 00  3d 54 e2 15 00 00 80 00  |X.......=T......|
000001c0  01 00 00 5c e0 fb 00 00  00 00 80 51 2e 00 00 fe  |...\.......Q....|
000001d0  ff ff ef fe ff ff 60 38  00 00 00 13 00 00 00 00  |......`8........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


/dev/sdb1: unknown GPT attributes
1000000000000001

/dev/sdb2: unknown GPT attributes
1000000000000001
Unknown BootLoader on sda5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 32 35 36 00 00  |........sha256..|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 40  |...............@|
00000070  5f b0 98 49 82 d5 01 0d  9f d9 61 b6 aa 0c eb c7  |_..I......a.....|
00000080  60 6e b3 06 ac 37 d1 e7  8b 0a be 0b 48 ae 5b 64  |`n...7......H.[d|
00000090  3b 08 19 ba 3f dd d0 97  68 a9 c9 c1 6e 32 a1 eb  |;...?...h...n2..|
000000a0  1b a8 f1 90 00 01 8b 82  34 38 61 63 37 32 63 64  |........48ac72cd|
000000b0  2d 32 65 39 36 2d 34 30  64 65 2d 61 36 37 62 2d  |-2e96-40de-a67b-|
000000c0  63 36 33 64 65 37 36 62  63 66 61 36 00 00 00 00  |c63de76bcfa6....|
000000d0  00 ac 71 f3 00 06 2e 46  e5 9e 38 03 e0 25 0b 04  |..q....F..8..%..|
000000e0  bd f4 41 3c ab a4 05 5f  bb 4f 9b d2 11 4a de 18  |..A<..._.O...J..|
000000f0  79 87 49 de 42 d2 48 d7  00 00 00 08 00 00 0f a0  |y.I.B.H.........|
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

Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  58 03 00 00 00 00 00 00  3d 54 e2 15 00 00 80 00  |X.......=T......|
000001c0  01 00 00 5c e0 fb 00 00  00 00 80 51 2e 00 00 fe  |...\.......Q....|
000001d0  ff ff ef fe ff ff 60 38  00 00 00 13 00 00 00 00  |......`8........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/5294/mounts) leaked on lvs invocation. Parent PID 12271: bash
File descriptor 63 (pipe:[38865]) leaked on lvs invocation. Parent PID 12271: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-02-24__00h43 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
boot-repair is executed in live-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda5 : Error code 32
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32

=================== os-prober:


=================== blkid:
/dev/sda1: UUID="3f81bc56-9c80-4fe4-bd85-707246ed409a" TYPE="ext2" PARTUUID="22eacc1a-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="48ac72cd-2e96-40de-a67b-c63de76bcfa6" TYPE="crypto_LUKS" PARTUUID="22eacc1a-05"
/dev/sdb1: UUID="2017-02-15-21-44-13-00" LABEL="Ubuntu 16.04.2 LTS amd64" TYPE="iso9660" PTUUID="15e2543d" PTTYPE="dos" PARTUUID="15e2543d-01"
/dev/sdb2: SEC_TYPE="msdos" UUID="E561-C446" TYPE="vfat" PARTUUID="15e2543d-02"

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda5 : Error code 32
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32
dd: invalid number: ‘0’
Warning: /var/log/boot-sav/log/2017-02-24__00h43boot-repair55/sdb/current_mbr.img could not be created. Please report this message to [email]boot.repair@gmail.com[/email]

=================== sda1recordfail=1/grub/grubenv :
recordfail=1




=================== efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0001
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........o.M.T.F.D.D.A.V.5.1.2.T.B.N............ ........A...................... .....>..Gd-.;.A..MQ..L. . . . . . . . .6.1.6.2.3.1.A.E.3.4.C.B... .....BO
Boot0002* UEFI: KingstonDataTraveler 2.0PMAP    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/CDROM(1,0x3860,0x4c00)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


=================== PARTITIONS & DISKS:
sda1    : sda,    is-sepboot,    grubenv-ng    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb2.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    no-os,    0 sectors * 512 bytes


=================== parted -l:

Model: ATA MTFDDAV512TBN (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type      File system  Flags
1      1049kB  512MB  511MB  primary   ext2         boot
2      513MB   512GB  512GB  extended
5      513MB   512GB  512GB  logical


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

=================== parted -lm:

BYT;
/dev/sda:512GB:scsi:512:512:msdos:ATA MTFDDAV512TBN:;
1:1049kB:512MB:511MB:ext2::boot;
2:513MB:512GB:512GB:::;
5:513MB:512GB:512GB:::;

BYT;
/dev/sdb:15.6GB:scsi:512:512:unknown:Kingston DataTraveler 2.0:;

=================== lsblk:
KNAME TYPE FSTYPE        SIZE LABEL
sdb   disk iso9660      14.6G Ubuntu 16.04.2 LTS amd64
sdb2  part vfat          2.4M Ubuntu 16.04.2 LTS amd64
sdb1  part iso9660       1.5G Ubuntu 16.04.2 LTS amd64
loop0 loop squashfs      1.4G
sda   disk               477G
sda2  part                 1K
sda5  part crypto_LUKS 476.5G
sda1  part ext2          487M

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  1 running /cdrom
sdb2     1  0  1
sdb1     1  0  1
loop0    1  1  0         /rofs
sda      0  0  0 running
sda2     0  0  0
sda5     0  0  0
sda1     0  0  0         /mnt/boot-sav/sda1


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4012124k,nr_inodes=1003031,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=805544k,mode=755)
/dev/sdb on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=27e19d29eadfb239)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=10023)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=805544k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  acpi_thermal_rel autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 ecryptfs fb0 fd full fuse gpiochip0 hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdb2 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 3c 90 6d 6b 66 73 2e  66 61 74 00 02 04 01 00  |.<.mkfs.fat.....|
00000010  02 00 02 00 13 f8 04 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  00 00 00 00 80 00 29 46  c4 61 e5 4e 4f 20 4e 41  |......)F.a.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 32 20 20 20 0e 1f  |ME    FAT12   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fe 54 68 69 73 20  |^..2.......This |
00000060  69 73 20 6e 6f 74 20 61  20 62 6f 6f 74 61 62 6c  |is not a bootabl|
00000070  65 20 64 69 73 6b 2e 20  20 50 6c 65 61 73 65 20  |e disk.  Please |
00000080  69 6e 73 65 72 74 20 61  20 62 6f 6f 74 61 62 6c  |insert a bootabl|
00000090  65 20 66 6c 6f 70 70 79  20 61 6e 64 0d 0a 70 72  |e floppy and..pr|
000000a0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 74  |ess any key to t|
000000b0  72 79 20 61 67 61 69 6e  20 2e 2e 2e 20 0d 0a 00  |ry again ... ...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     787M  9.7M  778M   2% /run
/dev/sdb       iso9660   1.5G  1.5G     0 100% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
aufs           aufs      3.9G   63M  3.8G   2% /
tmpfs          tmpfs     3.9G  6.8M  3.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  152K  3.9G   1% /tmp
tmpfs          tmpfs     787M   84K  787M   1% /run/user/999
/dev/sda1      ext2      472M   63M  385M  15% /mnt/boot-sav/sda1

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x22eacc1a

Device     Boot   Start        End   Sectors   Size Id Type
/dev/sda1  *       2048     999423    997376   487M 83 Linux
/dev/sda2       1001470 1000214527 999213058 476.5G  5 Extended
/dev/sda5       1001472 1000214527 999213056 476.5G 83 Linux


Disk /dev/sdb: 14.6 GiB, 15610576896 bytes, 30489408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x15e2543d

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *        0 3035519 3035520  1.5G  0 Empty
/dev/sdb2       14432   19295    4864  2.4M ef EFI (FAT-12/16/32)


No OS or WinEFI system
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
/boot detected. Please check the options.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
The boot flag will be placed on sdb2.
Additional repair will be performed:  repair-filesystems


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

fsck -fyM /dev/sda1
fsck from util-linux 2.27.1

fsck -fyM /dev/sda5
fsck from util-linux 2.27.1

fsck -fyM /dev/sdb2
fsck from util-linux 2.27.1
fsck.fat 3.0.28 (2015-05-16)
/dev/sdb2: 4 files, 1195/1205 clusters
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda5 : Error code 32
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32
parted /dev/sdb set 2 boot on
Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
                                                                            parted /dev/sdb set 1 boot off
Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
                                                                            [email]SET@_progressbar1.pulse[/email]()

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by DuckHook on 2017-02-24
Welcome to the forums, mrcapone.

...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by mörgæs on 2017-02-25
The output shows that you are using 16.04.2. 

I assume that you have nothing of value on the SSD now so I suggest that you try installing 17.04 (beta).

---

### Post by netdesk on 2017-03-07
We have issues too with a UX360UAK only booting randomly. Did you have any success?

---

### Post by oldfred on 2017-03-07
You have a new UEFI system and converted it to the 35 year old BIOS/MBR configuration.
While that should still work, you may want to try UEFI.
How you boot install media, UEFI or BIOS is then how it installs and the how you have to boot system.
UEFI also uses the gpt partitioning scheme not the old MBR(msdos).

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Issues are often more common by vendor as UEFI is same, across various similar models.
Asus has needed boot parameter pci=nomsi, the Intel boot parameter was for older Ubuntu and new Intel.

 Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04)
Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)
Asus N550JX Installing 15.04 , boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)

---

