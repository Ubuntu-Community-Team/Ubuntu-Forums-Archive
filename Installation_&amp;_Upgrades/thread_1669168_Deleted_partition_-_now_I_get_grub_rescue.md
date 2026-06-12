---
title: "Deleted partition - now I get grub rescue"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by bugrake on 2011-01-17
Hi,

I set up my Dell Inspiron Laptop as Dual Boot -> Xp / Ubuntu 10.04. - all worked well.

I had 2 installations of XP on this machine and I removed one - all worked well.

I then went into XP and deleted the partion (4) that the old XP had resided on (using Easeus Partition Master) 
  
All NOT working well !!

Now when booting the machine I get 

grub rescue>

I did ls and got ....

```


(hd0) (hd0,6) (hd0,5) (hd0,3) (hd0,2) (hd0,1)


```

I used an Ubuntu live cd and did $ sudo fdisk -l 

---------------------------------------------------

```
ubuntu@ubuntu:~$ sudo fdisk -ls

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        2697    21583327+   7  HPFS/NTFS
/dev/sda3            6904        7295     3148740   db  CP/M / CTOS / ...
/dev/sda4            4998        6903    15308884+   f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5            4998        6818    14619648   83  Linux
/dev/sda6            6818        6903      688128   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I have seen a lot of entries about recovering and fixing grub2, but will I need to fix the bad partition first? Is there a way to remove it completely or recover it to allow my machine to boot ? 

thanks for any help ..

---

### Post by oldfred on 2011-01-17
Do not know about Easeus Partition Master, but it may have reorganized the partition numbers, so grub cannot find the correct partition?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by bugrake on 2011-01-17
Contents of Results.txt

```
   
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650    43,327,304    43,166,655   7 HPFS/NTFS
/dev/sda3         110,896,695   117,194,174     6,297,480  db CP/M / CTOS / ...
/dev/sda4          80,277,335   110,895,103    30,617,769   f W95 Ext d (LBA)
/dev/sda5          80,277,504   109,516,799    29,239,296  83 Linux
/dev/sda6         109,518,848   110,895,103     1,376,256  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        07D5-0817                              vfat       DellUtility                   
/dev/sda2        282098AE2098848A                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2254ec63-58a1-494d-aa5b-5b6f4a1a7770   ext4                                     
/dev/sda6        6353e584-b48e-440d-88ab-a461dc29feec   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
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
search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2254ec63-58a1-494d-aa5b-5b6f4a1a7770 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2254ec63-58a1-494d-aa5b-5b6f4a1a7770 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2254ec63-58a1-494d-aa5b-5b6f4a1a7770 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2254ec63-58a1-494d-aa5b-5b6f4a1a7770 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2254ec63-58a1-494d-aa5b-5b6f4a1a7770
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d5-0817
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 282098ae2098848a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=2254ec63-58a1-494d-aa5b-5b6f4a1a7770 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6353e584-b48e-440d-88ab-a461dc29feec none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  45.5GB: boot/grub/core.img
  51.9GB: boot/grub/grub.cfg
  45.5GB: boot/initrd.img-2.6.32-21-generic
  45.6GB: boot/initrd.img-2.6.32-27-generic
  45.5GB: boot/vmlinuz-2.6.32-21-generic
  45.6GB: boot/vmlinuz-2.6.32-27-generic
  45.6GB: initrd.img
  45.5GB: initrd.img.old
  45.6GB: vmlinuz
  45.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  c7 ce 1c 2a cc f5 2c 69  a6 88 44 ca 4a 9c 69 94  |...*..,i..D.J.i.|
