---
title: "Cannot restore grub, nor reinstall ubuntu after reinstalling windows"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by linkinsebas on 2010-11-18
Hello to all comunity members. I run a dual/boot machine with windows 7 and ubuntu 10.10x64. Yesterday, I reinstalled Windows, and then tried to restore grub. I followed all the procedures listed here [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") but none of them worked (windows still was loading at boot). The I decided to reinstall ubuntu (which implies formatting the ext4 and swap partitions), but even after that grub still does not appear. 

I read somewhere that executing a script from meierfra could help, but I cannot get anything useful from the output (sorry, I am kind of a noob). Hope anyone can get something:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   215,029,822   215,029,760   7 HPFS/NTFS
/dev/sda2         215,031,806   312,580,095    97,548,290   5 Extended
/dev/sda5         304,582,656   312,580,095     7,997,440  82 Linux swap / Solaris
/dev/sda6         215,031,808   263,858,175    48,826,368  83 Linux
/dev/sda7         263,860,224   304,574,463    40,714,240  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16011542528 bytes
32 heads, 63 sectors/track, 15512 cylinders, total 31272544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    31,272,191    31,272,129   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7C14DB5A14DB164C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d70fe970-a1ef-4002-ad7d-45a8de4d78df   swap                                     
/dev/sda6        6268f341-501e-4f68-8f06-48c5038c9acb   ext4                                     
/dev/sda7        1ce86d98-0e0c-473b-acec-9a12e4ebc15f   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C8D0ACD8D0ACCE4E                       ntfs       Documentos                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9E6B-3C84                              vfat       SEBASTIAN                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 6268f341-501e-4f68-8f06-48c5038c9acb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 6268f341-501e-4f68-8f06-48c5038c9acb
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6268f341-501e-4f68-8f06-48c5038c9acb
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6268f341-501e-4f68-8f06-48c5038c9acb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6268f341-501e-4f68-8f06-48c5038c9acb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6268f341-501e-4f68-8f06-48c5038c9acb ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6268f341-501e-4f68-8f06-48c5038c9acb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6268f341-501e-4f68-8f06-48c5038c9acb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7c14db5a14db164c
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c8d0acd8d0acce4e
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6268f341-501e-4f68-8f06-48c5038c9acb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=1ce86d98-0e0c-473b-acec-9a12e4ebc15f /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=d70fe970-a1ef-4002-ad7d-45a8de4d78df none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 125.3GB: boot/grub/core.img
 119.0GB: boot/grub/grub.cfg
 110.7GB: boot/initrd.img-2.6.35-22-generic
 125.3GB: boot/vmlinuz-2.6.35-22-generic
 110.7GB: initrd.img
 125.3GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  eb 58 6e c3 0f ff d0 65  bf 6e ff a4 a3 6d 86 1f  |.Xn....e.n...m..|
00000010  f4 97 7c 30 d7 fd 55 b6  1b af f8 bb 87 af a4 95  |..|0..U.........|
00000020  d8 ff d5 dd 2f fd dd 7f  49 f2 5b 57 d2 ed b8 75  |..../...I.[W...u|
00000030  fe bd 86 bf a5 77 0c 3a  fa d1 91 57 76 1b af ea  |.....w.:...Wv...|
00000040  ae ec 7e 4d 02 17 0b eb  bb 0d 7a 17 49 77 c3 ff  |..~M......z.Iw..|
00000050  e9 2b 70 ff f5 de da f5  a5 5d b9 de 7e d7 d2 7b  |.+p......]..~..{|
00000060  4f ce f8 7d 2e f2 67 df  fa f7 74 2c 89 06 c1 fa  |O..}..g...t,....|
00000070  aa f6 c3 51 fd 55 bb 7a  f5 de db aa a5 4b f7 ff  |...Q.U.z.....K..|
00000080  ed d3 a3 25 35 f5 a7 b4  1a 23 92 d1 03 40 ce 39  |...%5....#...@.9|
00000090  87 20 83 94 39 27 26 e5  6f 34 b6 b7 bc c8 90 0d  |. ..9'&.o4......|
000000a0  74 8a e4 02 fe 85 bb 6f  08 82 41 0d 03 90 71 c9  |t......o..A...q.|
000000b0  8e 40 d0 30 b5 2b d8 35  75 f0 6f 04 44 4e 11 37  |.@.0.+.5u.o.DN.7|
000000c0  18 45 c3 19 92 58 32 52  f7 06 d2 08 11 56 29 37  |.E...X2R.....V)7|
000000d0  1b 09 99 2c 83 72 18 6c  f4 dd 9d d8 3e 10 20 c3  |...,.r.l....>. .|
000000e0  26 e2 62 e6 4a a0 b9 1b  06 20 8a 7a ee 0d c8 6c  |&.b.J.... .z...l|
000000f0  90 10 20 61 83 0d 23 20  b0 72 14 09 8e af 3b 40  |.. a..# .r....;@|
00000100  98 41 03 60 c3 c1 10 eb  20 e9 ef 61 b5 41 30 c3  |.A.`.... ..a.A0.|
00000110  0f 08 84 d9 a8 3e a6 45  76 e7 75 16 90 6c 30 f0  |.....>.Ev.u..l0.|
00000120  44 5d 9c 3f 5d e0 de 10  4d 86 d2 04 10 32 26 c4  |D].?]...M....2&.|
00000130  e9 57 c3 74 90 61 86 1e  08 10 30 fd 53 d8 c8 e4  |.W.t.a....0.S...|
00000140  2a 13 6d e1 02 0c 1e be  de 92 0d b7 84 08 18 7d  |*.m............}|
00000150  55 f5 49 b0 de 10 41 87  4a ab bc 24 db 69 04 10  |U.I...A.J..$.i..|
00000160  30 ff ef a4 db 78 41 06  1d ad 6f d0 4d b6 21 02  |0....xA...o.M.!.|
00000170  0c 3a ae f6 92 4c 36 c2  08 37 3b 1a ea ab 7d 27  |.:...L6..7;...}'|
00000180  6d 20 c3 a0 fd 6f e9 b6  c2 0a ed d2 d7 7a b6 da  |m ...o.......z..|
00000190  0a 1c 30 fa df 54 9b 6c  20 91 6e 1c 31 eb bd 1a  |..0..T.l .n.1...|
000001a0  d2 4d b6 12 48 37 69 6a  f6 96 9d b4 88 d6 ac 38  |.M..H7ij.......8|
000001b0  6f 17 b1 0a 95 b6 82 d2  0d c3 75 be ad b6 00 fe  |o.........u.....|
000001c0  ff ff 82 fe ff ff 02 70  56 05 00 08 7a 00 00 fe  |.......pV...z...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 08 e9 02 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

Note: Disk sda is supposed to hold windows and ubuntu, Disk sdb is a disk only for documents (I don't know why it is recognized as a Windows partition, there is no OS there) and sdc is a USB drive from which I am running an image of the Live disk.

Please help, I don't know what else to do, and I need ubuntu to do some work. Thanks.

---

### Post by krishnandu.sarkar on 2010-11-18
You may try this once : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by drs305 on 2010-11-18
linkinsebas,

Welcome to the Ubuntu forums.

Your RESULTS.txt looks normal. It appears you do still have at boot files on sdb. 

Even though it may be booting to your sda Windows install, it may be reading the sdb bootloader on startup. Please check your BIOS settings to see if it is booting sdb first. If it is, you must either change it to sda or install Grub2 on sdb as well.

---

### Post by linkinsebas on 2010-11-18
drs305,

You were right, BIOS was loading sdb first [IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG] Thank you! 
Haven't thought of that one, I feel really stupid right now.. As I said, I formatted my ubuntu partition.... Now I have to update all and install all my stuff from scratch... This will be a long day...

Is there any way of erasing the bootloader from sdb, so this doesn't happen again?

---

### Post by drs305 on 2010-11-18
> **linkinsebas said:**
> 
Is there any way of erasing the bootloader from sdb, so this doesn't happen again?

You can write Testkdisk to the MBR, which removes whatever bootloader is installed. I can give you the commands if you want.

An easier solution would be to install Grub to the sdb MBR as well. It can be on both and will still boot your sda Ubuntu (although it won't be used unless you change the BIOS boot order again). It could even be helpful should your sda MBR become corrupted for some reason.

If you wish to write it to the sdb MBR as well:
```
sudo grub-install /dev/sdb
```
That's all there is to it.

Once you don't have any more requests or questions, please mark the thread 'SOLVED' via the Thread Tools link near the top right of the first post.

---

### Post by linkinsebas on 2010-11-18
Thanks drs305, I think I will install grub on sdb too.

---

### Post by nooodles on 2010-11-27
> **krishnandu.sarkar said:**
> You may try this once : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Thank you much. 
I had to reinstall windows on my dual boot system when it died...
Checking to reinstall Grub and your link was fine.  Method 1 .. ftw.

Thank you much.

---

