---
title: "Can't boot into Windows after install"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by DRSorensen on 2011-06-25
[FONT=Verdana]I've been using Ubuntu 11.04 via the Wubi installer for about a month now. It had some problems and I ended up deleting it so that I could do a full install. I already have Ubuntu on a USB drive (just in case)


Anyway, after numerous problems (my laptop seems to follow Murphy's Law quite strictly), I was able to complete the install.  Unfortunately, Grub does not work. It would boot right into Windows Vista. After following advice from at least 10 different threads, still nothing worked.[/FONT]

[FONT=Verdana]So after failing to install/reinstall/update Grub, I restarted my computer to find that now, it boots straight into Ubuntu, and I don't even have an option to get into Vista.[/FONT]
[FONT=Verdana]
Any ideas? My laptop has never been able to do anything without hours of troubleshooting...


For reference, here's some terminal output:

[FONT=Courier New]
[/FONT][/FONT][FONT=Courier New]sudo fdisk -l:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf54413eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6515    52330713+   7  HPFS/NTFS
/dev/sda2            6516        7296     6272001    5  Extended
/dev/sda5            6516        7053     4316160   83  Linux
/dev/sda6            7053        7296     1954816   82  Linux swap / Solaris



sudo grub:

sudo: grub: command not found [FONT=Verdana](tried /sbin/grub and others, can't find grub launcher)[/FONT]



sudo grub-install --boot-directory=/mnt/boot /dev/sda [FONT=Verdana]([/FONT]after mounting /dev/sda5):

/usr/sbin/grub-setup: warn: Sector 5 is already in use by ZISD; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.



[/FONT]

---

### Post by YesWeCan on 2011-06-25
In Ubuntu run
sudo update-grub
This should detect your Vista and add it to the menu.

The Grub warning about ZISD is because Grub uses some unallocated sectors on the disk that another app has also used. This is not causing your Vista absence.

---

### Post by DRSorensen on 2011-06-25
After running [FONT=Courier New]sudo grub-update [FONT=Verdana](which I'm pretty sure I've tried already) and rebooting, I now get:

[FONT=Courier New]Error: File not found.

Grub rescue>

[FONT=Verdana]at startup. The update didn't have any errors.[/FONT] 

[FONT=Verdana]I'm running off of my USB drive now. For some reason it has no unity bar or bar of any kind. I had to search through the bin (which I could only get open through the 'Examples' folder on the desktop) to find the firefox launcher.[/FONT]
[/FONT][/FONT][/FONT]

---

### Post by Quackers on 2011-06-25
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by DRSorensen on 2011-06-25
Don't know if it's important, but the terminal showed 

[FONT=Courier New]"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.
[/FONT]
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/mnt/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe /GRLDR

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......I..V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1445258 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   104,663,474   104,661,427   7 NTFS / exFAT / HPFS
/dev/sda2         104,665,086   117,209,087    12,544,002   5 Extended
/dev/sda5         104,665,088   113,297,407     8,632,320  83 Linux
/dev/sda6         113,299,456   117,209,087     3,909,632  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,905,278     7,905,247   b W95 FAT32


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1       1,794,048     3,891,199     2,097,152 Data partition (Windows/Linux)
/dev/sdb2           4,096        36,863        32,768 -
/dev/sdb3          36,864     1,794,047     1,757,184 -
/dev/sdb4       3,956,736     3,989,503        32,768 -
/dev/sdb5       3,989,504     3,989,504             1 -
/dev/sdb6              34            34             1 -
/dev/sdb7              35            35             1 -
/dev/sdb8       3,891,200     3,923,967        32,768 Data partition (Windows/Linux)
/dev/sdb9              36            36             1 -
/dev/sdb10             37            37             1 -
/dev/sdb11             38            38             1 -
/dev/sdb12      3,923,968     3,956,735        32,768 EFI System partition
/dev/sdb121 8,273,188,659,167 2,147,483,648-8,271,041,175,518 -
/dev/sdb122 1,281,361,340,349,593,6774,282,394,793,129,366,6083,001,033,452,779,772,932 -
/dev/sdb123 1,801,862,997,568,683,584301,282,515,846,653,563-1,500,580,481,722,030,020 -
/dev/sdb124 178,489,717,203,957,7664,397,328,831,963,214,0804,218,839,114,759,256,315 -
/dev/sdb125              0             0             1 -

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       8574db77-1e6a-4884-9d1a-53d05427c46e   ext3       
/dev/sda1        90B45177B4516130                       ntfs       
/dev/sda5        f64660a2-e12f-4f4a-a602-261f5ca7758a   ext4       
/dev/sda6        1e594623-761e-4293-afc6-5bcd4d11189f   swap       
/dev/sdb1        6B1A-011B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f64660a2-e12f-4f4a-a602-261f5ca7758a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f64660a2-e12f-4f4a-a602-261f5ca7758a
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f64660a2-e12f-4f4a-a602-261f5ca7758a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f64660a2-e12f-4f4a-a602-261f5ca7758a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f64660a2-e12f-4f4a-a602-261f5ca7758a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f64660a2-e12f-4f4a-a602-261f5ca7758a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f64660a2-e12f-4f4a-a602-261f5ca7758a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f64660a2-e12f-4f4a-a602-261f5ca7758a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 90B45177B4516130
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f64660a2-e12f-4f4a-a602-261f5ca7758a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1e594623-761e-4293-afc6-5bcd4d11189f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  52.581726074 = 56.459198464   boot/grub/core.img                             1
  50.916233063 = 54.670888960   boot/grub/grub.cfg                             1
  51.053256989 = 54.818017280   boot/initrd.img-2.6.38-8-generic               1
  53.056140900 = 56.968597504   boot/vmlinuz-2.6.38-8-generic                  1
  51.053256989 = 54.818017280   initrd.img                                     1
  53.056140900 = 56.968597504   vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

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

Unknown GPT Partiton Type
5d2a3afe324fa741b725accc3285a309
Unknown GPT Partiton Type
02e2b83c7e3bdd478a3c7ff2a13cfcec
Unknown GPT Partiton Type
5d2a3afe324fa741b725accc3285a309
Unknown GPT Partiton Type
02e2b83c7e3bdd478a3c7ff2a13cfcec
Unknown GPT Partiton Type
5d2a3afe324fa741b725accc3285a309
Unknown GPT Partiton Type
02e2b83c7e3bdd478a3c7ff2a13cfcec
Unknown GPT Partiton Type
3d750a2e489eb0438337b15192cb1b5e
Unknown GPT Partiton Type
3d750a2e489eb0438337b15192cb1b5e
Unknown GPT Partiton Type
3d750a2e489eb0438337b15192cb1b5e
Unknown GPT Partiton Type
eb58905359534c494e55580002082000
Unknown GPT Partiton Type
b106893f894702f364a58a0e187c884d
Unknown GPT Partiton Type
7d0066b88a0d160066ba00000000bb00
Unknown GPT Partiton Type
064108e188c588d6b80102e837006661
Unknown GPT Partiton Type
52526141000000000000000000000000
Unknown BootLoader on sda2

00000000  b3 fe 8f f1 ff 00 46 bd  57 f8 be 0f 3f 87 ed f3  |......F.W...?...|
00000010  f9 ff 00 96 9d 57 77 62  7f c5 e7 7c 7f d9 3f 7f  |.....Wwb...|..?.|
00000020  9a cb 7f d9 3b ff 00 c0  6f a9 ff 00 d7 8f fe 38  |....;...o......8|
00000030  ff 00 cd 8f 62 0b bf f8  83 f0 7f 66 38 7f a6 3c  |....b......f8..<|
00000040  3f a3 e9 f2 e8 da 3f ec  1f 87 11 f1 70 ff 00 57  |?.....?.....p..W|
00000050  f9 7a 17 fb 4f fe 3c de  97 ff 00 8b b7 f9 ae b7  |.z..O.<.........|
00000060  ff 00 8f bf fc ff 00 fc  5a 6a bf e3 cd ff 00 9b  |........Zj......|
00000070  ff 00 f2 a9 fe 1e 4f 65  cf f1 dc fc 7f d8 7f a1  |......Oe........|
00000080  7c 7f 0f 9f fc 2f d7 e7  ab a4 d0 fc 6f c3 83 70  ||..../......o..p|
00000090  f8 78 8e 3f 3e 93 9d e3  ff 00 16 5d 8f fe 63 fe  |.x.?>......]..c.|
000000a0  2d 19 3f f3 ff 00 f3 35  ff 00 4d 47 fc 7c df f5  |-.?....5..MG.|..|
000000b0  64 ff 00 95 0f f1 bf b2  c4 f8 a2 fe cb e0 6f f4  |d.............o.|
000000c0  bc 0f c5 f3 f5 fe 97 5e  8b e0 b8 e3 f1 79 70 f2  |.......^.....yp.|
000000d0  f8 7e 7d 2e b3 5f f0 13  a4 bf e6 53 7f cc a3 c7  |.~}.._.....S....|
000000e0  7f c7 c7 ff 00 32 9b eb  90 ff 00 33 ff 00 57 8f  |.....2.....3..W.|
000000f0  f5 7f f3 7e fe d3 49 c6  5f ed 3e 39 7e 1f 8f e2  |...~..I._.>9~...|
00000100  6f 87 fa 3f e5 a7 4a bc  a3 e3 e5 c3 ec 1c 7f d5  |o..?..J.........|
00000110  eb d2 7b b1 ff 00 e6 59  0f f9 91 3f f0 05 3f e2  |..{....Y...?..?.|
00000120  f7 fa 7f ce 47 ff 00 1e  17 fd 32 7f 5f f1 b7 b6  |....G.....2._...|
00000130  6c 7f dc a7 e1 f1 fe 1f  8b e1 5f 87 fa 5f c5 f3  |l........._.._..|
00000140  af 5b 4f ed c7 c7 fe d7  fe 7e f9 74 73 30 bf f3  |.[O......~.ts0..|
00000150  21 f6 67 fc 7b ff 00 f3  2d 73 3f f1 e4 ff 00 c7  |!.g.{...-s?.....|
00000160  eb f4 a4 ff 00 8f 7f fe  ad 7f f3 b3 ff 00 9b 1e  |................|
00000170  4f 6b 6e 3f e4 a2 bc 7e  31 f1 f0 f8 d7 e3 fe 97  |Okn?...~1.......|
00000180  fc ff 00 5e a9 65 fd ab  7c 7f 10 e3 f6 1e 1f 2e  |...^.e..|.......|
00000190  a9 67 e4 d7 fc cd 9d c5  fe 7b e9 43 ff 00 51 ff  |.g.......{.C..Q.|
000001a0  00 f0 1a 9f fe 2f ff 00  f5 70 fe 9f f4 c7 e0 f6  |...../...p......|
000001b0  2a d9 7f e4 91 69 f0 f1  93 87 c1 f1 7e 0f 00 fe  |*....i......~...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 83 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  83 00 00 b0 3b 00 00 00  |............;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-06-25
This is the problem
```
 Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)[COLOR="Red"]/mnt/boot/grub[/COLOR] on this drive.
``` The red bit should read /boot/grub.

From the live cd desktop open a terminal and copy/paste these commands in, one at a time pressing enter after each one.
```
sudo mount /dev/sda5 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
``` which should report "finished. No errors"
If it reports an error please run the first command again then this one ```
sudo grub-install --boot-directory=/mnt /dev/sda
```

If no errors try rebooting and see if Ubuntu boots directly.

---

### Post by DRSorensen on 2011-06-25
Now when I boot up it loads Grub, tells me I can press TAB to see command options, then gives me a grub> prompt.

---

### Post by Quackers on 2011-06-25
It may be that the grub files are not configured properly.
I can only suggest that you purge and then re-install grub using the CHROOT section of the guide below.
The partition to be mounted is /dev/sda5 and grub should be installed to /dev/sda

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Rubi1200 on 2011-06-25
I hope Quackers won't mind me jumping in here, but I spotted something which may or may not be an issue.

On sda1, you have this file:
```
/GRLDR
```

I recommend deleting it as it may be interfering with the boot process.

---

### Post by Quackers on 2011-06-25
Not at all Rubi1200 :-)
It certainly may interfere with booting Windows later! That is assuming that we get Ubuntu booting of course :-)

---

### Post by YesWeCan on 2011-06-25
It is vital that the version of Ubuntu on your USB stick is the same as on the HD, otherwise the Grub versions may be different and the files that are installed from the USB will not work with those on the disk.

If they are not the same you have to make a new USB or use the chroot reinstall process.

---

### Post by DRSorensen on 2011-06-25
The purge and reinstall worked! Thank you all for your time and help! Here ends my 8 hour search :D

---

### Post by YesWeCan on 2011-06-25
> **Rubi1200 said:**
> I hope Quackers won't mind me jumping in here, but I spotted something which may or may not be an issue.

On sda1, you have this file:
```
/GRLDR
```

I recommend deleting it as it may be interfering with the boot process.
This is odd. I don't think it will be causing a failure of Grub to boot Ubuntu because the Windows partition is not involved in that process.

When the grub rescue prompt appears it is because the MBR part of Grub2 cannot find the correct /boot/grub files.

The latest symptom of a grub> prompt rather than a grub rescue> prompt is not clear to me.

---

### Post by YesWeCan on 2011-06-25
> **DRSorensen said:**
> The purge and reinstall worked! Thank you all for your time and help! Here ends my 8 hour search :D
Ah, the old grub-enema.

---

### Post by Quackers on 2011-06-25
Glad to hear that :-) Luvverley!
Please mark the thread as solved, using Thread Tools near the top of the page.
Thanks.

---

