---
title: "Dual boot, windows 7 sometimes fails loading"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by thesuker on 2011-03-31
Just installed windows 7 + ubuntu, first windows, updated it, and then ubuntu + updates.  now when i select windows on grub, it starts loading and sometimes, for no reason at all, just restarts... and others it loads just fine.  any ideas why?

---

### Post by Rubi1200 on 2011-03-31
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by thesuker on 2011-03-31
Copy&Paste results.txt


 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/grub.
 => Windows is installed in the MBR of /dev/sdc

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda4: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   368,642,047   368,435,200   7 HPFS/NTFS
/dev/sda3         368,642,048   369,618,943       976,896  83 Linux
/dev/sda4         369,620,990   488,396,799   118,775,810   5 Extended
/dev/sda5         369,620,992   379,383,807     9,762,816  82 Linux swap / Solaris
/dev/sda6         379,385,856   398,915,583    19,529,728  83 Linux
/dev/sda7         398,917,632   488,396,799    89,479,168  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8005 MB, 8005787648 bytes
32 heads, 63 sectors/track, 7756 cylinders, total 15636304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    15,636,095    15,636,033   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B6F43AF5F43AB807                       ntfs       System Reserved               
/dev/sda2        94FC4517FC44F4D0                       ntfs                                     
/dev/sda3        968a06d0-2b5f-4591-abb1-b190c1c2d7ba   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        053050ef-603d-422b-ad2e-2f524c0ef1d8   swap                                     
/dev/sda6        d30091a3-1380-43d1-9ff7-d412ce4ba1c7   ext4                                     
/dev/sda7        cc93881c-2508-4f35-8bb1-f4e1d169fccb   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        7873-B926                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/7873-B926         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sda3/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set d30091a3-1380-43d1-9ff7-d412ce4ba1c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 968a06d0-2b5f-4591-abb1-b190c1c2d7ba
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 968a06d0-2b5f-4591-abb1-b190c1c2d7ba
	linux	/vmlinuz-2.6.35-28-generic root=UUID=d30091a3-1380-43d1-9ff7-d412ce4ba1c7 ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 968a06d0-2b5f-4591-abb1-b190c1c2d7ba
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=d30091a3-1380-43d1-9ff7-d412ce4ba1c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 968a06d0-2b5f-4591-abb1-b190c1c2d7ba
	linux	/vmlinuz-2.6.35-22-generic root=UUID=d30091a3-1380-43d1-9ff7-d412ce4ba1c7 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 968a06d0-2b5f-4591-abb1-b190c1c2d7ba
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=d30091a3-1380-43d1-9ff7-d412ce4ba1c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 968a06d0-2b5f-4591-abb1-b190c1c2d7ba
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 968a06d0-2b5f-4591-abb1-b190c1c2d7ba
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b6f43af5f43ab807
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