00000010  31 58 af a1 65 de 71 8e  65 17 20 fa fb 5f 8b 04  |1X..e.q.e. .._..|
00000020  55 69 fc 63 59 fc 99 89  81 f0 9c 31 87 09 29 ed  |Ui.cY......1..).|
00000030  6c fe af e0 8d cf 65 1d  a9 bf 08 6b 3d 90 83 75  |l.....e....k=..u|
00000040  b1 dc 41 71 8c 47 b6 04  14 ca 27 aa b6 a1 ec c6  |..Aq.G....'.....|
00000050  9a 97 50 13 ea 92 70 5a  6a 15 f5 e5 2c b9 5d 99  |..P...pZj...,.].|
00000060  85 70 ce 2a d3 e2 97 b9  87 de d5 3f b4 03 37 50  |.p.*.......?..7P|
00000070  68 2a 38 fc f9 0c 4b f8  ce 47 18 95 52 e8 1e 0d  |h*8...K..G..R...|
00000080  06 13 eb cd 89 bb 4b 07  9d 41 62 57 a4 5a 57 c3  |......K..AbW.ZW.|
00000090  2a 88 11 54 7c 35 62 d5  19 b6 88 47 10 ff e3 3c  |*..T|5b....G...<|
000000a0  f3 9a a0 f6 ff ca 33 06  bd b7 2e d2 aa 69 0d 51  |......3......i.Q|
000000b0  bb 61 7d cb e6 c5 25 39  03 18 28 b2 21 bc e2 19  |.a}...%9..(.!...|
000000c0  40 f5 59 4d 41 3b e3 e0  31 14 68 d3 ab fd 63 60  |@.YMA;..1.h...c`|
000000d0  d8 64 b9 09 1c fd 15 6e  0e 0d 65 91 e5 80 3d c9  |.d.....n..e...=.|
000000e0  6a 06 69 01 78 c9 e8 e9  24 db 26 11 6f 9f 7b 04  |j.i.x...$.&.o.{.|
000000f0  e4 43 a5 44 71 de a5 ce  1f b8 2b 93 e6 29 3e 36  |.C.Dq.....+..)>6|
00000100  47 a2 22 bd 7e 29 4f 0d  a6 c8 0f 4e 46 0f 8c 7a  |G.".~)O....NF..z|
00000110  83 87 82 3c b5 51 9e ad  64 c6 16 c6 21 b5 ed 1c  |...<.Q..d...!...|
00000120  ef 82 34 21 7f 12 8b 52  de 87 15 2d c2 4c 4f 65  |..4!...R...-.LOe|
00000130  3d 3e 66 dd 71 2e 21 e3  42 2b 45 84 33 41 e8 1c  |=>f.q.!.B+E.3A..|
00000140  8b 3d 02 6d 30 8d 6d d4  52 2a d3 16 43 88 5e e9  |.=.m0.m.R*..C.^.|
00000150  63 99 6d 8c 7d c1 15 b2  73 46 76 0f de f8 75 e5  |c.m.}...sFv...u.|
00000160  57 3a 3f e9 26 31 82 cc  aa 34 f0 88 51 e0 a4 7f  |W:?.&1...4..Q...|
00000170  21 7c 80 a1 f7 12 67 b0  f8 23 18 7d a2 05 01 9c  |!|....g..#.}....|
00000180  de 35 43 53 a5 df 2c ef  ab 8a c0 de d1 6d 69 48  |.5CS..,......miH|
00000190  08 9b 26 5e 53 79 df 7d  bb f0 6c 14 8e bd 4c 56  |..&^Sy.}..l...LV|
000001a0  95 c8 d0 95 0c cf 95 9b  c3 43 1a fe 29 ee fa 87  |.........C..)...|
000001b0  f3 59 44 9f c8 f0 72 09  6a 92 2c e1 6e d9 00 0b  |.YD...r.j.,.n...|
000001c0  c7 ff 83 1a f9 ff a9 00  00 00 00 28 be 01 00 3a  |...........(...:|
000001d0  db ff 05 e5 ef ff 6a 30  be 01 3f 00 15 00 00 00  |......j0..?.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```


thanks !

---

### Post by oldfred on 2011-01-17
It must have changed numbers, grub2 is looking into partition #6 but your install is now in #5.

You should just have to reinstall  grub2.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by bugrake on 2011-01-17
Ok - that worked !  

I am now able to start up XP and ubuntu - many thanks

Is there a way to fix partition 4 - it still looks sick to me? It seems to be unallocated.  Ideally I would like to  extend sda5 to include this space, but otherwise make it directlyaccessible to my ubuntu system

```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        2697    21583327+   7  HPFS/NTFS
/dev/sda3            6904        7295     3148740   db  CP/M / CTOS / ...
/dev/sda4            4998        6903    15308884+   f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5            4998        6818    14619648   83  Linux
/dev/sda6            6818        6903      688128   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by wilee-nilee on 2011-01-17
sda4 is the extended partition, which is allowing you to have a additional logical partition for the Linux and swap it is not taking up extra space. It also is not broken, you have 3 primary partitions.
```
dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650    43,327,304    43,166,655   7 HPFS/NTFS
/dev/sda3         110,896,695   117,194,174     6,297,480  db CP/M / C
```

The maximum is 4 primaries, the extended allows you to have more logicals which Ubuntu can boot from.

Windows cannot boot from a extended, but will see a NTFS shared if put inside.

Notice the numbers where the etx4 and ext5 start and end.
```
/dev/sda4          **80,277,335**   **110,895,103**    30,617,769   f W95 Ext d (LBA)
/dev/sda5          **80,277,504**   109,516,799    29,239,296  83 Linux
/dev/sda6         109,518,848   **110,895,103**     1,376,256  82 Linux swap / Solaris
```

---

### Post by bugrake on 2011-01-17
Aha,  I see. It is partition 3 that is unallocated not 4.  

I ran gparted for the first time and this shows better how the partitions are organised - it's all new to me! I will check out  other threads to reorg these.  At least I am back up and running. 

Thanks for the speedy replies.

---

