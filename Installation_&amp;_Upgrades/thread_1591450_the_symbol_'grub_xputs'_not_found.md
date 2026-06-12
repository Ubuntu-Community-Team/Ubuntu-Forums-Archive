---
title: "the symbol 'grub_xputs' not found"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by ost2life on 2010-10-09
HELP! I appear to have cocked my upgrade to 10:10 right up. First the upgrade seemed to go fine until the reboot when I got dumped to the GRUB rescue prompt with the error "the symbol 'grub_xputs' not found". I tried to follow the instructions on [www.ubuntuforums.org/showthread.php?t=1580752](www.ubuntuforums.org/showthread.php?t=1580752) and now all I get is rapidly blinking underscore in the top left, which wont accept any input.

UPDATE:
I'm also trying this one [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

---

### Post by sideaway on 2010-10-10
I get this as well, I ran the bootinfo bash script and get the following;

Can anyone help?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf
 => Grub 2 is installed in the MBR of /dev/mapper/nvidia_djhfhafb and looks on 
    the same drive in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdd1 already mounted or sdd1 busy

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdd1 already mounted or sdd1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdd4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdd1 already mounted or sdd1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sdd4 already mounted or sdd4 busy

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

nvidia_djhfhafb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

nvidia_djhfhafb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

nvidia_djhfhafb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_djhfhafb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

nvidia_djhfhafb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,519,615 1,953,517,568   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048    58,587,135    58,585,088  83 Linux
/dev/sdd2          58,589,116    66,589,424     8,000,309   5 Extended
/dev/sdd5          58,589,118    66,589,424     8,000,307  82 Linux swap / Solaris
/dev/sdd3    *     66,590,720   187,975,679   121,384,960   7 HPFS/NTFS
/dev/sdd4         187,976,565   390,716,864   202,740,300  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


Drive: nvidia_djhfhafb ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_djhfhafb: 200.0 GB, 200049623040 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_djhfhafb1              2,048    58,587,135    58,585,088  83 Linux
/dev/mapper/nvidia_djhfhafb2         58,589,116    66,589,424     8,000,309   5 Extended
/dev/mapper/nvidia_djhfhafb5         58,589,118    66,589,424     8,000,307  82 Linux swap / Solaris
/dev/mapper/nvidia_djhfhafb3   *     66,590,720   187,975,679   121,384,960   7 HPFS/NTFS
/dev/mapper/nvidia_djhfhafb4        187,976,565   390,716,864   202,740,300  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_djhfhafb1 2c3b2240-133c-4ee1-a13e-099463d6c97c   ext4                                     
/dev/mapper/nvidia_djhfhafb3 2CD0D4C9D0D49B02                       ntfs                                     
/dev/mapper/nvidia_djhfhafb4 98384c72-6e9d-408c-9951-47b2215ff4ec   ext4                                     
/dev/mapper/nvidia_djhfhafb5 93645ecc-7ce6-483e-9b4e-334c823a0c8d   swap                                     
/dev/mapper/nvidia_djhfhafb: PTTYPE="dos" 
/dev/sda1        F2388FA0388F6309                       ntfs       First tb                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        518E81ED0DC23652                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        705EB65471F84A8A                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        2c3b2240-133c-4ee1-a13e-099463d6c97c   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd3        2CD0D4C9D0D49B02                       ntfs                                     
/dev/sdd4        98384c72-6e9d-408c-9951-47b2215ff4ec   ext4                                     
/dev/sdd5        93645ecc-7ce6-483e-9b4e-334c823a0c8d   swap                                     
/dev/sdd                                                nvidia_raid_member                               
/dev/sde1        28BFFB126F16DD75                       ntfs       New tb                        
/dev/sde: PTTYPE="dos" 
/dev/sdf1        01E006162323F47C                       ntfs       2.0 TB                        
/dev/sdf: PTTYPE="dos" 
error: /dev/mapper/nvidia_djhfhafb2: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


===================== nvidia_djhfhafb1/boot/grub/grub.cfg: =====================

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=2c3b2240-133c-4ee1-a13e-099463d6c97c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=2c3b2240-133c-4ee1-a13e-099463d6c97c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=2c3b2240-133c-4ee1-a13e-099463d6c97c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=2c3b2240-133c-4ee1-a13e-099463d6c97c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set 2c3b2240-133c-4ee1-a13e-099463d6c97c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos3)'
	search --no-floppy --fs-uuid --set 2cd0d4c9d0d49b02
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

