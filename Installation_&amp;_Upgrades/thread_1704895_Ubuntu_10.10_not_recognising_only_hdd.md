---
title: "Ubuntu 10.10 not recognising only hdd"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by richard.j.hughes on 2011-03-11
Hello All
 
I am trying to install a fresh install of Ubuntu 10.10, but I am finding it is not recognising my only HDD in the machine. It is working because I am running Windows 7 x64 on it.
 
I have looked around the forums, but I am not sure what really to try.
 
Here are my machine specs:
 
CPU: AMD Athlon 64 X2 5600+
Motherboard: XFX MI-A78U-8309 GeForce 8300
Graphics Card: NVIDIA GeForce 8300 + 8400
HDD: WDC WD5001AALS-00L3B2 ATA (~415GB)
 
The installation knows when my IDE drive is plugged in, but I want to install the boot sector in the WDC drive.
 
WUBI also fails to install on this current drive, though can setup the boot sector OK.
 
Thank you very much for all of your time and help,
 
Richard Hughes

---

### Post by Rubi1200 on 2011-03-11
Hi and welcome to the forums :-)

Please do the following from a LiveCD/USB:

choose to try not install.

go to Applications > Accessories > Terminal

post the output here of the following command:

```
sudo fdisk -lu
```

Thanks.

---

### Post by richard.j.hughes on 2011-03-11
Thanks.

Here is the output:

