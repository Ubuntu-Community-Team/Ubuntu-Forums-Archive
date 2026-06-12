---
title: "No boot loader is installed in the MBR of /dev/sdb"
date: 2016-07-07
forum: Installation &amp; Upgrades
---

### Post by afagarap on 2016-07-07
Good day! This is my first post here in Ubuntu Forums, first time to ask. I have a problem regarding my bootloader. Instead of the GRUB menu showing up when I turn on my laptop, the minimal bash shows up. I used ```
 bootinfoscript 
``` and the following was what I got:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    46580288 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Deepin GNU/Linux 2015
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Deepin Desktop 15.1/grubx64.efi

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048   294,389,759   294,387,712 Data partition (Linux)
/dev/sda2     294,389,760   588,482,559   294,092,800 Data partition (Linux)
/dev/sda3     588,482,560   903,055,359   314,572,800 Data partition (Linux)
/dev/sda4     903,055,360   905,152,511     2,097,152 EFI System partition
/dev/sda5   1,223,954,432 1,465,149,134   241,194,703 Data partition (Linux)
/dev/sda6     905,152,512   913,541,119     8,388,608 Swap partition (Linux)
/dev/sda7     913,541,120 1,223,954,431   310,413,312 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1    46,905,263    46,905,263  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048        98,303        96,256 EFI System partition

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        395515a0-2c3e-48d3-9bef-8d908175d06e   ext4       
/dev/sda2        4a0b3e74-9f3e-4c7e-916f-7ab7cfd09d0f   ext4       Data
/dev/sda3        c5d79230-8513-43c9-80fc-59c4d3c89a1d   ext4       
/dev/sda4        9EDE-ACB0                              vfat       
/dev/sda5        9a0fdfcd-6b8b-40eb-9b84-3345629a8712   ext4       Data
/dev/sda6        8eb6dd21-32a3-4ff5-a6eb-c3abab4e1a5c   swap       
/dev/sda7        eb7ced19-5e5b-4475-a00a-63fe859e4955   ext4       
/dev/sdb1        1044-22EE                              vfat       
/dev/sr1                                                iso9660    Ubuntu 14.04.3 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


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
insmod part_gpt
insmod ext2
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
else
  search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-395515a0-2c3e-48d3-9bef-8d908175d06e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
    else
      search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
    fi
    linux    /boot/vmlinuz-3.13.0-88-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-88-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-395515a0-2c3e-48d3-9bef-8d908175d06e' {
    menuentry 'Ubuntu, with Linux 3.13.0-88-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-88-generic-advanced-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-88-generic ...'
        linux    /boot/vmlinuz-3.13.0-88-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-88-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-88-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-88-generic-recovery-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-88-generic ...'
        linux    /boot/vmlinuz-3.13.0-88-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-88-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-87-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-87-generic-advanced-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-87-generic ...'
        linux    /boot/vmlinuz-3.13.0-87-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-87-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-87-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-87-generic-recovery-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-87-generic ...'
        linux    /boot/vmlinuz-3.13.0-87-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-87-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-advanced-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-recovery-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-83-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-83-generic-advanced-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-83-generic ...'
        linux    /boot/vmlinuz-3.13.0-83-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-83-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-83-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-83-generic-recovery-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-83-generic ...'
        linux    /boot/vmlinuz-3.13.0-83-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-83-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-79-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-79-generic-advanced-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-79-generic ...'
        linux    /boot/vmlinuz-3.13.0-79-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-79-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-79-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-79-generic-recovery-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        echo    'Loading Linux 3.13.0-79-generic ...'
        linux    /boot/vmlinuz-3.13.0-79-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-79-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Deepin 15.2  (15.2) (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
    else
      search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
    fi
    linux /boot/vmlinuz-4.4.0-2-deepin-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro splash quiet
    initrd /boot/initrd.img-4.4.0-2-deepin-amd64
}
submenu 'Advanced options for Deepin 15.2  (15.2) (on /dev/sda3)' $menuentry_id_option 'osprober-gnulinux-advanced-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
    menuentry 'Deepin 15.2 GNU/Linux (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-2-deepin-amd64--c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        linux /boot/vmlinuz-4.4.0-2-deepin-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro splash quiet
        initrd /boot/initrd.img-4.4.0-2-deepin-amd64
    }
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.4.0-2-deepin-amd64 (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-2-deepin-amd64--c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        linux /boot/vmlinuz-4.4.0-2-deepin-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro splash quiet
        initrd /boot/initrd.img-4.4.0-2-deepin-amd64
    }
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.4.0-2-deepin-amd64 (recovery mode) (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-2-deepin-amd64-root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro recovery-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        linux /boot/vmlinuz-4.4.0-2-deepin-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro recovery
        initrd /boot/initrd.img-4.4.0-2-deepin-amd64
    }
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.2.0-1-amd64 (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.2.0-1-amd64--c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        linux /boot/vmlinuz-4.2.0-1-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro splash quiet
        initrd /boot/initrd.img-4.2.0-1-amd64
    }
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.2.0-1-amd64 (recovery mode) (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.2.0-1-amd64-root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro recovery-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        linux /boot/vmlinuz-4.2.0-1-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro recovery
        initrd /boot/initrd.img-4.2.0-1-amd64
    }
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
UUID=395515a0-2c3e-48d3-9bef-8d908175d06e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=1044-22EE  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb2 during installation
# UUID=5b0fc267-c430-42bf-86fc-663681e3223c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
   set default="Deepin 15.1.1 GNU/Linux"
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
set root='hd0,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
else
  search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=1366x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='hd0,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
