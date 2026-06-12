---
title: "Can't install 7 next to Ubuntu 10.04"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by abdominalsnowman on 2011-02-16
Here's my problem, I had only 7 installed a while back (a problem of its own) and completely eliminated it, formating the partition and installing only Ubuntu 10.04.

Eventually, I found that unfortunately some things just work better in Windows so I decided to dual boot.

The partitions were as follows (as they appear in GParted):

[SWAP] [Ubuntu 10.04 (ext4)] [     Storage (NTFS)     ]

There was some free space on the storage partition, so I used GParted to make a new partition for windows, so here it is now:

[SWAP] [Ubuntu 10.04 (ext4)] [  Storage (NTFS)  ] [7 (NTFS)]

But when I try to install 7, it copies the files and expands them, but when it restarts at that point, it boots into Ubuntu. I tried to use the GRUB menu to boot to the 7 installation, but when I try that, it sticks at a blinking cursor.

Any ideas what is wrong? Thanks in advance.

---

### Post by wilee-nilee on 2011-02-16
> **abdominalsnowman said:**
> Here's my problem, I had only 7 installed a while back (a problem of its own) and completely eliminated it, formating the partition and installing only Ubuntu 10.04.

Eventually, I found that unfortunately some things just work better in Windows so I decided to dual boot.

The partitions were as follows (as they appear in GParted):

[SWAP] [Ubuntu 10.04 (ext4)] [     Storage (NTFS)     ]

There was some free space on the storage partition, so I used GParted to make a new partition for windows, so here it is now:

[SWAP] [Ubuntu 10.04 (ext4)] [  Storage (NTFS)  ] [7 (NTFS)]

But when I try to install 7, it copies the files and expands them, but when it restarts at that point, it boots into Ubuntu. I tried to use the GRUB menu to boot to the 7 installation, but when I try that, it sticks at a blinking cursor.

Any ideas what is wrong? Thanks in advance.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a picture of what is where.

---

### Post by abdominalsnowman on 2011-02-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdc4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,046     3,905,535     3,903,490   5 Extended
/dev/sdc5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdc2           3,905,536   163,829,759   159,924,224  83 Linux
/dev/sdc3    *    163,830,870 1,789,680,064 1,625,849,195   7 HPFS/NTFS
/dev/sdc4       1,789,681,664 1,953,521,663   163,840,000   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70566A1B5669E278                       ntfs       SATA 4 (Limbo)                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12BA13F3BA13D1D9                       ntfs       SATA 3 (Files, Audio, Pictures)
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc2        e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d   ext4                                     
/dev/sdc3        C64020EB4020E441                       ntfs       SATA 1 P 2 (Video)            
/dev/sdc4        2208D6EC08D6BE4B                       ntfs                                     
/dev/sdc5        7e56f826-4be8-4e6b-bba5-fe5ff36b0c07   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        9A3C65773C654EF7                       ntfs       SATA 2 (Video (Series))       
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc2        /                        ext4       (rw,errors=remount-ro)
/dev/sdc3        /media/SATA_1_P_2__Video_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/SATA_2__Video__Series__ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/SATA_3__Files,_Audio,_Pictures_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/SATA_4__Limbo_    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='(hd2,2)'
search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1920x1080
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,2)'
search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro   quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro   quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc3)" {
	insmod ntfs
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set c64020eb4020e441
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdd3 :
UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdd2 :
UUID=C64020EB4020E441	/media/SATA_1_P_2__Video_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=9A3C65773C654EF7	/media/SATA_2__Video__Series__	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=12BA13F3BA13D1D9	/media/SATA_3__Files,_Audio,_Pictures_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=70566A1B5669E278	/media/SATA_4__Limbo_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdd5 :
UUID=7e56f826-4be8-4e6b-bba5-fe5ff36b0c07	none	swap	sw	0	0



=================== sdc2: Location of files loaded by Grub: ===================


  45.1GB: boot/grub/core.img
  43.9GB: boot/grub/grub.cfg
  45.2GB: boot/initrd.img-2.6.32-21-generic
   6.3GB: boot/initrd.img-2.6.32-27-generic
  45.1GB: boot/vmlinuz-2.6.32-21-generic
  45.2GB: boot/vmlinuz-2.6.32-27-generic
   6.3GB: initrd.img
  45.2GB: initrd.img.old
  45.2GB: vmlinuz
  45.1GB: vmlinuz.old

