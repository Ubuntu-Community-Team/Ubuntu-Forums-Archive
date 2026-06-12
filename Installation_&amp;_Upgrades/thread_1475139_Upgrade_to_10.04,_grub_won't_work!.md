---
title: "Upgrade to 10.04, grub won't work!"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by booeyschewy on 2010-05-06
Ok so I've tried a number of approaches to restoring grub from this site. none work. I did manage to get grub 2 reinstalled to /sda so now it loads ubuntu, however it will not recognize windows or my external hard drive. if i boot with livecd, it recognizes all my partitions. 

What data should i post? Please help :)

fdisk -l says the boot drive is sda1 (windows), but I tried to install grub on sda3 (linux).

---

### Post by lechien73 on 2010-05-06
Please download boot_info_script from [here]("http://bootinfoscript.sourceforge.net/"). Follow the instructions at the link to run it, and then post the contents of RESULTS.txt here, surrounded by CODE tags.

Thanks

---

### Post by booeyschewy on 2010-05-06
not sure what code tags are but here it is

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 82012544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    72,596,201    72,596,139   7 HPFS/NTFS
/dev/sda2          77,834,986    81,738,719     3,903,734   5 Extended
/dev/sda5          77,834,988    81,738,719     3,903,732  82 Linux swap / Solaris
/dev/sda3          81,738,720   156,296,384    74,557,665  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,086,176,255 1,086,176,193   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A638AA6F38AA3DE5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1bd258e8-883d-48af-b41a-9b48fede5c49   ext4                                     
/dev/sda5        e6ad4bd0-03e1-408e-84da-7998e9ca4256   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        62C4DCEFC4DCC707                       ntfs       SimpleDrive                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        41E2-E990                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1bd258e8-883d-48af-b41a-9b48fede5c49 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1bd258e8-883d-48af-b41a-9b48fede5c49 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1bd258e8-883d-48af-b41a-9b48fede5c49 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1bd258e8-883d-48af-b41a-9b48fede5c49 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1bd258e8-883d-48af-b41a-9b48fede5c49
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=1bd258e8-883d-48af-b41a-9b48fede5c49 /               ext4    errors=remount-ro 0       1
# /dos was on /dev/sdd1 during installation
UUID=BC1A-B5D3  /dos            vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda1 during installation
UUID=A638AA6F38AA3DE5 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows2 was on /dev/sdc1 during installation
UUID=62C4DCEFC4DCC707 /windows2       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=e6ad4bd0-03e1-408e-84da-7998e9ca4256 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  41.9GB: boot/grub/core.img
  55.3GB: boot/grub/grub.cfg
  51.7GB: boot/initrd.img-2.6.31-20-generic
  44.0GB: boot/initrd.img-2.6.32-21-generic
  48.4GB: boot/vmlinuz-2.6.31-20-generic
  42.5GB: boot/vmlinuz-2.6.32-21-generic
  44.0GB: initrd.img
  42.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b2 c5 9f eb 20 90 0d 04  c6 ed 70 9a b6 34 68 67  |.... .....p..4hg|
