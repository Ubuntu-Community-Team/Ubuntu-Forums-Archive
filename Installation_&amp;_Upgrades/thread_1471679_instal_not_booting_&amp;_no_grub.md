---
title: "instal not booting &amp; no grub"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by herveb on 2010-05-03
Hi. I'm coming back to linux after a few years
just tried downloading the latest version of ubuntu and install it on my laptop
got an error message at the end of the installation (an I/O error, dev sr0,sector something)

now when booting i got grub rescue. the only command working are ls and set. commands such as 'linux' or 'boot' show 'unkown command'

typing
ls  (hd0,1) or ls /boot/
results in
unknown filesystem

I tried to reinstall grub using the 3 different methods as in
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)   Reinstalling GRUB 2

got no error message while doing so except when typing sudo grub-install --recheck /dev/sda  
it told me something about being unable to locate ubuntu or something along those lines - sorry i thought i'd remember

... running out of option
is there a possibility to download the latest pre 10.04 stable version? or other way to solve the problem would be appreciated

thanks

---

### Post by oldfred on 2010-05-03
Welcome to the forums:

To see if your install is there run this script from a liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by herveb on 2010-05-04
thanks, here it is. 


```
 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   112,332,799   112,330,752  83 Linux
/dev/sda2         112,334,846   117,209,087     4,874,242   5 Extended
/dev/sda5         112,334,848   117,209,087     4,874,240  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1       4,149,411,341 4,183,042,986    33,631,646  9d Unknown
/dev/sdb3          18,120,708    38,043,651    19,922,944   0 Empty
/dev/sdb4             131,072       262,399       131,328   0 Empty

/dev/sdb1 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6931e6fc-5848-4431-8089-e48ca2374e7b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b119b61e-2f64-4302-848c-166ce54c1e48   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb1: No such file or directory
error: /dev/sdb3: No such file or directory
error: /dev/sdb4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6931e6fc-5848-4431-8089-e48ca2374e7b
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6931e6fc-5848-4431-8089-e48ca2374e7b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6931e6fc-5848-4431-8089-e48ca2374e7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6931e6fc-5848-4431-8089-e48ca2374e7b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6931e6fc-5848-4431-8089-e48ca2374e7b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6931e6fc-5848-4431-8089-e48ca2374e7b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6931e6fc-5848-4431-8089-e48ca2374e7b
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6931e6fc-5848-4431-8089-e48ca2374e7b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b119b61e-2f64-4302-848c-166ce54c1e48 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
  30.2GB: boot/initrd.img-2.6.32-21-generic
  30.2GB: boot/vmlinuz-2.6.32-21-generic
  30.2GB: initrd.img
  30.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  d8 4d 0f 00 00 00 00 00  00 00 00 00 00 00 00 00  |.M..............|
00000010  00 00 00 00 e0 4d 0f 00  00 00 00 00 00 00 00 00  |.....M..........|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 a0 03 08 00  |................|
00000030  00 00 00 00 20 00 00 00  01 05 00 00 00 00 00 05  |.... ...........|
00000040  15 00 00 00 bf 21 9d 69  08 bb 0d fe 52 f7 9e 2d  |.....!.i....R..-|
00000050  ed 03 00 00 01 05 00 00  00 00 00 05 15 00 00 00  |................|
00000060  bf 21 9d 69 08 bb 0d fe  52 f7 9e 2d 01 02 00 00  |.!.i....R..-....|
00000070  63 43 70 c0 67 01 00 00  70 62 00 00 00 00 00 00  |cCp.g...pb......|
00000080  60 01 00 00 01 00 04 80  14 01 00 00 30 01 00 00  |`...........0...|
00000090  00 00 00 00 14 00 00 00  02 00 00 01 02 00 00 00  |................|
000000a0  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
000000b0  20 00 00 00 20 02 00 00  00 00 24 00 ff 01 1f 00  | ... .....$.....|
000000c0  01 05 00 00 00 00 00 05  15 00 00 00 bf 21 9d 69  |.............!.i|
000000d0  08 bb 0d fe 52 f7 9e 2d  ed 03 00 00 43 00 31 00  |....R..-....C.1.|
000000e0  2d 00 34 00 36 00 41 00  41 00 2d 00 31 00 31 00  |-.4.6.A.A.-.1.1.|
000000f0  44 00 33 00 2d 00 42 00  44 00 34 00 35 00 2d 00  |D.3.-.B.D.4.5.-.|
00000100  30 00 30 00 43 00 30 00  34 00 46 00 36 00 45 00  |0.0.C.0.4.F.6.E.|
00000110  41 00 35 00 41 00 45 00  7d 00 5c 00 4e 00 75 00  |A.5.A.E.}.\.N.u.|
00000120  6d 00 4d 00 65 00 74 00  68 00 6f 00 64 00 73 00  |m.M.e.t.h.o.d.s.|
00000130  00 00 00 00 f0 ba 06 00  5c 0d 91 7c 00 00 08 00  |........\..|....|
00000140  91 0e 91 7c 08 06 08 00  6d 05 91 7c 00 00 00 00  |...|....m..|....|
00000150  00 00 00 00 00 00 00 00  00 00 4e 01 08 00 00 00  |..........N.....|
00000160  d8 4d 0f 00 00 00 00 00  00 00 00 00 00 00 00 00  |.M..............|
00000170  00 00 00 00 e0 4d 0f 00  00 00 00 00 00 00 00 00  |.....M..........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 a0 03 08 00  |................|
00000190  00 00 00 00 20 00 00 00  01 05 00 00 00 00 00 05  |.... ...........|
000001a0  15 00 00 00 bf 21 9d 69  08 bb 0d fe 52 f7 9e 2d  |.....!.i....R..-|
000001b0  ed 03 00 00 01 05 00 00  00 00 00 05 15 00 00 00  |................|
000001c0  bf 21 9d 69 08 bb 0d fe  52 f7 9e 2d 01 02 00 00  |.!.i....R..-....|
000001d0  77 1b 7d 9c 68 01 00 00  d0 63 00 00 00 00 00 00  |w.}.h....c......|
000001e0  60 01 00 00 01 00 04 80  14 01 00 00 30 01 00 00  |`...........0...|
000001f0  00 00 00 00 14 00 00 00  02 00 00 01 02 00 00 00  |................|
00000200

Unknown BootLoader  on sda2

00000000  fd d1 28 c8 9b 27 16 ae  59 1d 24 34 37 b3 52 5a  |..(..'..Y.$47.RZ|
00000010  35 e9 a0 20 53 bf 0e 86  91 35 9c 8c ef 4b 4a 32  |5.. S....5...KJ2|
00000020  6d 01 18 78 0b 57 06 5e  c9 4d 14 e4 a7 e3 42 0a  |m..x.W.^.M....B.|
00000030  a5 19 90 d0 c3 ef fe 36  01 65 8c 3c 5f 7b 3a e2  |.......6.e.<_{:.|
00000040  dd 31 08 28 7b 87 f6 0e  39 7d 04 94 17 13 32 ba  |.1.({...9}....2.|
00000050  15 49 80 80 33 1f ee e6  71 95 7c ec cf ab 2a 92  |.I..3...q.|...*.|
00000060  4d 61 f8 d8 eb b7 e6 be  a9 ad f4 44 87 43 22 6a  |Ma.........D.C"j|
00000070  85 79 70 30 a3 4f de 96  e1 c5 6c 9c 3f db 1a 42  |.yp0.O....l.?..B|
00000080  bd 91 e8 88 5b e7 d6 6e  19 dd e4 f4 f7 73 12 1a  |....[..n.....s..|
00000090  f5 a9 60 e0 13 7f ce 46  51 f5 5c 4c af 0b 0a f2  |..`....FQ.\L....|
000000a0  2d c1 d8 38 cb 17 c6 1e  89 0d d4 a4 67 a3 02 ca  |-..8........g...|
000000b0  65 d9 50 90 83 af be f6  c1 25 4c fc 1f 3b fa a2  |e.P......%L..;..|
000000c0  9d f1 c8 e8 3b 47 b6 ce  f9 3d c4 54 d7 d3 f2 7a  |....;G...=.T...z|
000000d0  d5 09 40 40 f3 df ae a6  31 55 3c ac 8f 6b ea 52  |..@@....1U<..k.R|
000000e0  0d 21 b8 98 ab 77 a6 7e  69 6d b4 04 47 03 e2 2a  |.!...w.~im..G..*|
000000f0  45 39 30 f0 63 0f 9e 56  a1 85 2c 5c ff 9b da 02  |E90.c..V..,\....|
00000100  7d 51 a8 48 1b a7 96 2e  d9 9d a4 b4 b7 33 d2 da  |}Q.H.........3..|
00000110  b5 69 20 a0 d3 3f 8e 06  11 b5 1c 0c 6f cb ca b2  |.i ..?......o...|
00000120  ed 81 98 f8 8b d7 86 de  49 cd 94 64 27 63 c2 8a  |........I..d'c..|
00000130  25 99 10 50 43 6f 7e b6  81 e5 0c bc df fb ba 62  |%..PCo~........b|
00000140  5d b1 88 a8 fb 07 76 8e  b9 fd 84 14 97 93 b2 3a  |].....v........:|
00000150  95 c9 00 00 b3 9f 6e 66  f1 15 fc 6c 4f 2b aa 12  |......nf...lO+..|
00000160  cd e1 78 58 6b 37 66 3e  29 2d 74 c4 07 c3 a2 ea  |..xXk7f>)-t.....|
00000170  05 f9 f0 b0 23 cf 5e 16  61 45 ec 1c bf 5b 9a c2  |....#.^.aE...[..|
00000180  3d 11 68 08 db 67 56 ee  99 5d 64 74 77 f3 92 9a  |=.h..gV..]dtw...|
00000190  75 29 e0 60 93 ff 4e c6  d1 75 dc cc 2f 8b 8a 72  |u).`..N..u../..r|
000001a0  ad 41 58 b8 4b 97 46 9e  09 8d 54 24 e7 23 82 4a  |.AX.K.F...T$.#.J|
000001b0  e5 59 d0 10 03 2f 3e 76  41 a5 cc 7c 9f bb 00 fe  |.Y.../>vA..|....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 4a 00 00 00  |...........`J...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

