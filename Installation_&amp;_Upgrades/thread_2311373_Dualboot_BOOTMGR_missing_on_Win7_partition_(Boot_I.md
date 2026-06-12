---
title: "Dualboot BOOTMGR missing on Win7 partition (Boot Info Script)"
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by Nathan_Leite on 2016-01-26
I installed ubuntu as dual boot a year ago. Never been very good with system operations . 
Haven't tried opening windows until now. (Just got swept away in to an Ubuntu life)
Wondering if anyone can see what I did wrong???

```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/pdc_bcgcfeibbd and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 112 for .


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb3: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sdb4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


pdc_bcgcfeibbd1: _______________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


pdc_bcgcfeibbd2: _______________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe


pdc_bcgcfeibbd3: _______________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,663,555,583 1,663,348,736   7 NTFS / exFAT / HPFS
/dev/sda3       1,929,844,736 1,953,122,303    23,277,568   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sdb2    *      3,074,048   284,440,575   281,366,528   7 NTFS / exFAT / HPFS
/dev/sdb3         284,440,576   352,917,503    68,476,928  83 Linux
/dev/sdb4         352,919,550   390,721,535    37,801,986   5 Extended
/dev/sdb5         352,919,552   390,721,535    37,801,984  82 Linux swap / Solaris




Drive: pdc_bcgcfeibbd _____________________________________________________________________


Disk /dev/mapper/pdc_bcgcfeibbd: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/mapper/pdc_bcgcfeibbd1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bcgcfeibbd2            206,848 1,663,555,583 1,663,348,736   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bcgcfeibbd3      1,929,844,736 1,953,122,303    23,277,568   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        7EE86FA9E86F5F01                       ntfs       SYSTEM
/dev/sda2        01D062256A3BCB80                       ntfs       HP
/dev/sda3        72FE40BBFE4078FD                       ntfs       FACTORY_IMAGE
/dev/sdb1        D2AEBD92AEBD7019                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sdb2        01D062EE6EBEC940                       ntfs       spare
/dev/sdb3        b984dd93-c892-4245-a40b-70971b4ce0ce   ext4       
/dev/sdb5        9cf580cf-b869-48ce-bd34-b4f2e784c456   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb3        /                        ext4       (rw,errors=remount-ro)




=========================== sdb3/boot/grub/grub.cfg: ===========================


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
set root='hd1,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
else
  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b984dd93-c892-4245-a40b-70971b4ce0ce' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
	else
	  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
	fi
	linux	/boot/vmlinuz-3.16.0-59-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.16.0-59-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
	menuentry 'Ubuntu, with Linux 3.16.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-59-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-59-generic ...'
		linux	/boot/vmlinuz-3.16.0-59-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-59-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-59-generic ...'
		linux	/boot/vmlinuz-3.16.0-59-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-57-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-57-generic ...'
		linux	/boot/vmlinuz-3.16.0-57-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-57-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-57-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-57-generic ...'
		linux	/boot/vmlinuz-3.16.0-57-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-57-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-56-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-56-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-56-generic ...'
		linux	/boot/vmlinuz-3.16.0-56-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-56-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-56-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-56-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-56-generic ...'
		linux	/boot/vmlinuz-3.16.0-56-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-56-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-55-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-55-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-55-generic ...'
		linux	/boot/vmlinuz-3.16.0-55-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-55-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-55-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-55-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-55-generic ...'
		linux	/boot/vmlinuz-3.16.0-55-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-55-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-53-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-53-generic ...'
		linux	/boot/vmlinuz-3.16.0-53-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-53-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-53-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-53-generic ...'
		linux	/boot/vmlinuz-3.16.0-53-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-53-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-52-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-52-generic ...'
		linux	/boot/vmlinuz-3.16.0-52-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-52-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-52-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-52-generic ...'
		linux	/boot/vmlinuz-3.16.0-52-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-52-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-51-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-51-generic ...'
		linux	/boot/vmlinuz-3.16.0-51-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-51-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-51-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-51-generic ...'
		linux	/boot/vmlinuz-3.16.0-51-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-51-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-50-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-50-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-50-generic ...'
		linux	/boot/vmlinuz-3.16.0-50-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-50-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-50-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-50-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-50-generic ...'
		linux	/boot/vmlinuz-3.16.0-50-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-50-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-49-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-49-generic ...'
		linux	/boot/vmlinuz-3.16.0-49-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-49-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-49-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-49-generic ...'
		linux	/boot/vmlinuz-3.16.0-49-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-49-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-48-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-48-generic ...'
		linux	/boot/vmlinuz-3.16.0-48-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-48-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-48-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-48-generic ...'
		linux	/boot/vmlinuz-3.16.0-48-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-48-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-46-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-46-generic ...'
		linux	/boot/vmlinuz-3.16.0-46-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-46-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-46-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-46-generic ...'
		linux	/boot/vmlinuz-3.16.0-46-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-46-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-45-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-45-generic ...'
		linux	/boot/vmlinuz-3.16.0-45-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-45-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-45-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-45-generic ...'
		linux	/boot/vmlinuz-3.16.0-45-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-45-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-43-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-43-generic ...'
		linux	/boot/vmlinuz-3.16.0-43-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-43-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-43-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-43-generic ...'
		linux	/boot/vmlinuz-3.16.0-43-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-43-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-41-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-41-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-41-generic ...'
		linux	/boot/vmlinuz-3.16.0-41-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-41-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-41-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-41-generic ...'
		linux	/boot/vmlinuz-3.16.0-41-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-41-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-38-generic ...'
		linux	/boot/vmlinuz-3.16.0-38-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-38-generic ...'
		linux	/boot/vmlinuz-3.16.0-38-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-37-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-37-generic ...'
		linux	/boot/vmlinuz-3.16.0-37-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-37-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-37-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-37-generic ...'
		linux	/boot/vmlinuz-3.16.0-37-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-37-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-36-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-36-generic ...'
		linux	/boot/vmlinuz-3.16.0-36-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-36-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-36-generic ...'
		linux	/boot/vmlinuz-3.16.0-36-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-34-generic ...'
		linux	/boot/vmlinuz-3.16.0-34-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-34-generic ...'
		linux	/boot/vmlinuz-3.16.0-34-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-33-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-33-generic ...'
		linux	/boot/vmlinuz-3.16.0-33-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-33-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-33-generic ...'
		linux	/boot/vmlinuz-3.16.0-33-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-31-generic-advanced-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-31-generic ...'
		linux	/boot/vmlinuz-3.16.0-31-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-31-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-31-generic-recovery-b984dd93-c892-4245-a40b-70971b4ce0ce' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
		else
		  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
		fi
		echo	'Loading Linux 3.16.0-31-generic ...'
		linux	/boot/vmlinuz-3.16.0-31-generic root=UUID=b984dd93-c892-4245-a40b-70971b4ce0ce ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-31-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
	else
	  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b984dd93-c892-4245-a40b-70971b4ce0ce
	else
	  search --no-floppy --fs-uuid --set=root b984dd93-c892-4245-a40b-70971b4ce0ce
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


=============================== sdb3/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb3 during installation
UUID=b984dd93-c892-4245-a40b-70971b4ce0ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9cf580cf-b869-48ce-bd34-b4f2e784c456 none            swap    sw              0       0
/dev/disk/by-id/usb-Generic-_SD_MMC_058F63626476-0:0 /mnt/usb-Generic-_SD_MMC_058F63626476-0:0 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
--------------------------------------------------------------------------------


=================== sdb3: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sdb4


00000000  2e 03 2c b2 d3 38 ab 45  81 20 16 67 31 7f 0f 47  |..,..8.E. .g1..G|
00000010  b7 fe 29 b6 b1 63 bc 0f  de 09 9b 2d cd 3b 92 6e  |..)..c.....-.;.n|
00000020  ca b6 00 7f 51 2d 92 9f  ed e1 ce 9f 68 8a ba af  |....Q-......h...|
00000030  b2 dd a4 eb 2f 4c 09 31  32 c2 98 4c c1 15 08 26  |..../L.12..L...&|
00000040  9b 7e 20 11 f3 8b cd e0  b4 9b 95 92 4a d4 8d 46  |.~ .........J..F|
00000050  59 96 56 8d 1e 26 bf a4  92 92 94 a4 25 35 a8 ce  |Y.V..&......%5..|
00000060  b5 c8 08 82 cb c8 be 77  71 b0 0d 09 0f 01 c7 16  |.......wq.......|
00000070  fb 42 cf 7b f6 2a 19 7e  b3 ca 4b cd 29 48 4a 71  |.B.{.*.~..K.)HJq|
00000080  f3 41 15 19 e6 ae b8 a7  72 26 d2 1d bb b2 e1 69  |.A......r&.....i|
00000090  0b 03 4b 92 85 7f eb 8d  37 52 63 70 df 00 8a 2a  |..K.....7Rcp...*|
000000a0  f2 76 7b 6d cf c9 aa 5e  ce 72 5b 0b c1 4b 59 63  |.v{m...^.r[..KYc|
000000b0  46 02 68 6b 53 f3 11 f0  ed df bc 09 9f 99 76 5a  |F.hkS.........vZ|
000000c0  d8 6d 96 1e 7b 1e 15 55  64 27 3c 85 72 1b 46 5d  |.m..{..Ud'<.r.F]|
000000d0  db 62 d7 a8 cb ee 1b e0  10 6a 4c 6e 1b e0 10 10  |.b.......jLn....|
000000e0  f7 72 46 d5 90 2f 0b 4a  7d 13 a8 21 01 af 69 34  |.rF../.J}..!..i4|
000000f0  14 55 4d 05 6a 73 89 cc  49 eb 4c 37 a9 31 b8 6f  |.UM.js..I.L7.1.o|
00000100  80 41 a9 31 b8 6f 80 44  0e e2 4f 5a 60 c4 9e b4  |.A.1.o.D..OZ`...|
00000110  c3 5a 93 1b 86 f8 04 1a  93 1b 86 f8 04 03 b8 93  |.Z..............|
00000120  d6 98 31 27 ad 30 d6 a4  c6 e1 be 01 06 a4 c6 e1  |..1'.0..........|
00000130  be 01 00 ee 24 f5 a6 0c  49 eb 4c 35 a9 31 b8 6f  |....$...I.L5.1.o|
00000140  80 41 a9 31 b8 6f 80 40  3b 89 3d 69 83 12 7a d3  |.A.1.o.@;.=i..z.|
00000150  0d 6a 4c 6e 1b e0 10 6a  4c 6e 1b e0 10 0e 15 27  |.jLn...jLn.....'|
00000160  ad 31 8c 72 e9 4d 1c bd  3b 4f f2 e3 62 32 4c 6e  |.1.r.M..;O..b2Ln|
00000170  1b e0 11 8e 72 e4 da 5b  66 5d 29 48 4a 44 ce 40  |....r..[f])HJD.@|
00000180  0a 0f cb 80 c8 1c f5 4f  c2 1b 6f d7 10 41 11 5e  |.......O..o..A.^|
00000190  83 e4 67 fa bf 23 fd d2  ff 00 d7 1a 5c 10 45 41  |..g..#......\.EA|
000001a0  04 10 44 51 04 10 40 10  41 04 01 04 10 40 10 41  |..DQ..@.A....@.A|
000001b0  04 01 04 10 40 06 31 6e  5d bf 2e 5f fc 4f 00 fe  |....@.1n].._.O..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 40 02 00 00  |............@...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




