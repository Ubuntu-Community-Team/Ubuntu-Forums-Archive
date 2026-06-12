---
title: "grub do not show win7 after update"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by duskseeker on 2011-05-22
hi, may someone culd help me?
i&#472;e updated my ubuntu on 10.10.
now my win7 dosn show up in grub. grub-update dosn work.
i be verry thankfull for your help.

duskseeker

---

### Post by Hedgehog1 on 2011-05-22
First - May I request that you change the Title of you post - this is a site with young ones, so we try to keep it clean.  Thanks!

Next:

We need to get a look at your install to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by duskseeker on 2011-05-22
Hi,
thanks for the fast answer. I have changed the topic.

The output of the script is:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 250.1 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,265,024    27,455,084       190,061   7 NTFS / exFAT / HPFS
/dev/sda3          35,860,478   488,396,799   452,536,322   f W95 Extended (LBA)
/dev/sda5          35,860,480   171,246,023   135,385,544   7 NTFS / exFAT / HPFS
/dev/sda6         171,247,616   482,254,847   311,007,232  83 Linux
/dev/sda7         482,256,896   488,396,799     6,139,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FE7EE7CC7EE77BB1                       ntfs       PQSERVICE
/dev/sda2        01CC031CB9B8B7C0                       ntfs       SYSTEM RESERVED
/dev/sda5        A86AEA0B6AE9D5DA                       ntfs       Acer
/dev/sda6        164c2519-b4bd-4e62-9eb5-16518fa417b7   ext4       
/dev/sda7        10aee886-39e9-49d5-a47f-f1c7e72c9fad   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro single  splash
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
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=10aee886-39e9-49d5-a47f-f1c7e72c9fad none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 103.790611267 = 111.444320256  boot/grub/core.img                             1
 121.974273682 = 130.968879104  boot/grub/grub.cfg                             1
  88.273864746 = 94.783340544   boot/initrd.img-2.6.35-22-generic              1
  88.320747375 = 94.833680384   boot/initrd.img-2.6.35-28-generic              1
 104.239822388 = 111.926657024  boot/vmlinuz-2.6.35-22-generic                 1
 104.161228180 = 111.842267136  boot/vmlinuz-2.6.35-28-generic                 1
  88.320747375 = 94.833680384   initrd.img                                     1
  88.273864746 = 94.783340544   initrd.img.old                                 1
 104.161228180 = 111.842267136  vmlinuz                                        1
 104.239822388 = 111.926657024  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  00 00 d9 05 70 07 14 10  d9 9c 24 bc 11 00 00 d9  |....p.....$.....|
00000010  05 6c 07 14 10 d9 9c 24  c0 11 00 00 d9 05 68 07  |.l.....$......h.|
00000020  14 10 d9 9c 24 c4 11 00  00 d9 05 64 07 14 10 d9  |....$......d....|
00000030  9c 24 c8 11 00 00 d9 05  60 07 14 10 d9 9c 24 cc  |.$......`.....$.|
00000040  11 00 00 d9 05 5c 07 14  10 d9 9c 24 d0 11 00 00  |.....\.....$....|
00000050  d9 05 58 07 14 10 d9 9c  24 d4 11 00 00 d9 05 54  |..X.....$......T|
00000060  07 14 10 d9 9c 24 d8 11  00 00 d9 05 50 07 14 10  |.....$......P...|
00000070  d9 9c 24 dc 11 00 00 d9  05 4c 07 14 10 d9 9c 24  |..$......L.....$|
00000080  e0 11 00 00 d9 05 48 07  14 10 d9 9c 24 e4 11 00  |......H.....$...|
00000090  00 d9 05 44 07 14 10 d9  9c 24 e8 11 00 00 d9 05  |...D.....$......|
000000a0  40 07 14 10 d9 9c 24 ec  11 00 00 d9 05 3c 07 14  |@.....$......<..|
000000b0  10 d9 9c 24 f0 11 00 00  d9 05 38 07 14 10 d9 9c  |...$......8.....|
000000c0  24 f4 11 00 00 d9 05 34  07 14 10 d9 9c 24 f8 11  |$......4.....$..|
000000d0  00 00 d9 05 30 07 14 10  d9 9c 24 fc 11 00 00 d9  |....0.....$.....|
000000e0  05 2c 07 14 10 d9 9c 24  00 12 00 00 d9 05 28 07  |.,.....$......(.|
000000f0  14 10 d9 9c 24 04 12 00  00 d9 05 24 07 14 10 d9  |....$......$....|
00000100  9c 24 08 12 00 00 d9 05  20 07 14 10 d9 9c 24 0c  |.$...... .....$.|
00000110  12 00 00 d9 05 1c 07 14  10 d9 9c 24 10 12 00 00  |...........$....|
00000120  d9 05 18 07 14 10 d9 9c  24 14 12 00 00 d9 05 14  |........$.......|
00000130  07 14 10 d9 9c 24 18 12  00 00 d9 05 10 07 14 10  |.....$..........|
00000140  d9 9c 24 1c 12 00 00 d9  05 0c 07 14 10 d9 9c 24  |..$............$|
00000150  20 12 00 00 d9 05 08 07  14 10 d9 9c 24 24 12 00  | ...........$$..|
00000160  00 d9 05 04 07 14 10 d9  9c 24 28 12 00 00 d9 05  |.........$(.....|
00000170  00 07 14 10 d9 9c 24 2c  12 00 00 d9 05 fc 06 14  |......$,........|
00000180  10 d9 9c 24 30 12 00 00  d9 05 f8 06 14 10 d9 9c  |...$0...........|
00000190  24 34 12 00 00 d9 05 f4  06 14 10 d9 9c 24 38 12  |$4...........$8.|
000001a0  00 00 d9 05 f0 06 14 10  d9 9c 24 3c 12 00 00 d9  |..........$<....|
000001b0  05 ec 06 14 10 d9 9c 24  40 12 00 00 d9 05 00 fe  |.......$@.......|
000001c0  ff ff 07 fe ff ff 02 00  00 00 c8 d1 11 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff ca d1  11 08 38 9e 89 12 00 00  |..........8.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

The code of the grub.cfg is:

```

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
search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=164c2519-b4bd-4e62-9eb5-16518fa417b7 ro single  splash
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
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 164c2519-b4bd-4e62-9eb5-16518fa417b7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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


