---
title: "GRUB error. No error number"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by martin11ph on 2011-12-15
I don't normally post a thread until I've searched for a solution to my exact problem. However, this seems to be uncommon. I see people having problems with GRUB and getting an error number. I, on the other hand, did not see any. My laptop has 2 drives C: and D:

Windows is on C: and I installed Ubuntu 9.1 on D. After installation, I was able to see the GRUB menu and booted Ubuntu. I tried to upgrade but decided to do it later. I shut down the PC. When I turned it on again, the laptop kept restarting. First it loads the HP splash screen, then a black screen with one line "GRUB loading..." appears for a split-second and then goes back to the HP splash screen. This repeats without any end. I am currently on Ubuntu via Live-CD. Hope someone can help. Again, there is no error number. Just "GRUB loading...":(

---

### Post by coffeecat on 2011-12-15
Grub errors with numbers are from legacy grub, which you will only see if you are running Ubuntu 9.04 or earlier, or have upgraded from the same. Ubuntu 9.10 was the first release to come with grub2, so you won't see error numbers. You should see a more helpful text error message, except that it seems that you see the grub loading message for only a moment.

Boot up the live Ubuntu CD, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

This will, at least, give us an overview of your system. Whether it helps to find out what the problem is, I'm not sure. But try it anyway.

I guess you may know that Ubuntu 9.10 is now unsupported, because you mention considering upgrading.

---

### Post by martin11ph on 2011-12-15
Thank you for helping me with this problem.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (UUID=c4188555-5139-49eb-a078-9364fd9ce252)/boot/grub on this 
    drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 407551 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. The 
                       info in the boot sector on the starting sector of the 
                       MFT Mirror is wrong. According to the info in the boot 
                       sector, sda2 has 930207743 sectors, but according to 
                       the info from fdisk, it has 407551 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda3 starts 
                       at sector 930619392. But according to the info from 
                       fdisk, sda3 starts at sector 409600. According to the 
                       info in the boot sector, sda3 has 45940735 sectors, 
                       but according to the info from fdisk, it has 930207743 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda4 starts 
                       at sector 976560128. But according to the info from 
                       fdisk, sda4 starts at sector 930617344. According to 
                       the info in the boot sector, sda4 has 210992 sectors.. 
                       But according to the info from the partition table, it 
                       has 46153775 sectors.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2fbfe761

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   930,617,343   930,207,744  42 SFS
/dev/sda4         930,617,344   976,771,119    46,153,776  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0edb5de8

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   943,834,814   943,832,767   7 NTFS / exFAT / HPFS
/dev/sdb2         943,834,815   976,768,064    32,933,250   5 Extended
/dev/sdb5         943,834,878   975,290,084    31,455,207  83 Linux
/dev/sdb6         975,290,148   976,768,064     1,477,917  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        88549E3E549E2F46                       ntfs       SYSTEM
/dev/sda2        F4CA5D7CCA5D3C54                       ntfs       OS
/dev/sda3        64DC3DBFDC3D8BF4                       ntfs       RECOVERY
/dev/sda4        D21B-4093                              vfat       HP_TOOLS
/dev/sdb1        F61810461810086F                       ntfs       DATA
/dev/sdb5        c4188555-5139-49eb-a078-9364fd9ce252   ext4       
/dev/sdb6        6bf3bf03-cebf-46ae-a0aa-f2a4a29a6fb0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /cdrom                   iso9660    (rw)


=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set c4188555-5139-49eb-a078-9364fd9ce252
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c4188555-5139-49eb-a078-9364fd9ce252
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c4188555-5139-49eb-a078-9364fd9ce252 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c4188555-5139-49eb-a078-9364fd9ce252
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c4188555-5139-49eb-a078-9364fd9ce252 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 88549e3e549e2f46
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set f4ca5d7cca5d3c54
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=c4188555-5139-49eb-a078-9364fd9ce252 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6bf3bf03-cebf-46ae-a0aa-f2a4a29a6fb0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.31-14-generic              2
               =                boot/vmlinuz-2.6.31-14-generic                 2
               =                initrd.img                                     2
               =                vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  02 00 4f 8e 00 00 00 00  10 00 00 00 60 00 00 00  |..O.........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  e7 b3 19 9e 82 55 cb 01  e7 b3 19 9e 82 55 cb 01  |.....U.......U..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  e7 b3 19 9e 82 55 cb 01  |.............U..|
000000c0  e7 b3 19 9e 82 55 cb 01  e7 b3 19 9e 82 55 cb 01  |.....U.......U..|
000000d0  e7 b3 19 9e 82 55 cb 01  00 40 00 00 00 00 00 00  |.....U...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 42 00 01 d8 97  b0 00 00 00 50 00 00 00  |!@UB........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 42 21 01 fd fd  |........!.TB!...|
00000190  00 00 01 00 00 20 4f 8e  ff ff ff ff 00 00 00 00  |..... O.........|
000001a0  00 00 04 00 00 00 00 00  21 40 55 42 00 01 d8 97  |........!@UB....|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 42 21 01 fd fd  00 00 01 00 00 20 02 00  |!.TB!........ ..|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  a2 e1 4e 65 13 00 00 00  |FILE0.....Ne....|
00000010  01 00 01 00 38 00 01 00  d0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  e2 17 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  0c e4 1f 5b cb 27 cb 01  0c e4 1f 5b cb 27 cb 01  |...[.'.....[.'..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  0c e4 1f 5b cb 27 cb 01  |...........[.'..|
000000c0  0c e4 1f 5b cb 27 cb 01  0c e4 1f 5b cb 27 cb 01  |...[.'.....[.'..|
000000d0  0c e4 1f 5b cb 27 cb 01  00 40 00 00 00 00 00 00  |...[.'...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  ff d1 01 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 20 1d 00 00 00 00  |@......... .....|
00000130  00 00 20 1d 00 00 00 00  00 00 20 1d 00 00 00 00  |.. ....... .....|
00000140  33 80 be 00 00 00 0c 43  80 13 01 26 8a 5f 04 00  |3......C...&._..|
00000150  b0 00 00 00 78 00 00 00  01 00 40 00 00 00 05 00  |....x.....@.....|
00000160  00 00 00 00 00 00 00 00  0f 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 00 01 00 00 00 00 00  |@...............|
00000180  08 f0 00 00 00 00 00 00  08 f0 00 00 00 00 00 00  |................|
00000190  31 01 ff ff 0b 31 06 2c  9b 02 31 01 9b 45 72 41  |1....1.,..1..ErA|
000001a0  01 b3 10 63 02 41 01 78  9e 07 fe 41 02 cb 0a 6d  |...c.A.x...A...m|
000001b0  03 41 01 45 39 da fc 41  01 41 a3 7b 03 31 02 08  |.A.E9..A.A.{.1..|
000001c0  8c b2 00 00 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001d0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001e0  ff ff ff ff 00 00 00 00  08 00 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 00 00 00  ff ff ff ff 00 00 e2 17  |1...............|
00000200
Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ce 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 35 3a  |........?.... 5:|
00000020  30 38 03 00 19 03 00 00  00 00 00 00 02 00 00 00  |08..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 93 40 1b d2 4e  4f 20 4e 41 4d 45 20 20  |..).@..NO NAME  |
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

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by coffeecat on 2011-12-15
The boot script is reporting some inconsistencies in your Windows partitions in your first sda drive, which may or may not be important, but let's concentrate on the grub issue for now.

This is interesting:

> **martin11ph said:**
> 
```

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (UUID=c4188555-5139-49eb-a078-9364fd9ce252)/boot/grub on this 
    drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
```

You have grub installed in the mbr of both physical drives. Grub in sdb in looking to partition 5, sdb5, which is your Ubuntu root partition. If the BIOS was set to boot from sdb, then this *should* work OK. Grub in sda is looking to the partition with a UUID of c4188555-5139-49eb-a078-9364fd9ce252, which is sdb5. However, the boot script output is saying, "on this drive.". "This drive" would be sda, not sdb, so I wonder if the problem is there.

I suggest you try this first. Set the BIOS so that it boots from the sdb drive, the second physical drive. I'm avoiding using "C:" and "D:" terms, because these are Windows conventions and can be misleading, since they can refer to partitions or whole physical drives.

If that doesn't help, post back and we'll investigate further and/or I can show you how to re-install grub to sda to see if that helps.

---

### Post by martin11ph on 2011-12-15
Hi, sorry for the long delay.

My BIOS does not allow me to select which drive to boot. I can choose DVD/USB/HD but cannot choose which one among the HDs.

---

### Post by coffeecat on 2011-12-15
Yes, with a laptop that would make sense. But before you try the next bit, double-check in the BIOS. With some BIOS's there is a different entry to set the hard drive priority, different from the Optical/USB/HD entry that is. But I can understand why a laptop BIOS would not allow you to do this.

The next step is to re-install grub to the mbr of sda. To be honest, I'm not sure whether this will help, because from what you post in your OP, it seems that the system was booting with the current grub setup, and I don't see why it should have stopped doing so. Whatever, the following won't do any harm, so it is worth trying.

Boot up your Ubuntu 9.10 live CD and open a terminal. Run these two commands:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Yes, that is sdb5 in the first line and sda in the second. Now reboot and see if that helps.

---

### Post by martin11ph on 2011-12-15
Thank you! I did a similar one earlier but used /sdb5 on the first line and /sdb on the second. It was from a Google search. You got it right straight away though. :D

I booted straight to Windows but I am going to try rebooting to Ubuntu after posting this reply. Hopefully, everything is settled. 

I'm studying to be a Linux Network Admin and hope to be some help here in the future too.

---

### Post by coffeecat on 2011-12-15
> **martin11ph said:**
> Thank you! I did a similar one earlier but used /sdb5 on the first line and /sdb on the second. 

That would explain grub in the mbr of sdb5, which puzzled me! :wink:

Glad that worked, and good luck with the studies. I have this thread subscribed, so if you have any problems booting into Ubuntu, I'll notice if you post back. And since you can boot into Windows, those oddities in the boot script output for the Windows partitions can safely be ignored, I guess.

---

### Post by martin11ph on 2011-12-15
Hmm. . .it happened again. When I logged out of windows, grub no longer loaded. I will try to replicate the steps and see what happens. I wonder if it is because I opened Disk Management while in Windows. Didn't touch anything, just took a look at the partitions. 

Thanks for the encouragement. :)

---

### Post by coffeecat on 2011-12-15
> **martin11ph said:**
> Hmm. . .it happened again. When I logged out of windows, grub no longer loaded. 

:idea: !

I know what's happening. What make of laptop do you have? Have a look at these links:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

There's a rogue Windows application writing to the extended mbr (also known as the embedding area) and overwriting grub's core.img. The second link may help you to identify which the app is.

---

### Post by martin11ph on 2011-12-15
My laptop is a HP dv7-4190us from Amazon. I have upgraded to 10. something just now. Took me ~3 hours. Sorry about that. Yeah, Windows seems to be the culprit. I tried rebooting and logging in to Ubuntu again with no GRUB problems. I'm reading the links now. Thank you for the assistance!

Edit: 

> Some programs which might be writing  to the extended MBR: 
HP:  Credential Manager, **Recovery Manager**, ProtectTools, PC Angel, Backup and Recovery 


Busted. I have this.

---

### Post by coffeecat on 2011-12-15
> **martin11ph said:**
> 
Busted. I have this.

:)

Ironic that an application called recovery manager should break a bootloader!

---

### Post by martin11ph on 2011-12-15
Its also the cause why this Ubuntu installation has taken so long. Pre-partitioned drives when I got em. 

I don't think I can disable this program. Is it fine if I go with getting Legacy Grub?

Solution 4 on [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR) might not work as I already have Grub on the secondary hard drive. Weird.

Is solution 3 feasible? What do you suggest I try? Thank you for all your help. :)

---

### Post by coffeecat on 2011-12-15
> **martin11ph said:**
> Its also the cause why this Ubuntu installation has taken so long. Pre-partitioned drives when I got em. 

Yes, HP machines come with 4 primary partitions, which complicates things. I have a HP netbook, so I understand, but so far nothing that came pre-installed on the Windows partition has broken grub.

> **martin11ph said:**
> I don't think I can disable this program. Is it fine if I go with getting Legacy Grub?

Disabling the app is the best solution, but if you really cannot disable it, legacy grub may or may not work. It depends where in the embedding area the HP Recovery Manager is writing. Legacy grub stores its stage 1.5 in the embedding area, and legacy grub's 1.5 is smaller than grub2's equivalent core.img, but it would be the luck of the draw.

> **martin11ph said:**
> Solution 4 on [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR) might not work as I already have Grub on the secondary hard drive. Weird.

No, that won't work from sdb because you've already established that you can't boot from sdb in the BIOS. Grub in sdb is doing nothing. One (untidy) option would be to re-install the Windows bootloader to sda so that the system boots into Windows only if you have nothing attached. Then, install grub to a flash drive which you keep only for booting Ubuntu. With the flash drive plugged in, you get the grub menu.

> **martin11ph said:**
> Is solution 3 feasible? What do you suggest I try? Thank you for all your help. :)

It might be feasible. Installing grub 2 to the partition boot sector is hit and miss, hence the --force option. Even with the force option, it sometimes fails, depending on the drive geometry, or so I believe. When I tried it a couple of years ago (installing grub to the PBR) it worked on a couple of laptops but not on the desktops I tried. I have no idea why some worked, and not others.

---

### Post by martin11ph on 2011-12-15
Hmm. . .I guess I can do without the Recovery Console. I'll update again after. Thank you for the input.

In the event that it will not work, here is what I tried for solution 3:

ubuntu@ubuntu:~$ sudo grub-install --recheck --force /dev/sdb5
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

Edit:
Still does not work. Recovery console already uninstalled. I wonder what else is messing it up.

---

### Post by martin11ph on 2011-12-15
I reinstalled grub2 on Ubuntu 10.04 and now my wired LAN stopped working on both Ubuntu and Windows. I can still connect via Wifi on Windows but not on Ubuntu. This is beyond weird.

---

### Post by coffeecat on 2011-12-16
> **martin11ph said:**
> I reinstalled grub2 on Ubuntu 10.04 and now my wired LAN stopped working on both Ubuntu and Windows. I can still connect via Wifi on Windows but not on Ubuntu. This is beyond weird.

I cannot think of a connection between re-installing grub and ethernet and wi-fi connections. It must be co-incidence. Installing grub simply writes some code to the mbr and the extended mbr. Since ethernet is not working in both operating systems, you'll need to look at common hardware factors such as the LAN card itself, the ethernet cable and so on. 

You appear to have upgraded from 9.10 to 10.04 sometime over the course of this thread. Did the wi-fi stop working immediately after the upgrade? Because, if so, that suggests a driver problem in 10·04.

---

### Post by martin11ph on 2011-12-16
> **coffeecat said:**
> You appear to have upgraded from 9.10 to 10.04 sometime over the course of this thread. Did the wi-fi stop working immediately after the upgrade? Because, if so, that suggests a driver problem in 10·04.

Nope. It worked fine for some time. It was only when I used the Synaptics Update Manager to reinstall grub did the problem start. :( I agree though that it might just be a coincidence.

---

### Post by coffeecat on 2011-12-16
> **martin11ph said:**
> Nope. It worked fine for some time. It was only when I used the Synaptics Update Manager to reinstall grub did the problem start. :( I agree though that it might just be a coincidence.

As you say, beyond weird. And ethernet doesn't work in Windows either?

It would be a good idea to start a new thread about this. Link back to this one and hopefully someone will come up with some ideas. I'll keep a lookout for it. When you start your thread, post the terminal output of these:

```
lspci
ifconfig
iwconfig
sudo lshw -C network
```

---

### Post by martin11ph on 2011-12-16
Unfortunately, I need to resolve this problem asap. I don't think I can let it stay any longer. I am planning to reformat all my drives and asked for tips here:

[http://ubuntuforums.org/showthread.php?t=1896004](http://ubuntuforums.org/showthread.php?t=1896004)

The downside to this is if the problem remains even after the reformat. Might suggest my LAN card is faulty(checked cable already).

---

### Post by coffeecat on 2011-12-16
> **martin11ph said:**
> Unfortunately, I need to resolve this problem asap. I don't think I can let it stay any longer. I am planning to reformat all my drives and asked for tips here:

[http://ubuntuforums.org/showthread.php?t=1896004](http://ubuntuforums.org/showthread.php?t=1896004)

The downside to this is if the problem remains even after the reformat. Might suggest my LAN card is faulty(checked cable already).

Last suggestions for this thread: run the Ubuntu CD live and check both the ethernet and wireless from the live session. That will help to narrow possibilities. Also - try a different ethernet port in your router. Possibly even reboot the router and check the settings. I've not heard of a router spontaneously blocking all ethernet connections, but you never know.

---

### Post by martin11ph on 2011-12-16
You have a good point there. My router seems to be acting up. Let me double check.

Edit: Router is now fine. Still nothing on this laptop. Double checked connection and wiring on another. :(

---

### Post by martin11ph on 2011-12-17
Just an update. I installed Ubuntu 11 over the existing 10.04. The ethernet suddenly started working again which baffles me. It must mean that my grub reinstall really was the cause of its problem. In any case, I am now shown a grub menu where I need to type
> 
set boot=(hd0,2)
bootloader +1
boot

I recall seeing this being done at an office. It also worked for me just now. Doing that will bring me to Windows. I now wonder what will happen if I reformat the Windows drive and reinstall. I also wonder what will be the command to enter Ubuntu instead of Windows.

Although the ethernet problem is fixed, I have set my mind to reformat anyway given that the free OS is Windows 7 Home Premium and I have an Ultimate CD here.

---

### Post by westie457 on 2011-12-17
Hello, not sure if this is the main cause of your problems however it certainly is not helping things. > Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2fbfe761

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   930,617,343   930,207,744  42 SFS
/dev/sda4         930,617,344   976,771,119    46,153,776  42 SFS

Somehow your 1st hard drive has been converted to 'Dynamic' which is something Windows can work with. Sadly not much else can. No operating systems (including Windows) can be installed to a dynamic disk. 

I am sure however that 'coffeecat' or somebody else will correct me for being wrong. 

While it is possible to convert a hard drive back to 'normal' there is no guarantee that the procedure will work and Microsoft say that usually the only thing to do is repartition and format the hard drive and start over.

Best advice is to fix the Windows boot and back up everything you want. Here I would include the Windows installation, any personal files and the 'recovery partition', also now would be a good time to make a Windows recovery dvd for future repairs as needed.

Hope this helps.

---

### Post by martin11ph on 2011-12-17
Hi westie. You are right there. I have accidentally converted my primary boot drive to dynamic whilst configuring my partitions via Computer Management.

I have already backed up my files and plan to reformat the entire sda and reinstall Windows. Am I right in assuming that grub needs to be reinstalled in sda after? I am also wondering why the grub console was shown lately instead of the typical options.

---

### Post by coffeecat on 2011-12-17
> **westie457 said:**
> Somehow your 1st hard drive has been converted to 'Dynamic' which is something Windows can work with. Sadly not much else can. No operating systems (including Windows) can be installed to a dynamic disk. 

Good spot, westie457, and apologies to martin11ph for missing that.

> **martin11ph said:**
> I have already backed up my files and plan to reformat the entire sda and reinstall Windows. Am I right in assuming that grub needs to be reinstalled in sda after? I am also wondering why the grub console was shown lately instead of the typical options.

You need to install grub to the mbr of sda whether you install Ubuntu to sda or sdb, otherwise grub won't work - you mentioned that you can't set the BIOS to boot from sdb.

I don't understand why you were getting a grub console recently. I don't think the dynamic partitions were responsible for that or the ethernet problems, but as westie457 says, it doesn't help.

---

### Post by martin11ph on 2011-12-17
No need for apologies.

I have finished installing Windows already. I formatted the partition and it still remains a dynamic drive. Will this still hamper my dual-boot? I've seen some software that fixes this back to a simple drive but I would like advice first.

---

### Post by coffeecat on 2011-12-17
> **martin11ph said:**
> I have finished installing Windows already. I formatted the partition and it still remains a dynamic drive.

I have no direct experience of dynamic drives and I intend to keep it that way! Maybe (stress on maybe) you needed to completely reformat the whole drive with a new partition table first. My guess is that the Windows installer, seeing that the other partitions were dynamic, took it into its head to make the Windows C: partition dynamic as well, despite your reformatting.

> **martin11ph said:**
> Will this still hamper my dual-boot? I've seen some software that fixes this back to a simple drive but I would like advice first.

To the first question, I don't know. It's certainly a complication you can do without. I have seen other threads where Windows software has successfully converted dynamic partitions back to conventional ones.

---

### Post by martin11ph on 2011-12-17
I would like to try and install grub again if possible. Can you teach me how? At the moment, I am directly booted into windows. My guess is I will need to use the live cd again to reinstall it. If it doesn't work, I will have to try converting this dynamic drive.

---

### Post by coffeecat on 2011-12-18
I'm not quite sure where you are with Ubuntu on sdb. Is the Ubuntu root partition still sdb5? Have a look at my post #6. If Ubuntu is still on sdb5, run those two commands from the live CD. If not, all you need do is to substitute the partition it is on for /dev/sdb5 in the first command.

But what you should do is to use the same version of Ubuntu on the live CD as you have installed to sdb5. There are different point versions of grub2 that come with the different releases of Ubuntu, and the differences *might* lead to incompatibilities.

---

### Post by martin11ph on 2011-12-19
I double checked with fdisk -l and found Ubuntu 11 to be on SD5 still. I did the two steps again which brings me back to the grub console. I still need to do again:

> set boot=(hd0,2)
bootloader +1
bootI did try the following in the hopes that it will boot Ubuntu. It failed though.

> set boot=(hd1,2)
 bootloader +1
 bootAny ideas? Thank you both for your help.

Edit: 
I rebooted from Windows and found that grub(console this time around) failed to load again. Since I had a fresh Windows install, this could mean that the dynamic disk is interfering. I haven't had any experience with this. Is there a program on Ubuntu that can be used to to fix my sda? That is, if I learn how to boot from Ubuntu via grub console.

Edit2:
I might try this EASEUS Partition Master for Windows. I know this is a Linux forum but if anyone has experience with it, please do share.

---

### Post by martin11ph on 2011-12-19
Major update:

I used EASEUS Partition Master 9.0.0 Server Edition successfully to change my dynamic drive to a basic drive. I also noticed that Windows does not seem to write to the MBR anymore. The grub console shows now every time I restart. Also, I can now boot windows using the old method again:

> set root=(hd0,1)
bootloader +1
boot 			 		

I read that hd0,1 is for old grub versions and hd0,2 is for grub2. Why it is working now, I have no idea. As of now, I still do not know the command on how to access the Ubuntu OS. When replacing hd0,1 with hd1,1 and hd1,2 it says "BOOTMGR is missing".

---

### Post by coffeecat on 2011-12-19
A few things.

Are you sure you mean "bootloader"? As far as I can make out that is not a grub2 command. Or do you mean chainloader? chainloader only works if there are boot files in the boot sector of the partition you are booting to. Which means that you would need to install grub to the PBR of sdb5 (if you still have Ubuntu on sdb5) and even then it is not guaranteed to work with grub2. Chainloading used to work quite nicely with legacy grub, but it's uncertain with grub2 because the core.img file takes up too much room.

Next thing. In grub2, (hd0,1) is sda1, (hd0,2) is sda2, (hd1,1) is sdb1 and (hd1,2) is sdb2. Your sdb5 would be (hd1,5).

If your Ubuntu partition is still sdb5, have you tried simply re-installing grub with the commands I gave earlier? If it isn't, and now that you have successfully converted your dynamic partitions to basic ones, run the boot script again and that might help.

---

### Post by martin11ph on 2011-12-19
Ah yes. Really sorry about that. It is chainloader +1.

I see. So that's how chainloader works. Everytime I reinstall grub using the script, it appears as a console which is why I am baffled. Right after converting my dynamic disk to basic, I did that and get a console still.

I also tried setting root to hd1,5 but I forgot what the error message was. I'll try it again now and edit the post.

Edit: setting root to hd1,5 will give the error "Invalid Signature" when typing chainloader +1

Still, Ubuntu is definitely on sdb5. What is PBR and can we try installing grub there? Thank you.

---

### Post by coffeecat on 2011-12-20
> **martin11ph said:**
> 
Edit: setting root to hd1,5 will give the error "Invalid Signature" when typing chainloader +1

That's because grub is not in the partition boot sector of sdb5

> **martin11ph said:**
> Still, Ubuntu is definitely on sdb5. What is PBR and can we try installing grub there? Thank you.

Even if it worked, and there's no guarantee it would, I suggest trying re-installing grub to the mbr with the commands I posted earlier first. You've just converted a dynamic disk to basic. I really don't know exactly what that does, but I wouldn't be surprised if it messes up grub. Grub code is installed to the first 440 bytes of the mbr. The partition table comes immediately next, and then the embedding area (also called extended mbr) where grub's core.img is. The dynamic -> basic conversion will have rewritten the partition table and it could very well involve the embedding area, which would affect grub. 

It only takes a couple of minutes to re-install grub properly from the CD. If that doesn't work then by all means try installing it to the partition, but that will be a very inelegant solution.

Re-installing grub to the mbr of sda when Ubuntu is on sdb5. From the live CD:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Installing grub to the partition boot sector of sdb5:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb5
```

Or you may need:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --force --root-directory=/mnt /dev/sdb5
```

You only need to run the mount command once, if you try the grub-install to sdb5 and then need to run it again with the force option.

---

### Post by martin11ph on 2011-12-20
> **coffeecat said:**
> 
Re-installing grub to the mbr of sda when Ubuntu is on sdb5. From the live CD:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Installing grub to the partition boot sector of sdb5:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb5
```Or you may need:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --force --root-directory=/mnt /dev/sdb5
```You only need to run the mount command once, if you try the grub-install to sdb5 and then need to run it again with the force option.

Hi coffeecat, I'm sorry for forgetting to mention that after converting the disk to basic, I right away reinstalled grub using the script you gave. It still gives me the grub console. :( 

I will try it one more time and if it fails, I will try installing to sdb5. :)

---

### Post by coffeecat on 2011-12-20
> **martin11ph said:**
> Hi coffeecat, I'm sorry for forgetting to mention that after converting the disk to basic, I right away reinstalled grub using the script you gave. It still gives me the grub console. :( 

I will try it one more time and if it fails, I will try installing to sdb5. :)

If grub is failing after installing to the mbr with those commands, then something more fundamental must be wrong. One question: are you installing grub with the same version Ubuntu CD as you have running on the hard drive? There are minor version variations of grub2 in recent releases of Ubuntu, and it may be necessary to use the same point version.

---

### Post by martin11ph on 2011-12-20
> **coffeecat said:**
> If grub is failing after installing to the mbr with those commands, then something more fundamental must be wrong. One question: are you installing grub with the same version Ubuntu CD as you have running on the hard drive? There are minor version variations of grub2 in recent releases of Ubuntu, and it may be necessary to use the same point version.

So I tried the same commands again and I still get the console. It says version 1.99-12ubuntu5 and this has always been in place when I installed Ubuntu 11.10. I also installed grub using the same Ubuntu 11.10 CD.

I did this after:

> sudo mount /dev/sdb5 /mnt
sudo grub-install --force --root-directory=/mnt /dev/sdb5

I then tried booting:
> 
set root=(hd1,5)
chainloader +1
bootInstead of the usual error, it brings me back to the grub console. It looked as if it just refreshed.

---

### Post by coffeecat on 2011-12-20
If I'm following the sequence of events correctly, you've reinstalled Windows and then converted the dynamic partitions to basic ones. But if you re-installed Windows from the HP recovery partition or restore DVDs, it's likely that HP Recovery Manager is running again and is messing up grub every time you boot into Windows. You needed to disable HP Recovery Manager before you re-installed Windows. Make sure it is disabled now. That is the only reason I can think of for grub failing like this.

---

### Post by martin11ph on 2011-12-20
Nope. I deleted all the HP partitions. HP gave me a Home Premium OS. I installed an Ultimate instead. :confused:

Oh and you got the sequence right. I formatted hd1 and installed Ubuntu 11. Formatted hd0 and installed Windows 7 Ultimate then converted hd0 to a basic disk.

---

### Post by coffeecat on 2011-12-20
I'll pm another member to have a look and see if I've missed anything. I cannot think of a reason why grub would fail like this.

---

### Post by coffeecat on 2011-12-20
I've pm'd a forum friend to see if they can think of anything. They're offline now so I don't know when we'll get a response. In the meantime, please run the boot info script again and post the contents of the RESULTS.txt file. We ought to check that again.

---

### Post by martin11ph on 2011-12-20
Thanks a lot. Results.txt coming up in a while.

Results:
>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb5 
                       and looks at sector 17337152 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   976,769,023   976,359,424   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,046    41,015,295    41,013,250   5 Extended
/dev/sdb5               2,048    29,296,639    29,294,592  83 Linux
/dev/sdb6          29,298,688    41,015,295    11,716,608  82 Linux swap / Solaris
/dev/sdb2          41,015,296   976,769,023   935,753,728   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        88549E3E549E2F46                       ntfs       SYSTEM
/dev/sda2        646E9B876E9B50A2                       ntfs       
/dev/sdb2        F8A87A5FA87A1C76                       ntfs       Drive 2
/dev/sdb5        5147289c-127c-439f-b912-59094cf35180   ext4       
/dev/sdb6        a470a08c-1ca9-45ee-8ad5-57dda85c785d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=5147289c-127c-439f-b912-59094cf35180 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a470a08c-1ca9-45ee-8ad5-57dda85c785d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


---

### Post by Quackers on 2011-12-20
Hi there. I've been reading through the thread and it seems that much has changed since your original problem.
The boot script has some msising information.
In Your Ubuntu system (or in the live desktop) can you please install gawk via synaptic package manager and then re-run the boot script, posting the contents of the new results.txt file (it may be called Results1.txt or Results2.txt, depending on how many times you have run it).

---

### Post by oldfred on 2011-12-20
Back in post #5 you said this:
> My BIOS does not allow me to select which drive to boot. I can choose DVD/USB/HD but cannot choose which one among the HDs.Grub will not make a bootable disk out of a non-bootable drive. So what options does USB give? 

You can look at this which somehow does make a non-bootable usb drive work, if you cannot boot USB devices.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by martin11ph on 2011-12-20
Thank you for all the help. Here is the new boot info.

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb5 
                       and looks at sector 17337152 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   976,769,023   976,359,424   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,046    41,015,295    41,013,250   5 Extended
/dev/sdb5               2,048    29,296,639    29,294,592  83 Linux
/dev/sdb6          29,298,688    41,015,295    11,716,608  82 Linux swap / Solaris
/dev/sdb2          41,015,296   976,769,023   935,753,728   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        88549E3E549E2F46                       ntfs       SYSTEM
/dev/sda2        646E9B876E9B50A2                       ntfs       
/dev/sdb2        F8A87A5FA87A1C76                       ntfs       Drive 2
/dev/sdb5        5147289c-127c-439f-b912-59094cf35180   ext4       
/dev/sdb6        a470a08c-1ca9-45ee-8ad5-57dda85c785d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=5147289c-127c-439f-b912-59094cf35180 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a470a08c-1ca9-45ee-8ad5-57dda85c785d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.267024994 = 8.876650496    boot/grub/core.img                             1
   1.829101562 = 1.963982848    boot/initrd.img-3.0.0-12-generic               3
   8.248226166 = 8.856465408    boot/vmlinuz-3.0.0-12-generic                  1
   1.829101562 = 1.963982848    initrd.img                                     3
   8.248226166 = 8.856465408    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error


@oldfred, I see. However, I was still able to see Ubuntu 9.10 being displayed in the grub menu previously. I had to reformat it, however, since it ruined my wired ethernet somehow.

---

### Post by oldfred on 2011-12-20
Do you get grub rescue?
 It looks like you are missing grub.cfg but have the operating system installed.

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,5) or sdb5
sh:grub>ls (hd1,5)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,5)/vmlinuz root=/dev/sdb5
sh:grub>initrd (hd1,5)/initrd.img
sh:grub>boot

---

### Post by martin11ph on 2011-12-21
Sorry. I am a beginner when it comes to Linux and have no idea what you said. Do I enter those at the terminal or at the grub console?

---

### Post by oldfred on 2011-12-21
If you can get to terminal you have booted. 

Those commands are if you cannot boot and get either grub rescue or grub> command lines.

Sometimes this will boot a system that has grub issues, then you can repair grub after you have booted:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by martin11ph on 2011-12-21
I see. Currently, I am shown the grub command line every time I turn on the laptop. I will try the commands you posted and post the results in a while. Thank you.

Wow. That series of commands entered on the grub console booted me to Ubuntu. :)

I'll be reading the links you gave me tomorrow. Hopefully, the grub console will be back to a grub menu when done. Thank you.

Edit:
A little of topic: The sidebar has the button "Install RELEASE" which confuses me. I've already installed Ubuntu. Why does this appear?

---

### Post by oldfred on 2011-12-21
At the very least you need to run this:

sudo update-grub

That should write a grub.cfg which then will let you boot. If not you may have to use the manual commands again. Then you may just have to totally uninstall grub2 and reinstall, but lets worry about that later and only if you have to manually boot again.

I am not sure what you are seeing about install release. I have only used Unity a bit as I convert back to fallback on the new verisons, so the gui is more like my main install which still is Maverick 10.10 (gnome2). The system usually wants to do updates, but unless you install an older version it does not normally want to suggest upgrade which is to the next verison. Since you have 11.10 you should not get an upgrade suggestion until next April to 12.04.

You can do an install of grub to sdb and see if your BIOS lets you boot sdb. This will not change the MBR of sda. If it works then you should reinstall the Windows boot loader to sda.

sudo grub-install /dev/sdb

---

### Post by Quackers on 2011-12-21
If you are getting a "install release" icon it would seem to me that you are booted into a live system rather than your installed system.

---

### Post by martin11ph on 2011-12-21
> **oldfred said:**
> At the very least you need to run this:

sudo update-grub

That should write a grub.cfg which then will let you boot. If not you may have to use the manual commands again. Then you may just have to totally uninstall grub2 and reinstall, but lets worry about that later and only if you have to manually boot again.



This fixed everything right away. After upgrading grub, I no longer see the console. I now see the menu and can choose between Windows and Ubuntu. :P


> **Quackers said:**
> If you are getting a "install release" icon it  would seem to me that you are booted into a live system rather than your  installed system.

I wondered that myself. I think it may just be a glitch. I did not have a live CD in the drive and my installed system had a user account which it did ask me to authenticate. Also, I checked the free space and it told me there is >11GB available which should be right as I allocated 15GB ext4 for my Ubuntu. :) I removed the icon from the dock anyway.

