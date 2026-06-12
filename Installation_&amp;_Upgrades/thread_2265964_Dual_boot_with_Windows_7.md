---
title: "Dual boot with Windows 7"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by Anita_Park on 2015-02-18
Hi All,

I have a pre-installed windows 7 box from work that I'm trying to put Ubuntu onto.  I have installed 14.04, and selected install alongside Windows 7.  Ubunut installed all nice, and when I restart I get presented with the grub menu.  If I select Windows I am booted into windows without any issue.  But when I restart again, I don't get grub coming up, instead it appears as though it can't find anything to boot, as it goes into a cycle of rebooting, it never gets to grub again.

Below is the output of running the boot-repair-disk check (I haven't run the repair yet).  I did notice on another forum someone had s similar problem due to grub being installed in /dev/sda, which where it has installed it for me, so just wondering if this could be the issue?  And if so, how can I go about fixing it.

Thanks,
Anita

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07
    Boot sector info:  Syslinux looks at sector 8200 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   204,812,684   204,812,622   7 NTFS / exFAT / HPFS
/dev/sda2         204,812,685   315,120,064   110,307,380   7 NTFS / exFAT / HPFS
/dev/sda3         315,121,662 1,953,523,711 1,638,402,050   5 Extended
/dev/sda5         315,121,664 1,920,088,063 1,604,966,400  83 Linux
/dev/sda6       1,920,090,112 1,953,523,711    33,433,600  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1037 MB, 1037041152 bytes
255 heads, 63 sectors/track, 126 cylinders, total 2025471 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     2,025,470     2,023,423   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1028BC3728BC1DA2                       ntfs       WINDOWS
/dev/sda2        C27214997214946F                       ntfs       Data
/dev/sda5        8a1cd061-30b7-4618-a30e-1bd19a635808   ext4       
/dev/sda6        faa03343-6970-46d2-beb6-ed8427026b7d   swap       
/dev/sdb1        F268-B76C                              vfat       BOOT-REPAIR
/dev/zram0       953c5db6-8179-4a8c-b6e0-d766ac9b6c23   swap       
/dev/zram1       99611edd-5f8e-4e1c-8c10-4f7f9760c3ef   swap       
/dev/zram2       524f3d35-a94d-4567-b7d7-721cc0ee8df5   swap       
/dev/zram3       21d43f1f-ecac-40ee-9609-22acf978cfdd   swap       
/dev/zram4       61525d5f-3f2f-4f90-9fd6-383e92a9ae69   swap       
/dev/zram5       4c4a395c-3dd6-4e4b-99a8-3170137db289   swap       
/dev/zram6       0338d693-5c7f-44bc-8035-7a85677b6e7b   swap       
/dev/zram7       5b4cc03a-c1c3-4b54-a2c0-0eb73897552e   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb 19  2015 ata-HL-DT-ST_DVD+_-RW_GTA0N_M87ECTI0757 -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 19  2015 ata-ST1000DM003-1ER162_S4Y2RKLQ -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 19 02:02 ata-ST1000DM003-1ER162_S4Y2RKLQ-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 19  2015 ata-ST1000DM003-1ER162_S4Y2RKLQ-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 19  2015 ata-ST1000DM003-1ER162_S4Y2RKLQ-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb 19  2015 ata-ST1000DM003-1ER162_S4Y2RKLQ-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 19  2015 ata-ST1000DM003-1ER162_S4Y2RKLQ-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Feb 19  2015 usb-SanDisk_Cruzer_Micro_00017080C2D02F7D-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 19  2015 usb-SanDisk_Cruzer_Micro_00017080C2D02F7D-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 19  2015 wwn-0x5000c50080625041 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 19 02:02 wwn-0x5000c50080625041-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 19  2015 wwn-0x5000c50080625041-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 19  2015 wwn-0x5000c50080625041-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb 19  2015 wwn-0x5000c50080625041-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 19  2015 wwn-0x5000c50080625041-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Feb 19  2015 wwn-0x5001480000000000 -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  8a1cd061-30b7-4618-a30e-1bd19a635808
else
  search --no-floppy --fs-uuid --set=root 8a1cd061-30b7-4618-a30e-1bd19a635808
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8a1cd061-30b7-4618-a30e-1bd19a635808' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  8a1cd061-30b7-4618-a30e-1bd19a635808
    else
      search --no-floppy --fs-uuid --set=root 8a1cd061-30b7-4618-a30e-1bd19a635808
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=8a1cd061-30b7-4618-a30e-1bd19a635808 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8a1cd061-30b7-4618-a30e-1bd19a635808' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-8a1cd061-30b7-4618-a30e-1bd19a635808' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  8a1cd061-30b7-4618-a30e-1bd19a635808
        else
          search --no-floppy --fs-uuid --set=root 8a1cd061-30b7-4618-a30e-1bd19a635808
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=8a1cd061-30b7-4618-a30e-1bd19a635808 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-8a1cd061-30b7-4618-a30e-1bd19a635808' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  8a1cd061-30b7-4618-a30e-1bd19a635808
        else
          search --no-floppy --fs-uuid --set=root 8a1cd061-30b7-4618-a30e-1bd19a635808
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=8a1cd061-30b7-4618-a30e-1bd19a635808 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  8a1cd061-30b7-4618-a30e-1bd19a635808
    else
      search --no-floppy --fs-uuid --set=root 8a1cd061-30b7-4618-a30e-1bd19a635808
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  8a1cd061-30b7-4618-a30e-1bd19a635808
    else
      search --no-floppy --fs-uuid --set=root 8a1cd061-30b7-4618-a30e-1bd19a635808
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-1028BC3728BC1DA2' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1028BC3728BC1DA2
    else
      search --no-floppy --fs-uuid --set=root 1028BC3728BC1DA2
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
UUID=8a1cd061-30b7-4618-a30e-1bd19a635808 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=faa03343-6970-46d2-beb6-ed8427026b7d none            swap    sw              0       0
--------------------------------------------------------------------------------

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

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/2498/mounts) leaked on lvs invocation. Parent PID 10168: bash
File descriptor 63 (pipe:[32783]) leaked on lvs invocation. Parent PID 10168: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-02-19__13h02 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2498/mounts) leaked on lvs invocation. Parent PID 4615: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Ubuntu 14.04.1 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="WINDOWS" UUID="1028BC3728BC1DA2" TYPE="ntfs"
/dev/sda2: LABEL="Data" UUID="C27214997214946F" TYPE="ntfs"
/dev/sda5: UUID="8a1cd061-30b7-4618-a30e-1bd19a635808" TYPE="ext4"
/dev/sda6: UUID="faa03343-6970-46d2-beb6-ed8427026b7d" TYPE="swap"
/dev/sdb1: LABEL="BOOT-REPAIR" UUID="F268-B76C" TYPE="vfat"
/dev/zram0: UUID="953c5db6-8179-4a8c-b6e0-d766ac9b6c23" TYPE="swap"
/dev/zram1: UUID="99611edd-5f8e-4e1c-8c10-4f7f9760c3ef" TYPE="swap"
/dev/zram2: UUID="524f3d35-a94d-4567-b7d7-721cc0ee8df5" TYPE="swap"
/dev/zram3: UUID="21d43f1f-ecac-40ee-9609-22acf978cfdd" TYPE="swap"
/dev/zram4: UUID="61525d5f-3f2f-4f90-9fd6-383e92a9ae69" TYPE="swap"
/dev/zram5: UUID="4c4a395c-3dd6-4e4b-99a8-3170137db289" TYPE="swap"
/dev/zram6: UUID="0338d693-5c7f-44bc-8035-7a85677b6e7b" TYPE="swap"
/dev/zram7: UUID="5b4cc03a-c1c3-4b54-a2c0-0eb73897552e" TYPE="swap"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 22  2014 grub.d
total 76
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




