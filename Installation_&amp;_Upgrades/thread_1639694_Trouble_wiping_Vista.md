---
title: "Trouble wiping Vista"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by esvoytko on 2010-12-07
This may be a pretty rookie question...

I have finally convinced my wife to ditch Windows and she's let me install Ubuntu on her machine. When I installed, I selected the option to erase the existing OS and use the entire hard disk for Ubuntu (I want Vista and all the files on the machine GONE). 

When I booted the computer after the installation was complete, however, it gives me the option of choosing to boot Vista or Ubuntu. When I choose Vista, lo and behold, all the old files and the OS are still there. Upon questioning my wife, I learn that her computer had C:, D:, and E: drives, in addition to the optical drive (which is F: ). Three hard drives? I may be a newb, but this is not something I thought was very common on a stock machine. She vaguely claims that the other two drives are "backup" drives. 

Not sure what that means. So it looks like maybe I installed Ubuntu on one drive completely, with the other two drives staying like they were. I want Vista gone, but not sure what to do. I'm not savvy enough to navigate the manual partitioning menu.

Ideas?

---

### Post by sikander3786 on 2010-12-07
I think you just installed Ubuntu to one of the partitions and not the entire disk (and that proved a goody for you as recovery partition was there and is still there :-) )

I would recommend to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your setup/partitions and therefore, we'll be able to advise more efficiently.

Please wrap your output using proper code tags # from post menu. [/code] at the end [code] at the beginning.

---

### Post by tg3793 on 2010-12-07
I'm making three assumptions:

1) you want to avoid starting over from scratch. 
2) you don't have a love affair going with any of the data on the computer in question.
3) You are running Ubuntu 10.04 (Lucid)

*Note if #2 is not correct then make sure you back up your data on an external medium before following my advice.

So with those assumptions in mind I would say for you to simply boot into Ubuntu and to delete all of the data from your windows partition. 

If you are uncertain about this advice I can start to guide you by having you boot into Ubuntu then click on the top left where it says "Places", click on that to access it's drop down menu. Then click on "Computer"  and respond to this thread with the name of all the devices on the left hand side.
[COLOR="DimGray"]* You can leave out the ones that say; Documents, Music, Pictures, Videos, and Downloads. Everyone has those and that would tell me anything useful.[/COLOR]

Thanks.

---

### Post by tg3793 on 2010-12-07
Ooops didn't see sikander's post before I sent mine in. If you feel comfortable following those instruction then those are actually very good and will get you better results if you are concerned about the data on your drive.

My solution might take you to botched up land where you might need to (but not necessarily) have to reinstall Ubuntu. But this time around you'll be reinstalling with all of your VISTA data completely gone.

---

### Post by esvoytko on 2010-12-07
Thanks for the quick replies!

In response to tg3793: There are two drives listed when I view Places. One says File System, and the other says 77GB File System. Here is a screen capture:

