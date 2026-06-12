---
title: "Windows 7 not added to GRUB menu"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by ninjashby on 2014-04-21
I am having some trouble using boot-repair to get me back into my windows 7 installation. I have ubuntu 13.10 on the same hard drive. I am running boot-repair from an ubuntu live USB stick.. 

After running boot-repair, i end up grub entries for Ubuntu, memtest, etc but not windows 7. Two interesting lines appear in the boot info summary that I don't know exactly how to deal with: 

/mnt/boot-sav/sda3/ may need repair.
/mnt/boot-sav/sda3/bootmgr may need repair.

Any help is greatly appreciated!

Here is the boot info summary that was generated: 

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

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
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img /boot/burg/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 60876 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63     3,823,469     3,823,407  de Dell Utility
/dev/sda3    *     24,141,824   424,542,207   400,400,384   7 NTFS / exFAT / HPFS
/dev/sda4         526,944,254   976,773,119   449,828,866   5 Extended
/dev/sda5         959,033,344   976,773,119    17,739,776  82 Linux swap / Solaris
/dev/sda6         526,944,256   959,033,343   432,089,088  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8011 MB, 8011087872 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,635,593    15,635,532   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f617713b-984a-9645-bdbe-d5e02b5c20e1   ext2       casper-rw
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda3        F6A03163A0312B8D                       ntfs       OS
/dev/sda5        b2f6f4e4-8c35-4c2c-83dc-9cc2a9ee4b98   swap       
/dev/sda6        b53ff4a6-18b3-47a2-bffb-c79f9204a0f5   ext4       
/dev/sdb1        120C-186F                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt/hd1                 ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
else
  search --no-floppy --fs-uuid --set=root b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b53ff4a6-18b3-47a2-bffb-c79f9204a0f5' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
    else
      search --no-floppy --fs-uuid --set=root b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
    fi
    linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=b53ff4a6-18b3-47a2-bffb-c79f9204a0f5 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-18-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-b53ff4a6-18b3-47a2-bffb-c79f9204a0f5' {
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-advanced-b53ff4a6-18b3-47a2-bffb-c79f9204a0f5' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
        else
          search --no-floppy --fs-uuid --set=root b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=b53ff4a6-18b3-47a2-bffb-c79f9204a0f5 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-recovery-b53ff4a6-18b3-47a2-bffb-c79f9204a0f5' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
        else
          search --no-floppy --fs-uuid --set=root b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=b53ff4a6-18b3-47a2-bffb-c79f9204a0f5 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-18-generic
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
    else
      search --no-floppy --fs-uuid --set=root b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
    fi
    linux16    /boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
    else
      search --no-floppy --fs-uuid --set=root b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
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

menuentry "OS X" {
    insmod hfsplus
    set root="(hd1,gpt2)"
    chainloader /usr/standalone/i386/boot0
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sda6/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux, with Linux 3.11.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
    echo    'Loading Linux 3.11.0-18-generic ...'
    linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=b53ff4a6-18b3-47a2-bffb-c79f9204a0f5 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.11.0-18-generic
}
menuentry 'Ubuntu GNU/Linux, with Linux 3.11.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b53ff4a6-18b3-47a2-bffb-c79f9204a0f5
    echo    'Loading Linux 3.11.0-18-generic ...'
    linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=b53ff4a6-18b3-47a2-bffb-c79f9204a0f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.11.0-18-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
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
UUID=b53ff4a6-18b3-47a2-bffb-c79f9204a0f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b2f6f4e4-8c35-4c2c-83dc-9cc2a9ee4b98 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-PKxpNkbo/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-PKxpNkbo/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-PKxpNkbo/Tmp_Log: No such file or directory
File descriptor 9 (/proc/16786/mounts) leaked on lvscan invocation. Parent PID 26621: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-04-21__12h45 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 13.10, saucy, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed noprompt cdrom-detect/try-usb=true persistent boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda6:Ubuntu 13.10 (13.10):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: LABEL="casper-rw" UUID="f617713b-984a-9645-bdbe-d5e02b5c20e1" TYPE="ext2"
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat"
/dev/sda3: LABEL="OS" UUID="F6A03163A0312B8D" TYPE="ntfs"
/dev/sda5: UUID="b2f6f4e4-8c35-4c2c-83dc-9cc2a9ee4b98" TYPE="swap"
/dev/sda6: UUID="b53ff4a6-18b3-47a2-bffb-c79f9204a0f5" TYPE="ext4"
/dev/sdb1: LABEL="PENDRIVE" UUID="120C-186F" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda3.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /mnt/hd1/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Apr 20 18:58 grub.d
total 76
-rwxr-xr-x 1 root root  7850 Oct 10  2013 00_header
-rwxr-xr-x 1 root root  5949 Aug 15  2013 05_debian_theme
-rwxr-xr-x 1 root root 11479 Oct 10  2013 10_linux
-rwxr-xr-x 1 root root 10258 Oct 10  2013 20_linux_xen
-rwxr-xr-x 1 root root  1798 Jun 17  2013 20_memtest86+
-rwxr-xr-x 1 root root 11531 Oct 10  2013 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 10  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   324 Apr 20 18:58 40_custom
-rwxr-xr-x 1 root root   324 Apr 20 18:56 40_custom~
-rwxr-xr-x 1 root root   216 Oct 10  2013 41_custom
-rw-r--r-- 1 root root   483 Oct 10  2013 README


