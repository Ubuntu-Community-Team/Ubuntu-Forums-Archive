---
title: "Successful install refuses to boot"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Fu_Manchu on 2010-04-11
Long Story Short
Successfully installed Ubuntu, Computer refuses to boot says no operating system found
 
Dell Inspiron 1501 2 G ram 120 SATA HD 2 AMD athalon 64
 
 
Recently my hard drive died so I purchased a new one, and attempted to install XP on it and partition it so that I could install Ubuntu on it as well 
It formated and partitioned properly the XP failed to install properly. After concluding that it must be something wrong with the disk (lots of scratchs on it) I decided to install 
Ubuntu on the other partition after the install when it told me to restart the screen showed colored pixel garbage, I turned the machine off and on again and got the message failed to find operating system. Thinking this was some XP generated problem I restarted and decided to install U on the whole thing when taken to the partition screen Ubuntu cd said that one partition had XP and the other had Ubuntu I chose the option delete everything and install Ubuntu.
 
This install worked, the computer restarted told me to eject the disk and then failed to boot into ubuntu
 
after pressing the power button there is a dell screen (press f2 set up f12 multiboot)
then black screen with operating system not found 
 
when I use the CD under the test Ubuntu it says that its already installed on the computer 
 
using disk utility 
 
115 GB HD is ubuntu 9.10 says this is bootable
4.9 GB extended
contains logical partitions
-4.9 gb swap space
 
opened help 
searched boot
fixing GRUB boot problems
command line grub
got the message grub isn't installed 
to install type 
did that and it said it removed grub-pc and installed grub 
when tried typing grub into the command line again it said didn't exist then tried to connect online to get archive
 
I stopped to ask for help
tried searching and did not find answer 
 
Thank you for any help you can provide

---

### Post by Fu_Manchu on 2010-04-12
Searched some more, found and ran the boot log from
[http://bootinfoscript.sourceforge](http://bootinfoscript.sourceforge).

I'm not sure how to read it 

on a side note is it possible for me to connect to the internet while running Ubuntu from the CD

Karmic Koala 9.1 is the distribution I'm using



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb26d9c1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   113,756,264   113,756,202  83 Linux
/dev/sda2         113,756,265   234,436,544   120,680,280   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris
/dev/sda6         113,756,391   220,202,954   106,446,564  83 Linux
/dev/sda7         220,203,018   224,829,674     4,626,657  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders, total 3999373 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 245     3,995,711     3,995,467   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        185e4a0b-7d15-475d-83f8-1aebaefd45e3   ext4                                     
/dev/sda5        0499bef2-a78c-4c71-9dbc-d3daa883914a   swap                                     
/dev/sda6        a9f54f25-8a41-4a25-8c0d-45c49ff4cdc1   ext4                                     
/dev/sda7        966fb870-2ac4-4432-af55-459a3c4f978d   swap                                     
/dev/sdb1        CD5D-435A                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/CD5D-435A         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 185e4a0b-7d15-475d-83f8-1aebaefd45e3
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 185e4a0b-7d15-475d-83f8-1aebaefd45e3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=185e4a0b-7d15-475d-83f8-1aebaefd45e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 185e4a0b-7d15-475d-83f8-1aebaefd45e3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=185e4a0b-7d15-475d-83f8-1aebaefd45e3 ro single 
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=185e4a0b-7d15-475d-83f8-1aebaefd45e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0499bef2-a78c-4c71-9dbc-d3daa883914a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.5GB: boot/grub/core.img
   5.5GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: initrd.img
    .1GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set a9f54f25-8a41-4a25-8c0d-45c49ff4cdc1
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
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a9f54f25-8a41-4a25-8c0d-45c49ff4cdc1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a9f54f25-8a41-4a25-8c0d-45c49ff4cdc1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a9f54f25-8a41-4a25-8c0d-45c49ff4cdc1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a9f54f25-8a41-4a25-8c0d-45c49ff4cdc1 ro single 
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
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 185e4a0b-7d15-475d-83f8-1aebaefd45e3
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=185e4a0b-7d15-475d-83f8-1aebaefd45e3 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 185e4a0b-7d15-475d-83f8-1aebaefd45e3
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=185e4a0b-7d15-475d-83f8-1aebaefd45e3 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=a9f54f25-8a41-4a25-8c0d-45c49ff4cdc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=966fb870-2ac4-4432-af55-459a3c4f978d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  58.8GB: boot/grub/core.img
  61.5GB: boot/grub/grub.cfg
  58.8GB: boot/initrd.img-2.6.31-14-generic
  58.8GB: boot/vmlinuz-2.6.31-14-generic
  58.8GB: initrd.img
  58.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 40 01 00  |.<.MSDOS5.0..@..|
00000010  02 00 02 00 00 f8 f5 00  3f 00 40 00 f5 00 00 00  |........?.@.....|
00000020  4b f7 3c 00 80 00 29 5a  43 5d cd 4e 4f 20 4e 41  |K.<...)ZC].NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 53 79 73  |..'..Invalid Sys|
00000190  74 65 6d 20 44 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem Disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 50  72 65 73 73 20 41 6e 79  |d then Press Any|
000001d0  20 4b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | Key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200



```

---

### Post by oldfred on 2010-04-13
I see nothing obvious in your boot info script. You have grub2 and two installs of Ubuntu. It is booting from the second on sda6. 

It seems like the BIOS is not properly seeing the drive or MBR to boot. I would first review all the BIOS settings to make sure they are ok.

---

