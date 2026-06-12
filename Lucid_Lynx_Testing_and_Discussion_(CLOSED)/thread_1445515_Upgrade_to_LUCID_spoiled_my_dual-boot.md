---
title: "Upgrade to LUCID spoiled my dual-boot"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alex69 on 2010-04-02
Hi, since I upgrade to Lucid from karmic my dual-boot PC works only in one way, only Ubuntu starts and my Vista OS (used for computer gaming) won't run.
The Vista OS is now called "Windows Recovery Environment" and when chosed the cursor start blinding forever...

If anyone could help me, I append the results.txt from the BOOT INFO SCRIPT [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 17025 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 17025 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 17025 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 17025 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.1 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  12 Compaq diagnostics
/dev/sda2    *     20,466,810   254,710,574   234,243,765   6 FAT16
/dev/sda3         254,710,575   488,392,064   233,681,490   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 250.1 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       208,844       208,782  83 Linux
/dev/sdb2             208,845     6,072,569     5,863,725  82 Linux swap / Solaris
/dev/sdb3           6,074,368    86,042,623    79,968,256  83 Linux
/dev/sdb4          86,044,202   488,392,064   402,347,863   5 Extended
/dev/sdb5          86,044,203   488,392,064   402,347,862  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B044CC1716D9B5D2                       ntfs       PQSERVICE                     
/dev/sda2        B870C80C70C7CF76                       ntfs       ACER                          
/dev/sda3        52B00974B0096039                       ntfs       Margherita                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ec6f1416-84e6-4e10-9faf-8939cff2fc4e   ext4                                     
/dev/sdb2        c1b868e7-2267-4c30-aeed-d44d722c7ef5   swap                                     
/dev/sdb3        795ff9dd-1494-4cc1-b513-f3bae3c8b0b7   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        9ca15faa-4d3f-4dac-a5a6-35e9b405e5a1   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext4       (rw)
/dev/sdb1        /boot                    ext4       (rw)


============================= sdb1/grub/grub.cfg: =============================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 795ff9dd-1494-4cc1-b513-f3bae3c8b0b7
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
search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
set locale_dir=($root)/grub/locale
set lang=it
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
menuentry "Ubuntu, con Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	linux	/vmlinuz-2.6.32-19-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro   quiet splash
	initrd	/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, con Linux 2.6.32-19-generic (modalità ripristino)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/vmlinuz-2.6.32-19-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, con Linux 2.6.32-18-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	linux	/vmlinuz-2.6.32-18-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro   quiet splash
	initrd	/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, con Linux 2.6.32-18-generic (modalità ripristino)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	echo	Loading Linux 2.6.32-18-generic ...
	linux	/vmlinuz-2.6.32-18-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, con Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	linux	/vmlinuz-2.6.32-17-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro   quiet splash
	initrd	/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, con Linux 2.6.32-17-generic (modalità ripristino)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	echo	Loading Linux 2.6.32-17-generic ...
	linux	/vmlinuz-2.6.32-17-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, con Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	linux	/vmlinuz-2.6.32-16-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro   quiet splash
	initrd	/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, con Linux 2.6.32-16-generic (modalità ripristino)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/vmlinuz-2.6.32-16-generic root=UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ec6f1416-84e6-4e10-9faf-8939cff2fc4e
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b044cc1716d9b5d2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set b870c80c70c7cf76
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-16-generic
    .0GB: initrd.img-2.6.32-17-generic
    .0GB: initrd.img-2.6.32-18-generic
    .0GB: initrd.img-2.6.32-19-generic
    .0GB: vmlinuz-2.6.32-16-generic
    .0GB: vmlinuz-2.6.32-17-generic
    .0GB: vmlinuz-2.6.32-18-generic
    .0GB: vmlinuz-2.6.32-19-generic

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=795ff9dd-1494-4cc1-b513-f3bae3c8b0b7 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=ec6f1416-84e6-4e10-9faf-8939cff2fc4e /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=9ca15faa-4d3f-4dac-a5a6-35e9b405e5a1 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=c1b868e7-2267-4c30-aeed-d44d722c7ef5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


   3.1GB: initrd.img
   3.1GB: initrd.img.old
   3.1GB: vmlinuz
   3.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  3e 79 bf 2d 12 cc b1 46  91 bc 84 43 7e 43 49 1b  |>y.-...F...C~CI.|
00000010  fc c0 36 7c 2f 6b 5f ad  1b 67 6e e2 e3 c7 b7 76  |..6|/k_..gn....v|
00000020  ba 7f d4 bb 6c 0f 1d b1  ae 4e 76 da d9 4f 09 58  |....l....Nv..O.X|
00000030  8c 6a 20 46 81 56 34 40  ac a9 c2 f3 e2 37 2e e2  |.j F.V4@.....7..|
00000040  cb 58 e3 cc dd b3 b2 33  f2 23 80 32 c4 b2 e5 4a  |.X.....3.#.2...J|
00000050  d2 b0 40 cc c4 28 2d c2  ac c6 9e 7a ef a9 d8 f1  |..@..(-....z....|
00000060  5d f2 05 ff 00 eb bb 57  f9 f5 dc 9f a9 38 1f 93  |]......W.....8..|
00000070  c1 de 30 ee 69 83 81 ba  f7 1d a9 81 87 14 71 c2  |..0.i.........q.|
00000080  1c ac ca a2 58 9a 55 cb  92 36 b5 e9 21 e9 2d 3d  |....X.U..6..!.-=|
00000090  ab bf 48 7b 97 03 2b 66  ce ef 2c 8d cf 06 3e e7  |..H{..+f..,...>.|
000000a0  cb d8 f2 16 78 a4 9f 1b  23 08 44 48 57 63 40 4c  |....x...#.DHWc@L|
000000b0  8b 13 c8 3a 8d 1a aa 31  22 35 0a 9f a5 71 60 6d  |...:...1"5...q`m|
000000c0  b1 6c d9 7d c1 db 93 65  65 a4 32 2e 7c b3 09 36  |.l.}...ee.2.|..6|
000000d0  fc 95 79 24 12 d8 cc 3a  69 18 63 1d 7a 48 a9 ee  |..y$...:i.c.zH..|
000000e0  8d 77 87 e9 04 3b 76 d7  16 c3 9d 26 dd 36 6e 6a  |.w...;v....&.6nj|
000000f0  41 22 ee 12 ca b0 61 e5  07 79 04 a1 19 87 4d 23  |A"....a..y....M#|
00000100  b9 a3 af 49 15 3d d0 75  da df a5 5d de db 06 dc  |...I.=.u...]....|
00000110  33 76 bf 95 4e cd c7 c4  97 3b 23 26 08 f0 ab 95  |3v..N....;#&....|
00000120  26 4e 42 c8 98 e8 d2 cc  27 79 15 a0 78 e5 f8 88  |&NB.....'y..x...|
00000130  93 4c f7 c9 ae e7 d9 76  a8 46 3e d7 81 bc 67 e2  |.L.....v.F>...g.|
00000140  61 e3 dc cf d3 82 0c 99  12 34 b9 cb 31 b5 40 15  |a........4..1.@.|
00000150  62 4f a7 5f a6 a7 b4 f6  2c 4c ac ce ea c0 83 72  |bO._....,L.....r|
00000160  df b3 a7 55 8b 27 21 3a  71 e5 3c 6d 24 28 85 88  |...U.'!:q.<m$(..|
00000170  6c c6 48 1e 4e a7 46 35  b6 c9 6b 5d 6f 9d bb db  |l.H.N.F5..k]o...|
00000180  b8 38 f8 1b 46 fd db f8  9b d6 46 2c 11 24 31 c3  |.8..F.....F,.$1.|
00000190  93 85 92 d8 4a b0 24 41  15 51 95 d9 dc 15 66 32  |....J.$A.Q....f2|
000001a0  73 5c 3d 9d 7e ab 77 76  4e 3e 0a ee 1b 46 32 ef  |s\=.~.wvN>...F2.|
000001b0  b0 c5 0a 4a 20 39 31 ed  d2 44 15 c3 4a cc 00 fe  |...J 91..D..J...|
000001c0  ff ff 83 fe ff ff 01 00  00 00 56 57 fb 17 00 00  |..........VW....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by oldfred on 2010-04-02
If you notice you have grub installed everywhere. It should only be in the MBR. And windows has essential boot files in the partition boot sector and that is why you cannot boot as you overwrote the windows files.

