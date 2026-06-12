---
title: "ubuntu 12.10 with win7 - A disk read error occurred"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by KhuanHoliong on 2013-01-19
Installed Ubuntu 12.10 on an x64 machine already have a win 7. Now I can login my ubuntu successfully. But when I select Win7 from menu, it occurs that "a disk read error occurred, press ctrl alt del to restart".
I have tried to sudo update-grub, and it could find win7 and said "done" like this:
> 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-22-generic
Found initrd image: /boot/initrd.img-3.5.0-22-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

however "a disk read error occurred..." appeared again when I reboot my computer.

I have downloaded the [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and this is the output
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    600535672 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 72 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   204,802,047   204,595,200   7 NTFS / exFAT / HPFS
/dev/sda3         204,804,094   625,141,759   420,337,666   f W95 Extended (LBA)
/dev/sda5         204,804,096   409,604,095   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda6         409,606,144   512,006,143   102,400,000   7 NTFS / exFAT / HPFS
/dev/sda7         512,008,192   619,427,839   107,419,648  83 Linux
/dev/sda8         619,429,888   625,141,759     5,711,872  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        60282CB5282C8C5A                       ntfs       &#31995;&#32479;&#20445;&#30041;
/dev/sda2        62045A51045A27F5                       ntfs       
/dev/sda5        946E15296E150620                       ntfs       &#24212;&#29992;
/dev/sda6        78AA2CD7AA2C93A2                       ntfs       &#23398;&#20064;
/dev/sda7        8fcda201-7fb1-465e-8a81-915abdf9c201   ext4       
/dev/sda8        d7d675c2-81d7-4c76-b299-fd010fc43a5d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


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
insmod part_msdos
insmod ext2
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
else
  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=zh_CN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8fcda201-7fb1-465e-8a81-915abdf9c201' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
	else
	  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
	fi
	linux	/boot/vmlinuz-3.5.0-22-generic root=UUID=8fcda201-7fb1-465e-8a81-915abdf9c201 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8fcda201-7fb1-465e-8a81-915abdf9c201' {
	menuentry 'Ubuntu&#65292;Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-8fcda201-7fb1-465e-8a81-915abdf9c201' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
		else
		  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
		fi
		echo	'&#36733;&#20837; Linux 3.5.0-22-generic ...'
		linux	/boot/vmlinuz-3.5.0-22-generic root=UUID=8fcda201-7fb1-465e-8a81-915abdf9c201 ro   quiet splash $vt_handoff
		echo	'&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
		initrd	/boot/initrd.img-3.5.0-22-generic
	}
	menuentry 'Ubuntu&#65292;Linux 3.5.0-22-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-8fcda201-7fb1-465e-8a81-915abdf9c201' {
	recordfail
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
		else
		  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
		fi
		echo	'&#36733;&#20837; Linux 3.5.0-22-generic ...'
		linux	/boot/vmlinuz-3.5.0-22-generic root=UUID=8fcda201-7fb1-465e-8a81-915abdf9c201 ro recovery nomodeset 
		echo	'&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
		initrd	/boot/initrd.img-3.5.0-22-generic
	}
	menuentry 'Ubuntu&#65292;Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-8fcda201-7fb1-465e-8a81-915abdf9c201' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
		else
		  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
		fi
		echo	'&#36733;&#20837; Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=8fcda201-7fb1-465e-8a81-915abdf9c201 ro   quiet splash $vt_handoff
		echo	'&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu&#65292;Linux 3.5.0-17-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-8fcda201-7fb1-465e-8a81-915abdf9c201' {
	recordfail
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
		else
		  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
		fi
		echo	'&#36733;&#20837; Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=8fcda201-7fb1-465e-8a81-915abdf9c201 ro recovery nomodeset 
		echo	'&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
	else
	  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
	fi
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  8fcda201-7fb1-465e-8a81-915abdf9c201
	else
	  search --no-floppy --fs-uuid --set=root 8fcda201-7fb1-465e-8a81-915abdf9c201
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-60282CB5282C8C5A' {
	insmod ldm
	insmod ntfs
	set root='ldm/1f4ed62d-904c-11e1-b28a-ec55f9dc6523/Volume1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0 --hint-efi=hd0 --hint-baremetal=ahci0 --hint='ldm/1f4ed62d-904c-11e1-b28a-ec55f9dc6523/Volume1'  60282CB5282C8C5A
	else
	  search --no-floppy --fs-uuid --set=root 60282CB5282C8C5A
	fi
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
UUID=8fcda201-7fb1-465e-8a81-915abdf9c201 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d7d675c2-81d7-4c76-b299-fd010fc43a5d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-17-generic               3
               =                boot/initrd.img-3.5.0-22-generic               1
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                boot/vmlinuz-3.5.0-22-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  28 8b 4d 08 83 c1 f0 e8  54 f6 f2 ff 8b c6 e8 1a  |(.M.....T.......|
00000010  13 02 00 c2 1c 00 68 fc  00 00 00 b8 8f 8d 52 00  |......h.......R.|
00000020  e8 99 12 02 00 8b d9 33  f6 39 b3 80 00 00 00 74  |.......3.9.....t|
00000030  0a e8 09 ad f3 ff e9 c2  02 00 00 53 8d 4d 9c e8  |...........S.M..|
00000040  23 6e f3 ff 53 8d 45 9c  50 8d 8d f8 fe ff ff 89  |#n..S.E.P.......|
00000050  75 fc e8 77 df f4 ff c6  45 fc 01 8d 85 08 ff ff  |u..w....E.......|
00000060  ff 39 b5 00 ff ff ff 75  06 8b 85 fc fe ff ff 89  |.9.....u........|
00000070  45 98 8d 85 44 ff ff ff  50 ff 73 20 ff 15 08 e8  |E...D...P.s ....|
00000080  52 00 8d 85 34 ff ff ff  50 8b cb e8 f6 fa ff ff  |R...4...P.......|
00000090  8b 85 34 ff ff ff 8b 8d  44 ff ff ff ff b3 c8 00  |..4.....D.......|
000000a0  00 00 8d b5 44 ff ff ff  ff b3 c4 00 00 00 8d 7d  |....D..........}|
000000b0  80 a5 a5 a5 03 c8 8b 85  38 ff ff ff a5 01 45 84  |........8.....E.|
000000c0  8b 85 3c ff ff ff 29 45  88 8b 85 40 ff ff ff 29  |..<...)E...@...)|
000000d0  45 8c 89 4d 80 8d 4d 80  e8 1b 47 f5 ff 8b 83 b0  |E..M..M...G.....|
000000e0  00 00 00 8b 35 a4 e6 52  00 83 f8 ff 75 04 6a 17  |....5..R....u.j.|
000000f0  ff d6 89 45 94 8b 83 ac  00 00 00 83 f8 ff 75 04  |...E..........u.|
00000100  6a 17 ff d6 8d 4d 94 51  8d 4d 90 51 83 ec 10 8b  |j....M.Q.M.Q....|
00000110  fc ff 75 98 8d b5 44 ff  ff ff a5 a5 a5 89 45 90  |..u...D.......E.|
00000120  8b 03 8b cb a5 ff 90 50  01 00 00 ff 75 94 8d 8d  |.......P....u...|
00000130  68 ff ff ff 6a 01 6a 00  e8 67 71 f3 ff 8b 4d 98  |h...j.j..gq...M.|
00000140  8d 85 68 ff ff ff 50 c6  45 fc 02 e8 94 6f f3 ff  |..h...P.E....o..|
00000150  ff 75 94 8d b5 44 ff ff  ff 83 ec 10 8b fc ff 75  |.u...D.........u|
00000160  98 a5 a5 a5 89 85 64 ff  ff ff 8b 03 8b cb a5 ff  |......d.........|
00000170  90 54 01 00 00 33 d2 33  c0 52 8d 8b bc 00 00 00  |.T...3.3.R......|
00000180  50 e8 53 46 f5 ff 85 c0  74 62 83 bb 84 00 00 00  |P.SF....tb......|
00000190  00 74 59 8b 83 bc 00 00  00 03 45 80 8d 75 80 8d  |.tY.......E..u..|
000001a0  bd 70 ff ff ff a5 a5 a5  a5 89 85 78 ff ff ff 8b  |.p.........x....|
000001b0  83 c0 00 00 00 03 85 74  ff ff ff 83 ec 10 00 fe  |.......t........|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 00 35 0c 00 fe  |............5...|
000001d0  ff ff 05 fe ff ff 02 00  35 0c 00 88 1a 06 00 00  |........5.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

