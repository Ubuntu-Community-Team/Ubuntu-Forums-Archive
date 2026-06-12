---
title: "Need help with first Ubuntu run"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by sixeight327 on 2011-06-21
Hello all,

I am new to Ubuntu and linux in general. After trying Ubuntu from a live usb, I finally decided to install it to my hard drive alongside Windows 7. Before installing, I created new partitions for the installation of linux. One 4 GB partition for swap, one 10 GB partition for /, and a separate 10 GB partition for /home. The installation seemingly went smoothly, however i have not been able to actually boot from the hard drive. When my pc restarted, it booted windows. The data from the installation is still on my hard drive, I checked. If anyone could instruct me on how to actually boot Ubuntu, it would be greatly appreciated.

---

### Post by Quackers on 2011-06-21
Welcome to UF.
Where did you install grub to?

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by sixeight327 on 2011-06-21
This is what my results.txt file says.```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 586663192 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30542 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdb4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,717,952   178,810,879   148,092,928   7 NTFS / exFAT / HPFS
/dev/sda3         178,810,880   187,000,831     8,189,952  82 Linux swap / Solaris
/dev/sda4         187,004,926   625,139,711   438,134,786   f W95 Extended (LBA)
/dev/sda5         187,004,928   586,389,503   399,384,576   7 NTFS / exFAT / HPFS
/dev/sda6         586,391,552   605,642,751    19,251,200  83 Linux
/dev/sda7         605,644,800   625,139,711    19,494,912  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4016 MB, 4016045568 bytes
124 heads, 62 sectors/track, 1020 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)
/dev/sdb4           7,839,720     7,843,838         4,119  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       fdc7d379-4aeb-ee47-a4ed-8cdde2813fcf   ext2       casper-rw
/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        7E8EB6A58EB6557D                       ntfs       OS
/dev/sda3        c27891ae-75a4-40c2-b87c-eb04e8d827a1   swap       
/dev/sda5        20BEB85FBEB82F62                       ntfs       DATA
/dev/sda6        bab33082-7eed-4e8e-a6d2-5ffd64b96c95   ext4       
/dev/sda7        e688f88b-67a5-411c-8426-c53a4064eafb   ext4       
/dev/sdb1        0B0A-2B32                              vfat       PENDRIVE
/dev/sdb4        f9debb01-4d99-4be2-8dc4-8520d694b508   ext3       hybrid

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/casper-rw         ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/bab33082-7eed-4e8e-a6d2-5ffd64b96c95 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/e688f88b-67a5-411c-8426-c53a4064eafb ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb4        /media/hybrid            ext3       (rw,nosuid,nodev,uhelper=udisks)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 7E8EB6A58EB6557D
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
# / was on /dev/sda6 during installation
UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=e688f88b-67a5-411c-8426-c53a4064eafb /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=c27891ae-75a4-40c2-b87c-eb04e8d827a1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 279.742835999 = 300.371582976  boot/grub/core.img                             1
 286.182037354 = 307.285622784  boot/grub/grub.cfg                             1
 282.365482330 = 303.187628032  boot/initrd.img-2.6.38-8-generic               2
 280.415401459 = 301.093744640  boot/vmlinuz-2.6.38-8-generic                  1
 282.365482330 = 303.187628032  initrd.img                                     2
 280.415401459 = 301.093744640  vmlinuz                                        1

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

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
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

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  78 a9 d4 01 87 3a 00 00  00 00 00 00 02 00 00 00  |x....:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-06-21
You have installed grub to the Ubuntu root partition, sda6. This is not where grub normally needs to be.
It should be in the mbr of the hard drive - ie /dev/sda

From the live cd desktop please open a terminal and copy/paste these commands into it, one at a time, pressing enter after each line.
```
sudo mount /dev/sda6 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
``` This should report "installation finished. No errors"
If it does, please reboot, when Ubuntu should boot directly.
In your new Ubuntu desktop open up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is configured. You should see the Windows Loader appear. If so, when that's finished, you can reboot, when you should see a grub menu with a choice of which system to boot.

---

### Post by sixeight327 on 2011-06-21
Ok so i am using a different computer for this post. The computer in which i have installed ubuntu is at the grub menu. How do I go about booting up?

---

### Post by Quackers on 2011-06-21
At the grub menu? What does it say?
It should be a list of operating systems and kernels with the top item (Ubuntu) highlighted. It should boot by default on its own if you leave it until the timer counts down.
Or you can press enter.

But I suspect that's not what you're seeing, is it?

---

### Post by sixeight327 on 2011-06-21
There wasnt a timer or any options, 
 
grub>
 
is all it says

---

### Post by Quackers on 2011-06-21
Is your usb flash drive still plugged in? Try without.

---

### Post by sixeight327 on 2011-06-21
I just unplugged the flash drive. Nothing changed.

---

### Post by Quackers on 2011-06-21
Please boot from the live cd/usb again and re-run the boot script and post the output.
There are a couple of oddities in your previous boot script.
The first is that the flash drive seems to have a problem 
```
sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30542 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       [COLOR="Red"]The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.[/COLOR]
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

