---
title: "Grub boot problem"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by noyz on 2010-06-23
i'm trying to install ubuntu 10.4
i also tryed 8.04
fdisk -l

Disk /dev/sda: 300.1 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x187a187a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       84636    42656512+   7  HPFS/NTFS
/dev/sda2           84637      581460   250399073    f  W95 Ext'd (LBA)
/dev/sda5          134471      581460   225282928+   7  HPFS/NTFS
/dev/sda6           84637       88605     1999872   82  Linux swap / Solaris
/dev/sda7           88607      134466    23112704   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x374d0c22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       41432   332802508+   7  HPFS/NTFS
/dev/sdb2           41433       77826   292329324    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb5           41433       77826   292329292+   7  HPFS/NTFS

Disk /dev/sdc: 2055 MB, 2055019520 bytes
16 heads, 63 sectors/track, 3981 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3982     2006823+   b  W95 FAT32

sda7 is the partition where i want to install linux.
before this sda7 was after the sda5 fizical and i got grub2 error: no such partition or for grub 1 grub rescue  cmd i read what commands work at grub rescue .. none of them work's for me.. only ls. root / boot does't work.. i read somewhere on the internet that if u have a partition more than 137 gb bios cannot boot from the partition who is next to this first partition.. space :-?? whatever.. so i've moved the ext4 sda7 and 6 before sda5 wich is quite large.

now i don't get any error but system doesnt boot at all..
only the cursor appears, no message.. nothing same for 10.4 and 8.04

any ideeas how to make this bootloader work ?

---

### Post by darkod on 2010-06-23
Do you already have 10.04 installed in sda7 or you are trying to install it there?

---

### Post by noyz on 2010-06-23
is installed. 
but because it didn't quite work with grub2 reinstall .. 
i keep try to install it and after i install it .. nothing...
i've tryied to remove --no floppy from grub.cfg, 
i've tryied to install grub grub2.. nothing..
still not booting..
i don't know why.. is the first time in my life when i've spent almoust 2 days to install linux..
so 
what u see there is 10.4 already installed .. but because it doesnt boot i get to write here by booting from usb stick - live ubuntu..

---

### Post by garvinrick4 on 2010-06-23
darkod will get you fixed up. I do like a Extended partition for Linux. Notice sda3
holds all the non ntfs partitions. I believe sda3 or so as extended would have made
you a lot cleaner install. Simple thing but keeps from using all 4 of your primarys if  you
decide to add to sda.

[ATTACH]161371[/ATTACH]

The unallocated space of 4 gig between OS's is just incase I want to increase size
on either side. Have plenty of room so no big deal.

---

### Post by darkod on 2010-06-23
If you tried to install grub1 that's no good, you shouldn't mix them.

10.04 comes with grub2 and stick with it.

From live mode, try this:

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If that didn't work, again in live mode download the boot info script from my signature, run it and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by noyz on 2010-06-23
i've didn't mixed them
i've just said that i tried grub2 from 10.4 isntall
or gurb 1 from 8.04..
so i didn't try to install grub2 on 8.04 install


root@ubuntu:/media/ffee5f64-f6b8-4980-b8fc-53246075e04e/home/noyz# bash boot.sh Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdc1 for information... 
Finished. The results are in the file RESULTS.txt located in /media/ffee5f64-f6b8-4980-b8fc-53246075e04e/home/noyz

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 131551256 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    85,313,087    85,313,025   7 HPFS/NTFS
/dev/sda2          85,313,534   586,111,679   500,798,146   f W95 Ext d (LBA)
/dev/sda5         135,545,823   586,111,679   450,565,857   7 HPFS/NTFS
/dev/sda6          85,313,536    89,313,279     3,999,744  82 Linux swap / Solaris
/dev/sda7          89,315,328   135,540,735    46,225,408  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   665,605,079   665,605,017   7 HPFS/NTFS
/dev/sdb2         665,605,080 1,250,263,727   584,658,648   f W95 Ext d (LBA)
/dev/sdb5         665,605,143 1,250,263,727   584,658,585   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2055 MB, 2055019520 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     4,013,709     4,013,647   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C208002408001A55                       ntfs       Windows                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        C0FC5CD2FC5CC476                       ntfs       Noyz old                      
/dev/sda6        e078ebdf-ab5d-46eb-8bbf-2fe54788a726   swap                                     
/dev/sda7        ffee5f64-f6b8-4980-b8fc-53246075e04e   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9EB02335B02312F7                       ntfs       Noyz                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3EF4254CF42507AB                       ntfs       Otherz                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        E475-27C1                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/ffee5f64-f6b8-4980-b8fc-53246075e04e ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set ffee5f64-f6b8-4980-b8fc-53246075e04e
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set ffee5f64-f6b8-4980-b8fc-53246075e04e
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set ffee5f64-f6b8-4980-b8fc-53246075e04e
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ffee5f64-f6b8-4980-b8fc-53246075e04e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set ffee5f64-f6b8-4980-b8fc-53246075e04e
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ffee5f64-f6b8-4980-b8fc-53246075e04e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set ffee5f64-f6b8-4980-b8fc-53246075e04e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set ffee5f64-f6b8-4980-b8fc-53246075e04e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c208002408001a55
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e078ebdf-ab5d-46eb-8bbf-2fe54788a726 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  61.5GB: boot/grub/core.img
  61.6GB: boot/grub/grub.cfg
  61.6GB: boot/initrd.img-2.6.32-22-generic-pae
  61.6GB: boot/vmlinuz-2.6.32-22-generic-pae
  61.6GB: initrd.img
  61.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ff 1e 72 fe 3f b3 f8 ad  b9 7f c6 dd ef c7 e5 ee  |..r.?...........|
