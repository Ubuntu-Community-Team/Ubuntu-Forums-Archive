---
title: "no such device; after ubuntu 11.04 install"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by kevorski on 2011-05-16
I was dual-booting Ubuntu 11.04 just fine for about the last week but then ran into some issues and decided to reinstall Ubuntu. Now after the install I get this error:
**_error: nu such device : d38af2a9-740e-4d3c-b267-2a3848e5d319_** and it goes into the grub rescue command prompt screen.

anyone have any ideas on what causes this? I have tried to reinstall Ubuntu about 6 times now, complete installs. I have tried changing boot priority multiple times. I installed off a thumb drive and left the thumb drive in after install, took it out after install.

It's been very frustrating to get this up and running

---

### Post by kevorski on 2011-05-16
now I can't even boot into Windows after I remove the HDD that I'm installing Ubutnu to

---

### Post by drs305 on 2011-05-16
You may have installed Grub to the Windows drive MBR, which is why you can't boot Windows. 

With the Ubuntu drive connected, from the Grub menu (if you get one, if not, try holding down SHIFT during boot):
Press 'e'.
Use the cursor and DEL keys to remove the search line.
In the Linux line, make sure the "root=/dev/sdXY" point to the correct drive/partition.
If you think the kernel number has changed, change it in the menu.
Press CTRL-x and see if it boots.

That is a quick way to see if it boots. There are lots of reasons it wouldn't. If it doesn't, please click on the "BIS" link in my signature line. Download and run the boot info script, then post the contents of RESULTS.txt. 

When you are ready to copy the contents, click on the # icon in the post's menubar. This will generate [noparse]```
 
