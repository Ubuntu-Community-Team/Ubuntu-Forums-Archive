---
title: "Grub 2 can't find ntoskrnl.exe - Dual Boot issue"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by djvbmd on 2011-02-07
Hi all --

Recently I decided to quit keeping Ubuntu locked up in a VirtualBox and migrate back to a dual boot configuration.  I have 2 internal HDDs.  Before installing Ubuntu, I resized the main data partition on the data drive to create some free space.  I installed 10.10 there after booting from a USB flashdrive.

All seemed to go smoothly, and once I set the BIOS to boot from what was previously the data drive, the grub menu came up and Ubuntu booted normally.

However, when I try to boot XP from the grub menu, I get the following error (paraphrased):
<windows>\system32\ntoskrnl.exe is corrupt or missing

If I go into BIOS and change the HDD boot priority back to the original system drive, XP boots normally. (It did want me to run chkdsk, though -- no errors, and XP still won't boot from grub after running it.)

The info from the boot_info_script is below.  Thanks for any light you can shed on this...

djvbmd

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63        80,324        80,262  de Dell Utility
/dev/sda2              80,325   119,792,336   119,712,012   7 HPFS/NTFS
/dev/sda3         119,793,662   234,372,284   114,578,623   f W95 Ext d (LBA)
/dev/sda5         201,310,578   234,372,284    33,061,707   7 HPFS/NTFS
/dev/sda6         119,793,664   197,873,663    78,080,000  83 Linux
/dev/sda7         197,875,712   201,310,207     3,434,496  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   321,669,494   321,669,432   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D2-0C0B                              vfat       DellUtility                   
/dev/sda2        1CD43CBDD43C9B4A                       ntfs       beta                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        01CBC25A0B461AA0                       ntfs       PageFile                      
/dev/sda6        98b22061-62bc-45e9-bbf9-5d25762117e3   ext4                                     
/dev/sda7        f26b500d-15a4-4cd2-bcfd-19881eb4eea6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        08C49FADC49F9B8E                       ntfs       alpha                         
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        F44850B348507678                       ntfs       FreeAgent Drive               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/WirelessSetup     iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 98b22061-62bc-45e9-bbf9-5d25762117e3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 98b22061-62bc-45e9-bbf9-5d25762117e3
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 98b22061-62bc-45e9-bbf9-5d25762117e3
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=98b22061-62bc-45e9-bbf9-5d25762117e3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 98b22061-62bc-45e9-bbf9-5d25762117e3
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=98b22061-62bc-45e9-bbf9-5d25762117e3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 98b22061-62bc-45e9-bbf9-5d25762117e3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 98b22061-62bc-45e9-bbf9-5d25762117e3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 08c49fadc49f9b8e
	drivemap -s (hd0) ${root}
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
UUID=98b22061-62bc-45e9-bbf9-5d25762117e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=f26b500d-15a4-4cd2-bcfd-19881eb4eea6 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  93.8GB: boot/grub/core.img
  74.4GB: boot/grub/grub.cfg
  91.6GB: boot/initrd.img-2.6.35-25-generic-pae
  93.9GB: boot/vmlinuz-2.6.35-25-generic-pae
  91.6GB: initrd.img
  93.9GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 00 29 0b  0c d2 07 44 65 6c 6c 55  |.9....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 ff 0e 13  04 8b 0e 13 04 c1 e1 06  |{...............|
00000060  8e c1 b9 00 01 33 f6 33  ff f3 66 a5 c7 06 72 04  |.....3.3..f...r.|
00000070  45 44 8e c0 bd 00 7c e8  21 01 0f 82 bb 00 66 0f  |ED....|.!.....f.|
00000080  b7 86 16 00 66 d1 e0 66  0f b7 9e 0e 00 66 03 c3  |....f..f.....f..|
00000090  66 03 86 1c 00 66 89 86  3e 00 8b 86 11 00 c1 e8  |f....f..>.......|
000000a0  04 89 86 46 00 bb 00 05  e8 aa 00 0f 82 8a 00 ba  |...F............|
000000b0  10 00 b9 0b 00 be ec 7d  8b fb f3 a6 74 16 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 86 3e  00 ff 8e 46 00 75 d6 be  | Ju.f..>...F.u..|
000000d0  d9 7d eb 6d 66 0f b7 86  11 00 66 ba 20 00 00 00  |.}.mf.....f. ...|
000000e0  66 f7 e2 66 0f b7 8e 0b  00 66 03 c1 66 48 66 f7  |f..f.....f..fHf.|
000000f0  f1 66 01 86 3e 00 66 8b  86 3e 00 66 89 46 fc 66  |.f..>.f..>.f.F.f|
00000100  0f b7 47 1a 8b f8 2d 02  00 66 0f b6 9e 0d 00 66  |..G...-..f.....f|
00000110  f7 e3 66 01 86 3e 00 bb  00 07 c7 86 46 00 04 00  |..f..>......F...|
00000120  e8 32 00 72 14 81 c3 00  02 66 ff 86 3e 00 ff 8e  |.2.r.....f..>...|
00000130  46 00 75 ec ea 00 02 70  00 be cc 7d eb 03 be d9  |F.u....p...}....|
00000140  7d e8 02 00 eb fe ac 3c  00 74 09 b4 0e bb 07 00  |}......<.t......|
00000150  cd 10 eb f2 c3 66 8b 86  3e 00 66 33 d2 66 0f b7  |.....f..>.f3.f..|
00000160  8e 18 00 66 f7 f1 66 42  88 96 45 00 66 33 d2 66  |...f..fB..E.f3.f|
00000170  0f b7 8e 1a 00 66 f7 f1  88 96 44 00 89 86 42 00  |.....f....D...B.|
00000180  b8 01 02 8b 8e 42 00 c0  e5 06 0a ae 45 00 86 e9  |.....B......E...|
00000190  8a b6 44 00 8a 96 24 00  cd 13 c3 80 3e c2 07 06  |..D...$.....>...|
000001a0  74 29 b8 01 02 bb 00 06  b9 01 00 b6 00 8a 96 24  |t).............$|
000001b0  00 cd 13 72 16 c6 06 c2  07 06 b8 01 03 bb 00 06  |...r............|
000001c0  b9 01 00 b6 00 8a 96 24  00 cd 13 c3 44 69 73 6b  |.......$....Disk|
000001d0  20 65 72 72 6f 72 0d 0a  00 4d 69 73 73 69 6e 67  | error...Missing|
000001e0  20 27 69 6f 2e 73 79 73  27 0d 0a 00 49 4f 20 20  | 'io.sys'...IO  |
000001f0  20 20 20 20 53 59 53 00  00 00 00 00 00 00 55 aa  |    SYS.......U.|
00000200