```
and the second problem seems to be an encrypted swap partition?? Or is it using LVM or raid? Not sure what this is
```
# swap was on /dev/sda3 during installation
#UUID=c27891ae-75a4-40c2-b87c-eb04e8d827a1 none            swap    sw              0       0
[COLOR="Red"]/dev/mapper/cryptswap1 none swap sw 0 0[/COLOR]
--------------------------------------------------------------------------------

```

---

### Post by sixeight327 on 2011-06-21
I'm not sure about the oddities you found but here are the results from the second run
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 586663192 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30542 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdb4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,717,952   178,810,879   148,092,928   7 NTFS / exFAT / HPFS
/dev/sda3         178,810,880   187,000,831     8,189,952  82 Linux swap / Solaris
/dev/sda4         187,004,926   625,139,711   438,134,786   f W95 Extended (LBA)
/dev/sda5         187,004,928   586,389,503   399,384,576   7 NTFS / exFAT / HPFS
/dev/sda6         586,391,552   605,642,751    19,251,200  83 Linux
/dev/sda7         605,644,800   625,139,711    19,494,912  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4016 MB, 4016045568 bytes
124 heads, 62 sectors/track, 1020 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)
/dev/sdb4           7,839,720     7,843,838         4,119  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       fdc7d379-4aeb-ee47-a4ed-8cdde2813fcf   ext2       casper-rw
/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        7E8EB6A58EB6557D                       ntfs       OS
/dev/sda3        c27891ae-75a4-40c2-b87c-eb04e8d827a1   swap       
/dev/sda5        20BEB85FBEB82F62                       ntfs       DATA
/dev/sda6        bab33082-7eed-4e8e-a6d2-5ffd64b96c95   ext4       
/dev/sda7        e688f88b-67a5-411c-8426-c53a4064eafb   ext4       
/dev/sdb1        0B0A-2B32                              vfat       PENDRIVE
/dev/sdb4        f9debb01-4d99-4be2-8dc4-8520d694b508   ext3       hybrid

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb4        /media/hybrid            ext3       (rw,nosuid,nodev,uhelper=udisks)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 7E8EB6A58EB6557D
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
# / was on /dev/sda6 during installation
UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=e688f88b-67a5-411c-8426-c53a4064eafb /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=c27891ae-75a4-40c2-b87c-eb04e8d827a1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 279.742835999 = 300.371582976  boot/grub/core.img                             1
 286.182037354 = 307.285622784  boot/grub/grub.cfg                             1
 279.746692657 = 300.375724032  boot/grub/stage2                               1
 282.365482330 = 303.187628032  boot/initrd.img-2.6.38-8-generic               2
 280.415401459 = 301.093744640  boot/vmlinuz-2.6.38-8-generic                  1
 282.365482330 = 303.187628032  initrd.img                                     2
 280.415401459 = 301.093744640  vmlinuz                                        1

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

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
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

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  78 a9 d4 01 87 3a 00 00  00 00 00 00 02 00 00 00  |x....:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-06-21
When you booted fromn the live cd/usb and ran the commands I gave you earlier, which live cd did you use?
It seems that you used an earlier version. This installed grub legacy, rather than grub2.
You need to use a 11.04 live cd/usb and run those commands again. It may still work, but grub legacy (the old version) may mess things up a little. It it does we will need to purge then re-install grub2.
This is not a problem, just more for you to do :-)

---

### Post by sixeight327 on 2011-06-21
ok I re-did the grub install and got the same results.

---

### Post by Quackers on 2011-06-21
Oh dear. Please re-run the boot script again.

---

### Post by sixeight327 on 2011-06-21
here is the boot info script again, should i run the update grub command while in liveusb or wait until i actually load from hdd?
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 586663192 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30542 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdb4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,717,952   178,810,879   148,092,928   7 NTFS / exFAT / HPFS
/dev/sda3         178,810,880   187,000,831     8,189,952  82 Linux swap / Solaris
/dev/sda4         187,004,926   625,139,711   438,134,786   f W95 Extended (LBA)
/dev/sda5         187,004,928   586,389,503   399,384,576   7 NTFS / exFAT / HPFS
/dev/sda6         586,391,552   605,642,751    19,251,200  83 Linux
/dev/sda7         605,644,800   625,139,711    19,494,912  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4016 MB, 4016045568 bytes
124 heads, 62 sectors/track, 1020 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)
/dev/sdb4           7,839,720     7,843,838         4,119  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       fdc7d379-4aeb-ee47-a4ed-8cdde2813fcf   ext2       casper-rw
/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        7E8EB6A58EB6557D                       ntfs       OS
/dev/sda3        c27891ae-75a4-40c2-b87c-eb04e8d827a1   swap       
/dev/sda5        20BEB85FBEB82F62                       ntfs       DATA
/dev/sda6        bab33082-7eed-4e8e-a6d2-5ffd64b96c95   ext4       
/dev/sda7        e688f88b-67a5-411c-8426-c53a4064eafb   ext4       
/dev/sdb1        0B0A-2B32                              vfat       PENDRIVE
/dev/sdb4        f9debb01-4d99-4be2-8dc4-8520d694b508   ext3       hybrid

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb4        /media/hybrid            ext3       (rw,nosuid,nodev,uhelper=udisks)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bab33082-7eed-4e8e-a6d2-5ffd64b96c95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 7E8EB6A58EB6557D
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
# / was on /dev/sda6 during installation
UUID=bab33082-7eed-4e8e-a6d2-5ffd64b96c95 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=e688f88b-67a5-411c-8426-c53a4064eafb /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=c27891ae-75a4-40c2-b87c-eb04e8d827a1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 279.742835999 = 300.371582976  boot/grub/core.img                             1
 286.182037354 = 307.285622784  boot/grub/grub.cfg                             1
 279.746837616 = 300.375879680  boot/grub/stage2                               1
 282.365482330 = 303.187628032  boot/initrd.img-2.6.38-8-generic               2
 280.415401459 = 301.093744640  boot/vmlinuz-2.6.38-8-generic                  1
 282.365482330 = 303.187628032  initrd.img                                     2
 280.415401459 = 301.093744640  vmlinuz                                        1

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

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
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

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  78 a9 d4 01 87 3a 00 00  00 00 00 00 02 00 00 00  |x....:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-06-21
According to that boot script output you still have grub legacy in the mbr of the drive. Are you sure you are using an 11-04 live cd? And are you sure that's the latest Results.txt file?
If you are, then something's not working.

---

### Post by sixeight327 on 2011-06-21
I am positive that I am using Ubuntu 11.04 (I downloaded it last night), and I am positive that I am using the latest results.txt (that one was actually called results2.txt for it was the third one that was created).

---

### Post by Quackers on 2011-06-21
Very odd this is.
When you copy/pasted the command into the terminal what messages did you see, if any?

---

### Post by sixeight327 on 2011-06-21
the mount command yielded no messages but the install command yielded these messages
```

Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb

```

---

### Post by Quackers on 2011-06-21
I'm not sure why there is a device map.
From the live desktop please go to System > Admin > gparted and wait for it to scan your drive.
By default it will show the partition layout for /dev/sda
In the upper right you will see a box with /dev/sda in it. It has a little down arrow next to it. Please click on that arrow and in the drop-down box you will see /dev/sdb and any other attached discs.
Is there an entry there for /dev/mapper?
And if so, what shows for that?

---

### Post by sixeight327 on 2011-06-21
there is no entry for dev mapper just "pendrive" and "hybrid"

---

### Post by Quackers on 2011-06-21
What's in pendrive and hybrid please?

---

### Post by sixeight327 on 2011-06-21
[ whats in the screenshot above is all that shows up

---

### Post by Quackers on 2011-06-21
no screenshot :-)

---

### Post by sixeight327 on 2011-06-21
pendrive is my usb drive, and what the liveusb is installed to and hybrid is a 2MB space somewhere on my computer

---

### Post by Quackers on 2011-06-21
I can't think what a hybrid is, unless the system has used GUID partitioning at some time, or maybe if the hard drive had been used in a Mac, perhaps.
Are you using, or have you used LVM or raid on this disc?

---

### Post by sixeight327 on 2011-06-21
Ive never used raid, or lvm. The PC that I am using has windows 7 on it.

---

### Post by Quackers on 2011-06-21
Yes I appreciate that, but the hard drive could have been used in a Mac previously, or could have been used with a GUID partition system.

---

### Post by sixeight327 on 2011-06-21
should I just completely start over by downloading the iso, mounting to the usb and just instaling it all over again. What exactly did I do wrong the first time that is causing this mess? and how can I prevent this the second time? Its very frustrating that I've literally spent all day trying to get this to boot.

---

### Post by Quackers on 2011-06-21
I'm sure it is frustrating for you. It is for me.
The problem may be a partitioning type problem, I'm really not sure. There is a swap partition mentioned in the boot scripts which appears to be encrypted, possibly, and it's on a /dev/mapper partition. Sadly we can't seem to find this partition even though it is mentioned in /etc/fstab, though its UUID is commented out.
This could be the "hybrid" partition mentioned in gparted, but maybe not.
If these problems exist in the new installation the same thing will happen.

I would advise waiting for others to make suggestions.
I will contact some other users and ask them to take a look. However, they don't appear to be online at the moment.

---

### Post by oldfred on 2011-06-21
Could you try reinstalling grub2 like the instructions Quackers posted except use boot not root in the command. I know they recommend boot with grub2 v1.99 but I did not know that using boot would install grub legacy??

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
[COLOR=Red]sudo mount /dev/sda6 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
[COLOR=Red]sudo grub-install --boot-directory=/mnt/ /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Did you select encryption on the swap partition when you installed? And I thought they stopped using the device.map, but I do not think that causes an error.

Upgrade Guide/Issues Including 11.04 mörgæs
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
Grub 1.99 Submenus - drs305
[http://ubuntuforums.org/showthread.php?t=1739336](http://ubuntuforums.org/showthread.php?t=1739336)
New for grub 1.99
sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
Please note that the --boot-directory switch is new in Natty and is to be preferred, in case someone tries to tell you that should be --root-directory.

---

### Post by oldfred on 2011-06-21
This says the root version should still work, but the boot version is now preferred for grub 1.99.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

And if anything I am more confused if it is /mnt or /mnt/boot

From above link:
> sudo grub-install --boot-directory=/mnt/boot /dev/sdX
Example:  *sudo grub-install --**b**oot-directory=/mnt /dev/sd**a*** 


---

### Post by srs5694 on 2011-06-21
There's no evidence of stray GPT data on the drive, as has been suggested as a possible culprit. (The Boot Info Script is pretty good about reporting such things.) Thus, I think you can rule that out as a possibility.

My suggestion is more practical: Use [Super GRUB 2 Disk](http://www.supergrubdisk.org) (note: Super GRUB ***2*** disk, not just Super GRUB [no number] Disk) to boot the computer. It *should* be able to detect your GRUB files and get you booted into your regular system. By itself, of course, this is just a workaround, but it should then be possible to re-install GRUB 2 from your (hopefully now working) Ubuntu installation. That might work better than doing it from an emergency disk.

---

### Post by sixeight327 on 2011-06-21
Thank all of you for your help with this. While I was messing around with the configuration, I accidentally corrupted my windows os making me unable to boot even windows. As a result, I just wiped the whole hdd and installed ubuntu to the whole hdd.

---

### Post by Quackers on 2011-06-21
Thanks for looking srs5694 and oldfred :-)  I'm a bit lost as to what's happening here, myself :-)

oldfred, I think the ```
sudo grub-install --boot-directory=/mnt[COLOR="Red"]/boot[/COLOR] /dev/sdX
``` is used when mounting a separate boot partition as well as the root partition.

sixeight327,
how are things now that you've re-installed Ubuntu?

---

