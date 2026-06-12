---
title: "GRUB LEGECY UUID fixing and boot procedure cleanup after disk &quot;dd&quot; copy/clone"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by Akbar_Momin on 2016-01-10
Hi,

I have copied/cloned my 80GB HDD#1(if=/dev/sda) to another 80GB HDD#2(of=/dev/sdb) and trying to boot using HDD#2 while disconnecting HDD#1.

Surprisingly/unexpectedly UBUNTU boots up without problem but other OS (e.g. CENTOS) does not boot from the HDD#2.

My output from the bootinfoscript is at below of the mail. 

I assume UUID is one of the issue. Any support to fix the problem and clean by boot procedure without installing GRUB2 will be very helpful.

Regards,

Akbar

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy0.97 is installed in the MBR of /dev/sda and looks at sector 
    31471616 on boot drive #1 for the stage2 file.  A stage2 file is at this 
    location on /dev/sda.  Stage2 looks on partition #2 for /grub/grub.conf..

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg /grub/grub.conf

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  CentOS release 6.7 (Final) 
                       Kernel on an
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 NTFS / exFAT / HPFS
/dev/sda2          30,717,952    34,715,647     3,997,696  83 Linux
/dev/sda3          34,717,694   156,248,063   121,530,370   5 Extended
/dev/sda5          34,717,696    84,715,519    49,997,824  83 Linux
/dev/sda6          84,717,568   114,714,623    29,997,056  83 Linux
/dev/sda7         114,716,672   144,713,727    29,997,056  83 Linux
/dev/sda8         144,715,776   156,248,063    11,532,288  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6234EAF534EACADD                       ntfs       
/dev/sda2        ce3bf0ea-1c40-4f67-9cb9-63068352f9a7   ext3       
/dev/sda5        e3434b1b-2e49-41b7-bf73-38bcf3abdfc0   ext3       
/dev/sda6        14e2e613-b605-4203-8305-769d82777df2   ext3       
/dev/sda7        291d1729-0c44-4ff4-bffb-b7c3916f685b   ext4       
/dev/sda8        24502bdc-2e3f-4102-923c-3d4250d3f167   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot                    ext3       (rw)
/dev/sda5        /cad                     ext3       (rw)
/dev/sda6        /centos                  ext3       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7 --hint='hd0,msdos7'  291d1729-0c44-4ff4-bffb-b7c3916f685b
else
  search --no-floppy --fs-uuid --set=root 291d1729-0c44-4ff4-bffb-b7c3916f685b
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    else
      search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    fi
    linux    /vmlinuz-3.13.0-74-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.13.0-74-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
    menuentry 'Ubuntu, with Linux 3.13.0-74-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-74-generic ...'
        linux    /vmlinuz-3.13.0-74-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-74-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-74-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-74-generic ...'
        linux    /vmlinuz-3.13.0-74-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-74-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-71-generic ...'
        linux    /vmlinuz-3.13.0-71-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-71-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-71-generic ...'
        linux    /vmlinuz-3.13.0-71-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-71-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-59-generic ...'
        linux    /vmlinuz-3.13.0-59-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-59-generic ...'
        linux    /vmlinuz-3.13.0-59-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /vmlinuz-3.13.0-57-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /vmlinuz-3.13.0-57-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-55-generic ...'
        linux    /vmlinuz-3.13.0-55-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-55-generic ...'
        linux    /vmlinuz-3.13.0-55-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-54-generic ...'
        linux    /vmlinuz-3.13.0-54-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-54-generic ...'
        linux    /vmlinuz-3.13.0-54-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /vmlinuz-3.13.0-53-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /vmlinuz-3.13.0-53-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /vmlinuz-3.13.0-52-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /vmlinuz-3.13.0-52-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /vmlinuz-3.13.0-48-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /vmlinuz-3.13.0-48-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /vmlinuz-3.13.0-45-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /vmlinuz-3.13.0-45-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /vmlinuz-3.13.0-36-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /vmlinuz-3.13.0-36-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /vmlinuz-3.13.0-30-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /vmlinuz-3.13.0-30-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /vmlinuz-3.13.0-29-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /vmlinuz-3.13.0-29-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /vmlinuz-3.13.0-24-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /vmlinuz-3.13.0-24-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-573.3.1.el6.i686' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-573.3.1.el6.i686-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-573.3.1.el6.i686 ...'
        linux    /vmlinuz-2.6.32-573.3.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-573.3.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-573.3.1.el6.i686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-573.3.1.el6.i686-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-573.3.1.el6.i686 ...'
        linux    /vmlinuz-2.6.32-573.3.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-573.3.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.30.3.el6.i686' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-504.30.3.el6.i686-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-504.30.3.el6.i686 ...'
        linux    /vmlinuz-2.6.32-504.30.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-504.30.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.30.3.el6.i686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-504.30.3.el6.i686-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-504.30.3.el6.i686 ...'
        linux    /vmlinuz-2.6.32-504.30.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-504.30.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.16.2.el6.i686' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-504.16.2.el6.i686-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-504.16.2.el6.i686 ...'
        linux    /vmlinuz-2.6.32-504.16.2.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-504.16.2.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.16.2.el6.i686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-504.16.2.el6.i686-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-504.16.2.el6.i686 ...'
        linux    /vmlinuz-2.6.32-504.16.2.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-504.16.2.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.8.1.el6.i686' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-504.8.1.el6.i686-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-504.8.1.el6.i686 ...'
        linux    /vmlinuz-2.6.32-504.8.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-504.8.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.8.1.el6.i686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-504.8.1.el6.i686-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-504.8.1.el6.i686 ...'
        linux    /vmlinuz-2.6.32-504.8.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-504.8.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-431.20.3.el6.i686' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-431.20.3.el6.i686-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-431.20.3.el6.i686 ...'
        linux    /vmlinuz-2.6.32-431.20.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-431.20.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-431.20.3.el6.i686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-431.20.3.el6.i686-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.32-431.20.3.el6.i686 ...'
        linux    /vmlinuz-2.6.32-431.20.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-2.6.32-431.20.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.ELsmp' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.9-89.ELsmp-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.9-89.ELsmp ...'
        linux    /vmlinuz-2.6.9-89.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.6.9-89.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.ELsmp (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.9-89.ELsmp-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.9-89.ELsmp ...'
        linux    /vmlinuz-2.6.9-89.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.6.9-89.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.EL' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.9-89.EL-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.9-89.EL ...'
        linux    /vmlinuz-2.6.9-89.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.6.9-89.EL.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.EL (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.9-89.EL-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.6.9-89.EL ...'
        linux    /vmlinuz-2.6.9-89.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.6.9-89.EL.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.ELsmp' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.4.21-50.ELsmp-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.4.21-50.ELsmp ...'
        linux    /vmlinuz-2.4.21-50.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.4.21-50.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.ELsmp (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.4.21-50.ELsmp-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.4.21-50.ELsmp ...'
        linux    /vmlinuz-2.4.21-50.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.4.21-50.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.EL' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.4.21-50.EL-advanced-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.4.21-50.EL ...'
        linux    /vmlinuz-2.4.21-50.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.4.21-50.EL.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.EL (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.4.21-50.EL-recovery-291d1729-0c44-4ff4-bffb-b7c3916f685b' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        echo    'Loading Linux 2.4.21-50.EL ...'
        linux    /vmlinuz-2.4.21-50.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd-2.4.21-50.EL.img
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    else
      search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    fi
    knetbsd    /memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    else
      search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-6234EAF534EACADD' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  6234EAF534EACADD
    else
      search --no-floppy --fs-uuid --set=root 6234EAF534EACADD
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'CentOS release 6.7 (Final) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-14e2e613-b605-4203-8305-769d82777df2' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    else
      search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
    fi
    linux /vmlinuz-3.13.0-74-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
    initrd /initrd.img-3.13.0-74-generic
}
submenu 'Advanced options for CentOS release 6.7 (Final) (on /dev/sda6)' $menuentry_id_option 'osprober-gnulinux-advanced-14e2e613-b605-4203-8305-769d82777df2' {
    menuentry 'Ubuntu (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-74-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-74-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-74-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-74-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-74-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-74-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-74-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-74-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-74-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-74-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-74-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-71-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-71-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-71-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-71-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-71-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-71-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-59-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-59-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-59-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-59-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-57-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-57-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-57-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-57-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-55-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-55-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-55-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-55-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-54-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-54-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-54-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-54-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-53-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-53-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-53-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-53-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-52-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-52-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-52-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-52-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-48-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-48-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-48-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-48-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-45-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-45-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-45-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-45-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-36-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-36-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-36-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-36-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-30-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-30-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-30-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-30-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-29-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-29-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-29-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-29-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-24-generic--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-24-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.13.0-24-generic-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-3.13.0-24-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-573.3.1.el6.i686 (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-573.3.1.el6.i686--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-573.3.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initramfs-2.6.32-573.3.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-573.3.1.el6.i686 (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-573.3.1.el6.i686-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-573.3.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initramfs-2.6.32-573.3.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.30.3.el6.i686 (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-504.30.3.el6.i686--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-504.30.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initramfs-2.6.32-504.30.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.30.3.el6.i686 (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-504.30.3.el6.i686-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-504.30.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initramfs-2.6.32-504.30.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.16.2.el6.i686 (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-504.16.2.el6.i686--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-504.16.2.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initramfs-2.6.32-504.16.2.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.16.2.el6.i686 (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-504.16.2.el6.i686-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-504.16.2.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initramfs-2.6.32-504.16.2.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.8.1.el6.i686 (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-504.8.1.el6.i686--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-504.8.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initramfs-2.6.32-504.8.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-504.8.1.el6.i686 (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-504.8.1.el6.i686-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-504.8.1.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initramfs-2.6.32-504.8.1.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-431.20.3.el6.i686 (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-431.20.3.el6.i686--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-431.20.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initramfs-2.6.32-431.20.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.32-431.20.3.el6.i686 (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.32-431.20.3.el6.i686-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.32-431.20.3.el6.i686 root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initramfs-2.6.32-431.20.3.el6.i686.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.ELsmp (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.9-89.ELsmp--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.9-89.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd-2.6.9-89.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.ELsmp (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.9-89.ELsmp-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.9-89.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd-2.6.9-89.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.EL (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.9-89.EL--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.9-89.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd-2.6.9-89.EL.img
    }
    menuentry 'Ubuntu, with Linux 2.6.9-89.EL (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.6.9-89.EL-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.6.9-89.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd-2.6.9-89.EL.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.ELsmp (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.4.21-50.ELsmp--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.4.21-50.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd-2.4.21-50.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.ELsmp (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.4.21-50.ELsmp-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.4.21-50.ELsmp root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd-2.4.21-50.ELsmp.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.EL (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.4.21-50.EL--14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.4.21-50.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro quiet splash $vt_handoff
        initrd /initrd-2.4.21-50.EL.img
    }
    menuentry 'Ubuntu, with Linux 2.4.21-50.EL (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-2.4.21-50.EL-root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset-14e2e613-b605-4203-8305-769d82777df2' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        else
          search --no-floppy --fs-uuid --set=root ce3bf0ea-1c40-4f67-9cb9-63068352f9a7
        fi
        linux /vmlinuz-2.4.21-50.EL root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro recovery nomodeset
        initrd /initrd-2.4.21-50.EL.img
    }
}

