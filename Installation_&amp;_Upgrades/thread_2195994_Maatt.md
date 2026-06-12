---
title: "Maatt"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by matchubee on 2013-12-27
Hello! Nice to be able to post for my first time ever to all of you. I am a returning Ubuntu user with just basic experience and I know I have a long way to go. I installed Ubuntu 13.10 64-bit with upgrades at the time of install to dual boot with Win 7 on a Sony Vaio laptop. Win 7 works fine, but I could not boot Ubuntu yet. I get the following message:
Gave up waiting for root device. Alert! /dev/disk/by-uuid/xxx...does not exist. Dropping to a shell! Busy Box v1.20.2 (Ubuntu 1:1.20.0-8.1 | Ubuntu) built-in shell (ash).....(intramfs).
I tried a lot of different things from other posts, but nothing worked so far. I finally downloaded Bootinfoscript from a suggestion in another post, and am now posting the results for anyone to help me out here. Thanks a lot in advance. :D
                  Boot Info Script 0.61      [1 April 2012]


```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    23,267,327    23,265,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     23,267,328    23,472,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          23,472,128   896,980,991   873,508,864   7 NTFS / exFAT / HPFS
/dev/sda4         896,983,038 1,250,263,039   353,280,002   5 Extended
/dev/sda5       1,233,670,144 1,250,263,039    16,592,896  82 Linux swap / Solaris
/dev/sda6         896,983,040 1,233,670,143   336,687,104  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders, total 501759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  99       501,247       501,149   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AC1C56AE1C567376                       ntfs       Recovery
/dev/sda2        884A3A974A3A81CC                       ntfs       System Reserved
/dev/sda3        01CEFF98670FE590                       ntfs       
/dev/sda5        7b701f11-8543-448b-9774-a695d8fa4b15   swap       
/dev/sda6        1aea10a5-afd7-4667-99c6-aec0cc95ec34   ext4       
/dev/sdb1        F4D6-85AC                              vfat       NEW VOLUME
/dev/sr0                                                iso9660    Ubuntu 13.10 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ubuntu/F4D6-85AC  vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1aea10a5-afd7-4667-99c6-aec0cc95ec34
else
  search --no-floppy --fs-uuid --set=root 1aea10a5-afd7-4667-99c6-aec0cc95ec34
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
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1aea10a5-afd7-4667-99c6-aec0cc95ec34' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1aea10a5-afd7-4667-99c6-aec0cc95ec34
    else
      search --no-floppy --fs-uuid --set=root 1aea10a5-afd7-4667-99c6-aec0cc95ec34
    fi
    linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=1aea10a5-afd7-4667-99c6-aec0cc95ec34 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-12-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-1aea10a5-afd7-4667-99c6-aec0cc95ec34' {
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-1aea10a5-afd7-4667-99c6-aec0cc95ec34' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1aea10a5-afd7-4667-99c6-aec0cc95ec34
        else
          search --no-floppy --fs-uuid --set=root 1aea10a5-afd7-4667-99c6-aec0cc95ec34
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=1aea10a5-afd7-4667-99c6-aec0cc95ec34 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-1aea10a5-afd7-4667-99c6-aec0cc95ec34' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1aea10a5-afd7-4667-99c6-aec0cc95ec34
        else
          search --no-floppy --fs-uuid --set=root 1aea10a5-afd7-4667-99c6-aec0cc95ec34
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=1aea10a5-afd7-4667-99c6-aec0cc95ec34 ro recovery nomodeset 
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
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1aea10a5-afd7-4667-99c6-aec0cc95ec34
    else
      search --no-floppy --fs-uuid --set=root 1aea10a5-afd7-4667-99c6-aec0cc95ec34
    fi
    linux16    /boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1aea10a5-afd7-4667-99c6-aec0cc95ec34
    else
      search --no-floppy --fs-uuid --set=root 1aea10a5-afd7-4667-99c6-aec0cc95ec34
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-AC1C56AE1C567376' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  AC1C56AE1C567376
    else
      search --no-floppy --fs-uuid --set=root AC1C56AE1C567376
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-884A3A974A3A81CC' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  884A3A974A3A81CC
    else
      search --no-floppy --fs-uuid --set=root 884A3A974A3A81CC
    fi
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-01CEFF98670FE590' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  01CEFF98670FE590
    else
      search --no-floppy --fs-uuid --set=root 01CEFF98670FE590
    fi
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
UUID=1aea10a5-afd7-4667-99c6-aec0cc95ec34 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7b701f11-8543-448b-9774-a695d8fa4b15 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-pLXNmZcU/Tmp_Log: No such file or directory
  No volume groups found
```

---