Disk /dev/sda: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b736964

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?  1701998624  3331515282   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(435739, 33, 45)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(852922, 31, 29)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?  1330184192  1869160479   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(340548, 59, 47)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(478535, 44, 42)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?   538989391  1937352302   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(137990, 7, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(495993, 58, 49)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?  3910009470  3910074813       32672   bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1001026, 30, 55)
Partition 4 has different physical/logical endings:
     phys=(128, 0, 7) logical=(1001043, 13, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by Rubi1200 on 2011-03-11
Sorry to have to ask this, but we need something else too.

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by dabl on 2011-03-11
> **richard.j.hughes said:**
> Thanks.

Here is the output:

Disk /dev/sda: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b736964

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?  1701998624  3331515282   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(435739, 33, 45)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(852922, 31, 29)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?  1330184192  1869160479   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(340548, 59, 47)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(478535, 44, 42)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?   538989391  1937352302   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(137990, 7, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(495993, 58, 49)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?  3910009470  3910074813       32672   bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1001026, 30, 55)
Partition 4 has different physical/logical endings:
     phys=(128, 0, 7) logical=(1001043, 13, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

You're going to have to make a new partition table, then partition that drive as you need it, and THEN you can install Ubuntu.  First, back up anything and everything on that hdd that you'll ever want, because the following process will wipe out all data.

I recommend the Parted Magic Live CD, from here:  [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

However a GParted Live CD, or Gparted on your Ubuntu Live CD will also be sufficient.  On the GParted menu, after setting it to /dev/sda, you need to choose "Device > Make New Partition Table" and choose "MS-DOS" for the table type.

Then you'll have the entire drive as "unallocated" space.  You can make your partitions for the OS, swap, and otherwise as you wish.  Then you can boot your Ubuntu installation CD (Live or "Alternate") and proceed to install the OS.

---

### Post by richard.j.hughes on 2011-03-11
Thanks again

The idea of wiping my HDD scares me, so I've put in my other IDE HDD as a secondary HDD.

What I would like to do is to install Ubuntu 10.10 on my secondary HDD. The problem I have had before is because my WDC drive isn't recognised, I have not been able to update the boot sector.

Here is the new output of my fdisk -lu command:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056ec1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   374792191   187395072   83  Linux
/dev/sda2       374794238   390721535     7963649    5  Extended
/dev/sda5       374794240   390721535     7963648   82  Linux swap / Solaris
```

Here is the output printed in RESULTS.TXT:

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   374,792,191   374,790,144  83 Linux
/dev/sda2         374,794,238   390,721,535    15,927,298   5 Extended
/dev/sda5         374,794,240   390,721,535    15,927,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0aaa0b67-281d-4a1d-940d-78af62f95a9a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6669e0e5-c899-47f4-a198-8ccda90ecfa6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/0aaa0b67-281d-4a1d-940d-78af62f95a9a ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
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
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0aaa0b67-281d-4a1d-940d-78af62f95a9a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0aaa0b67-281d-4a1d-940d-78af62f95a9a ro single 
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
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
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
UUID=0aaa0b67-281d-4a1d-940d-78af62f95a9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6669e0e5-c899-47f4-a198-8ccda90ecfa6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  98.9GB: boot/grub/core.img
 137.5GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.35-22-generic
  98.9GB: boot/vmlinuz-2.6.35-22-generic
    .4GB: initrd.img
  98.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4a f4 74 dd f5 fe 65 72  30 57 7b 8e 33 0e 4d 6e  |J.t...er0W{.3.Mn|
00000010  36 ea cf 3c d4 f6 a1 59  00 2a 09 02 2e 10 c9 1f  |6..<...Y.*......|
00000020  28 b1 92 24 f4 fe 27 83  00 14 18 00 50 0e 4f e2  |(..$..'.....P.O.|
00000030  27 1f 9d 53 f4 fe 66 6a  00 02 d4 70 4b 0e 79 92  |'..S..fj...pK.y.|
00000040  3f 74 2d 61 d4 fe 05 5a  00 20 bd 55 5c 0f 49 9c  |?t-a...Z. .U\.I.|
00000050  c4 bf cd 49 d3 fe e5 59  80 80 ea d5 66 27 a1 b8  |...I...Y....f'..|
00000060  72 64 d9 4d ee ac 26 52  74 d7 57 dd 8b 4f 2f 1d  |rd.M..&Rt.W..O/.|
00000070  ab b9 3f 3f 4f 8c 88 5a  ef 8d 7d 7e 75 3f d3 ec  |..??O..Z..}~u?..|
00000080  26 f7 78 63 ad 7b 25 52  62 5f ed 8d 6f 40 21 e9  |&.xc.{%Rb_..o@!.|
00000090  4d 02 a5 49 8a 7b 23 52  ad ab 20 a8 79 4b 95 df  |M..I.{#R.. .yK..|
000000a0  fa a2 cd 3a aa 83 67 52  f2 ff f8 7a 66 10 ea 03  |...:..gR...zf...|
000000b0  3e 5a 43 35 b4 f6 c4 51  27 27 1f 35 1b 0f f7 e3  |>ZC5...Q''.5....|
000000c0  27 7f f2 44 f4 fe 6f cd  00 00 00 40 32 0e c9 ef  |'..D..o....@2...|
000000d0  7c c9 97 54 f4 fe ca 9b  00 42 40 f0 36 0e 7d ee  ||..T.....B@.6.}.|
000000e0  27 4e d5 5c f4 fe 03 6a  00 00 70 42 2f 0f 57 7e  |'N.\...j..pB/.W~|
000000f0  25 b9 ef 3a d4 fe 48 8b  04 04 20 2a 50 10 bf eb  |%..:..H... *P...|
00000100  58 e6 10 b1 d4 fe 66 6a  40 60 56 94 3f 10 7a a8  |X.....fj@`V.?.z.|
00000110  27 0a 6f 6f b3 f6 c3 59  c3 01 b1 5a 39 0f ce ff  |'.oo...Y...Z9...|
00000120  3e 56 22 35 d4 f6 c2 59  02 08 06 25 3f 0e 4e e2  |>V"5...Y...%?.N.|
00000130  e7 77 93 62 f4 fe 44 6a  00 80 20 5c 36 0f 39 ab  |.w.b..Dj.. \6.9.|
00000140  27 e8 13 29 f4 fe 03 62  f0 09 0d 14 2b 0f 42 ac  |'..)...b....+.B.|
00000150  ed 09 95 c4 f4 fe 27 8b  05 3d 70 80 37 10 75 de  |......'..=p.7.u.|
00000160  fb 5a 02 e5 b4 f6 24 6a  08 a0 0f 0d 2e 11 49 f4  |.Z....$j......I.|
00000170  f3 9f b3 3e f4 fe 0e bd  40 02 0c 2f 2d 0f 4b 92  |...>....@../-.K.|
00000180  27 79 9a 5f f4 fe 6b ac  03 00 c0 60 35 0e f7 ef  |'y._..k....`5...|
00000190  26 ba c3 fc f4 fe 0b a4  00 02 21 02 22 10 b9 95  |&.........!."...|
000001a0  7c f9 e3 3a f4 fe d0 d5  00 40 80 36 29 0f 4f a2  ||..:.....@.6).O.|
000001b0  27 55 1e 33 f4 fe d1 d5  00 01 07 00 27 0f 00 fe  |'U.3........'...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 f3 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by richard.j.hughes on 2011-03-12
Hello guys,

What do the above results suggest?

Thanks,

Richard Hughes

---

### Post by Rubi1200 on 2011-03-12
I assume these are the results from the IDE HDD?

According to this, Ubuntu is installed and you should be able to boot it.

I actually wanted to see the results for the other HDD, the one you are having problems with, to try and figure out what is going on.

When that drive is plugged in, how does BIOS report it? Does it recognize the whole drive?

Also, does the drive have encryption on it?

---

### Post by richard.j.hughes on 2011-03-12
They are the results I got when both HDDs are plugged in. Ubuntu doesn't seem to even know the WDC drive exists. I am running Windows on it now, so the drive itself seems fine.

Ubuntu is installed on the other drive because I tried WUBI, but when I boot into it, the installer in boot mode says it cannot find /dev/sda - confirming, I think, that Ubuntu cannot see my WDC drive.

Thanks

---

### Post by Rubi1200 on 2011-03-12
Is BIOS currently set to boot from sda with Ubuntu or do you change it each time?

What happens if you set it to boot from the WDC drive?

There is a test version of the boot script you ran last time (it includes various changes). Try running it and see if the drive is recognized.

First download:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=0c8e808eba272af5ef8b5f4df4654f350526d17b'
```Then, in a terminal:

```
 sudo apt-get install gawk
```
This is needed to parse certain information.

Then, instructions as previously posted.

Thanks.

---

### Post by richard.j.hughes on 2011-03-12
I always boot using the WDC drive.

Here is the RESULTS.TXT:

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   374,792,191   374,790,144  83 Linux
/dev/sda2         374,794,238   390,721,535    15,927,298   5 Extended
/dev/sda5         374,794,240   390,721,535    15,927,296  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0aaa0b67-281d-4a1d-940d-78af62f95a9a   ext4       
/dev/sda5        6669e0e5-c899-47f4-a198-8ccda90ecfa6   swap       
/dev/sdb         5E21-4875                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/0aaa0b67-281d-4a1d-940d-78af62f95a9a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
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
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0aaa0b67-281d-4a1d-940d-78af62f95a9a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0aaa0b67-281d-4a1d-940d-78af62f95a9a ro single 
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
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0aaa0b67-281d-4a1d-940d-78af62f95a9a
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0aaa0b67-281d-4a1d-940d-78af62f95a9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6669e0e5-c899-47f4-a198-8ccda90ecfa6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  92.134815216 = 98.929004544   boot/grub/core.img                             1
 128.138023376 = 137.587154944  boot/grub/grub.cfg                             1
   0.442161560 = 0.474767360    boot/initrd.img-2.6.35-22-generic              2
  92.133285522 = 98.927362048   boot/vmlinuz-2.6.35-22-generic                 1
   0.442161560 = 0.474767360    initrd.img                                     2
  92.133285522 = 98.927362048   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  4a f4 74 dd f5 fe 65 72  30 57 7b 8e 33 0e 4d 6e  |J.t...er0W{.3.Mn|
00000010  36 ea cf 3c d4 f6 a1 59  00 2a 09 02 2e 10 c9 1f  |6..<...Y.*......|
00000020  28 b1 92 24 f4 fe 27 83  00 14 18 00 50 0e 4f e2  |(..$..'.....P.O.|
00000030  27 1f 9d 53 f4 fe 66 6a  00 02 d4 70 4b 0e 79 92  |'..S..fj...pK.y.|
00000040  3f 74 2d 61 d4 fe 05 5a  00 20 bd 55 5c 0f 49 9c  |?t-a...Z. .U\.I.|
00000050  c4 bf cd 49 d3 fe e5 59  80 80 ea d5 66 27 a1 b8  |...I...Y....f'..|
00000060  72 64 d9 4d ee ac 26 52  74 d7 57 dd 8b 4f 2f 1d  |rd.M..&Rt.W..O/.|
00000070  ab b9 3f 3f 4f 8c 88 5a  ef 8d 7d 7e 75 3f d3 ec  |..??O..Z..}~u?..|
00000080  26 f7 78 63 ad 7b 25 52  62 5f ed 8d 6f 40 21 e9  |&.xc.{%Rb_..o@!.|
00000090  4d 02 a5 49 8a 7b 23 52  ad ab 20 a8 79 4b 95 df  |M..I.{#R.. .yK..|
000000a0  fa a2 cd 3a aa 83 67 52  f2 ff f8 7a 66 10 ea 03  |...:..gR...zf...|
000000b0  3e 5a 43 35 b4 f6 c4 51  27 27 1f 35 1b 0f f7 e3  |>ZC5...Q''.5....|
000000c0  27 7f f2 44 f4 fe 6f cd  00 00 00 40 32 0e c9 ef  |'..D..o....@2...|
000000d0  7c c9 97 54 f4 fe ca 9b  00 42 40 f0 36 0e 7d ee  ||..T.....B@.6.}.|
000000e0  27 4e d5 5c f4 fe 03 6a  00 00 70 42 2f 0f 57 7e  |'N.\...j..pB/.W~|
000000f0  25 b9 ef 3a d4 fe 48 8b  04 04 20 2a 50 10 bf eb  |%..:..H... *P...|
00000100  58 e6 10 b1 d4 fe 66 6a  40 60 56 94 3f 10 7a a8  |X.....fj@`V.?.z.|
00000110  27 0a 6f 6f b3 f6 c3 59  c3 01 b1 5a 39 0f ce ff  |'.oo...Y...Z9...|
00000120  3e 56 22 35 d4 f6 c2 59  02 08 06 25 3f 0e 4e e2  |>V"5...Y...%?.N.|
00000130  e7 77 93 62 f4 fe 44 6a  00 80 20 5c 36 0f 39 ab  |.w.b..Dj.. \6.9.|
00000140  27 e8 13 29 f4 fe 03 62  f0 09 0d 14 2b 0f 42 ac  |'..)...b....+.B.|
00000150  ed 09 95 c4 f4 fe 27 8b  05 3d 70 80 37 10 75 de  |......'..=p.7.u.|
00000160  fb 5a 02 e5 b4 f6 24 6a  08 a0 0f 0d 2e 11 49 f4  |.Z....$j......I.|
00000170  f3 9f b3 3e f4 fe 0e bd  40 02 0c 2f 2d 0f 4b 92  |...>....@../-.K.|
00000180  27 79 9a 5f f4 fe 6b ac  03 00 c0 60 35 0e f7 ef  |'y._..k....`5...|
00000190  26 ba c3 fc f4 fe 0b a4  00 02 21 02 22 10 b9 95  |&.........!."...|
000001a0  7c f9 e3 3a f4 fe d0 d5  00 40 80 36 29 0f 4f a2  ||..:.....@.6).O.|
000001b0  27 55 1e 33 f4 fe d1 d5  00 01 07 00 27 0f 00 fe  |'U.3........'...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 f3 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.<.MSWIN4.1..@ .|
00000010  02 00 02 00 00 f8 00 01  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 40 3c 00 80 00 29 75  48 21 5e 4e 4f 20 4e 41  |.@<...)uH!^NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200


