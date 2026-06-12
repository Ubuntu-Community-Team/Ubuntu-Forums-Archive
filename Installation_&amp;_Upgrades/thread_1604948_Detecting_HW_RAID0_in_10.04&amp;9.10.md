---
title: "Detecting HW RAID0 in 10.04&amp;9.10"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by Konikov on 2010-10-24
Hey,

My problem is: I can't detect my RAID0 with Win7 on:
[LIST]
[*]10.04 installed on separate disk (other Win7 installed on this disk can see whole raid0), it has dmraid,
[*]9.10 on LiveCD, even after I installed dmraid.
[/LIST]

"can't detect" == there's nothing in /dev/mapper (except for "control")
dmraid -ay shows "no raid disks"

My motherboard is:
**Gigabyte GA-P35-DS4**
and it has two options to make raid: via BIOS (ICH9R) or via RAID controller on this board ("GIGABYTE Technology Corp. PCIE-to-SATAII/IDE RAID Controller BIOSv1.06.59"; it has separate sockets).

I set RAID0 up on the second, separate RAID controller. My disks are:
2x Seagate ST3250410AS 250GB SATAII 16 MB cache

Is there any possibility to detect them, possibly without wiping data on current Win7 installation? If I have to set them up on ICH9R and it will work - I'll do so.

Thanks in advance ;]

---

### Post by ronparent on 2010-10-24
It is best NOT to move the disks from one raid chip set to another - that would most likely wipe the raid0 partition tables.

Go to:  [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Download and run the boot info script there and post results here. This may allow us to diagnose the problem. The raid0 should be supported by dmraid with both chip sets.

---

### Post by Konikov on 2010-10-26
> **ronparent said:**
> It is best NOT to move the disks from one raid chip set to another - that would most likely wipe the raid0 partition tables.

Go to:  [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Download and run the boot info script there and post results here. This may allow us to diagnose the problem. The raid0 should be supported by dmraid with both chip sets.

Nice script! ;] Here's the output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Dysk /dev/sda: 250.1 GB, bajtów: 250059350016
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 30401, w sumie sektorów: 488397168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,746,495   976,539,648   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Dysk /dev/sdb: 250.1 GB, bajtów: 250059350016
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 30401, w sumie sektorów: 488397168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdc ___________________ _____________________________________________________

Dysk /dev/sdc: 80.0 GB, bajtów: 80000000000
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 9726, w sumie sektorów: 156250000
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    77,818,859    77,818,797   7 HPFS/NTFS
/dev/sdc2          77,818,921   156,248,063    78,429,143   f W95 Ext d (LBA)
/dev/sdc5          77,818,923    87,871,657    10,052,735   7 HPFS/NTFS
/dev/sdc6          87,873,536   153,343,999    65,470,464  83 Linux
/dev/sdc7         153,346,048   156,248,063     2,902,016  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Dysk /dev/sdd: 500.1 GB, bajtów: 500107862016
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 60801, w sumie sektorów: 976773168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,751,999   976,751,937   c W95 FAT32 (LBA)


Drive: sde ___________________ _____________________________________________________

Dysk /dev/sde: 4018 MB, bajtów: 4018143232
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 488, w sumie sektorów: 7847936
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63     7,847,935     7,847,873   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda: PTTYPE="dos" 
/dev/sdc1        D2803F97803F80D1                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        2830BEBA30BE8E76                       ntfs                                     
/dev/sdc6        24852668-6e89-4c91-9d48-fe9da7a03425   ext4                                     
/dev/sdc7        3e9e1f87-2743-40c6-b84f-22f1aef0fc9e   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd: PTTYPE="dos" 
/dev/sde1        6C0F-C33F                              vfat                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/6C0F-C33F         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd2,6)'
search --no-floppy --fs-uuid --set 24852668-6e89-4c91-9d48-fe9da7a03425
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
set root='(hd2,6)'
search --no-floppy --fs-uuid --set 24852668-6e89-4c91-9d48-fe9da7a03425
set locale_dir=($root)/boot/grub/locale
set lang=pl
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,6)'
	search --no-floppy --fs-uuid --set 24852668-6e89-4c91-9d48-fe9da7a03425
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=24852668-6e89-4c91-9d48-fe9da7a03425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-24-generic-pae (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,6)'
	search --no-floppy --fs-uuid --set 24852668-6e89-4c91-9d48-fe9da7a03425
	echo	'Wczytywanie systemu Linux 2.6.32-24-generic-pae...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=24852668-6e89-4c91-9d48-fe9da7a03425 ro single 
	echo	'Wczytywanie pocz&#261;tkowego dysku RAM...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,6)'
	search --no-floppy --fs-uuid --set 24852668-6e89-4c91-9d48-fe9da7a03425
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,6)'
	search --no-floppy --fs-uuid --set 24852668-6e89-4c91-9d48-fe9da7a03425
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d2803f97803f80d1
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=24852668-6e89-4c91-9d48-fe9da7a03425 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=3e9e1f87-2743-40c6-b84f-22f1aef0fc9e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/core.img
  73.1GB: boot/grub/grub.cfg
  71.7GB: boot/initrd.img-2.6.32-24-generic-pae
  71.6GB: boot/vmlinuz-2.6.32-24-generic-pae
  71.7GB: initrd.img
  71.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1

