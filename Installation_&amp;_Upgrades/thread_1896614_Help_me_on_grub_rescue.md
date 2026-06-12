---
title: "Help me on grub rescue"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by rohhaan on 2011-12-17
Help, I'm so out of my depth here!
I have a desktop with dual os windows XP and Ubuntu 10.04 on it.
I've been using them fine for the past year or so, today while i was trying to recover some deleted files with testdisk during the rebooting process suddenly power failed for few seconds.
Now when ever i switch it on i get message 
[COLOR=Red]error : no such partition
          grub rescue >[/COLOR]

Now all I can get (unless I boot from the CD) is a GRUB RESCUE prompt.
 
after running boot_loader_script.sh command i got following result.txt


     ```
             Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 8 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda6 starts at sector 37977723. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda7 starts at sect]or 57448503. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    18,506,879    18,506,817   c W95 FAT32 (LBA)
/dev/sda2          18,506,943    25,788,038     7,281,096   c W95 FAT32 (LBA)
/dev/sda3          25,788,416    37,343,231    11,554,816  83 Linux
/dev/sda4          37,343,250    78,252,614    40,909,365   f W95 Extended (LBA)
/dev/sda5          37,345,280    37,976,047       630,768  82 Linux swap / Solaris
/dev/sda6          37,977,723    57,448,439    19,470,717   c W95 FAT32 (LBA)
/dev/sda7          57,448,503    78,220,484    20,771,982   c W95 FAT32 (LBA)

/dev/sda4 ends after the last sector of /dev/sda

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        D468-8224                              vfat       
/dev/sda2        150A-3124                              vfat       
/dev/sda3        87091611-e9ba-4ff6-8030-b68b1f7498f5   ext4       
/dev/sda5        b41ddd04-c5bd-4a88-ba76-bc04a25da13f   swap       
/dev/sda6        50CE-D7BC                              vfat       
/dev/sda7        9422-2618                              vfat       &#8240;PNG  
/dev/sdb         DC63-0000                              vfat       
/dev/sdc         3F53-75BC                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/D468-8224         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda2        /media/150A-3124         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda3        /media/87091611-e9ba-4ff6-8030-b68b1f7498f5 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb         /media/DC63-0000         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc         /media/3F53-75BC         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=87091611-e9ba-4ff6-8030-b68b1f7498f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=87091611-e9ba-4ff6-8030-b68b1f7498f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d468-8224
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=87091611-e9ba-4ff6-8030-b68b1f7498f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=b41ddd04-c5bd-4a88-ba76-bc04a25da13f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  15.032760620 = 16.141303808   boot/grub/core.img                             1
  16.947658539 = 18.197409792   boot/grub/grub.cfg                             1
  16.240234375 = 17.437818880   boot/initrd.img-2.6.32-21-generic              2
  15.769378662 = 16.932241408   boot/vmlinuz-2.6.32-21-generic                 1
  16.240234375 = 17.437818880   initrd.img                                     2
  15.769378662 = 16.932241408   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 10 2a 00  |.Z.MSWIN4.1...*.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 bf 64 1a 01  |........?....d..|
00000020  c8 19 6f 00 e2 0d 00 00  00 00 00 00 02 00 00 00  |..o.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 24 31 0a 15 4e  4f 20 4e 41 4d 45 20 20  |..)$1..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown BootLoader on sda4

00000000  b8 b4 ed ed cd 35 05 4f  79 56 6e 1a d8 59 92 e7  |.....5.OyVn..Y..|
00000010  93 ef dc e9 d4 e1 8e e7  57 86 8b 35 69 51 40 29  |........W..5iQ@)|
00000020  a5 f5 7d c6 6a ee d5 a9  ad 9a 3d aa 90 80 1d 0b  |..}.j.....=.....|
00000030  aa 7c 5f ee e6 ce 55 e2  28 75 cf ef 8a ac 53 d1  |.|_...U.(u....S.|
00000040  b6 21 a7 98 f9 80 84 39  a0 be b8 53 79 f1 f2 2f  |.!.....9...Sy../|
00000050  12 74 31 6c 03 9f ae c5  02 ea 34 4f bc 76 46 80  |.t1l......4O.vF.|
00000060  5b 28 79 49 88 a9 04 44  ba e2 19 bf 08 4e ba 82  |[(yI...D.....N..|
00000070  96 b3 1e 9c c7 61 56 6d  cb 5d 27 cc 68 a4 68 dc  |.....aVm.]'.h.h.|
00000080  b4 88 5c d5 a1 37 eb e7  10 9a c3 5a fb b8 57 ce  |..\..7.....Z..W.|
00000090  c8 16 46 41 f7 e3 56 c7  b2 b4 37 58 c0 99 fd 42  |..FA..V...7X...B|
000000a0  21 fb 69 50 35 b2 74 3f  43 68 9b 78 17 9e 02 ad  |!.iP5.t?Ch.x....|
000000b0  6e ab 0f 0d 5c 7d 8d 9d  35 b1 44 2b 3e 75 a5 00  |n...\}..5.D+>u..|
000000c0  ee ec 5f 62 fe 26 48 92  e7 41 6b 4b ad b7 01 8c  |.._b.&H..AkK....|
000000d0  08 2c dd b9 6f 13 05 82  c7 23 d5 af 09 20 5e a9  |.,..o....#... ^.|
000000e0  21 3f 0a 85 ff af 80 75  44 53 03 f2 49 77 8d 65  |!?.....uDS..Iw.e|
000000f0  6a 26 55 cc 81 26 2b b0  48 9b c0 99 10 bc 4f 34  |j&U..&+.H.....O4|
00000100  c6 75 3b b4 50 06 d8 b8  5a 79 80 d9 78 36 95 27  |.u;.P...Zy..x6.'|
00000110  a5 f4 95 cb 9f 8a 1d 3f  ed 38 fa ec 95 20 82 16  |.......?.8... ..|
00000120  a5 80 31 36 c5 52 cb 08  bb c1 cb 85 9a 9d 85 91  |..16.R..........|
00000130  e5 6a 0e 6d 08 3e 61 bf  b0 a9 0e 03 3d 12 28 62  |.j.m.>a.....=.(b|
00000140  26 03 f4 b1 b7 54 23 0c  b4 8d 92 99 f5 ce a0 68  |&....T#........h|
00000150  53 f2 1c f9 1d db 49 42  a5 0f de a6 bf 53 b2 54  |S.....IB.....S.T|
00000160  15 66 16 13 d6 b9 19 8a  ec 8d 7d 63 2b 25 40 96  |.f........}c+%@.|
00000170  c2 a9 29 89 68 c4 13 81  ba d1 aa 13 47 77 63 ac  |..).h.......Gwc.|
00000180  9e ff 8f ac 23 f3 0c e8  d1 63 88 e1 be c0 d3 08  |....#....c......|
00000190  30 c4 2c cf 74 3e ce d0  b1 6a b4 1b ba 11 e0 2f  |0.,.t>...j...../|
000001a0  7f 25 aa 56 70 ff c8 88  a6 61 91 b4 6c 09 62 1c  |.%.Vp....a..l.b.|
000001b0  22 31 cb 0e 7f 34 34 fc  c2 30 c0 56 3c f6 00 fe  |"1...44..0.V<...|
000001c0  ff ff 82 fe ff ff ee 07  00 00 f0 9f 09 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 2a ae  09 00 bc 19 29 01 00 00  |......*.....)...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

now i request you pupil to help me on this.

thanx & regards.

naresh

---

### Post by coffeecat on 2011-12-17
Hi and welcome to the forum. This is what has caused your problem:

> **rohhaan said:**
> i was trying to recover some deleted files with testdisk during the rebooting process suddenly power failed for few seconds.

Testdisk is for recovering lost partitions, not lost files. Photorec, which comes with testdisk is for lost files. Anyway, testdisk appears to have rewritten your partition table and "converted" your logical sda8 partition, your Ubuntu root partition, into a primary partition, now designated sda3. Grub is still looking for sda8, but can't find it.

I suggest you try reinstalling grub. Boot up with the Ubuntu live CD - you need to use the 10.04 one to be compatible with the grub 1.97 you have installed already - choose "try Ubuntu" to get to the live desktop and run these two terminal commands:

```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and see if you can now bootup.