```

---

### Post by oldfred on 2010-05-04
The script looks ok for sda, but what is sdb? It has nothing but errors so the script could not parse it. I do not know if that is contributing to the problem

Even though the script shows grub2 installed and looking to the correct partition, if you got errors on the recheck install their must be a problem that is not shown.

Since it seemed the install did not finish completely without error I would suggest a reinstall. My manual install to existing partitions took only about 10 minutes. It took longer to run the updates. Check that the install CD is good.

---

### Post by herveb on 2010-05-05
thanks for your answer

I believe i have 2 Hard drives, and sdb must be the second one.

I have tried the install twice with the same errors at the end, how do I get to check the CD?

Could you also point me to the right documentation on manual install?

---

### Post by oldfred on 2010-05-05
Install has not changed too much, so the Karmic version will be close.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

With manual install the only difference is you have to choose which partition is / (root) and /home if you have it and what format or not for /home. Right click on partition can choose. Besure you know which partitions you want to use. I have a bunch in sdc and chose the wrong one, fortunately it had not data.

---

### Post by herveb on 2010-05-05
ok, didn't solve the problem, same symptoms, here is the result. No obvious errors this time (good news) - actually it mentions 
# / was on /dev/sda2 during installation
UUID=c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e /               ext4    errors=remount-ro 0       1
towards the end.

haven't had the time to try the other fixes tonight


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sda2    *      3,905,536   117,209,087   113,303,552  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   117,209,087   117,207,040  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c2437be2-4bcf-480d-9a64-6621f3ca0b49   swap                                     
/dev/sda2        c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4ef2c300-5e57-4306-9565-39b05392d1e2   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=c1d6823e-4ac9-4e25-8cf0-505f12ae9c1e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=4ef2c300-5e57-4306-9565-39b05392d1e2 /home           ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  10.7GB: boot/grub/core.img
  40.9GB: boot/grub/grub.cfg
  10.7GB: boot/initrd.img-2.6.32-21-generic
  10.7GB: boot/vmlinuz-2.6.32-21-generic
  10.7GB: initrd.img
  10.7GB: vmlinuz
```

