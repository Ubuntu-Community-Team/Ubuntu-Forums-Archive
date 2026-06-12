---
title: "Can't Boot Ubuntu Using NeoGrubs Bootloader external hard drive"
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by jordan19 on 2014-04-04
Please help.. I have a mid 2010 Macbook pro 15 inch.. I have windows and OSX running on it.. I'm trying to install Ubuntu onto my external hard drive. That was successful however I can't get it to boot up when starting my Mac.. My problem is very similar to this guy's ubuntuforums.org/showthread.php?t=1036463.

I'm trying to use easybcd or neogrub to get the job done.. I tried configuring REFIT on the mac then launching linux but it kept loading winows instead.. My problems are exactly like this guy as I said ubuntuforums.org/showthread.php?t=1036463.

I ran a boot info script from the live cd. Here are the results

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640   291,841,607   291,431,968  af HFS / HFS+
/dev/sda3         291,841,608   293,111,143     1,269,536  ab Darwin boot
/dev/sda4    *    293,111,808   625,141,759   332,029,952   7 NTFS / exFAT / HPFS


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640   291,841,607   291,431,968 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda3     291,841,608   293,111,143     1,269,536 Apple Boot partition (Mac OS X)
/dev/sda4     293,111,808   625,141,759   332,029,952 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   287,082,126   287,080,079  83 Linux
/dev/sdc2         287,082,494   312,580,095    25,497,602   5 Extended
/dev/sdc5         287,082,496   312,580,095    25,497,600  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        70D6-1701                              vfat       EFI
/dev/sda2        8efa2875-b1c7-310d-9327-8de900c88860   hfsplus    Untitled
/dev/sda3        a68783c5-ea53-3dc5-baf3-f8cdb9f03c1b   hfsplus    Recovery HD
/dev/sda4        80BEDB14BEDB0218                       ntfs       BOOTCAMP
/dev/sdc1        691d35a0-4901-4f85-9963-6a30fea05db7   ext3       
/dev/sdc5        7701040c-a145-48a5-b6b7-eb15c7f00e72   swap       
/dev/sr0                                                iso9660    Ubuntu 13.10 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/ubuntu/691d35a0-4901-4f85-9963-6a30fea05db7 ext3       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
insmod part_msdos
insmod ext2
set root='hd2,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  691d35a0-4901-4f85-9963-6a30fea05db7
else
  search --no-floppy --fs-uuid --set=root 691d35a0-4901-4f85-9963-6a30fea05db7
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-691d35a0-4901-4f85-9963-6a30fea05db7' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  691d35a0-4901-4f85-9963-6a30fea05db7
    else
      search --no-floppy --fs-uuid --set=root 691d35a0-4901-4f85-9963-6a30fea05db7
    fi
    linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=691d35a0-4901-4f85-9963-6a30fea05db7 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-12-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-691d35a0-4901-4f85-9963-6a30fea05db7' {
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-691d35a0-4901-4f85-9963-6a30fea05db7' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  691d35a0-4901-4f85-9963-6a30fea05db7
        else
          search --no-floppy --fs-uuid --set=root 691d35a0-4901-4f85-9963-6a30fea05db7
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=691d35a0-4901-4f85-9963-6a30fea05db7 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-691d35a0-4901-4f85-9963-6a30fea05db7' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  691d35a0-4901-4f85-9963-6a30fea05db7
        else
          search --no-floppy --fs-uuid --set=root 691d35a0-4901-4f85-9963-6a30fea05db7
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=691d35a0-4901-4f85-9963-6a30fea05db7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  691d35a0-4901-4f85-9963-6a30fea05db7
    else
      search --no-floppy --fs-uuid --set=root 691d35a0-4901-4f85-9963-6a30fea05db7
    fi
    linux16    /boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  691d35a0-4901-4f85-9963-6a30fea05db7
    else
      search --no-floppy --fs-uuid --set=root 691d35a0-4901-4f85-9963-6a30fea05db7
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Mac OS X (32-bit) (on /dev/sda2)' --class osx --class darwin --class os $menuentry_id_option 'osprober-xnu-32-2fa40591334c70ce'  {
    insmod part_gpt
    insmod hfsplus
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  2fa40591334c70ce
    else
      search --no-floppy --fs-uuid --set=root 2fa40591334c70ce
    fi
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 2fa40591334c70ce uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           if [ /kernelcache -nt /System/Library/Extensions ]; then
              xnu_kernel /kernelcache boot-uuid=${uuid} rd=*uuid
           else
              xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
              if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
                xnu_mkext /System/Library/Extensions.mkext
              else
                xnu_kextdir /System/Library/Extensions
              fi
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry 'Mac OS X (64-bit) (on /dev/sda2)' --class osx --class darwin --class os $menuentry_id_option 'osprober-xnu-64-2fa40591334c70ce'  {
    insmod part_gpt
    insmod hfsplus
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  2fa40591334c70ce
    else
      search --no-floppy --fs-uuid --set=root 2fa40591334c70ce
    fi
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 2fa40591334c70ce uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           if [ /kernelcache -nt /System/Library/Extensions ]; then
              xnu_kernel64 /kernelcache boot-uuid=${uuid} rd=*uuid
           else
              xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
              if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
                xnu_mkext /System/Library/Extensions.mkext
              else
                xnu_kextdir /System/Library/Extensions
              fi
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry 'Windows 8 (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-80BEDB14BEDB0218' {
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  80BEDB14BEDB0218
    else
      search --no-floppy --fs-uuid --set=root 80BEDB14BEDB0218
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc1 during installation
UUID=691d35a0-4901-4f85-9963-6a30fea05db7 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=7701040c-a145-48a5-b6b7-eb15c7f00e72 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 01 17 d6 70 45  46 49 20 20 20 20 20 20  |..)...pEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc2

00000000  38 3a 41 00 00 00 00 00  02 00 00 00 e3 48 00 00  |8:A..........H..|
00000010  fc ff ff ff ff ff ff ff  9d 3a 41 00 00 00 00 00  |.........:A.....|
00000020  0b 00 00 00 72 00 00 00  00 00 00 00 00 00 00 00  |....r...........|
00000030  af 3a 41 00 00 00 00 00  02 00 00 00 c5 27 00 00  |.:A..........'..|
00000040  fc ff ff ff ff ff ff ff  13 3b 41 00 00 00 00 00  |.........;A.....|
00000050  0b 00 00 00 07 00 00 00  80 f0 0b 00 00 00 00 00  |................|
00000060  1f 3d 41 00 00 00 00 00  02 00 00 00 b7 4a 00 00  |.=A..........J..|
00000070  fc ff ff ff ff ff ff ff  40 3e 41 00 00 00 00 00  |........@>A.....|
00000080  02 00 00 00 fb 04 00 00  fc ff ff ff ff ff ff ff  |................|
00000090  53 40 41 00 00 00 00 00  02 00 00 00 0f 3c 00 00  |S@A..........<..|
000000a0  fc ff ff ff ff ff ff ff  63 40 41 00 00 00 00 00  |........c@A.....|
000000b0  02 00 00 00 19 3d 00 00  fc ff ff ff ff ff ff ff  |.....=..........|
000000c0  75 40 41 00 00 00 00 00  02 00 00 00 78 3d 00 00  |u@A.........x=..|
000000d0  fc ff ff ff ff ff ff ff  91 40 41 00 00 00 00 00  |.........@A.....|
000000e0  02 00 00 00 38 3a 00 00  fc ff ff ff ff ff ff ff  |....8:..........|
000000f0  16 42 41 00 00 00 00 00  02 00 00 00 bb 3c 00 00  |.BA..........<..|
00000100  fc ff ff ff ff ff ff ff  36 44 41 00 00 00 00 00  |........6DA.....|
00000110  02 00 00 00 0f 3c 00 00  fc ff ff ff ff ff ff ff  |.....<..........|
00000120  57 44 41 00 00 00 00 00  02 00 00 00 38 3a 00 00  |WDA.........8:..|
00000130  fc ff ff ff ff ff ff ff  ab 44 41 00 00 00 00 00  |.........DA.....|
00000140  02 00 00 00 19 3d 00 00  fc ff ff ff ff ff ff ff  |.....=..........|
00000150  bd 44 41 00 00 00 00 00  02 00 00 00 78 3d 00 00  |.DA.........x=..|
00000160  fc ff ff ff ff ff ff ff  aa 46 41 00 00 00 00 00  |.........FA.....|
00000170  0b 00 00 00 04 00 00 00  03 13 01 00 00 00 00 00  |................|
00000180  c4 46 41 00 00 00 00 00  0b 00 00 00 04 00 00 00  |.FA.............|
00000190  17 13 01 00 00 00 00 00  f7 46 41 00 00 00 00 00  |.........FA.....|
000001a0  0b 00 00 00 05 00 00 00  18 c7 00 00 00 00 00 00  |................|
000001b0  85 47 41 00 00 00 00 00  0b 00 00 00 05 00 00 fe  |.GA.............|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 10 85 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-PQ3qSwcP/Tmp_Log: No such file or directory
  No volume groups found
```

---

### Post by oldfred on 2014-04-04
I do not know Macs. They do have some work around to use Windows in BIOS mode with hybrid MBR/gpt partitioning as Windows only boots with BIOS.
But Ubuntu can boot with UEFI. And Some systems will not boot with EasyBCD in UEFI mode.
And all systems will only boot in the same mode as you start booting, so if you start with BIOS you must boot in BIOS or if you start in UEFI you must boot system in UEFI. 

Most with Macs find rEFInd works the best. The old refit has not been maintained.

       MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)

            [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)

    
 [https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

