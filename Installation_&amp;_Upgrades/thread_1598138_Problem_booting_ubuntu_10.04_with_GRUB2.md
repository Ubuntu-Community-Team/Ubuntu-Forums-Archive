---
title: "Problem booting ubuntu 10.04 with GRUB2"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by enrolled on 2010-10-16
I have Win 7 in my hard drive (sda) and I installed Ubuntu 10.04 in other hard disk (a usb disk), but when I try to boot my pc from the usb disk (sdb), the grub shell is displayed. No menu is displayed. When I boot Windows 7 from sda, it runs correctly. The problem it's when i wanna boot Ubuntu.
I ran bootscript on the live CD and this is what I've obtained:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 130316672 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
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

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,888,507,629 1,888,300,782   7 HPFS/NTFS
/dev/sda3       1,888,507,904 1,951,422,463    62,914,560   7 HPFS/NTFS
/dev/sda4       1,951,422,464 1,953,521,663     2,099,200  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 300.1 GB, 300090728448 bytes
255 cabezas, 63 sectores/pista, 36483 cilindros, 586114704 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   568,018,943   568,016,896  83 Linux
/dev/sdb2         568,020,990   586,113,023    18,092,034   5 Extended
/dev/sdb5         568,020,992   586,113,023    18,092,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BE86D10B86D0C555                       ntfs                                     
/dev/sda2        8EF2CF4FEA41EE07                       ntfs       Boot                          
/dev/sda3        DC9E43999E436ADA                       ntfs       Recover                       
/dev/sda4        12782F65782F46B7                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4494cb94-1c27-408e-8215-ae1bae847631   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        88c8bb2e-5193-4901-82e9-846796a1861a   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 4494cb94-1c27-408e-8215-ae1bae847631
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 4494cb94-1c27-408e-8215-ae1bae847631
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, con Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 4494cb94-1c27-408e-8215-ae1bae847631
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=4494cb94-1c27-408e-8215-ae1bae847631 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic-pae (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 4494cb94-1c27-408e-8215-ae1bae847631
    echo    'Cargando Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=4494cb94-1c27-408e-8215-ae1bae847631 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 4494cb94-1c27-408e-8215-ae1bae847631
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 4494cb94-1c27-408e-8215-ae1bae847631
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set be86d10b86d0c555
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 12782f65782f46b7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=4494cb94-1c27-408e-8215-ae1bae847631 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=88c8bb2e-5193-4901-82e9-846796a1861a none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  66.7GB: boot/grub/core.img
 165.6GB: boot/grub/grub.cfg
  66.7GB: boot/initrd.img-2.6.32-25-generic-pae
  66.7GB: boot/vmlinuz-2.6.32-25-generic-pae
  66.7GB: initrd.img
  66.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  56 fc e1 01 f7 a9 7b 4c  c6 ab 5e ec 03 fb 6c 5b  |V.....{L..^...l[|
00000010  bd 07 7f 5a f7 a7 a8 da  f3 94 e3 c4 1d ba f5 d6  |...Z............|
00000020  eb ce 79 4e 19 a0 cf 73  f0 d7 76 a1 d3 f0 15 cc  |..yN...s..v.....|
00000030  f8 84 b0 ab de c3 47 83  25 f4 ec b3 f7 0c ed c4  |......G.%.......|
00000040  8e f3 1b 32 82 fe 26 fe  e8 bd b1 87 24 fe f8 19  |...2..&.....$...|
00000050  9e 43 96 29 07 5d 87 57  3c df 6b b3 f8 73 4d bb  |.C.).].W<.k..sM.|
00000060  78 ce 38 c1 78 63 0a 7f  64 27 ef 53 6f 7e ae 49  |x.8.xc..d'.So~.I|
00000070  db e0 0f 0f b6 f5 4f ad  b8 63 1b fc 53 b7 d0 61  |......O..c..S..a|
00000080  ea c7 1f 80 a7 32 20 fe  e0 04 5e c8 5b 8b cf fa  |.....2 ...^.[...|
00000090  7d 88 e7 f4 ff e0 a9 ef  cf f6 22 03 3c a7 0d 79  |}.........".<..y|
000000a0  f2 c9 3b 87 fb da b2 1a  0f 8a bf 7a 0f 59 5e f6  |..;........z.Y^.|
000000b0  c3 df d2 1f cb 13 da 72  d3 4d d7 0c 7d 40 5e e9  |.......r.M..}@^.|
000000c0  73 c6 a3 dc 5b a2 af 4b  f1 c7 27 d1 96 da d6 29  |s...[..K..'....)|
000000d0  9a f2 7b f4 85 fe da af  a9 f2 8c bf b8 16 7f da  |..{.............|
000000e0  ad ed e7 1e f8 a7 7c a2  c7 2d bf 0e 6e f8 09 ea  |......|..-..n...|
000000f0  6d e1 6f 3d da 6d e4 5e  fc 7b 63 0e 64 ca b8 43  |m.o=.m.^.{c.d..C|
00000100  79 81 b8 6f 8c 20 d9 7f  78 94 31 21 fd c1 7f ce  |y..o. ..x.1!....|
00000110  f1 17 c8 05 ef ce 8d 2f  2a 4d c5 7f b4 93 b6 18  |......./*M......|
00000120  1f 6f 53 f6 3e c6 32 e0  0d 5f 8d 07 e1 15 7e 18  |.oS.>.2.._....~.|
00000130  fd 04 7f db 0b 5f b1 9f  8c ab c0 03 fc f9 9d be  |....._..........|
00000140  e2 cf 73 7c 09 ff f8 5d  aa 7a e1 73 e0 07 f6 e2  |..s|...].z.s....|
00000150  ef f8 a3 47 d4 ad 0d 10  7f 79 aa cc fb 6c c5 1f  |...G.....y...l..|
00000160  5d b3 1f 73 f8 c2 3b d4  b3 ad 4d 48 9b b5 26 7e  |]..s..;...MH..&~|
00000170  c8 6e f5 a7 bb 92 32 0a  9e e8 38 f8 ab f7 fa 11  |.n....2...8.....|
00000180  ee d1 6e f4 42 bb ce fd  a7 9e fa db 40 8c 0d 90  |..n.B.......@...|
00000190  17 ae 9f 79 e6 9e 21 0f  d0 92 31 64 a4 a7 7f 60  |...y..!...1d...`|
000001a0  6f 3c 07 c6 5f 7c f1 df  cd 97 5f 3e be 79 f3 cd  |o<.._|...._>.y..|
000001b0  33 5d 1d a2 ed 62 64 5c  04 b6 e6 4c ea 98 00 fe  |3]...bd\...L....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 10 14 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 

```I think it's connected with: 
"Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and looks at sector 130316672 of the same hard drive for core.img, but core.img can not be found at this location."
But I don't have experience with linux distributions, and I'm stuck.
I'll appreciate any suggestion. Thank you.

---

### Post by oldfred on 2010-10-16
You did not need to install grub to the partition boot sector of sdb1, but it makes no difference as it is not used.

Your grub2 in the MBR of sdb does point to the correct location. But we have seen some places where it just is not quite right and needs to be reinstalled.

Are you at a system rescue command?
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If at grub rescue you can try manual booting as discussed in above post.

If not try the purge and total reinstall of grub:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