``` [/noparse] tags. Paste between them. It helps with formatting.

RESULTS.txt will show the status of your boot files and allow us to make informed suggestions. If you have trouble running it there are instructions on the download page, and additional instructions by *louieb* on a link on the left side of the page.

---

### Post by kevorski on 2011-05-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cbdc4.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for cadc2.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   976,768,064   976,752,000   5 Extended
/dev/sda5              16,128   976,768,064   976,751,937   7 HPFS/NTFS
/dev/sda2    *             63        16,064        16,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   549,498,879   549,496,832  83 Linux
/dev/sdc2         549,500,926   625,141,759    75,640,834   5 Extended
/dev/sdc5         599,742,464   625,141,759    25,399,296  82 Linux swap / Solaris
/dev/sdc6         587,182,080   599,742,463    12,560,384  82 Linux swap / Solaris
/dev/sdc7         574,621,696   587,180,031    12,558,336  82 Linux swap / Solaris
/dev/sdc8         562,061,312   574,619,647    12,558,336  82 Linux swap / Solaris
/dev/sdc9         549,500,928   562,059,263    12,558,336  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8065 MB, 8065646080 bytes
8 heads, 32 sectors/track, 61535 cylinders, total 15753215 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32    15,753,214    15,753,183   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        2E9A59A09A59657D                       ntfs                                     
/dev/sda5        A4C85749C85718BE                       ntfs       Second HDD                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        10940ED9940EC168                       ntfs       OS                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        e760eb5f-fd85-4e85-9cdb-06ddf4a94c20   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        5961ecf5-9c5d-42bd-82ef-854cfad7ac97   swap                                     
/dev/sdc6        e93a8cb3-c02f-4bb5-9bd9-daedc02772e7   swap                                     
/dev/sdc7        ee8573b8-000d-4bff-ab1c-a9ba7b6beff7   swap                                     
/dev/sdc8        a101d4db-cb64-4528-b01d-27de12f57354   swap                                     
/dev/sdc9        eef23b8f-52b2-4543-8787-c1da5ea35f09   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        11DF-3658                              vfat       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e760eb5f-fd85-4e85-9cdb-06ddf4a94c20 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e760eb5f-fd85-4e85-9cdb-06ddf4a94c20 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 10940ED9940EC168
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=e760eb5f-fd85-4e85-9cdb-06ddf4a94c20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc9 during installation
UUID=eef23b8f-52b2-4543-8787-c1da5ea35f09 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
  30.6GB: boot/initrd.img-2.6.38-8-generic
  17.3GB: boot/vmlinuz-2.6.38-8-generic
  30.6GB: initrd.img
  17.3GB: vmlinuz

=========================== sdd1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdd1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  e1 b5 45 fe 8a 27 5a b5  db 67 da 1a da b9 38 14  |..E..'Z..g....8.|
00000010  da 9a 48 cb 81 94 ef ea  a5 4a 94 2a 2e c9 a9 f3  |..H......J.*....|
00000020  06 23 ee aa 9f 1e 7d 4d  da dd 39 14 29 2e fa ad  |.#....}M..9.)...|
00000030  8a b4 14 b2 77 19 0c 54  0f 80 39 56 78 b9 5d 56  |....w..T..9Vx.]V|
00000040  5f 90 44 e4 5f a2 ac 3d  2d a6 c1 4d 3d 1b 0c 24  |_.D._..=-..M=..$|
00000050  42 fa 5e ab 2c 51 9b 68  ab ca 21 d1 e8 ed 57 33  |B.^.,Q.h..!...W3|
00000060  73 e0 f9 70 03 81 ce 23  21 32 0a 73 25 a9 70 ff  |s..p...#!2.s%.p.|
00000070  d6 cd dc 8e 12 07 85 fe  aa 09 67 ec cc ff ad 3a  |..........g....:|
00000080  ae 97 8e 87 82 23 72 32  e0 c8 0a 66 46 38 53 19  |.....#r2...fF8S.|
00000090  72 9a db 2c 8d 4b a5 1e  aa c0 33 10 74 c2 ad 83  |r..,.K....3.t...|
000000a0  b2 35 4a 7d 3d 14 dc 1e  78 db a8 64 9c 80 bc 26  |.5J}=...x..d...&|
000000b0  cb 97 49 84 a1 2b f7 ea  87 ad df de d2 63 e3 30  |..I..+.......c.0|
000000c0  1e 09 5d 40 4f f0 37 2f  9e b1 eb 0d d6 9e 05 30  |..]@O.7/.......0|
000000d0  90 70 4e 06 01 20 91 f3  55 54 87 d4 fb 8d 36 48  |.pN.. ..UT....6H|
000000e0  5c a5 58 fc 4a 97 bd 0c  81 94 fe 17 5b 63 27 cb  |\.X.J.......[c'.|
000000f0  fe 68 03 c0 20 0a 60 a4  48 10 20 c4 10 c0 3f e3  |.h.. .`.H. ...?.|
00000100  f8 3c f0 f4 e0 ff ca fd  30 b9 61 fc ea 97 17 2b  |.<......0.a....+|
00000110  f7 87 bd 92 a5 73 8f 2b  2f 96 06 69 75 c9 df d1  |.....s.+/..iu...|
00000120  83 d3 cd 6c eb ee db 65  34 21 7f 3a b5 e7 38 93  |...l...e4!.:..8.|
00000130  ad 1e 61 ba 2c 72 7b 22  98 7b dc e0 b7 89 aa 21  |..a.,r{".{.....!|
00000140  bb c1 47 be d4 27 51 07  bc 52 3c 02 bd 2c 9a 7f  |..G..'Q..R<..,..|
00000150  55 32 a6 7c 15 47 85 c8  ab e5 c2 3f f4 1e 16 00  |U2.|.G.....?....|
00000160  f5 65 94 02 9a 59 c3 a1  15 95 03 14 d6 c6 cd a7  |.e...Y..........|
00000170  33 fb 8c 53 d3 ba d9 58  c4 29 ad 4a 68 64 1c 60  |3..S...X.).Jhd.`|
00000180  b4 05 9c 72 fe b6 78 ea  f0 45 dc 37 ef c6 92 c2  |...r..x..E.7....|
00000190  ca 2a 15 a8 cd c1 4d 47  ca fd 55 f8 79 eb 8c c4  |.*....MG..U.y...|
000001a0  d8 18 4f e8 1e 12 0b db  06 1d 8f 2f d9 51 d6 86  |..O......../.Q..|
000001b0  9e c0 61 d8 1d ad 35 9b  24 1a 52 f1 d0 ee 00 01  |..a...5.$.R.....|
000001c0  01 01 07 fe ff ff 3f 00  00 00 41 0d 38 3a 00 00  |......?...A.8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  df 5f f0 00 b9 77 00 00  00 00 00 00 02 00 00 00  |._...w..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 58 36 df 11 4e  4f 20 4e 41 4d 45 20 20  |..)X6..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 96  ef 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

here is the results

oops sorry for misposting it :S

---

### Post by drs305 on 2011-05-16
I actually should have had you click on "BIS-2", which is the script for Natty, but no matter (unless you have to run it again).

From the RESULTS, it looks like Windows is on sdb1 and Ubuntu is on sdc1.
You should be able to boot Ubuntu (and see a Windows entry in the menu) by changing the BIOS boot order to boot sdc first.

If necessary, from the LiveCD, you can restore sdc's bootloader with the following commands:```

