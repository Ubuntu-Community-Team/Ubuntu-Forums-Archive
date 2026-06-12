---
title: "GRUB can't see Windows 7 - Boot Info Script Included"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by raucous1 on 2011-05-14
I installed Windows 7, then Ubuntu 11.04, but GRUB can't seem to see my Windows partition.

I ran 'update-grub' but it didn't seem to find Windows.

Other forums seem to suggest editing */boot/grub/menu.lst* but I can't even find that file.

Here is the info I get from the 'boot_info_script'

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdg1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdg1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    73,433,087    73,226,240   7 HPFS/NTFS
/dev/sda3         141,795,326 1,953,523,711 1,811,728,386   5 Extended
/dev/sda5       1,936,750,592 1,953,523,711    16,773,120  82 Linux swap / Solaris
/dev/sda6         141,795,328 1,936,750,591 1,794,955,264  83 Linux
/dev/sda4          73,433,088   141,793,279    68,360,192  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 16.0 GB, 16028794368 bytes
64 heads, 32 sectors/track, 15286 cylinders, total 31306239 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32    31,305,727    31,305,696   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0E38099238097A4B                       ntfs       System Reserved               
/dev/sda2        6C22126122123096                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        c505dded-9648-4529-8260-eb6074ae4615   ext4                                     
/dev/sda5        2b54a8dc-8635-4ea4-ad3a-5622e0a2ae31   swap                                     
/dev/sda6        5b4aa0d3-4b16-4455-82d6-79dce8054271   ext4                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdg1        2009-6B13                              vfat                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,71,115; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c505dded-9648-4529-8260-eb6074ae4615 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c505dded-9648-4529-8260-eb6074ae4615 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=c505dded-9648-4529-8260-eb6074ae4615 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=5b4aa0d3-4b16-4455-82d6-79dce8054271 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=2b54a8dc-8635-4ea4-ad3a-5622e0a2ae31 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


  39.9GB: boot/grub/core.img
  40.1GB: boot/grub/grub.cfg
  40.6GB: boot/initrd.img-2.6.38-8-generic
  37.9GB: boot/vmlinuz-2.6.38-8-generic
  40.6GB: initrd.img
  37.9GB: vmlinuz

=========================== sdg1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Start Kubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/kubuntu.seed FRONTEND_BACKGROUND=original boot=casper maybe-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Kubuntu in text mode" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/kubuntu.seed FRONTEND_BACKGROUND=original quiet --
	initrd	/install/initrd.gz
}
menuentry "Install in expert mode" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/kubuntu.seed FRONTEND_BACKGROUND=original priority=low --
	initrd	/install/initrd.gz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Rescue a broken system" {
	set gfxpayload=keep
	linux	/install/vmlinuz  rescue/enable=true --
	initrd	/install/initrd.gz
}

