---
title: "After update stuck on blinking cursor"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2015-06-16
One of my PCs updated.  I rebooted this am and after GRUB it gets stuck on a blank screen with blinking cursor.

I have tried GRUB Repair but that has made no difference.  I think there was an kernel update, but not sure.
Noted that 'Bumblebee' had installed.  I think I recall seeing somewhere that that may cause booting problems... !?!?!?!

GR output.
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 6e593eb7-62ae-46b3-85ec-e20864445cf3 root hd0,msdos5 
    set prefix=($root)'/boot/grub'
    KZ
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   350,824,447   350,822,400   7 NTFS / exFAT / HPFS
/dev/sda2         350,826,494   455,583,743   104,757,250   5 Extended
/dev/sda5         350,828,544   455,583,743   104,755,200  83 Linux
/dev/sda4         455,583,744   488,396,799    32,813,056  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   566,050,815   566,050,753  83 Linux
/dev/sdb3         566,050,816   771,809,279   205,758,464   7 NTFS / exFAT / HPFS
/dev/sdb4         771,810,795   976,768,064   204,957,270   5 Extended
/dev/sdb5    *    771,813,376   976,766,975   204,953,600  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4AE5E83A4716097B                       ntfs       Windows
/dev/sda4        c434799f-bdbe-4d21-ac56-9bef10ec2559   swap       
/dev/sda5        6e593eb7-62ae-46b3-85ec-e20864445cf3   ext4       Root
/dev/sdb1        9972d3c0-79f8-4baa-ae8f-ccbc63f630a8   ext4       Backup
/dev/sdb3        2104697C2776893B                       ntfs       Documents
/dev/sdb5        22c1ecdc-2fc5-4b0d-8e26-92d62a48c567   ext4       home
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       c2b5de89-c28f-4cf3-a32e-cae849ba033b   swap       
/dev/zram1       6a06ca60-9453-4db1-81d6-75ba750c0beb   swap       
/dev/zram2       59b01837-36da-4176-b754-6bcbcfbd2c6b   swap       
/dev/zram3       61b7f696-58f4-4d93-8646-7cb80879c1fe   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jun 16  2015 ata-HL-DT-ST_DVDRAM_GSA-H66N_K5677SN1032 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jun 16 07:59 ata-SAMSUNG_HD501LJ_S0MUJ1EQ129689 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 16  2015 ata-SAMSUNG_HD501LJ_S0MUJ1EQ129689-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun 16 07:43 ata-SAMSUNG_HD501LJ_S0MUJ1EQ129689-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jun 16 07:59 ata-SAMSUNG_HD501LJ_S0MUJ1EQ129689-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Jun 16  2015 ata-SAMSUNG_HD501LJ_S0MUJ1EQ129689-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Jun 16 08:00 ata-WDC_WD2500AAJS-60M0A0_WD-WMAV2A990502 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 16 08:00 ata-WDC_WD2500AAJS-60M0A0_WD-WMAV2A990502-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun 16 07:42 ata-WDC_WD2500AAJS-60M0A0_WD-WMAV2A990502-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun 16  2015 ata-WDC_WD2500AAJS-60M0A0_WD-WMAV2A990502-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jun 16  2015 ata-WDC_WD2500AAJS-60M0A0_WD-WMAV2A990502-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Jun 16  2015 usb-Generic_USB_CF_Reader_058F312D81B-0:1 -> ../../sdd
lrwxrwxrwx 1 root root  9 Jun 16  2015 usb-Generic_USB_MS_Reader_058F312D81B-0:3 -> ../../sdf
lrwxrwxrwx 1 root root  9 Jun 16  2015 usb-Generic_USB_SD_Reader_058F312D81B-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  9 Jun 16  2015 usb-Generic_USB_SM_Reader_058F312D81B-0:2 -> ../../sde
lrwxrwxrwx 1 root root  9 Jun 16 07:59 wwn-0x50000f001b129689 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 16  2015 wwn-0x50000f001b129689-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun 16 07:43 wwn-0x50000f001b129689-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jun 16 07:59 wwn-0x50000f001b129689-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Jun 16  2015 wwn-0x50000f001b129689-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Jun 16 08:00 wwn-0x50014ee056c980e4 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 16 08:00 wwn-0x50014ee056c980e4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun 16 07:42 wwn-0x50014ee056c980e4-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun 16  2015 wwn-0x50014ee056c980e4-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jun 16  2015 wwn-0x50014ee056c980e4-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/lubuntu/Root      ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda5        /mnt/boot-sav/sda5       ext4       (rw)
/dev/sdb3        /media/lubuntu/Documents fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
else
  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
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
  set timeout=5
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=5
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=5
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
	else
	  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
	fi
	linux	/boot/vmlinuz-3.19.0-18-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.19.0-18-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-advanced-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-18-generic ...'
		linux	/boot/vmlinuz-3.19.0-18-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-init-upstart-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-18-generic ...'
		linux	/boot/vmlinuz-3.19.0-18-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-recovery-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-18-generic ...'
		linux	/boot/vmlinuz-3.19.0-18-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-advanced-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-16-generic ...'
		linux	/boot/vmlinuz-3.19.0-16-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-init-upstart-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-16-generic ...'
		linux	/boot/vmlinuz-3.19.0-16-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-recovery-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-16-generic ...'
		linux	/boot/vmlinuz-3.19.0-16-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-init-upstart-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-6e593eb7-62ae-46b3-85ec-e20864445cf3' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
		else
		  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic root=UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
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
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
	else
	  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  6e593eb7-62ae-46b3-85ec-e20864445cf3
	else
	  search --no-floppy --fs-uuid --set=root 6e593eb7-62ae-46b3-85ec-e20864445cf3
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-4AE5E83A4716097B' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4AE5E83A4716097B
	else
	  search --no-floppy --fs-uuid --set=root 4AE5E83A4716097B
	fi
	parttool ${root} hidden-
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=5
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
UUID=6e593eb7-62ae-46b3-85ec-e20864445cf3 /               ext4    errors=remount-ro 0       1

