---
title: "No longer booting after recent update"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by DalekClock on 2015-07-14
I am dual-booting Ubuntu 15.04 and Windows 8.1 on my Toshiba laptop. I installed updates to Ubuntu on Monday, and now it boots straight into Windows with no GRUB menu. I have tried using Boot-repair but this does nothing, and Secure Boot was disabled in the BIOS (I don't think it's UEFI even though WUBI wouldn't accept it) when I first installed Ubuntu.

---

### Post by Vladlenin5000 on 2015-07-14
Have you installed using WUBI? If so, two questions:

1. Why?
2. How? :p
The common knowledge is that it doesn't work in Windows 8.1.

---

### Post by DalekClock on 2015-07-14
I didn't use WUBI in the end.

---

### Post by oldfred on 2015-07-14
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Vladlenin5000 on 2015-07-14
Better post the report from Boot-Repair so we know how is it now. Report only.
I've been reading some advices against using the standard solutions/workarounds Boot-Repair implements.

---

### Post by DalekClock on 2015-07-14
Here is the report:
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/bcd

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/toshiba/Boot/bootmgfw.efi 
                       /EFI/toshiba/Boot/bootmgr.efi 
                       /EFI/toshiba/Boot/memtest.efi 
                       /boot-sav/log/2015-06-10__14h50boot-repair00/sdb2/bootx
                       64.efi

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 931.5 GiB, 1000204885504 bytes, 1953525167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       923,647       921,600 Windows Recovery Environment (Windows)
/dev/sdb2         923,648     1,456,127       532,480 EFI System partition
/dev/sdb3       1,456,128     1,718,271       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb4       1,718,272   210,716,671   208,998,400 Data partition (Windows/Linux)
/dev/sdb5     210,716,672   211,433,471       716,800 Windows Recovery Environment (Windows)
/dev/sdb6     211,433,472   646,851,464   435,417,993 Data partition (Windows/Linux)
/dev/sdb7     953,661,440   976,773,119    23,111,680 Windows Recovery Environment (Windows)
/dev/sdb8     646,852,608   945,516,543   298,663,936 Data partition (Linux)
/dev/sdb9     945,516,544   953,661,439     8,144,896 Swap partition (Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3.6 GiB, 3869544448 bytes, 7557704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048     7,557,703     7,555,656   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4A70AC4B70AC4015                       ntfs       Seagate Expansion Drive
/dev/sdb1        4842A99242A984F2                       ntfs       System
/dev/sdb2        FCAA-E40A                              vfat       
/dev/sdb3        0444AC6C44AC6262                       ntfs       
/dev/sdb4        860EAE880EAE713B                       ntfs       System
/dev/sdb5        3484B84684B80C7C                       ntfs       
/dev/sdb6        04DAD921DAD90FB2                       ntfs       Data
/dev/sdb7        3454B27754B23C04                       ntfs       Recovery
/dev/sdb8        2f1597e5-c6e2-492e-b553-43efe9f76b9e   ext4       
/dev/sdb9        e9e44c62-3afa-48a4-bc25-e112eafd90e4   swap       
/dev/sdc1        0CE5-36DB                              vfat       UBUNTU 15_0

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 14 08:31 ata-ST1000LM024_HN-M101MBB_S30CJ9BF504391 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 14 08:33 ata-ST1000LM024_HN-M101MBB_S30CJ9BF504391-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Jul 14 08:32 ata-TOSHIBA_MQ01ABF050_33BAC7BDT -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 14 08:33 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jul 14 08:32 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jul 14 08:33 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jul 14 08:33 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Jul 14 08:33 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Jul 14 08:33 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Jul 14 08:33 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part7 -> ../../sdb7
lrwxrwxrwx 1 root root 10 Jul 14 08:32 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part8 -> ../../sdb8
lrwxrwxrwx 1 root root 10 Jul 14 08:32 ata-TOSHIBA_MQ01ABF050_33BAC7BDT-part9 -> ../../sdb9
lrwxrwxrwx 1 root root  9 Jul 14  2015 ata-TSSTcorp_CDDVDW_SN-208DN_R9226GKD2008WL -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 14 08:31 usb-Kingston_DataTraveler_G3_001CC0EC32FEFBA0470F2536-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul 14 08:31 usb-Kingston_DataTraveler_G3_001CC0EC32FEFBA0470F2536-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jul 14 08:32 wwn-0x4439603068531920896x -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 14 08:33 wwn-0x4439603068531920896x-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jul 14 08:32 wwn-0x4439603068531920896x-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jul 14 08:33 wwn-0x4439603068531920896x-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jul 14 08:33 wwn-0x4439603068531920896x-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Jul 14 08:33 wwn-0x4439603068531920896x-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Jul 14 08:33 wwn-0x4439603068531920896x-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Jul 14 08:33 wwn-0x4439603068531920896x-part7 -> ../../sdb7
lrwxrwxrwx 1 root root 10 Jul 14 08:32 wwn-0x4439603068531920896x-part8 -> ../../sdb8
lrwxrwxrwx 1 root root 10 Jul 14 08:32 wwn-0x4439603068531920896x-part9 -> ../../sdb9
lrwxrwxrwx 1 root root  9 Jul 14 08:31 wwn-0x6718259163626098688x -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 14 08:33 wwn-0x6718259163626098688x-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb8        /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb8/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd1,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
else
  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
	else
	  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
	fi
	linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.19.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
	menuentry 'Ubuntu, with Linux 3.19.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-advanced-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-22-generic ...'
		linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-22-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-init-upstart-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-22-generic ...'
		linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-22-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-recovery-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-22-generic ...'
		linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-22-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-advanced-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-21-generic ...'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-init-upstart-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-21-generic ...'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-recovery-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-21-generic ...'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-advanced-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-20-generic ...'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-init-upstart-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-20-generic ...'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-recovery-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-20-generic ...'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-advanced-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-18-generic ...'
		linux	/boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-init-upstart-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-18-generic ...'
		linux	/boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-recovery-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-18-generic ...'
		linux	/boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-init-upstart-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-2f1597e5-c6e2-492e-b553-43efe9f76b9e' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  2f1597e5-c6e2-492e-b553-43efe9f76b9e
		else
		  search --no-floppy --fs-uuid --set=root 2f1597e5-c6e2-492e-b553-43efe9f76b9e
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic root=UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root FCAA-E40A
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root FCAA-E40A
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root FCAA-E40A
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "EFI/toshiba/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root FCAA-E40A
chainloader (${root})/EFI/toshiba/Boot/bootmgfw.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sdb2)' --class windows --class os $menuentry_id_option 'osprober-efi-FCAA-E40A' {
	insmod part_gpt
	insmod fat
	set root='hd1,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  FCAA-E40A
	else
	  search --no-floppy --fs-uuid --set=root FCAA-E40A
	fi
	chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb8 during installation
UUID=2f1597e5-c6e2-492e-b553-43efe9f76b9e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
#UUID=FCAA-E40A  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdb9 during installation
UUID=e9e44c62-3afa-48a4-bc25-e112eafd90e4 none            swap    sw              0       0
UUID=FCAA-E40A	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

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

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/5331/mounts) leaked on lvs invocation. Parent PID 23082: bash
File descriptor 63 (pipe:[62029]) leaked on lvs invocation. Parent PID 23082: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-07-14__08h31 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in live-session (Ubuntu 15.04, vivid, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access /home/usr/.config: No such file or directory
Unmount sda1 from /media/ubuntu/Seagate Expansion Drive to avoid space incompatibilities

=================== os-prober:
/dev/sdb2@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sdb8:Ubuntu 15.04 (15.04):Ubuntu:linux

=================== blkid:
/dev/sda1: LABEL="Seagate Expansion Drive" UUID="4A70AC4B70AC4015" TYPE="ntfs" PARTUUID="f749e710-01"
/dev/sdb1: LABEL="System" UUID="4842A99242A984F2" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="c651612b-7b3f-11e2-84c5-cb0876c6d7af"
/dev/sdb2: UUID="FCAA-E40A" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="c6516133-7b3f-11e2-84c5-cb0876c6d7af"
/dev/sdb3: UUID="0444AC6C44AC6262" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="c6516135-7b3f-11e2-84c5-cb0876c6d7af"
/dev/sdb4: LABEL="System" UUID="860EAE880EAE713B" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="c651613d-7b3f-11e2-84c5-cb0876c6d7af"
/dev/sdb5: UUID="3484B84684B80C7C" TYPE="ntfs" PARTUUID="06af7dbb-36ca-4aca-8835-f36683a1f76e"
/dev/sdb6: LABEL="Data" UUID="04DAD921DAD90FB2" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="54b4159e-81d4-4d5b-a432-4d52d6ff2f88"
/dev/sdb7: LABEL="Recovery" UUID="3454B27754B23C04" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="0b82542d-7c69-4c32-9abc-b06d911a0911"
/dev/sdb8: UUID="2f1597e5-c6e2-492e-b553-43efe9f76b9e" TYPE="ext4" PARTUUID="4ce05aaa-423f-4b30-be58-9de7b045106b"
/dev/sdc1: LABEL="UBUNTU 15_0" UUID="0CE5-36DB" TYPE="vfat" PARTUUID="88c8300b-01"
/dev/loop0: TYPE="squashfs"
/dev/sdb9: UUID="e9e44c62-3afa-48a4-bc25-e112eafd90e4" TYPE="swap" PARTUUID="5d79de1a-b8d0-4af8-93ac-c4c7af0a3bbb"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sdb4.
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sdb2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sdb2/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sdb2/EFI/Boot/bootx64.efi
Presence of bkp file detected: /mnt/boot-sav/sdb2/EFI/Boot/bkpbootx64.efi

=================== /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 13 08:49 grub.d
total 80
-rwxr-xr-x 1 root root  9424 Jun 26 11:13 00_header
-rwxr-xr-x 1 root root  6058 Feb 11 19:53 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr  6 20:43 10_linux
-rwxr-xr-x 1 root root 11082 Apr  6 20:43 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar  6 16:23 20_memtest86+
-rwxr-xr-x 1 root root   604 Jun 10 14:51 25_custom
-rwxr-xr-x 1 root root 11692 Apr  6 20:43 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr  6 20:43 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  6 20:43 40_custom
-rwxr-xr-x 1 root root   216 Apr  6 20:43 41_custom
-rw-r--r-- 1 root root   483 Apr  6 20:43 README




=================== /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/etc/default/grub :

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



/boot/efi detected in the fstab of sdb8: UUID=FCAA-E40A	 (sdb2)

=================== efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 2001,0003,0000,0004,2003,2002
Boot0000* ubuntu	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIubuntushimx64.efi)
Boot0001* EFI Network 0 for IPv6 (7C-05-07-3B-14-B5) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(7c05073b14b5,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI Network 0 for IPv4 (7C-05-07-3B-14-B5) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(7c05073b14b5,0)RC
Boot0003* Windows Boot Manager	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* Ubuntu	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIubuntugrubx64.efi)RC
Boot0005* EFI USB Device (KingstonDataTraveler G3)	ACPI(a0341d0,0)PCI(1a,0)USB(0,0)USB(1,0)HD(1,800,734a48,88c8300b)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb1.
sdb2	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb2.
sdb3	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb3.
sdb4	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb4.
sdb5	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb5.
sdb6	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb6.
sdb7	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb7.
sdb8	: sdb,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes
sdb	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: Seagate Expansion (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size    File system     Name                  Flags
1      1049kB  473MB  472MB   ntfs            Basic data partition  hidden, diag
2      473MB   746MB  273MB   fat32           Basic data partition  boot, esp
3      746MB   880MB  134MB   ntfs            Basic data partition  msftres
4      880MB   108GB  107GB   ntfs            Basic data partition  msftdata
5      108GB   108GB  367MB   ntfs                                  hidden, diag
6      108GB   331GB  223GB   ntfs            Basic data partition  msftdata
8      331GB   484GB  153GB   ext4
9      484GB   488GB  4170MB  linux-swap(v1)
7      488GB   500GB  11.8GB  ntfs            Basic data partition  hidden, diag


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdc: 3870MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  3870MB  3868MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:Seagate Expansion:;
1:1049kB:1000GB:1000GB:ntfs::;

BYT;
/dev/sdb:500GB:scsi:512:512:gpt:ATA TOSHIBA MQ01ABF0:;
1:1049kB:473MB:472MB:ntfs:Basic data partition:hidden, diag;
2:473MB:746MB:273MB:fat32:Basic data partition:boot, esp;
3:746MB:880MB:134MB:ntfs:Basic data partition:msftres;
4:880MB:108GB:107GB:ntfs:Basic data partition:msftdata;
5:108GB:108GB:367MB:ntfs::hidden, diag;
6:108GB:331GB:223GB:ntfs:Basic data partition:msftdata;
8:331GB:484GB:153GB:ext4::;
9:484GB:488GB:4170MB:linux-swap(v1)::;
7:488GB:500GB:11.8GB:ntfs:Basic data partition:hidden, diag;

BYT;
/dev/sdc:3870MB:scsi:512:512:msdos:Kingston DataTraveler G3:;
1:1049kB:3870MB:3868MB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL                   MODEL            UUID
sda   disk          931.5G                         Expansion
sda1  part ntfs     931.5G Seagate Expansion Drive                  4A70AC4B70AC4015
sdb   disk          465.8G                         TOSHIBA MQ01ABF0
sdb1  part ntfs       450M System                                   4842A99242A984F2
sdb2  part vfat       260M                                          FCAA-E40A
sdb3  part ntfs       128M                                          0444AC6C44AC6262
sdb4  part ntfs      99.7G System                                   860EAE880EAE713B
sdb5  part ntfs       350M                                          3484B84684B80C7C
sdb6  part ntfs     207.6G Data                                     04DAD921DAD90FB2
sdb7  part ntfs        11G Recovery                                 3454B27754B23C04
sdb8  part ext4     142.4G                                          2f1597e5-c6e2-492e-b553-43efe9f76b9e
sdb9  part swap       3.9G                                          e9e44c62-3afa-48a4-bc25-e112eafd90e4
sdc   disk            3.6G                         DataTraveler G3
sdc1  part vfat       3.6G UBUNTU 15_0                              0CE5-36DB
sr0   rom            1024M                         CDDVDW SN-208DN
loop0 loop squashfs     1G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdb2     1  0  0         /mnt/boot-sav/sdb2
sdb3     1  0  0         /mnt/boot-sav/sdb3
sdb4     1  0  0         /mnt/boot-sav/sdb4
sdb5     1  0  0         /mnt/boot-sav/sdb5
sdb6     1  0  0         /mnt/boot-sav/sdb6
sdb7     1  0  0         /mnt/boot-sav/sdb7
sdb8     1  0  0         /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e
sdb9     1  0  0         [SWAP]
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1950220k,nr_inodes=487555,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=392496k,mode=755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=392496k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdb8 on /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb3 on /mnt/boot-sav/sdb3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb4 on /mnt/boot-sav/sdb4 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb5 on /mnt/boot-sav/sdb5 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb6 on /mnt/boot-sav/sdb6 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb7 on /mnt/boot-sav/sdb7 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7 sdb8 sdb9 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet hugepages i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 initctl input kmsg kvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7 sdb8 sdb9 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 xconsole zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 70 74 00 00 00 00  |.........Wpt....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  15 40 ac 70 4b ac 70 4a  |.........@.pK.pJ|
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

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 0f 0e 00 00 00 00 00  |................|
00000030  ff 95 00 00 00 00 00 00  ff e0 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  f2 84 a9 42 92 a9 42 48  |...........B..BH|
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

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 18 0e 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 6d 18 00 00  |. ..........m...|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 0a e4 aa fc 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 16 00  |........?....8..|
00000020  00 00 00 00 80 00 80 00  ff ff 03 00 00 00 00 00  |................|
00000030  aa 2a 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.*..............|
00000040  f6 00 00 00 01 00 00 00  62 62 ac 44 6c ac 44 04  |........bb.Dl.D.|
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

=================== hexdump -n512 -C /dev/sdb4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 1a 00  |........?....8..|
00000020  00 00 00 00 80 00 80 00  ff 0f 75 0c 00 00 00 00  |..........u.....|
00000030  00 00 0c 00 00 00 00 00  ff ff 9f 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  3b 71 ae 0e 88 ae 0e 86  |........;q......|
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

=================== hexdump -n512 -C /dev/sdb5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 8f 0c  |........?....H..|
00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|
00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|
00000040  f6 00 00 00 01 00 00 00  7c 0c b8 84 46 b8 84 34  |........|...F..4|
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

=================== hexdump -n512 -C /dev/sdb6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 9a 0c  |........?....8..|
00000020  00 00 00 00 80 00 80 00  88 f3 f3 19 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  b2 0f d9 da 21 d9 da 04  |............!...|
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

=================== hexdump -n512 -C /dev/sdb7
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b8 d7 38  |........?......8|
00000020  00 00 00 00 80 00 80 00  ff a7 60 01 00 00 00 00  |..........`.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  04 3c b2 54 77 b2 54 34  |.........<.Tw.T4|
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

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     384M   11M  373M   3% /run
/dev/sdc1      vfat      3.6G  1.1G  2.6G  30% /cdrom
/dev/loop0     squashfs  1.1G  1.1G     0 100% /rofs
/cow           overlay   1.9G   92M  1.8G   5% /
tmpfs          tmpfs     1.9G   84K  1.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     1.9G  1.2M  1.9G   1% /tmp
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     384M   76K  384M   1% /run/user/999
/dev/sdb8      ext4      141G  6.8G  127G   6% /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e
/dev/sda1      fuseblk   932G  262G  671G  29% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk   450M  355M   96M  79% /mnt/boot-sav/sdb1
/dev/sdb2      vfat      256M   61M  196M  24% /mnt/boot-sav/sdb2
/dev/sdb3      fuseblk   128M   14M  115M  11% /mnt/boot-sav/sdb3
/dev/sdb4      fuseblk   100G   85G   16G  85% /mnt/boot-sav/sdb4
/dev/sdb5      fuseblk   350M  276M   75M  79% /mnt/boot-sav/sdb5
/dev/sdb6      fuseblk   208G   65G  144G  32% /mnt/boot-sav/sdb6
/dev/sdb7      fuseblk    12G   11G  633M  95% /mnt/boot-sav/sdb7

=================== fdisk -l:

Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C651612A-7B3F-11E2-84C5-CB0876C6D7AF

Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    923647    921600   450M Windows recovery environment
/dev/sdb2     923648   1456127    532480   260M EFI System
/dev/sdb3    1456128   1718271    262144   128M Microsoft reserved
/dev/sdb4    1718272 210716671 208998400  99.7G Microsoft basic data
/dev/sdb5  210716672 211433471    716800   350M Windows recovery environment
/dev/sdb6  211433472 646851464 435417993 207.6G Microsoft basic data
/dev/sdb7  953661440 976773119  23111680    11G Windows recovery environment
/dev/sdb8  646852608 945516543 298663936 142.4G Linux filesystem
/dev/sdb9  945516544 953661439   8144896   3.9G Linux swap

Partition table entries are not in disk order.
Disk /dev/sdc: 3.6 GiB, 3869544448 bytes, 7557704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x88c8300b

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *     2048 7557703 7555656  3.6G  c W95 FAT32 (LBA)

Disk /dev/sda: 931.5 GiB, 1000204885504 bytes, 1953525167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xf749e710

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1        2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sdb8, using the following options:        sdb2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file  restore-efi-backups


rm /mnt/boot-sav/sdb2/efi/Boot/bootx64.efi
Quantity of real Windows: 1
Mount sdb2 on /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi
ls sdb2/efi: /toshiba/Boot/zh-TW /toshiba/Boot/zh-HK /toshiba/Boot/zh-CN /toshiba/Boot/uk-UA /toshiba/Boot/tr-TR /toshiba/Boot/sv-SE /toshiba/Boot/sr-Latn-CS /toshiba/Boot/sl-SI /toshiba/Boot/sk-SK /toshiba/Boot/ru-RU /toshiba/Boot/ro-RO /toshiba/Boot/Resources /toshiba/Boot/qps-ploc /toshiba/Boot/pt-PT /toshiba/Boot/pt-BR /toshiba/Boot/pl-PL /toshiba/Boot/nl-NL /toshiba/Boot/nb-NO /toshiba/Boot/memtest.efi /toshiba/Boot/lv-LV /toshiba/Boot/lt-LT /toshiba/Boot/ko-KR /toshiba/Boot/ja-JP /toshiba/Boot/it-IT /toshiba/Boot/hu-HU /toshiba/Boot/hr-HR /toshiba/Boot/fr-FR /toshiba/Boot/Fonts /toshiba/Boot/fi-FI /toshiba/Boot/et-EE /toshiba/Boot/es-ES /toshiba/Boot/en-US /toshiba/Boot/en-GB /toshiba/Boot/el-GR /toshiba/Boot/de-DE /toshiba/Boot/da-DK /toshiba/Boot/cs-CZ /toshiba/Boot/boot.stl /toshiba/Boot/BOOTSTAT.DAT /toshiba/Boot/bootmgr.efi /toshiba/Boot/bootmgfw.efi /toshiba/Boot/bg-BG /toshiba/Boot/bcd.LOG /toshiba/Boot/bcd /Microsoft/Boot/zh-TW /Microsoft/Boot/zh-HK /Microsoft/Boot/zh-CN /Microsoft/Boot/uk-UA /Microsoft/Boot/tr-TR /Microsoft/Boot/sv-SE /Microsoft/Boot/sr-Latn-RS /Microsoft/Boot/sr-Latn-CS /Microsoft/Boot/sl-SI /Microsoft/Boot/sk-SK /Microsoft/Boot/ru-RU /Microsoft/Boot/ro-RO /Microsoft/Boot/Resources /Microsoft/Boot/qps-ploc /Microsoft/Boot/pt-PT /Microsoft/Boot/pt-BR /Microsoft/Boot/pl-PL /Microsoft/Boot/nl-NL /Microsoft/Boot/nb-NO /Microsoft/Boot/memtest.efi /Microsoft/Boot/lv-LV /Microsoft/Boot/lt-LT /Microsoft/Boot/ko-KR /Microsoft/Boot/ja-JP /Microsoft/Boot/it-IT /Microsoft/Boot/hu-HU /Microsoft/Boot/hr-HR /Microsoft/Boot/fr-FR /Microsoft/Boot/Fonts /Microsoft/Boot/fi-FI /Microsoft/Boot/et-EE /Microsoft/Boot/es-ES /Microsoft/Boot/en-US /Microsoft/Boot/en-GB /Microsoft/Boot/el-GR /Microsoft/Boot/de-DE /Microsoft/Boot/da-DK /Microsoft/Boot/cs-CZ /Microsoft/Boot/boot.stl /Microsoft/Boot/BOOTSTAT.DAT /Microsoft/Boot/bootmgr.efi /Microsoft/Boot/bootmgfw.efi /Microsoft/Boot/bg-BG /Microsoft/Boot/BCD.LOG2 /Microsoft/Boot/BCD.LOG1 /Microsoft/Boot/BCD.LOG /Microsoft/Boot/BCD /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /toshiba/Boot /Microsoft/Boot /Boot/bootx64.efi
ls sdb2: boot-sav
BOOTSECT.BAK
EFI  . Please report this message to boot.repair@gmail.com

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
Subsystem: Toshiba America Info Systems Device [1179:fb30]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-22ubuntu1.1,grub-install (GRUB) 2.

chroot /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 2001,0003,0000,0004,2003,2002
Boot0000* ubuntu	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIubuntushimx64.efi)
Boot0001* EFI Network 0 for IPv6 (7C-05-07-3B-14-B5) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(7c05073b14b5,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI Network 0 for IPv4 (7C-05-07-3B-14-B5) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(7c05073b14b5,0)RC
Boot0003* Windows Boot Manager	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* Ubuntu	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIubuntugrubx64.efi)RC
Boot0005* EFI USB Device (KingstonDataTraveler G3)	ACPI(a0341d0,0)PCI(1a,0)USB(0,0)USB(1,0)HD(1,800,734a48,88c8300b)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

chroot /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e uname -r
Kernel: 3.19.0-15-generic

Reinstall the grub-efi-amd64-signed of sdb8
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
mv 25_custom
ls sdb2/efi: /toshiba/Boot/zh-TW /toshiba/Boot/zh-HK /toshiba/Boot/zh-CN /toshiba/Boot/uk-UA /toshiba/Boot/tr-TR /toshiba/Boot/sv-SE /toshiba/Boot/sr-Latn-CS /toshiba/Boot/sl-SI /toshiba/Boot/sk-SK /toshiba/Boot/ru-RU /toshiba/Boot/ro-RO /toshiba/Boot/Resources /toshiba/Boot/qps-ploc /toshiba/Boot/pt-PT /toshiba/Boot/pt-BR /toshiba/Boot/pl-PL /toshiba/Boot/nl-NL /toshiba/Boot/nb-NO /toshiba/Boot/memtest.efi /toshiba/Boot/lv-LV /toshiba/Boot/lt-LT /toshiba/Boot/ko-KR /toshiba/Boot/ja-JP /toshiba/Boot/it-IT /toshiba/Boot/hu-HU /toshiba/Boot/hr-HR /toshiba/Boot/fr-FR /toshiba/Boot/Fonts /toshiba/Boot/fi-FI /toshiba/Boot/et-EE /toshiba/Boot/es-ES /toshiba/Boot/en-US /toshiba/Boot/en-GB /toshiba/Boot/el-GR /toshiba/Boot/de-DE /toshiba/Boot/da-DK /toshiba/Boot/cs-CZ /toshiba/Boot/boot.stl /toshiba/Boot/BOOTSTAT.DAT /toshiba/Boot/bootmgr.efi /toshiba/Boot/bootmgfw.efi /toshiba/Boot/bg-BG /toshiba/Boot/bcd.LOG /toshiba/Boot/bcd /Microsoft/Boot/zh-TW /Microsoft/Boot/zh-HK /Microsoft/Boot/zh-CN /Microsoft/Boot/uk-UA /Microsoft/Boot/tr-TR /Microsoft/Boot/sv-SE /Microsoft/Boot/sr-Latn-RS /Microsoft/Boot/sr-Latn-CS /Microsoft/Boot/sl-SI /Microsoft/Boot/sk-SK /Microsoft/Boot/ru-RU /Microsoft/Boot/ro-RO /Microsoft/Boot/Resources /Microsoft/Boot/qps-ploc /Microsoft/Boot/pt-PT /Microsoft/Boot/pt-BR /Microsoft/Boot/pl-PL /Microsoft/Boot/nl-NL /Microsoft/Boot/nb-NO /Microsoft/Boot/memtest.efi /Microsoft/Boot/lv-LV /Microsoft/Boot/lt-LT /Microsoft/Boot/ko-KR /Microsoft/Boot/ja-JP /Microsoft/Boot/it-IT /Microsoft/Boot/hu-HU /Microsoft/Boot/hr-HR /Microsoft/Boot/fr-FR /Microsoft/Boot/Fonts /Microsoft/Boot/fi-FI /Microsoft/Boot/et-EE /Microsoft/Boot/es-ES /Microsoft/Boot/en-US /Microsoft/Boot/en-GB /Microsoft/Boot/el-GR /Microsoft/Boot/de-DE /Microsoft/Boot/da-DK /Microsoft/Boot/cs-CZ /Microsoft/Boot/boot.stl /Microsoft/Boot/BOOTSTAT.DAT /Microsoft/Boot/bootmgr.efi /Microsoft/Boot/bootmgfw.efi /Microsoft/Boot/bg-BG /Microsoft/Boot/BCD.LOG2 /Microsoft/Boot/BCD.LOG1 /Microsoft/Boot/BCD.LOG /Microsoft/Boot/BCD /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /toshiba/Boot /Microsoft/Boot /Boot/bootx64.efi
ls sdb2: boot-sav
BOOTSECT.BAK
EFI  . Please report this message to boot.repair@gmail.com
df /dev/sdb2
Save and rename /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/Boot/bootx64.efi (/media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/ubuntu/shimx64.efi /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/Boot/bootx64.efi
ls sdb2/efi: /toshiba/Boot/zh-TW /toshiba/Boot/zh-HK /toshiba/Boot/zh-CN /toshiba/Boot/uk-UA /toshiba/Boot/tr-TR /toshiba/Boot/sv-SE /toshiba/Boot/sr-Latn-CS /toshiba/Boot/sl-SI /toshiba/Boot/sk-SK /toshiba/Boot/ru-RU /toshiba/Boot/ro-RO /toshiba/Boot/Resources /toshiba/Boot/qps-ploc /toshiba/Boot/pt-PT /toshiba/Boot/pt-BR /toshiba/Boot/pl-PL /toshiba/Boot/nl-NL /toshiba/Boot/nb-NO /toshiba/Boot/memtest.efi /toshiba/Boot/lv-LV /toshiba/Boot/lt-LT /toshiba/Boot/ko-KR /toshiba/Boot/ja-JP /toshiba/Boot/it-IT /toshiba/Boot/hu-HU /toshiba/Boot/hr-HR /toshiba/Boot/fr-FR /toshiba/Boot/Fonts /toshiba/Boot/fi-FI /toshiba/Boot/et-EE /toshiba/Boot/es-ES /toshiba/Boot/en-US /toshiba/Boot/en-GB /toshiba/Boot/el-GR /toshiba/Boot/de-DE /toshiba/Boot/da-DK /toshiba/Boot/cs-CZ /toshiba/Boot/boot.stl /toshiba/Boot/BOOTSTAT.DAT /toshiba/Boot/bootmgr.efi /toshiba/Boot/bootmgfw.efi /toshiba/Boot/bg-BG /toshiba/Boot/bcd.LOG /toshiba/Boot/bcd /Microsoft/Boot/zh-TW /Microsoft/Boot/zh-HK /Microsoft/Boot/zh-CN /Microsoft/Boot/uk-UA /Microsoft/Boot/tr-TR /Microsoft/Boot/sv-SE /Microsoft/Boot/sr-Latn-RS /Microsoft/Boot/sr-Latn-CS /Microsoft/Boot/sl-SI /Microsoft/Boot/sk-SK /Microsoft/Boot/ru-RU /Microsoft/Boot/ro-RO /Microsoft/Boot/Resources /Microsoft/Boot/qps-ploc /Microsoft/Boot/pt-PT /Microsoft/Boot/pt-BR /Microsoft/Boot/pl-PL /Microsoft/Boot/nl-NL /Microsoft/Boot/nb-NO /Microsoft/Boot/memtest.efi /Microsoft/Boot/lv-LV /Microsoft/Boot/lt-LT /Microsoft/Boot/ko-KR /Microsoft/Boot/ja-JP /Microsoft/Boot/it-IT /Microsoft/Boot/hu-HU /Microsoft/Boot/hr-HR /Microsoft/Boot/fr-FR /Microsoft/Boot/Fonts /Microsoft/Boot/fi-FI /Microsoft/Boot/et-EE /Microsoft/Boot/es-ES /Microsoft/Boot/en-US /Microsoft/Boot/en-GB /Microsoft/Boot/el-GR /Microsoft/Boot/de-DE /Microsoft/Boot/da-DK /Microsoft/Boot/cs-CZ /Microsoft/Boot/boot.stl /Microsoft/Boot/BOOTSTAT.DAT /Microsoft/Boot/bootmgr.efi /Microsoft/Boot/bootmgfw.efi /Microsoft/Boot/bg-BG /Microsoft/Boot/BCD.LOG2 /Microsoft/Boot/BCD.LOG1 /Microsoft/Boot/BCD.LOG /Microsoft/Boot/BCD /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /toshiba/Boot /Microsoft/Boot /Boot/bootx64.efi /Boot/bkpbootx64.efi
ls sdb2: boot-sav
BOOTSECT.BAK
EFI  . Please report this message to boot.repair@gmail.com
Add /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi efi entries in /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/etc/grub.d/25_custom
Adding custom /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/Boot/bkpbootx64.efi
sdb2/bkpbootx64.efi already added
Adding custom /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/ubuntu/MokManager.efi
sdb2/bootmgfw.efi already added
Adding custom /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e/boot/efi/EFI/toshiba/Boot/bootmgfw.efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0

chroot /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0000,2001,0003,2003,2002
Boot0000* ubuntu	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIubuntushimx64.efi)
Boot0001* EFI Network 0 for IPv6 (7C-05-07-3B-14-B5) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(7c05073b14b5,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI Network 0 for IPv4 (7C-05-07-3B-14-B5) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(7c05073b14b5,0)RC
Boot0003* Windows Boot Manager	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0005* EFI USB Device (KingstonDataTraveler G3)	ACPI(a0341d0,0)PCI(1a,0)USB(0,0)USB(1,0)HD(1,800,734a48,88c8300b)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

chroot /media/ubuntu/2f1597e5-c6e2-492e-b553-43efe9f76b9e update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found Windows Boot Manager on /dev/sdb2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sdb8/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (500GB) disk!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
```

---

### Post by oldfred on 2015-07-14
It is UEFI and for whatever reason your Seagate drive is sda. I assume that is an external drive?

Some Toshiba PCs need work around.

Most copy /EFI/ubuntu into /EFI/boot, backup bootx64.efi, and rename grubx64.efi or shimx64.efi to bootx64.efi. The in UEFI boot hard drive entry.

 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

Also in link below in my signature are command line ways to copy files.

---

### Post by DalekClock on 2015-07-15
I tried to mount the EFI partition from a Live USB, but I just got this:
```
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```
When I tried using FUSERMOUNT, it just said "old mounting style not supported".

---

### Post by oldfred on 2015-07-15
The efi partition is not NTFS, but FAT32(vfat).
Is error because you used wrong partition for efi? Shown as sdb2 in summary report.

And if you cannot mount your NTFS, does it need chkdsk or did you leave it hibernated? Windows 8 is always hibernated as its fast startup is just hibernation. And after a resize NTFS always needs chkdsk.

---

### Post by DalekClock on 2015-07-15
What do you mean by 'leave it hibernated'?

---

### Post by oldfred on 2015-07-15
WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast startup is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavailable, make sure fast startup is unchecked 
powercfg /h off

---

### Post by DalekClock on 2015-07-15
As far as I can tell, the hibernation problem only seems to apply to people who use a partition shared between OSes, which I don't use.

Anyway, I managed to mount the boot partition, but when I tried to follow the commands in the 'UEFI' tips, it wouldn't recognise "EFIBOOTMGR" at all. I have been able to boot into Ubuntu through Windows Advanced Restart, but powering on still goes straight to Windows.

---

### Post by oldfred on 2015-07-15
The efibootmgr is a terminal command and only in UEFI installs.

Anytime you see sudo we are posting a terminal command. Open terminal and run:
sudo efibootmgr -v

---

### Post by DalekClock on 2015-07-15
When I run that command I get:
```
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,0000,0004,2003,2001,2002
Boot0000* ubuntu	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(\EFI\ubuntu\shimx64.efi)
Boot0001* EFI Network 0 for IPv6 (**-**-**-**-**-**) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(************,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI Network 0 for IPv4 (**-**-**-**-**-**) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(MAC(************,0)RC
Boot0003* Windows Boot Manager	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...................
Boot0004* Ubuntu	HD(2,e1800,82000,c6516133-7b3f-11e2-84c5-cb0876c6d7af)File(\EFI\ubuntu\grubx64.efi)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

```

---

### Post by oldfred on 2015-07-15
You show 0003 Windows as default and both 0000 & 0004 Ubuntu.
Can you choose Ubuntu entry?

And you do not show a hard drive entry.
Did you create a /EFI/Boot/bootx64.efi which really is grub or shim?

If UEFI does not add a hard drive entry:
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
sudo efibootmgr -v

---

### Post by DalekClock on 2015-07-15
How do I change the boot order? In the UEFI setup, it only gives me the option for the hard disk and not individual partitions.

---

### Post by oldfred on 2015-07-15
Most systems have in UEFI boot tab a way to change boot order. Some have listings of first, second, etc, others show list and you use arrow key to move entries up & down.

You also can use efibootmgr.
see example #3
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)        Change boot order with efibootmgr
[URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr

[/URL]
 Envy M6 Change boot order [COLOR=#ff0000]sudo efibootmgr -o 2,1[/COLOR] post #23
[URL="http://ubuntuforums.org/showthread.php?t=2227889"]http://ubuntuforums.org/showthread.php?t=2227889


[/URL]

[URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]
[/URL]

---

### Post by DalekClock on 2015-07-15
With '-o', should I use the Boot____ number or does the AskUbuntu example use the order of boot numbers already there?

---

### Post by oldfred on 2015-07-15
You have to look at the output of your efibootmgr -v, then with -o parameter choose which you want first second etc.

I gather it can be all 4 char or just the last digit.

---

### Post by DalekClock on 2015-07-15
It now goes to the GRUB on startup. Thank you.

---

### Post by oldfred on 2015-07-15
You are welcome, glad that worked. :)

---

