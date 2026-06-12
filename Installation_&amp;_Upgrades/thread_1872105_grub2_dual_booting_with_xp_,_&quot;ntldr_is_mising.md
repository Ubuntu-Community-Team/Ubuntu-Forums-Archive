---
title: "grub2 dual booting with xp , &quot;ntldr is mising&quot;"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by zhulianhua on 2011-10-30
Hi, I have a trouble to dual boot ubuntu and Xp
This is what I've done  by time line

installed Xp sp3 on **sda2**, OK

installed Ubuntu 11.10 64-bit on sda1 ,no boot partition . In the installation process , installed grub on sda (MBR), Which is the default option.

But after installation and reboot , there no "windows " entry in the grub2 booting options.

Then I added thehe lines to my **/boot/grub/grub.cfg**, 
```

### BEGIN /etc/grub.d/30_otheros ###

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
menuentry "Windows XP (loader)" {
insmod ntfs
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/30_otheros ###
```Then reboot and choose to boot "Windows XP (loader)" ,but get a message "NTLDR is 
missing" on a black screen .

Then I copy a file "/i386/NTLRD" from XP intallation CD to my sda2(Xp system). 
reboot and get a error two line message 
"NTLDR is missing"
I don't know the 2nd line ,for it splash quickly, and reboot automatically.

I have googled long time ....:confused:

---