[http://img442.imageshack.us/img442/2635/screenshotij.png](http://img442.imageshack.us/img442/2635/screenshotij.png)

To sikander:

I was already in the middle of a second Ubuntu installation when I made the original post, so that is now done. Even when I selected the option for erasing the entire disk and using the whole thing for Ubuntu it let me pick from two disks. This time I picked the second one. Now it seems Vista is gone, but I have two copies of Ubuntu?


Anyway, here are the results from the boot script:

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

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        25a9a580-2509-43dc-b40d-3b09ddf6a25b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6d72ef58-b54d-4a7b-9073-dceb4b26b9d1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        af7f481e-9ec8-4573-a89d-3fa2e220a918   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        97a2dfad-99ae-4370-9d71-44f68dfd6b1c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/af7f481e-9ec8-4573-a89d-3fa2e220a918 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 25a9a580-2509-43dc-b40d-3b09ddf6a25b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 25a9a580-2509-43dc-b40d-3b09ddf6a25b
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
    search --no-floppy --fs-uuid --set 25a9a580-2509-43dc-b40d-3b09ddf6a25b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25a9a580-2509-43dc-b40d-3b09ddf6a25b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 25a9a580-2509-43dc-b40d-3b09ddf6a25b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25a9a580-2509-43dc-b40d-3b09ddf6a25b ro single 
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
    search --no-floppy --fs-uuid --set 25a9a580-2509-43dc-b40d-3b09ddf6a25b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 25a9a580-2509-43dc-b40d-3b09ddf6a25b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=af7f481e-9ec8-4573-a89d-3fa2e220a918 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=af7f481e-9ec8-4573-a89d-3fa2e220a918 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6d72ef58-b54d-4a7b-9073-dceb4b26b9d1 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  40.9GB: boot/grub/core.img
  81.9GB: boot/grub/grub.cfg
 107.9GB: boot/initrd.img-2.6.35-22-generic
  40.9GB: boot/vmlinuz-2.6.35-22-generic
 107.9GB: initrd.img
  40.9GB: vmlinuz

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
search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
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
    search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=af7f481e-9ec8-4573-a89d-3fa2e220a918 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=af7f481e-9ec8-4573-a89d-3fa2e220a918 ro single 
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
    search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af7f481e-9ec8-4573-a89d-3fa2e220a918
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 243c6bef3c6bba86
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=97a2dfad-99ae-4370-9d71-44f68dfd6b1c none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  26.0GB: boot/grub/core.img
  55.9GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  26.0GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  26.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a1 8e 40 84 d9 77 d8 0c  3a 78 84 6d 74 70 49 0c  |..@..w..:x.mtpI.|
00000010  1f 52 a6 7d 4c 72 2d 93  1c b9 7e b2 12 c6 98 09  |.R.}Lr-...~.....|
00000020  73 ac c2 e1 07 da 17 84  93 65 88 47 96 98 44 41  |s........e.G..DA|
00000030  de a4 e2 b6 83 15 64 9a  cc 3c e5 b1 49 99 1f f1  |......d..<..I...|
00000040  8c aa 14 f7 44 e0 19 9f  65 dd 11 16 4f 8b 0d 23  |....D...e...O..#|
00000050  15 dc 1a 79 07 e2 4e 54  6d 0c 16 30 1a 3d b6 2d  |...y..NTm..0.=.-|
00000060  54 83 83 60 63 af 68 01  0e 48 d3 87 27 fb 44 77  |T..`c.h..H..'.Dw|
00000070  1c 89 86 06 28 98 85 23  1d 52 fe 8c 23 35 41 d4  |....(..#.R..#5A.|
00000080  92 76 bc ed e0 fd 3c d4  b9 1e 3f 61 46 88 26 bb  |.v....<...?aF.&.|
00000090  08 81 11 d3 c6 62 4e 72  eb 45 cd a0 92 af 05 46  |.....bNr.E.....F|
000000a0  36 16 ff 6f af 24 da ab  70 45 d2 09 dd c9 43 f7  |6..o.$..pE....C.|
000000b0  04 20 08 97 40 cf c0 7a  06 0f cc 5a fb 76 95 bb  |. ..@..z...Z.v..|
000000c0  ba 69 64 9e aa a2 27 05  6c c3 f5 67 77 cc 92 0d  |.id...'.l..gw...|
000000d0  69 53 27 d7 07 ae bb 8c  ce 39 c2 f4 dd 3e 5a db  |iS'......9...>Z.|
000000e0  21 32 8c 9d f1 83 ac e8  74 d8 10 27 2e c7 d8 98  |!2......t..'....|
000000f0  09 f4 9e 68 e4 cc eb ad  cf de 65 03 5f ad 40 58  |...h......e._.@X|
00000100  d9 67 d4 2c a9 d7 0d 1e  84 e7 0f f2 75 25 cc cf  |.g.,........u%..|
00000110  17 aa 25 68 02 c9 c5 2b  f8 fc 35 94 74 f9 b4 c8  |..%h...+..5.t...|
00000120  76 fb a1 37 08 cc 0b 0e  8b 4f 35 c4 d3 9b 64 e2  |v..7.....O5...d.|
00000130  80 00 e7 49 b7 49 a4 3e  ed 05 0f 2a 2a 19 51 79  |...I.I.>...**.Qy|
00000140  93 28 28 87 48 d3 00 56  e3 8f 4b 9a 20 bc 4a ec  |.((.H..V..K. .J.|
00000150  75 13 3b ef c5 dc 8f 2c  c7 9e 51 ac 52 2d d5 20  |u.;....,..Q.R-. |
00000160  3e 99 85 d2 b0 87 a2 54  35 b1 87 e3 f5 40 16 ff  |>......T5....@..|
00000170  db b0 e6 26 87 d9 f2 25  30 1c 44 bc 18 e4 3a 69  |...&...%0.D...:i|
00000180  b3 2f c8 8d 9a 32 b3 c1  0c b2 39 93 11 f2 2d 0a  |./...2....9...-.|
00000190  11 e5 82 3d c9 c6 57 86  be 78 ab 5b d2 fb 54 1c  |...=..W..x.[..T.|
000001a0  ba 60 e5 3d c6 e1 01 43  a4 db 3e 94 7a 94 0d 74  |.`.=...C..>.z..t|
000001b0  aa 30 34 89 84 cd 70 27  67 78 75 6e 21 36 00 fe  |.04...p'gxun!6..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  85 eb de 32 5c dc 82 9b  e1 11 d8 3a 79 9b 2d f4  |...2\......:y.-.|
00000010  e9 0e 3c a4 94 99 89 fd  17 88 ef 0f 7d 08 ac af  |..<.........}...|
00000020  c1 8c 02 c4 0d c5 09 1a  e1 98 a0 7c d8 9e 56 95  |...........|..V.|
00000030  79 34 31 ae 5a d2 4a 44  7f 51 28 a5 f2 41 86 e1  |y41.Z.JD.Q(..A..|
00000040  90 d5 74 e9 e0 4d 02 80  09 d4 2e 8c f4 24 65 5c  |..t..M.......$e\|
00000050  30 e7 78 d9 09 15 e9 7f  e4 a3 d3 2c 15 b8 a9 c8  |0.x........,....|
00000060  2b 42 8a e5 cb 5e 61 cf  67 73 91 05 a7 7a 70 7f  |+B...^a.gs...zp.|
00000070  3b 70 f9 80 5f 2b a2 67  32 6c 89 c0 23 0b 5f 96  |;p.._+.g2l..#._.|
00000080  c0 2b b2 2f 09 9f 96 df  52 88 d3 1b 51 8f 8b d3  |.+./....R...Q...|
00000090  be 95 e8 99 18 3f ee 73  43 0e 26 37 3c 27 36 5e  |.....?.sC.&7<'6^|
000000a0  fc 42 a5 dd fb ae be eb  42 f4 12 03 54 a4 dc c5  |.B......B...T...|
000000b0  df 33 45 b2 a6 cb cb a0  f9 ea 90 8d 4a ce 34 65  |.3E.........J.4e|
000000c0  0e 4c 5d e2 2e e1 8f 67  fb 9b df 46 7b 76 34 ef  |.L]....g...F{v4.|
000000d0  04 18 be 49 91 f6 ed 75  55 0d 7a 0a 49 78 80 f6  |...I...uU.z.Ix..|
000000e0  91 69 7c b1 4c e6 c6 b0  0e 04 ac d4 cd 5f bc c7  |.i|.L........_..|
000000f0  d7 33 be 4a 67 ad 34 c4  09 26 fc 7c 4d f8 c0 01  |.3.Jg.4..&.|M...|
00000100  6e 70 bf 1f 30 5b ab 19  eb 16 83 ba 7b 5b c5 65  |np..0[......{[.e|
00000110  16 5d 8d c5 aa 69 0a ae  38 c3 97 c7 71 31 9b ac  |.]...i..8...q1..|
00000120  8c 1c df d8 69 2b 65 64  f8 47 ef b9 55 45 05 9b  |....i+ed.G..UE..|
00000130  1b 55 dd 27 ef e5 bb 10  c8 12 eb 78 32 3e 08 9d  |.U.'.......x2>..|
00000140  ad bb 9e be 4c 0f fd 8f  0b 5c 44 84 36 60 ae 86  |....L....\D.6`..|
00000150  4b fd 4b 88 15 73 43 83  54 d1 b5 da b9 4c 52 7f  |K.K..sC.T....LR.|
00000160  ca 29 c2 18 f8 e2 b1 bf  cc 8d ec 65 b9 bb 6e 03  |.).........e..n.|
00000170  3c 47 d2 dc ea 0f dd 28  44 43 e1 7f 1b 12 24 07  |<G.....(DC....$.|
00000180  91 3a 0e fd 3c 60 d9 8e  64 04 31 e3 a3 2f 50 61  |.:..<`..d.1../Pa|
00000190  37 c6 40 3a e5 1a ad 0b  77 3a a7 c7 a3 1b 3b a6  |7.@:....w:....;.|
000001a0  18 2f 90 fd d2 f2 e2 62  25 7a 65 95 5c c0 19 b4  |./.....b%ze.\...|
000001b0  fd 1c 37 2e 58 8b 65 32  dd 94 a4 ce 32 6f 00 fe  |..7.X.e2....2o..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

---

### Post by esvoytko on 2010-12-07
Forgot to mention, I am installing version 10.10 Meerkat.

Though I use 10.04 on my own machine.

---

### Post by smokeys on 2010-12-07
> **esvoytko said:**
> This may be a pretty rookie question...

I have finally convinced my wife to ditch Windows and she's let me install Ubuntu on her machine. When I installed, I selected the option to erase the existing OS and use the entire hard disk for Ubuntu (I want Vista and all the files on the machine GONE). 

When I booted the computer after the installation was complete, however, it gives me the option of choosing to boot Vista or Ubuntu. When I choose Vista, lo and behold, all the old files and the OS are still there. Upon questioning my wife, I learn that her computer had C:, D:, and E: drives, in addition to the optical drive (which is F: ). Three hard drives? I may be a newb, but this is not something I thought was very common on a stock machine. She vaguely claims that the other two drives are "backup" drives. 

Not sure what that means. So it looks like maybe I installed Ubuntu on one drive completely, with the other two drives staying like they were. I want Vista gone, but not sure what to do. I'm not savvy enough to navigate the manual partitioning menu.

Ideas?
can you help me out i cant find any where on here to post a thread can you help me out and point me in the right deriction please i would really aprichate that

---

### Post by esvoytko on 2010-12-07
Also, here is a camera shot of the screen I get when I boot. This may help as well.

[http://img137.imageshack.us/img137/350/img1127k.jpg](http://img137.imageshack.us/img137/350/img1127k.jpg)

---

### Post by smokeys on 2010-12-07
> **sikander3786 said:**
> I think you just installed Ubuntu to one of the partitions and not the entire disk (and that proved a goody for you as recovery partition was there and is still there :-) )

I would recommend to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your setup/partitions and therefore, we'll be able to advise more efficiently.

Please wrap your output using proper code tags # from post menu. [/code] at the end [code] at the beginning.
sorry but i got a quick quistion can you help me find out where to post a tgread im new to this site & i would really aprishate it if you could help  me out

---

### Post by smokeys on 2010-12-07
can any one help me out and tell me where to go to post a thread here thank you

---

### Post by Off Topic on 2010-12-07
Nuke it from space with GParted and start from scratch.

---

### Post by esvoytko on 2010-12-07
Also, here is a screenscot from the disk utility window, clearly showing two drives - one 80gb and one 120gb.

[http://img109.imageshack.us/img109/9942/screenshot1ru.png](http://img109.imageshack.us/img109/9942/screenshot1ru.png)


I might not be savvy enough to do anything with GParted. Anyway, I'm not sure it is a question of partitions, I think there are multiple drives.

---

### Post by matt_symes on 2010-12-07
Hi 

> **smokeys said:**
> can any one help me out and tell me where to go to post a thread here thank you

@smokeys

Select the sub forum you want to post in and select 'new thread'. It's near the top in the left hand side. Don't hijack  other peoples threads.

I.E

Select a forum from here (or one of the other ones)

[http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

when you have selected a forum select 'new thread'

Kind regards

---

### Post by sikander3786 on 2010-12-07
> 
To sikander:

I was already in the middle of a second Ubuntu installation when I made the original post, so that is now done. Even when I selected the option for erasing the entire disk and using the whole thing for Ubuntu it let me pick from two disks. This time I picked the second one. Now it seems Vista is gone, but I have two copies of Ubuntu?

So, I hope you've installed Ubuntu to your first HDD this time i.e, sda on the list. Make sure you are booting from fist HDD (Bios setting), boot Ubuntu, fire up gparted (needs to be installed from Software Center) or Disk Utility under System > Administration (already present there), unmount any partitions from sdb, delete them, create new partitions (whatever no. of partitions you need there) and then run this command to get rid of second Ubuntu entry in Grub menu.

```
sudo update-grub
```

You can definitely post back if you've got any queries :P

---

### Post by tg3793 on 2010-12-07
- Yup you have two drives
- I agree with [sikander]("http://ubuntuforums.org/member.php?u=806649") to make sure you install it to sda
- I'll add that you can use the built in "Disk Utility" that you have already accessed in order to delete partitions (though gparted is accepted as one of the best).

[sikander]("http://ubuntuforums.org/member.php?u=806649") has you well taken care of  ... tg3793 signing off :-)

---

### Post by esvoytko on 2010-12-07
Ok, Ubuntu is installed to sda (the 120gb drive).

I used GParted to entirely wipe sdb. It is now completely unallocated.

Two questions remain:

First, is this what my partitions should look like for sda?
[http://img64.imageshack.us/img64/6136/sdapartitions.png](http://img64.imageshack.us/img64/6136/sdapartitions.png)

And more importantly, why do I still have to sit through this screen when I boot?
[http://img574.imageshack.us/img574/3701/img1128r.jpg](http://img574.imageshack.us/img574/3701/img1128r.jpg)

---

### Post by sikander3786 on 2010-12-07
Yes sda looks absolutely fine.

And regardind the Grub menu issue, post the output of this command.

```
cat /etc/default/grub
```

---

### Post by wilee-nilee on 2010-12-07
> **esvoytko said:**
> Ok, Ubuntu is installed to sda (the 120gb drive).

I used GParted to entirely wipe sdb. It is now completely unallocated.

Two questions remain:

First, is this what my partitions should look like for sda?
[http://img64.imageshack.us/img64/6136/sdapartitions.png](http://img64.imageshack.us/img64/6136/sdapartitions.png)

And more importantly, why do I still have to sit through this screen when I boot?
[http://img574.imageshack.us/img574/3701/img1128r.jpg](http://img574.imageshack.us/img574/3701/img1128r.jpg)

Image one I would always wrap the extended around everything, but that works.

How long is the wait at the second grub image?

---

### Post by esvoytko on 2010-12-07
The wait is ten seconds, but I'd rather go straight through to my desktop.

Here is the output from that command:

```


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

---

### Post by tg3793 on 2010-12-07
- Yup the partitions look good.
- The grub menu is useful if you have more than one OS installed. However if you don't want to see that you'll have to get someone to guide you through setting Ubuntu as the default OS to boot from with a timeout of zero seconds ... I'm sure someone will respond any moment to help you out with that one :-)

---

### Post by wilee-nilee on 2010-12-07
> **tg3793 said:**
> - Yup the partitions look good.
- The grub menu is useful if you have more than one OS installed. However if you don't want to see that you'll have to get someone to guide you through setting Ubuntu as the default OS to boot from with a timeout of zero seconds ... I'm sure someone will respond any moment to help you out with that one :-)

A time out of 0 seconds will not be good, if your talking about the time down from grub showing to boot. This is a problem many run into, no access to the recovery kernel.

OP with one OS installed run the sudo update-grub in the sda1 install. If you have more then one OS you will see grub. The countdown can be changed to shorter then 10 but 0 is a very bad idea.

---

### Post by tg3793 on 2010-12-07
> **wilee-nilee said:**
> A time out of 0 seconds will not be good, if your talking about the time down from grub showing to boot. This is a problem many run into, no access to the recovery kernel.
.

Listen to the guy with 5,145 Beans :-)

---

### Post by wilee-nilee on 2010-12-07
> **tg3793 said:**
> Listen to the guy with 5,145 Beans :-)

Lol I bought the beans on ebay.;)

---

### Post by sikander3786 on 2010-12-07
Edit your /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

Remove the comment from this line's beginning.

```
#GRUB_HIDDEN_TIMEOUT=0
```

So that it looks like this.

```
GRUB_HIDDEN_TIMEOUT=0
```

Save and close and run this command.

```
sudo update-grub
```

This should hide your Grub menu from being visible at boot and if you want to access the options there, you'll need to press and hold down Shift key from your Bios Screen ;-)

---

### Post by esvoytko on 2010-12-07
Thanks guys this has all been very helpful. :)

---

### Post by esvoytko on 2010-12-07
The GRUB screen is no more, and accessible by pressing shift. Yay!

---

### Post by sikander3786 on 2010-12-07
> **esvoytko said:**
> The GRUB screen is no more, and accessible by pressing shift. Yay!
Glad to know that it is all sorted out :-)

If you've got no more queries at the moment, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Or if there are any queries left, you are definitely free to post them right away :P

Happy Ubuntu-ing!

---

