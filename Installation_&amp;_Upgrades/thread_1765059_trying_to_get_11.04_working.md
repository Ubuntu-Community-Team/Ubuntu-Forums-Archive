---
title: "trying to get 11.04 working"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by mcfritzl on 2011-05-22
Just upgraded to 11.04 but when my computer restarted I got this:

error: symbol not found: 'grub_env_export'.
grub rescue> 

I have no idea what that means or what I should do...

---

### Post by jesse.au on 2011-05-27
come on peoples
give this guy an answer...
He needs help and i cant give it!!

---

### Post by Rubi1200 on 2011-05-27
@mcfritzl; this is what you need to do to help us troubleshoot this:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

@jesse.au; thank you for bumping this up so we can try and help. That is what this community is all about.

---

### Post by mcfritzl on 2011-05-29
Alright, did all that and here's what I got:

 Boot Info Script 0.60    from 17 May 2011

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 30616 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,683,519    15,683,458   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       3ffc8552-2444-b44e-a36f-59d6eb14883a   ext2       casper-rw
/dev/mmcblk0p1   41d24e7d-77d7-46c8-aedb-d2413bc6989b   ext4       
/dev/mmcblk0p5   5e230ebd-5a16-4397-a0a6-391fbed6b45a   swap       
/dev/sda1        5d3dfc03-ca31-4d9f-826b-ae6a606d46e7   ext4       
/dev/sda5        059b872f-38a6-4856-b530-a5a146392ab6   swap       
/dev/sdb1        241D-3616                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/41d24e7d-77d7-46c8-aedb-d2413bc6989b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d3dfc03-ca31-4d9f-826b-ae6a606d46e7
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
UUID=5d3dfc03-ca31-4d9f-826b-ae6a606d46e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=059b872f-38a6-4856-b530-a5a146392ab6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.187969208 = 4.496797696    boot/grub/core.img                             1
   3.492965698 = 3.750543360    boot/grub/grub.cfg                             1
   1.800216675 = 1.932967936    boot/initrd.img-2.6.35-22-generic              2
   3.911781311 = 4.200243200    boot/initrd.img-2.6.38-8-generic               2
   4.667083740 = 5.011243008    boot/vmlinuz-2.6.35-22-generic                 1
   1.177062988 = 1.263861760    boot/vmlinuz-2.6.38-8-generic                  2
   3.911781311 = 4.200243200    initrd.img                                     2
   1.800216675 = 1.932967936    initrd.img.old                                 2
   1.177062988 = 1.263861760    vmlinuz                                        2
   4.667083740 = 5.011243008    vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  3a 00 20 00 4e 00 65 00  74 00 52 00 74 00 52 00  |:. .N.e.t.R.t.R.|