else
  search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
fi
insmod gfxmenu
loadfont ($root)/boot/grub/themes/deepin/unifont-regular-16.pf2
insmod png
set theme=($root)/boot/grub/themes/deepin/theme.txt
export theme
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=1
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=1
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_gpt
insmod ext2
set root='hd0,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
else
  search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
fi
insmod png
if background_image /boot/grub/themes/deepin/background.png; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
}
set linux_gfx_mode=
export linux_gfx_mode
menuentry 'Deepin 15.2 GNU/Linux' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
    load_video
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
    else
      search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
    fi
    echo    'Loading Linux 4.4.0-2-deepin-amd64 ...'
    linux    /boot/vmlinuz-4.4.0-2-deepin-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro  splash quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-4.4.0-2-deepin-amd64
}
submenu 'Advanced options for Deepin 15.2 GNU/Linux' $menuentry_id_option 'gnulinux-advanced-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.4.0-2-deepin-amd64' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-2-deepin-amd64-advanced-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        echo    'Loading Linux 4.4.0-2-deepin-amd64 ...'
        linux    /boot/vmlinuz-4.4.0-2-deepin-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro  splash quiet
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-2-deepin-amd64
    }
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.4.0-2-deepin-amd64 (recovery mode)' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-2-deepin-amd64-recovery-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        echo    'Loading Linux 4.4.0-2-deepin-amd64 ...'
        linux    /boot/vmlinuz-4.4.0-2-deepin-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro recovery 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-2-deepin-amd64
    }
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.2.0-1-amd64' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-1-amd64-advanced-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        echo    'Loading Linux 4.2.0-1-amd64 ...'
        linux    /boot/vmlinuz-4.2.0-1-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro  splash quiet
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-1-amd64
    }
    menuentry 'Deepin 15.2 GNU/Linux, with Linux 4.2.0-1-amd64 (recovery mode)' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-1-amd64-recovery-c5d79230-8513-43c9-80fc-59c4d3c89a1d' {
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  c5d79230-8513-43c9-80fc-59c4d3c89a1d
        else
          search --no-floppy --fs-uuid --set=root c5d79230-8513-43c9-80fc-59c4d3c89a1d
        fi
        echo    'Loading Linux 4.2.0-1-amd64 ...'
        linux    /boot/vmlinuz-4.2.0-1-amd64 root=UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d ro recovery 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-1-amd64
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 14.04 LTS (14.04) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-395515a0-2c3e-48d3-9bef-8d908175d06e' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
    else
      search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
    fi
    linux /boot/vmlinuz-3.13.0-88-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-88-generic
}
submenu 'Advanced options for Ubuntu 14.04 LTS (14.04) (on /dev/sda1)' $menuentry_id_option 'osprober-gnulinux-advanced-395515a0-2c3e-48d3-9bef-8d908175d06e' {
    menuentry 'Ubuntu (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-88-generic.efi.signed--395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-88-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-88-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-88-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-88-generic.efi.signed--395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-88-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-88-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-88-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-88-generic.efi.signed-root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-88-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-88-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-87-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-87-generic.efi.signed--395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-87-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-87-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-87-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-87-generic.efi.signed-root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-87-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-87-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-85-generic.efi.signed--395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-85-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-85-generic.efi.signed-root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-85-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-83-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-83-generic.efi.signed--395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-83-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-83-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-83-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-83-generic.efi.signed-root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-83-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-83-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-79-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-79-generic.efi.signed--395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-79-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-79-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-79-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-79-generic.efi.signed-root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset-395515a0-2c3e-48d3-9bef-8d908175d06e' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  395515a0-2c3e-48d3-9bef-8d908175d06e
        else
          search --no-floppy --fs-uuid --set=root 395515a0-2c3e-48d3-9bef-8d908175d06e
        fi
        linux /boot/vmlinuz-3.13.0-79-generic.efi.signed root=UUID=395515a0-2c3e-48d3-9bef-8d908175d06e ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-79-generic
    }
}

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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /dev/sda3
UUID=c5d79230-8513-43c9-80fc-59c4d3c89a1d    /             ext4          rw,relatime,data=ordered    0 1

