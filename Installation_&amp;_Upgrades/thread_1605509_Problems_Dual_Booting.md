---
title: "Problems Dual Booting"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Rellik Faros on 2010-10-25
Hi all.  First post here, so please be kind! :D
 
Anyways, I'm trying to run a multi-boot of Windows 7 Ultimate 32bit and Ubuntu 10.10 on my laptop.  I've made all my partitions and whatnot, and I'm able to install the OS with no real problems, but when I turn on my computer, I don't get a Multi-Boot selection menu, and the computer loads straight to Windows 7.
 
This is my first time trying to install set up a multi-boot, but after reading some of the guides I've found for dual booting the two systems off Google, I don't understand where I've gone wrong.  Any help would be greatly appreciated.

---

### Post by Rubi1200 on 2010-10-25
Hi and welcome to the forums :)

Please use a LiveCD or LiveUSB to boot the computer and then follow the instructions in the link at the bottom of my post.

Wrap the text with the # tag when posting the results back here.

The script will hopefully tell us what went wrong and then we can advise you as to how best to proceed.

Thanks.

---

### Post by Sef on 2010-10-25
> Hi all. First post here, so please be kind! 


If anyone is not kind, please click the report abuse button on the lower left.

> I don't get a Multi-Boot selection menu, and the computer loads straight to Windows 7.

Did you load Windows 7 last?

Also download [Boot Script Info]("http://bootinfoscript.sourceforge.net/") and run it.

---

### Post by Rellik Faros on 2010-10-25
> **Sef said:**
>  
Did you load Windows 7 last?
 
Also download [Boot Script Info]("http://bootinfoscript.sourceforge.net/") and run it.No, I installed Win7 first, since that was what pretty much every dual-boot guide I found said to do.  
 
As for running BSI, I'll have to get back to you on that, since I'm at school right now, and my college's network doesn't allow for downloading.  
 
Just so I'm sure I understand what you're asking me to do though, you want me to boot from the CD, and instead of going to the install option, you want me to use the Try Ubuntu without Installing option.  Then, you want me to run BSI from there.  That about right?

---

### Post by Rubi1200 on 2010-10-25
That's exactly what you need to do.

Please wrap the text with the # tag (which you can find on the menu bar) when you post the results back here.

---

### Post by kansasnoob on 2010-10-25
> **Rellik Faros said:**
> No, I installed Win7 first, since that was what pretty much every dual-boot guide I found said to do.  
 
As for running BSI, I'll have to get back to you on that, since I'm at school right now, and my college's network doesn't allow for downloading.  
 
Just so I'm sure I understand what you're asking me to do though, you want me to boot from the CD, and instead of going to the install option, you want me to use the Try Ubuntu without Installing option.  Then, you want me to run BSI from there.  That about right?

Yes. There are alternative instructions here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Rellik Faros on 2010-10-25
Okay, so I did what you guys said, and here's the info from the RESULT.txt that BSI spat out.  

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,802,047   204,595,200   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2AA0563CA0560EA7                       ntfs       System Reserved               
/dev/sda2        70D0B308D0B2D396                       ntfs       Windows 7                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

So there's that.  Any clue what my issue is?

---

### Post by Rubi1200 on 2010-10-25
>  Any clue what my issue is?Yes, Ubuntu is not installed on your system. 

Where did you try and create a partition?

Did you try installing using Wubi?

There is no evidence of an install here other than Windows.

---

### Post by Rellik Faros on 2010-10-25
> **Rubi1200 said:**
> Yes, Ubuntu is not installed on your system. 

Where did you try and create a partition?

Did you try installing using Wubi?

There is no evidence of an install here other than Windows.

Huh.  That's odd.  I had asked a friend to take a look at it to see what the problem was.  I guess maybe he deleted the partitions or something?  Anyways, no big, I'll just reinstall it and get back to you.  Shouldn't take me too long.

---