=================== sdg1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  6b d9 6f 91 06 7f 37 6a  d3 11 7b a6 70 08 18 dc  |k.o...7j..{.p...|
00000010  0a 88 48 fc 19 14 2b 6e  b7 5c c5 e5 eb 46 7e ee  |..H...+n.\...F~.|
00000020  b4 2c df e1 41 c2 bd 1f  49 96 bf 60 d0 f7 a5 59  |.,..A...I..`...Y|
00000030  dc cc 90 9e 8f dd 23 0a  59 5d 5d 1a 7f 9e 52 04  |......#.Y]]...R.|
00000040  69 84 5f bc 9e e6 c3 53  c7 f5 c1 c3 12 5a 22 0b  |i._....S.....Z".|
00000050  e6 04 db bc 59 bc c1 3e  a8 c5 e4 57 41 aa 2e c2  |....Y..>...WA...|
00000060  72 23 3e cf 53 41 cb c2  c3 e5 72 d5 a4 34 4d 08  |r#>.SA....r..4M.|
00000070  f0 72 35 ca ac 8a 4c 56  37 d2 4a db 58 4c ff 20  |.r5...LV7.J.XL. |
00000080  ad f3 75 dd f7 9b 74 e4  4b 79 8d 52 1f 54 85 cd  |..u...t.Ky.R.T..|
00000090  26 82 05 5c 08 a8 df f1  a6 4f f1 a7 7e 2c 3e d1  |&..\.....O..~,>.|
000000a0  9f a7 91 84 b5 28 04 f4  33 23 03 a9 8a 5a 03 79  |.....(..3#...Z.y|
000000b0  5c bb d1 e0 90 5a 92 ad  3a dd 19 18 24 90 60 e5  |\....Z..:...$.`.|
000000c0  a3 92 eb ea fa 34 fd fd  8c 98 a1 fb 5b 43 82 b5  |.....4......[C..|
000000d0  f2 74 f3 ba 57 07 f1 9b  6f a6 a2 07 86 c9 08 4b  |.t..W...o......K|
000000e0  dd 06 f8 ac ee 29 1f 99  a2 d3 23 84 88 97 29 67  |.....)....#...)g|
000000f0  c2 8b 69 21 13 71 03 33  3a ba 36 54 44 cd 0f e5  |..i!.q.3:.6TD...|
00000100  95 0c f5 e1 2c 6a e8 88  4f 83 00 67 c4 c6 e3 d2  |....,j..O..g....|
00000110  ca 1a c0 9b ad 6a 37 ab  32 23 d8 68 a9 5f 97 b4  |.....j7.2#.h._..|
00000120  2c 79 74 d5 79 aa c6 26  cc 3f df bf 32 94 36 37  |,yt.y..&.?..2.67|
00000130  d3 7e d5 ad 8b e5 1c 5d  e0 41 23 3b 56 22 7d a2  |.~.....].A#;V"}.|
00000140  9d 6d 12 6a 1b 66 2e 32  67 44 45 17 f7 f6 8d 70  |.m.j.f.2gDE....p|
00000150  87 eb d9 2b 02 4f 29 99  ac 9a a7 e1 bf c1 38 cb  |...+.O).......8.|
00000160  c7 ea 47 74 ba 47 3a 48  39 ab f7 4c 75 74 af a7  |..Gt.G:H9..Lut..|
00000170  21 23 e3 39 c9 77 c1 f2  16 d8 b2 7b 4e 60 d9 1b  |!#.9.w.....{N`..|
00000180  03 a3 24 86 e4 bc 1a db  b8 d9 bf a6 81 96 6c fb  |..$...........l.|
00000190  1f ab ba 37 65 bb 15 7f  e6 c8 d2 6a d4 df 09 4d  |...7e......j...M|
000001a0  fb a7 fa e6 c2 85 f5 29  cb 88 aa 19 4d 16 60 dd  |.......)....M.`.|
000001b0  a7 e9 ec 9c 45 64 d3 96  89 0d 03 c3 03 57 00 fe  |....Ed.......W..|
000001c0  ff ff 82 fe ff ff 02 d8  fc 6a 00 f0 ff 00 00 fe  |.........j......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 d8 fc 6a 00 00  |.............j..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdg1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  e0 af dd 01 b0 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 13 6b 09 20 20  20 20 20 20 20 20 20 20  |..).k.          |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 b0 5b 74 00  66 ba 00 00 00 00 bb 00  |}.f..[t.f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sdg1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

Any thoughts?

---

### Post by Rubi1200 on 2011-05-14
Hi,

>  Other forums seem to suggest editing */boot/grub/menu.lst* but I can't even find that file.This won't help you. Those instructions are for the older version of GRUB that was used on Ubuntu prior to version 9.10. 

Ubuntu now uses GRUB2:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Let's try reinstalling GRUB from the LiveCD as a first step in troubleshooting this:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda4 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```Back in Ubuntu, run ```
sudo update-grub
``` and see what happens.

---

### Post by Dutch70 on 2011-05-14
Edit: Nevermind, I was posting at the same time as Rubi. 


1. Did you run "update-grub" as root? as in...
```
sudo update-grub
```

