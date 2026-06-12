---
title: "Can't boot after BIOS Update"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by HankB on 2010-10-13
I updated the BIOS on my semi-ancient Abit AV8 and now the system gets stuck on boot. (System has a recent install of 10.04 64 bit Server. It was running an early beta of Maverick due to a screwed up upgrade from the previous LTS, but that should be a different matter.)

The system includes an IDE boot drive and a mix of 5 IDE/SATA drives configured in a RAID. Before the BIOS update the boot drive showed up as /dev/sda. Now it shows up as /dev/sdb.

The grub menu comes up and the boot process starts until 'mountall' tries to fsck /dev/sda1 (root and boot partition) and fails because it is not a file system. The startup process hangs there.

I have booted a live CD to examine the system and collect information.

I do not know where 'mountall' is getting /dev/sda1. I have checked both /boot/grub/grub.cfg and /etc/fstab and do not see sda1 in either. I checked the UUID for the root device and it remains unchanged and matches the entries in fstab and grub.cfg. 

Wait... :confused: This time when I booted a 10.04 live CD, the boot drive did come up as /dev/sda. The previous time I booted the live CD, it came up as /dev/sdb. Of that I am certain. However it still stalls at 'mountall' when I boot. I did fsck the boot partition (as /dev/sdb1 on a previous boot of the live CD and it reported errors that were quickly repaired.)

Here's the output of boot_info_script.sh

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdg1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdg1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders, total 60036480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    57,528,764    57,528,702  83 Linux
/dev/sda2          57,528,826    60,034,904     2,506,079   5 Extended
/dev/sda5          57,528,828    60,034,904     2,506,077  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   390,716,864   390,716,802  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   390,716,864   390,716,802  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   390,716,864   390,716,802  fd Linux raid autodetect


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   390,716,864   390,716,802  fd Linux raid autodetect


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   390,716,864   390,716,802  fd Linux raid autodetect


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             62     7,935,999     7,935,938   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ddf7afba-48c9-4e28-a436-ec9b57e06826   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        96670142-9e5a-4e12-b73f-633e2a7fe181   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a7cc80af-206d-e849-dd30-336a6ea23e69   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a7cc80af-206d-e849-dd30-336a6ea23e69   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        a7cc80af-206d-e849-dd30-336a6ea23e69   linux_raid_member                               
/dev/sdd: PTTYPE="dos" 
/dev/sde1        a7cc80af-206d-e849-dd30-336a6ea23e69   linux_raid_member                               
/dev/sde: PTTYPE="dos" 
/dev/sdf1        a7cc80af-206d-e849-dd30-336a6ea23e69   linux_raid_member                               
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        F44C-1515                              vfat                                     
/dev/sdg: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/F44C-1515         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
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
menuentry 'Ubuntu, with Linux 2.6.32-25-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
	linux	/boot/vmlinuz-2.6.32-25-server root=UUID=ddf7afba-48c9-4e28-a436-ec9b57e06826 ro   quiet
	initrd	/boot/initrd.img-2.6.32-25-server
}
menuentry 'Ubuntu, with Linux 2.6.32-25-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
	echo	'Loading Linux 2.6.32-25-server ...'
	linux	/boot/vmlinuz-2.6.32-25-server root=UUID=ddf7afba-48c9-4e28-a436-ec9b57e06826 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
	linux	/boot/vmlinuz-2.6.32-24-server root=UUID=ddf7afba-48c9-4e28-a436-ec9b57e06826 ro   quiet
	initrd	/boot/initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
	echo	'Loading Linux 2.6.32-24-server ...'
	linux	/boot/vmlinuz-2.6.32-24-server root=UUID=ddf7afba-48c9-4e28-a436-ec9b57e06826 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ddf7afba-48c9-4e28-a436-ec9b57e06826
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ddf7afba-48c9-4e28-a436-ec9b57e06826 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=96670142-9e5a-4e12-b73f-633e2a7fe181 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


## oak
/dev/mapper/uber_volume_group-redwood /export/redwood ext4 rw,auto 0 0
/dev/mapper/uber_volume_group-toonsinator /export/toonsinator reiserfs rw,auto 0 0
/dev/mapper/uber_volume_group-share /export/share reiserfs auto,rw 0 0


