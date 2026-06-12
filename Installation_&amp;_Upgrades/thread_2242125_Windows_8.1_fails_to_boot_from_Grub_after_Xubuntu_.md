---
title: "Windows 8.1 fails to boot from Grub after Xubuntu install"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by nigel.650 on 2014-08-30
After installing the latest Xubuntu, selecting Winows 8.1 from the Grub menu gives the following error:

"/EndEntire
file path: /ACPI(a0341d0,O)/PCI(2,1f)/Sata(1,0,0)/HD(2,1f4800,82000,d924496bf19dd641,2,2)/File(\EFI\Mircosoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image.


Press any key to continue..."

This is the first install of a linux os on this PC (Lenovo U310 touch)

---

### Post by yancek on 2014-08-30
We'll need more details on drives/partitions, boot files, etc. which can be obtained by running the bootinfoscript downloaded and run on Xubuntu.  There is a link in the Description box on that page which explains how to use it so read that page first.  After running it, there will be a file output named results.txt which you can post here and someone familiar with uefi should be able to advise you.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Did you install Xubuntu in EFI mode?

---

### Post by nigel.650 on 2014-08-31
Yes I did manage to install in EFI mode eventually. Here is the results from bootscript, thanks:

```
 Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 
    432086848 of the same hard drive for core.img, but core.img can not be 
    found at this location.


sda1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sda2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


sda3: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi


sdb3: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /bootmgr /boot/bcd


sdb4: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''


sdb5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr


sdb6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb6 starts at sector 213091079.
    Operating System:  
    Boot files:        


sdb7: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb8: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb9: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb10: _________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb11: _________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb12: _________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sdb13: _________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb14: _________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1    46,905,263    46,905,263  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           4,096    38,512,639    38,508,544 -
/dev/sda2      38,514,688    46,903,295     8,388,608 -
/dev/sda3           2,048         4,095         2,048 BIOS Boot partition


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1   976,773,167   976,773,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048     2,050,047     2,048,000 -
/dev/sdb2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sdb3       2,582,528     4,630,527     2,048,000 -
/dev/sdb4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb5       4,892,672   110,691,078   105,798,407 Data partition (Windows/Linux)
/dev/sdb6     213,091,079   422,982,588   209,891,510 Data partition (Windows/Linux)
/dev/sdb7     850,163,712   881,414,143    31,250,432 -
/dev/sdb8     881,414,144   897,900,543    16,486,400 -
/dev/sdb9     897,900,544   898,617,343       716,800 -
/dev/sdb10    898,617,344   951,046,143    52,428,800 Data partition (Windows/Linux)
/dev/sdb11    951,046,144   976,773,119    25,726,976 -
/dev/sdb12    110,692,352   150,691,839    39,999,488 Data partition (Linux)
/dev/sdb13    150,691,840   182,691,839    32,000,000 Swap partition (Linux)
/dev/sdb14    422,983,680   850,163,711   427,180,032 Data partition (Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sdb1        5A425020424FFF67                       ntfs       WINRE_DRV
/dev/sdb10       B212A84E12A8197D                       ntfs       LENOVO
/dev/sdb11       9C32A3AD32A38B3A                       ntfs       PBR_DRV
/dev/sdb12       f539aac6-3bcc-4e7e-aff4-c41504c708b0   ext4       
/dev/sdb13       470855f7-6123-482a-b293-51a509842b5b   swap       
/dev/sdb14       0543b8db-1a93-4d41-b516-8ed980250c54   ext4       
/dev/sdb2        9050-A64B                              vfat       SYSTEM_DRV
/dev/sdb3        C89D-F2B4                              vfat       LRS_ESP
/dev/sdb5        1690526D9052537B                       ntfs       Windows8_OS
/dev/sdb6        01CEFAA59569A680                       ntfs       Pauls Data
/dev/sdb7        31f38fdf-0c8e-40d8-86a0-811e64f57b9f   swap       
/dev/sdb8        8f4f0949-4cd1-4382-81b5-bc92f81a3132   swap       
/dev/sdb9        4474221C7422116A                       ntfs       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb12       /                        ext4       (rw,errors=remount-ro)
/dev/sdb14       /home                    ext4       (rw)
/dev/sdb2        /boot/efi                vfat       (rw)




========================== sdb12/boot/grub/grub.cfg: ===========================


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
set root='hd1,gpt12'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt12 --hint-efi=hd1,gpt12 --hint-baremetal=ahci1,gpt12  f539aac6-3bcc-4e7e-aff4-c41504c708b0
else
  search --no-floppy --fs-uuid --set=root f539aac6-3bcc-4e7e-aff4-c41504c708b0
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f539aac6-3bcc-4e7e-aff4-c41504c708b0' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt12'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt12 --hint-efi=hd1,gpt12 --hint-baremetal=ahci1,gpt12  f539aac6-3bcc-4e7e-aff4-c41504c708b0
	else
	  search --no-floppy --fs-uuid --set=root f539aac6-3bcc-4e7e-aff4-c41504c708b0
	fi
	linux	/boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=f539aac6-3bcc-4e7e-aff4-c41504c708b0 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-34-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f539aac6-3bcc-4e7e-aff4-c41504c708b0' {
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-advanced-f539aac6-3bcc-4e7e-aff4-c41504c708b0' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt12 --hint-efi=hd1,gpt12 --hint-baremetal=ahci1,gpt12  f539aac6-3bcc-4e7e-aff4-c41504c708b0
		else
		  search --no-floppy --fs-uuid --set=root f539aac6-3bcc-4e7e-aff4-c41504c708b0
		fi
		echo	'Loading Linux 3.13.0-34-generic ...'
		linux	/boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=f539aac6-3bcc-4e7e-aff4-c41504c708b0 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-recovery-f539aac6-3bcc-4e7e-aff4-c41504c708b0' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt12 --hint-efi=hd1,gpt12 --hint-baremetal=ahci1,gpt12  f539aac6-3bcc-4e7e-aff4-c41504c708b0
		else
		  search --no-floppy --fs-uuid --set=root f539aac6-3bcc-4e7e-aff4-c41504c708b0
		fi
		echo	'Loading Linux 3.13.0-34-generic ...'
		linux	/boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=f539aac6-3bcc-4e7e-aff4-c41504c708b0 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-34-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-f539aac6-3bcc-4e7e-aff4-c41504c708b0' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt12 --hint-efi=hd1,gpt12 --hint-baremetal=ahci1,gpt12  f539aac6-3bcc-4e7e-aff4-c41504c708b0
		else
		  search --no-floppy --fs-uuid --set=root f539aac6-3bcc-4e7e-aff4-c41504c708b0
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=f539aac6-3bcc-4e7e-aff4-c41504c708b0 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-f539aac6-3bcc-4e7e-aff4-c41504c708b0' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt12 --hint-efi=hd1,gpt12 --hint-baremetal=ahci1,gpt12  f539aac6-3bcc-4e7e-aff4-c41504c708b0
		else
		  search --no-floppy --fs-uuid --set=root f539aac6-3bcc-4e7e-aff4-c41504c708b0
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=f539aac6-3bcc-4e7e-aff4-c41504c708b0 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sdb2)' --class windows --class os $menuentry_id_option 'osprober-efi-9050-A64B' {
	insmod part_gpt
	insmod fat
	set root='hd1,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9050-A64B
	else
	  search --no-floppy --fs-uuid --set=root 9050-A64B
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


=============================== sdb12/etc/fstab: ===============================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb12 during installation
UUID=f539aac6-3bcc-4e7e-aff4-c41504c708b0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=9050-A64B  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sdb14 during installation
UUID=0543b8db-1a93-4d41-b516-8ed980250c54 /home           ext4    defaults        0       2
# swap was on /dev/sdb13 during installation
UUID=470855f7-6123-482a-b293-51a509842b5b none            swap    sw              0       0
# swap was on /dev/sdb7 during installation
UUID=31f38fdf-0c8e-40d8-86a0-811e64f57b9f none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=8f4f0949-4cd1-4382-81b5-bc92f81a3132 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sdb12: Location of files loaded by Grub: ===================


           GiB - GB             File                                 Fragment(s)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown GPT Partiton Type
5850cbb887c11947baf0379ca2d4c97e
Unknown GPT Partiton Type
dee2bfd3af3ddf11ba40e3a556d89593
Unknown GPT Partiton Type
a4bb94ded106404da1a6bfd50179d6ac
Unknown GPT Partiton Type
a4bb94ded106404da1a6bfd50179d6ac
Unknown GPT Partiton Type
a4bb94ded106404da1a6bfd50179d6ac
Unknown GPT Partiton Type
a4bb94ded106404da1a6bfd50179d6ac
Unknown GPT Partiton Type
a4bb94ded106404da1a6bfd50179d6ac
Unknown GPT Partiton Type
a4bb94ded106404da1a6bfd50179d6ac
Unknown BootLoader on sdb2


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 1f 00  |........?....H..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 4b a6 50 90 4e  4f 20 4e 41 4d 45 20 20  |..)K.P.NO NAME  |
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


Unknown BootLoader on sdb3


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 6e 10  |.X.MSDOS5.0...n.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 27 00  |........?....h'.|
00000020  00 40 1f 00 c9 07 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b4 f2 9d c8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-4QdUbSZE/Tmp_Log: No such file or directory



```

---

### Post by yancek on 2014-08-31
You have Grub installed to the mbr of both drives.  Your partitions on the first drive (sda1 and sda2) show as unknown filesystem and partition sda3 is a boot partition with only the core.img file.  Both windows and and Xubuntu are on sdb.  Generally, when using EFI boot, the bootloader is not installed to the master boot record. sdb2 has the Xubuntu efi files and sdb3 has the windows EFI files.  Usually, these are on the same VFAT partition.  This doesn't seem correct but, I don't use GPT or UEFI so can't really help.  Hopefully, someone more familiar will come along to help.

---

### Post by LostFarmer on 2014-08-31
> **yancek said:**
>  sdb2 has the Xubuntu efi files and sdb3 has the windows EFI files.  Usually, these are on the same VFAT partition.  This doesn't seem correct but, I don't use GPT or UEFI so can't really help.  Hopefully, someone more familiar will come along to help.
 On some comps that will be a problem but others it will be ok.

nigel.650-- when you first start the comp press the F12 key.  Do you get into the boot menu . If yes  - select Windows, does it boot ?

Boot into linux and in a terminal run **sudo efibootmgr -v** post output.


run below .     Note: you may need to install gdisk first.
```
sudo gdisk /dev/sdb
at gdisk prompt **i**
partition #** 2**
```
post output
next **i** partition # **3**
post output

It looks like you tried to install linux at least 3 times ( 3 swaps  partitions) and one time was a WUBI install (sdb5 boot files).

---

### Post by nigel.650 on 2014-08-31
Lostfarmer,

The boot menu gives me the following options:
1. ubuntu
2. ATA SSDI: RDM-II XM020C024G
3. ATA1 WDC WD5000LPVT-24G33TI
4. PCI LAN: EFI IPv4
5. PCI LAN: EFI IPv6

Selecting option 1 or 2 gives the same grub menu, and selecting the windows option gives the error I first posted.
Option 3 loads windows.

I did try several times to load ubuntu/xubuntu, thought I'd cleaned up the partitions, but apparently not.

efibootmgr -v reports:
```
Timeout: 0 secondsBootOrder: 000C,0009,0008,000A,0004,0003,0007,000B,0006,0005,000F
Boot0000  Setup	
Boot0001  Boot Menu	
Boot0002  Diagnostic Splash	
Boot0003* ATA HDD: WDC WD5000LPVT-24G33T1                  	ACPI(a0341d0,0)PCI(1f,2)03120a00010000000000..bYVD.A...O.*..
Boot0004* ATA SSD1: RDM-II XM020C024G                       	ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000..bYVD.A...O.*..
Boot0005* RAID DEVICE2:	030a2500d23878bc820f604d8316c068ee79d25ba5388f9ca46ace40bf2f0ade9bc05d6d01
Boot0006* RAID DEVICE1:	030a2500d23878bc820f604d8316c068ee79d25ba5388f9ca46ace40bf2f0ade9bc05d6d00
Boot0007* ATAPI CD:	030a2400d23878bc820f604d8316c068ee79d25baea2090adfde214e8b3a5e471856a354
Boot0008* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0009* USB FDD:	030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot000A* USB CD:	030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot000B* PCI LAN: EFI Network (IPv4)	ACPI(a0341d0,0)PCI(1c,1)PCI(0,0)MAC(089e01b1089e,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0x.J.+*.N.....=8.
Boot000C* ubuntu	HD(2,1f4800,82000,6b4924d9-9df1-41d6-a279-cb32c0ad2e53)File(\EFI\ubuntu\shimx64.efi)
Boot000D* Lenovo Recovery System	ACPI(a0341d0,0)PCI(1f,2)03120a00010000000000HD(3,276800,1f4000,af030b02-ace1-4837-9411-f5afa3c61557)File(\EFI\Microsoft\Boot\lrsBootMgr.efi)
Boot000E* Windows Boot Manager	HD(2,1f4800,82000,6b4924d9-9df1-41d6-a279-cb32c0ad2e53)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot000F* PCI LAN: EFI Network (IPv6)	ACPI(a0341d0,0)PCI(1c,1)PCI(0,0)MAC(089e01b1089e,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000x.J.+*.N.....=8.

```
gdisk partion #2 reports:
```
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9B832855-3707-4AA6-9102-D57F40C0F4C8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 30403632 sectors (14.5 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2050047   1000.0 MiB  FFFF  Ba
   2         2050048         2582527   260.0 MiB   EF00  EF
   3         2582528         4630527   1000.0 MiB  FFFF  Ba
   4         4630528         4892671   128.0 MiB   0C01  Mi
   5         4892672       110691078   50.4 GiB    0700  
   6       213091079       422982588   100.1 GiB   0700  
   7       850163712       881414143   14.9 GiB    FFFF  
   8       881414144       897900543   7.9 GiB     FFFF  
   9       897900544       898617343   350.0 MiB   FFFF  
  10       898617344       951046143   25.0 GiB    0700  Ba
  11       951046144       976773119   12.3 GiB    FFFF  Ba
  12       110692352       150691839   19.1 GiB    8300  
  13       150691840       182691839   15.3 GiB    8200  
  14       422983680       850163711   203.7 GiB   8300 
```
gdisk partition # 3 reports:
```
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9B832855-3707-4AA6-9102-D57F40C0F4C8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 30403632 sectors (14.5 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2050047   1000.0 MiB  FFFF  Ba
   2         2050048         2582527   260.0 MiB   EF00  EF
   3         2582528         4630527   1000.0 MiB  FFFF  Ba
   4         4630528         4892671   128.0 MiB   0C01  Mi
   5         4892672       110691078   50.4 GiB    0700  
   6       213091079       422982588   100.1 GiB   0700  
   7       850163712       881414143   14.9 GiB    FFFF  
   8       881414144       897900543   7.9 GiB     FFFF  
   9       897900544       898617343   350.0 MiB   FFFF  
  10       898617344       951046143   25.0 GiB    0700  Ba
  11       951046144       976773119   12.3 GiB    FFFF  Ba
  12       110692352       150691839   19.1 GiB    8300  
  13       150691840       182691839   15.3 GiB    8200  
  14       422983680       850163711   203.7 GiB   8300 
```

---

### Post by LostFarmer on 2014-08-31
The output of your 'gdisk' is different then mine and does not have the 'Partition unique GUID' number that I was looking for.  Will post my data and it might help you see.

```
dad@dad-X401A1 ~ $ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): i
Partition number (1-12): 1
Partition GUID code: C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI System)
Partition unique GUID: **A3F6A149-563B-46BB-93F4-32EA12C020B8**
First sector: 2048 (at 1024.0 KiB)
Last sector: 616447 (at 301.0 MiB)
Partition size: 614400 sectors (300.0 MiB)
Attribute flags: 0000000000000000
Partition name: 'EFI system partition'
```

part of efibootmgr:

```
Boot0000* Windows Boot Manager    HD(1,800,96000,**a3f6a149-563b-46bb-93f4-32ea12c020b8**)File(\EFI\Microsoft\Boot\bootmgfw.efi) (shorted)
Boot000A* ubuntu    HD(1,800,96000,**a3f6a149-563b-46bb-93f4-32ea12c020b8**)File(EFI\Ubuntu\grubx64.efi)

```
I wanted to check the efibootmgr output path to gdisk unique GUID, 

Your grub.cfg does have the normally correct WIN7/8 chainload path but on sdb2 nor sdb3 has the folder or file  /EFI/Microsoft/Boot/bootmgfw.efi. The chainloader path would be sdb2, the partiton linux has mounted at /boot/efi .
Due to the fact you can boot into Win8 , it must be via sda.  Look to see if any of sda partitions has a bootmgfw.efi file.  Is sda the   ATA HDD: WDC WD5000LPVT-24G33T1    hdd ?

What is on sda ?  Linux seems not to be able to mount the partitions.
Do you or did you have a RAID setup?

---

### Post by LostFarmer on 2014-08-31
You may want to look at having WIN menu boot linux instead of having linux menu boot WIN.  [http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub](http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub)  solution #2 .  Would then use efibootmgr to place the working WIN as the first boot entire if your bios setup does not have the option to change boot order.

---

### Post by nigel.650 on 2014-08-31
gdisk didn't look correct because I mis-understood your original request, here is what you were looking for:

```
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.


Command (? for help): i
Partition number (1-14): 2
Partition GUID code: C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI System)
Partition unique GUID: 6B4924D9-9DF1-41D6-A279-CB32C0AD2E53
First sector: 2050048 (at 1001.0 MiB)
Last sector: 2582527 (at 1.2 GiB)
Partition size: 532480 sectors (260.0 MiB)
Attribute flags: 0000000000000001
Partition name: 'EF'


Command (? for help): i
Partition number (1-14): 3
Partition GUID code: DE94BBA4-06D1-4D40-A1A6-BFD50179D6AC (Unknown)
Partition unique GUID: AF030B02-ACE1-4837-9411-F5AFA3C61557
First sector: 2582528 (at 1.2 GiB)
Last sector: 4630527 (at 2.2 GiB)
Partition size: 2048000 sectors (1000.0 MiB)
Attribute flags: 0000000000000001
Partition name: 'Ba'



```

---

### Post by nigel.650 on 2014-08-31
sda is used by lenovo, for what I don't know, and is a 24G SSD.
sdb is the 500G HDD
Question: How do I look at a partions contents if it has no label?

---

### Post by LostFarmer on 2014-08-31
One of the problems is no \EFI\Microsoft\Boot\bootmgfw.efi  in the EFI partition.  What I have read it can be rebuilt.  The basic steps would be make a minimal repair usb  [http://www.bleepingcomputer.com/tutorials/create-usb-recovery-drive-in-windows-8/](http://www.bleepingcomputer.com/tutorials/create-usb-recovery-drive-in-windows-8/)   , boot with it and get to the Command Prompt and do the steps at [http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader) with a few changes for your setup.  If you want to try , read the 2 sites and ask questions, I have not rebuilt the bcdboot store but it looks straight forward to do so.  I will not say  it will work or make something worse, I have never tried it.

Some one else may read all that has been written and have a better idea.

---

### Post by nigel.650 on 2014-09-01
yancek, LostFarmer thanks for your help. Lots of good information for me to digest, at present it seems that xubuntu is booting from the the solid state drive and windows from the hard drive (found by altering the device boot order). I will post back when I have some results from the above links.

---

