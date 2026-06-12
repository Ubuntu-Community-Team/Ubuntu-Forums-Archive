---
title: "MBR and GRUB installation"
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by ethanp3 on 2016-11-28
Hello, everyone!

So I've been using Ubuntu (16.04.1) here for about a week now and have just learned enough to make myself dangerous to my system.  I originally installed Ubuntu alongside Windows 10 (not a Wubi) and now was wanting to remove my windows operating system.
Through looking around and reading, it seems like the best way to do this (aside from a clean install) is to use Gparted to repartition the windows and windows recovery partition into ext4 (I've made a pack-up of my windows data).  However, I found that before doing this it is best to discover where GRUB is installed first.

I ran a boot info script to see where it would be installed at, and it came back with the results saying I don't have a boot loader installed in the MBR.  Below is the RESULTS.TXT.  I'm unsure really how to best read the results and was hoping to have some help from those who know much more than I do! :D  My system is a Lenovo-Flex14 laptop, and I haven't had any problems with booting.  When I power up, I receive the Lenovo screen and then the system boots into GRUB, allowing me to select if I want to boot Ubuntu or into Windows boot manager.  

At this point:

[LIST]
[*]Can you see where GRUB is installed? 
[*]Do I need to install GRUB to MBR? 
[*]Can I delete my windows system from the dual boot at this point without worrying about accidentally dusting GRUB in the process? 
[/LIST]

Thank you in advance for your help, and let me know if there is any information I can get to you!




                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /bootmgr /boot/bcd

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,630,527     2,048,000 -
/dev/sda4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,892,672   451,606,149   446,713,478 Data partition (Windows/Linux)
/dev/sda6     901,459,968   953,888,767    52,428,800 Data partition (Windows/Linux)
/dev/sda7     953,888,768   976,773,119    22,884,352 Windows Recovery Environment (Windows)
/dev/sda8     451,606,528   893,253,631   441,647,104 Data partition (Linux)
/dev/sda9     893,253,632   901,459,967     8,206,336 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3E8CB5608CB5137F                       ntfs       WINRE_DRV
/dev/sda2        6AB7-CDA9                              vfat       SYSTEM_DRV
/dev/sda3        B8BC-FF8C                              vfat       LRS_ESP
/dev/sda4                                                          
/dev/sda5        4262C08462C07E63                       ntfs       Windows8_OS
/dev/sda6        D6CC503ECC501B57                       ntfs       LENOVO
/dev/sda7        2E40C5A040C56F61                       ntfs       PBR_DRV
/dev/sda8        44b5bfed-3a3d-4c14-b91e-30f944e64a9e   ext4       
/dev/sda9        17c7ce85-d729-4cf6-a4f9-e8a2e91d55a5   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda8        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)


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
insmod part_gpt
insmod ext2
set root='hd0,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
else
  search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
    else
      search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
    fi
    linux    /boot/vmlinuz-4.4.0-47-generic root=UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-47-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
    menuentry 'Ubuntu, with Linux 4.4.0-47-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-47-generic-advanced-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        else
          search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        fi
        echo    'Loading Linux 4.4.0-47-generic ...'
        linux    /boot/vmlinuz-4.4.0-47-generic root=UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-47-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-47-generic-init-upstart-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        else
          search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        fi
        echo    'Loading Linux 4.4.0-47-generic ...'
        linux    /boot/vmlinuz-4.4.0-47-generic root=UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-47-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-47-generic-recovery-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        else
          search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        fi
        echo    'Loading Linux 4.4.0-47-generic ...'
        linux    /boot/vmlinuz-4.4.0-47-generic root=UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-advanced-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        else
          search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic.efi.signed root=UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-init-upstart-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        else
          search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic.efi.signed root=UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-recovery-44b5bfed-3a3d-4c14-b91e-30f944e64a9e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        else
          search --no-floppy --fs-uuid --set=root 44b5bfed-3a3d-4c14-b91e-30f944e64a9e
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic.efi.signed root=UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-6AB7-CDA9' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  6AB7-CDA9
    else
      search --no-floppy --fs-uuid --set=root 6AB7-CDA9
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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
UUID=44b5bfed-3a3d-4c14-b91e-30f944e64a9e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=6AB7-CDA9  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda9 during installation
UUID=17c7ce85-d729-4cf6-a4f9-e8a2e91d55a5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
e7afbfbf4fa38a449a5b6213eb736c22
Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 1f 00  |........?....H..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 a9 cd b7 6a 4e  4f 20 4e 41 4d 45 20 20  |..)...jNO NAME  |
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

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 6e 10  |.X.MSDOS5.0...n.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 27 00  |........?....h'.|
00000020  00 40 1f 00 c9 07 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 8c ff bc b8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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

cat: /tmp/BootInfo-mjB0GgLy/Tmp_Log: No such file or directory
```

---

### Post by Dennis N on 2016-11-28
Some comments that may help out:

You have UEFI installations. The Grub bootloader to boot Ubuntu is in the EFI system partition (which is sda2 - see line 97 of output), inside the folder 'ubuntu'. 

The Windows boot loader is also placed in the EFI system partition in a separate folder.

Be sure not to remove the EFI system partition (sda2), the Linux partition (sda8) or the swap if you decide to reformat for reuse, or remove any windows-related partitions. 

You don't need to install grub anywhere - its current installation should still be working to boot up Ubuntu.

---

### Post by oldfred on 2016-11-28
Please use code tags if posting a lot of text or terminal output.
Easy to add with # icon in forum's advanced editor.
Also generally better to use Boot-Repair's summary report which includes more data and provides link to pastebin site.

But you have UEFI system and UEFI installs. So you do not have a BIOS boot loader nor grub installed to MBR. Gpt only has protective MBR for older software that is not gpt aware. That software not seeing gpt, might offer incorrectly to reformat drive. MBR then has one entry for entire drive saying it is gpt. 

As long as you can boot ubuntu entry from UEFI boot menu, so have no issues.
But some brands restrict booting to one description "Windows Boot Manager" and then we have to do work arounds to boot grub/Ubuntu.

---

