---
title: "Upgraded to 10.04; now can't boot to Windows XP"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by donofrij on 2010-05-17
I also upgraded from Ubuntu 9.10 to 10.04 w/a dual boot to Windows XP using GRUB-2. Now, while the initial GRUB (black screen) menu lists Linux 2.6.32-22 generic and generic recovery mode; 2.6.31-20 generic and generic recovery mode, memory test, and Microsoft Windows XP (on /dev/sda/1), I cannot boot into Windows; only Linux. However, the /boot/grup/grup.cfg file is absolutely blank (neither Linux nor Windows appears in that file). sudo update-grup did not help. I've read some threads, but I can't say I'm that conversant in Linux. Below is my boot script info.  Can anyone help?

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 135298982 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 135298694 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    92,164,904    92,164,842   7 HPFS/NTFS
/dev/sda2         234,018,855   234,436,544       417,690  88 Linux plaintext
/dev/sda3          92,164,905   169,983,764    77,818,860   5 Extended
/dev/sda5          92,164,968    98,301,734     6,136,767  82 Linux swap / Solaris
/dev/sda6          98,301,798   139,267,484    40,965,687  83 Linux
/dev/sda7         139,267,548   169,983,764    30,716,217  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   277,828,109   277,828,047   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        537FFEB51126E2C1                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        557b764f-55de-4e66-a6be-28d593874d22   swap                                     
/dev/sda6        4354cc97-fe22-4517-9543-1855643fa75d   ext3                                     
/dev/sda7        9a5651ba-0965-4363-9e64-aee038753def   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C6EC7700EC76E9D7                       ntfs       Seagate Replica               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw)
/dev/sdb1        /media/Seagate Replica_  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=4354cc97-fe22-4517-9543-1855643fa75d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=4354cc97-fe22-4517-9543-1855643fa75d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=4354cc97-fe22-4517-9543-1855643fa75d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=4354cc97-fe22-4517-9543-1855643fa75d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4354cc97-fe22-4517-9543-1855643fa75d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 537ffeb51126e2c1
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=4354cc97-fe22-4517-9543-1855643fa75d /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=9a5651ba-0965-4363-9e64-aee038753def /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=557b764f-55de-4e66-a6be-28d593874d22 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  69.3GB: boot/grub/core.img
  69.2GB: boot/grub/grub.cfg
  69.3GB: boot/initrd.img-2.6.31-20-generic
  69.3GB: boot/initrd.img-2.6.32-22-generic
  69.3GB: boot/vmlinuz-2.6.31-20-generic
  69.3GB: boot/vmlinuz-2.6.32-22-generic
  69.3GB: initrd.img
  69.3GB: initrd.img.old
  69.3GB: vmlinuz
  69.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  26 0d 43 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |&.CA.K.r.'. .d.a|
00000010  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |.E.A.K.r.'. .d.a|
*
00000030  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e6 63  |.E.A.K.r.'. .d.c|
00000040  32 45 d3 61 47 57 17 74  f2 25 09 a0 23 e4 0f 32  |2E.aGW.t.%..#..2|
00000050  b1 45 d3 70 60 c5 39 fc  22 9b f3 00 12 c4 a5 1d  |.E.p`.9.".......|
00000060  f1 ba a7 43 28 89 b3 84  30 a7 87 74 5d 25 5e cb  |...C(...0..t]%^.|
00000070  98 88 c0 1b f2 39 a8 f3  09 72 59 55 aa c4 a4 1d  |.....9...rYU....|
00000080  49 85 a6 44 23 aa e0 06  c5 41 78 6c f9 da e0 1d  |I..D#....Axl....|
00000090  0b 01 2c 40 c6 c0 ff 36  8e e0 f7 30 e9 a3 a1 63  |..,@...6...0...c|
000000a0  cc 45 b5 c8 fc 43 26 36  f4 27 83 46 d8 a4 6c 25  |.E...C&6.'.F..l%|
000000b0  c9 23 5a 05 ac ff a3 bf  e1 55 f6 9b e9 14 0e 1c  |.#Z......U......|
000000c0  79 4d 1e 52 d3 41 17 b0  72 28 77 d6 e9 8d 62 61  |yM.R.A..r(w...ba|
000000d0  73 40 af 87 e4 b4 e1 14  c3 e7 7b d0 a9 02 6c 25  |s@........{...l%|
000000e0  c9 74 01 c9 6a 8a 03 70  7a cf 7b d4 a9 ed a1 69  |.t..j..pz.{....i|
000000f0  fc 85 5b 91 60 a3 e3 14  7b 23 95 81 ad 18 83 50  |..[.`...{#.....P|
00000100  1f 23 24 75 28 1f eb 14  c3 f5 95 d7 9d 60 6d 35  |.#$u(........`m5|
00000110  c6 cc 97 4d 9b 0f e9 0f  ce ad a7 2d 29 86 e3 eb  |...M.......-)...|
00000120  81 4f 2d 80 a8 9a 6b 1e  fe 7d 79 54 e2 df e5 11  |.O-...k..}yT....|
00000130  43 86 e2 9a 18 4a e3 bf  e1 55 ed ac 2a ea e3 29  |C....J...U..*..)|
00000140  b1 25 cd f8 a0 4a 6f a9  c3 d1 c2 df 15 97 40 7e  |.%...Jo.......@~|
00000150  ac ba f5 03 dc a0 e3 99  f2 cc 0d 67 bb 31 a7 41  |...........g.1.A|
00000160  cd 02 b6 2e cd 4b a9 13  80 43 d3 64 80 17 8e 61  |.....K...C.d...a|
00000170  9f 20 b2 25 a0 6b a4 00  80 48 81 20 45 58 e5 14  |. .%.k...H. EX..|
00000180  36 86 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |6..A.K.r.'. .d.a|
00000190  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |.E.A.K.r.'. .d.a|
*
000001f0  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 b0 cb  |.E.A.K.r.'. .d..|
00000200

---

### Post by darkod on 2010-05-17
sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of sda1  and 
                       looks at sector 135298982 of the same hard drive  for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.[/COLOR]
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

Look at these instructions to remove Grub2 from /dev/sda1 (the XP system partition, not the whole disk /dev/sda). So, you need to remove it from partition #1 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

> 
 the /boot/grup/grup.cfg file is absolutely blank


I don't know whether you made spelling mistake in the post, but if you didn't, trying to open /boot/grup/grup.cfg will resolt in blank (new) file because it doesn't exist previously. It's /boot/grub/grub.cfg.

But the above link will help you fix this, no need to intervene in grub.cfg.

---

### Post by donofrij on 2010-05-17
Thank you sooooooooooooooo much! I ran testdisk, and it fixed the problem. I now can boot into Ubuntu 10.04 or Windows. 

p.s. thanks for the spelling correction (Grub,not Grup!)

---

### Post by marklusty on 2010-05-17
I had the same issue after updating to Lucid Lynx with my XP, which lives on a seperate Hard drive to Ubuntu.
Thanx for this fix,it worked for me \\:D/

---

