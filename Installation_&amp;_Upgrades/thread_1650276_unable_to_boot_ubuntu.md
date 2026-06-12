---
title: "unable to boot ubuntu"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by ZStella on 2010-12-21
Hello, 
I'm a new linux user and after I installed Ubuntu 10.10 and my computer restarted, I couldn't find a way for it to boot Ubuntu, but it automatically went to Vista.

When I press 'esc' to enter the boot order, it only give me the option of CD drive or Hard drive.  I tried force installing GRUB2 from a live CD, but to no effect. 

Any ideas of what else I could try? In my search of the forums I couldn't find a similar problem, but I may have missed it. 

I have an HP Pavilion Notebook.

---

### Post by dino99 on 2010-12-21
welcome :)

is your installation looks like:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by oldfred on 2010-12-21
So we can see exactly what is where, from LiveCD run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by karthick87 on 2010-12-21
By oldfred suggestion,post the output of bootinfoscript with code tags.

---

### Post by ZStella on 2010-12-21
dino99:

I have 
- / : root, bootable, ext4, ~ 12 Gb 
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)

But I don't have:

- /home : ext3 or ext4 format, unlimited space to store your data and settings

Could this be my problem?

oldfred:

I have a limited download connection, so I'll have to try that in a few hours.

Thanks!

---

### Post by dino99 on 2010-12-21
its a good idea to have a /home, but it work without anyway. 

While installation, do you remember, at end, where you have installed grub (might have seen a popup with something like /dev/sda or so) ?

you can try, on booting:

hold "shift" key down at end of bios process to force grub menu to show up. If it exist, and so mean grub installed, select to boot on ubuntu instead of vista.

If its not installed, reboot on the livecd, and select to install grub on /dev/sda (you need to change the boot priority first into bios)

---

### Post by ZStella on 2010-12-21
Here is the boot info. 