========================= nvidia_djhfhafb1/etc/fstab: =========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=2c3b2240-133c-4ee1-a13e-099463d6c97c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd4 during installation
UUID=98384c72-6e9d-408c-9951-47b2215ff4ec /home           ext4    defaults        0       2
# swap was on /dev/sdd5 during installation
UUID=93645ecc-7ce6-483e-9b4e-334c823a0c8d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


/dev/sde1/	/media/TV/		auto	defaults	0       0	
/dev/sdc1/	/media/Movies/		auto	defaults	0	0
/dev/sda1/	/media/Movies2/		auto	defaults	0	0
/dev/sdb1/	/media/Installers/	auto	defaults	0	0
/dev/sdf1/	/media/Music/		auto	defaults	0	0

============= nvidia_djhfhafb1: Location of files loaded by Grub: =============


  17.3GB: boot/grub/core.img
  26.2GB: boot/grub/grub.cfg
  28.8GB: boot/initrd.img-2.6.32-25-generic-pae
  28.0GB: boot/initrd.img-2.6.35-22-generic-pae
  22.8GB: boot/vmlinuz-2.6.32-25-generic-pae
  23.0GB: boot/vmlinuz-2.6.35-22-generic-pae
  28.0GB: initrd.img
  28.8GB: initrd.img.old
  23.0GB: vmlinuz
  22.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd2

