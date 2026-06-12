---
title: "&quot;Kernel Panic - not syncing&quot; after upgrade"
date: 2014-05-29
forum: Installation &amp; Upgrades
---

### Post by csmilovitz on 2014-05-29
There's a old topic with this title already but my problem is different.  I try and start the newest ubuntu (on /dev/sda5) and it fails with "kernel panic - not syncing" and "VFS: Unable to mount root fs on unknown block (0,0)."  Importantly, all of the old ubuntu versions in the same partition (on the options submenu) still boot and looking at e from the grub2 boot menu for each option show they all say the same thing (except for the UUID).  That is, they all point to hd0,msdos5 which should be correct.

Is the problem the UUID?  How did that get messed up?

The operating system is in /dev/sda5
I'd like to attach bootinfo, but the paperclip icon comes up "404 not found nginx".  Here's my bootinfo:
```

 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

<sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 120820632 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for .
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/lilo.conf 
                       /boot/extlinux/extlinux.conf /boot/map

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     2,459,647     2,457,600   7 NTFS / exFAT / HPFS
/dev/sda2    *      2,459,648    94,619,647    92,160,000   7 NTFS / exFAT / HPFS
/dev/sda3         291,074,048   312,579,759    21,505,712   7 NTFS / exFAT / HPFS
/dev/sda4          94,620,960   291,059,999   196,439,040   5 Extended
/dev/sda5          94,621,696   135,581,695    40,960,000  83 Linux
/dev/sda6         135,583,744   291,059,711   155,475,968   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3E42C9D942C99655                       ntfs       SYSTEM_DRV
/dev/sda2        68B4CC1BB4CBE9A0                       ntfs       Windows7_OS
/dev/sda3        8078CF3978CF2D2A                       ntfs       Lenovo_Recovery
/dev/sda5        f791ca7f-bafd-4e4f-8266-595ef5a7c1a1   ext4       linux
/dev/sda6        3CBCE55941C06B79                       ntfs       NewVolume2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /media/craig/NewVolume2  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
else
  search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
    else
      search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-20-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-20-generic ...'
        linux    /boot/vmlinuz-3.11.0-20-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-20-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-20-generic ...'
        linux    /boot/vmlinuz-3.11.0-20-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-19-generic ...'
        linux    /boot/vmlinuz-3.11.0-19-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-19-generic ...'
        linux    /boot/vmlinuz-3.11.0-19-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-17-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-17-generic ...'
        linux    /boot/vmlinuz-3.11.0-17-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-17-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-17-generic ...'
        linux    /boot/vmlinuz-3.11.0-17-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-15-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-15-generic ...'
        linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-15-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.11.0-15-generic ...'
        linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-45-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.5.0-45-generic ...'
        linux    /boot/vmlinuz-3.5.0-45-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-45-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.5.0-45-generic ...'
        linux    /boot/vmlinuz-3.5.0-45-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-57-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-57-generic ...'
        linux    /boot/vmlinuz-3.2.0-57-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-57-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-57-generic ...'
        linux    /boot/vmlinuz-3.2.0-57-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-56-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-56-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-56-generic ...'
        linux    /boot/vmlinuz-3.2.0-56-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-56-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-56-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-56-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-56-generic ...'
        linux    /boot/vmlinuz-3.2.0-56-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-56-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-55-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-55-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-55-generic ...'
        linux    /boot/vmlinuz-3.2.0-55-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-55-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-55-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-55-generic ...'
        linux    /boot/vmlinuz-3.2.0-55-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-54-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-54-generic ...'
        linux    /boot/vmlinuz-3.2.0-54-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-54-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-54-generic ...'
        linux    /boot/vmlinuz-3.2.0-54-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-53-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-53-generic ...'
        linux    /boot/vmlinuz-3.2.0-53-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-53-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-53-generic ...'
        linux    /boot/vmlinuz-3.2.0-53-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-51-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-51-generic ...'
        linux    /boot/vmlinuz-3.2.0-51-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-51-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-51-generic ...'
        linux    /boot/vmlinuz-3.2.0-51-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-49-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-49-generic ...'
        linux    /boot/vmlinuz-3.2.0-49-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-49-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.2.0-49-generic ...'
        linux    /boot/vmlinuz-3.2.0-49-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.0.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-32-generic-advanced-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.0.0-32-generic ...'
        linux    /boot/vmlinuz-3.0.0-32-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.0.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-32-generic-recovery-f791ca7f-bafd-4e4f-8266-595ef5a7c1a1' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        else
          search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
        fi
        echo    'Loading Linux 3.0.0-32-generic ...'
        linux    /boot/vmlinuz-3.0.0-32-generic root=UUID=f791ca7f-bafd-4e4f-8266-595ef5a7c1a1 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
    else
      search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
    else
      search --no-floppy --fs-uuid --set=root f791ca7f-bafd-4e4f-8266-595ef5a7c1a1
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3E42C9D942C99655' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3E42C9D942C99655
    else
      search --no-floppy --fs-uuid --set=root 3E42C9D942C99655
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-68B4CC1BB4CBE9A0' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  68B4CC1BB4CBE9A0
    else
      search --no-floppy --fs-uuid --set=root 68B4CC1BB4CBE9A0
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_os-prober.old ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3E42C9D942C99655' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3E42C9D942C99655
    else
      search --no-floppy --fs-uuid --set=root 3E42C9D942C99655
    fi
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-68B4CC1BB4CBE9A0' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  68B4CC1BB4CBE9A0
    else
      search --no-floppy --fs-uuid --set=root 68B4CC1BB4CBE9A0
    fi
    chainloader +1
}
### END /etc/grub.d/30_os-prober.old ###

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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=6f60f4e6-1182-41d1-8713-01630c6fc54e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=d20f8811-fdfd-4eb3-9e6c-cb82b19d5bd4 none            swap    sw              0       0
UUID=0EDC81CB1C407392              /media/NewVolume      ntfs-3g    defaults,exec,fmask=000    0 0--------------------------------------------------------------------------------

============================= sda5/etc/lilo.conf: ==============================

--------------------------------------------------------------------------------
# /etc/lilo.conf  -   systemwide LILO configuration (LILO 23)
# details see in manpages: lilo(8) and lilo.conf(5)

# +-------------------------------------------------------------+
# |                        !! Reminder !!                       |
# |                                                             |
# | Don't forget to run 'lilo' after you make changes to this   |
# | conffile or you have installed a new kernel.                |
# +-------------------------------------------------------------+


# #################### LILO global section ######################

# With all newer systems (until year 2004) you can use the RAM
# above 15 MB. This option allows the use of this range of RAM.
#large-memory

# With all newer systems you can boot from any partition on disks 
# with more than 1024 cylinders. This option allows the use of 
# partitions above 1024 cylinders.
lba32

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
# With newer kernel you should use the ID of the boot device, which
# can be found here: /dev/disks/by-id/ata*.
#boot = /dev/sda
boot = /dev/disk/by-id/ata-WDC_WD5000BPVT-00HXZT3_WD-WX61E8242165

# This option may be needed for some software RAID installs.
#raid-extra-boot = mbr-only

# Enable map compaction.  This tries to merge read requests for 
# adjacent sectors into a single read request. This drastically 
# reduces load time and keeps the map smaller.  Using 'compact' 
# is especially recommended when booting from a floppy disk.  
# It is disabled here by default because it doesn't always work.
#compact

# Set the verbose level for bootloader installation. Value range:
# 0 to 5. Default value is 0.
#verbose = 1

# Specifies the location of the map file. Lilo creates the (sector) 
# map file of direct sector addresses which are independent of any
# filesystem.
map = /boot/map

# ---------------------------------------------------------------

# Specifies the menu interface. You have the choice between:
#   text: simple text menu with black background and white text
#   menu: configurable text menu with background and text colors.
#   bmp:  graphical menu with 640x480 bitmap background.
install = menu

# A) Customized boot message for choice 'text'.
# For the simple text menu you can set an extra message in the 
# created file. Its text will be displayed before boot prompt.
#message = /boot/message.txt

# B) Configuration of the scheme for choice 'menu'.
# Use following coding: <text>:<highlight>:<border>:<title>
# The first character of each part sets the text frontcolor, 
# the second character of earch part sets the text backcolor,
# an upper-case character sets bold face text (frontcolor).
# i.g. 'menu-scheme=wm:rw:wm:Wm'. Possible colors: 
# k=black, b=blue, g=green, c=cyan, r=red, m=magenta, y=yellow, w=white.
menu-scheme = Wb:Yr:Wb:Wb
#menu-title = " DESDEMONA Boot-Manager "

# C) Configuration of the image for choice 'bmp'.
# For the graphical menu you need a bitmap file, which needs a special
# menu configuration in the file header (see: lilo -E). Ideally you 
# use one of the delivered images of the lilo package.
#   with 16 colors:    onlyblue, tuxlogo, inside
#   with 256 colors:   coffee
#   for Debian:        debianlilo, debian, debian-de
#bitmap = /boot/tuxlogo.bmp

# ---------------------------------------------------------------

# Specifies the number of deciseconds (0.1 seconds) how long LILO 
# should wait before booting the first image.  LILO doesn't wait if
# 'delay' is omitted or set to zero. You do not see the defined menu.
#delay = 20

# Prompt to start one certain kernel from the displayed menu.
# It is very recommeded to also set 'timeout'. Without timeout boot 
# will not take place unless you hit return. Timeout is the number
# of deciseconds (0.1 seconds) after there the default image will 
# be started. With 'single-key' alias numbers for each menu line can
# be used.
prompt
timeout = 100
#single-key

# ---------------------------------------------------------------

# Specifying the VGA text mode that should be selected when booting.
# The following values are recognized (case is ignored):
#   vga=normal    80x25 text mode (default)
#   vga=extended  80x50 text mode (abbreviated to 'ext')
#   vga=ask       stop and ask for user input: choice of text mode
#   vga=<mode>    use the corresponding text mode number. A list of  
#                   available modes can be obtained by booting with  
#                   vga=ask'  and then pressing [Enter].
# Another way is the use of frame buffer mode. Then the kernel 
# will switch from the normal vga text mode (80x25) to the frame
# buffer mode (if frame buffer support is in the kernel):
#   vga=0x314      800x600 @ 16 bit
#   vga=0x317     1024x768 @ 16 bit
#   vga=0x318     1024x768 @ 24 bit
#vga = ask
vga = normal
#vga = 0x317

# ---------------------------------------------------------------

# Kernel command line options that apply to all installed images go
# here.  See 'kernel-parameters.txt' in the Linux kernel 'Documentation'
# directory. I.g. for start into 'init 5' write:  append="5"
#append = ""
 
# If you used a serial console to install Debian, this option should be
# enabled by default.
#serial = 0,9600

# Set the image which should be started after delay or timeout.
# If not set, the first defined image will be started.
#default = Linux


# ################### LILO per-image section ####################

# Each image is configured with the linux kernel (=image) and
# usually with the initrd file. Configure all GNU/Linux systems
# on other partitions, too.

image = /boot/vmlinuz-3.11.0-17-generic
    label = "Linux"
    #root = /dev/sda8
    root = "UUID=6f60f4e6-1182-41d1-8713-01630c6fc54e"
    read-only
#    restricted
#    alias = 1
#    optional
    initrd = /boot/initrd.img-3.11.0-17-generic

image = /boot/vmlinuz-3.11.0-15-generic
    label = "Linux Old"
    #root = /dev/sda8
    root = "UUID=6f60f4e6-1182-41d1-8713-01630c6fc54e"
    read-only
#    restricted
#    alias = 2
#    optional
    initrd = /boot/initrd.img-3.11.0-15-generic

--------------------------------------------------------------------------------

====================== sda5/boot/extlinux/extlinux.conf: =======================

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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sda5: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sda5: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-dCgVqqtM/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-dCgVqqtM/Tmp_Log: No such file or directory
```


Craig

---

### Post by csmilovitz on 2014-05-30
Sorry to bother people.  Things seem to have fixed themselves.  While the error condition lasted a few days, I turned things on this morning and everything seems fine.  The most recent ubuntu on the grub2 menu boots and "lsb_release -a" reports the correct "ubuntu 14.04 LTS" as description and "14.04" as version.

I share the computer with the rest of my family so I have no idea what fixed things.  It's unlikely that anyone else would have intentionally done things to fix things.  I'm the only administrator or computer tinkerer around here.

I'd mark the thread as solved but I can't find how to do it.

---