Unknown BootLoader  on sda3

00000000  47 1b cd 2e c2 3e 06 f9  2c 1a c4 9d ba d0 90 64  |G....>..,......d|
00000010  74 e5 49 a8 83 2c 6c a5  ce ad 3c 80 af 9e 7e 64  |t.I..,l...<...~d|
00000020  f5 ae c1 ef 9c 79 e5 6b  53 14 59 fe 92 5b eb e2  |.....y.kS.Y..[..|
00000030  18 d9 57 4e 79 e0 19 e9  04 16 73 c5 c7 20 25 56  |..WNy.....s.. %V|
00000040  16 9f 00 6b 86 f0 ab 3d  7b 1e 84 49 74 73 5f d2  |...k...={..Its_.|
00000050  50 99 3d 5e a1 e1 89 e8  44 25 57 8e 3a a3 0e ca  |P.=^....D%W.:...|
00000060  d0 56 6f 11 00 62 04 22  fa a9 a8 5f 69 60 0b 32  |.Vo..b."..._i`.2|
00000070  bc 69 f4 4c 74 8a 2e bd  3c ff 9f 1b 35 b4 e1 81  |.i.Lt...<...5...|
00000080  62 4f 1d 23 1c 47 92 f3  05 ed 13 da b1 31 87 2e  |bO.#.G.......1..|
00000090  b3 1d 7d 4c b3 90 19 05  c0 e1 c2 26 09 94 b8 da  |..}L.......&....|
000000a0  de ec 79 1c d3 cc 35 f7  6a 35 53 cb fc 6b 90 05  |..y...5.j5S..k..|
000000b0  38 9d f7 26 36 51 ed f1  83 43 dd 6e 23 b6 af de  |8..&6Q...C.n#...|
000000c0  9b a4 7c 7c 63 ec 95 46  f1 87 2d 8d ad d6 30 bc  |..||c..F..-...0.|
000000d0  f5 73 8b a9 59 4a c0 fb  87 a0 e3 5b 1b fa e7 b6  |.s..YJ.....[....|
000000e0  27 34 31 6a b2 31 b9 84  3f f2 52 79 8d 1b 5f 98  |'41j.1..?.Ry.._.|
000000f0  97 bd 43 e7 74 32 3a 99  86 e1 f1 79 5c 08 b5 5a  |..C.t2:....y\..Z|
00000100  b6 32 32 e0 e2 b6 dc 69  ac a7 d2 cd 7d cf ed 7c  |.22....i....}..||
00000110  63 4a c8 cd 8a 37 d6 eb  ae 1d 75 a2 cf ac a6 b1  |cJ...7....u.....|
00000120  d9 87 d5 c2 45 cc c6 4d  37 97 1d 4f 26 a8 35 75  |....E..M7..O&.5u|
00000130  c9 35 94 34 ad 19 7d fb  47 ce ac e3 1d 92 ba 75  |.5.4..}.G......u|
00000140  ed 43 6b 6e f0 bb 66 8d  0d 3e 33 3e 2f be 55 a3  |.Ckn..f..>3>/.U.|
00000150  37 fb b7 cc ca fb 8b e1  bc 40 11 9f 53 e5 5d d2  |7........@..S.].|
00000160  c1 86 f2 51 fc 85 f3 72  3c 6b 9f 02 6c b8 7b 44  |...Q...r<k..l.{D|
00000170  3e db e3 f3 f6 8a da bd  8c 37 88 1b e6 90 26 31  |>........7....&1|
00000180  fb 58 f9 ab 9c cd ed 9d  e1 e9 65 e2 a7 dc 15 73  |.X........e....s|
00000190  08 2c a0 bf 1c 7b 67 86  95 a0 e9 cc 0a f1 ba 57  |.,...{g........W|
000001a0  16 64 83 ea 7c 4b 43 83  e4 7f 51 dc 8d 6f 6c f3  |.d..|KC...Q..ol.|
000001b0  7d 97 57 a6 d0 1d a4 86  9b f0 a8 e3 c0 49 00 fe  |}.W..........I..|
000001c0  ff ff 07 fe ff ff 74 d9  db 04 4b 7b f8 01 00 fe  |......t...K{....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 68 a7 04 00 00  |...........h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2011-02-08
Your windows in sdb1 says it is in sda1.

multi(0)disk(0[COLOR=Red])rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows

I do not know if you can change that to rdisk(1) and it will work or not, but grub's drivemap may be telling windows it is the wrong drive.

Can you physically reverse drives, so windows is drive 0?

You also have RAID?
/dev/sdb          nvidia_raid_member  

Did you at some point turn on RAID in BIOS?

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