=================== sda3: Location of files loaded by Grub: ===================


 189.0GB: grub/core.img
 189.0GB: grub/grub.cfg
 188.8GB: initrd.img-2.6.35-22-generic
 188.8GB: initrd.img-2.6.35-28-generic
 188.7GB: vmlinuz-2.6.35-22-generic
 188.7GB: vmlinuz-2.6.35-28-generic

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
UUID=d30091a3-1380-43d1-9ff7-d412ce4ba1c7 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=968a06d0-2b5f-4591-abb1-b190c1c2d7ba /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=cc93881c-2508-4f35-8bb1-f4e1d169fccb /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=053050ef-603d-422b-ad2e-2f524c0ef1d8 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  55 79 97 c2 5e fb db 7b  b0 bb c3 11 f0 31 b2 aa  |Uy..^..{.....1..|
00000010  27 0b ed 1e ee 2b cf 62  8d 6b f1 78 f9 cb 68 d3  |'....+.b.k.x..h.|
00000020  c5 d6 97 7a 09 5f be 57  54 7a 97 fe 97 a9 b2 d8  |...z._.WTz......|
00000030  dd f7 fd 2b ac f5 d9 b9  76 6c 62 f0 54 0d 00 80  |...+....vlb.T...|
00000040  4a 5f 4f 64 3c b4 bf 32  0e 0e 58 7e 6c 25 1e 00  |J_Od<..2..X~l%..|
00000050  e1 2b 6d 84 dd e9 ca 7c  3e 16 b5 e2 62 f5 2d ca  |.+m....|>...b.-.|
00000060  3b 49 3a ef d7 0e 9c 1f  06 3f a7 39 7b 0c da a9  |;I:......?.9{...|
00000070  6f 9d 99 f9 af 1f 04 36  77 33 e4 99 ff f9 bb 2c  |o......6w3.....,|
00000080  62 d6 08 ec 2f d4 d4 b4  57 69 7d ee b4 c3 e8 ae  |b.../...Wi}.....|
00000090  95 e8 9c 15 01 13 d4 c0  3e 0c 34 b3 b7 67 ed b3  |........>.4..g..|
000000a0  cd 77 d3 3a d6 f7 50 c2  65 6b 62 8a d4 d5 2a 23  |.w.:..P.ekb...*#|
000000b0  6c c5 79 35 83 d0 7d b6  73 d6 df 8e e5 92 c5 73  |l.y5..}.s......s|
000000c0  57 f7 b6 a6 30 25 81 ef  ee 02 82 ff f6 35 42 10  |W...0%.......5B.|
000000d0  96 a5 16 ab b4 64 1f 00  af f2 8f 3d ef 5a 3f cb  |.....d.....=.Z?.|
000000e0  2c 85 c3 f5 4a bf 11 01  c9 9e 5e e5 4a fb 77 ea  |,...J.....^.J.w.|
000000f0  2f c7 9f fa ab c5 52 7f  d2 20 be d4 11 d2 fc b9  |/.....R.. ......|
00000100  54 05 0f ff e1 21 53 56  52 e0 86 08 11 55 03 1f  |T....!SVR....U..|
00000110  54 5e 3d 49 69 ab db 37  d6 0f 2c db 65 53 32 ad  |T^=Ii..7..,.eS2.|
00000120  f9 41 8f 07 c3 ff 31 7f  68 29 be 3d 9e 8b c9 6d  |.A....1.h).=...m|
00000130  d8 43 f8 07 ad a3 a1 2b  56 06 51 7f 52 df fe e0  |.C.....+V.Q.R...|
00000140  fb 48 6b 3d 93 f9 98 de  c4 9d b2 4a 46 5f fd 1d  |.Hk=.......JF_..|
00000150  6d bd c9 b6 c1 e4 96 f2  52 a3 e3 e0 66 8e a4 43  |m.......R...f..C|
00000160  96 62 3f 14 b9 4e db bb  65 bd b6 63 48 b9 f8 b5  |.b?..N..e..cH...|
00000170  c7 5f 2b f5 ef 8b c2 11  7e 08 a2 50 36 aa 57 89  |._+.....~..P6.W.|
00000180  55 d5 0f 52 22 ee ee 46  32 de f1 22 53 23 e0 88  |U..R"..F2.."S#..|
00000190  39 cb 26 cc 88 94 f2 d5  fc 7d 45 bf 57 c9 15 f2  |9.&......}E.W...|
000001a0  ec fa af 5f cb 8a 07 7e  57 ff 7b 9a df 5d ef ab  |..._...~W.{..]..|
000001b0  55 15 2b b6 fa df 22 88  d5 36 8d c2 40 90 00 fe  |U.+..."..6..@...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 94 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f8  94 00 00 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by thesuker on 2011-03-31
it restarts while on the windows logo screen (loading)...  it takes two or three restarts to load correctly.

ubuntu seems to work fine

---

### Post by oldfred on 2011-03-31
It is some sort of windows issue as once grub has passed the boot to windows, grub is not involved.

Often after an install, windows will want to run chkdsk.

I would try chkdsk first to see if that resolves the issue.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)


If you do not have a windows repair CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

