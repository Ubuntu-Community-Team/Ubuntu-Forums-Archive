---
title: "Natty destroyed grub..."
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by WG- on 2011-05-02
Well yesterday I had some troubles installing gnome3. In the end it destroyed ubuntu, it couldn't even start the rescue prompt anymore. The GRUB still worked fine, I could still choose to start either ubuntu, memtest or windows 7

Now today I did a complete reinstall of ubuntu over the one that broke. The install went fine but after the restart, grub rescue is started. I can not select ubuntu, windows7 or memtest anymore. Now I tried to fix my GRUB and did some reading but no success. So I'm asking for your help.

Here is the output I have from "boot_info_script" which I saw was used a couple of times. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   247,269,375   244,195,328   7 HPFS/NTFS
/dev/sda3         247,269,376   329,189,375    81,920,000   7 HPFS/NTFS
/dev/sda4         329,191,422   488,396,799   159,205,378   5 Extended
/dev/sda5         481,824,768   488,396,799     6,572,032  82 Linux swap / Solaris
/dev/sda6         329,191,424   475,940,863   146,749,440  83 Linux
/dev/sda7         475,942,912   481,820,671     5,877,760  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BE8A7D6B8A7D20D7                       ntfs       WinRE                         
/dev/sda2        F690B82590B7EA6F                       ntfs                                     
/dev/sda3        52D4BE87D4BE6CBB                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        23db0dfe-fcd9-4c2e-8d80-401cab0441d8   swap                                     
/dev/sda6        15df8d5f-772d-42b0-809c-f1f04d5d1af8   ext4                                     
/dev/sda7        2370c014-5dec-49ff-8c07-8c774a1df9e5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12FD-3B41                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
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
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=15df8d5f-772d-42b0-809c-f1f04d5d1af8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=15df8d5f-772d-42b0-809c-f1f04d5d1af8 ro single 
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
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root F690B82590B7EA6F
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2370c014-5dec-49ff-8c07-8c774a1df9e5 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 172.9GB: boot/grub/core.img
 218.0GB: boot/grub/grub.cfg
 169.6GB: boot/initrd.img-2.6.38-8-generic
 172.9GB: boot/vmlinuz-2.6.38-8-generic
 169.6GB: initrd.img
 172.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  93 74 d7 e1 ca 7d 3f e4  15 a1 ae c3 ef 02 8a 69  |.t...}?........i|