=================== sda5/etc/default/grub :

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
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  105GB   105GB   primary   ntfs            boot
2      105GB   161GB   56.5GB  primary   ntfs
3      161GB   1000GB  839GB   extended
5      161GB   983GB   822GB   logical   ext4
6      983GB   1000GB  17.1GB  logical   linux-swap(v1)


Model: SanDisk Cruzer Micro (scsi)
Disk /dev/sdb: 1037MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1037MB  1036MB  primary  fat32        boot, lba


                                                                            Error: /dev/zram0: unrecognised disk label

                                                                            Error: /dev/zram1: unrecognised disk label

                                                                            Error: /dev/zram2: unrecognised disk label

                                                                            Error: /dev/zram3: unrecognised disk label

                                                                            Error: /dev/zram4: unrecognised disk label

                                                                            Error: /dev/zram5: unrecognised disk label

                                                                            Error: /dev/zram6: unrecognised disk label

                                                                            Error: /dev/zram7: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA ST1000DM003-1ER1;
1:32.3kB:105GB:105GB:ntfs::boot;
2:105GB:161GB:56.5GB:ntfs::;
3:161GB:1000GB:839GB:::;
5:161GB:983GB:822GB:ext4::;
6:983GB:1000GB:17.1GB:linux-swap(v1)::;