---

### Post by oldfred on 2010-05-05
I see nothing in the boot info script results that looks out of place.

Some have had success with just reinstalling grub, some use the grub menu edit to delete the entire line that starts with search, some have turned off floppy in BIOS and I do not know what else.

---

### Post by herveb on 2010-05-06
I might have got something wrong during my partitionning: *[COLOR=Blue]Partition 1 does not end on cylinder boundary.[/COLOR]*

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005cad2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244     1951744   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         244        7296    56651776   83  Linux

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000104d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7296    58603520   83  Linux

```

---

### Post by herveb on 2010-05-06
ok, some more data here, rebooting in a sec. I still got that error message
*[COLOR=Blue]root@ubuntu:/# sudo grub-install --recheck /dev/sda[/COLOR]*
[COLOR=Blue][I]sudo: unable to resolve host ubuntu
[/I][/COLOR] 

```

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /usr/ /mnt/usr
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# sudo grub-install --recheck /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt/sys
ubuntu@ubuntu:~$ sudo umount /mnt/usr
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

---

### Post by herveb on 2010-05-06
no difference what so ever. Still black screen with
[COLOR="Blue"]error: unknown file system
grub rescue> set
prefix=(hd0,2)/boot/grub
root=hd0,2
grub rescue>ls (hd0,2)/
error: unkown filesystem
grub rescue>boot
unknown command 'boot'
grub rescue>linux
unknown command 'linux'[/COLOR]

---

### Post by frantid on 2010-05-06
I think you need to run fsck /dev/sda2

also when you have chroot'd in try

as a precaution (see release notes for explanation)
while in chroot:
```
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl 
``````
 dpkg-query -l 'grub*' 
 apt-get check  #check broken dependencies
```& post back screen results

---

### Post by kansasnoob on 2010-05-06
Another thing to try is booting in recovery mode. Since Ubuntu is your only OS in order to see the boot menu you'll have to hold down the Shift key as soon as the System/BIOS screen passes.

It's possible the text may tell you something valuable but regardless when it's complete you'll see these options:

resume
clean
dpkg
failsafeX
grub
netroot
root

I'd choose 'resume' which resumes the normal boot but in text mode, so you'll have to enter your username & password and then type **startx**.

---

### Post by herveb on 2010-05-06
thanks for your help, it is really appreciated.

