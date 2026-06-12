---
title: "Re-Installing GRUB"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by jakeargent on 2010-02-20
A few weeks ago I've installed Windows7 on my PC. It had Ubuntu (9.10) and WinXP before.

After that, I can't boot into ubuntu since GRUB is gone, and MS' default bootloader doesn't recognize linux. Now I want to reinstall GRUB.

Is there a way to do it without losing any data, and if there's what is it?

---

### Post by darkod on 2010-02-20
Yes, absolutely. Just follow the instructions here and make sure to use the instructions for 9.10 if this was a clean install because you would have grub2.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kansasnoob on 2010-02-20
If you have an Ubuntu Live CD boot it choosing to try Ubuntu "without changes" and from the Live Desktop run the Boot Info Script and post the results as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That will tell us a lot and we can proceed from there.

---

### Post by kansasnoob on 2010-02-20
> **darkod said:**
> Yes, absolutely. Just follow the instructions here and make sure to use the instructions for 9.10 if this was a clean install because you would have grub2.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Beat me to the punch by a few seconds :D

---

### Post by darkod on 2010-02-20
> **kansasnoob said:**
> Beat me to the punch by a few seconds :D

:-\"

---

### Post by jakeargent on 2010-02-20
I used the guide darkod linked; however it didn't work.

