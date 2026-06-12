---
title: "boot.ini bootloader not grub"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by green-fresh on 2011-02-17
Hello all 
i'm a new user to ubuntu and Linux and open-source community , from 5 days later i have installed ubuntu 10.10 with windows xp installed first . using the normal installation ,not the wubi , when i rebooted the pc nothing happen the window was loaded normally even if i press esc or f8 when i turn on my pc, ubuntu is not included in the list  ,just xp is there,  
-i tried to see menu.lst using live cd but it was empty.
-i tried to reinstall grub but it did't worke i had this in the terminal 

```

ubuntu@ubuntu:~$ sudo mount /dev/sdb1/mnt
mount: can't find /dev/sdb1/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 
```-i tried to renistall ubuntu a gain in a right steps but it didn't work .
-i used 
sudo bash ~/Desktop/boot_info_script*.sh
and i had this result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    75,188,223    75,186,176  83 Linux
/dev/sdb2          75,190,270    78,163,967     2,973,698   5 Extended
/dev/sdb5          75,190,272    78,163,967     2,973,696  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        EAC4D94CC4D91C1F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6b171e22-78dd-4a56-afde-514cbf5efa66   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        c1cb1321-822b-4f1e-8db8-f8d7cfbd5bd1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/EAC4D94CC4D91C1F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/6b171e22-78dd-4a56-afde-514cbf5efa66 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

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
search --no-floppy --fs-uuid --set 6b171e22-78dd-4a56-afde-514cbf5efa66
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6b171e22-78dd-4a56-afde-514cbf5efa66
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
    search --no-floppy --fs-uuid --set 6b171e22-78dd-4a56-afde-514cbf5efa66
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b171e22-78dd-4a56-afde-514cbf5efa66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6b171e22-78dd-4a56-afde-514cbf5efa66
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b171e22-78dd-4a56-afde-514cbf5efa66 ro single 
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
    search --no-floppy --fs-uuid --set 6b171e22-78dd-4a56-afde-514cbf5efa66
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6b171e22-78dd-4a56-afde-514cbf5efa66
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set eac4d94cc4d91c1f
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
UUID=6b171e22-78dd-4a56-afde-514cbf5efa66 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c1cb1321-822b-4f1e-8db8-f8d7cfbd5bd1 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  15.1GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
  15.3GB: boot/vmlinuz-2.6.35-22-generic
    .7GB: initrd.img
  15.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  2a eb ca a1 0a b0 eb 0d  55 5e 82 da be fd df ad  |*.......U^......|