menuentry 'Red Hat Enterprise Linux AS release 4 (Nahant) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c9ab339b-defd-418b-8cda-afc1dea0ef6c' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  c9ab339b-defd-418b-8cda-afc1dea0ef6c
    else
      search --no-floppy --fs-uuid --set=root c9ab339b-defd-418b-8cda-afc1dea0ef6c
    fi
    linux /boot/vmlinuz-2.6.9-89.ELsmp ro root=LABEL=/ rhgb quiet
    initrd /boot/initrd-2.6.9-89.ELsmp.img
}
submenu 'Advanced options for Red Hat Enterprise Linux AS release 4 (Nahant) (on /dev/sdb1)' $menuentry_id_option 'osprober-gnulinux-advanced-c9ab339b-defd-418b-8cda-afc1dea0ef6c' {
    menuentry 'CentOS-4 (2.6.9-89.ELsmp) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.9-89.ELsmp--c9ab339b-defd-418b-8cda-afc1dea0ef6c' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  c9ab339b-defd-418b-8cda-afc1dea0ef6c
        else
          search --no-floppy --fs-uuid --set=root c9ab339b-defd-418b-8cda-afc1dea0ef6c
        fi
        linux /boot/vmlinuz-2.6.9-89.ELsmp ro root=LABEL=/ rhgb quiet
        initrd /boot/initrd-2.6.9-89.ELsmp.img
    }
    menuentry 'CentOS-4-up (2.6.9-89.EL) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.9-89.EL--c9ab339b-defd-418b-8cda-afc1dea0ef6c' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  c9ab339b-defd-418b-8cda-afc1dea0ef6c
        else
          search --no-floppy --fs-uuid --set=root c9ab339b-defd-418b-8cda-afc1dea0ef6c
        fi
        linux /boot/vmlinuz-2.6.9-89.EL ro root=LABEL=/ rhgb quiet
        initrd /boot/initrd-2.6.9-89.EL.img
    }
}