### Post by zhulianhua on 2011-10-30
This is my boot-info
                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ntldr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 3162128 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdb2: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  ISOhybrid (Syslinux 3.82-4.04)
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    24,579,449    24,579,387  83 Linux
/dev/sda2          24,579,450   102,767,804    78,188,355   7 NTFS / exFAT / HPFS
/dev/sda3         102,770,686   488,396,799   385,626,114   f W95 Extended (LBA)
/dev/sda5         102,770,688   375,390,207   272,619,520  83 Linux
/dev/sda6         375,392,256   438,300,671    62,908,416  83 Linux
/dev/sda7         438,302,720   479,315,967    41,013,248  83 Linux
/dev/sda8         479,318,016   488,396,799     9,078,784  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     8,390,655     8,388,608  83 Linux
/dev/sdb2           8,390,656    15,646,719     7,256,064  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        92b772a1-76e0-4e7b-98f6-552dab49f1d2   ext4       
/dev/sda2        AE749BD6749BA01F                       ntfs       System
/dev/sda5        5ad18585-e751-41e9-a073-bde0771c6e9a   ext4       
/dev/sda6        e4d4242d-1e97-4ac8-9453-3386a2667bac   ext4       
/dev/sda7        10d12f3f-a886-46ab-ad8b-f1fa72a40a72   ext4       
/dev/sda8        992b15c4-0c24-40db-a6e0-8c61df494b00   swap       
/dev/sdb1        0C32-26E2                              vfat       PENDRIVE
/dev/sdb2                                               iso9660    Ubuntu 11.10 i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sda6        /opt                     ext4       (rw,commit=0)
/dev/sda7        /usr                     ext4       (rw,commit=0)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdb2        /media/Ubuntu 11.10 i386 iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 10d12f3f-a886-46ab-ad8b-f1fa72a40a72
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 92b772a1-76e0-4e7b-98f6-552dab49f1d2
  set locale_dir=($root)/boot/grub/locale
  set lang=zh_CN
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu&#65292;Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 92b772a1-76e0-4e7b-98f6-552dab49f1d2
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=92b772a1-76e0-4e7b-98f6-552dab49f1d2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu&#65292;Linux 3.0.0-12-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 92b772a1-76e0-4e7b-98f6-552dab49f1d2
    echo    '&#36733;&#20837; Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=92b772a1-76e0-4e7b-98f6-552dab49f1d2 ro recovery nomodeset 
    echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 92b772a1-76e0-4e7b-98f6-552dab49f1d2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 92b772a1-76e0-4e7b-98f6-552dab49f1d2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_otheros ###

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
menuentry "Windows XP (loader)" {
insmod ntfs
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/30_otheros ###
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=92b772a1-76e0-4e7b-98f6-552dab49f1d2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=5ad18585-e751-41e9-a073-bde0771c6e9a /home           ext4    defaults        0       2
# /opt was on /dev/sda6 during installation
UUID=e4d4242d-1e97-4ac8-9453-3386a2667bac /opt            ext4    defaults        0       2
# /usr was on /dev/sda7 during installation
UUID=10d12f3f-a886-46ab-ad8b-f1fa72a40a72 /usr            ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=992b15c4-0c24-40db-a6e0-8c61df494b00 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

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
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  42 27 9f 6b 14 08 39 0a  dc a3 1d 49 c5 75 de 75  |B'.k..9....I.u.u|
00000010  37 70 8f 05 8c 73 0c 07  67 3b 13 b4 d1 f8 96 74  |7p...s..g;.....t|
00000020  36 f9 ea e2 6a eb 6c 38  c1 31 05 84 4c 6a 2d d1  |6...j.l8.1..Lj-.|
00000030  64 9f 2d 2c 65 a2 43 6c  ad b5 a9 de de 0a c6 dd  |d.-,e.Cl........|
00000040  69 8e e9 cf f4 8a d3 2d  32 33 5a fc 2f fa 5a 6f  |i......-23Z./.Zo|
00000050  b6 cf 35 0b 1c 67 fa 6c  0f 40 4b 55 3d 31 4b cc  |..5..g.l.@KU=1K.|
00000060  71 cc fd c9 de 35 cf 17  3a 1f 1c 17 f8 6c 0b 9f  |q....5..:....l..|
00000070  91 e6 7f 70 05 bf e8 9f  f6 d6 c5 8e c3 2d bd 6c  |...p.........-.l|
00000080  89 23 16 d4 d4 32 c7 83  d6 f3 13 5b e6 d6 2c 50  |.#...2.....[..,P|
00000090  57 7b 63 32 63 c3 81 d6  34 45 4d 03 ba 30 e5 1f  |W{c2c...4EM..0..|
000000a0  df ae f4 95 7e b9 23 2a  76 70 72 5a aa d2 32 02  |....~.#*vprZ..2.|
000000b0  9d 48 dd 08 62 ac 78 2a  ef 55 3e d7 ca 67 ca 33  |.H..b.x*.U>..g.3|
000000c0  3d ee 7c c4 63 b3 e5 3e  bf 2f c7 d5 8e fb 09 6b  |=.|.c..>./.....k|
000000d0  80 e4 f8 64 25 6a cd 0f  ce e0 40 eb 38 b7 ce f1  |...d%j....@.8...|
000000e0  28 e2 6a 44 ef 94 b5 ad  32 73 3a 9f 04 39 af 77  |(.jD....2s:..9.w|
000000f0  a4 81 1e b2 34 75 a9 2f  b5 79 4f dd 15 db 00 64  |....4u./.yO....d|
00000100  2f b5 e4 b6 f1 1f 6d ef  d8 ec d8 02 ec db 1c 5b  |/.....m........[|
00000110  ff c5 d1 ed 34 28 f5 f6  56 d9 1d c0 b6 b3 d5 b5  |....4(..V.......|
00000120  eb 47 d3 d8 e3 d8 0d c2  f6 fe cb 23 68 65 e7 7d  |.G.........#he.}|
00000130  3e d9 39 be 33 d8 f4 d4  3a e4 00 08 39 04 d8 ef  |>.9.3...:...9...|
00000140  58 97 35 d3 17 3e 1c f4  da b0 67 d6 a5 35 51 91  |X.5..>....g..5Q.|
00000150  b1 69 ad bd fe 08 90 5f  dc b2 4e 58 90 22 7b bf  |.i....._..NX."{.|
00000160  fd d7 e2 9a ee bd f7 ef  88 4e 3d de 52 b6 13 ad  |.........N=.R...|
00000170  65 3c ea 38 03 ec e7 1c  a7 7d 3e 67 7d c7 93 8e  |e<.8.....}>g}...|
00000180  82 96 f1 f6 3c 70 5f f8  c9 f3 b9 e8 b8 d4 12 7e  |....<p_........~|
00000190  d9 67 5e 6d 71 5d 01 e6  75 c7 cd 16 d7 35 c7 0d  |.g^mq]..u....5..|
000001a0  c7 19 5f d9 6f 79 eb f2  27 f7 65 2c 8a bc ed b8  |.._.oy..'.e,....|
000001b0  e3 58 d8 da aa 77 9f ca  ff 9e cf 55 de 32 00 fe  |.X...w.....U.2..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 3f 10 00 fe  |............?...|
000001d0  ff ff 05 fe ff ff 89 da  3f 10 79 ed bf 03 00 00  |........?.y.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
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

### Post by Script Warlock on 2011-10-30
o sorted a couple of dual boot of windows and linux machines with an error of ntldr is missing... one instance i made is changed the ide cable and plugged to another computer with ide port and fired a live cd/usb ubuntu and opening the windows partition. thats all i did and placed back the hard drive to that machine and boot and taddah. can't explain well how it recovered but thats how i sorted some machines. well of course recovering the ntldr from the windows cd is the best solution of course.

---

### Post by zhulianhua on 2011-10-30
> **Script Warlock said:**
> o sorted a couple of dual boot of windows and linux machines with an error of ntldr is missing... one instance i made is changed the ide cable and plugged to another computer with ide port and fired a live cd/usb ubuntu and opening the windows partition. thats all i did and placed back the hard drive to that machine and boot and taddah. can't explain well how it recovered but thats how i sorted some machines. well of course recovering the ntldr from the windows cd is the best solution of course.
My machines is a laptop ...

“Ntldr is compressed”


```

sudo dd if=/dev/sda2 | hexdump -C 

......
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200  05 00 4e 00 54 00 4c 00  44 00 52 00 04 00 24 00  |..N.T.L.D.R...$.|
00000210  49 00 33 00 30 00 00 e0  00 00 00 30 00 00 00 00  |I.3.0......0....|
00000220  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
.......

```

---

### Post by oldfred on 2011-10-30
Please use code tags in long data or code posts like boot script. You can use the # in the edit menu. Highlight what you want code tags around and click on # or click on # and paste between the tags. 

Boot script does show ntldr, but a full XP install should have 3 boot files shown by the script.
WinXP
/boot.ini /ntldr /NTDETECT.COM

Windows XP will only repair a NTFS partition with the boot flag. Grub does not use boot flag, so use gparted and move boot flag back to sda2. Then you may be able to use your XP disk to repair your install.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

While discussing logical partition which is not recommended by Windows it has info on some of the files.
How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

---

### Post by zhulianhua on 2011-10-31
Thank you mach oldfred,  I solved it !
After I copyed the "ntdectect.com" to WinXP '/' , and changed the  ```
set root='(hd0,sda2)'
```to```
set root='(hd0,msdos2)'
``` in my XP grub entry, Because my other OS entries in the grub.cfg use 'msdos', other then 'sda2'. I don't know why.
I also made a 'boot.ini' file in Xp root directory as 
```

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP" /fastdetect


```But this file seems useless , because in the ntldr menus the title is "Microsoft Windows XP Professional" and have a second entry .

> **oldfred said:**
> Please use code tags in long data or code posts like boot script. You can use the # in the edit menu. Highlight what you want code tags around and click on # or click on # and paste between the tags. 

Boot script does show ntldr, but a full XP install should have 3 boot files shown by the script.
WinXP
/boot.ini /ntldr /NTDETECT.COM

Windows XP will only repair a NTFS partition with the boot flag. Grub does not use boot flag, so use gparted and move boot flag back to sda2. Then you may be able to use your XP disk to repair your install.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

While discussing logical partition which is not recommended by Windows it has info on some of the files.
How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

---

### Post by oldfred on 2011-10-31
Glad it worked.

It think to boot.ini should have the default also be the first drive & second partition. I you had another install before it would have had two entries.
rdisk(0)partition(2)

---

