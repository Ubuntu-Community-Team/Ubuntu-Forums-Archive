---
title: "Installation with preinstalled Windows 10 (UEFI)- problem of boot-repair"
date: 2017-03-02
forum: Installation &amp; Upgrades
---

### Post by sb.ssj4 on 2017-03-02
Hello! I have installed Xubuntu 14.04 in my laptop which already has windows 10 installed in C drive (Asus X556U). However, whenever I try to load it by restarting my laptop, I automatically opens windows 10 without giving any options for choosing to boot Xubuntu or Windows 10. I did some research and I found out that it was UEFI which was installed. I also tried to restart in live mode and install boot-repair but it didnt work as it said that it requires to be used on EFI session. So I restart my laptop with the boot option where I selected "UEFI: &lt;&lt;name of the USB drive&gt;&gt;" but the same problem occured. It restarted windows 10 again. I have absolutely no idea what is happening and why it is happening. Please help. Thanks in advance. Here is the report that I received from boot repair:

```

[COLOR=#000000]Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016][/COLOR]

============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    683743232 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt7)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
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
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 7860156 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048       534,527       532,480 EFI System partition
/dev/sda2               534,528       567,295        32,768 Microsoft Reserved Partition (Windows)
/dev/sda3               567,296   389,689,343   389,122,048 Data partition (Windows/Linux)
/dev/sda4      R    389,689,344   390,711,295     1,021,952 Windows Recovery Environment (Windows)
/dev/sda5           390,711,296   683,742,207   293,030,912 Data partition (Windows/Linux)
/dev/sda6           683,743,232   683,745,279         2,048 BIOS Boot partition
/dev/sda7           683,745,280   968,916,991   285,171,712 Data partition (Linux)
/dev/sda8           968,916,992   976,771,071     7,854,080 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.5 GB, 15502147584 bytes
86 heads, 22 sectors/track, 16002 cylinders, total 30277632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    30,277,631    30,269,568   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DAA4-6936                              vfat       SYSTEM
/dev/sda3        828AA72F8AA71F23                       ntfs       OS
/dev/sda4        FA306EAC306E7015                       ntfs       RECOVERY
/dev/sda5        0E1A304F1A303655                       ntfs       DATA
/dev/sda7        882731c2-14c2-421d-8011-b61d0f37b562   ext4       
/dev/sda8        e4b97452-ead3-4dd6-93ae-e112effb7879   swap       
/dev/sdb1        AD5D-7634                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Mar  2 16:33 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  2 16:22 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar  2 16:22 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar  2 16:33 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar  2 16:33 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Mar  2 16:33 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar  2 16:22 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar  2 16:22 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Mar  2 16:22 ata-HGST_HTS545050A7E680_RBE50ADC03YZ8R-part8 -> ../../sda8
lrwxrwxrwx 1 root root  9 Mar  2 16:22 ata-SlimtypeDVD_A_DA8A6SH_3508981_456549512317 -> ../../sr0
lrwxrwxrwx 1 root root  9 Mar  2 16:33 usb-Kingston_DataTraveler_3.0_60A44C413841BFB02992011B-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar  2 16:22 usb-Kingston_DataTraveler_3.0_60A44C413841BFB02992011B-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Mar  2 16:33 wwn-0x5000cca8acc1cda4 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  2 16:22 wwn-0x5000cca8acc1cda4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar  2 16:22 wwn-0x5000cca8acc1cda4-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar  2 16:33 wwn-0x5000cca8acc1cda4-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar  2 16:33 wwn-0x5000cca8acc1cda4-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Mar  2 16:33 wwn-0x5000cca8acc1cda4-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar  2 16:22 wwn-0x5000cca8acc1cda4-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar  2 16:22 wwn-0x5000cca8acc1cda4-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Mar  2 16:22 wwn-0x5000cca8acc1cda4-part8 -> ../../sda8

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
else
  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-882731c2-14c2-421d-8011-b61d0f37b562' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
	else
	  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
	fi
	linux	/boot/vmlinuz-3.19.0-74-generic root=UUID=882731c2-14c2-421d-8011-b61d0f37b562 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.19.0-74-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-882731c2-14c2-421d-8011-b61d0f37b562' {
	menuentry 'Ubuntu, with Linux 3.19.0-74-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-74-generic-advanced-882731c2-14c2-421d-8011-b61d0f37b562' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
		else
		  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
		fi
		echo	'Loading Linux 3.19.0-74-generic ...'
		linux	/boot/vmlinuz-3.19.0-74-generic root=UUID=882731c2-14c2-421d-8011-b61d0f37b562 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-74-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-74-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-74-generic-recovery-882731c2-14c2-421d-8011-b61d0f37b562' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
		else
		  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
		fi
		echo	'Loading Linux 3.19.0-74-generic ...'
		linux	/boot/vmlinuz-3.19.0-74-generic root=UUID=882731c2-14c2-421d-8011-b61d0f37b562 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-74-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-47-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-47-generic-advanced-882731c2-14c2-421d-8011-b61d0f37b562' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
		else
		  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
		fi
		echo	'Loading Linux 3.19.0-47-generic ...'
		linux	/boot/vmlinuz-3.19.0-47-generic root=UUID=882731c2-14c2-421d-8011-b61d0f37b562 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-47-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-47-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-47-generic-recovery-882731c2-14c2-421d-8011-b61d0f37b562' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
		else
		  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
		fi
		echo	'Loading Linux 3.19.0-47-generic ...'
		linux	/boot/vmlinuz-3.19.0-47-generic root=UUID=882731c2-14c2-421d-8011-b61d0f37b562 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-47-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
	else
	  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  882731c2-14c2-421d-8011-b61d0f37b562
	else
	  search --no-floppy --fs-uuid --set=root 882731c2-14c2-421d-8011-b61d0f37b562
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 10 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-828AA72F8AA71F23' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  828AA72F8AA71F23
	else
	  search --no-floppy --fs-uuid --set=root 828AA72F8AA71F23
	fi
	drivemap -s (hd0) ${root}
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
UUID=882731c2-14c2-421d-8011-b61d0f37b562 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e4b97452-ead3-4dd6-93ae-e112effb7879 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 458.167160034 = 491.953242112  boot/grub/grub.cfg                             1
 458.169151306 = 491.955380224  boot/grub/i386-pc/core.img                     1
 456.176254272 = 489.815523328  boot/vmlinuz-3.19.0-47-generic                 1
 456.182399750 = 489.822121984  boot/vmlinuz-3.19.0-74-generic                 1
 456.182399750 = 489.822121984  vmlinuz                                        1
 326.197547913 = 350.251950080  boot/initrd.img-3.19.0-47-generic              1
 330.072738647 = 354.412904448  boot/initrd.img-3.19.0-74-generic              2
 330.072738647 = 354.412904448  initrd.img                                     2
 326.197547913 = 350.251950080  initrd.img.old                                 1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
default vesamenu.c32
prompt 0
timeout 100

menu title Custom Live CD
menu background splash.png
menu color title 1;37;44 #c0ffffff #00000000 std

label live
menu label live - boot the Live System
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label xforcevesa
menu label xforcevesa - boot Live in safe graphics mode
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/custom.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --

label install
menu label install - start the installer directly
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/custom.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --

label memtest
menu label memtest - Run memtest
kernel /install/memtest
append -

label hd
menu label hd - boot the first hard disk
localboot 0x80
append -


--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/13187/mounts) leaked on lvs invocation. Parent PID 23176: bash
File descriptor 63 (pipe:[47093]) leaked on lvs invocation. Parent PID 23176: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-03-02__16h33 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
boot-repair is executed in live-session (Ubuntu 14.04.5 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash -- BOOT_IMAGE=/casper/vmlinuz
ls: impossible d'accÃ©der Ã  /home/usr/.config: Aucun fichier ou dossier de ce type

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda3:Windows 10 (loader):Windows:chain
/dev/sda7:Ubuntu 14.04.5 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="DAA4-6936" TYPE="vfat"
/dev/sda3: LABEL="OS" UUID="828AA72F8AA71F23" TYPE="ntfs"
/dev/sda4: LABEL="RECOVERY" UUID="FA306EAC306E7015" TYPE="ntfs"
/dev/sda5: LABEL="DATA" UUID="0E1A304F1A303655" TYPE="ntfs"
/dev/sda7: UUID="882731c2-14c2-421d-8011-b61d0f37b562" TYPE="ext4"
/dev/sda8: UUID="e4b97452-ead3-4dd6-93ae-e112effb7879" TYPE="swap"
/dev/sdb1: UUID="AD5D-7634" TYPE="vfat"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


AttentionÂ : identifiant de table de partitions GPT (GUID) dÃ©tectÃ© sur Â«Â /dev/sdaÂ Â». L'utilitaire sfdisk ne prend pas GPT en charge. Utilisez GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi

=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 nov.  23 14:25 grub.d
total 76
-rwxr-xr-x 1 root root  9791 dÃ©c.  17  2015 00_header
-rwxr-xr-x 1 root root  6058 mai   13  2015 05_debian_theme
-rwxr-xr-x 1 root root 11608 juin  26  2015 10_linux
-rwxr-xr-x 1 root root 10412 juin  26  2015 20_linux_xen
-rwxr-xr-x 1 root root  1992 mars  12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 juin  26  2015 30_os-prober
-rwxr-xr-x 1 root root  1418 aoÃ»t   2  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 juin  26  2015 40_custom
-rwxr-xr-x 1 root root   216 juin  26  2015 41_custom
-rw-r--r-- 1 root root   483 juin  26  2015 README




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




=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
EFI in dmesg.
[    0.000000] ACPI: UEFI 0x000000006E83E3D8 000042 (v01                 00000000      00000000)
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.
sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda4.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sda7	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda7.

sda	: GPT,	BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
1      1049kB  274MB  273MB   fat32           EFI system partition          boot
2      274MB   290MB  16.8MB                  Microsoft reserved partition  msftres
3      290MB   200GB  199GB   ntfs            Basic data partition          msftdata
4      200GB   200GB  523MB   ntfs            Basic data partition          hidden, diag
5      200GB   350GB  150GB   ntfs            Basic data partition          msftdata
6      350GB   350GB  1049kB                                                bios_grub
7      350GB   496GB  146GB   ext4
8      496GB   500GB  4021MB  linux-swap(v1)


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  15.5GB  15.5GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA HGST HTS545050A7;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:200GB:199GB:ntfs:Basic data partition:msftdata;
4:200GB:200GB:523MB:ntfs:Basic data partition:hidden, diag;
5:200GB:350GB:150GB:ntfs:Basic data partition:msftdata;
6:350GB:350GB:1049kB:::bios_grub;
7:350GB:496GB:146GB:ext4::;
8:496GB:500GB:4021MB:linux-swap(v1)::;

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos:Kingston DataTraveler 3.0;
1:4129kB:15.5GB:15.5GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          465,8G
sda1  part vfat       260M SYSTEM
sda2  part             16M
sda3  part ntfs     185,6G OS
sda4  part ntfs       499M RECOVERY
sda5  part ntfs     139,7G DATA
sda6  part              1M
sda7  part ext4       136G
sda8  part swap       3,8G
sdb   disk           14,4G
sdb1  part vfat      14,4G
sr0   rom            1024M
loop0 loop squashfs   3,7G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0
sda3     1  0  0         /mnt/boot-sav/sda3
sda4     1  0  0         /mnt/boot-sav/sda4
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0
sda7     1  0  0         /mnt/boot-sav/sda7
sda8     1  0  0         [SWAP]
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlay (rw)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=solene)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hpet i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 input kmsg kvm log mapper mcelog media0 mem memory_bandwidth net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 36 69 a4 da 4e  4f 20 4e 41 4d 45 20 20  |..)6i..NO NAME  |
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

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 08 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 87 31 17 00 00 00 00  |..........1.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  23 1f a7 8a 2f a7 8a 82  |........#.../...|
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

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 30 3a 17  |........?....0:.|
00000020  00 00 00 00 80 00 80 00  ff 97 0f 00 00 00 00 00  |................|
00000030  55 a6 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  15 70 6e 30 ac 6e 30 fa  |.........pn0.n0.|
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

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c8 49 17  |........?.....I.|
00000020  00 00 00 00 80 00 80 00  f8 4b 77 11 00 00 00 00  |.........Kw.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  55 36 30 1a 4f 30 1a 0e  |........U60.O0..|
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

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.8G   12K  1.8G   1% /dev
tmpfs          tmpfs     370M  1.8M  368M   1% /run
/dev/sdb1      vfat       15G  3.8G   11G  26% /cdrom
/dev/loop0     squashfs  3.7G  3.7G     0 100% /rofs
/cow           overlay   1.9G  348M  1.5G  19% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1.9G  8.0K  1.9G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.9G   80K  1.9G   1% /run/shm
none           tmpfs     100M   24K  100M   1% /run/user
/dev/sda1      vfat      256M   26M  231M  10% /mnt/boot-sav/sda1
/dev/sda3      fuseblk   186G   53G  133G  29% /mnt/boot-sav/sda3
/dev/sda4      fuseblk   499M  328M  172M  66% /mnt/boot-sav/sda4
/dev/sda5      fuseblk   140G  118M  140G   1% /mnt/boot-sav/sda5
/dev/sda7      ext4      134G   11G  117G   9% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd99c2d85

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 15.5 GB, 15502147584 bytes
86 heads, 22 sectors/track, 16002 cylinders, total 30277632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065643

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    30277631    15134784    c  W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix packages sign-grub) and reinstall the grub-efi-amd64-signed of sda7, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file


=================== Blockers in case of suggested repair
La session actuelle est en mode Legacy. Veuillez redÃ©marrer l'ordinateur, et utiliser ce logiciel dans une session EFI. Cela vous permettra d'utiliser cette fonctionnalitÃ©. Par exemple, utilisez un live-USB de Boot-Repair-Disk-64bit (www.sourceforge.net/p/boot-repair-cd), aprÃ¨s avoir vÃ©rifiÃ© que votre BIOS est rÃ©glÃ© pour dÃ©marrer l'USB en mode EFI.


=================== Advice in case of suggested repair
Le dÃ©marrage de votre ordinateur est en mode Legacy. Vous voudrez peut-Ãªtre rÃ©-essayer aprÃ¨s l'avoir changÃ© en mode EFI.
Voulez-vous continuerÂ ?


=================== Final advice in case of suggested repair
N'oubliez pas de rÃ©gler votre BIOS pour qu'il amorce sur le fichier sda1/efi/.../grub*.efiÂ !

Si votre ordinateur redÃ©marre directement sur Windows, essayez de changer l'ordre de dÃ©marrage dans votre BIOS.
Si votre BIOS ne permet pas de changer l'ordre de dÃ©marrage, changez l'entrÃ©e de dÃ©marrage par dÃ©faut de l'amorceur Windows.
Par exemple, vous pouvez dÃ©marrer Windows, puis saisir la commande suivante dans une invite de commande en mode administrateurÂ :
bcdedit /set {bootmgr} path \EFI\...\grub*.efi

Le dÃ©marrage de votre ordinateur est en mode Legacy. Vous voudrez peut-Ãªtre rÃ©-essayer aprÃ¨s l'avoir changÃ© en mode EFI.


=================== User settings
The settings chosen by the user will not act on the boot.

 
```

---

### Post by oldfred on 2017-03-02
I think Boot-Repair is telling you a major part of your issue here. (I have seen English version, do not know French).
> Le dÃ©marrage de votre ordinateur est en mode Legacy. Vous voudrez peut-Ãªtre rÃ©-essayer aprÃ¨s l'avoir changÃ© en mode EFI.

You have Windows in UEFI boot mode and Ubuntu in BIOS boot mode.
How you boot install media, UEFI or BIOS, is then how it installs.
Boot-Repair if you boot Ubuntu in live mode and UEFI, can un-install the BIOS version of grub and install the UEFI version converting install to UEFI.

You should have two boot options for Ubuntu installer in UEFI.
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen[URL="https://help.ubuntu.com/community/UEFI"]
https://help.ubuntu.com/community/UEFI[/URL]

---