menuentry 'Red Hat Enterprise Linux AS release 3 (Taroon) (on /dev/sdb2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-8d4745a0-cff8-4687-9148-4b1ba2494a8f' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  8d4745a0-cff8-4687-9148-4b1ba2494a8f
    else
      search --no-floppy --fs-uuid --set=root 8d4745a0-cff8-4687-9148-4b1ba2494a8f
    fi
    linux /boot/vmlinuz-2.4.21-50.ELsmp ro root=/dev/hdc2 hda=ide-scsi
    initrd /boot/initrd-2.4.21-50.ELsmp.img
}
submenu 'Advanced options for Red Hat Enterprise Linux AS release 3 (Taroon) (on /dev/sdb2)' $menuentry_id_option 'osprober-gnulinux-advanced-8d4745a0-cff8-4687-9148-4b1ba2494a8f' {
    menuentry 'CentOS-3 (2.4.21-50.ELsmp) (on /dev/sdb2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.4.21-50.ELsmp--8d4745a0-cff8-4687-9148-4b1ba2494a8f' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  8d4745a0-cff8-4687-9148-4b1ba2494a8f
        else
          search --no-floppy --fs-uuid --set=root 8d4745a0-cff8-4687-9148-4b1ba2494a8f
        fi
        linux /boot/vmlinuz-2.4.21-50.ELsmp ro root=/dev/hdc2 hda=ide-scsi
        initrd /boot/initrd-2.4.21-50.ELsmp.img
    }
    menuentry 'CentOS-3-up (2.4.21-50.EL) (on /dev/sdb2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.4.21-50.EL--8d4745a0-cff8-4687-9148-4b1ba2494a8f' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  8d4745a0-cff8-4687-9148-4b1ba2494a8f
        else
          search --no-floppy --fs-uuid --set=root 8d4745a0-cff8-4687-9148-4b1ba2494a8f
        fi
        linux /boot/vmlinuz-2.4.21-50.EL ro root=/dev/hdc2 hda=ide-scsi
        initrd /boot/initrd-2.4.21-50.EL.img
    }
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

