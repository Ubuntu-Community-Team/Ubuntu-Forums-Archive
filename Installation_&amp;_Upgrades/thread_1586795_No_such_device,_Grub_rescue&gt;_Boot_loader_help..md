---
title: "No such device, Grub rescue&gt; Boot loader help."
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by xieon on 2010-10-02
I've gone through a ton of threads trying to find the solution and so far have come up with nothing that works, hopefully from the individual data I post someone can help, also forgive me but I don't know anything about linux.

I am dual booting xp/ubuntu, I upgraded fron 10.04 to 10.10 and as a result messed up my bootloaer, now upon startup I get this message:
```
Error no such device b49c7330-fa14-4c7a-80c3-5217ac2caa3a
grub rescue>
```I have a windows restore cd, but I'm stuck at a dead end because to restore I need a password I forgot. So I have to fix this through linux.

Here's the output from the fdisk -l and bootinfo script respectively.

```
[B]Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b5d9b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5168    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000448ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18757   141797691    7  HPFS/NTFS
/dev/sdb2   *       18757       29566    81721237+   7  HPFS/NTFS
/dev/sdb3           29567       32301    20676600    f  W95 Ext'd (LBA)
/dev/sdb5           29567       32301    20676568+   7  HPFS/NTFS
[/B]
```I also ran a boot info script and got the following, seems that they are looking in the wrong place when booting.
```
Boot Info Script 0.55    dated February 15th, 2010                    
sudo bash ~/Desktop/boot_info_script*.sh 
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sudo grub-install --root-directory=/mnt /dev/sda 
sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 453627591 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

[COLOR=Red]sdb5/Wubi: _________________________________________________________________________
[/COLOR] 
    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5/Wubi 
                       and looks at sector 8910552 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   283,595,444   283,595,382   7 HPFS/NTFS
/dev/sdb2    *    283,595,445   447,037,919   163,442,475   7 HPFS/NTFS
/dev/sdb3         447,037,920   488,391,119    41,353,200   f W95 Ext d (LBA)
/dev/sdb5         447,037,983   488,391,119    41,353,137   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
**[COLOR=Red]/dev/loop1       b49c7330-fa14-4c7a-80c3-5217ae2caa3a   ext4   [/COLOR]    **                              
/dev/sda1        69A4175722DE71C1                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C470595C70595670                       ntfs       New Volume                    
/dev/sdb2        AE9C0BC59C0B8755                       ntfs       Entertainment2                
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        01CB612C09D1F0C0                       ntfs       Ubuntu                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /AVASTBOOT

C:\wubildr.mbr = "Ubuntu"


=================== sdb5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sdb5/Wubi/boot/grub/grub.cfg: ========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ntfs
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 01cb612c09d1f0c0
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 01cb612c09d1f0c0
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 01cb612c09d1f0c0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 01cb612c09d1f0c0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 01cb612c09d1f0c0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 01cb612c09d1f0c0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 69a4175722de71c1
    drivemap -s (hd0) ${root}
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

============================= sdb5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sdb5/Wubi: Location of files loaded by Grub: =================


   4.5GB: boot/grub/core.img
   8.9GB: boot/grub/grub.cfg
   1.8GB: boot/initrd.img-2.6.32-25-generic
  14.9GB: boot/initrd.img-2.6.35-22-generic
   4.7GB: boot/vmlinuz-2.6.32-25-generic
   4.9GB: boot/vmlinuz-2.6.35-22-generic
  14.9GB: initrd.img
   1.8GB: initrd.img.old
   4.9GB: vmlinuz
   4.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  a9 b3 2b 48 ea 76 a9 18  fa b7 3b 4a 04 68 98 31  |..+H.v....;J.h.1|
00000010  12 aa 95 9e 5d 18 8d 95  66 5a b5 5e b2 4c f3 83  |....]...fZ.^.L..|
00000020  0a c2 b2 37 33 75 d9 07  1e 83 34 3b 3a 1e 58 dd  |...73u....4;:.X.|
00000030  3a 2d 1e 1d 79 de 8f b9  cc 3c d7 30 29 d1 02 c9  |:-..y....<.0)...|
00000040  e8 dd 5e f7 4f 49 46 06  db b3 23 37 9f 93 ad 31  |..^.OIF...#7...1|
00000050  f7 5d ab d5 a8 da 1e 46  93 9d b9 99 bd de e8 a9  |.].....F........|
00000060  0c 98 c6 7f 7e 91 b6 dc  21 5b 01 5e 2a 9f d5 ad  |....~...![.^*...|
00000070  ee 56 f9 dc db bf 4a 89  cd 71 91 9b ca a4 ca b3  |.V....J..q......|
00000080  98 44 93 e7 49 00 ae 42  12 8f aa 12 87 c3 e1 29  |.D..I..B.......)|
00000090  56 0f bd 9e e4 9b bd b9  2d b5 3f 95 e5 02 6f 49  |V.......-.?...oI|
000000a0  de 2e 82 ac b7 09 15 ab  fd fd d7 c8 7d cc e0 82  |............}...|
000000b0  24 81 61 a4 0b 2f 8c a5  3d 2a 6b 85 2b a4 e1 d5  |$.a../..=*k.+...|
000000c0  53 f7 e2 25 f2 aa b6 4f  ff 8b e7 76 26 31 e6 cc  |S..%...O...v&1..|
000000d0  02 18 a7 14 f8 80 b3 3f  8d 2a aa 62 f1 a6 3f 67  |.......?.*.b..?g|
000000e0  ee 89 f9 f6 75 71 ef f3  a9 6f 34 69 55 68 f6 2a  |....uq...o4iUh.*|
000000f0  f0 f9 65 13 da 3d b8 bd  ff 2b 95 c1 24 49 80 80  |..e..=...+..$I..|
00000100  08 3e f8 f7 e2 49 7a aa  3c aa ec b8 9a 78 98 0e  |.>...Iz.<....x..|
00000110  38 0a 71 d4 62 03 8a 16  8f a2 2f ac ad 76 c9 46  |8.q.b...../..v.F|
00000120  4a fb 2d f7 29 7a af d9  f9 0a e1 04 85 f1 5f cb  |J.-.)z........_.|
00000130  d6 e7 7d 63 69 88 19 3a  60 2d 92 38 e2 01 85 79  |..}ci..:`-.8...y|
00000140  e0 22 44 39 c2 75 d3 b3  18 f1 2d 5b 38 37 ea 0e  |."D9.u....-[87..|
00000150  38 19 04 5c 05 30 54 0e  bd 82 a1 80 c3 e1 27 42  |8..\.0T.......'B|
00000160  08 92 a8 21 4b 9e 9d 57  63 32 37 e6 db b0 5c 08  |...!K..Wc27...\.|
00000170  51 44 c9 99 35 ae 7b 9d  44 ae 90 83 78 20 7b e5  |QD..5.{.D...x {.|
00000180  df b7 8a ff f9 b7 e9 b9  66 e7 62 b6 08 3d 6e 2e  |........f.b..=n.|
00000190  8d ba 37 30 25 7a 19 2f  fd c8 78 29 87 3d f1 7e  |..70%z./..x).=.~|
000001a0  04 20 87 e9 96 fe fa 7e  15 b2 06 f2 d3 a1 00 10  |. .....~........|
000001b0  6d f0 95 8c 7f 89 54 49  2a 3e e9 f0 0e 08 00 ef  |m.....TI*>......|
000001c0  ff ff 07 ef ff ff 3f 00  00 00 b1 ff 76 02 00 00  |......?.....v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```I noticed a few things I put in red.

There seems to be two errors of the drives looking in the wrong place for things, and there is a loop that corresponds to the uuid of the missing device?

Any help would be great, I've spent two days searching for answers

---

### Post by xieon on 2010-10-02
> **garvinrick4 said:**
> Lets get Windows booting first and then get Ubuntu booting.
Put in Live Cd and in Terminal:
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Now take out CD and boot into windows

I was having this same problem, and this worked perfect. Restored my mbr, then I was able to reinstall Ubuntu because the version I had was corrupted.

---

### Post by miclozada on 2010-10-03
i have to many kernel to boot because of upgrade. i want to delete the old ones but i dont know haw to? is anyone can help me? i cant find also the boot loader??? my latest ver. is ubuntu 10.04 (lucid) kernel 2.6.32-25-generic. pls help me...pinoy ako! [email]miclozada@yahoo.com[/email]

---