========= Devices which don't seem to have a corresponding hard drive: =========


sdc sdd sde sdf 


=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-0OiD39Ve/Tmp_Log: No such file or directory



```

---

### Post by oldfred on 2016-01-26
I do not know RAID.
Did you turn RAID on or off?

This is RAID or Intel SRT which looks like RAID from Linux.
 Disk /dev/mapper/pdc_bcgcfeibbd

You really should have grub in the MBR of sdb only. And boot from BIOS using sdb drive.

And have Windows in either sda if not really RAID, or in root of RAID where BIOS finds it. 
Script could not directly mount partitions in sda, but shows the BCD in the mapper mount.

---

### Post by Nathan_Leite on 2016-01-27
Thank you for the reply,

I do not know if I turned it off, would there be a way to check? 
does this tell you?
```
Attached devices:Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD10EADS-65M Rev: 0A01
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: Optiarc  Model: DVD RW AD-7231S5 Rev: 1H84
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: FUJITSU MHV2200B Rev: 0050
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic- Model: SD/MMC           Rev: 1.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi6 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic- Model: Compact Flash    Rev: 1.01
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi6 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic- Model: SM/xD-Picture    Rev: 1.02
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi6 Channel: 00 Id: 00 Lun: 03
  Vendor: Generic- Model: MS/MS-Pro        Rev: 1.03
  Type:   Direct-Access                    ANSI  SCSI revision: 00