============================= sda2/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/sda6
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.32-573.3.1.el6.i686)
    root (hd0,1)
    kernel /vmlinuz-2.6.32-573.3.1.el6.i686 ro root=UUID=14e2e613-b605-4203-8305-769d82777df2 rd_NO_LUKS LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 rd_NO_DM rd_NO_LVM  KEYBOARDTYPE=pc KEYTABLE=de rhgb quiet crashkernel=auto
    initrd /initramfs-2.6.32-573.3.1.el6.i686.img
title CentOS (2.6.32-504.30.3.el6.i686)
    root (hd0,1)
    kernel /vmlinuz-2.6.32-504.30.3.el6.i686 ro root=UUID=14e2e613-b605-4203-8305-769d82777df2 rd_NO_LUKS LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 rd_NO_DM rd_NO_LVM  KEYBOARDTYPE=pc KEYTABLE=de rhgb quiet crashkernel=auto
    initrd /initramfs-2.6.32-504.30.3.el6.i686.img
title Ubuntu
    root (hd0,1)
    kernel    /vmlinuz-3.13.0-29-generic root=UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.13.0-29-generic
title WinXP
    rootnoverify (hd0,0)
    chainloader +1
title CentOS-3.9 (2.4.21-50.ELsmp)
    root (hd0,1)
    kernel /vmlinuz-2.4.21-50.ELsmp ro root=/dev/sdb2 rhgb quiet
    initrd /initrd-2.4.21-50.ELsmp.img
title CentOS 4.8 (2.6.9-89.ELsmp)
    root (hd0,1)
    kernel /vmlinuz-2.6.9-89.ELsmp ro root=/dev/sdb1 rhgb quiet
    initrd /initrd-2.6.9-89.ELsmp.img
title CentOS 6.5 (2.6.32-431.20.3.el6.i686)
    root (hd0,1)
    kernel /vmlinuz-2.6.32-431.20.3.el6.i686 ro root=UUID=14e2e613-b605-4203-8305-769d82777df2 rd_NO_LUKS LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 rd_NO_DM rd_NO_LVM  KEYBOARDTYPE=pc KEYTABLE=de rhgb quiet crashkernel=auto
    initrd /initramfs-2.6.32-431.20.3.el6.i686.img
title CentOS 6.5 (2.6.32-504.8.1.el6.i686)
    root (hd0,1)
    kernel /vmlinuz-2.6.32-504.8.1.el6.i686 ro root=UUID=14e2e613-b605-4203-8305-769d82777df2 rd_NO_LUKS LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 rd_NO_DM rd_NO_LVM  KEYBOARDTYPE=pc KEYTABLE=de rhgb quiet crashkernel=auto
    initrd /initramfs-2.6.32-504.8.1.el6.i686.img
