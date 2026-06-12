---
title: "win xp loader missing after ubuntu 10.10 install"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by animae on 2011-01-11
Hello all!

I ve checked various thread in here, but none answered to my questions, so
this is my case:

I ve installed windows xp on my desktop and now i installed ubuntu 10.10.(2 different hard disks)

After installing ubuntu, it boots only to ubuntu, without giving me the choice of which OS to boot. To cut a long story short, i only boot to ubuntu, there is no windows choice. 

This happened(i suppose) because the grub is installed on a different disk than the xp is.  

Is there a way to modify the grub loader to see xp without the need of windows xp cd? 



In this thread [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1620022]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1620022") they found useful to run this script [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/") and paste the results here, so here are my result.txt:

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   490,207,409   285,410,790   f W95 Ext d (LBA)
/dev/sda5         204,796,683   490,207,409   285,410,727   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,065   625,137,344   625,121,280   5 Extended
/dev/sdb5              16,128   293,620,004   293,603,877   7 HPFS/NTFS
/dev/sdb6         293,620,068   419,457,149   125,837,082   7 HPFS/NTFS
/dev/sdb7         419,457,213   625,137,344   205,680,132   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   117,263,734   117,263,672  83 Linux
/dev/sdc2         117,264,382   119,216,127     1,951,746   5 Extended
/dev/sdc5         117,264,384   119,216,127     1,951,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56A8A9AEA8A98D55                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        488494CC8494BDBE                       ntfs       Warehouse                     
/dev/sda                                                isw_raid_member                               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        34506867F896A7EB                       ntfs       &#924;&#959;&#965;&#963;&#953;&#954;&#942;                
/dev/sdb6        99088A1B98E79907                       ntfs       WILI                          
/dev/sdb7        9D71A0CED8605368                       ntfs       &#913;&#960;&#959;&#952;&#942;&#954;&#951;                
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        062d8005-5fb2-4b44-a582-71b7c0c35cee   reiserfs                                 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        9cd41b62-3548-439f-bf7c-830b20ae8b66   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        reiserfs   (rw,notail)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
insmod reiserfs
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 062d8005-5fb2-4b44-a582-71b7c0c35cee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod reiserfs
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 062d8005-5fb2-4b44-a582-71b7c0c35cee
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod reiserfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 062d8005-5fb2-4b44-a582-71b7c0c35cee
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=062d8005-5fb2-4b44-a582-71b7c0c35cee ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod reiserfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 062d8005-5fb2-4b44-a582-71b7c0c35cee
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=062d8005-5fb2-4b44-a582-71b7c0c35cee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod reiserfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 062d8005-5fb2-4b44-a582-71b7c0c35cee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod reiserfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 062d8005-5fb2-4b44-a582-71b7c0c35cee
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=062d8005-5fb2-4b44-a582-71b7c0c35cee /               reiserfs notail          0       1
# swap was on /dev/sdc5 during installation
UUID=9cd41b62-3548-439f-bf7c-830b20ae8b66 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/initrd.img-2.6.35-24-generic-pae
    ??GB: boot/vmlinuz-2.6.35-24-generic-pae
    ??GB: initrd.img
    ??GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  55 85 dd c4 7e 15 9d 3a  03 ec 8c da 1e c7 e6 87  |U...~..:........|