00000000  fa c2 71 47 87 01 47 6f  54 24 7b 5d 14 42 7f 99  |..qG..GoT${].B..|
00000010  09 eb 72 82 a8 e4 cd 61  2d 0f c6 8f 8a 94 4a 4e  |..r....a-.....JN|
00000020  1c cd cf b3 7d e6 0f 83  f1 65 bd 6b b3 94 b1 be  |....}....e.k....|
00000030  b3 c3 cd 3e 1f 83 f1 f0  d6 d1 5a 79 4c 3f 7e f8  |...>......ZyL?~.|
00000040  eb 19 d0 1f 50 2e d5 b1  62 89 b5 a7 22 7d 0f e5  |....P...b..."}..|
00000050  42 be fd da 56 29 43 47  cb d2 16 c6 cc 05 ed de  |B...V)CG........|
00000060  7c 63 2b 2e fc bc 56 3b  7e 77 00 e4 9b 4f ef 4d  ||c+...V;~w...O.M|
00000070  20 d0 8e 25 a1 c7 83 fc  c0 ef 69 d4 f1 6a 5c 3c  | ..%......i..j\<|
00000080  9d f7 62 d6 3a 28 8f 5c  d2 ee b4 cb d0 a2 ed 99  |..b.:(.\........|
00000090  23 83 21 df 69 9e 56 1e  98 2a f0 0c 1c 17 ca ab  |#.!.i.V..*......|
000000a0  07 fe a1 11 08 86 e4 ee  2f 1d 23 28 dd 79 0c f0  |......../.#(.y..|
000000b0  3d bd 7d 2b aa f4 3d f6  d4 39 be 6f 28 f0 b7 7d  |=.}+..=..9.o(..}|
000000c0  51 93 f9 b4 bc 2a d7 7a  be 59 cf e4 93 b0 cb 71  |Q....*.z.Y.....q|
000000d0  d4 ff 62 ce 9e 47 83 a1  fe 68 5e 72 37 c5 1d da  |..b..G...h^r7...|
000000e0  77 f6 0f af 02 e3 ed ca  bd 14 04 ed 3f e6 40 df  |w...........?.@.|
000000f0  03 fb 8f 4b 22 ef 49 c9  26 f7 73 b5 c5 cc 7c 5d  |...K".I.&.s...|]|
00000100  10 dc 81 f6 c2 ef 34 3e  cb 27 ed a9 74 47 f3 73  |......4>.'..tG.s|
00000110  01 e7 4b 82 eb 2a 19 fb  d0 a9 80 0d f5 e5 56 35  |..K..*........V5|
00000120  cb bf 67 36 bb e5 6b a6  91 c7 bd 68 fe 38 ed 53  |..g6..k....h.8.S|
00000130  32 d0 ff 28 d9 65 c8 09  bf d8 f2 3a e4 96 b4 a4  |2..(.e.....:....|
00000140  98 b1 2f 1d f2 3e b4 34  f5 63 93 22 9d c6 0b 28  |../..>.4.c."...(|
00000150  55 56 2e 0f cc b3 74 1c  31 29 00 f0 09 9a 4e d0  |UV....t.1)....N.|
00000160  78 9a 7b e1 62 99 cb 73  06 5f 9b 48 64 a2 6c 47  |x.{.b..s._.Hd.lG|
00000170  cd ac e5 30 be 64 0e 0b  cb c2 45 fe b8 ed 35 7a  |...0.d....E...5z|
00000180  c0 40 bf f6 e4 5d 19 f6  24 fe 82 b0 99 89 cf 7f  |.@...]..$.......|
00000190  ad d4 c5 61 91 ed 81 a7  c2 50 88 c7 38 7c 35 1e  |...a.....P..8|5.|
000001a0  db 91 ba 6f ca ed 38 38  7f ea 7c 52 2e f4 d8 fe  |...o..88..|R....|
000001b0  d8 2f 00 fa c7 6c ba ab  0e c8 d1 c5 77 6b 00 fe  |./...l......wk..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 33 13 7a 00 00 00  |..........3.z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on nvidia_djhfhafb2



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/nvidia_djhfhafb2: No such file or directory
hexdump: /dev/mapper/nvidia_djhfhafb2: No such file or directory
```

---

### Post by Repabil on 2010-10-10
Check out [http://ubuntuforums.org/showthread.php?t=1580752](http://ubuntuforums.org/showthread.php?t=1580752)

---

### Post by franklamoureux on 2010-10-14
If you have more than 1 SATA drive, check out also my update in [http://ubuntuforums.org/showthread.php?p=9969299#post9969299]("http://ubuntuforums.org/showthread.php?p=9969299#post9969299")

---

### Post by fermulator on 2011-01-08
It's unacceptable.  Any normal user would have a hard time figuring this out, if they even tried.  Upgrading distributions SHOULD NOT break the boot sequence!

Here's the bug report that I found: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/609280](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/609280)

I fixed mine with:
 1) Boot alternate 10.04 disc
 2) drop to shell with the root partition as my ubuntu partition (/dev/mapper/isw_fegbaeadg_RAID0_SSD1
 3) re-install grub on the MBR of the drive containing ubuntu:
```
# grub-install /dev/mapper/isw_fegbaeadg_RAID0_SSD
```

Rebooted, and I was back in business.

---

### Post by bororeh on 2011-05-05
What if I don't have the disc? Is is possible to do this without it?

---

### Post by Repabil on 2011-05-05
I think you'll need to boot from a CD or an USB drive. There's instructions to create on of those in step 2 "Burn your CD or create a USB drive" of [the download page](http://www.ubuntu.com/download/ubuntu/download).

Also check the thread I linked in my previous post.

---

### Post by bororeh on 2011-05-05
I got to that thread before this one. It also mentions CD using. I downloaded the installation and now I'm gonna try to use a pen drive.
Thank you!

PS: lousy, lousy, lousy bug, ain't it? I use ubuntu for two months now and I am not comfortable at all doing this kind of stuff.

---

### Post by Repabil on 2011-05-05
Yeah, go for an USB drive if you can. They boot much faster than CDs.

It is a nasty problem. I have had to deal with it every upgrade since more than a year back. Doing some research I found what might be [a permanent solution](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589737#30).

---

### Post by bororeh on 2011-05-05
This is harder to fix than I thought!

I did what user drs305 said at the topic u mentioned, but all I've got was a weird blinking cursor at the screen where boot options should appear.

Here is what I did:

Created "Live PenDrive"
Booted from it
At the terminal:
```
 sudo mount /dev/sda5 /mnt
 sudo grub-install --root-directory=/mnt /dev/sda 