Thanks again. 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   205,360,933   205,360,871   7 HPFS/NTFS
/dev/sda2         205,361,150   295,282,687    89,921,538   5 Extended
/dev/sda5         205,361,152   291,377,151    86,016,000  83 Linux
/dev/sda6         291,379,200   295,282,687     3,903,488  82 Linux swap / Solaris
/dev/sda3         295,284,736   312,571,903    17,287,168   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FAC04748C04709F9                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        A2F24A6BF24A442F                       ntfs       HP_RECOVERY                   
/dev/sda5        d8be46c3-3f8b-458d-a682-bfecdad27425   ext4                                     
/dev/sda6        e5cadc36-e875-4cec-9e26-651d808c78c0   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set d8be46c3-3f8b-458d-a682-bfecdad27425
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set d8be46c3-3f8b-458d-a682-bfecdad27425
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d8be46c3-3f8b-458d-a682-bfecdad27425
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d8be46c3-3f8b-458d-a682-bfecdad27425 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d8be46c3-3f8b-458d-a682-bfecdad27425
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d8be46c3-3f8b-458d-a682-bfecdad27425 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d8be46c3-3f8b-458d-a682-bfecdad27425
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d8be46c3-3f8b-458d-a682-bfecdad27425
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fac04748c04709f9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set a2f24a6bf24a442f
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d8be46c3-3f8b-458d-a682-bfecdad27425 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e5cadc36-e875-4cec-9e26-651d808c78c0 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 107.4GB: boot/grub/core.img
 146.1GB: boot/grub/grub.cfg
 140.4GB: boot/initrd.img-2.6.35-22-generic
 107.4GB: boot/vmlinuz-2.6.35-22-generic
 140.4GB: initrd.img
 107.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  72 dc 39 0a b9 f9 54 7b  0c 74 a0 0e 39 02 42 c0  |r.9...T{.t..9.B.|
00000010  32 30 dc 4b cc be 59 1c  9e b8 27 8f c0 55 bd 43  |20.K..Y...'..U.C|
00000020  57 b2 7b 2b 7b 58 23 9e  3b 90 0c 77 04 02 43 73  |W.{+{X#.;..w..Cs|
00000030  c3 06 1d 38 ec 7d 3a f6  a0 0e 69 5e 78 99 5a 06  |...8.}:...i^x.Z.|
00000040  0a b1 6e 04 c8 18 92 7f  99 3e e6 aa 4b 14 93 e1  |..n......>..K...|
00000050  c1 45 28 31 14 61 32 44  8c 70 09 3f 43 ef 40 1b  |.E(1.a2D.p.?C.@.|
00000060  cf a3 88 e1 0c d1 a8 91  c9 05 b1 82 a7 15 90 74  |...............t|
00000070  99 dd 26 89 80 c2 9d e8  a4 67 03 d4 9e e7 34 01  |..&......g....4.|
00000080  98 fa 6d ec 7e 65 c0 21  63 2a b0 c9 31 42 43 64  |..m.~e.!c*..1BCd|
00000090  e3 6f f8 52 9b 0b a8 a3  de 04 90 ac 7b 8c 7e 58  |.o.R........{.~X|
000000a0  de ce 3d 31 40 1d 4e 95  f0 f3 c4 1a dd 9b dc d9  |..=1@.N.........|
000000b0  43 34 91 a2 35 c4 8c aa  a0 ec 03 24 e3 da b8 ed  |C4..5......$....|
000000c0  43 4e 92 de 59 6d 64 46  41 6c 0a 00 ac 5b 0e 39  |CN..YmdFAl...[.9|
000000d0  c9 3d b3 40 14 1c 4c e8  66 47 11 99 d1 6d b6 aa  |.=.@..L.fG...m..|
000000e0  a9 6d a3 a9 cf d2 ab 47  21 80 c8 bb f6 a8 4d 9b  |.m.....G!.....M.|
000000f0  5d 49 dc c7 a3 03 d3 f0  a0 05 88 00 aa e1 03 05  |]I..............|
00000100  25 40 6e 09 3d ce 2b 5a  d2 e6 e2 06 8e 48 9d a3  |%@n.=.+Z.....H..|
00000110  57 8f cb 2a 18 8d cd 9f  b8 7d bb d0 07 41 a7 5e  |W..*.....}...A.^|
00000120  9b 28 5d 77 3c 91 99 04  be 5b a9 2c 5f 3d 41 fe  |.(]w<....[.,_=A.|
00000130  ee 49 e3 bf 15 f5 87 c0  bf 19 e8 da 66 a1 1c fa  |.I..........f...|
00000140  bc b0 db dc 46 de 64 0f  27 01 a5 5e 55 49 fe 11  |....F.d.'..^UI..|
00000150  9e fe a7 f1 a0 0f 67 d1  be 20 5a 78 d3 c6 b3 d9  |......g.. Zx....|
00000160  b5 9d dd de 95 1c ea b2  34 50 34 ad 76 73 96 89  |........4P4.vs..|
00000170  47 42 4e 30 32 7a 9f c6  bc 5f e3 27 82 2f b5 5d  |GBN02z..._.'./.]|
00000180  6f 50 d6 e2 d3 6e ac 34  eb 76 2b f6 67 b5 74 16  |oP...n.4.v+.g.t.|
00000190  83 80 b1 92 78 2c 7a e0  7b fb 50 07 8a e9 fe 09  |....x,z.{.P.....|
000001a0  d7 a5 6b af 3a ca 48 ec  c4 41 96 ea 68 1d 56 65  |..k.:.H..A..h.Ve|
000001b0  cf 23 9f bd cf 15 f6 ef  c1 bf 80 7a 46 be 00 fe  |.#.........zF...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 20 05 00 fe  |............ ...|
000001d0  ff ff 05 fe ff ff 02 80  20 05 00 98 3b 00 00 00  |........ ...;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by ZStella on 2010-12-21
The shift key doesn't work, unfortunately.

Could you be a bit more specific on:

> If its not installed, reboot on the livecd, and select to install grub on /dev/sda (you need to change the boot priority first into bios)

Thanks again.

---

### Post by sikander3786 on 2010-12-21
> **ZStella said:**
> The shift key doesn't work, unfortunately.

Could you be a bit more specific on:



Thanks again.
Boot an Ubuntu Maverick/Lucid/Karmic Live CD and from Applicaitons > Accessories > Terminal:

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and you'll be able to boot Ubuntu this time hopefully. If it doesn't list Windows, from installed Ubuntu's Terminal,

```
sudo update-grub
```

Good Luck!

---

### Post by oldfred on 2010-12-21
Does your Vista boot ok? The script shows you are missing part of it.

You need to install the grub2 boot loader to the MBR. But you have a HP boot loader not the standard windows boot loader. Do you have some function keys that work directly from boot. You may lose those.

Just in case I would back up the code in the MBR.
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1

Copy mbr.bin to a place where it will be saved. The liveCD will not save it.

To install grub2 to the MBR:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You have Vista. With Vista grub seems to reverse the titles of the Vista install and the Recovery. So when you get the grub menu and want Vista use the one with Recovery as sda1 looks like your Vista. (sda3 is actually the recovery).

Windows Recovery Environment (loader) (on /dev/sda1)

If you run the recovery it will probably totally erase your drive and return it to as purchased. All changes & updates will be lost and you would have to rerun them.
But if the recovery lets you create a DVD recovery, you should. And if it lets you create a Vista repair CD you definitely should do that.

---

### Post by ZStella on 2010-12-21
sikander3786 Your tip worked like a charm! Thanks so much!

Thanks to everyone else too. You guys are really a great bunch to help us new users out!

---

