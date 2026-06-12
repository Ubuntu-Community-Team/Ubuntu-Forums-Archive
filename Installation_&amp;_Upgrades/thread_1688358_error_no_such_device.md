---
title: "error: no such device:"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by squid636 on 2011-02-15
I see that a lot of people have had this error but I seem to need some one on one help to fix this. I have two hard drives internal to my laptop and one external.  Right now I am on a usb stick running ubuntu.

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e306e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004c3b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9328    74920960   83  Linux
/dev/sdb2            9328        9730     3227649    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdc: 4000 MB, 4000317440 bytes
124 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002c68f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1016     3905473    b  W95 FAT32

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf72a0e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001    7  HPFS/NTFS
```

When I try to boot up my computer it give me the following error:
```
error: no such device; this uuid is NOT sdb1
grub rescue:
```

Below are the result of the boot_info_script

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4000 MB, 4000317440 bytes
124 heads, 62 sectors/track, 1016 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     7,811,007     7,810,946   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        203C1E043C1DD59E                       ntfs       Windows 7                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f844824b-23a1-42fe-bc0a-d577329c24f2   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5523c02d-5082-41f6-b694-9189b7c72f83   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6231-415C                              vfat       MYLINUXLIVE                   
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        4A841A75841A63AB                       ntfs       FantomHD                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/FantomHD          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/f844824b-23a1-42fe-bc0a-d577329c24f2 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set f844824b-23a1-42fe-bc0a-d577329c24f2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set f844824b-23a1-42fe-bc0a-d577329c24f2
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set f844824b-23a1-42fe-bc0a-d577329c24f2
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=f844824b-23a1-42fe-bc0a-d577329c24f2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set f844824b-23a1-42fe-bc0a-d577329c24f2
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=f844824b-23a1-42fe-bc0a-d577329c24f2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set f844824b-23a1-42fe-bc0a-d577329c24f2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set f844824b-23a1-42fe-bc0a-d577329c24f2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 203c1e043c1dd59e
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
UUID=f844824b-23a1-42fe-bc0a-d577329c24f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5523c02d-5082-41f6-b694-9189b7c72f83 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  34.4GB: boot/grub/core.img
  15.2GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-23-generic
  34.5GB: boot/vmlinuz-2.6.35-23-generic
    .9GB: initrd.img
  34.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  55 c7 ca 20 71 7a 56 92  ba 24 e5 13 73 6b 5f 8a  |U.. qzV..$..sk_.|
00000010  e5 af 61 79 74 9e 63 56  19 2b 57 13 c1 a6 10 e5  |..ayt.cV.+W.....|
00000020  55 2d 48 b3 4f 0f 12 ba  95 d5 6d 3b f8 99 7d ee  |U-H.O.....m;..}.|
00000030  ee dc ff fb b0 00 88 80  04 e4 66 55 01 e9 4b 72  |..........fU..Kr|
00000040  96 6c ca a0 3d ec 6e 12  bd 97 54 0c 25 2d ca 19  |.l..=.n...T.%-..|
00000050  aa 2a 81 83 25 79 a4 bb  e5 e6 e4 e6 5c fb 6e 2d  |.*..%y......\.n-|
00000060  de db 6f e4 7b 2d ec 52  f6 d6 b3 6f c9 99 99 de  |..o.{-.R...o....|
00000070  ac d2 67 77 ad 1c fc ba  40 a1 91 33 c6 f6 67 3b  |..gw....@..3..g;|
00000080  f6 6a 61 87 3f 3c b3 2b  3d 5c 3c f6 b3 7e 7f e1  |.ja.?<.+=\<..~..|
00000090  f5 69 27 e5 75 73 55 0d  ae 76 e0 e6 27 b8 64 a0  |.i'.usU..v..'.d.|
000000a0  47 02 d1 3f 31 b2 25 97  55 92 38 52 e4 68 90 09  |G..?1.%.U.8R.h..|
000000b0  96 44 e6 58 13 2e c1 9a  4b 63 ba 54 72 77 83 88  |.D.X....Kc.Trw..|
000000c0  88 99 11 c1 44 68 a4 50  9a c9 24 1a 0a 17 50 75  |....Dh.P..$...Pu|
000000d0  40 39 92 69 28 4e 45 0b  18 15 8d 2c 4b 24 28 44  |@9.i(NE....,K$(D|
000000e0  2a 9f 50 95 93 d5 11 c6  9f f1 71 5d e6 55 49 b1  |*.P.......q].UI.|
000000f0  09 ed 7a 20 3d 9a 8c 50  33 32 18 a1 5b 6e d9 49  |..z =..P32..[n.I|
00000100  93 92 46 99 b4 1f 2b 53  f1 48 ef 9f 22 50 81 82  |..F...+S.H.."P..|
00000110  a2 67 8d 06 67 3b f6 6a  61 87 2d f5 b3 fe df fa  |.g..g;.ja.-.....|
00000120  e2 1d 7f 3f fd 92 1b b3  74 ee 7c 58 29 c2 01 c3  |...?....t.|X)...|
00000130  00 8a 41 63 7c 9e 42 a0  4c 50 d8 91 73 7a b9 0a  |..Ac|.B.LP..sz..|
00000140  ed 46 c0 84 ba 1e 44 6c  99 64 63 c8 cf 21 27 1a  |.F....Dl.dc..!'.|
00000150  42 21 2b 3c 12 b2 8d e1  15 62 85 1e 12 72 36 8f  |B!+<.....b...r6.|
00000160  13 a2 66 1a f1 07 92 ec  4a 6a b0 46 a6 ab 56 4c  |..f.....Jj.F..VL|
00000170  8d 14 15 9d b0 81 e9 41  78 36 31 1a 9d 4e cb 9a  |.......Ax61..N..|
00000180  4e f2 3d 56 bf fa c6 33  88 62 fb 5f 42 1d b5 a1  |N.=V...3.b._B...|
00000190  d1 65 6d ea 80 0c 64 24  f9 1c 66 5a bc eb 7e af  |.em...d$..fZ..~.|
000001a0  4e 52 24 58 6c e2 b0 b8  ac 30 49 08 1d 46 5c 9c  |NR$Xl....0I..F\.|
000001b0  9c 40 c3 17 73 d5 d1 82  03 82 8c 8d a3 15 00 fe  |.@..s...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 88 04  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  82 2f 77 00 bc 1d 00 00  00 00 00 00 02 00 00 00  |./w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5c 41 31 62 4e  4f 20 4e 41 4d 45 20 20  |..)\A1bNO NAME  |
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
00000100  7d 00 66 b8 10 41 48 00  66 ba 00 00 00 00 bb 00  |}.f..AH.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
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
```