```


Either way is this fixable or should I just try to save everything and start over from scratch?

Again thank you

---

### Post by oldfred on 2016-01-28
Look in UEFI/BIOS for hard drive settings, does it show RAID or do you have a whole list of Intel SRT settings? Standard is now AHCI for drives. Years ago it was IDE.
Only if you really want or have RAID should that be the setting.

Some now older screen shots of Intel SRT.
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by Nathan_Leite on 2016-01-29
it said SATA was set to raid
it gave me the option to switch so I did to AHCI
it didnt help anything so I put it back

Being as it is RAID I am not sure the steps to take to accomplish 
> "[COLOR=#000000]You really should have grub in the MBR of sdb only. And boot from BIOS using sdb drive.[/COLOR]

[COLOR=#000000]And have Windows in either sda if not really RAID, or in root of RAID where BIOS finds it. [/COLOR]
[COLOR=#000000]Script could not directly mount partitions in sda, but shows the BCD in the mapper mount."[/COLOR]

---

### Post by oldfred on 2016-01-29
I would change to AHCI.

Then you may need to remove meta-data on drive.
       Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
From 2011, so now older
[http://tobestool.net/using-intels-rst-with-linux/](http://tobestool.net/using-intels-rst-with-linux/)

If using SSD for Ubuntu you will not be able to re-enable Intel SRT or the RAID.

---

