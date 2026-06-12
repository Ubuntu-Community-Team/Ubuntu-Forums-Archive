---
title: "looking for a grub2 thread"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by espen.john@gmail.com on 2011-02-10
sorry to post like this, because i know i should look more through the forum, but i've been stuck on installing ubuntu on my computer for 3 days now, reinstalling, manual grub installing and so on, but no go.
but i found a good thread on my still no fully functional ubuntu computer that explained very well for a complete linux noob how to install grub2 on ubuntu via the livecd. but since i was booting from the live cd meant that i couldn't bookmark it, and very little on this forum, as far as i can see, gets sticky, makes it very hard to find. 

the basic problem is, i completly reinstalled ubuntu 10.10, and the bootloader (that i now know is named grub2) could not be installed. so i've found several guides, including the wiki, but it haven't really worked.

now instead of explaining all of this over again, like all of you have probably done a million times, can you just post the most informative links here, so i can pick and choose, and eventually inform you what goes wrong from there?

thanks in advance.

---

### Post by hansdown on 2011-02-10
Welcome to the forum, [email]espen.john@gmail.com[/email].

This should help.

[http://www.google.com/search?client=ubuntu&channel=fs&q=installing+grub2+from+live+cd&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=installing+grub2+from+live+cd&ie=utf-8&oe=utf-8)

---

### Post by oldfred on 2011-02-10
Solutions are posted many times here on grub2, but sometimes the issues is unique, so we like to see the boot info script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

See also all the links in drs305's signature line.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by espen.john@gmail.com on 2011-02-10
> **oldfred said:**
> Solutions are posted many times here on grub2, but sometimes the issues is unique, so we like to see the boot info script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

See also all the links in drs305's signature line.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

thank you for the superbe reply. i got the boot info script right here.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   612,853,759   612,851,712  83 Linux
/dev/sda2         612,855,806   625,141,759    12,285,954   5 Extended
/dev/sda5         612,855,808   625,141,759    12,285,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   964,485,119   964,483,072  83 Linux
/dev/sdb2         964,487,166   976,771,071    12,283,906   5 Extended
/dev/sdb5         964,487,168   976,771,071    12,283,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9da1fea9-a012-46b7-b7a9-403318f60012   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f5eab16b-c389-4c04-b246-13ab514bb333   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        03cb871f-0ba2-45bf-a5b7-692c669d5f7e   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        edcb8c11-3747-4358-b875-b7a5ee7ea1dc   swap                                     
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
search --no-floppy --fs-uuid --set 9da1fea9-a012-46b7-b7a9-403318f60012
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 9da1fea9-a012-46b7-b7a9-403318f60012
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9da1fea9-a012-46b7-b7a9-403318f60012
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9da1fea9-a012-46b7-b7a9-403318f60012 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9da1fea9-a012-46b7-b7a9-403318f60012
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9da1fea9-a012-46b7-b7a9-403318f60012 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9da1fea9-a012-46b7-b7a9-403318f60012
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9da1fea9-a012-46b7-b7a9-403318f60012
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10 (10.10) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 03cb871f-0ba2-45bf-a5b7-692c669d5f7e
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdb1
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
UUID=9da1fea9-a012-46b7-b7a9-403318f60012 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f5eab16b-c389-4c04-b246-13ab514bb333 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 272.8GB: boot/grub/core.img
  19.4GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .4GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
    .4GB: vmlinuz

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=03cb871f-0ba2-45bf-a5b7-692c669d5f7e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=edcb8c11-3747-4358-b875-b7a5ee7ea1dc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: boot/vmlinuz-2.6.35-22-generic
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  5e e3 08 df 19 49 0c 24  12 bd e3 e7 99 47 31 88  |^....I.$.....G1.|
00000010  ca a5 45 4a 3c 29 45 94  75 fc 80 7b 64 13 a7 03  |..EJ<)E.u..{d...|
00000020  fa 24 73 9e 66 82 b4 0e  4d ef df cc 1b 11 01 7c  |.$s.f...M......||
00000030  60 7d ea 85 73 47 d8 75  2d d3 27 04 7b 0b c0 1e  |`}..sG.u-.'.{...|
00000040  8f ed 0c 32 98 e8 54 ac  28 8a 96 d4 f2 4b 68 23  |...2..T.(....Kh#|
00000050  b4 8b 2c b9 af 66 0c b2  89 1f 7d e7 ad cf 8b 17  |..,..f....}.....|
00000060  82 36 ba 30 c8 56 81 c1  71 7d c0 fe a3 61 e8 12  |.6.0.V..q}...a..|
00000070  d9 9f 73 d8 bb ec c4 4c  ca 3b 19 4e de 6e 77 92  |..s....L.;.N.nw.|
00000080  f8 8d 66 9e b3 43 0e 47  f5 5f 46 b9 4b 4c e5 88  |..f..C.G._F.KL..|
00000090  53 c6 f7 b5 ab b2 5a 50  40 aa f3 05 8a 77 fa 72  |S.....ZP@....w.r|
000000a0  0f 42 16 d3 61 d9 05 55  2d 9d 08 23 20 2b d0 1b  |.B..a..U-..# +..|
000000b0  48 d1 5c 44 39 8b 08 b8  c0 6b 7f 8c 86 be 60 60  |H.\D9....k....``|
000000c0  c1 94 d3 db 3a 8a c5 c1  02 53 32 22 04 35 a0 9d  |....:....S2".5..|
000000d0  7f b6 84 05 6f d8 ca 18  93 27 d2 fb de d9 61 b8  |....o....'....a.|
000000e0  de 76 19 a0 fc 64 dc 21  3e 85 bf 52 e2 74 ba 77  |.v...d.!>..R.t.w|
000000f0  4a 41 66 2b 20 5c 47 6c  56 a1 bc 32 c8 48 2c 04  |JAf+ \GlV..2.H,.|
00000100  c2 06 ae c8 79 45 71 4e  ed 68 18 ac f5 5e 3a 37  |....yEqN.h...^:7|
00000110  b2 ae b7 d2 93 4f 84 b9  d1 d0 2f bf a5 6b 1c 9f  |.....O..../..k..|
00000120  fb 0c 41 41 22 f5 65 a3  94 93 e7 98 14 0b df 7a  |..AA".e........z|
00000130  e1 b8 ff 01 e6 dc c0 27  9e 1d c3 30 64 8f 22 4e  |.......'...0d."N|
00000140  b7 a4 86 a2 73 e0 3e 9b  f2 fa cd 8a 7a e5 87 8d  |....s.>.....z...|
00000150  75 6d 69 33 a5 00 5c 2d  e2 86 95 de 17 02 19 47  |umi3..\-.......G|
00000160  52 5e b4 ee d4 b2 c2 62  19 24 b7 5a 99 3e d8 52  |R^.....b.$.Z.>.R|
00000170  80 f4 8d c4 55 1d 1f da  73 ce d0 1d dd 4b 6f 61  |....U...s....Koa|
00000180  9c db d1 90 c3 67 d1 02  60 20 0b 43 ed 8a 14 e4  |.....g..` .C....|
00000190  69 c8 b3 6a d5 1d 7d 3d  17 e3 20 ee d6 28 bc c0  |i..j..}=.. ..(..|
000001a0  9e 96 26 b1 bb f2 21 11  fa 4b ef 36 f5 01 1b 43  |..&...!..K.6...C|
000001b0  5a 28 2c e0 e3 68 6c 77  73 0a 08 69 cf a3 00 fe  |Z(,..hlws..i....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  55 e0 55 b7 ce ec f6 b0  db 7c a4 c5 58 65 58 87  |U.U......|..XeX.|
00000010  dc 46 71 47 00 ed 45 21  0e 07 cb 49 49 df 7e 82  |.FqG..E!...II.~.|
00000020  6b 66 63 eb 97 86 de d2  56 da 41 23 68 27 f9 d7  |kfc.....V.A#h'..|
00000030  95 5c 28 f2 8f 98 40 db  8d a7 d7 d4 9a f4 70 90  |.\(...@.......p.|
00000040  71 83 ef 73 92 bb 4a 56  39 79 ee 47 9d ea 0f 43  |q..s..JV9y.G...C|
00000050  ef 4d 89 a4 32 30 60 08  1c 66 bb 5d ec 72 ea 5f  |.M..20`..f.].r._|
00000060  90 87 50 49 04 f6 c7 b5  7b 07 85 2f 5a 7b 24 04  |..PI....{../Z{$.|
00000070  93 b3 e5 38 ae 5c 4c 6f  05 6d d1 b5 29 5a 47 52  |...8.\Lo.m..)ZGR|
00000080  b1 20 0c c8 32 15 8e 30  7a 52 98 14 f2 42 93 90  |. ..2..0zR...B..|
00000090  78 3d 0f 5a f3 12 5a d8  ef 8c 53 bb 64 41 59 9d  |x=.Z..Z...S.dAY.|
000000a0  83 29 2c 7d fa 57 9f f8  a6 24 17 11 87 c8 04 71  |.),}.W...$.....q|
000000b0  8f 5a d7 0d ee d4 4d f7  32 ac bf 77 a1 ca df d9  |.Z....M.2..w....|
000000c0  aa 2b 8f 31 18 11 d1 6b  93 03 e5 da b9 3f 30 e7  |.+.1...k.....?0.|
000000d0  d6 bd a6 d3 d5 1c 1b 1a  46 10 63 da bd 46 4d 36  |........F.c..FM6|
000000e0  15 63 85 39 ce 39 a2 4a  d6 05 b9 03 2a f9 84 0c  |.c.9.9.J....*...|
000000f0  90 1b 8a d0 b7 21 18 70  3a f0 4d 39 21 33 dd d2  |.....!.p:.M9!3..|
00000100  d8 0c 32 8c 31 01 ba 91  d4 77 ab 22 2d ea ad 93  |..2.1....w."-...|
00000110  8e e0 1e 95 e1 4a 1c d1  b4 b4 b1 e8 38 ae 83 91  |.....J......8...|
00000120  51 40 54 3d 0f 04 f7 34  86 32 ec 48 00 f4 ac 93  |Q@T=...4.2.H....|
00000130  4e cb d4 69 f5 02 a3 19  6d d9 1e 9d e9 db 37 0c  |N..i....m.....7.|
00000140  f9 78 00 f4 27 a5 38 a4  e3 6d 49 7a a6 2b 44 c0  |.x..'.8..mIz.+D.|
00000150  6c 27 e9 c7 41 9a 7f d9  c0 45 0d c9 07 19 cd 57  |l'..A....E.....W|
00000160  2a 72 d1 db 40 5b 21 a5  00 3c 33 2b 03 80 08 e0  |*r..@[!..<3+....|
00000170  54 c9 10 55 e9 82 49 04  7a fd 6a 63 f1 3b f4 2e  |T..U..I.z.jc.;..|
00000180  fa 3b 8d 10 03 eb 93 ce  29 3e ce c7 27 0e c3 a7  |.;......)>..'...|
00000190  02 ae 29 59 a4 c3 47 1d  8b 31 da 5c b6 0f 90 e3  |..)Y..G..1.\....|
000001a0  23 1c 71 4b fd 9d 31 3c  47 2b 72 7a ff 00 11 a7  |#.qK..1<G+rz....|
000001b0  cd 6d fa 22 a2 ae f5 1c  fa 35 c1 db b9 76 00 fe  |.m.".....5...v..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 bb 00 00 00  |...........p....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

as i\ve said, i\ve tried the wiki, and it didn\t work, and i have tried chroot & grub uninstall & reinstall -drs305, but i will try that again, incase i was abit to hasty. 
keep me updated if you find something interesting in the boot info script

---

### Post by espen.john@gmail.com on 2011-02-10
yes,i was hasty. finally it worked. they should put the chroot option in the wiki. would save alot of noob hassle. thanks again.

---

### Post by presence1960 on 2011-02-10
In addition to what oldfred gave you [here]("https://help.ubuntu.com/community/Grub2") is another to bookmark

---

### Post by oldfred on 2011-02-10
Did you resolve problem?

Script is ok for install in sda1, but script/grub does not identify drive correctly in MBR so I cannot be sure if booting is sda or sdb. And the install in sdb is not complete, so that install will not work.

A few computers will not boot without a boot flag. Some Intel motherboards, maybe others. Grub does not use boot flag, but if it is a BIOS error then you need a boot flag.

---

### Post by espen.john@gmail.com on 2011-02-13
> **oldfred said:**
> Did you resolve problem?

Script is ok for install in sda1, but script/grub does not identify drive correctly in MBR so I cannot be sure if booting is sda or sdb. And the install in sdb is not complete, so that install will not work.

A few computers will not boot without a boot flag. Some Intel motherboards, maybe others. Grub does not use boot flag, but if it is a BIOS error then you need a boot flag.

well, the original problem is solved, but some other problems have emerged.
everytime i start the computer, the start screen tells me "CMOS checksum error - Defaults loaded" and i press F1 to continue to a working linux. i had this problem on vista as well, but thought by installing linux this problem would be fixed. seems like i was mistaken.
 any ideas? 

and what do you mean by " the install in sdb is not complete, so that install will not work"? can the reason for this be that i have tried to install on both the disks when i booted the computer to see if that fixed anything (figured out it didn't)? or does linux install on both disks? any quick fixes?

oh, and im having problems with amarok. when i try to get my abit-to-big music library in my amarok library, it restarts the computer. im guessing it's the program,but in case you know otherwise, please let me know.

still, appreciate the help.

---

### Post by oldfred on 2011-02-13
Your CMOS error is not related to Windows nor Linux. It is from the BIOS. Not sure if an update or just resaving settings in BIOS would correct it. It is just reverting to some sort of defaults to boot.

---

### Post by espen.john@gmail.com on 2011-02-14
im on it. will have a newly updated bios in no time. no what about the ubuntu install. should reinstall, format or get a quick fix?

---

### Post by oldfred on 2011-02-14
If Ubuntu is working, I would it to not require any changes. But some BIOS settings can cause issues. So if you do have something happen, I would check BIOS settings first.

Sometimes simple things like many BIOS still default to ps/2 ports for mouse & keyboard. You have to change setting for USB keyboard & mouse.

---