I have tried to reinstall grub using the commands below:

```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Any advice on what I am missing? Thanks in advance.

---

### Post by sikander3786 on 2011-02-15
First of all make sure your Bios is properly set to boot from second HDD i.e, sdb and not sda.

I hope it is already set to boot from sdb but re-check. If that doesn't solve the issue, try purging and re-installing Grub2 completely from chroot.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
courtesy of forum member *drs305*

---

### Post by squid636 on 2011-02-15
> **sikander3786 said:**
> First of all make sure your Bios is properly set to boot from second HDD i.e, sdb and not sda.

I hope it is already set to boot from sdb but re-check. If that doesn't solve the issue, try purging and re-installing Grub2 completely from chroot.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
courtesy of forum member *drs305*

I haven't changed anything in my bios.  Before it booted up grub and I could select either windows 7 or ubuntu.  I will try to change it and then fix the windows 7 booting.

---

### Post by sikander3786 on 2011-02-15
Probably it is better to leave your Windows bootloader on your Windows HDD and install Grub2 to the MBR of your Ubuntu HDD. That way, if there are any issues with Grub, you'll still be able to boot Windows with just switching drives in your boot.

Let us know if you need any help restoring your Windows bootloader.

---

### Post by squid636 on 2011-02-15
Ok I got windows to boot up by doing what you said.  Thank you for that.  Looks like I need to tweak the version of Ubuntu that I just installed.  It wouldn't boot at all but I think that is a different issue all together. I could see it in the grub menu but it hung during the boot process.

---

### Post by sikander3786 on 2011-02-15
> **squid636 said:**
> Ok I got windows to boot up by doing what you said.  Thank you for that.  Looks like I need to tweak the version of Ubuntu that I just installed.  It wouldn't boot at all but I think that is a different issue all together. I could see it in the grub menu but it hung during the boot process.
In case of a re-install you might once again get the same problems and might need to put in some boot parameters. For an overlook on general Ubuntu boot + installation problems, see here.

[http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html](http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html)

And you need to select the proper boot device for installation of Grub so you Windows loader doesn't get replaced once again. See the Grub loader section here. Instructions are for 10.10 and 11.04.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

If you decide to install 10.04, the option to install Grub loader will appear just before installtion starts. Click the 'Advanced' button and choose appropriate device.

Good Luck!

---