=================== /mnt/hd1/etc/grub.d/40_custom :

menuentry "OS X" {
insmod hfsplus
set root="(hd1,gpt2)"
chainloader /usr/standalone/i386/boot0
}




=================== /mnt/hd1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/hd1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  1958MB  1958MB  primary   fat16           diag
3      12.4GB  217GB   205GB   primary   ntfs            boot
4      270GB   500GB   230GB   extended
6      270GB   491GB   221GB   logical   ext4
5      491GB   500GB   9083MB  logical   linux-swap(v1)


Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sdb: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  8005MB  8005MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA ST9500420AS;
1:32.3kB:1958MB:1958MB:fat16::diag;
3:12.4GB:217GB:205GB:ntfs::boot;
4:270GB:500GB:230GB:::;
6:270GB:491GB:221GB:ext4::;
5:491GB:500GB:9083MB:linux-swap(v1)::;

BYT;
/dev/sdb:8011MB:scsi:512:512:msdos:Kingston DataTraveler G2;
1:31.7kB:8005MB:8005MB:fat32::boot, lba;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda6 on /mnt/hd1 type ext4 (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse fw0 hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda3 sda4 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 40 01 00  |.T.Dell 8.0..@..|
00000010  02 00 02 00 00 f8 ea 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  f5 56 3a 00 80 01 29 30  30 30 30 44 65 6c 6c 55  |.V:...)0000DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 60 70 01  |........?....`p.|
00000020  00 00 00 00 80 00 80 00  f0 9f dd 17 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  8d 2b 31 a0 63 31 a0 f6  |.........+1.c1..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  301M  173M  113M  61% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      389M  1.3M  388M   1% /run
/dev/sdb1      vfat       7.5G  1.2G  6.3G  16% /cdrom
/dev/loop0     squashfs   843M  843M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.9G  1.6M  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G   76K  1.9G   1% /run/shm
none           tmpfs      100M   36K  100M   1% /run/user
/dev/sda6      ext4       203G  158G   35G  82% /mnt/hd1
/dev/sda1      vfat       1.9G   11M  1.9G   1% /mnt/boot-sav/sda1
/dev/sda3      fuseblk    191G  180G   12G  94% /mnt/boot-sav/sda3

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc648a420

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3823469     1911703+  de  Dell Utility
/dev/sda3   *    24141824   424542207   200200192    7  HPFS/NTFS/exFAT
/dev/sda4       526944254   976773119   224914433    5  Extended
/dev/sda5       959033344   976773119     8869888   82  Linux swap / Solaris
/dev/sda6       526944256   959033343   216044544   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8011 MB, 8011087872 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000af403

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15635593     7817766    c  W95 FAT32 (LBA)



=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda6 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
WinSE in sda3
/mnt/boot-sav/sda3/ may need repair.
/mnt/boot-sav/sda3/bootmgr may need repair.

*******lspci -nnk | grep -iA3 vga
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] [1002:68e0]
Subsystem: Dell Device [1028:0413]
Kernel driver in use: radeon
02:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68]
*******

grub-install (GRUB) 2.00-19ubuntu2.1,grub-install (GRUB) 2.

Reinstall the GRUB of sda6 into the MBR of sda
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

chroot /mnt/hd1 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found memtest86+ image: /boot/memtest86+.bin
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by oldfred on 2014-04-21
Better to use the pastebin link.

If you post longer output use code tags. You can easily add code tags in Go Advanced editor by highlighting text and click on # icon in edit panel.

Did you delete sda2? It loosk like you have space between sda1 & sda3.
Windows 7 or later uses a separate Boot partition which had bootmgr and BCD. Those files can be in your main install, but you do not show those. And those are the files grub looks for to add a Windows boot entry.

You may be able to use testdisk to restore the missing partition if otherwise just deleted. Or you may have to run Windows repairs to you Windows from a Windows repairCD or flash drive to add the missing boot files.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

            Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by ninjashby on 2014-04-21
Thanks oldfred. I had gotten rid of sda2, without realising that windows needed it to boot. I used windows install cd to repair so I could boot into windows again. I then used boot-repair again to restore grub and everything is working again.

---

