---
title: "xubuntu won't boot after initial install - help the linux newbie!"
date: 2016-05-29
forum: Installation &amp; Upgrades
---

### Post by NotGeoff on 2016-05-29
System Info I think is relevant:
AMD FX-4170 Zambezi 4.2GHz processor
GIGABYTE GA-970A-D3 motherboard (rev1.1) with most recent BIOS
PNY CS1311 SSD 120GB

Ok, let me start from the beginning. A friend talked me into dual booting xubuntu because my Windows 10 install is having issues lately. I ordered a new 120gb ssd to dedicate to it. I downloaded the Xubuntu ISO and created a bootable USB "live CD" using Rufus. I turned off the computer then I unplugged the hard drive with my Windows install on it and plugged the new ssd into a different spot. I booted from the live usb, told it to "erase disk and install xubuntu". I did not check "download updates" or "install third party software". It finished without incident and told me to reboot. I did. When it booted, it sat at a black screen for about a minute, then it gave me the message, "error: attempt to read or write outside of disk 'hd0'. Press any key to continue..." and freezes. Pressing keys does nothing. If I let it sit long enough, sometimes I get some other info dump that ends with, "unable to mount root fs on unknown block (0,0)".

I looked around for some answers and found bootinfoscript on sourceforge. Here's what it outputs:

```
                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => No known boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 is already mounted or /tmp/BootInfo-mlmeBZfr/sdb1 busy


sdb2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 2410708. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 is already mounted or /tmp/BootInfo-mlmeBZfr/sdb1 busy
mount: /dev/sdb2 is already mounted or /tmp/BootInfo-mlmeBZfr/sdb2 busy


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048   217,702,399   217,700,352  83 Linux
/dev/sda2         217,704,446   234,440,703    16,736,258   5 Extended
/dev/sda5         217,704,448   234,440,703    16,736,256  82 Linux swap / Solaris




Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 3.7 GiB, 3926949888 bytes, 7669824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *              0     2,424,831     2,424,832   0 Empty
/dev/sdb2           2,410,708     2,415,443         4,736  ef EFI (FAT-12/16/32)


/dev/sdb1 overlaps with /dev/sdb2


GUID Partition Table detected, but does not seem to be used.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1               0     2,424,775     2,424,776 Data partition (Windows/Linux)
/dev/sdb2       2,410,708     2,415,443         4,736 Data partition (Windows/Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        7737feeb-364a-4b85-937d-778628d25bc0   ext4       
/dev/sda5        4531dc82-647f-4a0f-939f-a02bb4a815f4   swap       
/dev/sdb1        2016-04-20-22-41-45-00                 iso9660    Xubuntu 16.04 LTS amd64
/dev/sdb2        B1F5-0A13                              vfat       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)




=========================== sda1/boot/grub/grub.cfg: ===========================


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7737feeb-364a-4b85-937d-778628d25bc0
else
  search --no-floppy --fs-uuid --set=root 7737feeb-364a-4b85-937d-778628d25bc0
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-7737feeb-364a-4b85-937d-778628d25bc0' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7737feeb-364a-4b85-937d-778628d25bc0
    else
      search --no-floppy --fs-uuid --set=root 7737feeb-364a-4b85-937d-778628d25bc0
    fi
    linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=7737feeb-364a-4b85-937d-778628d25bc0 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-21-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-7737feeb-364a-4b85-937d-778628d25bc0' {
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-7737feeb-364a-4b85-937d-778628d25bc0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7737feeb-364a-4b85-937d-778628d25bc0
        else
          search --no-floppy --fs-uuid --set=root 7737feeb-364a-4b85-937d-778628d25bc0
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=7737feeb-364a-4b85-937d-778628d25bc0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-7737feeb-364a-4b85-937d-778628d25bc0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7737feeb-364a-4b85-937d-778628d25bc0
        else
          search --no-floppy --fs-uuid --set=root 7737feeb-364a-4b85-937d-778628d25bc0
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=7737feeb-364a-4b85-937d-778628d25bc0 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-7737feeb-364a-4b85-937d-778628d25bc0' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7737feeb-364a-4b85-937d-778628d25bc0
        else
          search --no-floppy --fs-uuid --set=root 7737feeb-364a-4b85-937d-778628d25bc0
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=7737feeb-364a-4b85-937d-778628d25bc0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7737feeb-364a-4b85-937d-778628d25bc0
    else
      search --no-floppy --fs-uuid --set=root 7737feeb-364a-4b85-937d-778628d25bc0
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7737feeb-364a-4b85-937d-778628d25bc0
    else
      search --no-floppy --fs-uuid --set=root 7737feeb-364a-4b85-937d-778628d25bc0
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
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


=============================== sda1/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=7737feeb-364a-4b85-937d-778628d25bc0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4531dc82-647f-4a0f-939f-a02bb4a815f4 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




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
000001b0  ac 92 24 00 00 00 00 00  59 2e c4 4c 00 00 80 00  |..$.....Y..L....|
000001c0  01 00 00 49 e0 ff 00 00  00 00 00 00 25 00 00 fe  |...I........%...|
000001d0  ff ff ef fe ff ff d4 c8  24 00 80 12 00 00 00 00  |........$.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
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
000001b0  ac 92 24 00 00 00 00 00  59 2e c4 4c 00 00 80 00  |..$.....Y..L....|
000001c0  01 00 00 49 e0 ff 00 00  00 00 00 00 25 00 00 fe  |...I........%...|
000001d0  ff ff ef fe ff ff d4 c8  24 00 80 12 00 00 00 00  |........$.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-mlmeBZfr/Tmp_Log: No such file or directory



```