00000010  65 00 74 00 75 00 72 00  6e 00 43 00 68 00 65 00  |e.t.u.r.n.C.h.e.|
00000020  63 00 6b 00 0d 00 0a 00  5b 00 30 00 34 00 2f 00  |c.k.....[.0.4./.|
00000030  31 00 38 00 2f 00 31 00  30 00 2c 00 31 00 30 00  |1.8./.1.0.,.1.0.|
00000040  3a 00 34 00 39 00 3a 00  35 00 32 00 5d 00 20 00  |:.4.9.:.5.2.]. .|
00000050  4d 00 69 00 63 00 72 00  6f 00 73 00 6f 00 66 00  |M.i.c.r.o.s.o.f.|
00000060  74 00 20 00 2e 00 4e 00  45 00 54 00 20 00 46 00  |t. ...N.E.T. .F.|
00000070  72 00 61 00 6d 00 65 00  77 00 6f 00 72 00 6b 00  |r.a.m.e.w.o.r.k.|
00000080  20 00 33 00 2e 00 35 00  4c 00 50 00 20 00 28 00  | .3...5.L.P. .(.|
00000090  78 00 36 00 34 00 29 00  20 00 2d 00 20 00 e5 65  |x.6.4.). .-. ..e|
000000a0  2c 67 9e 8a 3a 00 20 00  52 00 65 00 74 00 75 00  |,g..:. .R.e.t.u.|
000000b0  72 00 6e 00 20 00 74 00  79 00 70 00 65 00 3a 00  |r.n. .t.y.p.e.:.|
000000c0  0d 00 0a 00 5b 00 30 00  34 00 2f 00 31 00 38 00  |....[.0.4./.1.8.|
000000d0  2f 00 31 00 30 00 2c 00  31 00 30 00 3a 00 34 00  |/.1.0.,.1.0.:.4.|
000000e0  39 00 3a 00 35 00 32 00  5d 00 20 00 4d 00 69 00  |9.:.5.2.]. .M.i.|
000000f0  63 00 72 00 6f 00 73 00  6f 00 66 00 74 00 20 00  |c.r.o.s.o.f.t. .|
00000100  2e 00 4e 00 45 00 54 00  20 00 46 00 72 00 61 00  |..N.E.T. .F.r.a.|
00000110  6d 00 65 00 77 00 6f 00  72 00 6b 00 20 00 33 00  |m.e.w.o.r.k. .3.|
00000120  2e 00 35 00 4c 00 50 00  20 00 28 00 78 00 36 00  |..5.L.P. .(.x.6.|
00000130  34 00 29 00 20 00 2d 00  20 00 e5 65 2c 67 9e 8a  |4.). .-. ..e,g..|
00000140  3a 00 20 00 4e 00 65 00  74 00 52 00 74 00 52 00  |:. .N.e.t.R.t.R.|
00000150  65 00 74 00 75 00 72 00  6e 00 43 00 68 00 65 00  |e.t.u.r.n.C.h.e.|
00000160  63 00 6b 00 0d 00 0a 00  5b 00 30 00 34 00 2f 00  |c.k.....[.0.4./.|
00000170  31 00 38 00 2f 00 31 00  30 00 2c 00 31 00 30 00  |1.8./.1.0.,.1.0.|
00000180  3a 00 34 00 39 00 3a 00  35 00 32 00 5d 00 20 00  |:.4.9.:.5.2.]. .|
00000190  4d 00 69 00 63 00 72 00  6f 00 73 00 6f 00 66 00  |M.i.c.r.o.s.o.f.|
000001a0  74 00 20 00 2e 00 4e 00  45 00 54 00 20 00 46 00  |t. ...N.E.T. .F.|
000001b0  72 00 61 00 6d 00 65 00  77 00 6f 00 72 00 00 c8  |r.a.m.e.w.o.r...|
000001c0  e5 a4 82 f8 e4 d4 02 00  00 00 00 d0 0b 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by jerrrys on 2011-05-29
i have not ran into this, but here a lead

[http://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+symbol+not+found%3A+%27grub_env_export%27&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=error%3A+symbol+not+found%3A+%27grub_env_export%27&ie=utf-8&oe=utf-8)

and a forum search

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=error%3A+symbol+not+found%3A+%27grub_env_export%27&as_qdr=all&sa=Google+Search&lang=en#866](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=error%3A+symbol+not+found%3A+%27grub_env_export%27&as_qdr=all&sa=Google+Search&lang=en#866)

---

### Post by LiteDrive on 2011-05-30
Awesome. Thanks again, I'll give that a go here in a little bit, as I just came across the same problem when installing 10.10.

---

### Post by Rubi1200 on 2011-05-30
mcfritzl, thanks for posting the results of the script.

I think jerrrys is right and you need to purge and reinstall grub as it seems something may have got messed up with the configuration.

Here is a guide for using the chroot method from the LiveCD:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by mcfritzl on 2011-05-30
Thanks! That worked! Only problem was network manager wasn't working but it's fine because I've had that happen before so I'm going to install wicd...thanks for everyone's help and i hope it works for others who are having the same problem

---

### Post by Rubi1200 on 2011-05-30
Excellent! I am really glad you got things working :-)

---

