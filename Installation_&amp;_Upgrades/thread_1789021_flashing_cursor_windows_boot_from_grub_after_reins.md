---
title: "flashing cursor windows boot from grub after reinstalling ubuntu"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by fifteenrabbits on 2011-06-23
that's my problem. here's my script output. please help. need windows. please help.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 55286352 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdc1 has 
                       1953519615 sectors, but according to the info from 
                       fdisk, it has 1953520001 sectors.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 34. According to the info in the 
                       boot sector, sdd1 has -1364690196 sectors.. But 
                       according to the info from the partition table, it has 
                       2930277100 sectors.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdg1 has 
                       1953519615 sectors, but according to the info from 
                       fdisk, it has 1953520001 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    42,347,339    42,347,277   7 NTFS / exFAT / HPFS
/dev/sda2          42,348,542   312,580,095   270,231,554   5 Extended
/dev/sda5          42,348,544    82,110,463    39,761,920  83 Linux
/dev/sda6         302,815,232   312,580,095     9,764,864  82 Linux swap / Solaris
/dev/sda7          82,112,512   302,807,039   220,694,528  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002  42 SFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 2,930,277,167 2,930,277,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34 2,930,277,134 2,930,277,101 MBR partition scheme

Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1                  63 1,953,520,064 1,953,520,002  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4A90E23890E22A61                       ntfs       
/dev/sda5        207253fc-a787-40ae-9a72-39ab4b2825db   ext4       
/dev/sda6        9eaa6139-01e7-4fc2-ad34-c92557ab0154   swap       
/dev/sda7        8cb96a55-a4fc-4412-aaa3-01f869e9a6f4   ext4       
/dev/sdb1        19DE6C9520AB72A8                       ntfs       3
/dev/sdc1        1E0C0E550C0E287B                       ntfs       1
/dev/sdd1        7F95-5851                              vfat       1BU
/dev/sdg1        0A58041D580409E1                       ntfs       2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=207253fc-a787-40ae-9a72-39ab4b2825db ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=207253fc-a787-40ae-9a72-39ab4b2825db ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=207253fc-a787-40ae-9a72-39ab4b2825db ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=207253fc-a787-40ae-9a72-39ab4b2825db ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 207253fc-a787-40ae-9a72-39ab4b2825db
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4A90E23890E22A61
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=207253fc-a787-40ae-9a72-39ab4b2825db /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=8cb96a55-a4fc-4412-aaa3-01f869e9a6f4 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=9eaa6139-01e7-4fc2-ad34-c92557ab0154 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.371009827 = 26.168172544   boot/grub/core.img                             1
  24.529609680 = 26.338467840   boot/grub/grub.cfg                             1
  24.450782776 = 26.253828096   boot/initrd.img-2.6.32-28-generic              1
  24.472003937 = 26.276614144   boot/initrd.img-2.6.32-32-generic              1
  24.396343231 = 26.195374080   boot/vmlinuz-2.6.32-28-generic                 1
  24.454544067 = 26.257866752   boot/vmlinuz-2.6.32-32-generic                 1
  24.472003937 = 26.276614144   initrd.img                                     1
  24.450782776 = 26.253828096   initrd.img.old                                 1
  24.454544067 = 26.257866752   vmlinuz                                        1
  24.396343231 = 26.195374080   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  56 99 8d be 52 98 97 7e  2d dd c5 52 a4 96 74 6a  |V...R..~-..R..tj|