ok, did a clean install with swap at the end of sda. No more error message  when doing grub-install --recheck, no more ' *[COLOR=Blue]Partition  1 does not end on cylinder boundary.[/COLOR]*' when running fdisk

One thing I just realised, I have** no  /boot/grub/grub.cfg, even after reinstalling as above**. is this normal?

Otherwise, 

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck  1.41.11 (14-Mar-2010)
/dev/sda1: clean, 137744/3514368 files,  799575/14041600 blocks
```after doing the mounting of dev, sys,.etc and chroot as previously

```

root@ubuntu:/#  dpkg-divert --local --rename --add /sbin/initctl
Adding `local  diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/#  ln -s /bin/true /sbin/initctl
root@ubuntu:/# dpkg-query -l 'grub*' 
Desired=Unknown/Install/Remove/Purge/Hold
|   Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/  Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/  Name           Version        Description
+++-==============-==============-============================================
un   grub           <none>         (no description available)
ii   grub-common    1.98-1ubuntu5  GRand Unified Bootloader, version 2  (common 
un  grub-coreboot  <none>         (no description  available)
un  grub-doc       <none>         (no description  available)
un  grub-efi       <none>         (no description  available)
un  grub-efi-amd64 <none>         (no description  available)
un  grub-efi-ia32  <none>         (no description  available)
un  grub-emu       <none>         (no description  available)
un  grub-ieee1275  <none>         (no description  available)
un  grub-legacy    <none>         (no description  available)
un  grub-legacy-do <none>         (no description  available)
un  grub-linuxbios <none>         (no description  available)
ii  grub-pc        1.98-1ubuntu5  GRand Unified  Bootloader, version 2 (PC/BIOS
un  grub2           <none>         (no description available)

```

```
root@ubuntu:/# apt-get check 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by frantid on 2010-05-06
you did another new install and it still wouldn't boot?

where are you installing grub, /dev/sda or /dev/sdb ?

did you run update-grub?  this is very strange.
  
with the new install we need another bootinfoscript:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

hang in there.

---

### Post by herveb on 2010-05-06
> **kansasnoob said:**
> Another thing to try is booting in recovery mode. Since Ubuntu is your only OS in order to see the boot menu you'll have to hold down the Shift key as soon as the System/BIOS screen passes.

It's possible the text may tell you something valuable but regardless when it's complete you'll see these options:

resume
clean
dpkg
failsafeX
grub
netroot
root

I'd choose 'resume' which resumes the normal boot but in text mode, so you'll have to enter your username & password and then type **startx**.

i've just tried that.
it now says:
[COLOR="Blue"]GRUB loading.
error: unkown filesystem
grub rescue>resume
unkown command 'resume'
[/COLOR]

the difference being '**GRUB loading**'
none of the commands from the menu you mentioned are recognised when typing it in the grub-rescue> prompt

---

### Post by herveb on 2010-05-06
> **frantid said:**
> you did another new install and it still wouldn't boot?

where are you installing grub, /dev/sda or /dev/sdb ?

did you run update-grub?  this is very strange.
  
with the new install we need another bootinfoscript:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

hang in there.

I have actually reinstalled 3 times tonight trying different arrangements without success. the final install as detailed below is the one i am setting for because it is the one that gave the less error messages when booting in lifeCD and doing all the diagnostics we discussed. It is also the install matching bootinfoscript as below that I used to do dpkg-divert.

here are the results


```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e02ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6993    56166400   83  Linux
/dev/sda2            6993        7296     2437120   82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000104d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7296    58603520   83  Linux

```

```
==============

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   112,334,847   112,332,800  83 Linux
/dev/sda2         112,334,848   117,209,087     4,874,240  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   117,209,087   117,207,040  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8c04f388-5768-4794-9e10-71ab46a853ff   ext4                                     
/dev/sda2        f36a4e82-c8f4-46c2-94bb-61780e0ca97f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c198efea-10cf-4f0d-ac2f-4c9a7eae0faa   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 8c04f388-5768-4794-9e10-71ab46a853ff
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 8c04f388-5768-4794-9e10-71ab46a853ff
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8c04f388-5768-4794-9e10-71ab46a853ff
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8c04f388-5768-4794-9e10-71ab46a853ff ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8c04f388-5768-4794-9e10-71ab46a853ff
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8c04f388-5768-4794-9e10-71ab46a853ff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8c04f388-5768-4794-9e10-71ab46a853ff
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8c04f388-5768-4794-9e10-71ab46a853ff
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8c04f388-5768-4794-9e10-71ab46a853ff /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=c198efea-10cf-4f0d-ac2f-4c9a7eae0faa /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=f36a4e82-c8f4-46c2-94bb-61780e0ca97f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  53.8GB: boot/grub/core.img
  17.5GB: boot/grub/grub.cfg
  53.8GB: boot/initrd.img-2.6.32-21-generic
  53.8GB: boot/vmlinuz-2.6.32-21-generic
  53.8GB: initrd.img
  53.8GB: vmlinuz