sudo mount /dev/sdc1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdc
```
Note you don't include the partition number in the second command.

We can also restore the Windows menu if you have BIOS boot sdb (as a backup if sdc fails). To do this, you *partially install and configure* a bootloader called lilo. Run only the following 2 commands, and disregard the messages that it needs to be configured:
```

sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```

When you reboot, make sure sdc boots first. If sdb boots first, you  should see the Windows menu.

Also, you have a bunch of swap partitions. You only need one. We can discuss that later if desired.

---

### Post by kevorski on 2011-05-16
ok thank you. i will try that and see what happens :D

---

### Post by kevorski on 2011-05-16
I have gotten Windows to boot just fine and when I try to change the boot order I still get it to boot into Windows no matter which HDD that I use. Where would I fix this at?

---

### Post by drs305 on 2011-05-16
> **kevorski said:**
> I have gotten Windows to boot just fine and when I try to change the boot order I still get it to boot into Windows no matter which HDD that I use. Where would I fix this at?

Are you seeing a menu when you boot? If so, is it a Grub menu or a Windows menu?

Did you run the 'mount' and 'grub-install' commands from my earlier post?

Please click the BIS-2 link and run the beta boot info script. There is a bit of a glitch in the original script that hides some of the information when run with Natty.

---

### Post by kevorski on 2011-05-16
yeah I ran everything you wrote earlier line for line

i'll do BIS2 in one second

---

### Post by kevorski on 2011-05-16
```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    -----
    search.fs_uuid e760eb5f-fd85-4e85-9cdb-06ddf4a94c20 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Lilo is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........F.:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 61334 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1              16,065   976,768,064   976,752,000   5 Extended
