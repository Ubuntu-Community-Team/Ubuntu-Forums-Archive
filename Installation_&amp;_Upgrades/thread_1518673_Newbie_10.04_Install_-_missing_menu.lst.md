---
title: "Newbie 10.04 Install - missing menu.lst"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by Frowzy on 2010-06-26
I installed Ubuntu 10.04 in a partition alongside two other partitions that contain windows.  One is a windows xp recovery partition (about 8 GB) and the other is windows xp media center (about 37 GB).  The Ubuntu partition is about 180 GB.  Anyway, after I installed it, I was only able to boot to Windows XP.  I can't boot to Ubuntu.  

Using supergrub, however, I am able to get Ubuntu to boot up.  In supergrub, I got to Gnu/Linux, select the option to "Boot Gnu/Linux directly", and it works. 

However, if I try the "Fix grub" option, I get "error 15: file not found".  Also, if I try to the option of "Boot to Partition" and I select the Ubuntu partition, I get "error 13: invalid or unsupported exectuable format".

When in Ubuntu, I opened the terminal and tried the following:

gksudo gedit /boot/grub/menu.lst

The menu.lst file is empty.  There is nothing in it.

What is going on?  How can I fix it so when I boot the computer I'm given the option of booting to Windows XP media center or to Ubuntu?

For additional info, I ran the bootinfoscript and the results.txt file is pasted below.  Thanks for your help in advance!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 69. But according to the info from fdisk, 
                       sda5 starts at sector 8643039.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 69. But according to the info from fdisk, 
                       sda8 starts at sector 68260254.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 65. But according to the info from fdisk, 
                       sda9 starts at sector 277892435.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     8,642,969     8,642,907   7 HPFS/NTFS
/dev/sda4           8,642,970   320,159,384   311,516,415   f W95 Ext d (LBA)
/dev/sda5           8,643,039    34,427,294    25,784,256   7 HPFS/NTFS
/dev/sda6          34,427,358    51,311,609    16,884,252   7 HPFS/NTFS
/dev/sda7          51,311,673    68,260,184    16,948,512   7 HPFS/NTFS
/dev/sda8          68,260,254   277,892,369   209,632,116   7 HPFS/NTFS
/dev/sda9         277,892,435   294,824,879    16,932,445   7 HPFS/NTFS
/dev/sda10        294,824,943   311,725,259    16,900,317   7 HPFS/NTFS
/dev/sda11        311,725,323   320,159,384     8,434,062   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    16,798,319    16,798,257   c W95 FAT32 (LBA)
/dev/sdb2    *     16,798,320    94,914,917    78,116,598   7 HPFS/NTFS
/dev/sdb3          94,916,606   488,396,799   393,480,194   5 Extended
/dev/sdb5          94,916,608   482,390,015   387,473,408  83 Linux
/dev/sdb6         482,392,064   488,396,799     6,004,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       309BD0BD201EB4FF                       ntfs       Downloads                     
/dev/sda11       465E-1156                              vfat       Paging                        
/dev/sda1        590CB73342BCB735                       ntfs       Data I                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        69E2FFD0B12E6109                       ntfs       Data II                       
/dev/sda6        28B8BE54BCDAADE9                       ntfs       Pictures                      
/dev/sda7        7F924A0044C9DFAC                       ntfs       Music                         
/dev/sda8        45C81BC18DD6A2BB                       ntfs       Programs                      
/dev/sda9        96610F87601C3A9B                       ntfs       Hal                           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        429B-99B8                              vfat       HP_RECOVERY                   
/dev/sdb2        CE18E8BA18E8A327                       ntfs       HP_PAVILION                   
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d   ext4                                     
/dev/sdb6        be3b7cd8-c289-456e-8627-8363ce8af01e   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 429b-99b8
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set ce18e8ba18e8a327
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=96cdfb4c-976d-418a-9dd3-5d6d8edb8d8d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=be3b7cd8-c289-456e-8627-8363ce8af01e none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 130.3GB: boot/grub/core.img
 132.4GB: boot/grub/grub.cfg
 130.3GB: boot/initrd.img-2.6.32-21-generic
 130.3GB: boot/vmlinuz-2.6.32-21-generic
 130.3GB: initrd.img
 130.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  44 38 36 46 31 43 34 00  35 39 30 31 41 32 45 43  |D86F1C4.5901A2EC|
