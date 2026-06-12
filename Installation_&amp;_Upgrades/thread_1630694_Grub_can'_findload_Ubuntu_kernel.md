---
title: "Grub can' find/load Ubuntu kernel"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by thaberfelde on 2010-11-25
After installation of Ubuntu 10.10, grub loads and has the right menu list.  However, Ubuntu doesn't load and I get an error message of :
Gave up waiting for root device. (with a list of common problems)
There is also:
ALERT! /dev/disk/by-uuid/1584598e-b8e5..... does not exist.
How can I fix the link?

---

### Post by pawhtiobo on 2010-11-25
Hi :)

See this:

[http://ubuntuforums.org/showthread.php?t=1355385](http://ubuntuforums.org/showthread.php?t=1355385)

[http://ubuntuforums.org/showthread.php?t=433710](http://ubuntuforums.org/showthread.php?t=433710)

[http://ubuntuforums.org/showthread.php?t=1369410](http://ubuntuforums.org/showthread.php?t=1369410)

[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)

You just need a little search in the forum :)


See ya...

---

### Post by DasEi on 2010-11-25
seems like your blkid and/or partitions are messed up, I'm still in some work but can help you on irc ~30 min.
HAve a live cd handy, preferably have it booted on that box when
logging on in #ubuntu , nick DasEi
for now, sudo blkid shows you the uuids of your partitions

---

### Post by Rubi1200 on 2010-11-25
Hi,
I suggest you boot the computer with a LiveCD and post the results of the boot info script linked at the bottom of my post (instructions included).

Thanks.

@pawhtiobo: most of those links are old and, anyway, most of the time the situation, or cause of it, is different and requires a solution for the particular user.

---

### Post by pawhtiobo on 2010-11-25
> **Rubi1200 said:**
> 

@pawhtiobo: most of those links are old and, anyway, most of the time the situation, or cause of it, is different and requires a solution for the particular user.

I was just saying that he should tried to search before asking in a new post, google is a friend and also the search button in this forum :)...i heard this from lots of people in the beginning when i started to use the forum :).

See ya...

---

### Post by Rubi1200 on 2010-11-25
> **pawhtiobo said:**
> I was just saying that he should tried to search before asking in a new post, google is a friend and also the search button in this forum :)...i heard this from lots of people in the beginning when i started to use the forum :).

See ya...
Can't argue with that ;)

And, there was no disrespect intended about your post.

Regards :-)

---

### Post by thaberfelde on 2010-12-04
Thanks for the links, I've read them all.  I think I'm one step away.
Grub thinks the partition is (hd0,msdos1) for both the /sbin/init and vmlinuz.
In Ubuntu the device map (from fdisk) is:
/dev/sdb1  Linux
/dev/sdb2  Extended
/dev/sdb5  Linux swap / Solaris

When I use /dev/sdb1 in the vmlinuz kernel command line, I get the same result ie, ALERT! /dev/sdb1 does not exist.

I can't figure out how to link the two.

---

### Post by Quackers on 2010-12-04
Then give us a chance :-)
Please post the details of the boot script that Rubi1200 asked for in post #4

---

### Post by thaberfelde on 2010-12-04
From the results file: 
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   476,108,799   476,106,752  83 Linux
/dev/sdb2         476,110,846   488,396,799    12,285,954   5 Extended
/dev/sdb5         476,110,848   488,396,799    12,285,952  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2008 MB, 2008023040 bytes
16 heads, 32 sectors/track, 7660 cylinders, total 3921920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064     3,921,919     3,913,856   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        4f894c13-a871-4502-ab04-cc6ec269d5be   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        620ec9d0-35af-4564-992f-85bbac0da11f   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F0AD-1743                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sda: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4f894c13-a871-4502-ab04-cc6ec269d5be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4f894c13-a871-4502-ab04-cc6ec269d5be
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4f894c13-a871-4502-ab04-cc6ec269d5be
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4f894c13-a871-4502-ab04-cc6ec269d5be ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4f894c13-a871-4502-ab04-cc6ec269d5be
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4f894c13-a871-4502-ab04-cc6ec269d5be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4f894c13-a871-4502-ab04-cc6ec269d5be
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4f894c13-a871-4502-ab04-cc6ec269d5be
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=4f894c13-a871-4502-ab04-cc6ec269d5be /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=620ec9d0-35af-4564-992f-85bbac0da11f none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
 219.1GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
   2.2GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
   2.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  32 82 42 e9 bc 39 69 1a  8f 54 83 9e 75 ae 77 54  |2.B..9i..T..u.wT|