---

### Post by oldfred on 2011-12-21
Progress.:)

Have you tried to install to sdb and booting from that?

---

### Post by martin11ph on 2011-12-22
> **oldfred said:**
> 

You can do an install of grub to sdb and see if your BIOS lets you boot  sdb. This will not change the MBR of sda. If it works then you should  reinstall the Windows boot loader to sda.

sudo grub-install /dev/sdb



To install grub to sdb, all I need is the script shared by coffeecat? Its good that you reassured me it will not affect the sda MBR but why would I need to reinstall the Windows boot loader? Basically, this will be the result:

sda = Windows boot loader
sdb = grub
and then I see if the bios allows me to boot from sdb.

Did I get it right? I will try what you suggest in a while. :)

---

### Post by Quackers on 2011-12-22
I'm glad that things seem to be good now :-)

I believe Oldfred is suggesting the above so that the two systems can be separated completely. Then if one fails the other is still bootable (via bios), rather than relying on grub to boot both.
However, I believe you stated earlier that your bios does not allow booting from sdb, so it's possibly best left as it is.

---

### Post by coffeecat on 2011-12-22
> **martin11ph said:**
> Basically, this will be the result:

sda = Windows boot loader
sdb = grub
and then I see if the bios allows me to boot from sdb.

Just to remind you, this is what you said near the beginning of the thread:

> **martin11ph said:**
> 
My BIOS does not allow me to select which drive to boot. I can choose DVD/USB/HD but cannot choose which one among the HDs.

If memory serves correct, you have a laptop with two 500GB drives, sda and sdb, but the BIOS only lets you boot from sda, the optical drive or an external device.

At one point you were able to use grub installed to sda to boot both Windows on sda and Ubuntu on sdb, but then HP Recovery Manager started to break grub and a number of other issues intervened. The latest - if I'm reading things correctly, is that when you re-installed Ubuntu, for some reason a grub.cfg file did not get written to /boot/grub in sdb5. Hence the grub prompt. A properly written grub.cfg (with update-grub) in sdb5, grub in the mbr of sda, and no interfering HP Recovery Manager *should* set you up with a dual-booting system. And, as far as I can make out from your recent post, it did. If it works, leave it. :)

---

### Post by martin11ph on 2011-12-22
Oh okay. I was under the impression that the BIOS might suddenly allow me to boot sdb given the recent changes. Thanks for clarifying it.

Thank you to the three of you and especially coffeecat for guiding me and calling the cavalry later on. :P

---

### Post by Quackers on 2011-12-22
It won't do any harm to check in your bios to see if sdb is now a bootable option.
I too have a twin drive laptop where only sda is bootable in the bios, but that's because my laptop came with bios raid set as default. In those circumstances I can see why Sony (in their infinite wisdom) never foresaw the need to boot from sdb.

---

### Post by martin11ph on 2011-12-23
That's true. It won't hurt so I checked. My HP laptop still does not allow it. :(

---

