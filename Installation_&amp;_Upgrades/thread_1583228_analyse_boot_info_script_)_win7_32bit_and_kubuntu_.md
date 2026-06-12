---
title: "analyse boot info script :) win7 32bit and kubuntu 10.04"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by mitas on 2010-09-27
Hi I have a problem, as most probably (from what I saw on various forums) As for GRUB, because it pops up the message "No Such partition" (I wanted to highlight that in the BIOS set to LBA Disabled I do not know why but my Windows for some time only on UP's, and as the other systems)
[COLOR=#000000]My System:
 1HDD it on Windows 7 and now Kubuntu 10.04 (sda8).
[/COLOR]Help me because I have no idea what and how ...
and here results.txt
> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   100,542,463   100,335,616   7 HPFS/NTFS
/dev/sda3         100,544,510   234,440,703   133,896,194   f W95 Ext d (LBA)
/dev/sda5         100,544,512   132,003,839    31,459,328   7 HPFS/NTFS
/dev/sda6         132,005,888   142,491,647    10,485,760   7 HPFS/NTFS
/dev/sda7         142,493,696   192,493,567    49,999,872   7 HPFS/NTFS
/dev/sda8         192,495,616   206,166,015    13,670,400  83 Linux
/dev/sda9         206,168,064   213,979,135     7,811,072  83 Linux
/dev/sda10        213,981,184   215,980,031     1,998,848  82 Linux swap / Solaris
/dev/sda11        215,982,080   234,440,703    18,458,624   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007624704 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb4                  63     7,827,391     7,827,329   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        42E4E115E4E10C4B                       ntfs       System Reserved               
/dev/sda10       4718323a-36af-43ad-9655-ac3e62d78263   swap                                     
/dev/sda11       9CBF-88A6                              vfat       dehints>
 <                   
/dev/sda2        74E0182AE017F15A                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        A2E2DA6CE2DA43E7                       ntfs       PROGRAMY                      
/dev/sda6        6C98EF7298EF396A                       ntfs       RÓ&#379;NE                       
/dev/sda7        6A1CE88C1CE8551B                       ntfs       MOJE                          
/dev/sda8        775755d0-b2cd-48d8-bd67-3474ca56e3fa   ext4                                     
/dev/sda9        698ac829-177f-4cfc-9c0f-64462da2a98d   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb4        2061-E4AB                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,relatime,errors=remount-ro,barrier=1,data=ordered)
/dev/sda11       /dos                     vfat       (rw,relatime,gid=46,fmask=0007,dmask=0007,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw,relatime,barrier=1,data=ordered)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/sdb4        /mnt/pendrive            vfat       (rw)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 775755d0-b2cd-48d8-bd67-3474ca56e3fa
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 775755d0-b2cd-48d8-bd67-3474ca56e3fa
set locale_dir=($root)/boot/grub/locale
set lang=pl
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 775755d0-b2cd-48d8-bd67-3474ca56e3fa
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=775755d0-b2cd-48d8-bd67-3474ca56e3fa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-21-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 775755d0-b2cd-48d8-bd67-3474ca56e3fa
    echo    'Wczytywanie systemu Linux 2.6.32-21-generic...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=775755d0-b2cd-48d8-bd67-3474ca56e3fa ro single 
    echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 775755d0-b2cd-48d8-bd67-3474ca56e3fa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 775755d0-b2cd-48d8-bd67-3474ca56e3fa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 42e4e115e4e10c4b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=775755d0-b2cd-48d8-bd67-3474ca56e3fa /               ext4    errors=remount-ro 0       1
/dev/sda11      /dos            vfat    utf8,umask=007,gid=46 0       1
/dev/sda9       /home           ext4    defaults        0       2
/dev/sda10      none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 103.2GB: boot/grub/core.img
 104.6GB: boot/grub/grub.cfg
 103.8GB: boot/initrd.img-2.6.32-21-generic
 104.3GB: boot/vmlinuz-2.6.32-21-generic
 103.8GB: initrd.img
 104.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  4d ff 27 fc e7 e5 c0 e0  35 e2 b4 0a ef fb 72 55  |M.'.....5.....rU|
00000010  ec 2e 6c 70 84 d5 e6 fd  7a eb 76 75 dd 85 8e 0c  |..lp....z.vu....|
00000020  6d 9f 6e cf 51 d9 12 7b  97 0b 70 5a 4d 97 10 c8  |m.n.Q..{..pZM...|
00000030  4e ab c3 75 86 53 b2 6d  18 61 a3 fa b5 a2 aa 33  |N..u.S.m.a.....3|
00000040  91 71 7e 04 0d b4 b0 ea  c1 40 de 12 df 2a c1 03  |.q~......@...*..|
00000050  85 2f 89 5a 88 02 78 a9  b0 78 e4 b1 38 16 15 ed  |./.Z..x..x..8...|
00000060  07 d4 41 14 91 68 c8 04  b2 b9 94 58 24 33 f5 a2  |..A..h.....X$3..|
00000070  90 59 db c6 b5 f7 38 e8  e6 e8 e8 4e 26 ba 1a 02  |.Y....8....N&...|
00000080  31 35 d6 ad 15 07 19 26  78 05 d1 07 92 9c 74 1a  |15.....&x.....t.|
00000090  40 65 87 af 0c 40 65 4f  3d 5a 4a a9 98 2f bd 65  |@e...@eO=ZJ../.e|
000000a0  a3 9d e1 74 03 1a 9f 54  9d 38 a6 71 69 a1 55 53  |...t...T.8.qi.US|
000000b0  74 e5 f1 7d fe 65 43 a1  ff 09 cb 28 af ff 5d 8c  |t..}.eC....(..].|
000000c0  88 45 67 09 aa 92 3e 7f  cb 9f f2 3a 47 ba c7 98  |.Eg...>....:G...|
000000d0  eb f4 37 97 ae b8 72 f0  c9 f1 74 dc 4c b0 6c e9  |..7...r...t.L.l.|
000000e0  56 88 c6 20 ca 1f 2a 69  f8 0c 43 2c 13 ae d9 35  |V.. ..*i..C,...5|
000000f0  3c 0b 35 de f7 8a ec 8c  82 04 2b 79 90 9b 58 5d  |<.5.......+y..X]|
00000100  a3 86 f9 38 ef 50 f7 53  e3 b6 a4 db 1b e5 1b e4  |...8.P.S........|
00000110  85 ea 2e dc 38 74 f0 8b  88 7f 27 4f 40 50 57 f2  |....8t....'O@PW.|
00000120  90 df 49 6c d6 2d 98 ae  cc d7 12 0a d8 71 90 bc  |..Il.-.......q..|
00000130  89 1d 94 ca 1b 81 12 f0  a1 5f a5 6d 34 a5 45 4b  |........._.m4.EK|
00000140  a6 2e 99 80 98 55 c6 97  ad 3c 86 e5 4b d8 2d 64  |.....U...<..K.-d|
00000150  ae 64 c2 6e 80 b1 7f 2e  ea 0c ce 89 36 e8 39 08  |.d.n........6.9.|
00000160  3b a8 3c 48 3c a8 3d a8  25 90 50 10 91 18 96 9c  |;.<H<.=.%.P.....|
00000170  63 73 df f7 c2 8f c6 16  24 53 01 d3 9d 5a 7d e3  |cs......$S...Z}.|
00000180  2d 72 40 a1 1b f6 56 b9  17 e2 97 4f 41 52 b4 54  |-r@...V....OAR.T|
00000190  18 42 47 44 d5 89 7e 48  31 3b 15 24 f8 2b 3d fa  |.BGD..~H1;.$.+=.|
000001a0  6d d1 e7 14 11 50 b6 16  3d 45 e8 5e 0a 53 d7 d4  |m....P..=E.^.S..|
000001b0  a1 0e 75 54 45 33 da 1c  1a 72 1c 3a 11 21 00 48  |..uTE3...r.:.!.H|
000001c0  69 a2 07 c3 c3 8c 02 00  00 00 00 08 e0 01 00 0f  |i...............|
000001d0  ff ff 05 0f ff ff 22 0f  e0 01 e0 00 a0 00 00 00  |......".........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 



i try fix Win7 bootloader and reinstall GRUB, but no any effects :(

---

### Post by mitas on 2010-09-27
nobody ? rlly ?! :(
pls give me some adivce
btw. sorry for my english

---

### Post by mitas on 2010-09-28
bump it up :)

---

### Post by oldfred on 2010-09-28
The script looks normal to me. 

I think the hard drive access mode in BIOS has to be large block or auto. Otherwise you have to set it manually like the old days for cylinders, heads, & sectors and new hard drives are too large for those settings.

---

### Post by mitas on 2010-09-28
Yes you're right :) LBA Disabled function in BIOS, like i said in earlier post is a problem. More here:[http://www.linuxquestions.org/questions/ubuntu-63/help-me-with-boot-ubuntu-10-04-and-windows-7-3bit-boot_info_script-included-834909/](http://www.linuxquestions.org/questions/ubuntu-63/help-me-with-boot-ubuntu-10-04-and-windows-7-3bit-boot_info_script-included-834909/)
[COLOR=Black]btw. thx for intrest this topic :)[/COLOR]

---

