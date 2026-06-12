---
title: "grub doesnt boot ubuntu, but it boots windows 7??"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by amerinde on 2011-04-10
ok, got myself a new pc, windows 7 installed.. i just got done installing ubuntu10.10. it said to finnish, i had to reboot.. ok, no problem.. i reboot,  loading says uuid is not valid.. but, it loads 7 fine.. they are on the same drive, but different partitions. any ideas? i only got a wireless usb keyboard and when it goes to the shell, it doesnt seen to recognize it.

---

### Post by Dutch70 on 2011-04-10
Hi and welcome to UF

Please post your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] & [ /CODE].

---

### Post by Rubi1200 on 2011-04-10
+1 to the boot script recommended by Dutch70.

The results of this diagnostic script will help us analyze and troubleshoot the situation. We will then be in a better position to offer advice as to how to resolve the problem.

Thanks.

---

### Post by amerinde on 2011-04-10
thanks for the help.. hope it aint too much info.. 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdg2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdg3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdh5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    46,139,391    46,137,344  27 Hidden HPFS/NTFS
/dev/sda2    *     46,139,392 1,002,031,103   955,891,712   7 HPFS/NTFS
/dev/sda3       1,002,033,150 1,953,523,711   951,490,562   5 Extended
/dev/sda5       1,002,033,152 1,007,890,431     5,857,280  83 Linux
/dev/sda6       1,007,892,480 1,953,523,711   945,631,232  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 7864 MB, 7864320000 bytes
255 heads, 63 sectors/track, 956 cylinders, total 15360000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63    15,359,999    15,359,937   b W95 FAT32


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             63       204,862       204,800   7 HPFS/NTFS
/dev/sdg2             204,863   976,751,999   976,547,137   7 HPFS/NTFS
/dev/sdg3         976,752,000 1,953,520,064   976,768,065   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1               2,048   976,760,831   976,758,784   7 HPFS/NTFS
/dev/sdh2         976,760,832 1,943,279,615   966,518,784   7 HPFS/NTFS
/dev/sdh3       1,943,281,662 1,953,523,711    10,242,050   5 Extended
/dev/sdh5       1,943,281,664 1,953,523,711    10,242,048  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       cd1d78df-bd5f-064a-8bac-1afdb210390f   ext2       casper-rw                     
/dev/sda1        74DC7F9DDC7F57F6                       ntfs       PQSERVICE                     
/dev/sda2        1E1E59F31E59C485                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        d948dc54-e658-4dfb-8ff3-67464accd05e   ext4                                     
/dev/sda6        b3d2cd78-515d-4b70-9691-06e0dc1990e7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        2A47-C1F5                              vfat       PENDRIVE                      
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        01CBADA9C8C4F3A0                       ntfs       SYSTEM RESERVED               
/dev/sdg2        01CBADB2D3978E60                       ntfs       Acer                          
/dev/sdg3        01CBAD9AD2ECE360                       ntfs       Data                          
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        CE323D55323D43AD                       ntfs       Storage                       
/dev/sdh2        2A804E30804E0335                       ntfs       Music                         
/dev/sdh3: PTTYPE="dos" 
/dev/sdh5        1917f5c8-e3bf-4336-82a5-b7103f7eb9b3   swap                                     
/dev/sdh: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set d948dc54-e658-4dfb-8ff3-67464accd05e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set d948dc54-e658-4dfb-8ff3-67464accd05e
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d948dc54-e658-4dfb-8ff3-67464accd05e
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=d948dc54-e658-4dfb-8ff3-67464accd05e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d948dc54-e658-4dfb-8ff3-67464accd05e
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=d948dc54-e658-4dfb-8ff3-67464accd05e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d948dc54-e658-4dfb-8ff3-67464accd05e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d948dc54-e658-4dfb-8ff3-67464accd05e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 74dc7f9ddc7f57f6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 1e1e59f31e59c485
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdg1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01cbada9c8c4f3a0
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d948dc54-e658-4dfb-8ff3-67464accd05e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=b3d2cd78-515d-4b70-9691-06e0dc1990e7 /home           ext4    defaults        0       2
# swap was on /dev/sdh5 during installation
UUID=1917f5c8-e3bf-4336-82a5-b7103f7eb9b3 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 514.6GB: boot/grub/core.img
 514.6GB: boot/grub/grub.cfg
 514.7GB: boot/initrd.img-2.6.35-28-generic
 514.7GB: boot/vmlinuz-2.6.35-28-generic
 514.7GB: initrd.img
 514.7GB: vmlinuz