BUT - testdisk has introduced another and more subtle error. I'll post about this separately, so as not to confuse things. Try the grub re-install first.

---

### Post by coffeecat on 2011-12-17
@rohhaan, this is the other problem that testdisk has introduced (from your boot script output):

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total [COLOR="Red"]78242976[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    18,506,879    18,506,817   c W95 FAT32 (LBA)
/dev/sda2          18,506,943    25,788,038     7,281,096   c W95 FAT32 (LBA)
/dev/sda3          25,788,416    37,343,231    11,554,816  83 Linux
/dev/sda4          37,343,250   [COLOR="Red"] 78,252,614 [/COLOR]   40,909,365   f W95 Extended (LBA)
/dev/sda5          37,345,280    37,976,047       630,768  82 Linux swap / Solaris
/dev/sda6          37,977,723    57,448,439    19,470,717   c W95 FAT32 (LBA)
/dev/sda7          57,448,503    78,220,484    20,771,982   c W95 FAT32 (LBA)

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```

The final sector of your extended partition (now sda4) is shown in the partition table as coming outside of the physical end of the drive - which is of course impossible. Testdisk is known to do this.

What is interesting is that your sda3 partition, formerly sda8, comes before all the logical partitions - sda5 to sda7. When it was sda8 it was a logical partition and the start sector of the extended partition would have included it. But what was sda8 would have been the first logical partition - hence the logical partitions were out of numerical order. This does not usually matter, but is what may have confused testdisk.

Anyway - the practical problem is that the erroneous end sector for sda4 will confuse Gparted and other applications. So long as the commands in my previous post work for you, you will be able to boot into Ubuntu despite the partition table irregularity, but this may become a problem further down the line. You need to fix it now. And to fix it you need fixparts. See this:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

A word of caution. Depending on what you do with fixparts, it *may* convert your current sda3 partition back into a logical one, with a different partition number. Which will confuse the re-installed grub. I suggest we take this one step at a time, which is why I've posted over two posts. See if you can repair grub first, and then think about using fixparts.

---

### Post by rohhaan on 2011-12-17
thanxs coffeecat :) i have completed 1st step and its successful now i am able to boot my pc 

i could not understand your 2nd suggestion kindly guide me to overcome this problem too.

once again thanx

---

### Post by coffeecat on 2011-12-17
OK, have a careful read-through of the fixparts link. This is the important bit:

> It can repair mis-sized extended partitions. These partitions normally serve as placeholders for logical partitions, but some partitioning tools miscompute the size of the extended partition, which can cause problems. FixParts is designed in such a way that this type of repair occurs automatically, so if it's the only problem with your disk, you can launch the program and then immediately save the partition table (as described in the upcoming section Saving Your Changes), making no manual changes, and the program will fix the problem. 

That covers your situation. I read that as meaning that it will detect the extended partition end sector irregularity and fix it automatically. However, if you are more ambitious, you can use fixparts to convert your sda3 partition back to a logical one (which it was originally), but this will cause the partition number to change again (logical partitions are always numbered 5 and upwards) and may cause problems with grub again. That would be easily fixed, but you need to know in advance.

The reason I'm being a little bit cagey about what will happen with fixparts is because, although I've used it, it's not the sort of software I use every day! :wink: So I'm going partly from memory and partly from what is in that tutorial.

Try running fixparts and back out if you are uncertain. If you run it and get a grub error again, simply run the boot script, post the output and I can tell you how to amend the grub-install commands I posted earlier.

---

### Post by rohhaan on 2011-12-18
cofeecat iam unable to download fixparts when i try to download fixparts i endedup downloading [COLOR="DarkRed"]gptfdisk-0.8.1[/COLOR] and there is a warning on fixparts tutorial page :-

[COLOR="rgb(139, 0, 0)"]Warning

Do not use gdisk if you want to use FixParts! More than one person has made that mistake, despite explicit advice to use FixParts. Unlike FixParts, gdisk is designed to work on GUID Partition Table (GPT) disks, and it will automatically convert from MBR to GPT format. This will have the effect of fixing the problems that FixParts fixes, but in most cases, and especially if Windows boots from the disk, such a conversion is inappropriate.[/COLOR]

so tell me what to do.

thanxs and regards.

---

### Post by coffeecat on 2011-12-18
Don't, whatever you do, run gdisk. You could end up converting your partition table to a GUID one, which you don't want.

The link to the fixparts download is there on the page I linked earlier, but here it is:

[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.0/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.0/fixparts-binaries/)

If you want to run fixparts in Ubuntu, download the .deb package, but make sure you download the correct one - i386 for 32-bit or amd64 for 64-bit. Or if you want to run fixparts in Windows, there's a zip for the Windows version on that page.

---

### Post by rohhaan on 2011-12-18
dear cofeecat i have downloaded and run fixparts it has write the mbr after saving changes i am able to boot my system now please chek the result txt from boot info script and tell if my problem is solved ?


```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda4 and looks at sector 1 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda6 starts at sector 37977723. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda7 starts at sector 57448503. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    18,506,879    18,506,817   c W95 FAT32 (LBA)
/dev/sda2          18,506,943    25,788,038     7,281,096   c W95 FAT32 (LBA)
/dev/sda3          25,788,416    37,343,231    11,554,816  83 Linux
/dev/sda4          37,345,279    78,220,484    40,875,206   f W95 Extended (LBA)
/dev/sda5          37,345,280    37,976,047       630,768  82 Linux swap / Solaris
/dev/sda6          37,977,723    57,448,439    19,470,717   c W95 FAT32 (LBA)
/dev/sda7          57,448,503    78,220,484    20,771,982   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D468-8224                              vfat       
/dev/sda2        150A-3124                              vfat       
/dev/sda3        87091611-e9ba-4ff6-8030-b68b1f7498f5   ext4       
/dev/sda5        b41ddd04-c5bd-4a88-ba76-bc04a25da13f   swap       
/dev/sda6        50CE-D7BC                              vfat       
/dev/sda7        9422-2618                              vfat       &#8240;PNG
 
/dev/sdb         DC63-0000                              vfat       
/dev/sdc         3F53-75BC                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb         /media/DC63-0000         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc         /media/3F53-75BC         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=87091611-e9ba-4ff6-8030-b68b1f7498f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=87091611-e9ba-4ff6-8030-b68b1f7498f5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 87091611-e9ba-4ff6-8030-b68b1f7498f5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d468-8224
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=87091611-e9ba-4ff6-8030-b68b1f7498f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=b41ddd04-c5bd-4a88-ba76-bc04a25da13f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.693660736 = 15.777198080   boot/grub/core.img                             1
  16.947658539 = 18.197409792   boot/grub/grub.cfg                             1
  16.240234375 = 17.437818880   boot/initrd.img-2.6.32-21-generic              2
  15.769378662 = 16.932241408   boot/vmlinuz-2.6.32-21-generic                 1
  16.240234375 = 17.437818880   initrd.img                                     2
  15.769378662 = 16.932241408   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 10 2a 00  |.Z.MSWIN4.1...*.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 bf 64 1a 01  |........?....d..|
00000020  c8 19 6f 00 e2 0d 00 00  00 00 00 00 02 00 00 00  |..o.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 24 31 0a 15 4e  4f 20 4e 41 4d 45 20 20  |..)$1..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200
```


thanx and regards.

---

### Post by coffeecat on 2011-12-18
> **rohhaan said:**
>  please chek the result txt from boot info script and tell if my problem is solved ?

It is indeed. This is the important bit:


```
Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total [COLOR="Red"]78242976[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    18,506,879    18,506,817   c W95 FAT32 (LBA)
/dev/sda2          18,506,943    25,788,038     7,281,096   c W95 FAT32 (LBA)
/dev/sda3          25,788,416    37,343,231    11,554,816  83 Linux
/dev/sda4          37,345,279    [COLOR="Red"]78,220,484[/COLOR]    40,875,206   f W95 Extended (LBA)
/dev/sda5          37,345,280    37,976,047       630,768  82 Linux swap / Solaris
/dev/sda6          37,977,723    57,448,439    19,470,717   c W95 FAT32 (LBA)
/dev/sda7          57,448,503    78,220,484    20,771,982   c W95 FAT32 (LBA)
```

Fixparts has done the job. The end sector of your extended partition is now recorded as inside the physical drive.

I think everything is fixed now if you can boot up OK. Good luck! :)

By the way, I added code tags to your boot script output so that there is not a wall of text.

---

### Post by rohhaan on 2011-12-19
thanx a lot cofeecat i think every thing is alright now. you were a great help.

regards.:D

---