00000010  5e 0f d5 85 0b 25 b3 36  22 0a 3b 9a 48 9b ac 79  |^....%.6".;.H..y|
00000020  d8 a3 dd 52 42 7b 2d 52  b9 f9 bd 65 b4 8c d3 9e  |...RB{-R...e....|
00000030  16 5a e3 f7 01 84 eb af  86 2d 78 69 c2 d2 be cf  |.Z.......-xi....|
00000040  cd 3a bd 33 57 63 2e 1a  02 a1 f4 0d 36 c4 b7 9d  |.:.3Wc......6...|
00000050  fc 61 42 77 5b c6 b5 7f  0f 45 4d 56 68 09 d8 2c  |.aBw[....EMVh..,|
00000060  d3 ca 4a 91 1e 89 11 83  e5 25 f2 24 64 33 9f 4f  |..J......%.$d3.O|
00000070  ac 2d ec f5 6d f3 8c 62  47 3c 7c 8b e8 27 63 3e  |.-..m..bG<|..'c>|
00000080  32 9a b7 80 da 2b 08 ef  f3 ad 83 44 98 c1 0d 21  |2....+.....D...!|
00000090  f7 08 c0 36 4d ed 60 35  34 46 3f 46 10 c1 04 76  |...6M.`54F?F...v|
000000a0  9b b2 94 4d e8 f1 9c cf  54 b4 f5 62 84 6f e9 42  |...M....T..b.o.B|
000000b0  89 17 be eb 9a 65 ad 46  27 e3 c3 81 10 69 9f e3  |.....e.F'....i..|
000000c0  f5 35 64 25 cf 06 8b d9  47 69 55 3a b8 3b db e1  |.5d%....GiU:.;..|
000000d0  42 8a 6e 22 ee 83 b3 8d  6f 4b fe 6c 43 8f ea 2d  |B.n"....oK.lC..-|
000000e0  84 73 79 f8 eb 35 80 0a  f8 bb e2 c3 d0 cd 51 22  |.sy..5........Q"|
000000f0  c7 5e 7e ea e5 58 68 a8  f7 8e 54 03 80 d3 fd 16  |.^~..Xh...T.....|
00000100  1a f1 f8 5c fc 6c 38 7d  46 98 62 62 63 53 63 bf  |...\.l8}F.bbcSc.|
00000110  4b 8e 36 0c c0 46 62 11  a0 bc 5f 06 b8 0a 76 a3  |K.6..Fb..._...v.|
00000120  5f a2 7d 16 df ee 2e 63  21 ff d7 2b 7d 8a 01 49  |_.}....c!..+}..I|
00000130  bb f8 b4 7b 72 80 ca ac  77 ad d4 78 a1 0d de 95  |...{r...w..x....|
00000140  a6 d0 18 b2 e4 51 fc 6a  ff a5 01 01 35 5d 6c 08  |.....Q.j....5]l.|
00000150  7b 6a 63 1e 54 fa 2f 0c  92 56 27 c4 9b 20 46 14  |{jc.T./..V'.. F.|
00000160  25 98 65 4f a5 95 73 7f  3a f0 73 f6 e9 e0 49 20  |%.eO..s.:.s...I |
00000170  d6 c2 77 47 13 66 11 f3  ea 8c b3 aa 21 7e 80 a1  |..wG.f......!~..|
00000180  de c5 20 d6 ca e1 6b 63  98 1b d7 46 c2 38 5b 56  |.. ...kc...F.8[V|
00000190  85 6e 4a 83 41 96 98 ac  b1 0c e3 02 13 3d 60 41  |.nJ.A........=`A|
000001a0  cf 7c 90 32 ca 8a de ec  a1 93 fb c9 dd 1a fb c8  |.|.2............|
000001b0  2d 86 14 db 69 e3 19 6a  eb 36 13 96 14 4f 00 01  |-...i..j.6...O..|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 a7 05 03 11 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  54 55 ae 3f 52 09 7c c5  b9 6b 25 7e 65 30 24 49  |TU.?R.|..k%~e0$I|
00000010  c3 45 66 e0 92 92 06 d1  24 99 3a 76 a4 4b be eb  |.Ef.....$.:v.K..|
00000020  a6 f2 de 8b 2e e5 6f 61  6d 79 0e ed c5 52 8c a5  |......oamy...R..|
00000030  03 5a 1a 7d 4a 1c c4 9c  41 09 0f 20 a8 5a 20 93  |.Z.}J...A.. .Z .|
00000040  a8 ec 79 c0 7e 8e 2f bb  44 46 dc 47 54 d4 39 9c  |..y.~./.DF.GT.9.|
00000050  a3 7d 3c 89 88 16 86 dc  ca ca af 87 a7 39 a1 48  |.}<..........9.H|
00000060  cb e6 f3 44 70 83 1a 1c  38 cd 8a 4c 3f 79 79 fc  |...Dp...8..L?yy.|
00000070  69 5b b7 48 f4 7f f2 cb  0e b0 2c fe 3a b5 38 cb  |i[.H......,.:.8.|
00000080  6a ae f1 f6 e3 65 79 f5  13 2e ad 07 1e 0d af 16  |j....ey.........|
00000090  b1 30 f6 78 be 04 97 87  b8 5a dc 3c 32 b5 c9 2c  |.0.x.....Z.<2..,|
000000a0  38 3e 94 a5 64 71 89 03  78 bf 85 3c 8e 38 9b 7a  |8>..dq..x..<.8.z|
000000b0  92 2f cd b3 08 29 a7 ae  61 b6 89 49 38 db 69 a6  |./...)..a..I8.i.|
000000c0  ea 18 1a 95 20 35 02 10  c3 4a 01 23 d0 fd 87 41  |.... 5...J.#...A|
000000d0  57 25 91 d9 42 d8 81 65  51 ca 49 6c 42 02 a5 50  |W%..B..eQ.IlB..P|
000000e0  32 25 2d 14 12 20 f9 78  54 d5 2e 41 c7 67 4b 00  |2%-.. .xT..A.gK.|
000000f0  af 01 a7 71 d3 95 a9 46  12 dd 25 54 d9 47 d0 9c  |...q...F..%T.G..|
00000100  d5 5f 0b 90 33 4f 4e e0  00 14 da 30 c0 07 26 41  |._..3ON....0..&A|
00000110  c3 85 16 8b 1a e4 b5 15  73 f1 61 9e c7 0a b4 da  |........s.a.....|
00000120  7a cc af 83 56 e9 24 89  15 a9 81 c9 83 d5 1a 8e  |z...V.$.........|
00000130  78 aa 99 c7 2b b3 d1 75  79 28 e5 3a 44 be b0 e9  |x...+..uy(.:D...|
00000140  95 8e ad 4f 97 70 10 88  17 91 c2 90 d4 f3 9c 8a  |...O.p..........|
00000150  6d 37 27 19 90 95 d6 3c  38 bb 95 dd 52 ef 59 2b  |m7'....<8...R.Y+|
00000160  15 eb 2b fb ed a5 96 13  a8 d0 a6 ae 21 4d 68 17  |..+.........!Mh.|
00000170  a4 58 32 2e a1 44 de 1b  1f 2e 27 a1 fa cd 78 2d  |.X2..D....'...x-|
00000180  ef 63 c2 60 86 f9 8c f2  a4 aa 88 92 2e ea cd 2a  |.c.`...........*|
00000190  d4 1e 9c 99 9e 3b d5 f8  51 7e 96 ab 49 b4 92 50  |.....;..Q~..I..P|
000001a0  50 31 c1 3e 0c aa 8a 8b  b4 0a 34 0c 55 10 98 64  |P1.>......4.U..d|
000001b0  86 bb 63 6c 02 a2 21 98  5c a1 e3 c2 0f 40 00 fe  |..cl..!.\....@..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

ERROR: isw: wrong number of devices in RAID set "isw_dbajfgeebg_WDRaid" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dbajfgeebg_WDRaid" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dbajfgeebg_WDRaid" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dbajfgeebg_WDRaid" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dbajfgeebg_WDRaid" [1/2] on /dev/sda
```

---

### Post by lethal666 on 2011-01-11
When you boot up ubuntu and look at your computer do you see your other hard drive with xp? Have you tried putting the windows xp cd back in?

---

### Post by drs305 on 2011-01-11
Have you tried running "sudo update-grub" from Ubuntu. Sometimes that is necessary to get Grub2 to recognize the Windows installs.

---

### Post by lethal666 on 2011-01-11
When you boot up ubuntu and look at your computer do you see your other hard drive with xp? Have you tried putting the windows xp cd back in?

---

### Post by Rubi1200 on 2011-01-11
Which disk is set as first boot priority?

Have you run these commands in Ubuntu to try and pick up the Windows install?

```
sudo update-grub
```

```
sudo os-prober
```

---

### Post by animae on 2011-01-11
> **lethal666 said:**
> When you boot up ubuntu and look at your computer do you see your other hard drive with xp? Have you tried putting the windows xp cd back in?

Yes, i can see the partition which has xp installed on.
Havent tried this one yet, cause i dont have the original xp cd.
I will try it, if nothing else comes out, with a copy of the same edition of xp, but has another serial (both original cds).

> **drs305 said:**
> Have you tried running "sudo update-grub" from Ubuntu. Sometimes that is necessary to get Grub2 to recognize the Windows installs.

I did it right now, after posting this, i ll restart.

Thank you for your answers :D

---

### Post by animae on 2011-01-11
unfortunately, nothing happened with *sudo update-grub*, still boots directly on ubuntu.

The command ```
sudo os-prober
``` gives this

```
ERROR: isw: wrong number of devices in RAID set "isw_dbajfgeebg_WDRaid" [1/2] on /dev/sda

```

Just to inform you, that am a noob in ubuntu world.


edit:
I changed, the boot device, but i wouldnt boot. 
The problem is, that i dont remember which is the exact partition that i ve installed ubuntu. In any case, the 250gb hard drive is the one that i can boot. I as can recall, this drive, has 2 partitions and in one of them i ve installed xp. 
In the 160gb drive i installed ubuntu (tried to make it first boot device, but it wouldnt boot).
If you understand something else(rather than the setup that i am describing now) from the result.txt that i ve posted earlier,be my guest to correct me :)