# /home was on /dev/sdb5 during installation
UUID=22c1ecdc-2fc5-4b0d-8e26-92d62a48c567 /home           ext4    defaults        0       2

# swap was on /dev/sda4 during installation
UUID=c434799f-bdbe-4d21-ac56-9bef10ec2559 none            swap    sw              0       0


# /media/Documents is on /dev/sdb3
UUID=2104697C2776893B	/home/baronipc/Desktop/Documents	ntfs	defaults,locale=en_GB.utf8	0	0

# /media/Backup was on /dev/sdb1 during installation
UUID=9972d3c0-79f8-4baa-ae8f-ccbc63f630a8	/home/baronipc/Backup		ext4	defaults	0	2

# /media/Documents is on /dev/sda1
UUID=4AE5E83A4716097B			/home/baronipc/Windows	ntfs 	defaults,locale=en_GB.utf8	0	0

# 85 is the USB group
#none	/proc/bus/usb	usbfs	devgid=85,devmode=666	0	0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: write error: Broken pipe
File descriptor 9 (/proc/3185/mounts) leaked on lvs invocation. Parent PID 26289: bash
File descriptor 63 (pipe:[24501]) leaked on lvs invocation. Parent PID 26289: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-06-16__07h41 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/3185/mounts) leaked on lvs invocation. Parent PID 4849: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Ubuntu 15.04 (15.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda1: LABEL="Windows" UUID="4AE5E83A4716097B" TYPE="ntfs"
/dev/sda4: UUID="c434799f-bdbe-4d21-ac56-9bef10ec2559" TYPE="swap"
/dev/sda5: LABEL="Root" UUID="6e593eb7-62ae-46b3-85ec-e20864445cf3" TYPE="ext4"
/dev/sdb1: LABEL="Backup" UUID="9972d3c0-79f8-4baa-ae8f-ccbc63f630a8" TYPE="ext4"
/dev/sdb3: LABEL="Documents" UUID="2104697C2776893B" TYPE="ntfs"
/dev/sdb5: LABEL="home" UUID="22c1ecdc-2fc5-4b0d-8e26-92d62a48c567" TYPE="ext4"
/dev/zram0: UUID="c2b5de89-c28f-4cf3-a32e-cae849ba033b" TYPE="swap"
/dev/zram1: UUID="6a06ca60-9453-4db1-81d6-75ba750c0beb" TYPE="swap"
/dev/zram2: UUID="59b01837-36da-4176-b754-6bcbcfbd2c6b" TYPE="swap"
/dev/zram3: UUID="61b7f696-58f4-4d93-8646-7cb80879c1fe" TYPE="swap"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Apr 22 12:07 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr  6 20:43 00_header
-rwxr-xr-x 1 root root  6058 Feb 11 19:53 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr  6 20:43 10_linux
-rwxr-xr-x 1 root root 11082 Apr  6 20:43 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar  6 16:23 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr  6 20:43 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr  6 20:43 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  6 20:43 40_custom
-rwxr-xr-x 1 root root   216 Apr  6 20:43 41_custom
-rw-r--r-- 1 root root   483 Apr  6 20:43 README




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
GRUB_BACKGROUND=&#8221;/usr/share/images/desktop-base/TheKissnWilliam.png&#8221;

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
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda1.
sda5	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb1.
sdb3	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb3.
sdb5	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb5.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	63 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD2500AAJS-6 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  180GB  180GB   primary   ntfs            boot
2      180GB   233GB  53.6GB  extended
5      180GB   233GB  53.6GB  logical   ext4
4      233GB   250GB  16.8GB  primary   linux-swap(v1)


Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
1      32.3kB  290GB  290GB  primary   ext4
3      290GB   395GB  105GB  primary   ntfs
4      395GB   500GB  105GB  extended
5      395GB   500GB  105GB  logical   ext4



                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA WDC WD2500AAJS-6;
1:1049kB:180GB:180GB:ntfs::boot;
2:180GB:233GB:53.6GB:::;
5:180GB:233GB:53.6GB:ext4::;
4:233GB:250GB:16.8GB:linux-swap(v1)::;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA SAMSUNG HD501LJ;
1:32.3kB:290GB:290GB:ext4::;
3:290GB:395GB:105GB:ntfs::;
4:395GB:500GB:105GB:::;
5:395GB:500GB:105GB:ext4::;


                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
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
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)
/dev/sdb3 on /mnt/boot-sav/sdb3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /mnt/boot-sav/sdb5 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb3 sdb4 sdb5 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda4 sda5 sdb sdb1 sdb3 sdb4 sdb5 sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 1f e9 14 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff 3f 9c 00 00 00 00 00  |.........?......|
00000040  f6 00 00 00 01 00 00 00  7b 09 16 47 3a e8 e5 4a  |........{..G:..J|
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

=================== hexdump -n512 -C /dev/sdb3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 bd 21  |........?....@.!|
00000020  00 00 00 00 80 00 80 00  f8 9f 43 0c 00 00 00 00  |..........C.....|
00000030  04 00 00 00 00 00 00 00  ff fa 9c 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  3b 89 76 27 7c 69 04 21  |........;.v'|i.!|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  7.9G  6.3M  7.9G   1% /
udev           devtmpfs   7.9G   12K  7.9G   1% /dev
tmpfs          tmpfs      1.6G  1.2M  1.6G   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.9G  8.0K  7.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      7.9G     0  7.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk    168G  116G   53G  69% /mnt/boot-sav/sda1
/dev/sda5      ext4        50G   11G   36G  24% /mnt/boot-sav/sda5
/dev/sdb1      ext4       266G  137M  252G   1% /mnt/boot-sav/sdb1
/dev/sdb3      fuseblk     99G   90G  8.9G  91% /mnt/boot-sav/sdb3
/dev/sdb5      ext4        97G   31G   61G  34% /mnt/boot-sav/sdb5

=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9a63

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   350824447   175411200    7  HPFS/NTFS/exFAT
/dev/sda2       350826494   455583743    52378625    5  Extended
/dev/sda4       455583744   488396799    16406528   82  Linux swap / Solaris
/dev/sda5       350828544   455583743    52377600   83  Linux

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f620

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   566050815   283025376+  83  Linux
/dev/sdb3       566050816   771809279   102879232    7  HPFS/NTFS/exFAT
/dev/sdb4       771810795   976768064   102478635    5  Extended
/dev/sdb5       771813376   976766975   102476800   83  Linux




=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda5 into the MBRs of all disks (except USB without OS).
The boot flag would be placed on sdb5.
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (250GB) disk!


=================== User settings
The settings chosen by the user will reinstall the grub2 of sda5 into the MBRs of all disks (except USB without OS).
The boot flag will be placed on sdb5.
Additional repair will be performed: unhide-bootmenu-5s


parted /dev/sdb set 5 boot on

                                                                          
Information: You may need to update /etc/fstab.

Error: no /mnt/boot-sav/sda5/etc/fstab
umount: /mnt/boot-sav/sda1: not mounted
Mounted /dev/sda5 on /mnt/boot-sav/sda5
Unhide GRUB boot menu in sda5/etc/default/grub

Reinstall the GRUB of sda5 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GTX 650] [10de:0fc6] (rev a1)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:362b]
Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-22ubuntu1,grub-install (GRUB) 2.