/dev/sda5              16,128   976,768,064   976,751,937   7 NTFS / exFAT / HPFS
/dev/sda2    *             63        16,064        16,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   549,498,879   549,496,832  83 Linux
/dev/sdc2         549,500,926   625,141,759    75,640,834   5 Extended
/dev/sdc5         599,742,464   625,141,759    25,399,296  82 Linux swap / Solaris
/dev/sdc6         587,182,080   599,742,463    12,560,384  82 Linux swap / Solaris
/dev/sdc7         574,621,696   587,180,031    12,558,336  82 Linux swap / Solaris
/dev/sdc8         562,061,312   574,619,647    12,558,336  82 Linux swap / Solaris
/dev/sdc9         549,500,928   562,059,263    12,558,336  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8065 MB, 8065646080 bytes
8 heads, 32 sectors/track, 61535 cylinders, total 15753215 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             32    15,753,214    15,753,183   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        2E9A59A09A59657D                       ntfs       
/dev/sda5        A4C85749C85718BE                       ntfs       Second HDD
/dev/sdb1        10940ED9940EC168                       ntfs       OS
/dev/sdc1        e760eb5f-fd85-4e85-9cdb-06ddf4a94c20   ext4       
/dev/sdc5        5961ecf5-9c5d-42bd-82ef-854cfad7ac97   swap       
/dev/sdc6        e93a8cb3-c02f-4bb5-9bd9-daedc02772e7   swap       
/dev/sdc7        ee8573b8-000d-4bff-ab1c-a9ba7b6beff7   swap       
/dev/sdc8        a101d4db-cb64-4528-b01d-27de12f57354   swap       
/dev/sdc9        eef23b8f-52b2-4543-8787-c1da5ea35f09   swap       
/dev/sdd1        11DF-3658                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e760eb5f-fd85-4e85-9cdb-06ddf4a94c20 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e760eb5f-fd85-4e85-9cdb-06ddf4a94c20 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root e760eb5f-fd85-4e85-9cdb-06ddf4a94c20
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 10940ED9940EC168
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
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=e760eb5f-fd85-4e85-9cdb-06ddf4a94c20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc9 during installation
UUID=eef23b8f-52b2-4543-8787-c1da5ea35f09 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.143264771 = 17.333698560   boot/grub/core.img                             1
  28.180805206 = 30.258909184   boot/grub/grub.cfg                             1
  28.536647797 = 30.640992256   boot/initrd.img-2.6.38-8-generic               1
  16.133792877 = 17.323528192   boot/vmlinuz-2.6.38-8-generic                  1
  28.536647797 = 30.640992256   initrd.img                                     1
  16.133792877 = 17.323528192   vmlinuz                                        1