title CentOS 6.5 (2.6.32-504.16.2.el6.i686)
    root (hd0,1)
    kernel /vmlinuz-2.6.32-504.16.2.el6.i686 ro root=UUID=14e2e613-b605-4203-8305-769d82777df2 rd_NO_LUKS LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 rd_NO_DM rd_NO_LVM  KEYBOARDTYPE=pc KEYTABLE=de rhgb quiet crashkernel=auto
    initrd /initramfs-2.6.32-504.16.2.el6.i686.img

--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Wed Jun 11 01:36:34 2014
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=14e2e613-b605-4203-8305-769d82777df2    /                      ext3    defaults        1 1
UUID=ce3bf0ea-1c40-4f67-9cb9-63068352f9a7     /boot                   ext3    defaults        1 2
UUID=e3434b1b-2e49-41b7-bf73-38bcf3abdfc0     /cad                   ext3    defaults        1 2
UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b     /ubuntu                  ext4    defaults        0 2
UUID=24502bdc-2e3f-4102-923c-3d4250d3f167     swap                     swap    defaults        0 0
#
tmpfs                               /dev/shm                tmpfs   defaults        0 0
devpts                              /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                               /sys                    sysfs   defaults        0 0
proc                                /proc                   proc    defaults        0 0
#
UUID=c9ab339b-defd-418b-8cda-afc1dea0ef6c     /mnt/centos4        ext3    defaults        0 3
UUID=8d4745a0-cff8-4687-9148-4b1ba2494a8f     /mnt/centos3            ext3    defaults        0 3
UUID=e4d6d146-8026-4061-9974-0faabc2c6cfe     /mnt/TEMP               ext3    defaults        1 3
UUID=c449f220-b792-4465-bda9-a0807ff8a5cf     /mnt/CAD                ext3    defaults        1 3
#
#/dev/sdb1                     /mnt/centos4        ext3    defaults        0 3
#/dev/sdb2                     /mnt/centos3            ext3    defaults        0 3
#/dev/sdb5                     /mnt/TEMP               ext3    defaults        1 3
#/dev/sdb6                     /mnt/CAD                ext3    defaults        1 3
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
UUID=291d1729-0c44-4ff4-bffb-b7c3916f685b     /        ext4    errors=remount-ro 1       1
UUID=ce3bf0ea-1c40-4f67-9cb9-63068352f9a7     /boot           ext3    defaults        1       2
UUID=e3434b1b-2e49-41b7-bf73-38bcf3abdfc0     /cad            ext3    defaults        1       2
UUID=14e2e613-b605-4203-8305-769d82777df2     /centos          ext3    defaults        1       2
UUID=24502bdc-2e3f-4102-923c-3d4250d3f167     none            swap    sw              0       0
#
UUID=c9ab339b-defd-418b-8cda-afc1dea0ef6c     /mnt/centos4        ext3    defaults        0 3
UUID=8d4745a0-cff8-4687-9148-4b1ba2494a8f     /mnt/centos3            ext3    defaults        0 3
UUID=e4d6d146-8026-4061-9974-0faabc2c6cfe     /mnt/TEMP               ext3    defaults        1 3
UUID=c449f220-b792-4465-bda9-a0807ff8a5cf     /mnt/CAD                ext3    defaults        1 3
#
#/dev/sdb1                     /mnt/centos4        ext3    defaults        0 3
#/dev/sdb2                     /mnt/centos3            ext3    defaults        0 3
#/dev/sdb5                     /mnt/TEMP               ext3    defaults        1 3
#/dev/sdb6                     /mnt/CAD                ext3    defaults        1 3
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-FMvQc6Lz/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-FMvQc6Lz/Tmp_Log: No such file or directory
```

---

### Post by oldfred on 2016-01-10
Your grub2 grub.cfg shows the Centos.
But it looks like you used the same /boot for both installs. That almost never will work as you get conflicts.
With standard desktop, generally better just not to use /boot as separate partition and keep it in the/ (root) partition. 
You Centos may default to LVM and separate /boot, but I do not think that is required. Best not to use LVM unless entire drive is LVM.
You may also want to house clean some kernels. Menu looks long.

I would just install grub2 from system you boot the most to MBR.
You can reconfigure by copying /boot back into / , remove /boot entry in fstab and reinstalling grub2.

       [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

