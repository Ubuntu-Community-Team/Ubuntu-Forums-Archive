---
title: "Grub prompt cannot key anything"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Dextrocardic on 2010-03-06
I have been trying ubantu 9.10 via dual boot (with windows XP) for a while now. Today I decided to wipe out windows and install ubantu only. After I completed the install I get GRUB prompt and I cannot type anything. So I booted from CD again and opened ubantu from disk. ran the boot_info_script as mentioned on other posts here and here is the results. Please help...
 
 
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 2928391 of 
    the same hard drive for core.img, core.img is at this location on /dev/sdb 
    and looks for (UUID=e76d4181-57e6-4524-93fb-ba5fee3b167d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
sdb1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdc1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk
sdc1/Wubi: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab
sdc2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdd1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000
Partition  Boot         Start           End          Size  Id System
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7
Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  63    74,862,899    74,862,837  83 Linux
/dev/sdb2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdb5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris

Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 20.0 GB, 20020396032 bytes
240 heads, 63 sectors/track, 2586 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc37cc37
Partition  Boot         Start           End          Size  Id System
/dev/sdc1    *             63    39,085,199    39,085,137   7 HPFS/NTFS
/dev/sdc2          39,085,200    39,100,319        15,120   f W95 Ext d (LBA)
Empty Partition

Drive: sdd ___________________ _____________________________________________________
Disk /dev/sdd: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18
Partition  Boot         Start           End          Size  Id System
/dev/sdd1    *             32     1,966,079     1,966,048   6 FAT16

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/loop1       a1d76960-3dd1-4b77-bc8d-5271fcb3a3fc   ext4                                     
/dev/sdb1        e76d4181-57e6-4524-93fb-ba5fee3b167d   ext4                                     
/dev/sdb5        ad7b9ac1-595e-448d-8e33-8047aa3d3433   swap                                     
/dev/sdc1        1E6C79396C790CB1                       ntfs       System                        
/dev/sdd1        C57F-37A6                              vfat       UDISK                         
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdd1        /media/UDISK             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== sdb1/boot/grub/grub.cfg: ===========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set e76d4181-57e6-4524-93fb-ba5fee3b167d
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd1,1)
 search --no-floppy --fs-uuid --set e76d4181-57e6-4524-93fb-ba5fee3b167d
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e76d4181-57e6-4524-93fb-ba5fee3b167d ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd1,1)
 search --no-floppy --fs-uuid --set e76d4181-57e6-4524-93fb-ba5fee3b167d
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e76d4181-57e6-4524-93fb-ba5fee3b167d ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e76d4181-57e6-4524-93fb-ba5fee3b167d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ad7b9ac1-595e-448d-8e33-8047aa3d3433 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sdb1: Location of files loaded by Grub: ===================

   1.4GB: boot/grub/core.img
   1.4GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.31-14-generic
   1.5GB: boot/vmlinuz-2.6.31-14-generic
   1.5GB: initrd.img
   1.5GB: vmlinuz
======================== sdc1/Wubi/boot/grub/grub.cfg: ========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
 insmod ntfs
 set root=(hd2,1)
 search --no-floppy --fs-uuid --set 1e6c79396c790cb1
 loopback loop0 /ubuntu/disks/root.disk
 set root=(loop0)
 linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 loop=/ubuntu/disks/root.disk ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
 insmod ntfs
 set root=(hd2,1)
 search --no-floppy --fs-uuid --set 1e6c79396c790cb1
 loopback loop0 /ubuntu/disks/root.disk
 set root=(loop0)
 linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 loop=/ubuntu/disks/root.disk ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###
### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
 insmod ntfs
 set root=(hd1,1)
 search --no-floppy --fs-uuid --set 4648fa4648fa33f1
 drivemap -s (hd0) ${root}
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
============================= sdc1/Wubi/etc/fstab: =============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
================= sdc1/Wubi: Location of files loaded by Grub: =================

   2.4GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: initrd.img
   2.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sdd1
00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 20 08 00  |.<.MSWIN4.1.. ..|
00000010  02 00 02 00 00 f8 f0 00  20 00 40 00 20 00 00 00  |........ .@. ...|
00000020  e0 ff 1d 00 00 00 29 a6  37 7f c5 4e 4f 20 4e 41  |......).7..NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  [EMAIL="|.ar.@u.B.^.Iuw"]|.ar.@u.B.^.Iuw[/EMAIL]..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  [EMAIL="|.A....~...@...U"]|.A....~...@...U[/EMAIL].|
00000200

```

```

---

### Post by meierfra. on 2010-03-07
> Grub 2 is installed in the MBR of /dev/sda and looks at sector 2928391 of
the [COLOR="Red"]same hard drive [/COLOR]for core.img, core.img is at this location on [COLOR="Red"]/dev/sdb [/COLOR]

Grub is looking on the wrong hard drive for the boot files. I suggest to install Grub to the MBR of the Ubuntu drive.

Boot from the Live CD

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```

Reboot. But set your Bios to boot from the 40GB Ubuntu drive. Then  you should boot directly into Ubuntu.

Once you booted into Ubuntu, you should let Grub know about the changes in the boot order:

```
gksudo gedit /boot/grub/device.map
```
change it to

(hd0) [COLOR="Red"]/dev/sdb[/COLOR]
(hd1) [COLOR="Red"]/dev/sda[/COLOR]
(hd2)  /dev/sdc
(hd3)  /dev/sdd

Save and close the file. Back in the terminal

```
sudo update-grub
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate

```

I noticed that you still have Wubi installed on /dev/sdc1.  If you want I can show you how to boot Wubi from the Grub menu and/or how to access the  Wubi files from Ubuntu

---

### Post by Dextrocardic on 2010-03-07
Thank you very much that worked :D... Actually I want to remove windows completely...I had selected erase drive and install when I did Ubuntu install. How can I remove it? so I can reuse the disk space. do I just remove that partition?

---

### Post by meierfra. on 2010-03-07
> Actually I want to remove windows completely...I had selected erase drive and install when I did Ubuntu install.
Everything on the Ubuntu drive got erased. But Wubi wad  on /dev/sdc  and so survived.


> How can I remove it? so I can reuse the disk space. do I just remove that partition? 

Yes. Use gparted to erase all the partitions on /dev/sdc. To use the freed space you will have to create a new ext4 partition and use it as a data partition.

---