```

Thanks,
duskseeker

---

### Post by Hedgehog1 on 2011-05-22
Well, I have mixed news.

First, lets get Ubuntu to boot.

From you Ubuntu 10.10 LiveCD/LvieUSB, select 'TRY' and then:

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

You can reboot and you will be able to boot into Ubuntu.

The news for Windows 7 is not as easy.  Windows 7 is not in a logical partitions (/dev/sda5) instead of a primary partition (dev/sda1-4).  Windows doe not like to boot from a non primary partition.

This means moving the partition (or doing a clean and organized reinstall of Windows 7).

How comfortable are you with either of these options?

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-22
- deleted - duplicate post -

---

### Post by duskseeker on 2011-05-22
Okay,
Ubuntu is running, but why did the win7 showed up in the grub before updating?
Cant i write the win boot instructions manually in the grub.cfg?
sorry, but my english seems to be a bit out of praktice.
duskseeker

---

### Post by Hedgehog1 on 2011-05-22
> **duskseeker said:**
> Okay,
Ubuntu is running, **but why did the win7 showed up in the grub before updating**?
Cant i write the win boot instructions manually in the grub.cfg?
sorry, but my english seems to be a bit out of praktice.
duskseeker

**Why did it show up before:** That is a great question that I don't know the answer to.

Can you write in the Win7 entry in **/etc/grub.d/40_custom** ? Yes I think you can!  Let Me fire up a 10.10 Vbox and get a sample of the script...

***The Hedge***

:KS

---

### Post by duskseeker on 2011-05-22
Great, i wil be thankfull.............

---

### Post by Hedgehog1 on 2011-05-22
```
gksudo gedit /etc/grub.d/40_custom
``` 

```
menuentry "Windows 7 (loader) (on /dev/sda5)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root A86AEA0B6AE9D5DA
	chainloader +1
}
```

```
sudo update-grub
```

***The Hedge***

:KS

---

### Post by duskseeker on 2011-05-22
Ok,
the win entry is still not found in the boot-menue.
the file in grub.d is changed. funny, if i start the startupmanager i can choose between linux and win.
should i change th grub.cfg?

---

### Post by duskseeker on 2011-05-22
Ok,
got it in the menue now. but if i want to boot win, the error "invaild signature" appears.

---

### Post by Hedgehog1 on 2011-05-22
Yeah, I was afraid this might happen.

There is a way to get Windows to boot from a logical partition, but in the end most folks move the partition to a primary.

If you would, now that we know this issue here, can you make a new thread with the subject "Ubuntu Install moved Windows to Logical Partition" and place an updated bootinfoscript output on the first post.

This will attract the attention of the folks who can help with this.

***The Hedge***

:KS

---

### Post by duskseeker on 2011-05-22
ok, opend a new post. thanks

---

