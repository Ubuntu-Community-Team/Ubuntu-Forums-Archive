---
title: "kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by andreaconsole on 2016-05-15
Good morning,
I know that it's a common problem and I already read the related topics, but I still don't know how to proceed.
Prior my last shutdown, I started receiving warnings about some file not writable in /home, but I didn't take note of it.
However, on next boot, I found myself in troubles with kernel panic.
I tried to use the second kernel, but it lead me to initramfs (I don't know what it means).
Fortunately, I have a live version on USB stick, so I booted from it.
The following is the result of bootinfo script. 
You can see
- sda, that is the hd with kubuntu OS (it's a temporary installation on an old hd, which includes also a not-working windows partition; I'm using it while waiting for the replacement of my SSD);
- sdb, that is the data backup hd, which also has a windows partition on it (dual boot)
- sdc, the USB stick I'm using in this very moment.

How can I fix the boot error? Thanks

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........u.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1892372 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   406,241,302   406,241,240   7 NTFS / exFAT / HPFS
/dev/sda2         406,243,326   625,139,711   218,896,386   5 Extended
/dev/sda5         406,243,328   613,271,551   207,028,224  83 Linux
/dev/sda6         613,273,600   625,139,711    11,866,112  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    30,716,279    30,714,232   c W95 FAT32 (LBA)
/dev/sdb2          30,716,280   186,996,599   156,280,320   7 NTFS / exFAT / HPFS
/dev/sdb3         186,996,661   625,135,615   438,138,955   f W95 Extended (LBA)
/dev/sdb5         186,998,784   625,135,615   438,136,832   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 3.8 GiB, 4022337024 bytes, 7856127 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,856,126     7,856,064   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B60CFB8A0CFB4441                       ntfs       
/dev/sda5        3a38ab26-5673-4a44-9b6f-ee29c49728b5   ext4       
/dev/sda6        9f36bc82-002f-421c-ba7b-35629092076b   swap       
/dev/sdb1        3C98-AC5D                              vfat       RECOVERY
/dev/sdb2        AA2ABDE92ABDB2A5                       ntfs       OS
/dev/sdb5        3B11B7A307666FCD                       ntfs       data
/dev/sdc1        B47E-4829                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/kubuntu/B60CFB8A0CFB4441 fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda5        /media/kubuntu/3a38ab26-5673-4a44-9b6f-ee29c49728b5 ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb2        /media/kubuntu/OS        fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
else
  search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3a38ab26-5673-4a44-9b6f-ee29c49728b5' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
    else
      search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
    fi
    linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=3a38ab26-5673-4a44-9b6f-ee29c49728b5 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3a38ab26-5673-4a44-9b6f-ee29c49728b5' {
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-advanced-3a38ab26-5673-4a44-9b6f-ee29c49728b5' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
        else
          search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=3a38ab26-5673-4a44-9b6f-ee29c49728b5 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-recovery-3a38ab26-5673-4a44-9b6f-ee29c49728b5' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
        else
          search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=3a38ab26-5673-4a44-9b6f-ee29c49728b5 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-3a38ab26-5673-4a44-9b6f-ee29c49728b5' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
        else
          search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=3a38ab26-5673-4a44-9b6f-ee29c49728b5 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-3a38ab26-5673-4a44-9b6f-ee29c49728b5' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
        else
          search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=3a38ab26-5673-4a44-9b6f-ee29c49728b5 ro recovery nomodeset 
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
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
    else
      search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  3a38ab26-5673-4a44-9b6f-ee29c49728b5
    else
      search --no-floppy --fs-uuid --set=root 3a38ab26-5673-4a44-9b6f-ee29c49728b5
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-B60CFB8A0CFB4441' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  B60CFB8A0CFB4441
    else
      search --no-floppy --fs-uuid --set=root B60CFB8A0CFB4441
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-3C98-AC5D' {
    insmod part_msdos
    insmod fat
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  3C98-AC5D
    else
      search --no-floppy --fs-uuid --set=root 3C98-AC5D
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sdb2)' --class windows --class os $menuentry_id_option 'osprober-chain-AA2ABDE92ABDB2A5' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  AA2ABDE92ABDB2A5
    else
      search --no-floppy --fs-uuid --set=root AA2ABDE92ABDB2A5
    fi
    parttool ${root} hidden-
    chainloader +1
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=3a38ab26-5673-4a44-9b6f-ee29c49728b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9f36bc82-002f-421c-ba7b-35629092076b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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

menuentry "Start Kubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/kubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --- persistent

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry1
menu label ^Start Kubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity  quiet splash --- persistent

label ubnentry2
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --- persistent

label ubnentry3
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

label ubnentry4
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry5
menu label Start Kubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --- persistent

label ubnentry6
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/kubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --- persistent

label ubnentry7
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --- persistent

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-1j01SVtE/Tmp_Log: No such file or directory
/home/kubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-1j01SVtE/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-1j01SVtE/Tmp_Log: No such file or directory