2. menu.lst is not a part of grub2, that's for grub legacy.

3. The boot script you ran (0.55) is for Grub2, but it's for version 1.98. 11.04 uses version 1.99. So, you would need to do the following to get the correct boot info script.

From the live cd, run the following command in a terminal.*(copy&paste)*
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```

That should put the boot info script in your downloads folder. Cut & Paste it to your desktop, and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by raucous1 on 2011-05-14
Sorry for the delay, my liveCD was corrupted, and I had to make another. And thanks for the help.

Here is what happens when I run the latest b_script on a live system:

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdg.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/pdc_bechaeiegi and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda6 already mounted or sda6 busy

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda4 already mounted or sda4 busy

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......GZ.V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:  Syslinux looks at sector 1453280 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdg1 starts at sector 
                       0. But according to the info from fdisk, sdg1 starts 
                       at sector 32.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

pdc_bechaeiegi1: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

pdc_bechaeiegi2: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

pdc_bechaeiegi3: _______________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_bechaeiegi5: _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda4 already mounted or sda4 busy
mount: unknown filesystem type ''

pdc_bechaeiegi6: _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda4 already mounted or sda4 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

pdc_bechaeiegi4: _______________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    73,433,087    73,226,240   7 NTFS / exFAT / HPFS
/dev/sda3         141,795,326 1,953,523,711 1,811,728,386   5 Extended
/dev/sda5       1,936,750,592 1,953,523,711    16,773,120  82 Linux swap / Solaris
/dev/sda6         141,795,328 1,936,750,591 1,794,955,264  83 Linux
/dev/sda4          73,433,088   141,793,279    68,360,192  83 Linux


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 16.0 GB, 16028794368 bytes
64 heads, 32 sectors/track, 15286 cylinders, total 31306239 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             32    31,305,727    31,305,696   c W95 FAT32 (LBA)


Drive: pdc_bechaeiegi _____________________________________________________________________

Disk /dev/mapper/pdc_bechaeiegi: 1000.1 GB, 1000137752576 bytes
255 heads, 63 sectors/track, 121593 cylinders, total 1953394048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_bechaeiegi1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bechaeiegi2            206,848    73,433,087    73,226,240   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bechaeiegi3        141,795,326 1,953,523,711 1,811,728,386   5 Extended
/dev/mapper/pdc_bechaeiegi5      1,936,750,592 1,953,523,711    16,773,120  82 Linux swap / Solaris
/dev/mapper/pdc_bechaeiegi6        141,795,328 1,936,750,591 1,794,955,264  83 Linux
/dev/mapper/pdc_bechaeiegi4         73,433,088   141,793,279    68,360,192  83 Linux

/dev/mapper/pdc_bechaeiegi3 ends after the last sector of /dev/mapper/pdc_bechaeiegi
/dev/mapper/pdc_bechaeiegi5 ends after the last sector of /dev/mapper/pdc_bechaeiegi

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       7e0721b4-2ef2-400c-8a4a-268976e4cb07   ext3       
/dev/sda1        0E38099238097A4B                       ntfs       System Reserved
/dev/sda2        6C22126122123096                       ntfs       
/dev/sda4        c505dded-9648-4529-8260-eb6074ae4615   ext4       
/dev/sda5        2b54a8dc-8635-4ea4-ad3a-5622e0a2ae31   swap       
/dev/sda6        5b4aa0d3-4b16-4455-82d6-79dce8054271   ext4       
/dev/sdg1        0748-1A3E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdg1/boot/grub/grub.cfg: ===========================

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

menuentry "Start Kubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdg1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdg1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdg1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdg1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

===================== pdc_bechaeiegi4/boot/grub/grub.cfg: ======================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,71,115; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c505dded-9648-4529-8260-eb6074ae4615 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c505dded-9648-4529-8260-eb6074ae4615 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root c505dded-9648-4529-8260-eb6074ae4615
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

========================== pdc_bechaeiegi4/etc/fstab: ==========================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=c505dded-9648-4529-8260-eb6074ae4615 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=5b4aa0d3-4b16-4455-82d6-79dce8054271 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=2b54a8dc-8635-4ea4-ad3a-5622e0a2ae31 none            swap    sw              0       0
--------------------------------------------------------------------------------

============== pdc_bechaeiegi4: Location of files loaded by Grub: ==============

           GiB - GB             File                                 Fragment(s)

  37.185237885 = 39.927345152   boot/grub/core.img                             1
  37.376949310 = 40.133193728   boot/grub/grub.cfg                             1
  37.893074036 = 40.687378432   boot/initrd.img-2.6.38-8-generic               2
  35.312808990 = 37.916839936   boot/vmlinuz-2.6.38-8-generic                  1
  37.893074036 = 40.687378432   initrd.img                                     2
  35.312808990 = 37.916839936   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  6b d9 6f 91 06 7f 37 6a  d3 11 7b a6 70 08 18 dc  |k.o...7j..{.p...|
00000010  0a 88 48 fc 19 14 2b 6e  b7 5c c5 e5 eb 46 7e ee  |..H...+n.\...F~.|
00000020  b4 2c df e1 41 c2 bd 1f  49 96 bf 60 d0 f7 a5 59  |.,..A...I..`...Y|
00000030  dc cc 90 9e 8f dd 23 0a  59 5d 5d 1a 7f 9e 52 04  |......#.Y]]...R.|
00000040  69 84 5f bc 9e e6 c3 53  c7 f5 c1 c3 12 5a 22 0b  |i._....S.....Z".|
00000050  e6 04 db bc 59 bc c1 3e  a8 c5 e4 57 41 aa 2e c2  |....Y..>...WA...|
00000060  72 23 3e cf 53 41 cb c2  c3 e5 72 d5 a4 34 4d 08  |r#>.SA....r..4M.|
00000070  f0 72 35 ca ac 8a 4c 56  37 d2 4a db 58 4c ff 20  |.r5...LV7.J.XL. |
00000080  ad f3 75 dd f7 9b 74 e4  4b 79 8d 52 1f 54 85 cd  |..u...t.Ky.R.T..|
00000090  26 82 05 5c 08 a8 df f1  a6 4f f1 a7 7e 2c 3e d1  |&..\.....O..~,>.|
000000a0  9f a7 91 84 b5 28 04 f4  33 23 03 a9 8a 5a 03 79  |.....(..3#...Z.y|
000000b0  5c bb d1 e0 90 5a 92 ad  3a dd 19 18 24 90 60 e5  |\....Z..:...$.`.|
000000c0  a3 92 eb ea fa 34 fd fd  8c 98 a1 fb 5b 43 82 b5  |.....4......[C..|
000000d0  f2 74 f3 ba 57 07 f1 9b  6f a6 a2 07 86 c9 08 4b  |.t..W...o......K|
000000e0  dd 06 f8 ac ee 29 1f 99  a2 d3 23 84 88 97 29 67  |.....)....#...)g|
000000f0  c2 8b 69 21 13 71 03 33  3a ba 36 54 44 cd 0f e5  |..i!.q.3:.6TD...|
00000100  95 0c f5 e1 2c 6a e8 88  4f 83 00 67 c4 c6 e3 d2  |....,j..O..g....|
00000110  ca 1a c0 9b ad 6a 37 ab  32 23 d8 68 a9 5f 97 b4  |.....j7.2#.h._..|
00000120  2c 79 74 d5 79 aa c6 26  cc 3f df bf 32 94 36 37  |,yt.y..&.?..2.67|
00000130  d3 7e d5 ad 8b e5 1c 5d  e0 41 23 3b 56 22 7d a2  |.~.....].A#;V"}.|
00000140  9d 6d 12 6a 1b 66 2e 32  67 44 45 17 f7 f6 8d 70  |.m.j.f.2gDE....p|
00000150  87 eb d9 2b 02 4f 29 99  ac 9a a7 e1 bf c1 38 cb  |...+.O).......8.|
00000160  c7 ea 47 74 ba 47 3a 48  39 ab f7 4c 75 74 af a7  |..Gt.G:H9..Lut..|
00000170  21 23 e3 39 c9 77 c1 f2  16 d8 b2 7b 4e 60 d9 1b  |!#.9.w.....{N`..|
00000180  03 a3 24 86 e4 bc 1a db  b8 d9 bf a6 81 96 6c fb  |..$...........l.|
00000190  1f ab ba 37 65 bb 15 7f  e6 c8 d2 6a d4 df 09 4d  |...7e......j...M|
000001a0  fb a7 fa e6 c2 85 f5 29  cb 88 aa 19 4d 16 60 dd  |.......)....M.`.|
000001b0  a7 e9 ec 9c 45 64 d3 96  89 0d 03 c3 03 57 00 fe  |....Ed.......W..|
000001c0  ff ff 82 fe ff ff 02 d8  fc 6a 00 f0 ff 00 00 fe  |.........j......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 d8 fc 6a 00 00  |.............j..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on pdc_bechaeiegi3


Unknown BootLoader on pdc_bechaeiegi5


Unknown BootLoader on pdc_bechaeiegi6



========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

ERROR: dos: partition address past end of RAID device
/home/ubuntu/Desktop/boot_info_script.sh: line 1577: [: 2.73495e+09: integer expression expected
hexdump: /dev/mapper/pdc_bechaeiegi3: No such file or directory
hexdump: /dev/mapper/pdc_bechaeiegi3: No such file or directory
hexdump: /dev/mapper/pdc_bechaeiegi5: No such file or directory
hexdump: /dev/mapper/pdc_bechaeiegi5: No such file or directory
hexdump: /dev/mapper/pdc_bechaeiegi6: No such file or directory
hexdump: /dev/mapper/pdc_bechaeiegi6: No such file or directory
ERROR: dos: partition address past end of RAID device


```