```

Thanks

---

### Post by Rubi1200 on 2011-03-12
i have asked someone else to take a look and offer some ideas.

Please be patient.

Thanks.

---

### Post by oldfred on 2011-03-12
Is this an IDE or SATA drive. I assume IDE.

Disk /dev/sda: 2021 MB, 2021654528 bytes
[COLOR=Red]63 heads,[/COLOR] [COLOR=Red]62 sectors/trac[/COLOR]k, 1010 cylinders, total 3948544 sectors

This says it is only a 2GB drive??

Your other drive looks more normal:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
[COLOR=Red]255 heads, 63 sectors/track[/COLOR], 24321 cylinders, total 390721968 sectors

How is BIOS seeing this drive. It should be set to LBA or you have not manual set heads, sectors correctly if it is that old.

---

### Post by richard.j.hughes on 2011-03-12
The 2GB drive is a USB stick, sorry. I should have taken that out.

The BIOS sees the drive as normal.

The primary drive, the one with Windows on and the one that boots and that Ubuntu does not see, is a SATA drive.

The drive that Ubuntu sees, the secondary drive (which, interestingly, Windows only sees in device manager...) is IDE.

Thanks for your help so far guys! I really do appreciate it.

---

### Post by oldfred on 2011-03-12
Mixed SATA & PATA/IDE are often a problem and it is usually the BIOS. Some BIOS promote the IDE to sda automatically, some do not see it as fast in loading and do not make it sda.

Often some setting in BIOS is the issue.

These are notes from others with various BIOS issues, check to see if any apply:

Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick.

---

### Post by XsheepX on 2011-03-12
> **richard.j.hughes said:**
> Hello All
 
I am trying to install a fresh install of Ubuntu 10.10, but I am finding it is not recognising my only HDD in the machine. It is working because I am running Windows 7 x64 on it.
 
I have looked around the forums, but I am not sure what really to try.
 
Here are my machine specs:
 
CPU: AMD Athlon 64 X2 5600+
Motherboard: XFX MI-A78U-8309 GeForce 8300
Graphics Card: NVIDIA GeForce 8300 + 8400
HDD: WDC WD5001AALS-00L3B2 ATA (~415GB)
 
The installation knows when my IDE drive is plugged in, but I want to install the boot sector in the WDC drive.
 
WUBI also fails to install on this current drive, though can setup the boot sector OK.
 
Thank you very much for all of your time and help,
 
Richard Hughes
Can you tell us what it *is* recognizing?

---

### Post by richard.j.hughes on 2011-03-13
> **XsheepX said:**
> Can you tell us what it *is* recognizing?

Hello

Ubuntu *is* recognising my ST3200822A ATA HDD which is connected via IDE.

Ubuntu is *not* recognising my WDC WD5001AALS-00L3B2 ATA which is connected via SATA

(It is also recognising my USB stick...)

---

### Post by richard.j.hughes on 2011-03-13
> **oldfred said:**
> Mixed SATA & PATA/IDE are often a problem and it is usually the BIOS. Some BIOS promote the IDE to sda automatically, some do not see it as fast in loading and do not make it sda.

Often some setting in BIOS is the issue.

These are notes from others with various BIOS issues, check to see if any apply:

Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick.

I just checked the IDE access for both HDDs and they are both set to large. My BIOS gives me the option of Audo or Disabled for large, and they are both set to Auto.

Thanks,

Richard Hughes

---