# /dev/sda7
UUID=eb7ced19-5e5b-4475-a00a-63fe859e4955    /home         ext4          rw,relatime,data=ordered    0 2

# /dev/sda4
UUID=9EDE-ACB0          /boot/efi     vfat          rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=utf8,shortname=mixed,errors=remount-ro    0 2

# /dev/sda6
UUID=8eb6dd21-32a3-4ff5-a6eb-c3abab4e1a5c    none          swap          defaults      0 0

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-y5if9Ydr/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-y5if9Ydr/Tmp_Log: No such file or directory
  No volume groups found


```

I hope you guys could help me. Thank you very much in advance.

My /boot and / are in the same partition, not separate partition. Could I still re-install GRUB?

---

### Post by grahammechanical on 2016-07-07
You need to explain your setup for us.

As far as I can see Grub is installed into the MBR of sda. But should it be? There are efi boot files in sdb1. Are they for Ubuntu or Deepin? According to my understanding when an OS is installed in EFI mode then grub is not installed into the MBR. The grub boot files go into a special efi_boot partition that is usually on the same drive as the OS. The boot files for more than one OS can go into the same efi_boot partition.

Which OS was installed last? Ubuntu or Deepin? 

It is my guess that Ubuntu was installed first and it was installed in EFI mode. I have no idea why its boot files should be in an efi_boot partition on sdb when Ubuntu is on sda. It is also my guess the Deepin was installed in BIOS/Legacy/CSM mode and it is the Deepin version of Grub that is installed in the MBR of sda.

If one OS is installed in EFI mode then every other OS must also be installed in EFI. If the first OS is installed in BIOS mode then all other OS must be installed in BIOS mode. If we do not follow this rule then there are problems with loading each OS.

It is my guess that the Grub configuration file (grub.cfg) that boot info script is showing us is the Ubuntu Grub configuration file but the Grub that is broken is the Deepin Grub. Does Deepin load?

Direct the UEFI settings utility to load from sdb. That might get you loading Ubuntu and Deepin but it will all depend on whether the motherboard is in EFI mode or BIOS mode. That is the complication that come with mixing motherboard boot modes.

Regards.

---

### Post by oldfred on 2016-07-07
Ubuntu's grub only installs to the ESP - efi system partition on sda.
Did drives change boot order?

And Ubuntu installed to a gpt partitioned drive will require a bios_grub partition. I thought it added it, but if you used manual partitioning and then did not create either the ESP for UEFI or bios_grub for BIOS, grub will not install.

While I still run bootinfoscript as part of my backup to document my system, I use a newer fork that works better. An even better is the Summary Repair from Boot-Repair which also uses the newer version of bootinfosript as part of the report.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

      [/URL]
 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 
    [URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by Dennis N on 2016-07-07
The history of all the installation activity undertaken would help. I infer from the display that you installed Ubuntu first. And that worked OK? Was that in BIOS mode? GPT with a BIOS install should have had a bios_grub partition - now missing*. Then did you install Deepin? That is a UEFI install. If inferences are correct, you should not mix install modes. Unexplained is an EFI system partition on sdb1 with Ubuntu files! Could running a boot repair session have done that? 

*will it go through without it?

---