---

### Post by raucous1 on 2011-05-14
[SIZE="1"]Let's try reinstalling GRUB from the LiveCD as a first step in troubleshooting this:

Code:
sudo mount /dev/sda4 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
Back in Ubuntu, run

Code:
sudo update-grub
and see what happens.[/SIZE]

[SIZE="3"]I tried this, assuming that the last step (sudo update-grub) was supposed to be done back in the hard-drive system.I still get[/SIZE]

> Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done


---

### Post by drs305 on 2011-05-14
Grub isn't going to find your Windows OS as long as Ubuntu registers the fuse errors. Note the CD can't see anything on sda, including any boot files in your Windows partitions. Grub looks for the boot files, and when it finds them, builds the appropriate menu entry.

If you run "sudo fdisk -l" (lowercase L) does it show the partitions correctly?

I don't know what is causing the fuse errors - the CD can read one of the other drivers.  Fix that and updating grub will probably add a bootable Windows menuentry.

---

### Post by raucous1 on 2011-05-14
sudo fdisk -l

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ebb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4571    36613120    7  HPFS/NTFS
/dev/sda3            8827      121602   905864193    5  Extended
/dev/sda4            4571        8827    34180096   83  Linux
/dev/sda5          120558      121602     8386560   82  Linux swap / Solaris
/dev/sda6            8827      120558   897477632   83  Linux

