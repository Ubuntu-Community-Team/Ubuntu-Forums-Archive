---
title: "Dual boot upgrade (win7 &amp; 14.04 -&gt; 18.04)"
date: 2019-01-28
forum: Installation &amp; Upgrades
---

### Post by mastablasta on 2019-01-28
final upgrade to do. i have a dualboot win7 starter and Kubuntu 14.04 64bit in MBR. I found out i need to actually move to 18.04 due to 3 years support cycle for Kubuntu.

issues:

1. upgrade from 14.04 to 16.04 is not supported by Kubuntu.
2. i have AMD drivers installed.
3. possibly not enough disk space at the start for new grub.

i am thinking a reinstall (installing over previous install also seems to not be working). backing it all up. not much stuff installed and not much data to backup. plan is to test it if it all works as it should then erase partition and re-install.

i need to keep windows 7 for some tax reporting and such.

questions:
1. do i have enough space for new grub to install?
2. grub goes to sda6 or sda? 



```
                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe


sda6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda7: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd


sda4: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,662   938,870,783   938,461,122   f W95 Extended (LBA)
/dev/sda5             409,664   629,747,999   629,338,336   7 NTFS / exFAT / HPFS
/dev/sda6         629,749,760   930,529,279   300,779,520  83 Linux
/dev/sda7         930,531,328   938,870,783     8,339,456  82 Linux swap / Solaris
/dev/sda3         938,872,832   968,450,047    29,577,216   7 NTFS / exFAT / HPFS
/dev/sda4         968,450,048   976,771,119     8,321,072   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        02CA6F18CA6F06EF                       ntfs       SYSTEM
/dev/sda3        70705369705334D6                       ntfs       Recovery
/dev/sda4        1A7D-CD7B                              vfat       HP_TOOLS
/dev/sda5        01CE966381257F10                       ntfs       
/dev/sda6        b8d9906e-6a55-4762-a562-6bc1c558f30d   ext4       
/dev/sda7        34b63990-c920-43b3-9bf1-60d6570e7823   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda6        /                        ext4       (rw,errors=remount-ro)




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
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
else
  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
	else
	  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
	fi
	linux	/boot/vmlinuz-3.13.0-164-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-164-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
	menuentry 'Ubuntu, with Linux 3.13.0-164-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-164-generic-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-164-generic ...'
		linux	/boot/vmlinuz-3.13.0-164-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-164-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-164-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-164-generic-recovery-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-164-generic ...'
		linux	/boot/vmlinuz-3.13.0-164-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-164-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-163-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-163-generic-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-163-generic ...'
		linux	/boot/vmlinuz-3.13.0-163-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-163-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-163-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-163-generic-recovery-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-163-generic ...'
		linux	/boot/vmlinuz-3.13.0-163-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-163-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-96-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-96-generic-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-96-generic ...'
		linux	/boot/vmlinuz-3.13.0-96-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-96-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-96-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-96-generic-recovery-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-96-generic ...'
		linux	/boot/vmlinuz-3.13.0-96-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-96-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-83-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-83-generic-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-83-generic ...'
		linux	/boot/vmlinuz-3.13.0-83-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-83-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-83-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-83-generic-recovery-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-83-generic ...'
		linux	/boot/vmlinuz-3.13.0-83-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-83-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-53-generic ...'
		linux	/boot/vmlinuz-3.13.0-53-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-53-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-53-generic ...'
		linux	/boot/vmlinuz-3.13.0-53-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-53-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-44-generic ...'
		linux	/boot/vmlinuz-3.13.0-44-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-44-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-44-generic ...'
		linux	/boot/vmlinuz-3.13.0-44-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-44-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-b8d9906e-6a55-4762-a562-6bc1c558f30d' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
		else
		  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
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
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
	else
	  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  b8d9906e-6a55-4762-a562-6bc1c558f30d
	else
	  search --no-floppy --fs-uuid --set=root b8d9906e-6a55-4762-a562-6bc1c558f30d
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-02CA6F18CA6F06EF' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  02CA6F18CA6F06EF
	else
	  search --no-floppy --fs-uuid --set=root 02CA6F18CA6F06EF
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-70705369705334D6' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  70705369705334D6
	else
	  search --no-floppy --fs-uuid --set=root 70705369705334D6
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda5)' --class windows --class os $menuentry_id_option 'osprober-chain-01CE966381257F10' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  01CE966381257F10
	else
	  search --no-floppy --fs-uuid --set=root 01CE966381257F10
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
UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=34b63990-c920-43b3-9bf1-60d6570e7823 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda6: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda2


00000000  31 00 2e 00 43 00 4d 00  44 00 50 00 00 00 00 00  |1...C.M.D.P.....|
00000010  d2 28 00 00 00 00 01 00  60 00 4e 00 00 00 00 00  |.(......`.N.....|
00000020  2d 00 00 00 00 00 01 00  6a a9 e9 c4 ed 57 cc 01  |-.......j....W..|
00000030  2a 6c ee c4 ed 57 cc 01  2a 6c ee c4 ed 57 cc 01  |*l...W..*l...W..|
00000040  6a a9 e9 c4 ed 57 cc 01  00 80 03 00 00 00 00 00  |j....W..........|
00000050  5e 7f 03 00 00 00 00 00  20 00 00 00 00 00 00 00  |^....... .......|
00000060  06 03 68 00 70 00 2e 00  69 00 63 00 6f 00 35 00  |..h.p...i.c.o.5.|
00000070  1c 2f 00 00 00 00 01 00  68 00 52 00 00 00 00 00  |./......h.R.....|
00000080  2d 00 00 00 00 00 01 00  06 f4 e0 e8 ed 57 cc 01  |-............W..|
00000090  66 55 e3 e8 ed 57 cc 01  66 55 e3 e8 ed 57 cc 01  |fU...W..fU...W..|
000000a0  06 f4 e0 e8 ed 57 cc 01  00 10 00 00 00 00 00 00  |.....W..........|
000000b0  61 07 00 00 00 00 00 00  20 00 00 00 00 00 00 00  |a....... .......|
000000c0  08 01 48 00 50 00 2e 00  74 00 68 00 65 00 6d 00  |..H.P...t.h.e.m.|
000000d0  65 00 2e 00 63 00 6d 00  1c 2f 00 00 00 00 01 00  |e...c.m../......|
000000e0  70 00 5a 00 00 00 00 00  2d 00 00 00 00 00 01 00  |p.Z.....-.......|
000000f0  06 f4 e0 e8 ed 57 cc 01  66 55 e3 e8 ed 57 cc 01  |.....W..fU...W..|
00000100  66 55 e3 e8 ed 57 cc 01  06 f4 e0 e8 ed 57 cc 01  |fU...W.......W..|
00000110  00 10 00 00 00 00 00 00  61 07 00 00 00 00 00 00  |........a.......|
00000120  20 00 00 00 00 00 00 00  0c 02 48 00 50 00 31 00  | .........H.P.1.|
00000130  31 00 36 00 36 00 7e 00  31 00 2e 00 54 00 48 00  |1.6.6.~.1...T.H.|
00000140  45 00 64 00 00 00 00 00  1e 2f 00 00 00 00 01 00  |E.d....../......|
00000150  68 00 58 00 00 00 00 00  2d 00 00 00 00 00 01 00  |h.X.....-.......|
00000160  c7 b6 e5 e8 ed 57 cc 01  27 18 e8 e8 ed 57 cc 01  |.....W..'....W..|
00000170  27 18 e8 e8 ed 57 cc 01  c7 b6 e5 e8 ed 57 cc 01  |'....W.......W..|
00000180  00 10 00 00 00 00 00 00  61 07 00 00 00 00 00 00  |........a.......|
00000190  20 00 00 00 00 00 00 00  0b 01 48 00 50 00 41 00  | .........H.P.A.|
000001a0  4b 00 53 00 2e 00 74 00  68 00 65 00 6d 00 65 00  |K.S...t.h.e.m.e.|
000001b0  1e 2f 00 00 00 00 01 00  68 00 58 00 00 00 00 01  |./......h.X.....|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 e0 f0 82 25 00 fe  |.............%..|
000001d0  ff ff 05 fe ff ff e2 f0  82 25 e0 8e ed 11 00 00  |.........%......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-MeyBzemo/Tmp_Log: No such file or directory