Here's the content of the trial;

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde1dde1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6425    51608781    7  HPFS/NTFS
/dev/sda2           10072       60800   407480692+   f  W95 Ext'd (LBA)
/dev/sda3            6426        9944    28266367+  83  Linux
/dev/sda4            9945       10071     1020127+  82  Linux swap / Solaris
/dev/sda5           10072       22819   102398278+   7  HPFS/NTFS
/dev/sda6           22820       60800   305082351    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bc84bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156288000    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mkdir /media/sda3
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/sda3
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda3 dev/sda
grub-probe: error: Cannot stat `dev/sda'
Invalid device `dev/sda'.
Try ``grub-setup --help'' for more information.
```

[hr]

As to the boot info script;

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub  is installed in the MBR of /dev/sdb and looks at sector 67870383 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde1dde1d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   103,217,624   103,217,562   7 HPFS/NTFS
/dev/sda2         161,790,615   976,751,999   814,961,385   f W95 Ext d (LBA)
/dev/sda5         161,790,678   366,587,234   204,796,557   7 HPFS/NTFS
/dev/sda6         366,587,298   976,751,999   610,164,702   7 HPFS/NTFS
/dev/sda3         103,217,625   159,750,359    56,532,735  83 Linux
/dev/sda4         159,750,360   161,790,614     2,040,255  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4bc84bc7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   312,578,047   312,576,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        68B8B718B8B6E42A                       ntfs                                     
/dev/sda3        7ccdffdb-eb4f-45da-8afb-3f6f3902125c   ext4                                     
/dev/sda4        9507a507-f8a8-4d53-97e1-33bb43324b32   swap                                     
/dev/sda5        4CC604BFC604AB72                       ntfs       Module Management System      
/dev/sda6        C8C87541C8752EB6                       ntfs       Life Support System           
/dev/sdb1        ACAEB586AEB54A1A                       ntfs       Müzik                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda3        /media/sda3              ext4       (rw)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set 7ccdffdb-eb4f-45da-8afb-3f6f3902125c
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7ccdffdb-eb4f-45da-8afb-3f6f3902125c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7ccdffdb-eb4f-45da-8afb-3f6f3902125c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7ccdffdb-eb4f-45da-8afb-3f6f3902125c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7ccdffdb-eb4f-45da-8afb-3f6f3902125c ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7ccdffdb-eb4f-45da-8afb-3f6f3902125c
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=7ccdffdb-eb4f-45da-8afb-3f6f3902125c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7ccdffdb-eb4f-45da-8afb-3f6f3902125c
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=7ccdffdb-eb4f-45da-8afb-3f6f3902125c ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7ccdffdb-eb4f-45da-8afb-3f6f3902125c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7ccdffdb-eb4f-45da-8afb-3f6f3902125c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7ccdffdb-eb4f-45da-8afb-3f6f3902125c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7ccdffdb-eb4f-45da-8afb-3f6f3902125c ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4018aac518aab8f4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=7ccdffdb-eb4f-45da-8afb-3f6f3902125c / ext4 errors=remount-ro 0 1
# Entry for /dev/sda4 :
UUID=9507a507-f8a8-4d53-97e1-33bb43324b32 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda6 /media/Life\040Support\040System ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/WinMain ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Module\040Management\040System ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda3: Location of files loaded by Grub: ===================


  54.2GB: boot/grub/core.img
  57.9GB: boot/grub/grub.cfg
  54.5GB: boot/initrd.img-2.6.31-14-generic
  54.7GB: boot/initrd.img-2.6.31-15-generic
  58.1GB: boot/initrd.img-2.6.31-16-generic
  53.5GB: boot/vmlinuz-2.6.31-14-generic
  53.9GB: boot/vmlinuz-2.6.31-15-generic
  54.3GB: boot/vmlinuz-2.6.31-16-generic
  58.1GB: initrd.img
  54.7GB: initrd.img.old
  54.3GB: vmlinuz
  53.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  a7 ef aa 2e 2f 97 df 5e  6f aa 57 17 40 d0 ed 1e  |..../..^o.W.@...|
00000010  5b 1a 60 30 71 1c 6c 6a  0b 2f a4 ad 13 07 44 8e  |[.`0q.lj./....D.|
00000020  0a 69 56 9e 19 92 d6 82  c2 44 e9 a1 f0 5d 5d 18  |.iV......D...]].|
00000030  79 e0 53 ee f5 cf 82 22  41 a3 64 92 3a 0e 46 4a  |y.S...."A.d.:.FJ|
00000040  b9 87 25 b7 62 73 44 c4  43 27 15 18 f8 45 97 98  |..%.bsD.C'...E..|
00000050  df 67 3d a0 a6 f0 19 5d  5d db ac 47 0f a7 bd eb  |.g=....]]..G....|
00000060  55 81 ae ec b6 e7 91 d6  7a 23 74 ff 56 14 0c c4  |U.......z#t.V...|
00000070  6a 95 97 0f 64 9f f7 95  a6 b7 20 13 a3 c5 68 c1  |j...d..... ...h.|
00000080  8e 4b 28 30 19 e7 84 65  55 48 f0 19 12 88 08 4a  |.K(0...eUH.....J|
00000090  80 a6 7a 91 50 63 1e cb  6d 91 63 27 c2 9b 41 de  |..z.Pc..m.c'..A.|
000000a0  5a 86 0b 14 36 30 98 be  10 04 a6 8a 9c 46 99 a5  |Z...60.......F..|
000000b0  72 7a 07 cb e7 87 80 a1  12 fe a9 95 54 7f f0 42  |rz..........T..B|
000000c0  b4 0b 8f bc a0 bb f8 c0  f6 7c f0 8b 0e 7a 69 38  |.........|...zi8|
000000d0  14 cb bb 9a 04 19 41 09  5f bd a0 c3 a1 ff b7 90  |......A._.......|
000000e0  0d f9 a0 3a b6 7f 84 01  8d f2 ae a9 c9 ff 28 be  |...:..........(.|
000000f0  fe fd 45 9e 56 b2 f6 e7  b1 66 dc 44 2a 4a 93 2c  |..E.V....f.D*J.,|
00000100  8a 3d 39 6d 6b 72 44 d2  1a f7 a7 1c dd b0 2e 6d  |.=9mkrD........m|
00000110  b7 33 90 05 ce 93 bb 4a  7c 29 db 80 2a fc 74 96  |.3.....J|)..*.t.|
00000120  b0 de 04 5e d8 20 51 68  ec 32 6d 91 5b 1b 9b c8  |...^. Qh.2m.[...|
00000130  5e 9b a7 39 58 6d cf bb  b9 4b da cd 0d b8 6c 9c  |^..9Xm...K....l.|
00000140  14 df 55 43 0f 4d 03 11  26 f6 8a be 19 61 2c 18  |..UC.M..&....a,.|
00000150  05 35 52 ad 59 7f 5b 25  ca 82 c2 b1 60 bf d0 47  |.5R.Y.[%....`..G|
00000160  ce 34 a7 81 49 37 a7 1e  0a 3b bd 34 a1 24 a2 3e  |.4..I7...;.4.$.>|
00000170  68 e0 8d 7a 3b 3e 03 41  49 5a 7e 96 93 0f 7b e3  |h..z;>.AIZ~...{.|
00000180  04 10 a0 5e 0a ef aa 8c  f7 44 42 49 84 a0 a2 5c  |...^.....DBI...\|
00000190  9e 2c 85 f3 78 bf 33 ec  86 e6 14 59 bc 1e 83 23  |.,..x.3....Y...#|
000001a0  2e a3 e5 3c 11 3d fa 07  d4 37 df c5 55 33 ba c9  |...<.=...7..U3..|
000001b0  80 29 a6 29 7e 1b db 33  b6 4e 55 0b de 12 2a f5  |.).)~..3.NU...*.|
000001c0  dd b8 a3 f1 4f bf 2c 83  df 5d b3 1a 60 50 0c e7  |....O.,..]..`P..|
000001d0  07 42 d6 eb ca 5a 50 5c  a3 9d f8 96 ae 0f 53 e0  |.B...ZP\......S.|
000001e0  f8 4a df 2a d5 cb c4 bf  e0 31 31 33 5d 96 b9 34  |.J.*.....113]..4|
000001f0  a1 2b 41 3c a4 7d 34 05  3e 99 b7 1b b6 05 c7 d5  |.+A<.}4.>.......|
00000200


```

---

### Post by darkod on 2010-02-20
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda3 [COLOR=Red]dev/sda[/COLOR]

/dev/sda

The rest is fine. And make sure you have the 500GB disk as first option in BIOS hdd boot options because it seems so far you were booting grub off the 160GB disk.

---

### Post by jakeargent on 2010-02-20
@darkod: I hate typos... Thanks a lot.

---