======================================================================
```



Grub reinstall - this is the most strange because after running the script below, i still can't see any /boot/grub/grub.cfg (by looking into places... that might not be the most accurate way to do it)```
ubuntu@ubuntu:~$ grub-probe -t device /boot/grub
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
/dev/sda2 looks like swapspace - not mounted
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$  sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /usr/ /mnt/usr
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt/sys
ubuntu@ubuntu:~$ sudo umount /mnt/usr
ubuntu@ubuntu:~$ sudo umount /mnt

```

---

### Post by frantid on 2010-05-06
you still get the grub> prompt on boot?

well since your good at chroot, let's try to update your install.

this time don't mount /usr/
and add -- before chroot
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```for net access in your chroot.

then chroot

after chroot remember:
```
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

apt-get update

apt-get -u upgrade 

```let's see how that goes.


ps.  in order to see your grub.cfg from the livecd, you have to mount your drive.   You are unmounting at the end of chroot.  If you go to Places/Computer from the main menu, you can click mount the drive, then look for the file.

---

### Post by herveb on 2010-05-06
> **frantid said:**
> 
did you run update-grub?  this is very strange.


just done that after rebooting (I don't know if i should have done it before rebooting). here you go
```

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?

```

do i need to mount /dev and others like /sys and /proc?

---

### Post by oldfred on 2010-05-06
You did not get any errors on the grub install commands.

The boot info script prints out your grub.cfg.

Since you have only the one operating system you will not get a menu (grub.cfg) unless you hold down the shift key from BIOS boot until menu appears. Then you should see recovery & memory test and eventually older kernels.

The list Kansas posted is a menu you should get from booting with the recovery mode.

---

### Post by frantid on 2010-05-06
oldfred, he's still getting the grub prompt on boot. I hope that's still right.

herveb.  run your chroot like you did before, but leave out the mount /sys/  add in the extras before chroot.  and aftert chroot

don't do any of the grub commands. there were a few updates today, a kernel and grub + others.  let's hope it's one of them.

---

### Post by herveb on 2010-05-06
going through a long list of update right now

---

### Post by herveb on 2010-05-06
well, in short:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# apt-get update


```
 and then a list of urls, followed by
```
root@ubuntu:/# apt-get -u upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  acpid capplets-data empathy empathy-common file-roller gedit gedit-common gnome-control-center
  gnome-settings-daemon grub-common grub-pc language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libgnome-window-settings1 libgtksourceview2.0-0 libgtksourceview2.0-common
  libkpathsea5 libnautilus-extension1 librsvg2-2 librsvg2-common linux-libc-dev nautilus nautilus-data
  nautilus-sendto-empathy python-ubuntuone-client rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins tomboy
  transmission-common transmission-gtk ubuntuone-client ubuntuone-client-gnome
35 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 15.9MB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

```

after pressing Y there was an impressive-looking list of update that went on. I got the logs somewhere of what happened if needed.

rebooting now

---

### Post by herveb on 2010-05-06
unfortunately that was not the solution

still get 
error: unkown filesystem
grub rescue>

trying to press shift key only results in displaying "grub loading" before the above. I have no access to the menu.

---

### Post by herveb on 2010-05-06
i've found where my grub.cfg is by the way

---

### Post by frantid on 2010-05-06
I don't know what to tell you hang on a second.

---

### Post by frantid on 2010-05-06
there's some thing going on I can't figure out yet.  I somehow think it's tied to this line in your config.


edit:  I must have been far too sleepy last night. pttype=dos is normal.

---

### Post by frantid on 2010-05-07
herveb, did you format these partitions using the installer or with gparted?

edit:  another question, is this an older motherboard?  Have you booted off the same partitions before?

please run

sudo sfdisk -l /dev/sda


I'd like to try running testdisk.  Have it do the analysis then deeper search.  Once it has the partition list right, i.e. matches what was recorded last in fdisk -l, then have it write the partition.

If you're not familiar with testdisk, here's a walk through:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by herveb on 2010-05-08
> **frantid said:**
> herveb, did you format these partitions using the installer or with gparted?


using the installer


> **frantid said:**
> 
edit:  another question, is this an older motherboard?  Have you booted  off the same partitions before?

dunno. I bought the laptop in 2005-2006, toshiba qosmio, was top specs at the time, maybe a bit too much top specs. Result, the fans struggle to keep up and I've had to have PCworld replace the motherboard 3 times those last 3 years. It came back from such a replacement about a month ago, running windows XP, and was contanimated by nasty viruses in the process. That's when i decided to give linux a go. Tried opensuse but install failed - can't remember the error message.


```
ubuntu@ubuntu:~$ sudo sfdisk -l /dev/sda

Disk /dev/sda: 7296 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6992-   6993-  56166400   83  Linux
/dev/sda2       6992+   7295-    304-   2437120   82  Linux swap / Solaris
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ 

```


will do testdisk later on

---

### Post by frantid on 2010-05-08
good to see you're still hanging on.  Try looking through this site it can walk you through booting from the grub prompt

[http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html)

to get to the normal prompt.  you will probably have to do 

insmod normal

normal

hopefully testdisk can fix it up

---

### Post by herveb on 2010-05-08
thanks - it starts to get a little bit more involved.

I've tried to run the testdisk, but the command to run it is not obvious, or it is not installed. I've looked in /bin and /sbin and /usr/bin for a file called testdisk but couldn't find one. Maybe it's not installed. Looking on the download website, i got 4 options, i don't know which one applies


[LIST]
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2"),  kernel  2.6.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux24.tar.bz2"),  kernel  2.4.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/rpm.png[/IMG]  Linux [i386 RPM]("http://www.cgsecurity.org/testdisk-6.11.3-1.i386.rpm")
[*] [IMG]http://www.cgsecurity.org/os/rpm.png[/IMG]  Linux [SRPM]("http://www.cgsecurity.org/testdisk-6.11.3-1.src.rpm")
[/LIST]

---

### Post by frantid on 2010-05-08
I thought it should be on the cd.

sudo testdisk

to install

sudo apt-get install testdisk

---

### Post by herveb on 2010-05-08
thanks - no luck unfortunately

```
buntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found

```

---

### Post by oldfred on 2010-05-08
In software sources have you enabled universe? I always enable all Ubuntu sources. I think testdisk is in universe.

It is in universe - see instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by kansasnoob on 2010-05-08
Maybe I'm missing something here, and please **at this point just consider this thinking out loud**!

So, is this a one OS installation?

This throws me:

> The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic


Then again that came from:

```
apt-get -u upgrade

```

I'd have to google to find out what -u upgrade does :confused:

(well I googled and still don't know)

But I'm honestly thinking it's time to look at this from a different angle. What about hardware?

What Live CD can you run?

If you can run a Live CD it would be nice to see the output of:

```
cat /proc/cpuinfo
```

```
cat /proc/meminfo
```

```
lspci | grep VGA
```

```
lsb_release -a
```

Those are all pretty generic and should run from Knoppix, Puppy, DSL, etc.

---

### Post by frantid on 2010-05-08
```
apt-get -u upgrade

```just prints out the complete list of packages that will be upgraded

;)

---

### Post by herveb on 2010-05-09
> **kansasnoob said:**
> Maybe I'm missing something here, and please **at this point just consider this thinking out loud**!

So, is this a one OS installation?


yes

> **kansasnoob said:**
> But I'm honestly thinking it's time to look at this from a different  angle. What about hardware?

What Live CD can you run?

If you can run a Live CD it would be nice to see the output of:


after installation on the harddrive, I can only run my pc through live CD with the latest version of Ubuntu 10.04 lts

```
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping    : 8
cpu MHz        : 1000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm
bogomips    : 3325.29
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping    : 8
cpu MHz        : 1000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm
bogomips    : 3325.04
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

```


```
ubuntu@ubuntu:~$ cat /proc/meminfo
MemTotal:        1025916 kB
MemFree:          123884 kB
Buffers:          106384 kB
Cached:           523540 kB
SwapCached:            0 kB
Active:           412928 kB
Inactive:         387440 kB
Active(anon):     297308 kB
Inactive(anon):        0 kB
Active(file):     115620 kB
Inactive(file):   387440 kB
Unevictable:          32 kB
Mlocked:              32 kB
HighTotal:        138696 kB
HighFree:            252 kB
LowTotal:         887220 kB
LowFree:          123632 kB
SwapTotal:       2437112 kB
SwapFree:        2437112 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        170468 kB
Mapped:            64052 kB
Shmem:            126872 kB
Slab:              46860 kB
SReclaimable:      32400 kB
SUnreclaim:        14460 kB
KernelStack:        2176 kB
PageTables:         5144 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2950068 kB
Committed_AS:     772288 kB
VmallocTotal:     122880 kB
VmallocUsed:      115268 kB
VmallocChunk:       4088 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      897024 kB

```

```
ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce Go 7600] (rev a1)