00000010  be bf a0 7b ff 5e 2b db  d4 3b 79 e1 41 dc 79 2f  |...{.^+..;y.A.y/|
00000020  62 2e 4c 73 61 fd fc ed  ae 51 b3 d8 6c dc d9 41  |b.Lsa....Q..l..A|
00000030  27 6a 58 42 c4 94 7e ea  21 7d fa f4 05 96 40 6d  |'jXB..~.!}....@m|
00000040  57 cf 6b ae 70 ba 3d 15  35 ea f8 6f cc 54 ca 13  |W.k.p.=.5..o.T..|
00000050  0f fd 08 96 44 ac 3c fa  0f 75 a2 5d 6b e3 a1 53  |....D.<..u.]k..S|
00000060  39 42 02 01 b1 36 82 10  2a cc 83 87 3e 22 0f b4  |9B...6..*...>"..|
00000070  b3 87 cf 1e 3c 00 e9 63  2e 6b 94 dd 13 da 91 c9  |....<..c.k......|
00000080  bb 83 73 17 5d cb 2b 4b  4c c5 76 cc 35 dc 15 cb  |..s.].+KL.v.5...|
00000090  b5 49 a1 eb f4 99 6c 20  a5 54 57 69 42 37 95 83  |.I....l .TWiB7..|
000000a0  52 db f0 69 23 e0 3f 2e  ac bf 29 ef 9e a9 a6 cc  |R..i#.?...).....|
000000b0  6e 68 8e 87 a1 ea 8a 80  1e ab 12 c1 7c 80 cc fc  |nh..........|...|
000000c0  90 7a 3e 3a 67 14 7b 0f  3e 54 ff df a2 d1 7b f8  |.z>:g.{.>T....{.|
000000d0  ec 18 7f 4d 37 4e c8 98  15 21 db f4 0d ed 39 02  |...M7N...!....9.|
000000e0  ea 22 b6 cb 34 88 37 8f  64 fb 76 0b b7 52 31 0f  |."..4.7.d.v..R1.|
000000f0  20 e1 41 ab 29 4a fc a0  ea 05 31 0f b1 c5 d2 0b  | .A.)J....1.....|
00000100  be 45 8a 0e 1b 63 b4 fd  34 76 2d 3b 5c 79 ca 3f  |.E...c..4v-;\y.?|
00000110  b3 3a 0e 04 74 9f a8 e7  dd 7b 49 d2 ef 7e 93 3b  |.:..t....{I..~.;|
00000120  b0 c0 c0 f5 6a 2f e3 0b  06 f5 39 40 80 b4 e8 80  |....j/....9@....|
00000130  d5 36 d3 2b 5e ea 10 59  35 0b 67 35 2f 62 e9 33  |.6.+^..Y5.g5/b.3|
00000140  2d c7 ab d8 23 ad 42 97  e9 8b 0e c0 14 75 d8 aa  |-...#.B......u..|
00000150  15 77 90 86 73 91 91 79  3d b8 a4 a4 d9 be db a4  |.w..s..y=.......|
00000160  84 87 d0 a4 1a 67 e2 7b  bd c7 82 8c aa 87 d5 f5  |.....g.{........|
00000170  04 22 05 86 6f dc f8 f7  15 8e 85 28 c8 2e 3e c0  |."..o......(..>.|
00000180  9e 86 0b ed 67 7e 91 1b  6b 7b bf cf 33 2d ef 6c  |....g~..k{..3-.l|
00000190  29 e1 bc 02 cb 77 c2 a2  ea 16 3b 0d fe 96 f1 4f  |)....w....;....O|
000001a0  3c 31 f1 a5 71 80 42 65  41 87 3f 99 02 e3 94 29  |<1..q.BeA.?....)|
000001b0  55 6d 78 6b 6b 2b c6 92  9e 95 5f d5 5a c0 00 fe  |Umxkk+...._.Z...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 32 02  |.X.SYSLINUX...2.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 b8 3b 00 e7 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 43 17 ad f0 4e  4f 20 4e 41 4d 45 20 20  |..)C...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
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
00000100  7d 00 66 b8 d0 dd 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
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


=======Devices which don't seem to have a corresponding hard drive==============

sda

---

### Post by thaberfelde on 2010-12-05
I ran this code after reviewing other threads:



 	Code:
 	sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb 
It ran sucessfully but didn't make a difference

---

### Post by Rubi1200 on 2010-12-05
Is there an sda? Have you tried changing the device boot priority in BIOS to boot sdb first?

---

### Post by thaberfelde on 2010-12-11
Ultimately when all else failed, I reformatted my hard drive.  There was  a small partition ahead of the linux root (appeared as sda) which I can only  surmise was the cause of the disconnect.  After that, worked great.

---