What should I do next? Is there any method that needn't reinstall win7?

Thanks!

---

### Post by Mark Phelps on 2013-01-19
HOW did you shrink the Win7 OS partition to make room for Ubuntu? If you used GParted or used the Slider with the Ubuntu installer, you likely corrupted the Win7 OS -- as that's a common side effect of using Linux utilities to tamper with Win7 filesystems.

---

### Post by KhuanHoliong on 2013-01-19
> **Mark Phelps said:**
> HOW did you shrink the Win7 OS partition to make room for Ubuntu? If you used GParted or used the Slider with the Ubuntu installer, you likely corrupted the Win7 OS -- as that's a common side effect of using Linux utilities to tamper with Win7 filesystems.
The whole disk was NTFS filesystem earlier like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230304&stc=1&d=1358605188[/IMG]
The 55GB Ext4 and 2.9GB Swap used to be **one** NTFS partition in Win7. In order to make room for ubuntu, I deleted this partition in Win7 using the disk tool provided by Win7. Then I installed ubuntu...
I'm sorry, but English is not my mother tongue, and I don't know if I have explained clearly.

---

### Post by oldfred on 2013-01-19
Did you convert to dynamic partitions at some point and convert back to basic partitions in Windows? Or is the main Windows partition still dynamic?
Post this if SFS then you have a dynamic partition:
sudo fdisk -lu

You have this shown:
> insmod ldm        GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)


Several work arounds in bug report.

---

### Post by KhuanHoliong on 2013-01-19
> **oldfred said:**
> Did you convert to dynamic partitions at some point and convert back to basic partitions in Windows? Or is the main Windows partition still dynamic?
Post this if SFS then you have a dynamic partition:
sudo fdisk -lu

You have this shown:
        GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)


Several work arounds in bug report.

Sorry I don't know what you mean. Here is the result of sudo fdisk -lu
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3941ca79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   204802047   102297600    7  HPFS/NTFS/exFAT
/dev/sda3       204804094   625141759   210168833    f  W95 Ext'd (LBA)
/dev/sda5       204804096   409604095   102400000    7  HPFS/NTFS/exFAT
/dev/sda6       409606144   512006143    51200000    7  HPFS/NTFS/exFAT
/dev/sda7       512008192   619427839    53709824   83  Linux
/dev/sda8       619429888   625141759     2855936   82  Linux swap / Solaris

My disk is not a dynamic disk..

---

### Post by oldfred on 2013-01-20
Was drive ever dynamic?
There seem to be some meta-data left on the drive that the new grub2 finds and then cannot boot Windows correctly. Work around is just to create your own boot stanza in 40_custom.

---

