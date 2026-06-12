---
title: "Unwanted clone of install"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by Yooper on 2011-01-19
Let me preface this by saying I may be in way over my head.


I made a machine that dual boots Windows Vista and Ubuntu 10.10.  Every thing was fab.  I would turn the computer on and the screen for me to select the operating system would appear.  Everything worked great.

Then one day a third set of options appeared, it was a clone of the ubuntu that I had already installed.   Shortly there after, a fourth option appeared, it was another ubuntu.

The computer would load fine when left unattended until today.  I get the following error:

Kernel Panic

Please note, if I select one of the other ubuntu installs, the system loads up just fine.

Any help is appreciated.

---

### Post by presence1960 on 2011-01-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Yooper on 2011-01-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => No known boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sde2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             64   306,986,084   306,986,021   7 HPFS/NTFS
/dev/sda2         306,986,088   511,911,224   204,925,137   7 HPFS/NTFS
/dev/sda3         511,911,286   669,411,327   157,500,042   5 Extended
/dev/sda5         511,911,288   629,925,640   118,014,353   7 HPFS/NTFS
/dev/sda6         629,925,888   667,674,623    37,748,736  83 Linux
/dev/sda7         667,676,672   669,411,327     1,734,656  82 Linux swap / Solaris
/dev/sda4         669,412,488   976,768,064   307,355,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sde: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 926 cylinders, total 14651280 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63        48,194        48,132   0 Empty
/dev/sde2              48,195    14,651,278    14,603,084   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        585A6A635A6A3E3E                       ntfs       Windows                       
/dev/sda2        120062AC0062970F                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        E66A5B616A5B2E15                       ntfs                                     
/dev/sda5        F03447C034478914                       ntfs       New Volume                    
/dev/sda6        4ab094fd-5671-4caf-a537-b359cb4c4235   ext4                                     
/dev/sda7        338409bd-fda6-4b7b-a5b0-0946f6ee5b08   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4E40F7F340F7DF9F                       ntfs       Storage 2                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B244D59C44D5639F                       ntfs       Storage 1                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        E20467CA04679FF1                       ntfs       Storage 3                     
/dev/sdd: PTTYPE="dos" 
/dev/sde2        8F1A-98E0                              vfat       DAVE                          
/dev/sde         A88B-3652                              vfat       iPod                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sde2        /media/DAVE              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 585a6a635a6a3e3e
	chainloader +1
}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=338409bd-fda6-4b7b-a5b0-0946f6ee5b08 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 337.7GB: boot/grub/core.img
 325.0GB: boot/grub/grub.cfg
 325.5GB: boot/initrd.img-2.6.35-22-generic-pae
 325.6GB: boot/initrd.img-2.6.35-23-generic-pae
 325.5GB: boot/initrd.img-2.6.35-24-generic-pae
 337.7GB: boot/vmlinuz-2.6.35-22-generic-pae
 337.8GB: boot/vmlinuz-2.6.35-23-generic-pae
 337.8GB: boot/vmlinuz-2.6.35-24-generic-pae
 325.5GB: initrd.img
 325.6GB: initrd.img.old
 337.8GB: vmlinuz
 337.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sde

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 08 08 00 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  8f 8f df 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  02 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 00 fe 3f 02 3f 00  00 00 04 bc 00 00 00 00  |....?.?.........|
000001d0  01 03 0b fe fe 8f 43 bc  00 00 4c d3 de 00 00 00  |......C...L.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde1