### Post by Rellik Faros on 2010-10-25
Right then, here's the fixed RESULT.txt output.  

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 305744912 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,802,047   204,595,200   7 HPFS/NTFS
/dev/sda3         204,802,048   341,520,383   136,718,336  83 Linux
/dev/sda4         341,522,430   347,379,711     5,857,282   5 Extended
/dev/sda5         341,522,432   347,379,711     5,857,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2AA0563CA0560EA7                       ntfs       System Reserved               
/dev/sda2        70D0B308D0B2D396                       ntfs       Windows 7                     
/dev/sda3        1afa2787-199b-40b1-a1e5-36be4d4a291c   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        41795049-072a-4fa2-aeed-8d93a1be479e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 1afa2787-199b-40b1-a1e5-36be4d4a291c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 1afa2787-199b-40b1-a1e5-36be4d4a291c
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 1afa2787-199b-40b1-a1e5-36be4d4a291c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1afa2787-199b-40b1-a1e5-36be4d4a291c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 1afa2787-199b-40b1-a1e5-36be4d4a291c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1afa2787-199b-40b1-a1e5-36be4d4a291c ro single 
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 1afa2787-199b-40b1-a1e5-36be4d4a291c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 1afa2787-199b-40b1-a1e5-36be4d4a291c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2aa0563ca0560ea7
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=1afa2787-199b-40b1-a1e5-36be4d4a291c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=41795049-072a-4fa2-aeed-8d93a1be479e none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 156.5GB: boot/grub/core.img
 109.3GB: boot/grub/grub.cfg
 105.8GB: boot/initrd.img-2.6.35-22-generic
 156.5GB: boot/vmlinuz-2.6.35-22-generic
 105.8GB: initrd.img
 156.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  80 28 28 99 41 ea 37 a9  69 eb 96 b6 80 57 5a 36  |.((.A.7.i....WZ6|
00000010  a8 18 88 29 d8 6c ed 3b  f8 4c 0c fb ab 1e 98 b9  |...).l.;.L......|
00000020  08 59 82 55 57 95 7a 2a  8a 9b 3d 22 a5 50 c7 6a  |.Y.UW.z*..=".P.j|
00000030  e6 c7 5e 5a 70 d0 ea 08  07 80 f2 aa df 9d c3 e1  |..^Zp...........|
00000040  4e 87 f1 6a f5 76 70 94  19 e0 c1 99 d7 05 31 53  |N..j.vp.......1S|
00000050  be 08 57 f4 bb a7 0f 7d  a3 af 57 4d 09 4a b6 db  |..W....}..WM.J..|
00000060  5e 1c c4 3d b1 d0 9c 78  d8 4e 70 b0 b8 30 f7 07  |^..=...x.Np..0..|
00000070  43 09 12 0c 43 35 73 f8  7e 6e 1b 4d 06 03 30 cc  |C...C5s.~n.M..0.|
00000080  fe 1b 0a 3b 2a c3 32 e1  fd 6a 33 5f f3 5e 33 fc  |...;*.2..j3_.^3.|
00000090  1d 6a ef 0a 76 ae 9e a3  c1 16 88 ef b3 0c 8f d5  |.j..v...........|
000000a0  03 1d 86 58 d1 a0 0d 05  02 cc 44 92 9f 33 4f a0  |...X......D..3O.|
000000b0  a4 68 f4 76 9a 70 73 15  3e c7 42 65 cd 04 e5 6f  |.h.v.ps.>.Be...o|
000000c0  0c c0 f8 5e c0 65 80 d5  09 ad 8c 52 df 6c 19 be  |...^.e.....R.l..|
000000d0  5a ca 2b 90 61 bc 90 07  84 c6 74 40 e2 80 a0 4f  |Z.+.a.....t@...O|
000000e0  80 6e 7d 48 38 3b 3e 14  4c bf 7c 66 63 3a 76 18  |.n}H8;>.L.|fc:v.|
000000f0  a6 17 24 4d 04 e2 ae ed  19 17 2b fa 98 78 7d ef  |..$M......+..x}.|
00000100  61 bd 55 c3 83 36 5d 51  31 54 84 ca 28 f1 5b 8b  |a.U..6]Q1T..(.[.|
00000110  cc ef 5c 75 36 99 3c af  4f 2b e4 74 bf 3a 33 32  |..\u6.<.O+.t.:32|
00000120  36 60 e7 fd 36 00 47 00  21 c9 57 50 dc ff 5d 4d  |6`..6.G.!.WP..]M|
00000130  a6 38 de 39 5e be 9a 00  b0 a6 6c 28 8f fc ad 87  |.8.9^.....l(....|
00000140  80 7b 7c 76 d3 ca c7 df  c3 a1 70 5e 14 4c ba 78  |.{|v......p^.L.x|
00000150  75 74 e9 f7 b8 2a db 3e  19 bd c1 c6 f0 56 dc a1  |ut...*.>.....V..|
00000160  5f 3f 29 82 f1 f9 81 28  48 69 ee 2c f0 5d 90 fd  |_?)....(Hi.,.]..|
00000170  cf 0a ee 85 e7 86 41 93  c2 94 65 6f 9f 00 b7 06  |......A...eo....|
00000180  4f 43 16 04 59 ee 19 ac  f8 33 f7 84 20 c1 99 7e  |OC..Y....3.. ..~|
00000190  13 b8 46 26 55 ce b7 c0  10 e7 8e 42 21 fb 3f ff  |..F&U......B!.?.|
000001a0  1a 00 ff 0f fc ac 47 38  e0 23 20 da 60 5a 18 b8  |......G8.# .`Z..|
000001b0  7a da 57 7c 4b 0d 04 84  f9 e5 71 60 8c f0 00 fe  |z.W|K.....q`....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 59 00 00 00  |...........`Y...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2010-10-25
Everything looks fine except for this:
> Grub 2 is installed in the boot sector of [COLOR=Red]sda3[/COLOR] and 
                       looks at sector 305744912 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.GRUB should not be installed to the partition but rather to the MBR (Master Boot Record) of the drive where it is installed; in this case sda.

There is a simple fix to reinstall GRUB:

From the LiveCD run these commands:
```
sudo mount /dev/sda3 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```After rebooting run ```
sudo update-grub
``` in Ubuntu.

---

### Post by Rellik Faros on 2010-10-25
Thanks, that seemed to do it! :D

---

### Post by Rubi1200 on 2010-10-25
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

