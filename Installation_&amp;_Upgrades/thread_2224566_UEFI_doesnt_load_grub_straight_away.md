---
title: "UEFI doesnt load grub straight away"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by Kiesel on 2014-05-16
Hi,

after a fresh install of xubuntu 14.04 and some serious fiddling to get grub running I am now stuck in a weird situation.
I need to first start the UEFIs "Boot Menu" where you can chose from all the boot entries from where I then can start grub and from there ubuntu or win7.

When I choose, in the uefi setup, to load the grub entry directly I just get a black screen with a blinking cursor for a few seconds and then the screen switches off and after a second back on again to show the cursor for a short while etc.

Once I am in the Boot Menu it doesnt matter which entry I choose it always loads grub. :confused:

EFI-Partition: /dev/sda1
win7: /dev/sda3
Ubuntu: /dev/sda4
Home: /dev/sda5


Here is the efibootmgr -v output:
```
kiesel@molukkke:~$ sudo efibootmgr -v
BootCurrent: 0016
Timeout: 2 seconds
BootOrder: 0016,0015,001F,0000,0001,000E,000F
Boot0000  Setup	
Boot0001* Boot Menu	
Boot0002  Recovery	
Boot0003* SATA CD:	030a2400d23878bc820f604d8316c068ee79d25baea2090adfde214e8b3a5e471856a354
Boot0004* CD-ROM:	030a2400d23878bc820f604d8316c068ee79d25bbe9d0102e211f3489efa0b983c96839b
Boot0005* SATA HDD:	030a2500d23878bc820f604d8316c068ee79d25b91af625956449f41a7b91f4f892ab0f600
Boot0006* USB CD:	030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot0007* USB FDD:	030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot0008* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0009* NETWORK:	030a2400d23878bc820f604d8316c068ee79d25b78a84aaf2b2afc4ea79cf5cc8f3d3803
Boot000A* Windows Boot Manager	HD(1,800,32000,7f126d8b-f921-4c5f-87ce-99d2794b0ef9)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot000B  Setup	
Boot000C  Boot Menu	
Boot000D  Recovery	
Boot000E* SATA CD:	030a2400d23878bc820f604d8316c068ee79d25baea2090adfde214e8b3a5e471856a354
Boot000F* CD-ROM:	030a2400d23878bc820f604d8316c068ee79d25bbe9d0102e211f3489efa0b983c96839b
Boot0010* SATA HDD:	030a2500d23878bc820f604d8316c068ee79d25b91af625956449f41a7b91f4f892ab0f600
Boot0011* USB CD:	030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot0012* USB FDD:	030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot0013* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0014* NETWORK:	030a2400d23878bc820f604d8316c068ee79d25b78a84aaf2b2afc4ea79cf5cc8f3d3803
Boot0015  grub	HD(1,800,32000,7f126d8b-f921-4c5f-87ce-99d2794b0ef9)File(\EFI\BOOT\bootx64.efi)
Boot0016* rootgrub	HD(1,800,32000,7f126d8b-f921-4c5f-87ce-99d2794b0ef9)File(\grubx64.efi)
Boot0017  Setup	
Boot0018  Boot Menu	
Boot0019  Recovery	
Boot001A* SATA CD:	030a2400d23878bc820f604d8316c068ee79d25baea2090adfde214e8b3a5e471856a354
Boot001B* CD-ROM:	030a2400d23878bc820f604d8316c068ee79d25bbe9d0102e211f3489efa0b983c96839b
Boot001C* SATA HDD:	030a2500d23878bc820f604d8316c068ee79d25b91af625956449f41a7b91f4f892ab0f600
Boot001D* USB CD:	030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot001E* USB FDD:	030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot001F* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0020* NETWORK:	030a2400d23878bc820f604d8316c068ee79d25b78a84aaf2b2afc4ea79cf5cc8f3d3803

```

And here is the output of the boot-info-script
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    150854680 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /grub.cfg /efi/boot/bootx64.efi /efi/ubuntu/core.efi 
                       /efi/ubuntu/grub.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: okänd filsystemstyp ""

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /NST/nst_linux.mbr 
                       looks at sector 89796 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: okänd filsystemstyp ""