```
Restarted

What now? Any ideas? Ty!

---

### Post by Repabil on 2011-05-05
Did the command, grub-install, finish with success?

Are you sure that you are feeding the command with the right drives? That is are you sure that /dev/sda is your boot drive?

---

### Post by bororeh on 2011-05-05
> **Repabil said:**
> Did the command, grub-install, finish with success?

Are you sure that you are feeding the command with the right drives? That is are you sure that /dev/sda is your boot drive?

Yes, yes. I checked the devices in the Disk Utility (from Live Pen).

After typing the commands at the terminal, I received the message:
"Installation finished. No error reported."
I felt great, until I tried to restart and get the same error again (the weird blinking cursor).

---

### Post by kansasnoob on 2011-05-05
> **bororeh said:**
> Yes, yes. I checked the devices in the Disk Utility (from Live Pen).

After typing the commands at the terminal, I received the message:
"Installation finished. No error reported."
I felt great, until I tried to restart and get the same error again (the weird blinking cursor).

Would it be terribly inconvenient for you to DL and burn this disc:

[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

It's really not designed to fix anything but just to help boot unbootable OS's, and I'd prefer not fixing this with anything but Ubuntu's own grub anyway.

I've had very good luck with the Detect any OS option. Expect it to be slow, like maybe even a couple of minutes slow booting :)

If that gets you booted then I should get some additional info, like the output of these three commands (please copy-n-paste):

```
sudo parted -l
```

```
df -H
```

```
uname -m
```

---

### Post by drs305 on 2011-05-05
> **bororeh said:**
> I did what user drs305 said at the topic u mentioned, but all I've got was a weird blinking cursor at the screen where boot options should appear.
What now? Any ideas? Ty!

You describe it as 'weird', so I am not sure what I'll post is relevant to you or not. Is it just a normal, blinking cursor in the upper left part of the screen?

When Grub2 fails, it will either give you an error message or leave you at the 'grub' or 'grub rescue' prompt. It's possible G2 has passed control to the initrd image or kernel and you have a video problem.

If you think this might be the case and you can get to the Grub menu (hold SHIFT down if necessary to get the menu to display), let us know and we can tell you what to try next.

---

### Post by kansasnoob on 2011-05-05
> **drs305 said:**
> You describe it as 'weird', so I am not sure what I'll post is relevant to you or not. Is it just a normal, blinking cursor in the upper left part of the screen?

When Grub2 fails, it will either give you an error message or leave you at the 'grub' or 'grub rescue' prompt. It's possible G2 has passed control to the initrd image or kernel and you have a video problem.

If you think this might be the case and you can get to the Grub menu (hold SHIFT down if necessary to get the menu to display), let us know and we can tell you what to try next.

I just assumed that bororeh was getting this error, the symbol 'grub_xputs' not found, since he latched onto this old thread :confused:

---

### Post by drs305 on 2011-05-05
> **kansasnoob said:**
> I just assumed that bororeh was getting this error, the symbol 'grub_xputs' not found, since he latched onto this old thread :confused:

I thought he had fixed the 'xputs' problem and now has the blinking cursor.

@ bororeh,

Please look at the recent posts by *kansasnoob* and me. Decide which one deals with your problem and if you need further help please confirm your current problem.

---

### Post by kansasnoob on 2011-05-05
> **drs305 said:**
> I thought he had fixed the 'xputs' problem and now has the blinking cursor.

@ bororeh,

Please look at the recent posts by *kansasnoob* and me. Decide which one deals with your problem and if you need further help please confirm your current problem.

Things do get confusing at times, then again the only time I'm not confused is when I'm sleeping :)

---

### Post by bororeh on 2011-05-05
Ok! One at a time... but, first of all, let me say I'm sorry for letting you guys waiting and thank you for the concern! The problem with my pc's boot was fixed and I just had to get back to work, completely forgetting the topic.

Now!!

Kansasnoob: Since the problem is solved, I wont have to burn any disks (of course it would not be a terrible inconvenient, but even better this way, dont you think?)

drs 305: yes, the weird cursor is on the left upper corner. It was not normal, it blinked faster than usual and was bigger and looked buggy. This only appeared AFTER I tried your solution.

Using the Live Pen and seeing that my files were, it occured to me that all I needed was to recover grub, so I looked some simple *howtos* and found this:

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

What solved my problem and saved my day were these lines:

```

$ sudo mount /dev/sda5 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /dev/pts  /mnt/dev/pts
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys  /mnt/sys
$ sudo chroot /mnt
# grub-install --recheck /dev/sda 
$ sudo aptitude install grub2

```A little note: I don't even know what most of them means. I just copied every character, closed my eyes and pressed enter. Still... I think the only difference between drs 305's solution and this one was updating the grub after calling it a bunch of names! That made it feel good and do its work.

---

### Post by bororeh on 2011-05-05
I just wanted to say thanks once again. These problems are a terrible headache... and you were all very kind!

Thanks a lot and good night!

---

### Post by drs305 on 2011-05-05
> **bororeh said:**
> A little note: I don't even know what most of them means. 

Glad it's working. 

What you did was use a procedure called 'chroot'. It loads your CD's system files to run operations on your real Ubuntu partition. I won't go into more specifics lest your head start hurting. You can certainly find more information about the process if you wish.

Happy Ubuntu-ing !

---

### Post by karg on 2011-09-07
After upgrading to 11.04 x64 I had the same problem: 

The symbol 'grub_xputs' not found.
grub_rescue>_

1. Rebooted with Ubuntu CD 11.04
2. sudo mount /dev/sda2 /mnt
3. sudo grub-install --root-directory=/mnt /dev/sda
4. Reboot

Here /dev/sda2 is the linux boot partition.

Worked perfectly :)

---