=================== sda1: Location of files loaded by Grub: ===================


  10.8GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
  21.2GB: boot/initrd.img-2.6.32-24-server
  21.2GB: boot/initrd.img-2.6.32-25-server
  21.2GB: boot/vmlinuz-2.6.32-24-server
  18.7GB: boot/vmlinuz-2.6.32-25-server
  21.2GB: initrd.img
  21.2GB: initrd.img.old
  18.7GB: vmlinuz
  21.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  86 ec f8 62 5d 79 b9 ba  b2 f1 64 ce e3 8d a3 92  |...b]y....d.....|
00000010  80 4f b9 45 f3 14 06 ef  a6 02 70 0d 06 27 ba 19  |.O.E......p..'..|
00000020  28 ff 7d f2 dc 70 fb 48  09 c0 40 28 f1 37 10 01  |(.}..p.H..@(.7..|
00000030  58 02 8c 01 78 67 02 a0  53 39 0d 9d 25 6c dc bd  |X...xg..S9..%l..|
00000040  8d d8 09 91 ee 98 0c 48  40 60 f3 f1 f8 dc 26 c8  |.......H@`....&.|
00000050  07 40 31 c1 bb 2d 77 48  0c 40 60 90 28 5f df 08  |.@1..-wH.@`.(_..|
00000060  f7 d0 02 a0 20 ee 71 cf  68 00 d4 0a 7c a3 fd ce  |.... .q.h...|...|
00000070  02 a4 21 b9 8d ee 79 97  48 10 33 c0 31 c0 0b 80  |..!...y.H.3.1...|
00000080  30 0d 0d 04 4f c0 d7 0c  26 63 82 7e 5f 01 15 91  |0...O...&c.~_...|
00000090  30 bf fb 5a 00 ec b0 1b  15 fd fa 10 40 c5 00 62  |0..Z........@..b|
000000a0  4b 01 8f 0c 2b ba 08 4e  8c 2d 4c 93 96 7d de 00  |K...+..N.-L..}..|
000000b0  77 c0 2d 2d 26 3a 6e 78  02 72 19 61 a1 a9 e9 ff  |w.--&:nx.r.a....|
000000c0  bf fd c7 3d d1 00 bc a1  f8 de b1 f7 38 14 41 28  |...=........8.A(|
000000d0  ab b0 0a 97 c3 4b fc 5d  dc 58 63 2b 91 3d 50 03  |.....K.].Xc+.=P.|
000000e0  60 18 74 86 e1 c6 4f 89  84 be fb 8e b1 80 2e 00  |`.t...O.........|
000000f0  d0 e7 5c 79 95 97 51 63  00 c0 84 76 17 79 30 02  |..\y..Qc...v.y0.|
00000100  00 cc 18 9e 59 b9 17 a3  00 b8 98 bc f8 e3 af 32  |....Y..........2|
00000110  00 a3 92 89 89 e2 ad 09  a7 5c e0 30 24 de 30 0d  |.........\.0$.0.|
00000120  40 18 96 42 ed bb 08 b6  01 50 06 21 a0 54 af 86  |@..B.....P.!.T..|
00000130  b8 f5 fb 40 03 d2 6b a5  b5 00 04 80 27 40 0e 89  |...@..k.....'@..|
00000140  80 54 94 10 43 ff 23 8f  19 9f a8 76 37 9d 6f f6  |.T..C.#....v7.o.|
00000150  d6 09 2f ed 7a 8a 01 d0  15 01 38 0e dd bf 1b d5  |../.z.....8.....|
00000160  bd e4 40 10 00 3e 28 01  d1 45 16 1b 80 bf 39 cf  |..@..>(..E....9.|
00000170  d7 40 01 10 08 0a 0c dc  06 20 3b 19 b2 0e 73 78  |.@....... ;...sx|
00000180  7d 9c 06 20 0c 4a 2f b1  5c ef 9b 88 ab f3 24 4c  |}.. .J/.\.....$L|
00000190  c0 7f de b0 06 24 d2 c0  2f 00 bc 35 29 dc f6 c2  |.....$../..5)...|
000001a0  35 48 14 01 87 01 00 0e  b9 7b 01 70 d0 2c 50 f1  |5H.......{.p.,P.|
000001b0  7c 2a e6 80 e8 04 c0 1a  00 62 30 87 89 59 00 fe  ||*.......b0..Y..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 5d 3d 26 00 00 00  |..........]=&...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  81 ee a2 0b b4 30 e6 47  fe ba 0a 09 1b 69 66 20  |.....0.G.....if |
00000010  28 67 65 74 5f 55 73 65  53 68 00 00 ce c1 50 14  |(get_UseSh....P.|
00000020  85 03 00 00 1e 00 00 20  ff ff 90 0d 70 12 cd 03  |....... ....p...|
00000030  5b 6c 01 00 dc 1b 49 73  45 72 32 46 73 00 00 00  |[l....IsEr2Fs...|
00000040  fc ff 2c 00 40 02 4b 17  51 6c 00 00 a8 0e 00 00  |..,.@.K.Ql......|
00000050  00 00 00 00 d5 b6 c1 1d  74 35 4c b8 a7 14 4a 72  |........t5L...Jr|
00000060  9f 27 05 37 8f 7e 00 00  00 00 00 00 00 00 00 00  |.'.7.~..........|
00000070  ff ff 2c 00 10 02 01 00  53 6c 00 00 8f 7e 00 00  |..,.....Sl...~..|
00000080  01 00 00 00 00 00 00 10  00 00 08 00 08 02 01 00  |................|
00000090  53 6c 00 00 90 7e 00 00  00 00 00 00 00 00 00 00  |Sl...~..........|
000000a0  ff ff 2c 00 dc 01 01 00  53 6c 00 00 90 7e 00 00  |..,.....Sl...~..|
000000b0  01 00 00 00 00 00 00 10  00 00 04 00 d8 01 01 00  |................|
000000c0  73 74 61 74 65 2d 3e 64  6d 61 62 75 67 3b 0a 09  |state->dmabug;..|
000000d0  e5 9a 09 09 9d e7 6f 70  b0 f7 61 63 84 e9 74 61  |......op..ac..ta|
000000e0  d9 ff 29 3b a4 93 09 09  a6 93 64 6d cf f8 75 66  |..);......dm..uf|
000000f0  82 a4 72 65 ca fe 79 20  92 ba 30 3b a1 93 09 09  |..re..y ..0;....|
00000100  a6 93 64 6d c8 f8 75 66  82 a4 53 47 c6 f1 20 3d  |..dm..uf..SG.. =|
00000110  8f aa 3b 0a a0 93 09 09  a6 f3 66 28 df fb 6c 3e  |..;.......f(..l>|
00000120  9e b3 0a 09 a0 93 09 09  a6 fe 6d 61 cb ef 66 2d  |..........ma..f-|
00000130  91 fc 6d 74 89 e6 3d 20  ec c9 5f 46 e4 ce 5f 53  |..mt..= .._F.._S|
00000140  fb df 52 45 e6 a1 0a 09  a6 93 09 09 cc f6 73 65  |..RE..........se|
00000150  a5 93 09 09 a0 93 09 64  c2 fb 62 75 cf b7 3e 66  |.......d..bu..>f|
00000160  c2 ee 20 26 94 ba 7e 43  fc c5 46 4d fd c5 53 54  |.. &..~C..FM..ST|
00000170  ea c8 45 4f 92 90 09 09  a6 93 09 63 da c5 73 65  |..EO.......c..se|
00000180  db c5 64 69 df f3 73 6f  dd b2 64 6d c8 f8 75 66  |..di..so..dm..uf|
00000190  86 a1 0a 09 a0 93 09 09  c6 fc 20 28 d9 e8 6f 67  |.......... (..og|
000001a0  f0 fe 6d 61 cb ef 66 28  dc ee 61 74 cc b3 29 0a  |..ma..f(..at..).|
000001b0  a6 93 09 09 a0 93 72 65  db ef 72 6e 89 aa 3b 0a  |......re..rn..;.|
000001c0  a6 93 09 09 d4 90 09 09  a6 e7 0a 09 a0 93 69 66  |..............if|
000001d0  8f b2 66 69 c5 ff 2d 3e  af 9a 00 00 0d 1b 00 00  |..fi..->........|
000001e0  ae 9a 00 00 df 9c 00 00  af 9a 00 00 a9 9a 00 00  |................|
000001f0  af 9a 00 00 21 62 d7 41  fc 7e d7 41 fa 7e d7 41  |....!b.A.~.A.~.A|
00000200

Unknown BootLoader  on sdf1

00000000  01 00 06 00 34 01 45 4c  53 3a 0a 09 09 69 66 20  |....4.ELS:...if |
00000010  28 67 65 74 5f 75 73 65  53 6c 00 00 8d 7e 00 00  |(get_useSl...~..|
00000020  01 00 00 00 00 00 00 20  ff ff 90 0d 70 02 01 00  |....... ....p...|
00000030  53 6c 00 00 8e 7e 00 00  00 00 00 00 00 00 00 00  |Sl...~..........|
00000040  ff ff 2c 00 44 02 01 00  53 6c 00 00 8e 7e 00 00  |..,.D...Sl...~..|
00000050  01 00 00 00 00 00 00 10  00 00 08 00 3c 02 01 00  |............<...|
00000060  53 6c 00 00 8f 7e 00 00  00 00 00 00 00 00 00 00  |Sl...~..........|
00000070  ff ff 2c 00 10 02 01 00  53 6c 00 00 8f 7e 00 00  |..,.....Sl...~..|
00000080  01 00 00 00 00 00 00 10  00 00 08 00 08 02 01 00  |................|
00000090  53 6c 00 00 90 7e 00 00  00 00 00 00 00 00 00 00  |Sl...~..........|
000000a0  ff ff 2c 00 dc 01 01 00  53 6c 00 00 90 7e 00 00  |..,.....Sl...~..|
000000b0  01 00 00 00 00 00 00 10  00 00 04 00 d8 01 01 00  |................|
000000c0  73 74 61 74 65 2d 3e 64  6d 61 62 75 66 3b 0a 09  |state->dmabuf;..|
000000d0  09 09 09 09 73 74 6f 70  5f 64 61 63 28 73 74 61  |....stop_dac(sta|
000000e0  74 65 29 3b 0a 09 09 09  09 09 64 6d 61 62 75 66  |te);......dmabuf|
000000f0  2d 3e 72 65 61 64 79 20  3d 20 30 3b 0a 09 09 09  |->ready = 0;....|
00000100  09 09 64 6d 61 62 75 66  2d 3e 53 47 6f 6b 20 3d  |..dmabuf->SGok =|
00000110  20 30 3b 0a 09 09 09 09  09 69 66 28 76 61 6c 3e  | 0;......if(val>|
00000120  31 29 0a 09 09 09 09 09  09 64 6d 61 62 75 66 2d  |1).......dmabuf-|
00000130  3e 66 6d 74 20 7c 3d 20  43 53 5f 46 4d 54 5f 53  |>fmt |= CS_FMT_S|
00000140  54 45 52 45 4f 3b 0a 09  09 09 09 09 65 6c 73 65  |TEREO;......else|
00000150  0a 09 09 09 09 09 09 64  6d 61 62 75 66 2d 3e 66  |.......dmabuf->f|
00000160  6d 74 20 26 3d 20 7e 43  53 5f 46 4d 54 5f 53 54  |mt &= ~CS_FMT_ST|
00000170  45 52 45 4f 3b 0a 09 09  09 09 09 63 73 5f 73 65  |EREO;......cs_se|
00000180  74 5f 64 69 76 69 73 6f  72 28 64 6d 61 62 75 66  |t_divisor(dmabuf|
00000190  29 3b 0a 09 09 09 09 09  69 66 20 28 70 72 6f 67  |);......if (prog|
000001a0  5f 64 6d 61 62 75 66 28  73 74 61 74 65 29 29 0a  |_dmabuf(state)).|
000001b0  09 09 09 09 09 09 72 65  74 75 72 6e 20 30 3b 0a  |......return 0;.|
000001c0  09 09 09 09 7d 0a 09 09  09 7d 0a 09 09 09 69 66  |....}....}....if|
000001d0  20 28 66 69 6c 65 2d 3e  00 00 00 00 a4 81 00 00  | (file->........|
000001e0  01 00 00 00 76 06 00 00  00 00 00 00 00 00 00 00  |....v...........|
000001f0  00 00 00 00 88 f8 d7 41  53 e4 d7 41 53 e4 d7 41  |.......AS..AS..A|
00000200

```

At this point I'm thoroughly confused as to why the system won't boot and would just like to get it working again.

thanks,
hank

Edit: I just booted the live CD again and this time the boot device came up as /dev/sdf. :confused:

---