00000010  19 a1 7e f5 23 43 67 be  96 e6 15 15 be b8 f8 53  |..~.#Cg........S|
00000020  fe 92 8e 05 0f fd 61 7b  88 4c dd 3c f7 27 3f ed  |......a{.L.<.'?.|
00000030  6b 6a 46 0f dd 24 f9 25  3c 9f 5e e2 70 cc 0a 79  |kjF..$.%<.^.p..y|
00000040  7f 8f 20 a7 03 30 cc 33  28 e5 ff 7a 4d ef 7a 7b  |.. ..0.3(..zM.z{|
00000050  ff 6f 8f 06 6f 4f 7d 8f  7f 08 85 f4 f8 53 fe 76  |.o..oO}......S.v|
00000060  d8 f7 ff 4e b9 e9 ff 18  d6 89 69 ba bb d2 fd 27  |...N......i....'|
00000070  a4 c7 d3 ce d3 47 a9 d0  a4 d5 d7 86 75 ce 78 8f  |.....G......u.x.|
00000080  a7 be 68 33 a7 1c 9e 19  fd e7 fe 6d 3d e7 c0 2c  |..h3.......m=..,|
00000090  02 c2 8b 0c c3 30 0b 73  c6 78 66 ff 98 7b c6 7f  |.....0.s.xf..{..|
000000a0  e3 80 2e c3 60 17 4f 8c  fa 78 33 2f 31 4c 53 a8  |....`.O..x3/1LS.|
000000b0  f0 ce 93 06 69 3a e7 bd  3d e1 98 66 6c 43 eb ce  |....i:..=..flC..|
000000c0  b8 d8 b3 bc 14 9f 94 d9  a7 3c 77 9d 7a 7d 60 fe  |.........<w.z}`.|
000000d0  11 b2 49 4e 25 27 c2 07  bd 29 e1 98 fa 40 33 3d  |..IN%'...)...@3=|
000000e0  34 68 e7 c0 20 f8 ca 7f  9a 58 f5 a7 1e 23 9d c2  |4h.. ....X...#..|
000000f0  75 74 d3 ee 9c a7 c7 25  b9 c3 e7 5e 05 23 2a 95  |ut.....%...^.#*.|
00000100  d6 db 20 c5 62 5c 1f 0f  c4 82 f5 4a a8 21 f4 0f  |.. .b\.....J.!..|
00000110  a9 df d5 6a 6c db 24 e4  85 dc 55 09 22 c4 e3 42  |...jl.$...U."..B|
00000120  31 1d 6b 12 35 85 8d 4a  42 ac f7 53 66 cd 45 a6  |1.k.5..JB..Sf.E.|
00000130  98 1a 9f 19 e3 37 d3 a3  37 88 98 b3 84 a1 98 66  |.....7..7......f|
00000140  9f 4f 51 80 67 f3 49 ff  7b e8 ce 9e 5f 38 01 63  |.OQ.g.I.{..._8.c|
00000150  0f ba e7 bc 63 df 49 3a  e7 85 3f fe 23 00 bd 9a  |....c.I:..?.#...|
00000160  68 88 e1 d1 9e 19 be 9e  fd 3c 74 10 f2 36 b0 cd  |h........<t..6..|
00000170  f4 a0 d7 db 30 5a 2e 4c  8e 9b 7a e4 c3 51 90 af  |....0Z.L..z..Q..|
00000180  e9 f2 77 85 0c af ab 9c  73 c0 a9 bf be f4 c9 b7  |..w.....s.......|
00000190  88 fb a6 3e d1 d0 cf ef  72 4e 9b 06 78 05 8c f7  |...>....rN..x...|
000001a0  d3 ff 3b f3 cf 18 f7 d3  3f 3c f4 5a b3 07 e9 f4  |..;.....?<.Z....|
000001b0  f0 0b 78 66 19 8c fa 77  e4 20 16 f7 a4 ff 00 fe  |..xf...w. ......|
000001c0  ff ff 82 fe ff ff 02 00  19 09 00 48 64 00 00 fe  |...........Hd...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 38 bf 08 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 6b ee 00 c0 76 00 00  00 00 00 00 02 00 00 00  |.k...v..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 41 3b fd 12 4e  4f 20 4e 41 4d 45 20 20  |..)A;..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 a4  ed 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by kansasnoob on 2011-05-02
Because of this:

> Grub 2 is installed in the MBR of /dev/sda and **[COLOR="Red"]looks for b2d[/COLOR]**.

I need you to run a newer version of the Boot Info Script:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

That will place a newer development version of the script in the home folder, so then if you run:

```
sudo bash boot_info_script.sh RESULTS_NEW.txt
```

You should find a new file named "RESULTS_NEW.txt" in your home folder.

Hopefully that new output will provide a clearer set of results :)

I'll need to resume work on getting that fixed now that Natty has been released, but those who are interested can get some idea of the BIS dev process here:

[http://ubuntuforums.org/showthread.php?t=1676235](http://ubuntuforums.org/showthread.php?t=1676235)

---

### Post by WG- on 2011-05-02
> **kansasnoob said:**
> Because of this:



I need you to run a newer version of the Boot Info Script:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```That will place a newer development version of the script in the home folder, so then if you run:

```
sudo bash boot_info_script.sh RESULTS_NEW.txt
```You should find a new file named "RESULTS_NEW.txt" in your home folder.

Hopefully that new output will provide a clearer set of results :)

I'll need to resume work on getting that fixed now that Natty has been released, but those who are interested can get some idea of the BIS dev process here:

[http://ubuntuforums.org/showthread.php?t=1676235](http://ubuntuforums.org/showthread.php?t=1676235)

This is the new result:

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......gL.:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 60836 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   247,269,375   244,195,328   7 NTFS / exFAT / HPFS
/dev/sda3         247,269,376   329,189,375    81,920,000   7 NTFS / exFAT / HPFS
/dev/sda4         329,191,422   488,396,799   159,205,378   5 Extended
/dev/sda5         481,824,768   488,396,799     6,572,032  82 Linux swap / Solaris
/dev/sda6         329,191,424   475,940,863   146,749,440  83 Linux
/dev/sda7         475,942,912   481,820,671     5,877,760  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BE8A7D6B8A7D20D7                       ntfs       WinRE
/dev/sda2        F690B82590B7EA6F                       ntfs       
/dev/sda3        52D4BE87D4BE6CBB                       ntfs       
/dev/sda5        23db0dfe-fcd9-4c2e-8d80-401cab0441d8   swap       
/dev/sda6        15df8d5f-772d-42b0-809c-f1f04d5d1af8   ext4       
/dev/sda7        2370c014-5dec-49ff-8c07-8c774a1df9e5   swap       
/dev/sdb1        12FD-3B41                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
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
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=15df8d5f-772d-42b0-809c-f1f04d5d1af8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=15df8d5f-772d-42b0-809c-f1f04d5d1af8 ro single 
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
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 15df8d5f-772d-42b0-809c-f1f04d5d1af8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root F690B82590B7EA6F
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
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2370c014-5dec-49ff-8c07-8c774a1df9e5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 161.104740143 = 172.984897536  boot/grub/core.img                             1
 203.109394073 = 218.087051264  boot/grub/grub.cfg                             1
 157.994140625 = 169.644916736  boot/initrd.img-2.6.38-8-generic               2
 161.103008270 = 172.983037952  boot/vmlinuz-2.6.38-8-generic                  1
 157.994140625 = 169.644916736  initrd.img                                     2
 161.103008270 = 172.983037952  vmlinuz                                        1

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

Unknown BootLoader on sda4

00000000  93 74 d7 e1 ca 7d 3f e4  15 a1 ae c3 ef 02 8a 69  |.t...}?........i|
00000010  19 a1 7e f5 23 43 67 be  96 e6 15 15 be b8 f8 53  |..~.#Cg........S|
00000020  fe 92 8e 05 0f fd 61 7b  88 4c dd 3c f7 27 3f ed  |......a{.L.<.'?.|
00000030  6b 6a 46 0f dd 24 f9 25  3c 9f 5e e2 70 cc 0a 79  |kjF..$.%<.^.p..y|
00000040  7f 8f 20 a7 03 30 cc 33  28 e5 ff 7a 4d ef 7a 7b  |.. ..0.3(..zM.z{|
00000050  ff 6f 8f 06 6f 4f 7d 8f  7f 08 85 f4 f8 53 fe 76  |.o..oO}......S.v|
00000060  d8 f7 ff 4e b9 e9 ff 18  d6 89 69 ba bb d2 fd 27  |...N......i....'|
00000070  a4 c7 d3 ce d3 47 a9 d0  a4 d5 d7 86 75 ce 78 8f  |.....G......u.x.|
00000080  a7 be 68 33 a7 1c 9e 19  fd e7 fe 6d 3d e7 c0 2c  |..h3.......m=..,|
00000090  02 c2 8b 0c c3 30 0b 73  c6 78 66 ff 98 7b c6 7f  |.....0.s.xf..{..|
000000a0  e3 80 2e c3 60 17 4f 8c  fa 78 33 2f 31 4c 53 a8  |....`.O..x3/1LS.|
000000b0  f0 ce 93 06 69 3a e7 bd  3d e1 98 66 6c 43 eb ce  |....i:..=..flC..|
000000c0  b8 d8 b3 bc 14 9f 94 d9  a7 3c 77 9d 7a 7d 60 fe  |.........<w.z}`.|
000000d0  11 b2 49 4e 25 27 c2 07  bd 29 e1 98 fa 40 33 3d  |..IN%'...)...@3=|
000000e0  34 68 e7 c0 20 f8 ca 7f  9a 58 f5 a7 1e 23 9d c2  |4h.. ....X...#..|
000000f0  75 74 d3 ee 9c a7 c7 25  b9 c3 e7 5e 05 23 2a 95  |ut.....%...^.#*.|
00000100  d6 db 20 c5 62 5c 1f 0f  c4 82 f5 4a a8 21 f4 0f  |.. .b\.....J.!..|
00000110  a9 df d5 6a 6c db 24 e4  85 dc 55 09 22 c4 e3 42  |...jl.$...U."..B|
00000120  31 1d 6b 12 35 85 8d 4a  42 ac f7 53 66 cd 45 a6  |1.k.5..JB..Sf.E.|
00000130  98 1a 9f 19 e3 37 d3 a3  37 88 98 b3 84 a1 98 66  |.....7..7......f|
00000140  9f 4f 51 80 67 f3 49 ff  7b e8 ce 9e 5f 38 01 63  |.OQ.g.I.{..._8.c|
00000150  0f ba e7 bc 63 df 49 3a  e7 85 3f fe 23 00 bd 9a  |....c.I:..?.#...|
00000160  68 88 e1 d1 9e 19 be 9e  fd 3c 74 10 f2 36 b0 cd  |h........<t..6..|
00000170  f4 a0 d7 db 30 5a 2e 4c  8e 9b 7a e4 c3 51 90 af  |....0Z.L..z..Q..|
00000180  e9 f2 77 85 0c af ab 9c  73 c0 a9 bf be f4 c9 b7  |..w.....s.......|
00000190  88 fb a6 3e d1 d0 cf ef  72 4e 9b 06 78 05 8c f7  |...>....rN..x...|
000001a0  d3 ff 3b f3 cf 18 f7 d3  3f 3c f4 5a b3 07 e9 f4  |..;.....?<.Z....|
000001b0  f0 0b 78 66 19 8c fa 77  e4 20 16 f7 a4 ff 00 fe  |..xf...w. ......|
000001c0  ff ff 82 fe ff ff 02 00  19 09 00 48 64 00 00 fe  |...........Hd...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 38 bf 08 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1577: [: 2.73495e+09: integer expression expected

```

---

### Post by kansasnoob on 2011-05-02
Well it says that grub is looking at:

> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,**[COLOR="Red"]msdos5[/COLOR]**)/boot/grub on this drive.

But sda5 is one of two swap partitions:

> sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

So let's try this. Using a Live CD/USB copy-n-paste the following commands:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Hopefully that gets you booting.

---

### Post by WG- on 2011-05-02
> **kansasnoob said:**
> Well it says that grub is looking at:



But sda5 is one of two swap partitions:



So let's try this. Using a Live CD/USB copy-n-paste the following commands:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
``````
grub-install /dev/sda
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```Hopefully that gets you booting.

Thanks. Gonne try this right now!

---

### Post by WG- on 2011-05-02
It worked!!! Thank you very much!! And thanks for explaining what was wrong. I will try to remember those commands and such.

\\:D/

---

### Post by kansasnoob on 2011-05-02
Glad it worked out for you :)

Could I get you to use the thread tools to mark this solved?

---

