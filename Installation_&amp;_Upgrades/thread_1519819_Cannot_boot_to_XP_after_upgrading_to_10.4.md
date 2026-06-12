---
title: "Cannot boot to XP after upgrading to 10.4"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by RGBrasel on 2010-06-28
I have a dual boot (2 hard drive) system, and upgraded to 10.4.  Booting into XP results in a flashing cursor that doesn't do anything.  I know that GRUB screwed everything up, but I need to know what to do--and assume I don't know what I'm doing--to restore my dual boot ability.  

Here's what I get after running a boot info script:

> Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 29794255 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 100940607 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 215519775 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

/dev/sda1                  63    10,506,509    10,506,447  12 Compaq diagnostics
/dev/sda2    *     10,506,510    39,809,069    29,302,560   7 HPFS/NTFS
/dev/sda3          39,809,070   234,436,544   194,627,475   f W95 Ext d (LBA)
/dev/sda5          39,809,133   234,436,544   194,627,412   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   970,807,295   970,805,248  83 Linux
/dev/sdb2         970,809,342   976,773,119     5,963,778   5 Extended
/dev/sdb5         970,809,344   976,773,119     5,963,776  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,064   976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8AFCF940FCF9275B                       ntfs                                     
/dev/sda2        8A00464800463C07                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6030699C30697A44                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        634912d7-2dbb-4734-8f49-3810717a4e5c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9233a346-274d-4994-93e1-d1029bee9279   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6853-5BA9                              vfat       LACIE                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/8A00464800463C07  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/LACIE             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=634912d7-2dbb-4734-8f49-3810717a4e5c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=634912d7-2dbb-4734-8f49-3810717a4e5c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=634912d7-2dbb-4734-8f49-3810717a4e5c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=634912d7-2dbb-4734-8f49-3810717a4e5c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 634912d7-2dbb-4734-8f49-3810717a4e5c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8afcf940fcf9275b
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8a00464800463c07
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=634912d7-2dbb-4734-8f49-3810717a4e5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9233a346-274d-4994-93e1-d1029bee9279 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 197.7GB: boot/grub/core.img
  43.3GB: boot/grub/grub.cfg
 197.7GB: boot/initrd.img-2.6.32-21-generic
 197.7GB: boot/initrd.img-2.6.32-22-generic
 197.7GB: boot/vmlinuz-2.6.32-21-generic
 197.7GB: boot/vmlinuz-2.6.32-22-generic
 197.7GB: initrd.img
 197.7GB: initrd.img.old
 197.7GB: vmlinuz
 197.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  55 89 e5 0f 1f 44 00 00  ba c0 22 15 c0 b8 8c 97  |U....D....".....|
00000010  6b c0 e8 a9 55 05 00 5d  c3 8d b4 26 00 00 00 00  |k...U..]...&....|
00000020  55 89 e5 0f 1f 44 00 00  ba 10 29 15 c0 b8 8c 97  |U....D....).....|
00000030  6b c0 e8 89 55 05 00 5d  c3 8d b4 26 00 00 00 00  |k...U..]...&....|
00000040  55 89 e5 0f 1f 44 00 00  ba 80 23 15 c0 b8 9d 97  |U....D....#.....|
00000050  6b c0 e8 69 55 05 00 5d  c3 8d b4 26 00 00 00 00  |k..iU..]...&....|
00000060  55 89 e5 0f 1f 44 00 00  ba b0 29 15 c0 b8 9d 97  |U....D....).....|
00000070  6b c0 e8 49 55 05 00 5d  c3 8d b4 26 00 00 00 00  |k..IU..]...&....|
00000080  55 89 e5 0f 1f 44 00 00  ba 40 24 15 c0 b8 ab 97  |U....D...@$.....|
00000090  6b c0 e8 29 55 05 00 5d  c3 8d b4 26 00 00 00 00  |k..)U..]...&....|
000000a0  55 89 e5 0f 1f 44 00 00  ba 50 2a 15 c0 b8 ab 97  |U....D...P*.....|
000000b0  6b c0 e8 09 55 05 00 5d  c3 8d b4 26 00 00 00 00  |k...U..]...&....|
000000c0  55 89 e5 83 ec 20 89 5d  f4 89 75 f8 89 7d fc 0f  |U.... .]..u..}..|
000000d0  1f 44 00 00 89 e3 89 c7  81 e3 00 e0 ff ff 89 4d  |.D.............M|
000000e0  f0 8b 4b 14 9c 58 8d 74  26 00 89 c6 fa 90 8d 74  |..K..X.t&......t|
000000f0  26 00 64 a1 40 0a 84 c0  f6 43 17 04 74 7a 8b 1d  |&.d.@....C..tz..|
00000100  2c e8 8b c0 85 db 74 58  03 1c 85 c0 fe 79 c0 89  |,.....tX.....y..|
00000110  f2 89 d8 c7 43 0c 00 00  00 00 c7 43 10 00 00 00  |....C......C....|
00000120  00 e8 8a be 05 00 a1 e4  d2 79 c0 31 d2 89 7b 0c  |.........y.1..{.|
00000130  31 c9 66 89 03 8b 45 f0  89 43 10 a1 e4 d2 79 c0  |1.f...E..C....y.|
00000140  c7 44 24 0c 14 00 00 00  89 5c 24 08 c7 04 24 01  |.D$......\$...$.|
00000150  00 00 00 c7 44 24 04 00  00 00 00 e8 e0 50 07 00  |....D$.......P..|
00000160  89 f0 50 9d 8d 74 26 00  8b 5d f4 8b 75 f8 8b 7d  |..P..t&..]..u..}|
00000170  fc 89 ec 5d c3 8d 76 00  8b 1d 28 e8 8b c0 eb 84  |...]..v...(.....|
00000180  55 89 e5 83 ec 20 89 5d  f4 89 75 f8 89 7d fc 0f  |U.... .]..u..}..|
00000190  1f 44 00 00 89 e3 89 c7  81 e3 00 e0 ff ff 89 55  |.D.............U|
000001a0  f0 8b 4b 14 9c 58 8d 74  26 00 89 c6 fa 90 8d 74  |..K..X.t&......t|
000001b0  26 00 64 a1 40 0a 84 c0  f6 43 17 04 74 7a 00 fe  |&.d.@....C..tz..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by darkod on 2010-06-28
sda2: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of sda2[/COLOR]  and 
                       looks at sector 100940607 of the same hard drive  for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

You installed grub2 onto your XP partition. Use this procedure to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to repair partition #2 on disk /dev/sda.

---

### Post by RGBrasel on 2010-06-28
I owe you an IPA.  I followed the instructions, and it repaired my boot sectors perfectly.  Many thanks!  This thread should be elevated to gospel.

---