BYT;
/dev/sdb:1037MB:scsi:512:512:msdos:SanDisk Cruzer Micro;
1:1049kB:1037MB:1036MB:fat32::boot, lba;

                                                                            Error: /dev/zram0: unrecognised disk label

                                                                            Error: /dev/zram1: unrecognised disk label

                                                                            Error: /dev/zram2: unrecognised disk label

                                                                            Error: /dev/zram3: unrecognised disk label

                                                                            Error: /dev/zram4: unrecognised disk label

                                                                            Error: /dev/zram5: unrecognised disk label

                                                                            Error: /dev/zram6: unrecognised disk label

                                                                            Error: /dev/zram7: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net watchdog watchdog0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  4d 31 35 0c 00 00 00 00  |........M15.....|
00000030  02 00 00 00 00 00 00 00  13 53 c3 00 00 00 00 00  |.........S......|
00000040  f6 00 00 00 01 00 00 00  a2 1d bc 28 37 bc 28 10  |...........(7.(.|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 8d 31 35 0c  |........?....15.|
00000020  00 00 00 00 80 00 80 00  33 28 93 06 00 00 00 00  |........3(......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  6f 94 14 72 99 14 72 c2  |........o..r..r.|
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
/cow           overlayfs  7.9G  5.2M  7.9G   1% /
udev           devtmpfs   7.8G   12K  7.8G   1% /dev
tmpfs          tmpfs      1.6G  1.1M  1.6G   1% /run
/dev/sdb1      vfat       984M  614M  371M  63% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.9G  8.0K  7.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      7.9G     0  7.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk     98G   53G   45G  55% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     53G  2.1G   51G   4% /mnt/boot-sav/sda2
/dev/sda5      ext4       754G  3.1G  712G   1% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0002f7ba

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204812684   102406311    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       204812685   315120064    55153690    7  HPFS/NTFS/exFAT
Partition 2 does not start on physical sector boundary.
/dev/sda3       315121662  1953523711   819201025    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       315121664  1920088063   802483200   83  Linux
/dev/sda6      1920090112  1953523711    16716800   82  Linux swap / Solaris

Disk /dev/sdb: 1037 MB, 1037041152 bytes
255 heads, 63 sectors/track, 126 cylinders, total 2025471 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001acb0c

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     2025470     1011711+   c  W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda5 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.




```

---

### Post by oldfred on 2015-02-19
Please use code tags for longer text. It also preserves formatting.
Better just to provide link that Boot-Repair provides.

Do not see anything specific wrong. You can let Boot-Repair reinstall grub to MBR as default repair, or in advanced repair it can do a full uninstall/reinstall of grub which sometimes fixes things.

Be sure to fully backup Windows. And do not reinstall Ubuntu unless you use Something Else or you may erase entire hard drive and all of Windows.

What video card/chip do you have?

Have you tried the second Ubuntu option or the recovery mode. That sometimes boots where nothing else will.

---