---

### Post by Quackers on 2011-01-11
Are you using a raid setup? Or has this hard drive ever been used with a raid setup?

---

### Post by animae on 2011-01-11
> **Quackers said:**
> Are you using a raid setup? Or has this hard drive ever been used with a raid setup?

I ve bought this disk (the 250gb one) from a friend of mine, who had 2 of these and i m almost sure he used these as raid.
Now, its an everyday disk :P

---

### Post by drs305 on 2011-01-11
Try to clear the RAID remants with this command:
```
sudo dmraid -E -r /dev/sda
```

If you can clear RAID from Grub's consciousness things may run correctly.

---

### Post by Quackers on 2011-01-11
First I would run this in the terminal
```
 sudo dmraid -rE /dev/sda
```
This will remove any raid metadata left from the disk's previous use. Please report any output from that command.

---

### Post by Guidobot on 2011-01-11
I have the same issue but on an origninal XP on a AMD Athlon 64 PC.
 
Not sure if the thread is resolved here: what is GRUB?
 
Should I try creating a boot CD? (Unfortunately I have to do this using a different PC.)

---

### Post by Quackers on 2011-01-11
Grub is the bootloader used by Ubuntu.

---

### Post by Guidobot on 2011-01-11
So is GRUB the boot program that I can't get to when I restart, i.e. if I could select to boot Ubuntu?
 