00000000  c1 7f 60 a0 6a ef 23 4c  43 ab 57 a7 06 65 12 57  |..`.j.#LC.W..e.W|
00000010  d6 58 bc e5 7a 20 3e 9b  74 0a e7 3a 20 3c 5e 60  |.X..z >.t..: <^`|
00000020  54 f9 5d 50 01 d2 ca b4  0e 3c 12 0b 0a 76 aa 87  |T.]P.....<...v..|
00000030  eb 24 86 2c 46 b6 1d 81  dc 66 80 e1 ed b9 39 b4  |.$.,F....f....9.|
00000040  3a 51 45 14 c6 1d 3c c2  bd af 11 51 0f 6d 83 62  |:QE...<....Q.m.b|
00000050  f2 8d 94 1f 81 1e e6 95  cb 2a 26 4c d9 74 bd 8a  |.........*&L.t..|
00000060  a7 87 07 4f a4 04 90 97  cc a6 89 40 2f c5 1f 12  |...O.......@/...|
00000070  ec c7 89 ff 6f fa 3d 80  f8 2d 01 77 c5 5d 15 71  |....o.=..-.w.].q|
00000080  37 c6 56 a4 a1 28 6d 57  ab 60 d1 e4 d1 60 1e 56  |7.V..(mW.`...`.V|
00000090  8f 18 cd 78 cf e7 d6 5f  5b c3 67 c8 2b c1 95 85  |...x..._[.g.+...|
000000a0  49 57 2d f6 b4 d2 a6 71  ac 87 0e e2 9e b4 e0 83  |IW-....q........|
000000b0  6e 19 30 80 48 f1 a1 b5  e6 8e a6 71 8a f3 38 0f  |n.0.H......q..8.|
000000c0  d5 ba 92 02 21 eb a8 60  66 42 f5 e6 08 ff 60 58  |....!..`fB....`X|
000000d0  98 f9 09 c3 ca 06 42 9b  b5 60 b2 a2 ce 64 32 90  |......B..`...d2.|
000000e0  47 18 f4 68 58 7b 25 07  73 02 91 22 58 e0 54 b4  |G..hX{%.s.."X.T.|
000000f0  75 ab 75 88 c1 ce 22 41  bf d4 82 c0 02 ca 00 5e  |u.u..."A.......^|
00000100  91 37 08 23 b7 17 61 e9  54 12 fb 03 30 b6 92 2a  |.7.#..a.T...0..*|
00000110  c2 ba b9 b6 ae 86 21 e8  8c 01 f3 b8 2f 5d c7 06  |......!...../]..|
00000120  90 de c8 f6 56 72 ab ae  42 77 12 9a dc 95 1d 46  |....Vr..Bw.....F|
00000130  73 11 e1 cd f1 42 20 b5  9e ce 25 e5 02 35 16 7c  |s....B ...%..5.||
00000140  ba 8c 68 33 40 27 7e 33  22 87 23 69 3c 95 66 4f  |..h3@'~3".#i<.fO|
00000150  b0 07 9e 1e fb dc 9b ce  0e 4c 30 3e 87 e6 2c bd  |.........L0>..,.|
00000160  29 91 b1 24 cc aa 8d 2d  61 ab b8 35 2f 9b e1 1b  |)..$...-a..5/...|
00000170  57 fb 7c 0f ea 81 b6 97  4f 40 6b 7d 7c 7b 12 eb  |W.|.....O@k}|{..|
00000180  e9 ea d6 5a e0 be 8f 7c  b8 30 92 f4 d3 23 91 ef  |...Z...|.0...#..|
00000190  86 f9 a8 1f 37 cb e9 36  09 23 1c 9e 9a f2 58 06  |....7..6.#....X.|
000001a0  97 1a 06 b0 e8 2f ce d9  35 cf 68 82 ba eb f2 d7  |...../..5.h.....|
000001b0  32 59 64 91 66 30 a1 91  68 8c b3 c5 87 b3 6f 5d  |2Yd.f0..h.....o]|
000001c0  bd 37 44 31 8a ad 11 87  7f 05 2f f0 1f 0e d0 7a  |.7D1....../....z|
000001d0  9f c0 b9 87 6e ec b8 75  18 94 23 1f 95 ea 70 80  |....n..u..#...p.|
000001e0  52 54 f7 d9 f9 8d e4 09  9a 02 47 40 8e d5 bd a0  |RT........G@....|
000001f0  d5 f4 e4 52 e4 55 2a 4d  31 01 b7 81 34 8c 82 08  |...R.U*M1...4...|
00000200



```

sda1 and sda2(?!) are RAID0

---

### Post by ronparent on 2010-10-26
It is typical for the raid drives to be unreadable in the 'results' layout as are your sda and sdb. The raid partitions ought to show up separately though. The fact they don't show even with blkid is disturbing. 

I am also disturbed with newegg - the separate SATA ports are not labeled so it is kind of hard to determine what distinguishes them (I may have to chase it down on the manufacturer's site). You should probably file a bug report on your problem. I can't think of a fix. For more info you might check your logs and see if there is an error in detecting ATA devices that could be included in a bug report. If I think of something new I will post here.

Edit: Gigabyte site is just as uninformative!

---