Any help you can provide would be much appreciated!!! :D

---

### Post by oldfred on 2016-05-29
May be IOMMU settings in UEFI & boot parameter?

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU in UEFI and in grub when booting iommu=soft 
  If permanent setting add this to quiet splash to /etc/default/grub: GRUB_CMD_LINUX_DEFAULT="iommu=soft"

 [http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by NotGeoff on 2016-05-29
I tried toggling the IOMMU setting, but no change. It was initially set to disabled, if that makes a difference. Also, since I'm a linux noob, I'm not sure how to set GRUB_CMDLiNE_LINUX="iommu=soft"...


EDIT: I think I figured out the command thing. I went into GRUB, hit e to edit the thing and added GRUB_CMDLINE_LINUX="iommu=soft" right after "loadvideo" then hit f10 to boot, but had the same result.

---

### Post by oldos2er on 2016-05-29
Moved to Installation & Upgrades.

---

### Post by NotGeoff on 2016-05-29
> **oldos2er said:**
> Moved to Installation & Upgrades.

Oops. Sorry. My bad.

---

### Post by NotGeoff on 2016-05-29
[IMG]http://s33.postimg.org/9bmr8ca7j/20160529_190812.jpg[/IMG]

Here's the info dump. Not sure if this is helpful at all.

---

### Post by oldfred on 2016-05-29
This is editing grub so it is a permanent change.
GRUB_CMDLINE_LINUX="iommu=soft"

If manually editing the boot stanza then you replace quiet splash with iommu=soft.

I have not understood it setting in UEFI is on or off. The various threads have mostly just said change and have not made it clear. Or different versions of UEFI are not exactly the same.

And in grub it is GRUB_CMD_LINUX, I will edit post above just in case someone else sees this.

 sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by NotGeoff on 2016-05-30
Ok, I tried all four permutations of EFI/Non-EFI and iommu enabled/disabled on the motherboard with "quiet splash" replaced with "iommu=soft" in the boot stanza. All came to the same result as before, crash. 
(I may be showing my computer-ineptness a little too much when I say that nothing in my motherboard settings mentions UEFI, only EFI. The motherboard is 4 years old, not sure if that's a new thing or what. You don't have to explain it to me, I'm just trying to give you as much information as possible :)

I had a thought that may end up being useless, but nonetheless, here it is: When I was creating the live boot USB stick with Rufus on Windows 10, the log said something to the effect of "some links are symbolic and will not be copied due to file system differences, which may cause some of the ISOs features to become unusable." Do you think burning the ISO to a DVD and installing that way would be beneficial or do you feel the problem lies elsewhere?

Are we having fun yet?! xD

---

### Post by oldfred on 2016-05-30
It does sound like Rufus did not then make correct flash drive.
I thought Rufus was one of the better tools to make flash drives.

This shows a variety of installer for all systems.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I would try another installer.
But sometimes it is the flash drive, and sometimes it is just the phase of the moon.

Some systems need additional boot parameters also. 
With Gigabyte you need the iommu, with with nVidia you normally need nomodeset.

I have an older nVidia card 620GT. And always had to use nomodeset. But with the newer versions it has worked without the nomodeset.
If AMD video it may also need nomodeset, but I do not know AMD.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by NotGeoff on 2016-05-30
I formatted the hard drive and reinstalled using a DVD burned from the ISO. It's still not booting correctly. It just sits at a blank, black screen until I power it down. Same blank, black screen when I modify the boot stanza with the iommu=soft trick from before, same with nomodeset. Then I tried all the ones suggested by ubfan1 on [http://ubuntuforums.org/showthread.p...0#post12871710]("http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"). All perpetual blackness.

After 3 days of this, I have to admit I'm losing hope :|

Oh and I have a Radeon video card :\ XFX Double D Radeon HD 6950 2GB

---

### Post by oldfred on 2016-05-31
Are you using both iommu=soft nomodeset in place of quiet splash?
Then you may see boot process and where it stops. Usually last line posted is not issue, but several lines above.

What video card/chip do you have?

---

### Post by NotGeoff on 2016-05-31
I had a super techy friend come over and try to help me out since he has lots of experience with linux. We tried everything he could think of and got no where. I've decided to give up on this endeavor until I get a new computer. Thanks for all your help.

---

