---
title: "Help Ubuntu 18.04.1 and Windows 10 boot"
date: 2018-11-10
forum: Installation &amp; Upgrades
---

### Post by alfredocuaresma on 2018-11-10
Hello, í've happily and sucessively installed 18.04.1 but i feel i have lost my Windows 10 installation. At boot, Grub just displays Ubuntu options to boot in several kernels, but not any entry for Windows.
I also have tried utility "boot-repair", but i think i&#7743; doing something wrong.
 
My pastebin is the following, please could you help me?

[http://paste.ubuntu.com/p/SdPk8QsbkZ/]("http://paste.ubuntu.com/p/SdPk8QsbkZ/")
```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/BOOT/fbx64.efi 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   381,081,325   381,079,278   7 NTFS / exFAT / HPFS
/dev/sda2         381,081,600   382,844,927     1,763,328  27 Hidden NTFS (Recovery Environment)
/dev/sda3    *    382,844,928   384,876,543     2,031,616  ef EFI (FAT-12/16/32)
/dev/sda4         384,878,590   468,860,927    83,982,338   f W95 Extended (LBA)
/dev/sda5         384,878,592   437,610,495    52,731,904  83 Linux
/dev/sda6         437,612,544   468,860,927    31,248,384  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                    34 3,907,027,377 3,907,027,344 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D880756D8075534C                       ntfs       OS Windows
/dev/sda2        E6609A75609A4BE5                       ntfs       
/dev/sda3        379A-1AAC                              vfat       
/dev/sda5        14aba4f6-9ce0-4b6e-b025-9d8d1e07f744   ext4       
/dev/sda6        18a7f44b-4d6d-4aea-9b3f-0e36f8c0ab23   swap       
/dev/sdb1        c61458f8-10cf-4532-9da8-5a2dc4b4b733   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Nov 10 13:09 ata-Hitachi_HDS723020BLA642_MN5240F32WHDMK -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov 10 13:09 ata-Hitachi_HDS723020BLA642_MN5240F32WHDMK-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Nov 10 13:09 ata-SanDisk_SDSSDA240G_162732414613 -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 10 13:09 ata-SanDisk_SDSSDA240G_162732414613-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 10 13:09 ata-SanDisk_SDSSDA240G_162732414613-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 10 13:09 ata-SanDisk_SDSSDA240G_162732414613-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Nov 10 13:09 ata-SanDisk_SDSSDA240G_162732414613-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Nov 10 13:09 ata-SanDisk_SDSSDA240G_162732414613-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov 10 13:09 ata-SanDisk_SDSSDA240G_162732414613-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Nov 10 13:07 usb-Multiple_Card_Reader_058F63666433-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  9 Nov 10 13:09 wwn-0x5000cca369e8aedd -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov 10 13:09 wwn-0x5000cca369e8aedd-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Nov 10 13:09 wwn-0x5001b444a408ba8f -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 10 13:09 wwn-0x5001b444a408ba8f-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 10 13:09 wwn-0x5001b444a408ba8f-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 10 13:09 wwn-0x5001b444a408ba8f-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Nov 10 13:09 wwn-0x5001b444a408ba8f-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Nov 10 13:09 wwn-0x5001b444a408ba8f-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov 10 13:09 wwn-0x5001b444a408ba8f-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1        /home                    ext4       (rw,relatime,data=ordered)


========================== sda3/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid 14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 root hd0,msdos5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
else
  search --no-floppy --fs-uuid --set=root 14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=es_ES
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
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
		set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-14aba4f6-9ce0-4b6e-b025-9d8d1e07f744' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
	else
	  search --no-floppy --fs-uuid --set=root 14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
	fi
        linux	/boot/vmlinuz-4.15.0-38-generic root=UUID=14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.15.0-38-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-14aba4f6-9ce0-4b6e-b025-9d8d1e07f744' {
	menuentry 'Ubuntu, with Linux 4.15.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-38-generic-advanced-14aba4f6-9ce0-4b6e-b025-9d8d1e07f744' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		else
		  search --no-floppy --fs-uuid --set=root 14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		fi
		echo	'Loading Linux 4.15.0-38-generic ...'
	        linux	/boot/vmlinuz-4.15.0-38-generic root=UUID=14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-38-generic-recovery-14aba4f6-9ce0-4b6e-b025-9d8d1e07f744' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		else
		  search --no-floppy --fs-uuid --set=root 14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		fi
		echo	'Loading Linux 4.15.0-38-generic ...'
	        linux	/boot/vmlinuz-4.15.0-38-generic root=UUID=14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-29-generic-advanced-14aba4f6-9ce0-4b6e-b025-9d8d1e07f744' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		else
		  search --no-floppy --fs-uuid --set=root 14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		fi
		echo	'Loading Linux 4.15.0-29-generic ...'
	        linux	/boot/vmlinuz-4.15.0-29-generic root=UUID=14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-29-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-29-generic-recovery-14aba4f6-9ce0-4b6e-b025-9d8d1e07f744' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		else
		  search --no-floppy --fs-uuid --set=root 14aba4f6-9ce0-4b6e-b025-9d8d1e07f744
		fi
		echo	'Loading Linux 4.15.0-29-generic ...'
	        linux	/boot/vmlinuz-4.15.0-29-generic root=UUID=14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-29-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
#UUID=379A-1AAC  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb1 during installation
UUID=c61458f8-10cf-4532-9da8-5a2dc4b4b733 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=18a7f44b-4d6d-4aea-9b3f-0e36f8c0ab23 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 195.863792419 = 210.307145728  boot/grub/grub.cfg                             1
 191.839046478 = 205.985607680  boot/grub/i386-pc/core.img                     1
 191.797344208 = 205.940830208  boot/vmlinuz-4.15.0-29-generic                 1
 186.664932251 = 200.429944832  boot/vmlinuz-4.15.0-38-generic                 1
 191.797344208 = 205.940830208  vmlinuz                                        1
 193.751201630 = 208.038768640  boot/initrd.img-4.15.0-29-generic              2
 189.279232025 = 203.237027840  boot/initrd.img-4.15.0-38-generic              3
 193.751201630 = 208.038768640  initrd.img                                     2
 193.751201630 = 208.038768640  initrd.img.old                                 2

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 


ADDITIONAL INFORMATION :
=================== log of boot-repair 20181110_1308 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-repair is executed in installed-session (Ubuntu 18.04.1 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-generic root=UUID=14aba4f6-9ce0-4b6e-b025-9d8d1e07f744 ro quiet splash vt.handoff=1
Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

=================== os-prober:
/dev/sda5:El sistema operativo que se está usando - Ubuntu 18.04.1 LTS CurrentSession:linux

=================== blkid:
/dev/sda1: LABEL="OS Windows" UUID="D880756D8075534C" TYPE="ntfs" PARTUUID="fe090871-01"
/dev/sda2: UUID="E6609A75609A4BE5" TYPE="ntfs" PARTUUID="fe090871-02"
/dev/sda3: UUID="379A-1AAC" TYPE="vfat" PARTUUID="fe090871-03"
/dev/sda5: UUID="14aba4f6-9ce0-4b6e-b025-9d8d1e07f744" TYPE="ext4" PARTUUID="fe090871-05"
/dev/sda6: UUID="18a7f44b-4d6d-4aea-9b3f-0e36f8c0ab23" TYPE="swap" PARTUUID="fe090871-06"
/dev/sdb1: UUID="c61458f8-10cf-4532-9da8-5a2dc4b4b733" TYPE="ext4" PARTUUID="7dbba1f5-25ee-4bb7-949f-19754df2d1bc"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda1.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 nov 10 12:26 grub.d
drwxr-xr-x  2 root root     4096 nov 10 12:26 grub.d.bak
total 76
-rwxr-xr-x 1 root root  9783 oct 11 14:39 00_header
-rwxr-xr-x 1 root root  6258 jul 13 15:21 05_debian_theme
-rwxr-xr-x 1 root root 12693 oct 11 14:39 10_linux
-rwxr-xr-x 1 root root 11298 oct 11 14:39 20_linux_xen
-rwxr-xr-x 1 root root 12059 oct 11 14:39 30_os-prober
-rwxr-xr-x 1 root root  1418 oct 11 14:39 30_uefi-firmware
-rwxr-xr-x 1 root root   214 oct 11 14:39 40_custom
-rwxr-xr-x 1 root root   216 oct 11 14:39 41_custom
-rw-r--r-- 1 root root   483 oct 11 14:39 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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



Presence of EFI/Boot file detected: /mnt/boot-sav/sda3/EFI/Boot/fbx64.efi
ls /sys/firmware/efi/vars : UsbSupport-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,ucal-707c9176-a4c1-4e27-851d-1c37b7ca73c8,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,SystemIds-71202eee-5f53-40d9-ab3d-9e0c26d96657,StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupCpuFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SbNvramVar-393c4833-402f-4bd5-bf5a-1f5cd8681444,PowerOnTime-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,PNP0501_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,PEGAControlVariables-3e82bad6-1848-46fa-9d12-ab72b5249192,OldLegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,new_var,NBMemoryLength-490216c0-076a-44d3-a536-ace05c90e386,MonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemoryS3SaveVolLength-0a51b41d-de21-43fe-be27-d6dbc9efd104,MemoryS3SaveVol-0a51b41d-de21-43fe-be27-d6dbc9efd104,MemoryS3SaveNv-b1cfc482-4cb2-4cee-9b00-ce2579ec7186,MemCeil.-8be4df61-93ca-11d2-aa0d-00e098032b8c,LegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c,HPSYSID-72cb10a8-b2e3-407f-98fa-1b25c58af28b,HpPreviousBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpPassphraseStructureVariable-707c9176-a4c1-4e27-851d-1c37b7ca73c8,HpDefaultBootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpBoot0008-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpBoot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpBiosFlag-98872116-cda0-4ef0-8ea9-29341288f913,HobRomImage-dde1bc72-d45e-4209-ab85-14462d2f5074,HddDevice-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD02-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD01-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD00-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,FLOPPYDEVICE-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,FLOPPY00-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,DmiVar0b00081f0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00081e0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00081d0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00081c0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00081b0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00081a0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008190-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008180-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008170-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008160-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008150-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008140-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008130-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008120-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008110-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008100-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00080f0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00080e0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00080d0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00080c0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00080b0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b00080a0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008090-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008080-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008070-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008060-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008050-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008040-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008030-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008020-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008010-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0b0008000-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar030003080-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar030003070-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar020002080-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar020002070-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar020002050-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar0100011a0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar010001190-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar010001080-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar010001070-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar010001050-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar010001040-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiArray-4b3082a3-80c6-4d7e-9cd0-583917265df1,del_var,CpuS3Resume-30b98b95-dfa3-4501-a3ce-e38c186384a0,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,CDROMDEVICE-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM00-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrentDP-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot000A-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0009-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0007-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,BBSChecksums-8be4df61-93ca-11d2-aa0d-00e098032b8c,AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34,AMIMemInfo-43387991-1223-7645-b5bb-aa7675c5c8ef,AmiAgesaSetup-840f6ac6-6f42-11d4-bce7-0080c73c8881,AMDDG-72a775aa-3c54-4f07-9fa1-65ec19543390,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,
Informe de este mensaje a boot.repair@gmail.com

=================== efibootmgr -v
Timeout: 0 seconds
BootOrder: 0000,0001,0009,000A,0007,0006,0005
Boot0000* ubuntu	HD(3,MBR,0xfe090871,0x16d1c000,0x1f0000)/File(EFIubuntushimx64.efi)
Boot0001* USB Floppy/CD	VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0005* USB Floppy/CD	VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot0006* Hard Drive	BBS(HD,,0x0)AMGOAMNOk.......+.P.0.:. .S.a.n.D.i.s.k. .S.D.S.S.D.A.2.4.0.G.........................rN.D+..,..........AMBOAMNOu.......+.P.3.:. .H.i.t.a.c.h.i. .H.D.S.7.2.3.0.2.0.B.L.A.6.4.2.........................rN.D+..,..........AMBO
Boot0007* Realtek PXE B03 D00	BBS(Network,,0x0)..........rN.D+..,..........AMBO
Boot0009* Windows Boot Manager	HD(1,GPT,5f93c81a-df3e-4004-8898-e1e4b91dc225,0x800,0x20c000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot000A* USB Hard Drive	VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot maybe enabled. (maybe sec-boot, Informe de este mensaje a boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda5	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	notbiosboot, .
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda2.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda3.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /home.

sda	: not-GPT,	BIOSboot-not-needed,	has-correctEFI, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sdb	: GPT,	no-BIOS_boot,	has-no-EFIpart, 	not-usb,	not-mmc, no-os,	34 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:240GB:scsi:512:512:msdos:ATA SanDisk SDSSDA24:;
1:1049kB:195GB:195GB:ntfs::;
2:195GB:196GB:903MB:ntfs::diag;
3:196GB:197GB:1040MB:fat32::boot, esp;
4:197GB:240GB:43.0GB:::lba;
5:197GB:224GB:27.0GB:ext4::;
6:224GB:240GB:16.0GB:linux-swap(v1)::;

BYT;
/dev/sdb:2000GB:scsi:512:512:gpt:ATA Hitachi HDS72302:;
1:17.4kB:2000GB:2000GB:ext4::;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL
sda   disk        223,6G
sda1  part ntfs   181,7G OS Windows
sda2  part ntfs     861M
sda3  part vfat     992M
sda4  part            1K
sda5  part ext4    25,1G
sda6  part swap    14,9G
sdb   disk          1,8T
sdb1  part ext4     1,8T

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0         /mnt/boot-sav/sda1
sda2     0  0  0         /mnt/boot-sav/sda2
sda3     0  0  0         /mnt/boot-sav/sda3
sda4     0  0  0
sda5     0  0  0         /
sda6     0  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0         /home


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2757216k,nr_inodes=689304,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=557496k,mode=755)
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15906)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /home type ext4 (rw,relatime,data=ordered)
tmpfs on /run/user/119 type tmpfs (rw,nosuid,nodev,relatime,size=557492k,mode=700,uid=119,gid=124)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=557492k,mode=700,uid=1000,gid=1000)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sdc sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uhid uinput urandom usb userio vboxdrv vboxdrvu vboxnetctl vboxusb vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ed ce b6 16 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4c 53 75 80 6d 75 80 d8  |........LSu.mu..|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 d8 b6 16  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff e7 1a 00 00 00 00 00  |................|
00000030  00 1f 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  e5 4b 9a 60 75 9a 60 e6  |.........K.`u.`.|
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
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 45 72 72 6f  |............Erro|
00000190  72 20 64 65 20 64 69 73  63 6f 00 0d 0a 42 4f 4f  |r de disco...BOO|
000001a0  54 4d 47 52 20 63 6f 6d  70 72 69 6d 69 64 6f 00  |TMGR comprimido.|
000001b0  0d 0a 50 72 65 73 2e 20  43 74 72 6c 2b 41 6c 74  |..Pres. Ctrl+Alt|
000001c0  2b 53 75 70 72 20 70 61  72 61 20 72 65 69 6e 69  |+Supr para reini|
000001d0  63 69 61 72 0d 0a 00 72  65 73 74 61 72 74 0d 0a  |ciar...restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  9b 01 b0 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 c0 d1 16  |........?.......|
00000020  00 00 1f 00 c0 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 ac 1a 9a 37 4e  4f 20 4e 41 4d 45 20 20  |..)...7NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.7G     0  2.7G   0% /dev
tmpfs          tmpfs     545M  1.5M  544M   1% /run
/dev/sda5      ext4       25G  7.1G   17G  31% /
tmpfs          tmpfs     2.7G   40M  2.7G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.7G     0  2.7G   0% /sys/fs/cgroup
/dev/sdb1      ext4      1.8T  1.4T  382G  79% /home
tmpfs          tmpfs     545M     0  545M   0% /run/user/119
tmpfs          tmpfs     545M   12K  545M   1% /run/user/1000
/dev/sda1      fuseblk   182G  143G   40G  79% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   861M  394M  468M  46% /mnt/boot-sav/sda2
/dev/sda3      vfat      991M  6.1M  984M   1% /mnt/boot-sav/sda3

=================== fdisk -l:
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xfe090871

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048 381081325 381079278 181.7G  7 HPFS/NTFS/exFAT
/dev/sda2       381081600 382844927   1763328   861M 27 Hidden NTFS WinRE
/dev/sda3  *    382844928 384876543   2031616   992M ef EFI (FAT-12/16/32)
/dev/sda4       384878590 468860927  83982338    40G  f W95 Ext'd (LBA)
/dev/sda5       384878592 437610495  52731904  25.1G 83 Linux
/dev/sda6       437612544 468860927  31248384  14.9G 82 Linux swap / Solaris


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 885C4C55-A78E-416E-89BB-CCF8E9A4474D

Device     Start        End    Sectors  Size Type
/dev/sdb1     34 3907027377 3907027344  1.8T Linux filesystem




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda5 into the MBRs of all disks (except live-disks and removable disks without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
No olvide configurar su BIOS para arrancar en el disco sda (ATA SanDisk SDSSDA24).

Los archivos de arranque de [El sistema operativo que se está usando - Ubuntu 18.04.1 LTS] están lejos del inicio del disco. Su BIOS podría no detectarlos. Quizá quiera reintentarlo después de crear una partición /boot (EXT4, >200MB, comienzo del disco). Esto puede hacerse con herramientas como gParted. Luego seleccione esta partición a través de la opción [Partición /boot separada:] de [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)


=================== User settings
The settings chosen by the user will not act on the boo
```

---

### Post by oldfred on 2018-11-10
First general rule is do not mix UEFI & BIOS.
You have new UEFI system which supports CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
So you can install in the now 35 year old BIOS/MBR configuration or the new UEFI/gpt configuration. 
Windows only boots from MBR(msdos) partitioned drives with BIOS. And Windows only boots from gpt partitioned drives with UEFI.
And converting from MBR to gpt with an install will erase drive. Windows is just about impossible to convert without total reinstall.
How you boot install media, UEFI or BIOS for both Windows & Ubuntu is then how it installs.

You have Windows installed in BIOS boot mode on MBR drive.
But you installed Ubuntu in UEFI boot mode on same drive. Normally you do not install in UEFI mode to MBR drive, but it can be done.
But it makes it very difficult to dual boot.
Windows has to have its boot loader in MBR (you have grub), and boot flag on its boot partition with boot files(your sda1).
But UEFI has to have boot flag on ESP - efi system partition (your sda3). 
You cannot have two boot flags.

While probably better to have installed Windows in UEFI boot mode, at this point better to convert Ubuntu back to BIOS boot mode.
It looks like you have commented out the mount of the ESP, so grub in MBR probably has converted install to BIOS boot.

Move boot flag back to sda1, so you can fix Windows. And install Windows boot loader to MBR of sda. Do not run any autofix with Boot-Repair, only use advanced mode.
Now Windows 10 has fast start up or always on hibernation. And it keeps turning it on with updates. And it in effect makes all NTFS partitions read only as the Linux NTFS drive will not mount NTFS read/write when hibernation flag is set. And then grub will not see it to boot it.
And in BIOS mode, you have to temporarily reinstall Windows boot loader, fix Windows and restore grub2's boot loader. 
With UEFI you can always directly boot both installs from UEFI. 
Grub only boots working Windows.

Since you have two drives, it might be easier to just keep Windows boot loader on sda, and install grub2's boot loader to sdb. Only protective MBR in gpt drive will be used. But you have to add a tiny 1 or 2MB unformatted partition with bios_grub flag within first 2TB of drive for grub to install in BIOS boot mode on gpt drives. Use gparted to create bios_grub partition and Boot-Repair's advanced mode to install grub to only sdb.

Then if you have Windows in sda's MBR & grub in sdb's drive and set BIOS to boot sdb, you can boot either Windows or Ubuntu from grub in BIOS mode. And when Windows needs fixing, you can in BIOS switch to directly boot sda. Still best to have both Windows repair/recovery flash drive and Ubuntu live installer always available.

---