Partition table entries are not in disk order

Disk /dev/sdg: 16.0 GB, 16028794368 bytes
64 heads, 32 sectors/track, 15286 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004d55d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       15286    15652848    c  W95 FAT32 (LBA)

```

---

### Post by drs305 on 2011-05-14
That message for 'Partition 1' looks ominous but it is harmless.

Are you able to boot your normal Ubuntu OS? And if so, are the fuse error messages gone? If so, please post a new RESULTS.txt. 

Also, if you can run Ubuntu without the LiveCD, do you get any error messages when you run these commands:
```

sudo update-grub
sudo os-prober
```

---

### Post by raucous1 on 2011-05-14
Solved it!

Apparently the problem was "raid metadata" left on my harddrive. Following the advice from this post:

[http://ubuntuforums.org/showthread.php?t=1267663]("http://ubuntuforums.org/showthread.php?t=1267663")

I used these commands:

```
# disable the raid setup
dmraid -an
dmraid -si

# remove the metadata
dmraid -E -r
```

Ran 'update-grub' and it found Windows 7. Perfect! 

Thanks for your help everyone.

---

### Post by Rubi1200 on 2011-05-15
Excellent! Glad you got it sorted out.

Enjoy :-)

---

### Post by Allleksandar on 2011-06-19
having the same problem 
 i`ve try 