================================ sdc3/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  a1 17 00 13 54 b0 00 00  36 0d 00 07 de 00 02 00  |....T...6.......|
00000010  65 10 00 8b 41 b0 00 00  a1 d7 01 03 60 bc 01 00  |e...A.......`...|
00000020  01 11 f0 02 5e 02 00 00  a1 d7 00 84 5e e0 00 00  |....^.......^...|
00000030  a1 f7 00 84 5e e0 00 00  3a 0d 00 07 5e 02 02 00  |....^...:...^...|
00000040  a1 37 d4 84 5e e8 00 00  3a 0d f0 02 de bf 03 00  |.7..^...:.......|
00000050  3a 0d 00 07 5e 02 02 00  3a 0d 00 07 5e 80 02 00  |:...^...:...^...|
00000060  a2 37 00 1b 00 90 00 00  a1 57 f4 12 54 e8 00 00  |.7.......W..T...|
00000070  00 00 f0 02 de 02 00 00  3e 0d 00 bf 00 04 02 00  |........>.......|
00000080  7e 0f f0 02 5e 02 00 00  42 0d f0 02 de bf 03 00  |~...^...B.......|
00000090  45 b1 f0 b6 44 a0 00 00  42 0d 00 bf 80 07 02 00  |E...D...B.......|
000000a0  42 0d 00 17 c5 68 00 00  45 31 00 03 60 bc 01 00  |B....h..E1..`...|
000000b0  00 00 f0 02 de 02 00 00  52 0d 00 bf 00 00 02 00  |........R.......|
000000c0  a8 37 00 a3 5e e0 00 00  52 cd 05 a0 5e 6d 00 00  |.7..^...R...^m..|
000000d0  a1 17 00 5b 24 b0 00 00  bd 00 f0 02 5e 02 00 00  |...[$.......^...|
000000e0  a2 17 00 67 40 b0 00 00  4f ed ff a3 de 68 00 00  |...g@...O....h..|
000000f0  a2 f7 22 89 5e b0 00 00  4e 8d 00 a7 00 6d 00 00  |..".^...N....m..|
00000100  50 4d 00 77 9a 6d 00 00  4f 0d f0 02 de bf 03 00  |PM.w.m..O.......|
00000110  50 0d 00 77 9a 68 00 00  a2 f7 22 89 5e b8 00 00  |P..w.h....".^...|
00000120  c2 00 f0 02 5e 02 00 00  a8 17 00 03 60 bc 01 00  |....^.......`...|
00000130  00 00 f0 02 de 02 00 00  66 0d 00 b3 5e 01 02 00  |........f...^...|
00000140  ac 97 f5 02 60 81 01 00  62 10 1f 0f 60 bc 01 00  |....`...b...`...|
00000150  86 30 02 04 60 90 01 00  8a 10 00 27 54 b0 00 00  |.0..`......'T...|
00000160  80 f0 00 03 61 bc 01 00  a9 20 00 a7 02 e0 00 00  |....a.... ......|
00000170  84 10 00 03 60 bc 01 00  85 10 00 03 60 bc 01 00  |....`.......`...|
00000180  e0 10 00 07 54 b0 00 00  e1 10 00 0b 54 b0 00 00  |....T.......T...|
00000190  e3 90 1a 03 60 bc 01 00  e4 10 00 03 60 bc 01 00  |....`.......`...|
000001a0  92 b7 06 03 60 bc 01 00  c3 f0 1f ff 63 bc 01 00  |....`.......c...|
000001b0  c4 f0 1f ff 63 bc 01 00  84 f0 1f 03 60 bc 00 20  |....c.......`.. |
000001c0  21 00 82 1b 28 f3 02 00  00 00 00 90 3b 00 00 00  |!...(.......;...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```

---

### Post by presence1960 on 2011-02-16
> **abdominalsnowman said:**
> ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   [COLOR="Red"]/boot.ini[/COLOR] [COLOR="Blue"]/bootmgr /Boot/BCD[/COLOR] /grldr [COLOR="Red"]/ntldr 
                       /NTDETECT.COM[/COLOR]

sdc4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,046     3,905,535     3,903,490   5 Extended
/dev/sdc5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdc2           3,905,536   163,829,759   159,924,224  83 Linux
/dev/sdc3    *    163,830,870 1,789,680,064 1,625,849,195   7 HPFS/NTFS
/dev/sdc4       1,789,681,664 1,953,521,663   163,840,000   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70566A1B5669E278                       ntfs       SATA 4 (Limbo)                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12BA13F3BA13D1D9                       ntfs       SATA 3 (Files, Audio, Pictures)
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc2        e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d   ext4                                     
/dev/sdc3        C64020EB4020E441                       ntfs       SATA 1 P 2 (Video)            
/dev/sdc4        2208D6EC08D6BE4B                       ntfs                                     
/dev/sdc5        7e56f826-4be8-4e6b-bba5-fe5ff36b0c07   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        9A3C65773C654EF7                       ntfs       SATA 2 (Video (Series))       
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc2        /                        ext4       (rw,errors=remount-ro)
/dev/sdc3        /media/SATA_1_P_2__Video_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/SATA_2__Video__Series__ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/SATA_3__Files,_Audio,_Pictures_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/SATA_4__Limbo_    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='(hd2,2)'
search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1920x1080
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,2)'
search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro   quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro   quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,2)'
	search --no-floppy --fs-uuid --set e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc3)" {
	insmod ntfs
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set c64020eb4020e441
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdd3 :
UUID=e6f8c7ae-a9da-403d-9f2d-bb599ea6e63d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdd2 :
UUID=C64020EB4020E441	/media/SATA_1_P_2__Video_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=9A3C65773C654EF7	/media/SATA_2__Video__Series__	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=12BA13F3BA13D1D9	/media/SATA_3__Files,_Audio,_Pictures_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=70566A1B5669E278	/media/SATA_4__Limbo_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdd5 :
UUID=7e56f826-4be8-4e6b-bba5-fe5ff36b0c07	none	swap	sw	0	0



=================== sdc2: Location of files loaded by Grub: ===================


  45.1GB: boot/grub/core.img
  43.9GB: boot/grub/grub.cfg
  45.2GB: boot/initrd.img-2.6.32-21-generic
   6.3GB: boot/initrd.img-2.6.32-27-generic
  45.1GB: boot/vmlinuz-2.6.32-21-generic
  45.2GB: boot/vmlinuz-2.6.32-27-generic
   6.3GB: initrd.img
  45.2GB: initrd.img.old
  45.2GB: vmlinuz
  45.1GB: vmlinuz.old

================================ sdc3/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  a1 17 00 13 54 b0 00 00  36 0d 00 07 de 00 02 00  |....T...6.......|
00000010  65 10 00 8b 41 b0 00 00  a1 d7 01 03 60 bc 01 00  |e...A.......`...|
00000020  01 11 f0 02 5e 02 00 00  a1 d7 00 84 5e e0 00 00  |....^.......^...|
00000030  a1 f7 00 84 5e e0 00 00  3a 0d 00 07 5e 02 02 00  |....^...:...^...|
00000040  a1 37 d4 84 5e e8 00 00  3a 0d f0 02 de bf 03 00  |.7..^...:.......|
00000050  3a 0d 00 07 5e 02 02 00  3a 0d 00 07 5e 80 02 00  |:...^...:...^...|
00000060  a2 37 00 1b 00 90 00 00  a1 57 f4 12 54 e8 00 00  |.7.......W..T...|
00000070  00 00 f0 02 de 02 00 00  3e 0d 00 bf 00 04 02 00  |........>.......|
00000080  7e 0f f0 02 5e 02 00 00  42 0d f0 02 de bf 03 00  |~...^...B.......|
00000090  45 b1 f0 b6 44 a0 00 00  42 0d 00 bf 80 07 02 00  |E...D...B.......|
000000a0  42 0d 00 17 c5 68 00 00  45 31 00 03 60 bc 01 00  |B....h..E1..`...|
000000b0  00 00 f0 02 de 02 00 00  52 0d 00 bf 00 00 02 00  |........R.......|
000000c0  a8 37 00 a3 5e e0 00 00  52 cd 05 a0 5e 6d 00 00  |.7..^...R...^m..|
000000d0  a1 17 00 5b 24 b0 00 00  bd 00 f0 02 5e 02 00 00  |...[$.......^...|
000000e0  a2 17 00 67 40 b0 00 00  4f ed ff a3 de 68 00 00  |...g@...O....h..|
000000f0  a2 f7 22 89 5e b0 00 00  4e 8d 00 a7 00 6d 00 00  |..".^...N....m..|
00000100  50 4d 00 77 9a 6d 00 00  4f 0d f0 02 de bf 03 00  |PM.w.m..O.......|
00000110  50 0d 00 77 9a 68 00 00  a2 f7 22 89 5e b8 00 00  |P..w.h....".^...|
00000120  c2 00 f0 02 5e 02 00 00  a8 17 00 03 60 bc 01 00  |....^.......`...|
00000130  00 00 f0 02 de 02 00 00  66 0d 00 b3 5e 01 02 00  |........f...^...|
00000140  ac 97 f5 02 60 81 01 00  62 10 1f 0f 60 bc 01 00  |....`...b...`...|
00000150  86 30 02 04 60 90 01 00  8a 10 00 27 54 b0 00 00  |.0..`......'T...|
00000160  80 f0 00 03 61 bc 01 00  a9 20 00 a7 02 e0 00 00  |....a.... ......|
00000170  84 10 00 03 60 bc 01 00  85 10 00 03 60 bc 01 00  |....`.......`...|
00000180  e0 10 00 07 54 b0 00 00  e1 10 00 0b 54 b0 00 00  |....T.......T...|
00000190  e3 90 1a 03 60 bc 01 00  e4 10 00 03 60 bc 01 00  |....`.......`...|
000001a0  92 b7 06 03 60 bc 01 00  c3 f0 1f ff 63 bc 01 00  |....`.......c...|
000001b0  c4 f0 1f ff 63 bc 01 00  84 f0 1f 03 60 bc 00 20  |....c.......`.. |
000001c0  21 00 82 1b 28 f3 02 00  00 00 00 90 3b 00 00 00  |!...(.......;...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```

You have your windows 7 boot files combined with a former windows XP install that was on sdc3 (see sdc above in the quoted text- red is XP boot files and blue belongs to 7). Your win 7 OS is installed on sdc4.

This is way more complicated than you led on in your original post. I would suggest cleaning up sdc3 & sdc4 by backing up anything you don't want to lose. Then use Gparted to delete both sdc3 and sdc4 and make a new NTFS partition for windows 7.

Once that is done reinstall win 7 by booting to BIOS and making the 1 TB disk (sdc) first in the hard disk boot order. Save changes to CMOS and boot the windows DVD and install to that newly created NTFS partition. When completed reboot and make sure windows boots OK.

Next boot the Ubuntu Live CD/USB to reinstall GRUB2. Choose "try Ubuntu". When the desktop loads open a terminal and run ```
sudo mount /dev/sdc2 /mnt
```

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```When completed reboot and choose ubuntu from the GRUB menu. Open a terminal and run ```
sudo dpkg-reconfigure grub-pc
``` Choose OK for each window until you get to the window to choose where to put GRUB. Unselect sda & sdb if selected. Make sure sdc is selected. proceed. This will insure when GRUB gets updated it goes to MBR of sdc, so your booting does not get fouled up. You should now be good to go.

---

### Post by abdominalsnowman on 2011-02-16
wow, I don't even remember having XP installed on this computer... I've gone through so many OS installs I can see how things got so cluttered. Sounds like a lot of work for tomorrow. Thanks for the help!

---

### Post by presence1960 on 2011-02-16
> **abdominalsnowman said:**
> wow, I don't even remember having XP installed on this computer... I've gone through so many OS installs I can see how things got so cluttered. Sounds like a lot of work for tomorrow. Thanks for the help!

Actually not too much work! Installing windows is the bulk of it. Deleting the sdc3 & sdc4 partitions with gparted and reinstalling GRUB2 will take about 5 minutes combined. Depending on how much data you need to back up that can add some time to it.

---

### Post by abdominalsnowman on 2011-02-17
yea, I have almost 500GB of data to back up, so that will take a while, but at least it doesn't require constant attention. Just to clarify, why does the script label the drive sdc while GParted labels it sda? Am I getting the drives mixed up?

---

### Post by abdominalsnowman on 2011-02-18
well 7 installed and runs fine, grub installed fine, but I can't run dpkg-reconfigure because ubuntu doesn't start up. It just hangs on the plymouth screen. I tried the recovery options, but they don't load either. Any ideas?

---

### Post by wilee-nilee on 2011-02-18
Could be a graphic driver is needed. At the grub menu choose the Ubuntu kernel with the arrow key and hit e for edit. use the arrow key to navigate to the quiet splash and replace it with nomodeset, hit ctrl+x to boot.

This is a per session fix.

---

