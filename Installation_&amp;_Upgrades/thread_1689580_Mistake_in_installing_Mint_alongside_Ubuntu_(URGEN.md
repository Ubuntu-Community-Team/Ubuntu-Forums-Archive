---
title: "Mistake in installing Mint alongside Ubuntu (URGENT)"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by pedi0022003 on 2011-02-17
Hi everyone.
I have very serious problem.I have just installed Mint using a Live-CD and I used "Alongside" option.
But after installing there is just "Mint"!!!
how can I solve this? I think I made a mistake when I had to choose the boot loader.
PLEASE PLEASE PLEASE HELP ME!

---

### Post by amsterdamharu on 2011-02-17
You might have overwritten your Ubuntu partition, first of all DO NOT USE THE HARDDISK ANYMORE. This is important because the more you use it the less likely you can recover data from it.

Can you start the computer with the mint cd and choose "try without installing" commonly called live CD. 
When you are running the live CD don't mount any partitions on that harddisk but run the boot info script.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Copy it to your Desktop (it usually is in Downloads).
Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script*
```To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
There should be a file on your Desktop named RESULTS.txt please post the content of this file here using &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by pedi0022003 on 2011-02-17
Thanks for the reply. Here is the results :
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
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

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   600,565,759   600,563,712  83 Linux
/dev/sda2         600,567,806   625,141,759    24,573,954   5 Extended
/dev/sda5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8021 MB, 8021606400 bytes
247 heads, 62 sectors/track, 1023 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,666,221    15,666,160   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f390cc19-df3a-406d-9138-25d36b4309b9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2adbaeb1-8cda-4f64-bc00-7a40d0c9874f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1010-6048                              vfat       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f390cc19-df3a-406d-9138-25d36b4309b9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f390cc19-df3a-406d-9138-25d36b4309b9
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f390cc19-df3a-406d-9138-25d36b4309b9
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda1)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f390cc19-df3a-406d-9138-25d36b4309b9
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f390cc19-df3a-406d-9138-25d36b4309b9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f390cc19-df3a-406d-9138-25d36b4309b9
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f390cc19-df3a-406d-9138-25d36b4309b9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f390cc19-df3a-406d-9138-25d36b4309b9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f390cc19-df3a-406d-9138-25d36b4309b9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=f390cc19-df3a-406d-9138-25d36b4309b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2adbaeb1-8cda-4f64-bc00-7a40d0c9874f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
 232.0GB: boot/grub/grub.cfg
 215.0GB: boot/initrd.img-2.6.35-22-generic
  60.2GB: boot/vmlinuz-2.6.35-22-generic
 215.0GB: initrd.img
  60.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  50 32 20 2d d8 f4 08 07  0f 08 a3 b2 10 92 1e 15  |P2 -............|
00000010  a9 d5 70 8c a0 60 6c 29  b7 ce 69 20 37 02 a1 07  |..p..`l)..i 7...|
00000020  15 98 1e 85 82 a0 cd 2e  30 1c 09 d1 d7 49 c9 03  |........0....I..|
00000030  8c 87 83 06 cc 73 06 0d  8c 06 9e 0a 5c 2f 27 2b  |.....s......\/'+|
00000040  48 c9 59 a3 66 9f ab 48  e4 32 fa 79 92 8d 94 3c  |H.Y.f..H.2.y...<|
00000050  00 8c 8a 38 43 72 93 1a  19 22 39 19 28 2a ff 1e  |...8Cr..."9.(*..|
00000060  80 c9 0d 35 c9 80 d7 c8  31 1a e8 11 00 41 b9 c7  |...5....1....A..|
00000070  8b 17 d1 28 83 d1 cf 89  1e 8d f3 24 59 13 f7 39  |...(.......$Y..9|
00000080  b3 14 a8 e0 7b 89 1d 3d  49 38 11 64 25 4e b5 4f  |....{..=I8.d%N.O|
00000090  26 1b 9b c1 90 7e 02 50  e0 72 89 7b 42 0a 94 c3  |&....~.P.r.{B...|
000000a0  9e 90 81 a6 01 d3 80 53  79 60 c4 77 d6 fb 1b 12  |.......Sy`.w....|
000000b0  94 7e 5e 07 68 2c 47 c1  47 73 92 19 73 d3 2b 61  |.~^.h,G.Gs..s.+a|
000000c0  07 02 26 87 93 4c aa 28  b3 f4 7f e6 13 42 1d 53  |..&..L.(.....B.S|
000000d0  13 98 25 3c fe 72 80 35  d9 91 3c 68 79 d9 53 86  |..%<.r.5..<hy.S.|
000000e0  13 79 8c 00 1d 08 b0 5e  85 75 70 72 84 f4 8d e4  |.y.....^.upr....|
000000f0  9c 9c 70 14 74 7d 4e 86  9a a5 55 ce 4d 08 21 d2  |..p.t}N...U.M.!.|
00000100  27 8f 6b a5 39 72 c8 59  3a df b8 c8 f5 40 a5 39  |'.k.9r.Y:....@.9|
00000110  c6 3f e5 32 43 83 a7 0e  f8 0c a0 41 93 87 d8 de  |.?.2C......A....|
00000120  6c e4 64 53 c4 f8 46 d8  8b 3c c4 4e 72 36 88 01  |l.dS..F..<.Nr6..|
00000130  a2 ee 95 83 11 7f 32 50  d0 a8 37 43 61 34 7e 76  |......2P..7Ca4~v|
00000140  db 4d 09 81 fe e9 00 a4  07 90 b8 ab ef 50 10 b0  |.M...........P..|
00000150  14 98 1c 5d 00 0c 1a a4  a7 9d 9c 7c 84 60 1b 73  |...].......|.`.s|
00000160  b8 da fb 44 00 4e 3a 10  3d f9 48 2b 1e 87 e8 dd  |...D.N:.=.H+....|
00000170  66 2b bd f0 7e 91 a3 e5  c0 98 a4 38 fc 6f 6f 1f  |f+..~......8.oo.|
00000180  c4 41 20 29 33 63 26 ee  26 39 38 9e 9c 4f 08 48  |.A )3c&.&98..O.H|
00000190  82 04 43 91 9c 17 e4 7d  c9 80 97 76 52 0e 92 33  |..C....}...vR..3|
000001a0  79 4c 77 5d 38 57 4e de  3e 45 09 21 bd db ad 45  |yLw]8WN.>E.!...E|
000001b0  af 0d 0e 04 7d 30 73 00  03 b3 81 e1 81 31 00 fe  |....}0s......1..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 76 01 00 00  |............v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 f7 00 00 00 00 00  |........>.......|
00000020  f0 0b ef 00 a8 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 48 60 10 10 4e  65 77 20 56 6f 6c 75 6d  |..)H`..New Volum|
00000050  65 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |e FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 f8 ea 1a 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by pedi0022003 on 2011-02-17
I just want to save some of my files.The rest are not so important.

---

### Post by sikander3786 on 2011-02-17
If you want to recover your files, stop using your PC right now. If you have no other choice, boot a Live CD/USB on the same PC for browsing the internet. That way you won't be overwriting your files on the HDD which are still there but the sectors have been marked empty.

Well, another case of 10.10 destruction. It is a bug in the new ubiquity installer. See here.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

For data recovery, I don't think that you'll be able to recover whole of your partitions. The chances are low, still you can try testdisk.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

If that fails, photorec can surely recover most of your files but it won't preserve filenames.

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by pedi0022003 on 2011-02-17
Thanks but what's the connection between the post #3 and your answer?

---

### Post by sikander3786 on 2011-02-17
> **pedi0022003 said:**
> Thanks but what's the connection between the post #3 and your answer?
This.

> sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  



There is nothing except Mint on your PC. Aplogies I should have mentioned that in my above post.

Mint over-wrote whole of your drive and sadly, there is nothing left on your HDD.

---

### Post by amsterdamharu on 2011-02-17
There should be a bug on launchpad.net for that but I can't seem to find it.

Sorry for the bad news here, I had one thread before of a user who swore they'd choose alongside option but Windows was wiped and whole disk was used.

Can't access blogspot here in China because it's blocked but there should be.

I have no experience with the alongside option because I always manually partition (using seporate home dir).
Is this the bug that you are talking about?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Here is a list of all the ubiquity bugs:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)

---

### Post by sikander3786 on 2011-02-17
> **amsterdamharu said:**
> There should be a bug on launchpad.net for that but I can't seem to find it.

Sorry for the bad news here, I had one thread before of a user who swore they'd choose alongside option but Windows was wiped and whole disk was used.

Can't access blogspot here in China because it's blocked but there should be.

I have no experience with the alongside option because I always manually partition (using seporate home dir).
Is this the bug that you are talking about?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Here is a list of all the ubiquity bugs:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)
Yes the one you linked above. Here is another one.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

---