You need your windows cd/dvd and run repairs.

General instructions - do not run fixboot unless you want to boot windows only.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by alex69 on 2010-04-02
what a wonderful reply!
thank you so much for your care on my troubles...
But I've got a seriuos problem in following your detailed instructions, infact I bought a windows PC with a OEM Vista OS pre-installed and no CD in on my own...
Do you think that the win CD is the only way to repair? if yes I'll find the way to find a CD somewhere...

---

### Post by oldfred on 2010-04-02
Not everyone  needs this and when I include everything in one post new users eyes glaze over and they give up.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)

---

### Post by alex69 on 2010-04-02
I made all you wanted me to do!

I've burned a CD with the Vista repair disk from the link you gave me,
from the console I've tried to browse trought my win partition and all is ok (all file and data where in the same old place...) but the problem begun when I tried to repair:
from the console, when I wrote "bootrec.exe /fixboot the replay was: "The volume does not contain a recognized file system";
when I wrote "bootrec.exe /scanos the reply was "windows installations found = 0" and so on...
when I tried chkdsk /f the replay was some like: "YOU CANNOT PERFORM IN A READ-ONLY ENVIRONMENT"

I'M GETTING VERY BAD...

---

### Post by oldfred on 2010-04-02
I just noticed your Vista partition is showing as FAT16. That does not look correct. I thought Vista was NTFS only?? I know the win7 boot partition comes up with a non-standard format but the install should be NTFS.

---

