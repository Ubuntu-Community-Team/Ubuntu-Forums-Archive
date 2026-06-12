---
title: "Ubuntu Remix 10.10 fails to boot after Install"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by Dilot on 2011-05-28
I installed remix 10.10 from the Try Me, which automatically re-partitions for Ubuntu (kept Windows 7) now when I try to boot into Ubuntu proper I get:

Gave up waiting for root device.  Common Problems:
- Boot args (cat /proc/cndline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/cb439897-5d71-4ae0-8662-fe84fabcf536 does not exsist.
Dropping to shell!

Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

imbedded is my Boot Info

                  ```
[SIZE=1]Boot Info Script 0.60    from 17 May 2011




============================= Boot Info Summary: ===============================



 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector
 
    1 of the same hard drive for core.img. core.img is at this location and
 
    looks in partition 5 for (,msdos5)/boot/grub.

 => No boot loader is installed in the MBR of /dev/sdc.



sda1: __________________________________________________________________________



    File system:       vfat

    Boot sector type:  SYSLINUX 4.03
 2010-10-22 ........>..sr>.........p9...0...~.....~...f...M.f.f....f..0~....>E}.u......

    Boot sector info:   Syslinux looks at sector 3704352 of /dev/sda1 for its
 
                       second stage. SYSLINUX is installed in the  directory.
 
                       The integrity check of the ADV area failed. No errors
 
                       found in the Boot Parameter Block.

    Operating System:

    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys



sdb1: __________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista/7

    Boot sector info:   No errors found in the Boot Parameter Block.

    Operating System:

    Boot files:        /bootmgr /Boot/BCD



sdb2: __________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista/7

    Boot sector info:   No errors found in the Boot Parameter Block.

    Operating System:  Windows 7

    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe



sdb3: __________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista/7

    Boot sector info:   No errors found in the Boot Parameter Block.

    Operating System:

    Boot files:        /BOOTMGR /BOOT/BCD



sdb4: __________________________________________________________________________



    File system:       Extended Partition

    Boot sector type:  Unknown

    Boot sector info:  



sdb5: __________________________________________________________________________



    File system:       ext4

    Boot sector type:  -

    Boot sector info:

    Operating System:  Ubuntu 10.10

    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img



sdb6: __________________________________________________________________________



    File system:       swap

    Boot sector type:  -

    Boot sector info:  



sdc1: __________________________________________________________________________



    File system:       vfat

    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.

    Operating System:  
    
    Boot files:        



============================ Drive/Partition Info: =============================



Drive: sda _____________________________________________________________________



Disk /dev/sda: 8160 MB, 8160018432 bytes

17 heads, 48 sectors/track, 19531 cylinders, total 15937536 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes



Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



/dev/sda1    *          1,656    15,937,535    15,935,880   b W95 FAT32




Drive: sdb _____________________________________________________________________



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes



Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



/dev/sdb1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)

/dev/sdb2           3,074,048   238,297,204   235,223,157   7 NTFS / exFAT / HPFS

/dev/sdb3         296,998,912   312,580,095    15,581,184  17 Hidden NTFS / HPFS

/dev/sdb4         238,299,134   296,998,911    58,699,778   5 Extended

/dev/sdb5         238,299,136   294,483,967    56,184,832  83 Linux
/dev
/sdb6         294,486,016   296,998,911     2,512,896  82 Linux swap / Solaris




Drive: sdc _____________________________________________________________________



Disk /dev/sdc: 2013 MB, 2013265920 bytes

16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes



Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



/dev/sdc1                 255     3,932,159     3,931,905   6 FAT16





"blkid" output: ________________________________________________________________



Device           UUID                                   TYPE       LABEL



/dev/loop0                                              squashfs

/dev/loop1       b65e9ac9-155f-0a4c-aa0c-7d0f0ee4ef5f   ext2       casper-rw

/dev/sda1        E88A-12D2                              vfat       PENDRIVE

/dev/sdb1        CCA288E1A288D17E                       ntfs       System

/dev/sdb2        B22CAF672CAF2577                       ntfs       TI103127W0E

/dev/sdb3        4844F79B44F78A48                       ntfs       HDDRECOVERY

/dev/sdb5        cb439897-5d71-4ae0-8662-fe84fabcf536   ext4       

/dev/sdb6        7e08d626-8b61-4eca-90da-1aa55454d30f   swap       

/dev/sdc1        2CD7-44D1                              vfat       



================================ Mount points: =================================



Device           Mount_Point              Type       Options



/dev/loop0       /rofs                    squashfs   (ro,noatime)

/dev/sda1        /cdrom                   vfat
(rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

/dev/sdb5        /media/cb439897-5d71-4ae0-8662-fe84fabcf536 ext4       (rw,nosuid,nodev,uhelper=udisks)

/dev/sdc1        /media/2CD7-44D1         vfat
(rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)





========================= sda1/syslinux/syslinux.cfg: ==========================



--------------------------------------------------------------------------------

# D-I config version 2.0

include menu.cfg

default vesamenu.c32

prompt 0

timeout 50

ui gfxboot bootlogo

--------------------------------------------------------------------------------



================= sda1: Location of files loaded by Syslinux: ==================



           GiB - GB             File                                 Fragment(s)



            ?? = ??             ldlinux.sys                                    1

            ?? = ??             syslinux/gfxboot.c32                           1

            ?? = ??             syslinux/syslinux.cfg                          1

            ?? = ??             syslinux/vesamenu.c32                          1



============== sda1: Version of COM32(R) files used by Syslinux: ===============



 syslinux/gfxboot.c32               :  COM32R module (v4.xx)

 syslinux/vesamenu.c32              :  COM32R module (v4.xx)



=========================== sdb5/boot/grub/grub.cfg: ===========================



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

set root='(hd1,msdos5)'

search --no-floppy --fs-uuid --set cb439897-5d71-4ae0-8662-fe84fabcf536

if loadfont /usr/share/grub/unicode.pf2 ; then

  set gfxmode=640x480

  load_video

  insmod gfxterm

fi

terminal_output gfxterm

insmod part_msdos

insmod ext2

set root='(hd1,msdos5)'

search --no-floppy --fs-uuid --set cb439897-5d71-4ae0-8662-fe84fabcf536

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

    set root='(hd1,msdos5)'

    search --no-floppy --fs-uuid --set cb439897-5d71-4ae0-8662-fe84fabcf536

    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cb439897-5d71-4ae0-8662-fe84fabcf536 ro   quiet splash

    initrd    /boot/initrd.img-2.6.35-22-generic

}

menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --
class os {

    recordfail

    insmod part_msdos

    insmod ext2

    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set cb439897-5d71-4ae0-8662-fe84fabcf536

    echo    'Loading Linux 2.6.35-22-generic ...'

    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cb439897-5d71-4ae0-8662-fe84fabcf536 ro single
 
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

    set root='(hd1,msdos5)'

    search --no-floppy --fs-uuid --set cb439897-5d71-4ae0-8662-fe84fabcf536

    linux16    /boot/memtest86+.bin

}

menuentry "Memory test (memtest86+, serial console 115200)" {

    insmod part_msdos

    insmod ext2

    set root='(hd1,msdos5)'

    search --no-floppy --fs-uuid --set cb439897-5d71-4ae0-8662-fe84fabcf536

    linux16    /boot/memtest86+.bin console=ttyS0,115200n8

}

### END /etc/grub.d/20_memtest86+ ###



### BEGIN /etc/grub.d/30_os-prober ###

menuentry "Windows 7 (loader) (on /dev/sdb1)" {

    insmod part_msdos

    insmod ntfs

    set root='(hd1,msdos1)'

    search --no-floppy --fs-uuid --set cca288e1a288d17e

    chainloader +1

}

menuentry "Windows 7 (loader) (on /dev/sdb2)" {

    insmod part_msdos

    insmod ntfs

    set root='(hd1,msdos2)'

    search --no-floppy --fs-uuid --set b22caf672caf2577

    chainloader +1

}

menuentry "Windows Vista (loader) (on /dev/sdb3)" {

    insmod part_msdos

    insmod ntfs

    set root='(hd1,msdos3)'

    search --no-floppy --fs-uuid --set 4844f79b44f78a48

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



=============================== sdb5/etc/fstab: ================================



--------------------------------------------------------------------------------

# /etc/fstab: static file system information.

#

# Use 'blkid -o value -s UUID' to print the universally unique identifier

# for a device; this may be used with UUID= as a more robust way to name

# devices that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sdb5 during installation

UUID=cb439897-5d71-4ae0-8662-fe84fabcf536 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sdb6 during installation

UUID=7e08d626-8b61-4eca-90da-1aa55454d30f none            swap    sw              0       0

--------------------------------------------------------------------------------



=================== sdb5: Location of files loaded by Grub: ====================



           GiB - GB             File                                 Fragment(s)



 121.783134460 = 130.763644928  boot/grub/core.img                             1

 115.876789093 = 124.421754880  boot/grub/grub.cfg                             1

 138.168945312 = 148.357775360  boot/initrd.img-2.6.35-22-generic              2

 121.780628204 = 130.760953856  boot/vmlinuz-2.6.35-22-generic                 1

 138.168945312 = 148.357775360  initrd.img                                     2

 121.780628204 = 130.760953856  vmlinuz                                        1



======================== Unknown MBRs/Boot Sectors/etc: ========================



Unknown BootLoader on sdb4



00000000  24 83 24 6a f8 b7 c5 5f  bf c2 a4 50 b3 b0 26 9e  |$.$j..._...P..&.|

00000010  c2 61 51 7a 28 26 69 4f  28 58 03 63 61 1c 03 12  |.aQz(&iO(X.ca...|

00000020  8f 14 f5 af dc 5f 9b 33  b9 73 bc e9 41 30 e4 7a  |....._.3.s..A0.z|

00000030  01 89 84 b1 cf bf 24 2a  ab e9 c0 bc 97 04 19 0a  |......$*........|

00000040  94 ac 78 70 08 60 a2 ad  65 56 aa 23 c5 d7 43 d3  |..xp.`..eV.#..C.|

00000050  af 86 58 08 c3 90 31 78  31 73 63 c6 54 fb db 1a  |..X...1x1sc.T...|

00000060  b2 f3 fc 0f 37 94 d9 4a  c2 91 9b 4a ab 4b 6e 28  |....7..J...J.Kn(|

00000070  bd 42 28 0a 40 a1 1d 41  fa 45 6c 37 3b be 4c 9f  |.B(.@..A.El7;.L.|

00000080  70 d8 79 9b bc 0a 83 c3  78 8a a1 e4 a4 a3 64 31  |p.y.....x.....d1|

00000090  1c e0 ad 23 c1 4c 20 40  a6 20 7c 0f fa c5 03 b9  |...#.L @. |.....|

000000a0  8c 93 fe 4d 4f 17 30 dd  3f 7b 0d 9f 23 86 70 af  |...MO.0.?{..#.p.|

000000b0  83 e5 9d 36 e3 46 32 fc  9f df df ff 90 f0 7c 35  |...6.F2.......|5|

000000c0  e4 0f c1 3d 05 05 8a 28  63 0f c7 b2 30 a7 af 8b  |...=...(c...0...|

000000d0  d5 47 4a 70 1b 75 88 56  bb 95 be e2 10 9e 0b 0a  |.GJp.u.V........|

000000e0  a9 b5 34 2a 5d 96 17 13  2c 22 d2 aa 04 35 2a 8f  |..4*]...,"...5*.|

000000f0  3e 2e 70 46 30 e0 12 e7  aa 27 38 33 ad cd 3d d0  |>.pF0....'83..=.|

00000100  08 f9 32 a6 f8 f5 7b 0f  01 bb 49 f8 a7 27 45 2b  |..2...{...I..'E+|

00000110  b4 8e 58 30 42 f5 18 de  6c 7f 49 cf ca 1c e4 3f  |..X0B...l.I....?|

00000120  1f 70 88 07 ce 8e bf 47  bf 2a f3 76 d8 55 6f b7  |.p.....G.*.v.Uo.|

00000130  54 1b e8 64 52 46 26 05  04 d0 45 69 47 e4 e2 2e  |T..dRF&...EiG...|

00000140  65 68 ab a4 b2 d5 e0 ce  10 9d 52 ad 27 7d 7b 7b  |eh........R.'}{{|

00000150  54 b7 6b 63 08 4c 88 33  52 33 54 f8 b7 2c e7 36  |T.kc.L.3R3T..,.6|

00000160  f6 d4 22 8d d0 37 c1 81  4d f5 4a 0b 36 7d 44 c9  |.."..7..M.J.6}D.|

00000170  cf 77 b8 54 8a 92 a0 29  70 bc 79 93 3d 8a 34 ae  |.w.T...)p.y.=.4.|

00000180  0d e1 aa 86 52 5e ac 29  14 2b 1f 60 e3 6f b3 bb  |....R^.).+.`.o..|

00000190  a8 b8 74 e3 6c 7d 56 b1  50 6f 2e 8c e2 95 c6 bc  |..t.l}V.Po......|

000001a0  03 69 30 9e 73 97 9d 44  4a f7 bb 86 e7 79 50 8c  |.i0.s..DJ....yP.|

000001b0  82 25 73 f9 79 cb 14 f3  bc 42 80 fc 43 64 00 fe  |.%s.y....B..Cd..|

000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 59 03 00 fe  |...........PY...|

000001d0  ff ff 05 fe ff ff 02 50  59 03 00 60 26 00 00 00  |.......PY..`&...|

000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|

00000200





=============================== StdErr Messages: ===============================



/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected[/SIZE]

```Formatting is kinda goosed, but any help would be appreciated!!

I am kinda stuck now as I cannot remove Ubuntu until I can get into it since I did not install it inside windows.

Thanks - Dilot

---

### Post by Hedgehog1 on 2011-05-28
Dilot,

I think I see what has happened; you will need to do TWO things to fix this issue.

1) Install GRUB on your system's hard drive Using the LiveUSB

2) Boot the system WITHOUT the LiveUSB plugged in after that.


So, here is the first things to do:

Please boot off the LiveCD/Live USB, select TRY, and then:

```
sudo mount /dev/sdb5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sdb
```

Then, select 'shutdown' from the menu and shutdown the system.

Remove the LiveUSB

Power up.  If you get the BUSYBOX again, count to 10 and the type 'exit'.  Tell us if the GUI starts.


***The Hedge***

:KS

---

### Post by Dilot on 2011-05-29
Finally got the grub installed, now on boot I still get the busy box, I type exit and it goes dormant, then I get:

[ 1455.913368] INFO: task modprobe :422 blocked for more than 120 seconds.
[ 1455.913919 (numbers change) "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

I can try to install ubuntu 11, but need to figure out how to remove this current version as I did not install in windows and cannot see it in windows remove programs, I can see the partition in disk manager and can delete (would this work?).

Thanks - Dilot

---