00000000  7b 7b 7e 7e 20 20 2f 2d  2d 2d 2d 2d 5c 20 20 20  |{{~~  /-----\   |
00000010  7b 7b 7e 7e 20 2f 20 20  20 20 20 20 20 5c 20 20  |{{~~ /       \  |
00000020  7b 7b 7e 7e 7c 20 20 20  20 20 20 20 20 20 7c 20  |{{~~|         | |
00000030  7b 7b 7e 7e 7c 20 53 20  54 20 4f 20 50 20 7c 20  |{{~~| S T O P | |
00000040  7b 7b 7e 7e 7c 20 20 20  20 20 20 20 20 20 7c 20  |{{~~|         | |
00000050  7b 7b 7e 7e 20 5c 20 20  20 20 20 20 20 2f 20 20  |{{~~ \       /  |
00000060  7b 7b 7e 7e 20 20 5c 2d  2d 2d 2d 2d 2f 20 20 20  |{{~~  \-----/   |
00000070  43 6f 70 79 72 69 67 68  74 28 43 29 20 32 30 30  |Copyright(C) 200|
00000080  31 20 41 70 70 6c 65 20  43 6f 6d 70 75 74 65 72  |1 Apple Computer|
00000090  2c 20 49 6e 63 2e 2d 2d  2d 2d 2d 2d 2d 2d 2d 2d  |, Inc.----------|
000000a0  2d 2d 2d 2d 2d 2d 2d 2d  2d 2d 2d 2d 2d 2d 2d 2d  |----------------|
*
000000f0  2d 2d 2d 2d 2d 2d 2d 2d  2d 2d 2d 2d 2d 2d 2d 00  |---------------.|
00000100  5d 69 68 5b 00 40 00 00  0c 01 03 00 00 00 00 00  |]ih[.@..........|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

Unknown BootLoader  on sde2

00000000  eb 3c 90 2a 55 4f 4b 4a  49 48 43 00 08 08 20 00  |.<.*UOKJIHC... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 43 bc 00 00  |........?...C...|
00000020  4a d3 de 00 ed 0d 00 00  00 00 00 00 02 00 00 00  |J...............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e0 98 1a 8f 49  50 4f 44 20 20 20 20 20  |..)....IPOD     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 5b 7c ac  |  FAT32   ...[|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 7b  7b 7e 7e 7c 20 53 20 54  |.......{{~~| S T|
00000080  20 4f 20 50 20 7c 20 54  68 69 73 20 69 73 20 41  | O P | This is A|
00000090  70 70 6c 65 20 69 50 6f  64 20 6e 6f 74 20 61 20  |pple iPod not a |
000000a0  62 6f 6f 74 61 62 6c 65  20 64 69 73 6b 2e 50 6c  |bootable disk.Pl|
000000b0  65 61 73 65 20 74 72 79  20 61 67 61 69 6e 20 2e  |ease try again .|
000000c0  2e 2e 20 00 00 00 00 00  00 00 00 00 00 00 00 00  |.. .............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Yooper on 2011-01-20
In advance, thank you for any and all help you provide.

---

### Post by presence1960 on 2011-01-20
The following is from your grub.cfg:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry [COLOR="Red"]'Ubuntu, with Linux 2.6.35-24-generic-pae[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry '[COLOR="Red"]Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry '[COLOR="Red"]Ubuntu, with Linux 2.6.35-23-generic-pae[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
[COLOR="Red"]menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry '[COLOR="Red"]Ubuntu, with Linux 2.6.35-22-generic-pae[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry '[COLOR="Red"]Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 4ab094fd-5671-4caf-a537-b359cb4c4235
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=4ab094fd-5671-4caf-a537-b359cb4c4235 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###
```

They are not clones of Ubuntu but rather kernels. When kernels are included in the updates to Ubuntu the new kernel will appear in GRUB menu.

Which kernel will not boot? You want to remove it by going System > Administration > Synaptic Package Manager. Remove the offending kernel (say it is 2.6.35-24) by ticking the box and Marking For Complete Removal linux-image 2.6.35-24 and linux-headers-2.6.35-24. Click Apply at top. Now go back and mark them both for installation. When complete reboot and try booting that same kernel. If it does not boot properly remove the kernel again and leave it removed. it is important that you mark them for complete removal not mark for removal. When you mark for removal the package(s) are uninstalled but the download remains in cache. if the problem was a corrupted download the same download will be installed again from cache. When you mark for complete removal the package(s) are uninstalled and the downloaded package is removed from cache. So next time you try to install the package(s) they will be downloaded again and installed.

It is suggested to keep the two most recent kernels that work. That way if one has a problem and won't boot you can boot to the alternate kernel and troubleshoot and hopefully fix the problem.

FYI info here is your hard disk sda and you will see in red your one and only ubuntu install (no clones):
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => No known boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

[COLOR="Red"]sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
[/COLOR]
sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
```

Edit: mark for complete removal linux-headers-2.6.35-24-generic-pae & linux-image-2.6.35-24-generic-pae 
sorry I forgot you have pae enabled kernel.

---

### Post by presence1960 on 2011-01-20
In windows when you need updates you must go to windows update for windows security updates and for hardware updates to each manufacturer's website to get updated drivers. In linux you get security and kernel updates from the repositories. In linux all are combined with the kernel. You don't have to download a separate driver for each piece of hardware as in windows. So when a kernel update comes out it basically has almost everything needed except for a few hardware for which there are no linux drivers.

---

### Post by Yooper on 2011-01-21
Thank you so much for the help and explanation.  The offending kernel magically worked on reboot.   Thank you again, and if this problem comes up again, I know how to fix it.  THANK YOU.

---

### Post by presence1960 on 2011-01-21
> **Yooper said:**
> Thank you so much for the help and explanation.  The offending kernel magically worked on reboot.   Thank you again, and if this problem comes up again, I know how to fix it.  THANK YOU.

You are welcome. Enjoy Ubuntu!

---