00000010  3c e4 1c 18 3d 2d 6a 22  c7 b8 1d 15 bd f6 87 93  |<...=-j"........|
00000020  f5 fb bd 2d e3 08 d6 b1  cd 9b 49 79 00 92 66 19  |...-......Iy..f.|
00000030  94 23 19 6e e2 c1 b0 da  e5 66 b1 2a cf 76 71 72  |.#.n.....f.*.vqr|
00000040  dc b9 4d ff 7e 5c 64 b4  ec a3 ba 1d 3e 5a e0 d9  |..M.~\d.....>Z..|
00000050  7a 81 c6 47 bb 84 3b 1d  2c d3 89 75 24 bc f1 85  |z..G..;.,..u$...|
00000060  65 d0 59 cf 48 7d a6 56  c1 66 16 5d 48 aa bc ca  |e.Y.H}.V.f.]H...|
00000070  08 a7 51 b1 e6 76 f1 d4  bd 02 f4 6e 62 d8 da dc  |..Q..v.....nb...|
00000080  3c 6e b9 eb c5 a3 59 c6  13 d7 26 b8 c6 82 41 3a  |<n....Y...&...A:|
00000090  69 cd 2b 24 c1 da 19 c2  c5 66 a8 c5 bd c6 21 bc  |i.+$.....f....!.|
000000a0  14 4d fc 1b 6b fa 16 46  53 fe d4 ab 87 e7 44 1a  |.M..k..FS.....D.|
000000b0  5f 34 c2 40 10 82 c2 e5  a8 39 5f e7 b1 25 ba 1a  |_4.@.....9_..%..|
000000c0  71 e4 3e b2 b3 6e 69 c7  f6 da d0 9c 13 93 65 ad  |q.>..ni.......e.|
000000d0  9d 3e 3a db 9e f7 76 18  7b 28 f5 6f c1 13 2a 8a  |.>:...v.{(.o..*.|
000000e0  3e 92 c0 be fa 74 e1 04  3e 4b 92 7d 6d b8 51 38  |>....t..>K.}m.Q8|
000000f0  d7 c6 d9 52 5f 4b 4c b8  62 75 8f 2f 8d bb 6a c6  |...R_KL.bu./..j.|
00000100  47 28 35 db 43 cb f7 93  9d 2a 83 0a ad 05 57 23  |G(5.C....*....W#|
00000110  ea be 85 43 b3 17 f5 a5  5b 49 53 09 3f ce f9 7d  |...C....[IS.?..}|
00000120  0f 9c bc 23 c6 5e ab 84  d2 80 e5 d1 64 58 db 00  |...#.^......dX..|
00000130  9f 3c e6 79 b3 21 50 c7  cf 5f 31 11 d6 6b fe 38  |.<.y.!P.._1..k.8|
00000140  51 0e 0b e1 a5 bf 21 66  41 51 9d 85 81 41 15 55  |Q.....!fAQ...A.U|
00000150  c0 97 48 e5 ae 01 19 0c  27 03 63 ae 25 fd 81 5d  |..H.....'.c.%..]|
00000160  56 6a c0 3e 50 10 a6 c4  09 1e 5d d3 40 9f 8a 9e  |Vj.>P.....].@...|
00000170  86 9c 5a db 04 69 82 8c  c9 e7 38 2f 9b db 09 92  |..Z..i....8/....|
00000180  a1 2d 3f 32 33 d6 ac af  0c 2a 70 aa 72 3b 7a 88  |.-?23....*p.r;z.|
00000190  bd fd a4 67 61 d5 71 57  e2 02 08 8b 3e 63 52 0e  |...ga.qW....>cR.|
000001a0  05 d1 24 61 3b fc 28 91  2b 2e 59 12 71 83 12 b6  |..$a;.(.+.Y.q...|
000001b0  0b cd 61 7e ad 89 5d a4  ea 10 1b 85 20 03 00 fe  |..a~..]..... ...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 2d 00 00 00  |...........`-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```so what i shall do to make the boot loader from grub not from boot.ini .

by the way my xp is in sda and ubuntu in sdb .

thanks and i'm sorry for this long question 

yahya!

---

### Post by oldfred on 2011-02-17
Have you changed BIOS to boot the sdb or 40GB drive? Does your BIOS let you change boot in BIOS or do you have to change jumpers on hard drive to make it primary master?

You are missing a space:
sudo mount /dev/sdb1/mnt

Should be as you have two parameters:
sudo mount /dev/sdb1 /mnt

---

### Post by green-fresh on 2011-02-18
thanks **oldfred** for you replay but :

> Should be as you have two parameters:
sudo mount /dev/sdb1 /mnt 	
i still have the same result 

> Have you changed BIOS to boot the sdb or 40GB drive? Does your BIOS let  you change boot in BIOS or do you have to change jumpers on hard drive  to make it primary master?


when i change the 1st boot to dh1(40 GB device where ubuntu is installed) and restart the pc it return to the default which is
1st boot CD-room
2nd boot disabled
3rd boot dh0

---

### Post by oldfred on 2011-02-18
Since I fully converted to SATA 3 years ago, I have not experimented with IDE drives. Even if your BIOS lets you set boot drive, do you have to have jumpers set to primary master. Or do you have the 80 conductor cable with cable select.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by green-fresh on 2011-02-18
tank you olfred but :
is this  the only solution ? 
is it a hardware bug from ubuntu ?.
can't any one tell me a software solution  please!

---

### Post by oldfred on 2011-02-18
I normally like to install grub to the same drive as the install, so each drive boot independently.  But if only one drive in the IDE chain is bootable, then you have to install grub2 to sda.

---