00000010  00 31 46 45 35 44 37 34  39 fb 75 2a 31 03 b8 f0  |.1FE5D749.u*1...|
00000020  19 7f 2a 7f 2a 7f 2a ff  be bf ff be ff be 7f 55  |..*.*.*........U|
00000030  ff be f9 2c 3d 14 5c 70  c2 ba 69 30 aa 69 34 15  |...,=.\p..i0.i4.|
00000040  5f 2a f3 3f 80 70 0d 67  7f 15 7f 15 75 15 b0 9e  |_*.?.p.g....u...|
00000050  7f 15 71 15 9c 01 78 15  46 41 43 41 35 34 32 00  |..q...x.FACA542.|
00000060  33 36 39 44 34 39 33 36  00 34 32 38 33 31 30 34  |369D4936.4283104|
00000070  39 c0 34 39 35 37 37 33  30 16 75 15 fd 31 03 10  |9.4957730.u..1..|
00000080  f0 04 7f 15 7f 15 71 15  ff 54 ff 54 bf f1 39 ff  |......q..T.T..9.|
00000090  3f ff 3f 7f 2a 7f 2a 7d  2a 57 90 7f a8 64 00 64  |?.?.*.*}*W...d.d|
000000a0  90 2a 6e 30 bf 20 d0 d9  fe 61 90 d9 37 ab 72 3f  |.*n0. ...a..7.r?|
000000b0  70 27 ff 14 ff 14 76 2a  16 9f ff 14 f1 14 a0 f9  |p'....v*........|
000000c0  14 38 43 38 00 36 35 33  35 30 44 31 38 00 42 31  |.8C8.65350D18.B1|
000000d0  36 34 44 41 30 39 08 44  30 45 50 d6 36 41 33 38  |64DA09.D0EP.6A38|
000000e0  cc 33 43 f5 14 31 03 20  a0 7f 3f 7f 3f 7b 73 3f  |.3C..1. ..?.?{s?|
000000f0  f1 0a 28 f0 07 ff 0a ff  0a f5 0a d8 0d ff 0a 00  |..(.............|
00000100  f1 0a f9 9f 32 44 44 35  10 46 45 30 34 31 cb 37  |....2DD5.FE041.7|
00000110  44 45 02 34 20 f1 35 33  41 39 30 30 a8 33 30 43  |DE.4 .53A900.30C|
00000120  70 4b 45 71 07 c8 70 0a  21 71 00 10 a2 0d 01 71  |pKEq..p.!q.....q|
00000130  00 68 a3 09 73 00 a8 a4  73 00 e8 a5 0d 01 67 b5  |.h..s...s.....g.|
00000140  00 68 62 69 6e 00 a0 0d  01 08 00 10 00 12 00 58  |.hbin..........X|
00000150  ff ff ff 00 63 00 3a 00  5c 00 50 00 20 72 00 6f  |....c.:.\.P. r.o|
00000160  00 67 00 14 61 00 00 6d  00 20 00 46 00 69 00 a0  |.g..a..m. .F.i..|
00000170  6c 00 65 00 73 00 36 53  00 32 0a 6e 00 1e 63 00  |l.e.s.6S.2.n..c.|
00000180  16 4d 00 79 00 08 44 00  56 00 06 5c 00 53 00 46  |.M.y..D.V..\.S.F|
00000190  74 00 1a 05 4a 4e 00 54  00 22 43 05 00 46 44 00  |t...JN.T."C..FD.|
000001a0  6e 66 00 61 00 75 2d 00  82 74 00 4b 0b 27 57 00  |nf.a.u-..t.K.'W.|
000001b0  1d 64 00 4a 64 00 4f 6e  00 6f 5c 00 0b 0f 00 fe  |.d.Jd.On.o\.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 18 17 00 fe  |...........`....|
000001d0  ff ff 05 fe ff ff 02 60  18 17 00 a8 5b 00 00 00  |.......`....[...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by cj.surrusco on 2010-06-26
The default for 10.04 is grub2, which means that there won't be any menu.lst since grub2 doesn't use it. To install grub2 to the bootsector, run 
```
sudo grub-install /dev/sdx
```
'sdx' being the drive with Ubuntu on it. (NOT the partition, the whole drive)

Then run 
```
sudo update-grub
```
so that grub will find your Windows installation

Then you should be able to boot into Ubuntu and Windows.

---

### Post by Frowzy on 2010-06-27
Thanks [cj.surrusco]("http://ubuntuforums.org/member.php?u=969779").  That did the trick.

One more thing - the boot menu now gives more options than I want it to.  It shows the windows recovery system and I don't want it too.  A while ago my young son's friend started this computer and mistakenly chose, and ran, the windows XP recovery system -not good.  I'd like to prevent that by not having that option appear.  How do I do that in Grub2?

---

### Post by darkod on 2010-06-27
> **Frowzy said:**
> Thanks [cj.surrusco]("http://ubuntuforums.org/member.php?u=969779").  That did the trick.

One more thing - the boot menu now gives more options than I want it to.  It shows the windows recovery system and I don't want it too.  A while ago my young son's friend started this computer and mistakenly chose, and ran, the windows XP recovery system -not good.  I'd like to prevent that by not having that option appear.  How do I do that in Grub2?

Open /boot/grub/grub.cfg and copy the entry you want for windows into /etc/grub.d/40_custom. Then disable the os-prober with:

sudo chmod -x /etc/grub.d/30_os-prober

To update grub.cfg run:

sudo update-grub

Note: That will prevent grub2 automatically detecting new OS if you install one. You can always enable os-prober again with the same command only using +x instead of -x.

---

### Post by Frowzy on 2010-06-27
Thanks Darkod - everything is working now!

---

### Post by Vuk Matic on 2010-07-30
although i probably wont get an answer, i need to know what you mean by sdx being the whole hard drive? can you give me an example of what i should type in? coz i ve had no luck!

thanks!

---

### Post by cj.surrusco on 2010-07-30
> **Vuk Matic said:**
> although i probably wont get an answer, i need to know what you mean by sdx being the whole hard drive? can you give me an example of what i should type in? coz i ve had no luck!

thanks!

You will get an answer! The 'x' in sdx is a variable. When a hard drive is detected in Ubuntu, it is given a name. The first hard drive would be sda, the second sdb, and so on. So you would need to enter /dev/sda if you only have one drive, or /dev/sdb if Ubuntu is on a secondary drive.

---