```

```
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid

```

---

### Post by herveb on 2010-05-09
> **oldfred said:**
> In software sources have you enabled universe? I always enable all Ubuntu sources. I think testdisk is in universe.

It is in universe - see instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

well spotted - sorry, I didn't touch linux in 7years - updating now

---

### Post by herveb on 2010-05-09
> **frantid said:**
> 
I'd like to try running testdisk.  Have it do the analysis then deeper search.  Once it has the partition list right, i.e. matches what was recorded last in fdisk -l, then have it write the partition.

If you're not familiar with testdisk, here's a walk through:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)


ok, going through testdisk - after selecting sda

```
Disk /dev/sda - 60 GB / 55 GiB - ATA TOSHIBA MK6034GS

Hidden sectors are present.

size       117210240 sectors
user_max   117210240 sectors
native_max 16546944 sectors
dco        117210240 sectors
Device Configuration Overlay (DCO) present.

```

```
Disk /dev/sda - 60 GB / 55 GiB - ATA TOSHIBA MK6034GS

Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

```

analysis of sda gives

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0  32 33  6992 132 52  112332800
 2 P Linux Swap            6992 132 53  7295 236 45    4874240

```

quick search yield

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63

The harddisk (60 GB / 55 GiB) seems too small! (< 110 GB / 102 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS              0   1  1 13374 254 63  214869312


```

looks wrong, but I do no understand the problem. Is this due to the fact I have 2 hard drives of 60GB? I don't know what's a jumper btw.


next step ask to modify something, I am unsure what to do at this stage. What do you advise?

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
* Linux                    0  32 33  6992 132 52  112332800
P Linux Swap            6992 132 53  7295 236 29    4874224




Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 57 GB / 53 GiB

```


also, what do you mean by > **frantid said:**
> 
  then have it write the partition.


---

### Post by frantid on 2010-05-09
that last shot, is that after a deep search?

---

### Post by frantid on 2010-05-09
don't modify anything.  press enter it will give something like this:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 38912 254 63  625137282 [data]













[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions
```

choose "deeper search"  it may take a while.  It will go over all the cylinders of your disk, looking for errors.  Was this drive ever part of a raid array?

---

### Post by frantid on 2010-05-09
on this link:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)

scroll up a bit you'll see it

you're on "[SIZE=1]A partition is still missing: Deeper  Search[/SIZE]"


scroll up a bit you'll see it

the "write"  part comes after "deep search"  after it put's up a screen that matches your last screen shot.  It just writes the partition table, it does not touch the data.

---

### Post by herveb on 2010-05-09
no, i just found out how to do the deeper search.

Here you go - puzzling for such a newbie as I. Why on earth do I have so many partitions?

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63

The harddisk (60 GB / 55 GiB) seems too small! (< 110 GB / 102 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS              0   1  1 13374 254 63  214869312
  Linux                 3414 220  7 10407  65 26  112332800
  Linux                 3418  77 52 10410 178  8  112332800
  Linux                 3418 240 23 10411  85 42  112332800
  Linux                 3419 180 26 10412  25 45  112332800
  Linux                 3664 153 10 10717 107 14  113303552
  Linux                 3666 130 49 10719  84 53  113303552
  Linux                 3667   5 51 10719 214 55  113303552
  Linux                 3668  43 24 10720 252 28  113303552

```

---

### Post by herveb on 2010-05-09
```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  6687 254 63  107442657
D Linux                    0  32 33  6992 132 52  112332800
D Linux                  243  27 41  7295 236 45  113303552
D Linux                 6688   0  1  7258 254 60    9173112
D Linux Swap            6808  78 55  7295 236 29    7833584
D Linux Swap            6992 132 53  7295 236 29    4874224
D Linux                 7259   0  1  7294 254 59     578336



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ubuntu@ubuntu:~$ backup sector!, 55 GB / 51 GiB

```

unfortunately i pressed the wrong key, I have to start again - those bloody big fingers :(

---

### Post by herveb on 2010-05-09
ok, the first one is damaged

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

     HPFS - NTFS              0   1  1  6687 254 63  107442657



Can't open filesystem. Filesystem seems damaged.

```

second seems all right

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   * Linux                    0  32 33  6992 132 52  112332800
Directory /

drwxr-xr-x     0     0      4096  6-May-2010 20:43 .
drwxr-xr-x     0     0      4096  6-May-2010 20:43 ..
drwx------     0     0     16384  6-May-2010 20:23 lost+found
drwxr-xr-x     0     0      4096 29-Apr-2010 12:26 var
drwxr-xr-x     0     0      4096  6-May-2010 20:23 home
drwxr-xr-x     0     0     12288  6-May-2010 22:53 etc
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 media
drwxr-xr-x     0     0      4096  6-May-2010 20:44 bin
drwxr-xr-x     0     0      4096  6-May-2010 20:45 boot
drwxr-xr-x     0     0      4096  6-May-2010 20:37 dev
drwxr-xr-x     0     0     12288  6-May-2010 20:44 lib
drwxr-xr-x     0     0      4096 23-Apr-2010 10:11 mnt
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 opt
drwxr-xr-x     0     0      4096 23-Apr-2010 10:11 proc
drwx------     0     0      4096 29-Apr-2010 12:28 root
drwxr-xr-x     0     0      4096  6-May-2010 21:38 sbin
drwxr-xr-x     0     0      4096  5-Dec-2009 21:55 selinux
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 srv
drwxr-xr-x     0     0      4096 30-Mar-2010 07:17 sys
drwxrwxrwt     0     0      4096  6-May-2010 22:53 tmp
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 usr
lrwxrwxrwx     0     0        30  6-May-2010 20:43 vmlinuz
lrwxrwxrwx     0     0        33  6-May-2010 20:43 initrd.img
drwxr-xr-x     0     0      4096  6-May-2010 20:34 cdrom


```

thrid seems to contain the same thing :confused:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
     Linux                  243  27 41  7295 236 45  113303552
Directory /

drwxr-xr-x     0     0      4096  5-May-2010 23:34 .
drwxr-xr-x     0     0      4096  5-May-2010 23:34 ..
drwx------     0     0     16384  5-May-2010 23:20 lost+found
drwxr-xr-x     0     0      4096 29-Apr-2010 12:26 var
drwxr-xr-x     0     0      4096  5-May-2010 23:21 home
drwxr-xr-x     0     0      4096  6-May-2010 18:34 etc
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 media
drwxr-xr-x     0     0      4096  5-May-2010 23:35 bin
drwxr-xr-x     0     0      4096  5-May-2010 23:36 boot
drwxr-xr-x     0     0      4096  5-May-2010 23:33 dev
drwxr-xr-x     0     0     12288  5-May-2010 23:35 lib
drwxr-xr-x     0     0      4096 23-Apr-2010 10:11 mnt
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 opt
drwxr-xr-x     0     0      4096 23-Apr-2010 10:11 proc
drwx------     0     0      4096 29-Apr-2010 12:28 root
drwxr-xr-x     0     0      4096  5-May-2010 23:36 sbin
drwxr-xr-x     0     0      4096  5-Dec-2009 21:55 selinux
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 srv
drwxr-xr-x     0     0      4096 30-Mar-2010 07:17 sys
drwxrwxrwt     0     0      4096  6-May-2010 18:34 tmp
drwxr-xr-x     0     0      4096 29-Apr-2010 12:17 usr
lrwxrwxrwx     0     0        30  5-May-2010 23:34 vmlinuz
lrwxrwxrwx     0     0        33  5-May-2010 23:34 initrd.img
drwxr-xr-x     0     0      4096  5-May-2010 23:32 cdrom


```


fourth seems on the light side

```
     Linux                 6688   0  1  7258 254 60    9173112
Directory /

drwxr-xr-x     0     0      4096 14-Mar-2006 10:12 .
drwxr-xr-x     0     0      4096 14-Mar-2006 10:12 ..
drwx------     0     0      4096 14-Mar-2006 10:12 lost+found
-rw-r--r--     0     0        44  8-Mar-2006 06:49 checksum
-rw-r--r--     0     0        28  8-Mar-2006 06:48 version

```

there is one too many swap, and the last one seems incomplete, with last two lines in red
```
     Linux                 7259   0  1  7294 254 59     578336
Directory /

drwxr-xr-x     0     0      4096 29-May-2006 16:42 .
drwxr-xr-x     0     0      4096 29-May-2006 16:42 ..
drwx------     0     0      4096 14-Mar-2006 10:12 lost+found
drwxr-xr-x     0     0      4096 29-May-2006 16:42 boot
-rw-r--r--     0     0      6149  8-Mar-2006 06:49 checksum
drwxr-xr-x     0     0      4096 29-May-2006 16:42 etc
drwxr-xr-x     0     0      4096 28-Jan-2008 16:42 log
----------     0     0   87752704 14-Mar-2006 10:14 recovery.iso
drwxr-xr-x     0     0      4096 26-Jul-2009 11:38 system
drwxr-xr-x     0     0      4096 14-Mar-2006 10:12 update
-rw-r--r--     0     0         0 14-Mar-2006 10:14 successflag
-rw-r--r--     0     0       169 28-Jan-2008 12:32 setupflag
-rw-r--r--     0     0       114 11-Aug-2007 11:18 linksetupflag

```

---

### Post by herveb on 2010-05-09
modifying for:

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  6687 254 63  107442657
* Linux                    0  32 33  6992 132 52  112332800
D Linux                  243  27 41  7295 236 45  113303552
D Linux                 6688   0  1  7258 254 60    9173112
D Linux Swap            6808  78 55  7295 236 29    7833584
P Linux Swap            6992 132 53  7295 236 29    4874224
D Linux                 7259   0  1  7294 254 59     578336


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Sparse superblock, 4696 MB / 4479 MiB

```

and rebooting

---

### Post by herveb on 2010-05-09
ok, that didn't work - actually, just as if nothing had been done, still not booting, running testdisk again gives the same structure. Is that because I am booting from liveCD?

How to I get the first linux partition to start at 0 1 1?

---

### Post by frantid on 2010-05-09
you would have to resize it with gparted.  Seems like there were a lot of old partition data hanging in there.

---

### Post by herveb on 2010-05-09
ye-ah!!!!! a working ubuntu!!!!

the problem was the few Mb of free space at the beginning of the disk which failed to be corrected by the partitionning tool of the installer. testdisk now gives consistent results


THANK YOU EVERYONE, you have been very helpful

:guitar:

---