```

---

### Post by andreaconsole on 2016-05-15
Well, I was finally able to boot from my older kernel following these indications
[http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox)

What's next? And mainly: what's happening to my installation? After fixing it, will it happen again in a few days?

---

### Post by andreaconsole on 2016-05-15
trying to reinstall my latest kernel:
[FONT=monospace][COLOR=#000000]dpkg --list | grep linux-image
to find my latest kernel name
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]sudo update-initramfs -u -k 4.4.0-22-generic[/COLOR]
[/FONT]to install it
[FONT=monospace][COLOR=#000000]sudo update-grub[/COLOR]
[/FONT]to update grub.

Rebooting...
wish me luck

Ok, it worked, everything is fine now, BUT
am I going to face this issue again? The hd smart function says it is ok: what happened?

---

### Post by poltiser2 on 2016-05-15
In Xubuntu 64 16.04 I had the same problem - kernel 4.5.3 -> 4.5.4 - same problem. Some updates. I delete the session and save the new one. Rebooted from console. Problem vanished. I don't really know why. :D
Now everything works - as it was working well in spite of the error message and hanging on shut-down... but now no messages. Back to normal.
Best regards.

---

### Post by andreaconsole on 2016-05-15
Here again...
After a while, my hd goes to read-only mode (I guess, since I start receiving warnings about files that are impossible to write).
On the restart, I have again the issue with bad superblocks to fix
After a while, this cicle restarts...
What the heck is happening?

---

### Post by ubfan1 on 2016-05-15
I does sound like a bad disk.  Is the hd smart funciton the smartctl -a  report?  smartctl in in the smartmontools package.  That should indicate a disk failing.  Did you run (or have it automatically run) the fsck on the disk?  That should indicate/fix any filesystem problem.

---

### Post by andreaconsole on 2016-05-16
I'm not sure about that, it's like something were corrupting always the same area.
As a matter of fact, smartctl keep saying that the hdd is ok:
```

smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-21-generic] (local build)                                                                                                                     
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org                                                                                                                     
                                                                                                                                                                                                
=== START OF INFORMATION SECTION ===                                                                                                                                                            
Model Family:     Western Digital Blue Mobile                                                                                                                                                   
Device Model:     WDC WD3200LPVX-22V0TT0                                                                                                                                                        
Serial Number:    WD-WX21A2307716                                                                                                                                                               
LU WWN Device Id: 5 0014ee 658a42b96                                                                                                                                                            
Firmware Version: 01.01A01                                                                                                                                                                      
User Capacity:    320,072,933,376 bytes [320 GB]                                                                                                                                                
Sector Sizes:     512 bytes logical, 4096 bytes physical                                                                                                                                        
Rotation Rate:    5400 rpm                                                                                                                                                                      
Device is:        In smartctl database [for details use: -P show]                                                                                                                               
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon May 16 20:18:59 2016 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                ( 7380) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  85) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x7035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1771
  3 Spin_Up_Time            0x0027   150   143   021    Pre-fail  Always       -       1458
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1844
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1330
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       309
191 G-Sense_Error_Rate      0x0032   001   001   000    Old_age   Always       -       127
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       74
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       4785
194 Temperature_Celsius     0x0022   108   090   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1284         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

I also run the short test and this is the result:
```

kubuntu@kubuntu:~$ sudo smartctl -l selftest /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-21-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1330         -
# 2  Short offline       Completed without error       00%      1284         -

```

I'm still waiting for the new ssd; in the meantime I'm suffering with this annoying situation :/

---

### Post by andreaconsole on 2016-05-16
something more:
```

sudo fsck */dev/sda5
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda5: clean, 270417/6471680 files, 7152473/25878528 blocks

```

```

kubuntu@kubuntu:~$ sudo fsck /dev/sda5 -f
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 270417/6471680 files (0.2% non-contiguous), 7152473/25878528 blocks

```

Do you know any other way for me to understand what's happening?

---

### Post by ubfan1 on 2016-05-16
Backup that disk as soon as possible.  If you know a bad file, you might identify it's data blocks with hdparm --fibmap, and try to copy them with dd, but the one time I tried that on an SSD which started giving me trouble, even dd would die early with an "IO error".  The SDD only lasted 9 mo before trouble started -- I put the old hard disk back in the machine.  It was an older SSD, so maybe the newer ones handle a frequently modified file better.

---

### Post by pterosky on 2016-10-22
I started up my computer and got this message during boot, with the lights on my keyboard flashing:
> kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)
So I booted up with an earlier  linux images, which worked fine and tried to update the computer with this command:
```
$ sudo apt update
```
It gave me this information:
```
Ign https://deb.opera.com stable/non-free Translation-en_US
Ign https://deb.opera.com stable/non-free Translation-en
Fetched 4.845 kB in 3s (1.582 kB/s)           
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
So I ran the command:
```
$ sudo dpkg --configure -a
Setting up linux-headers-4.4.0-45-generic (4.4.0-45.66~14.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
...
done
Setting up linux-image-generic-lts-xenial (4.4.0.45.33) ...
Setting up linux-generic-lts-xenial (4.4.0.45.33) ...
```
And I can now boot up with the latest linux image again.

---