=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  e1 b5 45 fe 8a 27 5a b5  db 67 da 1a da b9 38 14  |..E..'Z..g....8.|
00000010  da 9a 48 cb 81 94 ef ea  a5 4a 94 2a 2e c9 a9 f3  |..H......J.*....|
00000020  06 23 ee aa 9f 1e 7d 4d  da dd 39 14 29 2e fa ad  |.#....}M..9.)...|
00000030  8a b4 14 b2 77 19 0c 54  0f 80 39 56 78 b9 5d 56  |....w..T..9Vx.]V|
00000040  5f 90 44 e4 5f a2 ac 3d  2d a6 c1 4d 3d 1b 0c 24  |_.D._..=-..M=..$|
00000050  42 fa 5e ab 2c 51 9b 68  ab ca 21 d1 e8 ed 57 33  |B.^.,Q.h..!...W3|
00000060  73 e0 f9 70 03 81 ce 23  21 32 0a 73 25 a9 70 ff  |s..p...#!2.s%.p.|
00000070  d6 cd dc 8e 12 07 85 fe  aa 09 67 ec cc ff ad 3a  |..........g....:|
00000080  ae 97 8e 87 82 23 72 32  e0 c8 0a 66 46 38 53 19  |.....#r2...fF8S.|
00000090  72 9a db 2c 8d 4b a5 1e  aa c0 33 10 74 c2 ad 83  |r..,.K....3.t...|
000000a0  b2 35 4a 7d 3d 14 dc 1e  78 db a8 64 9c 80 bc 26  |.5J}=...x..d...&|
000000b0  cb 97 49 84 a1 2b f7 ea  87 ad df de d2 63 e3 30  |..I..+.......c.0|
000000c0  1e 09 5d 40 4f f0 37 2f  9e b1 eb 0d d6 9e 05 30  |..]@O.7/.......0|
000000d0  90 70 4e 06 01 20 91 f3  55 54 87 d4 fb 8d 36 48  |.pN.. ..UT....6H|
000000e0  5c a5 58 fc 4a 97 bd 0c  81 94 fe 17 5b 63 27 cb  |\.X.J.......[c'.|
000000f0  fe 68 03 c0 20 0a 60 a4  48 10 20 c4 10 c0 3f e3  |.h.. .`.H. ...?.|
00000100  f8 3c f0 f4 e0 ff ca fd  30 b9 61 fc ea 97 17 2b  |.<......0.a....+|
00000110  f7 87 bd 92 a5 73 8f 2b  2f 96 06 69 75 c9 df d1  |.....s.+/..iu...|
00000120  83 d3 cd 6c eb ee db 65  34 21 7f 3a b5 e7 38 93  |...l...e4!.:..8.|
00000130  ad 1e 61 ba 2c 72 7b 22  98 7b dc e0 b7 89 aa 21  |..a.,r{".{.....!|
00000140  bb c1 47 be d4 27 51 07  bc 52 3c 02 bd 2c 9a 7f  |..G..'Q..R<..,..|
00000150  55 32 a6 7c 15 47 85 c8  ab e5 c2 3f f4 1e 16 00  |U2.|.G.....?....|
00000160  f5 65 94 02 9a 59 c3 a1  15 95 03 14 d6 c6 cd a7  |.e...Y..........|
00000170  33 fb 8c 53 d3 ba d9 58  c4 29 ad 4a 68 64 1c 60  |3..S...X.).Jhd.`|
00000180  b4 05 9c 72 fe b6 78 ea  f0 45 dc 37 ef c6 92 c2  |...r..x..E.7....|
00000190  ca 2a 15 a8 cd c1 4d 47  ca fd 55 f8 79 eb 8c c4  |.*....MG..U.y...|
000001a0  d8 18 4f e8 1e 12 0b db  06 1d 8f 2f d9 51 d6 86  |..O......../.Q..|
000001b0  9e c0 61 d8 1d ad 35 9b  24 1a 52 f1 d0 ee 00 01  |..a...5.$.R.....|
000001c0  01 01 07 fe ff ff 3f 00  00 00 41 0d 38 3a 00 00  |......?...A.8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
boot_info_script.sh: line 1577: [: 2.73495e+09: integer expression expected

```


thank you for all the help you have been giving me

:D

---

### Post by drs305 on 2011-05-16
Is BIOS set to boot sdc (320GB)?

Things look fairly normal. So when it boots, do you see a Grub menu? Do you see any menu? If not, hold down SHIFT during boot and the grub menu should appear.

It's certainly acting like it isn't booting from the Ubuntu drive.

---

### Post by kevorski on 2011-05-16
> **drs305 said:**
> Is BIOS set to boot sdc (320GB)?

Things look fairly normal. So when it boots, do you see a Grub menu? Do you see any menu? If not, hold down SHIFT during boot and the grub menu should appear.

It's certainly acting like it isn't booting from the Ubuntu drive.

Yeah I have everything setup for it to boot from the 320 first. I only see the Windows loading screen when I boot, no GRUB. I will try to hold Shift during boot and see if that fixes anything but as of right now I don't see anything related to Ubuntu at all

---

### Post by kevorski on 2011-05-16
holding shift didn't get it working either.

---

### Post by kevorski on 2011-05-17
i can get into windows just fine but no grub comes up when booting of the 320gb. is there a way to repair the grub.cfg in a live cd?

---

### Post by drs305 on 2011-05-17
> **kevorski said:**
> i can get into windows just fine but no grub comes up when booting of the 320gb. is there a way to repair the grub.cfg in a live cd?

I am not seeing a problem in the files. There was a problem in the first BIS but that has been corrected. The first thing to try is to purge and  reinstall (reinstalling isn't enough) Grub2 from the LiveCD, using the 'chroot' procedure detailed in the 'Chroot' link in my signature line. You can go directly to the "Chroot" section.

In following the chroot instructions, mount /dev/sdc1. When it gets to the point where you select the G2 installation, select sdc and NOT the partition.

If you have any questions you can post them here.

---