dmraid -ani get (The program 'dmraid' is currently not installed.)
can any one help me ?

---

### Post by zaciatocnik on 2011-12-05
Hello, please help me if you can. I can't see the GRUB2 boot menu for selecting windows7 or linux after BIOS POST. (sorry for my english) Thank you. :(

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   $MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 67. But according to the info from fdisk, 
                       sda5 starts at sector 92229232.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 5 R1 - Code Name 
                       Revolution 32 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             64    76,562,426    76,562,363   7 NTFS / exFAT / HPFS
/dev/sda2          92,229,230   312,580,095   220,350,866   5 Extended
/dev/sda5          92,229,232   260,012,024   167,782,793   7 NTFS / exFAT / HPFS
/dev/sda6         260,012,032   310,315,007    50,302,976  83 Linux
/dev/sda7         310,317,056   312,580,095     2,263,040  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D03C64E73C64C9D4                       ntfs       c_system_win7
/dev/sda5        02FC4428FC4417F5                       ntfs       data
/dev/sda6        11c440b0-3e2c-476b-bb31-b9a89d3f2737   ext4       
/dev/sda7        6168d57c-9971-4a82-b0ff-3e309b48b133   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.39.4' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=11c440b0-3e2c-476b-bb31-b9a89d3f2737 ro   text splash vga=791
    initrd    /boot/initrd.img-2.6.39.4
}
menuentry 'Ubuntu, with Linux 2.6.39.4 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
    echo    'Loading Linux 2.6.39.4 ...'
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=11c440b0-3e2c-476b-bb31-b9a89d3f2737 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39.4
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=11c440b0-3e2c-476b-bb31-b9a89d3f2737 ro   text splash vga=791
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
    echo    'Loading Linux 2.6.32-36-generic ...'
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=11c440b0-3e2c-476b-bb31-b9a89d3f2737 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-36-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 11c440b0-3e2c-476b-bb31-b9a89d3f2737
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=11c440b0-3e2c-476b-bb31-b9a89d3f2737 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6168d57c-9971-4a82-b0ff-3e309b48b133 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 132.345710754 = 142.105124864  boot/grub/core.img                             1
 126.635810852 = 135.974166528  boot/grub/grub.cfg                             1
 124.146705627 = 133.301510144  boot/initrdf.img-2.6.39.4                      1
 129.014648438 = 138.528423936  boot/initrd.img-2.6.32-36-generic              2
 126.041030884 = 135.335526400  boot/initrd.img-2.6.39.4                       2
 124.162330627 = 133.318287360  boot/initrds.img-2.6.39.4                      1
 132.341384888 = 142.100480000  boot/vmlinuz-2.6.32-36-generic                 1
 132.114303589 = 141.856653312  boot/vmlinuz-2.6.39.4                          1
 129.014648438 = 138.528423936  initrd.img                                     2
 126.041030884 = 135.335526400  initrd.img.old                                 2
 132.341384888 = 142.100480000  vmlinuz                                        1
 132.114303589 = 141.856653312  vmlinuz.old                                    1
  
```
************************************************
OK :popcorn: I fixed it using win7 boot DVD, repair mode, 
  ```
bootsect.exe /nt60 all
``` commad and then, back in the linux the ```
update-grub
```  command :)

---