Reinstall the GRUB of sda5 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GTX 650] [10de:0fc6] (rev a1)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:362b]
Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-22ubuntu1,grub-install (GRUB) 2.

Reinstall the GRUB of sda5 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda5 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (250GB) disk!

```[COLOR=#000]



[/COLOR]

---

### Post by dino99 on 2015-06-16
this is not related to 'grub' but to a graphic driver issue. Seems to me you already have posted a similar thread which got answered.

---

### Post by Bucky Ball on 2015-06-16
When you boot the machine do you get a list with kernels/OSs to choose from? If not, try hitting shift just after the manufacturer's splash screen. Can you get that screen? If so, choose the kernel you want to boot, hit 'e', look for the line that ends in 'quiet splash' or any combination or one of those two words. Make the end of that line look like:

```
quiet splash nomodeset
```

Follow the instructions at the bottom of the screen to save, exit and reboot. Any luck?

PS: Switch the machine off and remove the USB dongle (sdb) if that is what is plugged in. Reboot. You have grub installed on sda and sdb so who knows what is happening ... what drive do you have the BIOS set to boot from??? What have you got installed on each drive, in detail, thanks? You should be booting from the grub in sda.

---

### Post by Jonners59 on 2015-06-17
> **dino99 said:**
> this is not related to 'grub' but to a graphic driver issue. Seems to me you already have posted a similar thread which got answered.
I didn't say it had anything to do with GRUB...  and similar, but not quite the same.

> **Bucky Ball said:**
> When you boot the machine do you get a list with kernels/OSs to choose from? If not, try hitting shift just after the manufacturer's splash screen. Can you get that screen? If so, choose the kernel you want to boot, hit 'e', look for the line that ends in 'quiet splash' or any combination or one of those two words. Make the end of that line look like:

```
quiet splash nomodeset
```

Follow the instructions at the bottom of the screen to save, exit and reboot. Any luck?

PS: Switch the machine off and remove the USB dongle (sdb) if that is what is plugged in. Reboot. You have grub installed on sda and sdb so who knows what is happening ... what drive do you have the BIOS set to boot from??? What have you got installed on each drive, in detail, thanks? You should be booting from the grub in sda.

Bucky Ball
Many thanks, but not a nomodeset issue.....  Though I had forggotten to test that when I created the thread.  The other problem with nomodeset is all the 3D and other enhancements are lost.  Hope below helps someone else.  If not at least an aid for me if/when it happens again.


Did fix it, though and very painful it was too.  There really needs to be some quality check on nvidia drivers.  Can't be doing this every update and upgrade....

I did remove "Bumblebee" as that has been a cause of driver failures from what I have seen and it did install during this update.

The rest was a very trial and error drive through of all the commands and tricks I had picked up on this subject - and known bug - over the past few months.

Some of these lines may not be required, but I did them to make sure it worked having tried this route and commands several times before the driver(s) installed correctly. It is easy to check if it has worked.  Either you can't boot up fully - blank screen again or you can look in Applications ->System -> NVIDIA X Server Settings
If when you open the app there are only 2 lines on the left hand column, then the drivers have NOT installed correctly and the whole thing needs to be purged...  Hence the first stages below.  Failure to do so and every install will fail.

Before starting:
Check which video card you have:
Firstupdate pciids before next steps:
```
sudo update-pciids
```
Then one of the following.....


```
lspci
lspci -k
lspci -v
lspci -v | less
```


Vidiohardware details
```
sudo lspci -v -s 01:00.0
```

Then check for the latest driver for your card.  Great little tool on Nvidia's website:
[http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk)

```
Boot and after GRUB&#8230;
Control+ALT+F1
Sudo su (I found it was the only way to get full control, otherwise some commands do not work)
Sudo service lightdm stop (stopping lightdm, not sure if really required)
sudo apt-get clean && apt-get autoclean && apt-get autoremove (a little cleaning)
sudo apt-get update && apt-get install &#8211;f  (update source and fix)