00000010  be 3d e7 7c 7f b9 f8 f6  7f e4 8d 30 a6 74 f9 6f  |.=.|.......0.t.o|
00000020  f1 b6 ff ee ef 61 ec 9b  be 3e db fd fa 30 82 a4  |.....a...>...0..|
00000030  f4 e7 53 bb c3 be 3f aa  3f 3f de f9 dd fc 8b c3  |..S...?.??......|
00000040  fe 12 6e 7b fc 7b d3 fd  f2 b4 eb e2 df 83 b0 b5  |..n{.{..........|
00000050  35 b3 be 2f 94 aa 19 f8  b3 29 c9 ff 88 fc 1f 9f  |5../.....)......|
00000060  8e 75 3f 8d fd be 37 f6  f8 f3 ff f7 7d db bf f1  |.u?...7.....}...|
00000070  73 ed bf c6 db 9b fc 72  9d 39 b7 e7 dc ef 90 9f  |s......r.9......|
00000080  1c b6 b4 7e 0b 7e cc ce  79 bd 0f 5c bf d9 73 c7  |...~.~..y..\..s.|
00000090  7e 47 01 69 12 c8 2d fe  ac 8b 59 85 6b ff be dd  |~G.i..-...Y.k...|
000000a0  55 f4 67 ed 3d 76 54 47  04 0f 06 ee fb 8a dc 8b  |U.g.=vTG........|
000000b0  3c 57 0f 2e dc eb cb 35  0e 7c 95 bd 3c 98 b1 0d  |<W.....5.|..<...|
000000c0  f1 e6 df c6 db 7f 1b ef  7c 79 b7 f1 bc ff c7 de  |........|y......|
000000d0  ff 1b dd fc 6f 6a f8 6d  b9 ff 8d b6 fe 37 a7 fc  |....oj.m.....7..|
000000e0  7f 37 f1 b9 97 f1 fd e7  e1 b9 7f ff 8b bd f7 f5  |.7..............|
000000f0  f5 1c f0 8d 23 df 13 35  9f 5f 2c 1e 7e 3d 3f 8d  |....#..5._,.~=?.|
00000100  f7 bf 79 a0 49 6b 19 f8  90 cb bb 7c 6f 6f fb b9  |..y.Ik.....|oo..|
00000110  84 7a 4c 7e 28 04 8c 94  fd 1d dc 8b e7 fc b6 16  |.zL~(...........|
00000120  f5 8f 4f c3 78 2d 55 fe  14 4b 93 74 fc 1c 9f 8d  |..O.x-U..K.t....|
00000130  27 ff 3d a2 7e 17 3c f3  fc bd e5 06 e7 bf 15 3b  |'.=.~.<........;|
00000140  b7 f0 db a8 9e f7 c9 b9  4f a5 8e 27 3f 1c fd fe  |........O..'?...|
00000150  3d 9f fd 59 9a 4e 39 fd  6b 0b f0 8a 21 1b 77 ef  |=..Y.N9.k...!.w.|
00000160  2a 23 77 31 a7 7e e8 fd  3d 40 17 19 7a ff b8 b2  |*#w1.~..=@..z...|
00000170  1e 3d 90 18 04 97 32 5a  3b e4 2e 43 9c 9f f8 25  |.=....2Z;..C...%|
00000180  12 72 6e 7f 1b 6f 7c 7f  f7 f1 b6 df c6 db 7f 1f  |.rn..o|.........|
00000190  6d fc 6d bf f1 37 c7 df  c6 f3 df 0f b7 57 f8 95  |m.m..7.......W..|
000001a0  1c fa 5f 1b cd fc 7f bd  f1 5b ae ff 8f 53 7f db  |.._......[...S..|
000001b0  ba 56 7a e9 d5 88 7e 9a  89 3d 07 be fa 27 00 0f  |.Vz...~..=...'..|
000001c0  ff ff 07 0f ff ff 3f 00  00 00 99 2e d9 22 00 00  |......?......"..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



from what it is in result.txt.. i think there are 3 bootloaders installed :-??

---

### Post by oldfred on 2010-06-24
It looks like if you are booting from sda the 300GB drive in BIOS it should boot.

I do not see any 8.04 other than the grub legacy in the MBR of sdb. sdc looks like your 2gb USB flash drive with syslinux.

you also have grub installed to the PBR or boot sector of your windows partition, so it will not boot.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Your boot.ini shows two windows installs but you only have one. It looks like it defaults to the one missing.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

---

### Post by darkod on 2010-06-24
You should set the 300GB disk as first boot option in BIOS. That should show you the grub boot menu and ubuntu should boot fine.

As oldfred said, you also have grub2 on the windows partition which you can repair with this procedure:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to repair partition #1 on disk /dev/sda.

---

