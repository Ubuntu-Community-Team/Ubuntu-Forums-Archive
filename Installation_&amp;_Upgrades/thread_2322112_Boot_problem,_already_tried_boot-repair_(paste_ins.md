---
title: "Boot problem, already tried boot-repair (paste inside)"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by acariquara on 2016-04-26
Boot-repair paste follows

When I try to boot I get "target filesystem doesn't have requested /sbin/init. /bin/sh:0" and a kernel panic.

System was working fine before, tried to upgrade from 14.04 LTS to 16.04 LTS in place

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 20cff169-586c-46de-ae07-93ca11585880 root hd0,msdos1 
    set prefix=($root)'/boot/grub'
    0230)
    ---------------------------------------------------------------------------
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 20cff169-586c-46de-ae07-93ca11585880 root hd0,msdos1 
    set prefix=($root)'/boot/grub'
    0230)
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......Y\.:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 37630 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   972,580,863   972,578,816  83 Linux
/dev/sda2         972,582,910   976,771,071     4,188,162   5 Extended
/dev/sda5         972,582,912   976,771,071     4,188,160  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931.5 GiB, 1000170586112 bytes, 1953458176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,458,175 1,953,456,128   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 7.2 GiB, 7756087296 bytes, 15148608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    15,148,223    15,148,161   b W95 FAT32


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 930.9 GiB, 999501594624 bytes, 1952151552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048 1,952,151,551 1,952,149,504   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        20cff169-586c-46de-ae07-93ca11585880   ext4       
/dev/sda5        a4a332c7-b135-423f-9543-16900b145ace   swap       
/dev/sdb1        4E1AEA7B1AEA6007                       ntfs       My Passport
/dev/sdc1        4217-578F                              vfat       KINGSTON
/dev/sdd1        12C23AD8C23AC031                       ntfs       My Book
/dev/sr1         4B61ED46                               udf        WD SmartWare

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 26 13:02 ata-Optiarc_DVD_RW_AD-7590S -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 26 13:09 ata-WDC_WD10EADS-00M2B0_WD-WCAV5D963484 -> ../../sdd
lrwxrwxrwx 1 root root 10 Apr 26 13:10 ata-WDC_WD10EADS-00M2B0_WD-WCAV5D963484-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Apr 26 13:09 ata-WDC_WD5000BEVT-00A0RT0_WD-WXE1A8021268 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 26 13:09 ata-WDC_WD5000BEVT-00A0RT0_WD-WXE1A8021268-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 26 13:09 ata-WDC_WD5000BEVT-00A0RT0_WD-WXE1A8021268-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 26 13:09 ata-WDC_WD5000BEVT-00A0RT0_WD-WXE1A8021268-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Apr 26 13:08 usb-Kingston_DataTraveler_SE6_1C6F6581FDFCCCB019212B21-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Apr 26 13:08 usb-Kingston_DataTraveler_SE6_1C6F6581FDFCCCB019212B21-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Apr 26 13:09 usb-WD_My_Passport_0820_575832314535344E5A373731-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 26 13:10 usb-WD_My_Passport_0820_575832314535344E5A373731-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr 26 13:02 usb-WD_Virtual_CD_1110_574341563544393633343834-0:1 -> ../../sr1
lrwxrwxrwx 1 root root  9 Apr 26 13:09 wwn-0x50014ee204a15d2e -> ../../sdd
lrwxrwxrwx 1 root root 10 Apr 26 13:10 wwn-0x50014ee204a15d2e-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Apr 26 13:09 wwn-0x50014ee6ab14bee0 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 26 13:09 wwn-0x50014ee6ab14bee0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 26 13:09 wwn-0x50014ee6ab14bee0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 26 13:09 wwn-0x50014ee6ab14bee0-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr1         /media/ubuntu/WD SmartWare udf        (ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,uhelper=udisks2)


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
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
else
  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
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
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-20cff169-586c-46de-ae07-93ca11585880' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
	else
	  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
	fi
	linux	/boot/vmlinuz-3.13.0-86-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-86-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-20cff169-586c-46de-ae07-93ca11585880' {
	menuentry 'Ubuntu, with Linux 3.13.0-86-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-86-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-86-generic ...'
		linux	/boot/vmlinuz-3.13.0-86-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-86-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-86-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-86-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-86-generic ...'
		linux	/boot/vmlinuz-3.13.0-86-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-86-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-85-generic ...'
		linux	/boot/vmlinuz-3.13.0-85-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-85-generic ...'
		linux	/boot/vmlinuz-3.13.0-85-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-78-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-78-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-78-generic ...'
		linux	/boot/vmlinuz-3.13.0-78-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-78-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-78-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-78-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-78-generic ...'
		linux	/boot/vmlinuz-3.13.0-78-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-78-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-77-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-77-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-77-generic ...'
		linux	/boot/vmlinuz-3.13.0-77-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-77-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-77-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-77-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-77-generic ...'
		linux	/boot/vmlinuz-3.13.0-77-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-77-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-75-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-75-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-75-generic ...'
		linux	/boot/vmlinuz-3.13.0-75-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-75-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-75-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-75-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-75-generic ...'
		linux	/boot/vmlinuz-3.13.0-75-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-75-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-74-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-74-generic ...'
		linux	/boot/vmlinuz-3.13.0-74-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-74-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-74-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-74-generic ...'
		linux	/boot/vmlinuz-3.13.0-74-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-74-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-59-generic ...'
		linux	/boot/vmlinuz-3.13.0-59-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-59-generic ...'
		linux	/boot/vmlinuz-3.13.0-59-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-58-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-58-generic ...'
		linux	/boot/vmlinuz-3.13.0-58-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-58-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-58-generic ...'
		linux	/boot/vmlinuz-3.13.0-58-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-54-generic ...'
		linux	/boot/vmlinuz-3.13.0-54-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-54-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-54-generic ...'
		linux	/boot/vmlinuz-3.13.0-54-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-54-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-46-generic ...'
		linux	/boot/vmlinuz-3.13.0-46-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-46-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-46-generic ...'
		linux	/boot/vmlinuz-3.13.0-46-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-46-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-44-generic ...'
		linux	/boot/vmlinuz-3.13.0-44-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-44-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-44-generic ...'
		linux	/boot/vmlinuz-3.13.0-44-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-44-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-40-generic ...'
		linux	/boot/vmlinuz-3.13.0-40-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-40-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-40-generic ...'
		linux	/boot/vmlinuz-3.13.0-40-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-40-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-36-generic ...'
		linux	/boot/vmlinuz-3.13.0-36-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-36-generic ...'
		linux	/boot/vmlinuz-3.13.0-36-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-33-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-33-generic ...'
		linux	/boot/vmlinuz-3.13.0-33-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-33-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-33-generic ...'
		linux	/boot/vmlinuz-3.13.0-33-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-30-generic ...'
		linux	/boot/vmlinuz-3.13.0-30-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-30-generic ...'
		linux	/boot/vmlinuz-3.13.0-30-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-29-generic ...'
		linux	/boot/vmlinuz-3.13.0-29-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-29-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-29-generic ...'
		linux	/boot/vmlinuz-3.13.0-29-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-29-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-27-generic ...'
		linux	/boot/vmlinuz-3.13.0-27-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.13.0-27-generic ...'
		linux	/boot/vmlinuz-3.13.0-27-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-20-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.11.0-20-generic ...'
		linux	/boot/vmlinuz-3.11.0-20-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-20-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.11.0-20-generic ...'
		linux	/boot/vmlinuz-3.11.0-20-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-32-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.8.0-32-generic ...'
		linux	/boot/vmlinuz-3.8.0-32-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-32-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.8.0-32-generic ...'
		linux	/boot/vmlinuz-3.8.0-32-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.7.0-7-generic ...'
		linux	/boot/vmlinuz-3.7.0-7-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.7.0-7-generic
	}
	menuentry 'Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.7.0-7-generic ...'
		linux	/boot/vmlinuz-3.7.0-7-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.7.0-7-generic
	}
	menuentry 'Ubuntu, with Linux 3.7.0-4-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-4-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.7.0-4-generic ...'
		linux	/boot/vmlinuz-3.7.0-4-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.7.0-4-generic
	}
	menuentry 'Ubuntu, with Linux 3.7.0-4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-4-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.7.0-4-generic ...'
		linux	/boot/vmlinuz-3.7.0-4-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.7.0-4-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.2.0-32-generic ...'
		linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.2.0-32-generic ...'
		linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-22-generic-advanced-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.0.0-22-generic ...'
		linux	/boot/vmlinuz-3.0.0-22-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.0.0-22-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-22-generic-recovery-20cff169-586c-46de-ae07-93ca11585880' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
		else
		  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
		fi
		echo	'Loading Linux 3.0.0-22-generic ...'
		linux	/boot/vmlinuz-3.0.0-22-generic root=UUID=20cff169-586c-46de-ae07-93ca11585880 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.0.0-22-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
	else
	  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20cff169-586c-46de-ae07-93ca11585880
	else
	  search --no-floppy --fs-uuid --set=root 20cff169-586c-46de-ae07-93ca11585880
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=20cff169-586c-46de-ae07-93ca11585880 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a4a332c7-b135-423f-9543-16900b145ace none            swap    sw              0       0
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
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash ---

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash ---

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash ---

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
File descriptor 9 (/proc/4991/mounts) leaked on lvs invocation. Parent PID 19654: bash
File descriptor 63 (pipe:[79739]) leaked on lvs invocation. Parent PID 19654: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-04-26__13h07 ===================
boot-repair version : 4ppa36
boot-sav version : 4ppa36
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa36
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 has been opened read-only.
Error: The partition's data region doesn't occupy the entire partition.
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 has been opened read-only.
Error: The partition's data region doesn't occupy the entire partition.
boot-repair is executed in live-session (Ubuntu 16.04 LTS, xenial, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --- BOOT_IMAGE=/ubnkern
ls: cannot access '/home/usr/.config': No such file or directory
Unmount sdb1 from /media/ubuntu/My Passport to avoid space incompatibilities
Unmount sdd1 from /media/ubuntu/My Book to avoid space incompatibilities

=================== os-prober:
/dev/sda1:Ubuntu 16.04 LTS (16.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="20cff169-586c-46de-ae07-93ca11585880" TYPE="ext4" PARTUUID="000b3710-01"
/dev/sdb1: LABEL="My Passport" UUID="4E1AEA7B1AEA6007" TYPE="ntfs" PARTUUID="ac66161e-01"
/dev/sdc1: LABEL="KINGSTON" UUID="4217-578F" TYPE="vfat" PARTUUID="3afa4bfc-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="a4a332c7-b135-423f-9543-16900b145ace" TYPE="swap" PARTUUID="000b3710-05"
/dev/sr1: UUID="4B61ED46" LABEL="WD SmartWare" TYPE="udf" PTTYPE="mac"
/dev/sdd1: LABEL="My Book" UUID="12C23AD8C23AC031" TYPE="ntfs" PARTUUID="0002ae3f-01"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root  root             4096 Apr 10 22:15 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Dec 19 08:08 00_header
-rwxr-xr-x 1 root root  6058 Apr 10  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11  2014 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct  1  2011 40_custom
-rwxr-xr-x 1 root root   216 Oct 14  2012 41_custom
-rw-r--r-- 1 root root   483 Oct  1  2011 README




=================== sda1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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




=================== sda1recordfail=1/grub/grubenv :
recordfail=1




=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	grubenv-ng	grub2,	grub-pc ,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb1.
sdd1	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdd1.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	no-os,	2048 sectors * 512 bytes
sdd	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD5000BEVT-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
1      1049kB  498GB  498GB   primary   ext4            boot
2      498GB   500GB  2144MB  extended
5      498GB   500GB  2144MB  logical   linux-swap(v1)


Model: WD My Passport 0820 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs


Model: Kingston DataTraveler SE6 (scsi)
Disk /dev/sdc: 7756MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  7756MB  7756MB  primary  fat32        boot


Model: WD My Book 1110 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs


Model: Unknown (unknown)
Disk /dev/sr1: 700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags:

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA WDC WD5000BEVT-0:;
1:1049kB:498GB:498GB:ext4::boot;
2:498GB:500GB:2144MB:::;
5:498GB:500GB:2144MB:linux-swap(v1)::;

BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:WD My Passport 0820:;
1:1049kB:1000GB:1000GB:ntfs::;

BYT;
/dev/sdc:7756MB:scsi:512:512:msdos:Kingston DataTraveler SE6:;
1:32.3kB:7756MB:7756MB:fat32::boot;

BYT;
/dev/sdd:1000GB:scsi:512:512:msdos:WD My Book 1110:;
1:1049kB:1000GB:1000GB:ntfs::;

BYT;
/dev/sr1:700MB:unknown:2048:2048:unknown:Unknown:;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          465.8G
sda1  part ext4     463.8G
sda2  part              1K
sda5  part swap         2G
sdb   disk          931.5G
sdb1  part ntfs     931.5G My Passport
sdc   disk            7.2G
sdc1  part vfat       7.2G KINGSTON
sdd   disk          930.9G
sdd1  part ntfs     930.9G My Book
sr0   rom            1024M
sr1   rom  udf        668M WD SmartWare
loop0 loop squashfs   1.4G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0
sda5     1  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
sdd      1  0  0 running
sdd1     1  0  0         /mnt/boot-sav/sdd1
sr0      1  0  1 running
sr1      1  0  1 running /media/ubuntu/WD SmartWare
loop0    1  1  0         /rofs


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1017720k,nr_inodes=213035,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=206192k,mode=755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory,nsroot=/)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,nsroot=/)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices,nsroot=/)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,nsroot=/)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,nsroot=/)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,nsroot=/)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=206192k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sr1 on /media/ubuntu/WD SmartWare type udf (ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw,relatime,data=ordered)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdd1 on /mnt/boot-sav/sdd1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdc sdc1 sdd sdd1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 5f 6f 74 00 00 00 00  |........._ot....|
00000030  00 00 0c 00 00 00 00 00  ff f5 46 07 00 00 00 00  |..........F.....|
00000040  f6 00 00 00 01 00 00 00  07 60 ea 1a 7b ea 1a 4e  |.........`..{..N|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdd1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 6f 5b 74 00 00 00 00  |.........o[t....|
00000030  00 00 0c 00 00 00 00 00  ff b6 45 07 00 00 00 00  |..........E.....|
00000040  f6 00 00 00 01 00 00 00  31 c0 3a c2 d8 3a c2 12  |........1.:..:..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  994M     0  994M   0% /dev
tmpfs          tmpfs     202M  6.5M  195M   4% /run
/dev/sdc1      vfat      7.3G  1.5G  5.8G  20% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
/cow           overlay  1007M   63M  944M   7% /
tmpfs          tmpfs    1007M  180K 1007M   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs    1007M     0 1007M   0% /sys/fs/cgroup
tmpfs          tmpfs    1007M  256K 1007M   1% /tmp
tmpfs          tmpfs     202M  108K  202M   1% /run/user/999
/dev/sr1       udf       443M  443M     0 100% /media/ubuntu/WD SmartWare
/dev/sda1      ext4      457G  374G   60G  87% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk   932G  525G  407G  57% /mnt/boot-sav/sdb1
/dev/sdd1      fuseblk   931G  778G  153G  84% /mnt/boot-sav/sdd1

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1460752384 bytes, 2853032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000b3710

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 972580863 972578816 463.8G 83 Linux
/dev/sda2       972582910 976771071   4188162     2G  5 Extended
/dev/sda5       972582912 976771071   4188160     2G 82 Linux swap / Solaris


Disk /dev/sdb: 931.5 GiB, 1000170586112 bytes, 1953458176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xac66161e

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953458175 1953456128 931.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 7.2 GiB, 7756087296 bytes, 15148608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x3afa4bfc

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *       63 15148223 15148161  7.2G  b W95 FAT32


Disk /dev/sdd: 930.9 GiB, 999501594624 bytes, 1952151552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002ae3f

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdd1        2048 1952151551 1952149504 930.9G  7 HPFS/NTFS/exFAT



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sda1 into the MBRs of all disks (except USB without OS).
The boot flag will be placed on sdd1.
Additional repair will be performed: unhide-bootmenu-10s


parted /dev/sdd set 1 boot on
Information: You may need to update /etc/fstab.


                                                                          
[email]SET@_progressbar1.pulse[/email]()
Unhide GRUB boot menu in sda1/etc/default/grub

Reinstall the GRUB of sda1 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [ION] [10de:0a64] (rev a2)
Subsystem: ASUSTeK Computer Inc. Device [1043:841f]
Kernel driver in use: nouveau
03:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.8,grub-install (GRUB) 2.

Reinstall the GRUB of sda1 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

*******lspci -nnk | grep -iA3 vga
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [ION] [10de:0a64] (rev a2)
Subsystem: ASUSTeK Computer Inc. Device [1043:841f]
Kernel driver in use: nouveau
03:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.8,grub-install (GRUB) 2.

Reinstall the GRUB of sda1 into the MBR of sdd
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdd: exit code of grub-install /dev/sdd:0

*******lspci -nnk | grep -iA3 vga
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [ION] [10de:0a64] (rev a2)
Subsystem: ASUSTeK Computer Inc. Device [1043:841f]
Kernel driver in use: nouveau
03:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.8,grub-install (GRUB) 2.

Reinstall the GRUB of sda1 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda1 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-86-generic
Found initrd image: /boot/initrd.img-3.13.0-86-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found linux image: /boot/vmlinuz-3.13.0-78-generic
Found initrd image: /boot/initrd.img-3.13.0-78-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-75-generic
Found initrd image: /boot/initrd.img-3.13.0-75-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found initrd image: /boot/initrd.img-3.13.0-33-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.7.0-7-generic
Found initrd image: /boot/initrd.img-3.7.0-7-generic
Found linux image: /boot/vmlinuz-3.7.0-4-generic
Found initrd image: /boot/initrd.img-3.7.0-4-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.0.0-22-generic
Found initrd image: /boot/initrd.img-3.0.0-22-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (500GB) disk!
paste.ubuntu.com ko (), using paste.debian
paste.debian.net ko (), using paste2

```

---

### Post by acariquara on 2016-04-26
oh and btw my sig is a little old :D

---

### Post by kansasnoob on 2016-04-26
> tried to upgrade from 14.04 LTS to 16.04 LTS in place

Looking at the available kernel versions it's apparent that the upgrade failed. Did it freeze during the upgrade? Can you at least boot into the recovery mode?

---