sudo apt-get purge libvdpau-va-gl1 bumblebee* nvidia* (just cleans out everything)[INDENT=2]OR for a more targeted approach[/INDENT]
dpkg &#8211;l[SIZE=2][FONT=Lucida Grande]| [/FONT][/SIZE]greb nvidia
            lists everything installed for nvidia
then remove everything except
                        nvidia-cg-toolkit (if it or equivellent exists)
                        nvidia-common
sudo apt-get purge nvidia-xxxx (where xxxx is anything from the list)
 
sudo apt-get autoremove (another little clean. I did have a couple of packages appear in mine)
sudo dpkg-reconfigure nvidia-common (should return a message does not exist)

sudo apt-get install nvidia-352 nvidia-settings nvidia-prime nvidia-current nvidia-cg-toolkit common[INDENT=2]OR[/INDENT]
Sudo apt-get install --reinstall nvidia-xxx-updates-uvm     (install nvidia-xxx, change the xxx to the number you want (331, 340, 352, and can have multiple with && nvidia-xxx if you want more than one)


sudo apt-get install xserver-xorg-video-nouveau (may say already installed, but just check)
sudo apt-get install linux-headers-generic
sudo apt-get clean && apt-get autoclean && apt-get autoremove (another clean up)
sudo apt-get apt-get upgrade && update && apt-get install &#8211;f
sudo update-alternatives --config x86_64-linux-gnu_gl_conf (choose your driver)
sudo ldconfig -n
sudo update-initramfs -u
sudo shutdown &#8211;r now
```

Suggest printing this out as the list will not be available whilst doing this unless you have 2 machines.

Hope this helps someone else.

---

### Post by Bucky Ball on 2015-06-17
Glad you got it fixed and thanks for marking as solved. ;)

[QUOTE=Jonners59]There really needs to be some quality check on nvidia drivers.[/QUOTE]

By whom? Ubuntu/Canonical has nothing to do with the creation of these third-party drivers. Best to contact Nvidia directly. ;)

---

### Post by Jonners59 on 2015-06-18
> **Bucky Ball said:**
> Glad you got it fixed and thanks for marking as solved. ;)



By whom? Ubuntu/Canonical has nothing to do with the creation of these third-party drivers. Best to contact Nvidia directly. ;)

I don't know, but Ubuntu have it as a bug - several - and are fixing it.  There are several on launchpad.....

---