=========================== sdf1/boot/grub/grub.cfg: ===========================


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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdf1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  d8 5c ec 00 00 00 00 00  56 96 06 f8 0e e0 cb 01  |.\......V.......|
00000010  00 20 00 80 00 00 00 00  00 00 00 00 20 00 00 00  |. .......... ...|
00000020  12 00 3c 00 73 00 65 00  74 00 75 00 70 00 2e 00  |..<.s.e.t.u.p...|
00000030  69 00 6e 00 69 00 00 00  87 dd 3e 17 00 00 00 00  |i.n.i.....>.....|
00000040  72 dd 3e 17 00 00 00 00  72 dd 3e 17 00 00 00 00  |r.>.....r.>.....|
00000050  68 00 00 00 00 00 00 00  01 00 00 00 18 00 00 00  |h...............|
00000060  00 00 00 00 00 00 00 00  0b 00 0b 00 28 00 20 00  |............(. .|
00000070  48 00 20 00 18 00 01 00  08 01 00 00 02 00 02 00  |H. .............|
00000080  d7 04 00 00 00 00 00 00  d7 04 0c 00 00 00 00 00  |................|
00000090  00 00 f0 00 00 00 00 00  28 5d ec 00 00 00 00 00  |........(]......|
000000a0  28 5d ec 00 00 00 00 00  00 00 88 00 00 00 00 00  |(]..............|
000000b0  00 00 f0 00 00 00 00 00  d8 5c ec 00 00 00 00 00  |.........\......|
000000c0  28 5d ec 00 00 00 00 00  00 00 88 00 00 00 00 00  |(]..............|
000000d0  9a dd 3e 17 00 00 00 00  87 dd 3e 17 00 00 00 00  |..>.......>.....|
000000e0  87 dd 3e 17 00 00 00 00  38 00 00 00 00 00 00 00  |..>.....8.......|
000000f0  01 00 00 00 18 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  07 00 07 00 28 00 08 00  30 00 08 00 18 00 01 00  |....(...0.......|
00000110  38 00 58 00 00 00 02 00  71 08 00 00 00 00 00 00  |8.X.....q.......|
00000120  71 08 0c 00 00 00 00 00  d8 5c ec 00 00 00 00 00  |q........\......|
00000130  88 5c ec 00 00 00 00 00  a7 dd 3e 17 00 00 00 00  |.\........>.....|
00000140  9a dd 3e 17 00 00 00 00  00 00 00 00 00 00 00 00  |..>.............|
00000150  28 00 00 00 00 00 00 00  01 00 00 00 18 00 00 00  |(...............|
00000160  00 00 00 00 00 00 00 00  1b 00 01 00 28 00 00 00  |............(...|
00000170  28 00 00 00 18 00 00 00  00 00 00 00 00 00 02 00  |(...............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 80 f8 ff ff  |................|
00000190  b2 dd 3e 17 00 00 00 00  00 00 00 00 00 00 00 00  |..>.............|
000001a0  00 00 00 00 00 00 00 00  98 00 00 00 00 00 00 00  |................|
000001b0  01 00 00 00 18 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 59 00 00 fe  |...........`Y...|
000001d0  ff ff 05 fe ff ff 02 60  59 00 00 38 5d 38 00 00  |.......`Y..8]8..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdf1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 10 0b  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 5f ea 00 78 3a 00 00  00 00 00 00 02 00 00 00  |._..x:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f5 c1 47 2a 4e  4f 20 4e 41 4d 45 20 20  |..)..G*NO NAME  |
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
00000110  c6 06 45 7d 00 66 b8 70  80 30 00 66 ba 00 00 00  |..E}.f.p.0.f....|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by coffeecat on 2011-04-10
I can't see anything in your boot script output that would cause this:

> **amerinde said:**
> i reboot,  loading says uuid is not valid..

The UUIDs for  the Ubuntu and both the Windows installs seem to check out. Unless I'm missing something - quite possible - it's a puzzle.

So - just to be sure. You get this error message trying to boot into  Ubuntu? Yes? You say Win7 loads fine, but you would appear to have two Windows installations, on sda and on sdg. Do they both boot OK?

The grub.cfg menu entry for your sdg installation is odd:

```
menuentry "Windows 7 (loader) (on /dev/sdg1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01cbada9c8c4f3a0
    chainloader +1
}
```sdg1 != (hd2,msdos1), so I don't understand what happened there. The UUID is OK though.

Lastly, post the exact error message you get - word for word - including any UUID. That may give us a clue as to what is going wrong.

---

### Post by amerinde on 2011-04-10
ok, i tell you the system first...

Acer Aspire M7721
i7-930 2.8oGHz
64-bit 
3 - 1T SATA II hard drives
NVIDIA GTX 480
8G DDR3

(sda is the factors HD)
sda1.. is the factory restore ( i tried and grub loads it)
sda2.. just sits there, clean install of windows 7
sda3.. linux extenden
sda5.. linux boot
sda6.. linux home

sdf1.. my dvd

sdg1.. windows system reserved(100M)
sdg2.. windows 7 (installed with everything)
sdg3.. data backup

sdh1.. my storage
sdh2.. my music
sdh3.. linux extended
sdh5.. linux swap

but i guess i knew most of that already..

when i try to boot, i get the grub loader.. i choose.

Ubuntu, with Linux 2.6.35-28generic

then get a purple screen. says Ubuntu 10.10, with the dots under it as loading.( in the middle of the screen)

then...

gave up waiting for the root device. common problem
-boot args ( cat /proc/cmdline)
      -check rootdelay=(did the system wait long enough?)
      -check root=(did the system wait for the right device?)
-Missing modules (cat /proc/modules, ls /dev

ALERT! /dev/disk/by-uuid/d948dc54-e658-4dfb-8ff3-67464accd05e does not exist.

Dropping to shell!

BusyBox v1.15.3 (ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)

enter ´help´for a list of built-in commands


-- ok, thats all i get.. i hope u are as confused as me
lol

oh yes, grub loads any of the 3 windows partitions, sda1, sda2, sdg1..

---

### Post by coffeecat on 2011-04-10
> **amerinde said:**
> 
ALERT! /dev/disk/by-uuid/d948dc54-e658-4dfb-8ff3-67464accd05e does not exist.

Which, of course, it does. 

Which means that the underlying problem, whatever it is, is confusing the output.

The only sensible thing I can suggest is that the installation got itself corrupted. Dropping to a busybox shell is usually indicative of something serious. Since this is a brand-new install I would suggest simply re-installing.

Before you do so, check the md5sum of the downloaded ISO, and did you burn the CD at low speed? If you start the CD and tap any key when the two small icons appear at the bottom of the screen, you will get the old-style menu. Third on the list, iirc, is a CD integrity check. That's worth doing. You need to be sure both the ISO and CD are OK before installing.

Also - see what the others say.

---

### Post by amerinde on 2011-04-10
it is on a usb stick, it runs fine live, thats why i decided to install it. it actually runs great, off the stick, just slow. and no, i didnt check the mdm... this was actually my second install, had the same problem the first time. i will download another and check that and go to cd..

---

### Post by drs305 on 2011-04-10
Note: This entry was composed before I read the previous two posts, which were made while I was writing this post.

From the Grub2 menu, first go to the G2 prompt by pressing 'c'.

At the prompt, type:
```
ls (hd0,5)/boot/grub
ls (hd0,5)/

```
Does it see the files in /boot/grub? 
If not, the second command. Does it see the normal Ubuntu folders?

If yes, then ESC back to the menu, highlight the first entry, and press 'e' to edit the entry. Use the cursors/DEL key and keyboard to make these changes. Entries to add are **bold**, lines to [s]delete[/s] hold down the DEL key. Once you have made the changes, press CTRL-x to boot. If it boots, run "sudo update-grub" to update the menu.


> 
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
[s]    [COLOR="DarkRed"]search --no-floppy --fs-uuid --set d948dc54-e658-4dfb-8ff3-67464accd05e[/COLOR][/s]
    linux    /boot/vmlinuz-2.6.35-28-generic [s][COLOR="DarkRed"]root=UUID=d948dc54-e658-4dfb-8ff3-67464accd05e[/COLOR][/s] **[COLOR="DarkRed"]root=/dev/sda5[/COLOR]** ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}

---

### Post by amerinde on 2011-04-10
ok, i tried the commands you gave me. this was what all i saw on my screen:

grub>ls (hd0,5) /boot/grub
partition hd0,5: file system type ext2- Last modification time
2011-04-10 19:06:27 Sunday, UUID d948dc54-e658-4df6-8ff3-6746accd05e

grub>ls (hd0,5) /
partition hd0,5: file system type ext2- Last modification time
2011-04-10 19:06:27 Sunday, UUID d948dc54-e658-4df6-8ff3-6746accd05e

---

### Post by drs305 on 2011-04-10
> **amerinde said:**
> ok, i tried the commands you gave me. this was what all i saw on my screen:

grub>ls (hd0,5) /boot/grub
partition hd0,5: file system type ext2- Last modification time
2011-04-10 19:06:27 Sunday, UUID d948dc54-e658-4df6-8ff3-6746accd05e

grub>ls (hd0,5) /
partition hd0,5: file system type ext2- Last modification time
2011-04-10 19:06:27 Sunday, UUID d948dc54-e658-4df6-8ff3-6746accd05e

If you typed it as you posted, you have added a space between (hd0,5) and /boot/grub. It should all be together, with no spaces except between "ls" and "(hd0,5)/boot/grub".

---

### Post by amerinde on 2011-04-10
solved..

thanks coffecat, 

i tried to install 2 times from my live USB, but it must of been corrupt, i dont know why it worked so good. I down loaded a new iso and did a 3rd install by cd, and now all works.

---

### Post by Dutch70 on 2011-04-15
Please mark the thread solved so others with the same issue can find your thread and possibly get theirs taken care of also. See my sig for "how to mark your thread solved".

---