Is this something that needs to be configured from Windows (XP) to enable the boot option or ... ?

---

### Post by animae on 2011-01-11
> **Quackers said:**
> First I would run this in the terminal
```
 sudo dmraid -rE /dev/sda
```
This will remove any raid metadata left from the disk's previous use. Please report any output from that command.

This was the output:

```
Do you really want to erase "isw" ondisk metadata on /dev/sda ? [y/n] :y

```

and then, the usual command prompt.

Rebooting now.

---

### Post by Quackers on 2011-01-11
> **Guidobot said:**
> So is GRUB the boot program that I can't get to when I restart, i.e. if I could select to boot Ubuntu?
 
Is this something that needs to be configured from Windows (XP) to enable the boot option or ... ?

It might be better if you start your own thread, giving full details of what has happened.

---

### Post by animae on 2011-01-11
> **drs305 said:**
> Try to clear the RAID remants with this command:
```
sudo dmraid -E -r /dev/sda
```

If you can clear RAID from Grub's consciousness things may run correctly.

> **Quackers said:**
> First I would run this in the terminal
```
 sudo dmraid -rE /dev/sda
```
This will remove any raid metadata left from the disk's previous use. Please report any output from that command.


I ve used the second command(Quackers') and then i updated again grub and everything is back to normal!

A huge "thank you", to all the people in this thread:D
Thanx so much!

---

### Post by Quackers on 2011-01-11
Excellent, well done :-)

---

