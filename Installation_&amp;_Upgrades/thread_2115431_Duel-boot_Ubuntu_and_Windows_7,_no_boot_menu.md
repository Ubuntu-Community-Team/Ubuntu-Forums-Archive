---
title: "Duel-boot Ubuntu and Windows 7, no boot menu"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by stewarts9090 on 2013-02-12
I have Windows 7 on my computer and installed Ubuntu 12.10 alongside for a duel-boot via a live USB, but it boots directly to Windows 7 when I restart the computer.

I have looked up the 'boot-repair' fix, however it still hasn't fixed my problem.

I'm using an ASUS N56V, CPU: Intel Core i7-3610QM 2.30GHz, OS: Windows 7 x64

I have the boot info from my last attempt at a boot-repair fix.

If anybody could help it would be much appreciated.

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda6: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 85104 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The 2 ADV sectors are not the same (corrupt). No 
                       errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi.signed /EFI/BOOT/grubx64.efi 
                       /ldlinux.sys

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
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648       673,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         673,792   586,733,567   586,059,776 Data partition (Windows/Linux)
/dev/sda4     586,733,568 1,024,947,075   438,213,508 Data partition (Windows/Linux)
/dev/sda5   1,413,949,440 1,465,147,618    51,198,179 Windows Recovery Environment (Windows)
/dev/sda6   1,024,948,224 1,024,950,271         2,048 BIOS Boot partition
/dev/sda7   1,024,950,272 1,397,407,743   372,457,472 EFI System partition
/dev/sda8   1,397,407,744 1,413,949,439    16,541,696 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7885 MB, 7885291520 bytes
256 heads, 43 sectors/track, 1399 cylinders, total 15400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,760    15,400,959    15,398,200   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       a67701c6-84c2-104c-b575-0869722955da   ext2       casper-rw
/dev/sda1        C224-2A64                              vfat       SYSTEM
/dev/sda3        62082D74082D47FD                       ntfs       OS
/dev/sda4        2AC42E68C42E370B                       ntfs       DATA
/dev/sda5        8E7233AF72339AC3                       ntfs       Recovery
/dev/sda7        c4983e51-591e-45d3-8d8f-5b63c471417d   ext4       
/dev/sda8        9cc45059-410a-4811-940a-de9d938eb907   swap       
/dev/sdb1        B522-E22C                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  c4983e51-591e-45d3-8d8f-5b63c471417d
else
  search --no-floppy --fs-uuid --set=root c4983e51-591e-45d3-8d8f-5b63c471417d
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c4983e51-591e-45d3-8d8f-5b63c471417d' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  c4983e51-591e-45d3-8d8f-5b63c471417d
    else
      search --no-floppy --fs-uuid --set=root c4983e51-591e-45d3-8d8f-5b63c471417d
    fi
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=c4983e51-591e-45d3-8d8f-5b63c471417d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c4983e51-591e-45d3-8d8f-5b63c471417d' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-c4983e51-591e-45d3-8d8f-5b63c471417d' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  c4983e51-591e-45d3-8d8f-5b63c471417d
        else
          search --no-floppy --fs-uuid --set=root c4983e51-591e-45d3-8d8f-5b63c471417d
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=c4983e51-591e-45d3-8d8f-5b63c471417d ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-c4983e51-591e-45d3-8d8f-5b63c471417d' {
    recordfail
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  c4983e51-591e-45d3-8d8f-5b63c471417d
        else
          search --no-floppy --fs-uuid --set=root c4983e51-591e-45d3-8d8f-5b63c471417d
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=c4983e51-591e-45d3-8d8f-5b63c471417d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  c4983e51-591e-45d3-8d8f-5b63c471417d
    else
      search --no-floppy --fs-uuid --set=root c4983e51-591e-45d3-8d8f-5b63c471417d
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  c4983e51-591e-45d3-8d8f-5b63c471417d
    else
      search --no-floppy --fs-uuid --set=root c4983e51-591e-45d3-8d8f-5b63c471417d
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-62082D74082D47FD' {
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  62082D74082D47FD
    else
      search --no-floppy --fs-uuid --set=root 62082D74082D47FD
    fi
    chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda5)' --class windows --class os $menuentry_id_option 'osprober-chain-8E7233AF72339AC3' {
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  8E7233AF72339AC3
    else
      search --no-floppy --fs-uuid --set=root 8E7233AF72339AC3
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=c4983e51-591e-45d3-8d8f-5b63c471417d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9cc45059-410a-4811-940a-de9d938eb907 none            swap    sw              0       0
#UUID=C224-2A64    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 556.877937317 = 597.943132160  boot/grub/grub.cfg                             1
 556.869178772 = 597.933727744  boot/grub/i386-pc/core.img                     1
 556.868129730 = 597.932601344  boot/vmlinuz-3.5.0-17-generic                  1
 556.868129730 = 597.932601344  vmlinuz                                        1
 495.514175415 = 532.054294528  boot/initrd.img-3.5.0-17-generic               1
 495.514175415 = 532.054294528  initrd.img                                     1

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
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  boot=casper integrity-check quiet splash --
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

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             ldlinux.sys                                    2
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/7058/mounts) leaked on lvscan invocation. Parent PID 18324: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-02-12__20h53 ===================
boot-repair version : 3.197~ppa31~quantal
boot-sav version : 3.197~ppa31~quantal
glade2script version : 3.2.2~ppa45~quantal
boot-sav-extra version : 3.197~ppa31~quantal
boot-repair is executed in live-session (Ubuntu 12.10, quantal, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- maybe-ubiquity

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda3:Windows 7 (loader):Windows:chain
/dev/sda5:Windows Recovery Environment (loader):Windows1:chain
/dev/sda7:Ubuntu 12.10 (12.10):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: LABEL="casper-rw" UUID="a67701c6-84c2-104c-b575-0869722955da" TYPE="ext2"
/dev/sda1: LABEL="SYSTEM" UUID="C224-2A64" TYPE="vfat"
/dev/sda3: LABEL="OS" UUID="62082D74082D47FD" TYPE="ntfs"
/dev/sda4: LABEL="DATA" UUID="2AC42E68C42E370B" TYPE="ntfs"
/dev/sda5: LABEL="Recovery" UUID="8E7233AF72339AC3" TYPE="ntfs"
/dev/sda7: UUID="c4983e51-591e-45d3-8d8f-5b63c471417d" TYPE="ext4"
/dev/sda8: UUID="9cc45059-410a-4811-940a-de9d938eb907" TYPE="swap"
/dev/sdb1: LABEL="PENDRIVE" UUID="B522-E22C" TYPE="vfat"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi


=================== sda7/etc/default/grub :

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




=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct 17 10:59 grub.d
total 72
-rwxr-xr-x 1 root root  7541 Oct 14 13:36 00_header
-rwxr-xr-x 1 root root  5488 Oct  4 05:30 05_debian_theme
-rwxr-xr-x 1 root root 10891 Oct 14 13:36 10_linux
-rwxr-xr-x 1 root root 10258 Oct 14 13:36 20_linux_xen
-rwxr-xr-x 1 root root  1688 Oct 11 10:10 20_memtest86+
-rwxr-xr-x 1 root root 10976 Oct 14 13:36 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 14 13:36 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 14 13:36 40_custom
-rwxr-xr-x 1 root root   216 Oct 14 13:36 41_custom
-rw-r--r-- 1 root root   483 Oct 14 13:36 README


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.

sda    : GPT,    BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
1      1049kB  211MB  210MB   fat32           EFI system partition          boot
2      211MB   345MB  134MB                   Microsoft reserved partition  msftres
3      345MB   300GB  300GB   ntfs            Basic data partition
4      300GB   525GB  224GB   ntfs            Basic data partition
6      525GB   525GB  1049kB                                                bios_grub
7      525GB   715GB  191GB   ext4
8      715GB   724GB  8469MB  linux-swap(v1)
5      724GB   750GB  26.2GB  ntfs            Basic data partition          hidden, diag


Model: Lexar JumpDrive (scsi)
Disk /dev/sdb: 7885MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1413kB  7885MB  7884MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:750GB:scsi:512:4096:gpt:ATA Hitachi HTS54757;
1:1049kB:211MB:210MB:fat32:EFI system partition:boot;
2:211MB:345MB:134MB::Microsoft reserved partition:msftres;
3:345MB:300GB:300GB:ntfs:Basic data partition:;
4:300GB:525GB:224GB:ntfs:Basic data partition:;
6:525GB:525GB:1049kB:::bios_grub;
7:525GB:715GB:191GB:ext4::;
8:715GB:724GB:8469MB:linux-swap(v1)::;
5:724GB:750GB:26.2GB:ntfs:Basic data partition:hidden, diag;

BYT;
/dev/sdb:7885MB:scsi:512:512:msdos:Lexar JumpDrive;
1:1413kB:7885MB:7884MB:fat32::boot, lba;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fb1 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control
Files in /mnt/boot-sav/sda1/efi: /mnt/boot-sav/sda1/efi/ASUS/N56VZ.BIN /mnt/boot-sav/sda1/efi/ASUS/N56VM.BIN /mnt/boot-sav/sda1/efi/ASUS /mnt/boot-sav/sda1/efi/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Boot /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD.LOG2 /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD.LOG1 /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD.LOG /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/wgl4_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/kor_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/jpn_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/cht_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/chs_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts /mnt/boot-sav/sda1/efi/Microsoft/Boot/BOOTSTAT.DAT /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-HK/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-HK/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-HK /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-CN/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-CN/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-CN/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-CN /mnt/boot-sav/sda1/efi/Microsoft/Boot/tr-TR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/tr-TR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/tr-TR /mnt/boot-sav/sda1/efi/Microsoft/Boot/sv-SE/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/sv-SE/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/sv-SE /mnt/boot-sav/sda1/efi/Microsoft/Boot/ru-RU/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ru-RU/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ru-RU /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-BR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-BR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-BR /mnt/boot-sav/sda1/efi/Microsoft/Boot/pl-PL/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pl-PL/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pl-PL /mnt/boot-sav/sda1/efi/Microsoft/Boot/nl-NL/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nl-NL/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nl-NL /mnt/boot-sav/sda1/efi/Microsoft/Boot/nb-NO/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nb-NO/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nb-NO /mnt/boot-sav/sda1/efi/Microsoft/Boot/memtest.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/ko-KR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ko-KR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ko-KR /mnt/boot-sav/sda1/efi/Microsoft/Boot/ja-JP/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ja-JP/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ja-JP /mnt/boot-sav/sda1/efi/Microsoft/Boot/it-IT/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/it-IT/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/it-IT /mnt/boot-sav/sda1/efi/Microsoft/Boot/hu-HU/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/hu-HU/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/hu-HU /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR /mnt/boot-sav/sda1/efi/Microsoft/Boot/fi-FI/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fi-FI/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fi-FI /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US /mnt/boot-sav/sda1/efi/Microsoft/Boot/el-GR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/el-GR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/el-GR /mnt/boot-sav/sda1/efi/Microsoft/Boot/de-DE/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/de-DE/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/de-DE /mnt/boot-sav/sda1/efi/Microsoft/Boot/da-DK/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/da-DK/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/da-DK /mnt/boot-sav/sda1/efi/Microsoft/Boot/cs-CZ/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/cs-CZ/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/cs-CZ /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgr.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot /mnt/boot-sav/sda1/efi/Microsoft /mnt/boot-sav/sda1/efi

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 04 de 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 40 06 00 11 03 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 64 2a 24 c2 4e  4f 20 4e 41 4d 45 20 20  |..)d*$.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 0a 00  |........?....H..|
00000020  00 00 00 00 80 00 80 00  ff 8f ee 22 00 00 00 00  |..........."....|
00000030  00 00 0c 00 00 00 00 00  ff e8 2e 02 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  fd 47 2d 08 74 2d 08 62  |.........G-.t-.b|
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

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 d8 f8 22  |........?......"|
00000020  00 00 00 00 80 00 80 00  78 9b 1e 1a 00 00 00 00  |........x.......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  0b 37 2e c4 68 2e c4 2a  |.........7..h..*|
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

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 47 54  |........?....(GT|
00000020  00 00 00 00 80 00 80 00  e2 38 0d 03 00 00 00 00  |.........8......|
00000030  00 00 0c 00 00 00 00 00  8e d3 30 00 00 00 00 00  |..........0.....|
00000040  f6 00 00 00 01 00 00 00  c3 9a 33 72 af 33 72 8e  |..........3r.3r.|
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

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  974M   93M  831M  10% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      1.6G  876K  1.6G   1% /run
/dev/sdb1      vfat       7.4G  2.7G  4.7G  36% /cdrom
/dev/loop0     squashfs   717M  717M     0 100% /rofs
tmpfs          tmpfs      3.9G   16K  3.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      3.9G   76K  3.9G   1% /run/shm
none           tmpfs      100M   32K  100M   1% /run/user
/dev/sda1      vfat       196M   31M  166M  16% /mnt/boot-sav/sda1
/dev/sda3      fuseblk    280G  263G   18G  94% /mnt/boot-sav/sda3
/dev/sda4      fuseblk    209G   27G  183G  13% /mnt/boot-sav/sda4
/dev/sda5      fuseblk     25G   15G   11G  59% /mnt/boot-sav/sda5
/dev/sda7      ext4       175G  2.9G  164G   2% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2902cc6d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 7885 MB, 7885291520 bytes
256 heads, 43 sectors/track, 1399 cylinders, total 15400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2760    15400959     7699100    c  W95 FAT32 (LBA)


EFI detected. Please check the options.

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages unsign-grub) and reinstall the grub-efi of sda7, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files

=================== Settings chosen by the user
Custom-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda7.
Additional repair will be performed: unhide-bootmenu-10s


Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 7 boot on

                                                                          
Information: You may need to update /etc/fstab.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Boot successfully repaired.

You can now reboot your computer.

```

---

### Post by oldfred on 2013-02-13
You have a UEFI install of Windows, so Ubuntu needs to be installed in UEFI mode also to easily dual boot. But you have a bios_grub partition, so Ubuntu was installed in BIOS/legacy/AHCI/CSM or whatever your sytem calls it mode.

You also have two efi partitions. There can only be one and Ubuntu has to use the same efi partition as Windows. Use gparted from your live installer and remove boot flag from sda7.

       In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

    
Boot-Repair has the capability to convert a BIOS install to UEFI by un-installing grub-pc and installing grub-efi.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
       To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.

    
Boot-Repair also fixes the issues with this bug.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

