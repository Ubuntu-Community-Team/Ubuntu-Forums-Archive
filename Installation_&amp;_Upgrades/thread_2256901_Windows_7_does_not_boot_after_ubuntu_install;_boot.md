---
title: "Windows 7 does not boot after ubuntu install; boot loader logs included!"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by Kieranjam2 on 2014-12-15
Hi all!

Just as the title says, I've installed ubuntu but now cannot boot windows. The relavent information is supplied below. 

I have tried the following commands in grub, but they return as such:

Insmod chain
Insmod ntfs

e: '/boot/grub/x86_64-efi/ntfs.mod' not found

I have also tried to follow the instructions in this post ([https://bbs.archlinux.org/viewtopic.php?id=150183](https://bbs.archlinux.org/viewtopic.php?id=150183)) but I am unable to modify them to suit my situation. If anyone could help me onto the right track, and hopefully explain what I did wrong, I would be most grateful. 

Yours,

Kieranjam2

[U]Boot repair Log

[/U] ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi /DELLBIO.BIN /DELLRMK.BIN 
                       /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda5 
                       and looks at sector 1732816424 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub.
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 40838 of /dev/sda6 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. According to the info in the boot sector, 
                       sda6 starts at sector 2048. But according to the info 
                       from fdisk, sda6 starts at sector 1943037952. "63" and 
                       "2048" are quite common values for the starting sector 
                       of a logical partition and they only need to be fixed 
                       when you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         81,920    18,395,135    18,313,216   7 NTFS / exFAT / HPFS
/dev/sda3          18,395,136 1,523,603,455 1,505,208,320   7 NTFS / exFAT / HPFS
/dev/sda4       1,523,605,502 1,953,521,663   429,916,162   f W95 Extended (LBA)
/dev/sda5       1,534,091,264 1,943,035,903   408,944,640  83 Linux
/dev/sda6       1,943,037,952 1,953,521,663    10,483,712   c W95 FAT32 (LBA)
/dev/sda7       1,523,605,504 1,534,091,263    10,485,760  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5450-4444                              vfat       DellUtility
/dev/sda2        841E79671E795362                       ntfs       RECOVERY
/dev/sda3        AA9C7BB09C7B7623                       ntfs       OS
/dev/sda5        ed843ab7-d50c-48c1-8e19-901513a54374   ext2       
/dev/sda6        1216-1531                              vfat       UUI
/dev/sda7        e83d20f3-56f3-45dd-965b-b8557f062b34   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Dec 14 23:33 ata-ST1000LM014-1EJ164_W38208S0 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 14 23:25 ata-ST1000LM014-1EJ164_W38208S0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec 14 23:33 ata-ST1000LM014-1EJ164_W38208S0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 14 23:33 ata-ST1000LM014-1EJ164_W38208S0-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 14 23:25 ata-ST1000LM014-1EJ164_W38208S0-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 14 23:25 ata-ST1000LM014-1EJ164_W38208S0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 14 23:25 ata-ST1000LM014-1EJ164_W38208S0-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 14 23:25 ata-ST1000LM014-1EJ164_W38208S0-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Dec 14 23:33 wwn-0x5000c50077e2d9eb -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 14 23:25 wwn-0x5000c50077e2d9eb-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec 14 23:33 wwn-0x5000c50077e2d9eb-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 14 23:33 wwn-0x5000c50077e2d9eb-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 14 23:25 wwn-0x5000c50077e2d9eb-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 14 23:25 wwn-0x5000c50077e2d9eb-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 14 23:25 wwn-0x5000c50077e2d9eb-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 14 23:25 wwn-0x5000c50077e2d9eb-part7 -> ../../sda7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext2       (rw,errors=remount-ro)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed843ab7-d50c-48c1-8e19-901513a54374
else
  search --no-floppy --fs-uuid --set=root ed843ab7-d50c-48c1-8e19-901513a54374
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ed843ab7-d50c-48c1-8e19-901513a54374' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed843ab7-d50c-48c1-8e19-901513a54374
    else
      search --no-floppy --fs-uuid --set=root ed843ab7-d50c-48c1-8e19-901513a54374
    fi
    linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=ed843ab7-d50c-48c1-8e19-901513a54374 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-43-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ed843ab7-d50c-48c1-8e19-901513a54374' {
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-ed843ab7-d50c-48c1-8e19-901513a54374' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed843ab7-d50c-48c1-8e19-901513a54374
        else
          search --no-floppy --fs-uuid --set=root ed843ab7-d50c-48c1-8e19-901513a54374
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=ed843ab7-d50c-48c1-8e19-901513a54374 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-ed843ab7-d50c-48c1-8e19-901513a54374' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed843ab7-d50c-48c1-8e19-901513a54374
        else
          search --no-floppy --fs-uuid --set=root ed843ab7-d50c-48c1-8e19-901513a54374
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=ed843ab7-d50c-48c1-8e19-901513a54374 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-ed843ab7-d50c-48c1-8e19-901513a54374' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed843ab7-d50c-48c1-8e19-901513a54374
        else
          search --no-floppy --fs-uuid --set=root ed843ab7-d50c-48c1-8e19-901513a54374
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=ed843ab7-d50c-48c1-8e19-901513a54374 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-ed843ab7-d50c-48c1-8e19-901513a54374' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed843ab7-d50c-48c1-8e19-901513a54374
        else
          search --no-floppy --fs-uuid --set=root ed843ab7-d50c-48c1-8e19-901513a54374
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=ed843ab7-d50c-48c1-8e19-901513a54374 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

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
UUID=ed843ab7-d50c-48c1-8e19-901513a54374 /               ext2    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=5450-4444  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda7 during installation
UUID=e83d20f3-56f3-45dd-965b-b8557f062b34 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
hexdump: u: bad byte count
/usr/share/boot-sav/b-i-s.sh: line 1746: [: -eq: unary operator expected
cat: write error: Broken pipe

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-12-14__23h33 ===================
boot-repair version : 4ppa22
boot-sav version : 4ppa22
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa22
boot-repair is executed in installed-session (Ubuntu 14.04.1 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUID=ed843ab7-d50c-48c1-8e19-901513a54374 ro quiet splash vt.handoff=7

=================== os-prober:
/dev/sda5:The OS now in use - Ubuntu 14.04.1 LTS CurrentSession:linux

=================== blkid:
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="5450-4444" TYPE="vfat"
/dev/sda2: LABEL="RECOVERY" UUID="841E79671E795362" TYPE="ntfs"
/dev/sda3: LABEL="OS" UUID="AA9C7BB09C7B7623" TYPE="ntfs"
/dev/sda5: UUID="ed843ab7-d50c-48c1-8e19-901513a54374" TYPE="ext2"
/dev/sda6: LABEL="UUI" UUID="1216-1531" TYPE="vfat"
/dev/sda7: UUID="e83d20f3-56f3-45dd-965b-b8557f062b34" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda3.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Dec 14 17:05 grub.d
drwxr-xr-x  2 root root     4096 Dec 14 17:02 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




=================== /etc/default/grub :

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



=================== No kernel in /mnt/boot-sav/sda6/boot:
grub


Presence of EFI/Boot file detected: /mnt/boot-sav/sda6/EFI/Boot/grubx64.efi

efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0002,0004,0001,0000,2001
Boot0000* Network    BIOS(80,0,2a)........................J..............................................
Boot0001* Hard Drive    BIOS(2,0,2e)........................P..............................................
Boot0002* EFI HDD1 PATH1    ACPI(a0341d0,0)PCI(1f,2)Vendor(cf31fac5-c24e-11d2-85f3-00a0c93ec93b,80)HD(4,5ad05ffe,19a00002,c3238b70)HD(2,73d06800,9ff800,00000000)RC
Boot0003* ubuntu    HD(1,3f,13986,c3238b70)File(EFIubuntushimx64.efi)
Boot0004* Ubuntu    HD(1,3f,13986,c3238b70)File(EFIubuntugrubx64.efi)RC
Boot2001* EFI USB Device    RC
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    no-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.

sda    : not-GPT,    BIOSboot-not-needed,    has-maybe-EFI,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  41.1MB  41.1MB  primary   fat16
2      41.9MB  9418MB  9376MB  primary   ntfs            boot
3      9418MB  780GB   771GB   primary   ntfs
4      780GB   1000GB  220GB   extended                  lba
7      780GB   785GB   5369MB  logical   linux-swap(v1)
5      785GB   995GB   209GB   logical   ext2
6      995GB   1000GB  5368MB  logical   fat32           lba

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA ST1000LM014-1EJ1;
1:32.3kB:41.1MB:41.1MB:fat16::;
2:41.9MB:9418MB:9376MB:ntfs::boot;
3:9418MB:780GB:771GB:ntfs::;
4:780GB:1000GB:220GB:::lba;
7:780GB:785GB:5369MB:linux-swap(v1)::;
5:785GB:995GB:209GB:ext2::;
6:995GB:1000GB:5368MB:fat32::lba;


=================== mount:
/dev/sda5 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=kieran)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fb1 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sg0 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sda1/1:
ls /mnt/boot-sav/sda1: COMMAND.COM
DELLBIO.BIN
DELLRMK.BIN
EFI
oobedone.flg  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== hexdump -n512 -C /dev/sda1
00000000  eb 4a 90 44 45 4c 4c 20  34 2e 31 00 02 04 01 00  |.J.DELL 4.1.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 01 29 44  44 50 54 44 65 6c 6c 55  |.9....)DDPTDellU|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 01 00  |........?....@..|
00000020  00 00 00 00 80 00 80 00  ff 6f 17 01 00 00 00 00  |.........o......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  62 53 79 1e 67 79 1e 84  |........bSy.gy..|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  52 45 43 4f 56 45 52 59  a7 01 bf 01 00 00 55 aa  |RECOVERY......U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b0 18 01  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff a7 b7 59 00 00 00 00  |...........Y....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  23 76 7b 9c b0 7b 9c aa  |........#v{..{..|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200
ls /mnt/boot-sav/sda6/1:
ls /mnt/boot-sav/sda6: autorun.inf
boot
casper
dists
EFI
install
isolinux
license.txt
md5sum.txt
pics
pool
preseed
README.diskdefines
Uni-USB-Installer-Copying.txt
Uni-USB-Installer-Readme.txt
uui
wubi.exe  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== hexdump -n512 -C /dev/sda6
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 f8 9f 00 ad 4f 00 00  00 00 00 00 02 00 00 00  |.....O..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 31 15 16 12 4e  4f 20 4e 41 4d 45 20 20  |..)1...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d f8 50 50 50 50 cd  13 eb 62 8b 55 aa 8b 75  |.M.PPPP...b.U..u|
000000a0  a8 c1 ee 04 01 f2 83 fa  4f 76 31 81 fa b2 07 73  |........Ov1....s|
000000b0  2b f6 45 b4 7f 75 25 38  4d b8 74 20 66 3d 21 47  |+.E..u%8M.t f=!G|
000000c0  50 54 75 10 80 7d b8 ed  75 0a 66 ff 75 ec 66 ff  |PTu..}..u.f.u.f.|
000000d0  75 e8 eb 0f 51 51 66 ff  75 bc eb 07 51 51 66 ff  |u...QQf.u...QQf.|
000000e0  36 1c 7c b4 08 e8 e9 00  72 13 20 e4 75 0f c1 ea  |6.|.....r. .u...|
000000f0  08 42 89 16 1a 7c 83 e1  3f 89 0e 18 7c fb bb aa  |.B...|..?...|...|
00000100  55 b4 41 e8 cb 00 72 10  81 fb 55 aa 75 0a f6 c1  |U.A...r...U.u...|
00000110  01 74 05 c6 06 46 7d 00  66 b8 86 9f 00 00 66 ba  |.t...F}.f.....f.|
00000120  00 00 00 00 bb 00 80 e8  0e 00 66 81 3e 1c 80 a1  |..........f.>...|
00000130  f3 42 6f 75 74 e9 f8 02  66 03 06 60 7b 66 13 16  |.Bout...f..`{f..|
00000140  64 7b b9 10 00 eb 2b 66  52 66 50 06 53 6a 01 6a  |d{....+fRfP.Sj.j|
00000150  10 89 e6 66 60 b4 42 e8  77 00 66 61 8d 64 10 72  |...f`.B.w.fa.d.r|
00000160  01 c3 66 60 31 c0 e8 68  00 66 61 e2 da c6 06 46  |..f`1..h.fa....F|
00000170  7d 2b 66 60 66 0f b7 36  18 7c 66 0f b7 3e 1a 7c  |}+f`f..6.|f..>.||
00000180  66 f7 f6 31 c9 87 ca 66  f7 f7 66 3d ff 03 00 00  |f..1...f..f=....|
00000190  77 17 c0 e4 06 41 08 e1  88 c5 88 d6 b8 01 02 e8  |w....A..........|
000001a0  2f 00 66 61 72 01 c3 e2  c9 31 f6 8e d6 bc 68 7b  |/.far....1....h{|
000001b0  8e de 66 8f 06 78 00 be  da 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001c0  0e bb 07 00 cd 10 eb f2  31 c0 cd 16 cd 19 f4 eb  |........1.......|
000001d0  fd 8a 16 74 7b 06 cd 13  07 c3 42 6f 6f 74 20 65  |...t{.....Boot e|
000001e0  72 72 6f 72 0d 0a 00 00  00 00 00 00 00 00 00 00  |rror............|
000001f0  00 00 00 00 00 00 00 00  fe 02 b2 3e 18 37 55 aa  |...........>.7U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda5      ext2      192G  4.1G  179G   3% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  2.9G   12K  2.9G   1% /dev
tmpfs          tmpfs     585M  1.2M  584M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.9G  156K  2.9G   1% /run/shm
none           tmpfs     100M   36K  100M   1% /run/user
/dev/sda1      vfat       40M  3.5M   36M   9% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   8.8G  6.4G  2.5G  73% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   718G  424G  294G  60% /mnt/boot-sav/sda3
/dev/sda6      vfat      5.0G  980M  4.1G  20% /mnt/boot-sav/sda6

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc3238b70

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131    6  FAT16
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    18395135     9156608    7  HPFS/NTFS/exFAT
/dev/sda3        18395136  1523603455   752604160    7  HPFS/NTFS/exFAT
/dev/sda4      1523605502  1953521663   214958081    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5      1534091264  1943035903   204472320   83  Linux
/dev/sda6      1943037952  1953521663     5241856    c  W95 FAT32 (LBA)
/dev/sda7      1523605504  1534091263     5242880   82  Linux swap / Solaris

Partition table entries are not in disk order



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sda5 into the MBR of sda.
Grub-efi will not be selected by default because: no-win-efi
Additional repair will be performed: unhide-bootmenu-10s



*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
Subsystem: Dell Device [1028:0552]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 650M] [10de:0fd1] (rev a1)
Subsystem: Dell Device [1028:0552]
Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev ff)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1,grub-install (GRUB) 2.