```

---

### Post by yancek on 2019-01-28
The Kubuntu site indicates 14.04LTS has 5 years support which I would expect means it could be upgraded to 16.04 then 18.04.  Don't use it myself so am not sure.

[https://kubuntu.org/news/kubuntu-14-04-lts/](https://kubuntu.org/news/kubuntu-14-04-lts/)

If you do a new install and want to keep windows 7 (which is currently a Legacy install) you should do a Legacy install of Kubuntu rather than EFI and select to install the new Kubuntu to sda6 and Grub to /dev/sda.  Some general principles on problems mixing UEFI/Legacy are xplained at the Ubuntu site at the link below.  

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-01-28
Post this, if any partitions with data not mounted make sure they are mounted by clicking on them with file browser.

df -H

That will show amount of space used. Windows likes to have 30% free in its NTFS partition to work well. It gets slower as it fills and at 10% free, you just about cannot do a defrag as no working room to move files around.

---

### Post by mastablasta on 2019-01-30
> **yancek said:**
> The Kubuntu site indicates 14.04LTS has 5 years support which I would expect means it could be upgraded to 16.04 then 18.04.  Don't use it myself so am not sure.


Yes it should be easy enough, but:
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu)
 
> **14.04 LTS to 16.04 LTS upgrade**


**WARNING:** LTS to LTS upgrade to Xerus is currently problematic and should not be attempted. Please install a fresh copy of 16.04 instead. To prevent messages about upgrading, change Prompt=lts to Prompt=normal or Prompt=never in the /etc/update-manager/release-upgrades file.


and this sucks. i didn't see this before so i attempted the upgrade. what happened was not just damaged OS bot it also corrupted GRUB. additionally the 16.04 and 18.04 only have 3 years support on LTS. which sucks, but i guess i would have to live with it. though i wonder what would happened if i installed Ubuntu-desktop on it and then try the upgrade.

> 
If you do a new install and want to keep windows 7 (which is currently a Legacy install) you should do a Legacy install of Kubuntu rather than EFI and select to install the new Kubuntu to sda6 and Grub to /dev/sda. 

It's a BIOS system so legacy is the only way to go i guess. the issue here is if i have enough space for the grub install as grub increased in size i believe. or at least it needs a little bit more space than on the old install.


> **oldfred said:**
> Post this, if any partitions with data not mounted make sure they are mounted by clicking on them with file browser.

df -H

That will show amount of space used. Windows likes to have 30% free in its NTFS partition to work well. It gets slower as it fills and at 10% free, you just about cannot do a defrag as no working room to move files around.

```
udev            786M  4,0K  786M   1% /devtmpfs           161M  1,4M  159M   1% /run
/dev/sda6       142G   68G   67G  51% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
none            5,0M     0  5,0M   0% /run/lock
none            801M   80K  801M   1% /run/shm
none            100M   20K  100M   1% /run/user
/dev/sda5       301G  103G  198G  35% /media/gregor/01CE966381257F10
/dev/sda1       199M   29M  171M  15% /media/gregor/SYSTEM
/dev/sda4       4,0G  2,9G  1,1G  73% /media/gregor/HP_TOOLS

```

not much stuff installed and not much data.

attached is a screenshot of kde parted. sorry for the strange colours. it's the theme i am using. 

basically it's:
[LIST]
[*]windows 7 system boot partition,
[*]then the actual windows 7 install,
[*]then linux & swap
[*]then windows 7 recovery partition
[*]and finally the HP tools partition that includes "fast boot" OS for quick broswing.... anyway it's a linux of sorts that is booted by a press of a button and also it has some HP system maintenance tools & drivers backed up there i believe. the tools are quite good and there wasn't much bloatware preinstalled if any.
[/LIST]

---