00000010  33 d2 af 90 35 e9 1c 08  ad b9 41 1e 1d ed 8e ea  |3...5.....A.....|
00000020  89 f0 ed 72 7f 51 14 91  4b c7 52 b6 99 84 a8 e2  |...r.Q..K.R.....|
00000030  67 97 30 22 49 9e ea 16  e4 c7 4f df ed 6f 51 16  |g.0"I.....O..oQ.|
00000040  51 87 a4 93 9c ba c6 e4  7a b8 c7 75 ab 2a 6b 62  |Q.......z..u.*kb|
00000050  2b 90 94 5b 3a 0e 55 18  a0 f1 da 09 f8 5e c9 5a  |+..[:.U......^.Z|
00000060  38 b5 db 7b 11 8d 09 f0  49 ba 45 d9 67 c5 56 98  |8..{....I.E.g.V.|
00000070  b0 23 f3 8e 7b a5 b1 1d  9f 20 a5 14 cd 5a ed 04  |.#..{.... ...Z..|
00000080  fb 55 97 f9 26 2b c8 b8  77 b2 e6 ab 13 ba 55 24  |.U..&+..w.....U$|
00000090  49 6d a4 8c 9a 28 95 77  d6 74 3f 9f ff 97 b1 65  |Im...(.w.t?....e|
000000a0  f3 e8 0e 26 97 de 98 a0  c2 ff 1c fc f6 ff d8 37  |...&...........7|
000000b0  56 5d 8d 10 51 e5 88 f6  60 5e c2 a1 19 27 f1 18  |V]..Q...`^...'..|
000000c0  48 98 ec ac 8a 27 63 0c  f4 90 77 12 69 1e 75 ed  |H....'c...w.i.u.|
000000d0  7e a6 7a aa 64 d3 19 98  2b bf c7 ea 3c cd 52 b9  |~.z.d...+...<.R.|
000000e0  94 a6 c9 db c4 6a b8 7e  9b 4f d2 ca 99 8b 88 bf  |.....j.~.O......|
000000f0  75 76 4c 63 fd 93 3c 35  d8 b8 03 ec ff f8 59 18  |uvLc..<5......Y.|
00000100  e5 a2 bf 6a 16 00 07 00  49 00 7b 09 6f df 2c 3a  |...j....I.{.o.,:|
00000110  b9 66 1f cb 4c bb fb 35  51 75 92 e8 54 eb 76 f2  |.f..L..5Qu..T.v.|
00000120  c5 05 28 17 2f 82 e5 3c  f1 44 36 4d 56 92 cb 61  |..(./..<.D6MV..a|
00000130  3e 49 3a aa 9a 3f 9b dc  28 aa df ef b3 c4 89 3a  |>I:..?..(......:|
00000140  bc d6 42 94 3c 5f 25 5b  70 99 85 d0 df cd db c4  |..B.<_%[p.......|
00000150  6d ef 74 53 c4 ff cb ff  76 c8 eb dd 1f 3d 87 1b  |m.tS....v....=..|
00000160  dc 33 c2 46 a6 d1 ec 48  c6 09 e9 b7 2c aa 21 b1  |.3.F...H....,.!.|
00000170  12 7e 2a 90 53 2b 28 ea  5e 45 d4 be c1 7c 7c e2  |.~*.S+(.^E...||.|
00000180  40 ae 47 0d 76 36 87 54  38 75 1d 29 3f b6 f7 29  |@.G.v6.T8u.)?..)|
00000190  b0 d1 24 4c 61 93 37 1c  ff a3 34 31 a4 7d 4f c8  |..$La.7...41.}O.|
000001a0  7a 4a 72 65 72 38 78 b2  a4 df 7f ae 89 62 87 2e  |zJrer8x......b..|
000001b0  27 da 7d f8 ed ff 16 2c  95 7a 8a d2 df 02 00 fe  |'.}....,.z......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 5e 02 00 fe  |............^...|
000001d0  ff ff 05 fe ff ff 63 50  86 0f 9f 17 95 00 00 00  |......cP........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf 


```

---

### Post by fifteenrabbits on 2011-06-23
I posted this first thing in the morning. I'll provide a little clearer info now:

when I choose xp all I get is a flashing cursor. no hard drive activity indication.

I tried update-grub.

let's get this going!

I am already grateful!

---

### Post by srs5694 on 2011-06-23
I believe your immediate problem is that you've got GRUB installed in /dev/sda1, which seems to be your Windows XP boot partition. I'm not an expert at Windows recovery, which is what this requires, but you could try booting your Windows XP installation disc, or a Windows XP recovery disc, and use it to repair the installation. With any luck that will work and restore the system to bootability.

I do have one additional comment, although I don't believe it's related to your problem: Your /dev/sdd uses a GUID Partition Table (GPT), which is fine in and of itself; however, its single partition seems to be marked with the "MBR partition scheme" type code. AFAIK, *nothing* uses that type code, although there are proposals to use it to enable legacy OSes such as Windows XP to boot from GPT disks. Also, Windows XP can't read GPT disks at all, except with the help of third-party software such as [GPT Mounter.](http://www.mediafour.com/products/gptmounter) Since there's little or no point to having a FAT partition for Linux alone, my guess is that you intended this disk to be a shared-data disk. If I'm right, your best bet is to convert it to MBR form. If the disk doesn't yet have any data on it, the simplest way to do this is to use GParted or parted to create a new MBR partition table (these tools call it an "msdos disklabel") and a new FAT partition. If you've got data on the disk already, you can use GPT fdisk (gdisk) to convert it from GPT to MBR form without losing your data. One further caveat, though: /dev/sdd1 begins on sector 34, which is not properly aligned if the disk uses Advanced Format technology (4 KiB physical sectors with an in-disk translation so it looks like it's got regular 512-byte sectors). If this is the case, I strongly recommend backing up, repartitioning, and restoring; or using GParted to resize the partition so that it begins on 1 MiB boundaries. Post back if you need more advice on this -- but deal with the XP booting issue first.

---

### Post by fifteenrabbits on 2011-06-24
this has become a mess. I'm starting over. is there an "unresolved but unconcerned" tag?

---

### Post by srs5694 on 2011-06-24
> **fifteenrabbits said:**
> this has become a mess. I'm starting over. is there an "unresolved but unconcerned" tag?

Be careful with /dev/sdd! Depending on how you "start over" with it, you could leave traces of GPT data behind, which will confuse GParted and other tools based on libparted. I recommend you either keep it GPT (and therefore not use it with Windows XP) or be sure to use GParted or some other libparted-based program to repartition it. Using fdisk or the Windows partitioner is a definite no-no; there tools will *not* do it in a way that will work well with GParted!

---