Reinstall the GRUB of sda5 into the MBR of sda
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
grub-install /dev/sda: exit code of grub-install /dev/sda:1

---- Grub-install verbose
+ è\C1\FF\D9k\A4\90\86\A8!%hhX\80\80 \C1\80 0I
/usr/sbin/grub-install: 1: /usr/sbin/grub-install: è\C1\FF\D9k\A4\90\86\A8!%hhX\80\80: not found
/usr/sbin/grub-install: 1: /usr/sbin/grub-install: cannot create n\F0\F0TT@T@DDP\E5td\CC\D2\CC\D2L\CC\D2Ll9l9Q\E5tdR\E5td\F0=\F0=n\F0=n/lib64/ld-linux-x86-64.so.2GNUGNU\D6dj?\92\B0\9E: Directory nonexistent
+ ELF @@@@@@\F8\F888@8@@@\A4:\A4: \F0=\F0=n\F0=n\9E{ \81 
/usr/sbin/grub-install: 1: /usr/sbin/grub-install: ELF: not found
/usr/sbin/grub-install: 2: /usr/sbin/grub-install: Syntax error: word unexpected (expecting ")")
--------
/usr/sbin/grub-install /dev/sda: exit code of grub-install /dev/sda:2
---- End of grub-install verbose


update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

An error occurred during the repair.

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
```

---

### Post by oldfred on 2014-12-15
Please use Code tags with long text output. 
With Boot-Repair better just to post link to pastebin it provides.

You have a drive partitioned with MBR(msdos). 
Windows and Ubuntu only boot from MBR partitioned drives with BIOS, not UEFI.
Windows only boots from gpt partitioned drives with UEFI.

It looks like Boot-Repair did convert install from UEFI to BIOS as you now have grub installed to the MBR of sda. But you also have grub installed to the partition boot sector of sda5 which should not be done, but causes no issues as long as the most current grub is in MBR, not partition.
And there was an error on the reinstall of grub from Boot-Repair that you posted.

You used ext2 for the Ubuntu partition. It really should be ext4.

Grub will only boot Windows installed in the same boot mode. Since you forced an UEFI boot onto a MBR drive (I did not think that worked?), grub cannot boot Windows. 
UEFI and BIOS are not compatible and you can only boot different systems from UEFI menu. And then you would have to have a Windows boot loader in the MBR and boot it from UEFI boot menu in BIOS/CSM mode, and if you did have working UEFI boot could perhaps boot Ubuntu from UEFI menu in UEFI mode.

Best to reinstall Ubuntu using ext4 partition in BIOS boot mode. Only use Something Else or you may erase the entire hard drive as there is a bug that does not make it clear on reinstall that not just Ubuntu may be overwritten.

You have to boot Ubuntu installer in BIOS/CSM mode. Make sure in UEFI you have turned off UEFI mode and from UEFI boot menu you should have two boot options for flash drive. One says UEFI - name of flash, and the other just has the name/label of flash drive.

You want to make sure you are in BIOS mode.
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Reinstall in BIOS mode using Something Else. Leave combo box on where to install grub2 boot loader to MBR of drive shown as sda.

---

### Post by Kieranjam2 on 2014-12-17
Thanks for your advice, I shall enact it as soon as I can get hold of my spare memory stick!

---