00000010  b1 de 4a 67 df 3e 98 dc  7c 66 36 a1 9e 14 26 93  |..Jg.>..|f6...&.|
00000020  1d 18 64 6a 68 c1 01 b7  47 e6 25 22 98 e4 18 21  |..djh...G.%"...!|
00000030  69 05 04 20 43 c9 94 00  66 17 5f 18 18 58 18 0e  |i.. C...f._..X..|
00000040  34 60 c8 ca 00 b5 dc 99  c6 17 04 99 e0 16 24 27  |4`............$'|
00000050  42 83 0e 00 46 ea 33 85  1e 55 61 80 71 31 f2 d0  |B...F.3..Ua.q1..|
00000060  82 59 2d f0 c2 6d a2 4a  04 da 62 10 6e 2e 48 40  |.Y-..m.J..b.n.H@|
00000070  b0 8a f9 7f ab e6 27 06  ba a0 80 59 2c 9e 85 2a  |......'....Y,..*|
00000080  9c e8 ec 0c bc a5 d7 25  0b ad 7e ca ee 49 a5 b7  |.......%..~..I..|
00000090  a5 31 ee 61 95 8c 5d 1e  fe 74 13 30 be 61 20 ce  |.1.a..]..t.0.a .|
000000a0  83 27 c2 7f 3f f0 17 e6  85 a4 d5 67 76 76 5c ce  |.'..?......gvv\.|
000000b0  76 ff 9d ac e9 ff a6 44  bb 46 a2 8d dd 9b 9a 6b  |v......D.F.....k|
000000c0  92 34 89 6f 2a 88 e2 8a  c7 3f bb e1 fb 70 8b cd  |.4.o*....?...p..|
000000d0  a4 77 7c c5 b6 e3 e4 75  f7 94 f1 ad 8d cc 6e 4b  |.w|....u......nK|
000000e0  62 e1 22 e4 54 19 43 92  7d 4f b0 6b 7d 55 27 4f  |b.".T.C.}O.k}U'O|
000000f0  f4 16 00 88 dd ce 91 69  37 ca 5c c1 45 33 41 27  |.......i7.\.E3A'|
00000100  0d db 3e 0e 06 98 08 f4  60 f0 29 93 80 a3 88 a3  |..>.....`.).....|
00000110  31 22 cc 20 52 01 1b cc  64 24 1a 43 26 c0 a0 3c  |1". R...d$.C&..<|
00000120  6a 7e 62 c1 11 9b 06 cd  d4 cd c1 a3 07 93 08 81  |j~b.............|
00000130  44 20 83 09 a3 0c d2 3d  30 80 28 78 3c 60 50 b9  |D .....=0.(x<`P.|
00000140  9d 31 98 20 14 a1 09 e0  d1 a6 e2 85 f1 0e 30 0b  |.1. ..........0.|
00000150  5a e0 2a 88 00 0c d2 2d  9e b7 14 92 4d f4 1c 6a  |Z.*....-....M..j|
00000160  ee 74 76 1a 5e 6f 2c 86  84 c1 01 f8 a5 a7 46 ea  |.tv.^o,.......F.|
00000170  b7 bd 91 c4 6e 5e 92 b7  6c e3 32 fd df b7 17 fa  |....n^..l.2.....|
00000180  71 a8 69 f5 6d e8 43 f5  15 2e 4e 32 70 ff 8d 6c  |q.i.m.C...N2p..l|
00000190  14 89 65 db 9c 25 f6 f5  0c 6d 6c 6a 92 93 2b e3  |..e..%...mlj..+.|
000001a0  50 b2 ca 94 44 d9 a4 7d  e8 e1 ad 4a 53 77 c5 a2  |P...D..}...JSw..|
000001b0  e5 6a 71 95 e2 25 6d 09  69 b9 64 dc 88 16 00 fe  |.jq..%m.i.d.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 f4 90 3b 00 00 00  |............;...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by oldfred on 2010-05-06
Have you tried this?
```

sudo update-grub
```

The above is in code tags which you highlight some code  and click on the # in the edit menu and it wrap code tags around it automatically.

---

### Post by booeyschewy on 2010-05-06
can't believe it was so simple!!! It worked, you're the best.

---

### Post by booeyschewy on 2010-05-07
One last thing. It still doesn't see my windows partition and external hard drives when in ubuntu. fdisk does though

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d944d94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4519    36298069+   7  HPFS/NTFS
/dev/sda2            4846        5088     1951867    5  Extended
/dev/sda3            5089        9729    37278832+  83  Linux
/dev/sda5            4846        5088     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7831e5d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       67612   543088096+   7  HPFS/NTFS

---

### Post by oldfred on 2010-05-07
IF fdisk sees it, I would expect nautilus to see it. In places computer, are not all partitions shown in left panel.

If you want to see it directly you should mount it in fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by .volatile. on 2010-05-07
I would like to join having the same problem.
I upgraded from 9.10 to 10.04 and my grub does not start.

I tried sudo update-grub without any success.
During upgrade I provided sda1 as the destination for grub installation.

I copy my results.txt below, can you help, please:

```

```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 70052551 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /ubninit looks at sector 39 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda8 and 
                       looks at sector 69700583 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #8 for /boot/grub.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,096,574     4,096,512   7 HPFS/NTFS
/dev/sda2           4,096,575   160,055,594   155,959,020   f W95 Ext d (LBA)
/dev/sda5           4,096,638    34,877,114    30,780,477   7 HPFS/NTFS
/dev/sda6          34,877,178    55,359,989    20,482,812   7 HPFS/NTFS
/dev/sda7          55,360,053    65,545,199    10,185,147   7 HPFS/NTFS
/dev/sda8          65,545,263    86,734,934    21,189,672  83 Linux
/dev/sda9          86,734,998    87,779,159     1,044,162  82 Linux swap / Solaris
/dev/sda10         87,779,223   160,055,594    72,276,372   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda10       4CDC5576DC555B72                       ntfs       iWORK                         
/dev/sda1        520C96BC0C969B15                       ntfs       base                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        D2D03EF1D03EDC03                       ntfs       XP                            
/dev/sda6        087CFEDF7CFEC70A                       ntfs       TRANS-L                       
/dev/sda7        049865E59865D5A8                       ntfs       PROGs                         
/dev/sda8        b0eb733c-283e-45ba-9abd-f45d1d1838df   ext4                                     
/dev/sda9        92c4be46-1693-460a-95c4-03052aa2537c   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=================== sda1: Location of files loaded by Grub: ===================


    hpGB: grub/core.img
    hpGB: grub/stage2

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
search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
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
search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set b0eb733c-283e-45ba-9abd-f45d1d1838df
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 520c96bc0c969b15
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b0eb733c-283e-45ba-9abd-f45d1d1838df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=92c4be46-1693-460a-95c4-03052aa2537c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  35.8GB: boot/grub/core.img
  34.1GB: boot/grub/grub.cfg
  39.8GB: boot/initrd.img-2.6.31-20-generic
  42.7GB: boot/initrd.img-2.6.32-22-generic
  34.6GB: boot/vmlinuz-2.6.31-20-generic
  41.8GB: boot/vmlinuz-2.6.32-22-generic
  35.6GB: grub/core.img
  42.7GB: initrd.img
  41.8GB: vmlinuz

---

### Post by frantid on 2010-05-07
volatile, please start a new thread and post your results between CODE tags -- i.e. click on the # sign in the reply box and paste in between the brakets ] [

---