mount: okänd filsystemstyp ""

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: okänd filsystemstyp ""
mount: okänd filsystemstyp ""
mount: okänd filsystemstyp ""

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 huvuden, 63 sektorer/spår, 77825 cylindrar, totalt 1250263728 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,250,263,727 1,250,263,727  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   125,028,351   124,559,360 Data partition (Windows/Linux)
/dev/sda4     125,028,352   176,315,461    51,287,110 Data partition (Windows/Linux)
/dev/sda5     176,316,416   248,893,439    72,577,024 Data partition (Windows/Linux)
/dev/sda6     248,893,440 1,237,155,839   988,262,400 Data partition (Windows/Linux)
/dev/sda7   1,237,155,840 1,250,263,039    13,107,200 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        50B0-89C3                              vfat       
/dev/sda3        12646DDB646DC259                       ntfs       
/dev/sda4        91706520-8695-47cd-b10f-a20ec14dde85   ext4       
/dev/sda5        0077af2b-8471-41de-a5e7-e017fa0720f3   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw)


================================ sda1/grub.cfg: ================================

--------------------------------------------------------------------------------
search.fs_uuid 91706520-8695-47cd-b10f-a20ec14dde85 root hd0,gpt4 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  91706520-8695-47cd-b10f-a20ec14dde85
else
  search --no-floppy --fs-uuid --set=root 91706520-8695-47cd-b10f-a20ec14dde85
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=sv_SE
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-91706520-8695-47cd-b10f-a20ec14dde85' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  91706520-8695-47cd-b10f-a20ec14dde85
	else
	  search --no-floppy --fs-uuid --set=root 91706520-8695-47cd-b10f-a20ec14dde85
	fi
	linux	/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=91706520-8695-47cd-b10f-a20ec14dde85 ro  noplymouth
	initrd	/boot/initrd.img-3.13.0-24-generic
}
submenu 'Avancerade flaggor för Ubuntu' $menuentry_id_option 'gnulinux-advanced-91706520-8695-47cd-b10f-a20ec14dde85' {
	menuentry 'Ubuntu, med Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-91706520-8695-47cd-b10f-a20ec14dde85' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  91706520-8695-47cd-b10f-a20ec14dde85
		else
		  search --no-floppy --fs-uuid --set=root 91706520-8695-47cd-b10f-a20ec14dde85
		fi
		echo	'Läser in Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=91706520-8695-47cd-b10f-a20ec14dde85 ro  noplymouth
		echo	'Läser in initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-91706520-8695-47cd-b10f-a20ec14dde85' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  91706520-8695-47cd-b10f-a20ec14dde85
		else
		  search --no-floppy --fs-uuid --set=root 91706520-8695-47cd-b10f-a20ec14dde85
		fi
		echo	'Läser in Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=91706520-8695-47cd-b10f-a20ec14dde85 ro recovery nomodeset 
		echo	'Läser in initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (på /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-efi-50B0-89C3' {
	insmod part_gpt
	insmod fat
	set root='hd0,gpt1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  50B0-89C3
	else
	  search --no-floppy --fs-uuid --set=root 50B0-89C3
	fi
	chainloader /efi/Microsoft/Boot/bootmgfw.efi
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
menuentry "Microsoft Windows x86_64 UEFI-GPT" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root 50b0-89c3
    chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=91706520-8695-47cd-b10f-a20ec14dde85 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=50B0-89C3  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda5 during installation
UUID=0077af2b-8471-41de-a5e7-e017fa0720f3 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=608e0f24-738b-4652-abb6-7cd41c49aa1f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=50B0-89C3	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda6

00000000  13 ef 2b 79 e4 22 a5 c4  e3 d7 fe 3f 62 ae 74 c5  |..+y.".....?b.t.|
00000010  99 96 10 31 71 38 87 e1  79 04 67 ad 3e 1e 5e 3e  |...1q8..y.g.>.^>|
00000020  02 7c f2 e4 54 6a 24 41  ac 2d 8a ad 09 03 f5 29  |.|..Tj$A.-.....)|
00000030  61 94 f4 36 74 83 2b 02  43 5d fa 11 cc c2 ea ac  |a..6t.+.C]......|
00000040  4e 3e 8b f5 be 71 23 05  ca c8 dd 5b fd f8 bd 15  |N>...q#....[....|
00000050  ef 2f 83 38 5b a0 28 7e  9f 0d 31 58 44 1d cb 10  |./.8[.(~..1XD...|
00000060  2f e5 88 b7 77 7d 56 86  2d be 22 27 8a eb dd 7c  |/...w}V.-."'...||
00000070  c6 ab 0e 92 05 af aa e5  f2 2c 60 9c 1e 6a 61 19  |.........,`..ja.|
00000080  f9 ca 5e c9 20 f2 6a 54  07 21 b3 2f 15 57 df 18  |..^. .jT.!./.W..|
00000090  50 3f 27 aa dc 6d 7d e6  56 a9 82 65 94 a8 8a c4  |P?'..m}.V..e....|
000000a0  7f 7f 10 37 45 cd 5a 26  dd e4 62 bf 60 d3 ef 0d  |...7E.Z&..b.`...|
000000b0  f9 8d 2e 0e 55 f8 04 bf  89 37 3b c3 c4 b4 2a 6d  |....U....7;...*m|
000000c0  ff be 91 27 ca ef 98 b6  2f 7d c1 dd dc ec 0c 54  |...'..../}.....T|
000000d0  0b 98 25 f6 61 59 01 b4  dc 05 42 ec b8 4c 61 46  |..%.aY....B..LaF|
000000e0  17 3e 5e 73 47 5f 79 d6  3f 59 8f 15 a3 a3 fb 7d  |.>^sG_y.?Y.....}|
000000f0  b8 03 92 fc a8 9c 02 79  74 e2 79 b5 46 e2 0e 8c  |.......yt.y.F...|
00000100  ea bb 9e a1 c6 48 72 b6  41 10 f0 0d 13 68 63 76  |.....Hr.A....hcv|
00000110  34 80 12 21 4e 0c 19 a8  ae b2 c1 9d 89 46 c9 0e  |4..!N........F..|
00000120  1c 61 11 e2 12 52 b2 9f  ca 0b b6 4f 70 ce ad 0e  |.a...R.....Op...|
00000130  ea 25 5e 6d 80 38 29 b9  1d 03 76 79 c3 e6 e6 38  |.%^m.8)...vy...8|
00000140  2b 5e ec 55 ac 4b 86 e6  b9 55 69 48 23 31 3a 10  |+^.U.K...UiH#1:.|
00000150  9c 2b fc d3 97 8a 82 10  89 9d 36 fb 18 5d a2 45  |.+........6..].E|
00000160  d2 bf 71 1a cb 9e 33 7d  b3 b2 5d 4c 09 c2 59 63  |..q...3}..]L..Yc|
00000170  a9 16 67 54 86 ce 28 26  63 68 c8 85 42 31 a0 01  |..gT..(&ch..B1..|
00000180  c0 5b cd 12 e1 a3 4f 30  13 d1 60 8e 0f 26 fb 02  |.[....O0..`..&..|
00000190  29 23 c2 fb 0d 97 bb 29  a8 9a 1b b5 f7 ef 20 55  |)#.....)...... U|
000001a0  c5 5b 57 6b 0f 30 d6 43  53 d3 a1 b0 40 37 44 c1  |.[Wk.0.CS...@7D.|
000001b0  e4 af 03 c7 5e c8 98 ff  e8 e8 00 50 96 fa 3a 24  |....^......P..:$|
000001c0  a8 5b c4 15 89 f3 05 68  a1 ff 21 db b8 06 40 99  |.[.....h..!...@.|
000001d0  72 23 1e 20 3a dd cc 84  09 8d 27 ee d2 c2 07 ad  |r#. :.....'.....|
000001e0  ab 77 66 6e 60 a4 98 ec  bb 57 09 fd 7d ef 21 da  |.wfn`....W..}.!.|
000001f0  42 9f fc fb 48 2e a8 8a  10 3f de 67 4a e7 5c e1  |B...H....?.gJ.\.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-rNOxRPZl/Tmp_Log: Filen eller katalogen finns inte
cat: /tmp/BootInfo-rNOxRPZl/Tmp_Log: Filen eller katalogen finns inte


```

The laptop is a Samsung RV520.
Any help I really appreciated as this is really annoying.

---

### Post by oldfred on 2014-05-17
You have a lot of UEFI entries? Did things get duplicated somehow?
Not sure what to suggest. Does system let you boot ubuntu entry or is this one that only boots Windows entry and you have to do rename to make it work?

You also created a /grub entry in efi and UEFI?
And boot script does not show the Microsoft folder, but even os-prober found a Windows entry. Is script missing Widnows efi folder/files or did they get deleted?

In grub menu but no /efi/Microsoft folder in efi partition?
 chainloader /efi/Microsoft/Boot/bootmgfw.efi

Normal folders in efi partition are /Boot, /ubuntu & /Windows.

Some other threads where users renamed or moved files around. I would back up the entire efi partition before doing changes.

 Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

It also looks like you originally installed in BIOS boot mode using grub-pc as you have grub in protective MBR. But now have in fstab the efi partition link so grub-efi now installed.
Be sure to only boot in UEFI mode not BIOS and usually better with secure boot off.

Some other Samsungs.
 Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

You may want to house clean some entries in UEFI menu.
      
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

---

