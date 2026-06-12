---
title: "Windows VISTA won't boot after Ubuntu 10.4 upgrade"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by mumble83 on 2010-06-05
Hi all,
After the upgrade to Ubuntu 10.4 I'm not able to boot on my Windows Vista any more. It is most likely due to my fault during installation, since I ask to overwrite with GRUB also Windows partition's MBR (but if I remember well I think it was not the best solution to put as default overwriting all the MBRs).
Anyway I was not able to fix it until now.
Here is the RESULT.txt from the boot script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 593897347 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 593900323 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 593903299 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,467,712   323,074,047   302,606,336   6 FAT16
/dev/sda3         323,074,048   584,059,139   260,985,092   7 HPFS/NTFS
/dev/sda4         584,059,140   625,137,344    41,078,205   5 Extended
/dev/sda5         584,059,203   623,129,219    39,070,017  83 Linux
/dev/sda6         623,129,283   625,137,344     2,008,062  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3448D9F8E49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        DAE4F6C7E4F6A543                       ntfs       ACER                          
/dev/sda3        38924BB7924B7880                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b3489956-ea40-44c7-90d1-87cc4467e773   ext4                                     
/dev/sda6        a3e6263a-a328-4004-928d-ff53070ab028   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1                                               vfat       VERBATIM                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/VERBATIM_         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="7"
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
set locale_dir=($root)/boot/grub/locale
set lang=it
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    echo    'Caricamento Linux 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-14-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    echo    'Caricamento Linux 2.6.31-14-generic...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3489956-ea40-44c7-90d1-87cc4467e773 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b3489956-ea40-44c7-90d1-87cc4467e773
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3448d9f8e49bed2a
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set dae4f6c7e4f6a543
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b3489956-ea40-44c7-90d1-87cc4467e773 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a3e6263a-a328-4004-928d-ff53070ab028 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#DIMT  mount DATA hard drive at startup 
/dev/sda3       /media/DATA   ntfs 0       0

=================== sda5: Location of files loaded by Grub: ===================


 299.3GB: boot/grub/core.img
 299.7GB: boot/grub/grub.cfg
 303.3GB: boot/initrd.img-2.6.31-14-generic
 300.0GB: boot/initrd.img-2.6.32-22-generic
 301.1GB: boot/vmlinuz-2.6.31-14-generic
 300.5GB: boot/vmlinuz-2.6.32-22-generic
 300.0GB: initrd.img
 303.3GB: initrd.img.old
 300.5GB: vmlinuz
 301.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```I tried to use "bootrec" from Vista recovery disc but /fixboot fails with error:
"Volume does not contain a recognized file system". I don't know if this is because it's not applying it to the right partition, but I cannot select it also with "diskpart" utility as I read somewhere (or, anyway I have the same results).
Using "testdisk" from Ubuntu does not show "BackupBS" but "RebuildBS". Should I proceed?
Please help me
Thanks
EDIT Forgot to say I have a dual boot on the same hard drive.

---

### Post by arrange on 2010-06-05
There should be no Grub in the boot sectors of *sda1* and *sda2*. Did you try to "fixboot" these two?

In *testdisk*:
Does it say that the sectors **are** identical?
[IMG]http://img59.imageshack.us/img59/8882/td7.png[/IMG]

---

### Post by darkod on 2010-06-05
Another thing I am worried about is that your vista partition is suddenly reported as fat16, at least according to fdisk. Don't know if this is a result of diskpart and what you were trying to do with it.
Either way, I would be very careful what I do from now on in your place. You can lose the whole partition with a wrong move.

This is what I am talking about:

```
Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,467,712   323,074,047   302,606,336   6 [COLOR=Red]FAT16[/COLOR]
/dev/sda3         323,074,048   584,059,139   260,985,092   7 HPFS/NTFS
/dev/sda4         584,059,140   625,137,344    41,078,205   5 Extended
/dev/sda5         584,059,203   623,129,219    39,070,017  83 Linux
/dev/sda6         623,129,283   625,137,344     2,008,062  82 Linux swap / Solaris
```

---

### Post by mumble83 on 2010-06-05
This is the list of partitions in testdisk:

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

     Partition                  Start        End    Size in sectors
 1 * Windows RE(store)        0   1  1  1273 254 63   20466747
 2 P FAT16 >32M            1274  14 21 20110 109 31  302606336
 3 P HPFS - NTFS          20110 109 32 36355 254 63  260985092 [DATA]
 4 E extended             36356   0  1 38912 254 63   41078205
 5 L Linux                36356   1  1 38787 254 63   39070017
   X extended             38788   0  1 38912 254 63    2008125
 6 L Linux Swap           38788   1  1 38912 254 63    2008062

[  Type  ]  [  Boot  ]  [Image Creation]  [Undelete]  [  Quit  ]

```

I cannot understand also the meaning of the partition 1: is this the one I should consider to boot on Vista or Partition 2 (where the OS is actually stored?)
And this is the output for Partition 2:

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 2 P FAT16 >32M            1274  14 21 20110 109 31  302606336

Boot sector
Bad

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.


[  Quit  ]  [Rebuild BS]  [  Dump  ]  [Repair FAT]

```

---

### Post by mumble83 on 2010-06-05
> **arrange said:**
> There should be no Grub in the boot sectors of *sda1* and *sda2*. Did you try to "fixboot" these two?



How should I do this? From the command prompt of the recovery CD i cannot use simply "fixboot" but "bootrec /fixboot", but as I said I think I have to specify the partition to apply it. Let's say the target volume is C: and target partition is Partition 2. How is the right sintax?
As a last solution, would a Vista reinstallation solve the MBR problem or not?
Thanks

---

### Post by arrange on 2010-06-05
Not an expert on this, but IMO as *testdisk* sees the partition as FAT, going for a *Rebuild BS* or *Repair FAT* would make things worse.

Could you please post the output of```
sudo dd if=/dev/sda2 bs=512 count=1 | hd
sudo dd if=/dev/sda2 bs=512 skip=302606335 count=1 | hd
```
(should list the boot sector and its backup (first and last sectors of the partition))
Be very careful - **if=** in the commands must be IF (input), not *of* (output).

---

### Post by mumble83 on 2010-06-05
```

~$ sudo dd if=/dev/sda2 bs=512 count=1 | hd
00000000  eb 63 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.c.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 50 38 01  |........?....P8.|
1+0 record dentro
1+0 record fuori
00000020  00 00 00 00 80 00 00 00  ff 67 09 12 00 00 00 00  |.........g......|
00000030  00 00 0c 00 00 00 00 00  2a f8 1a 00 00 00 00 00  |........*.......|
512 byte (512 B) copiati00000040  f6 00 00 00 01 00 00 00  43 a5 f6 e4 c7 f6 e4 da  |........C.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 80 23 33 66 23  |.....3......#3f#|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 75 02 b2 80 ea  |...........u....|
, 0,0448145 s, 11,4 kB/s
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  bb 17 04 80 27 03 74 06  ||<.t...R....'.t.|
00000090  be 88 7d e8 1c 01 be 05  7c f6 c2 80 74 48 b4 41  |..}.....|...tH.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  4d 47 52 20 69 73 20 63  |...<.u..MGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


```

```

~$ sudo dd if=/dev/sda2 bs=512 skip=302606335 count=1 | hd
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 50 38 01  |........?....P8.|
00000020  00 00 00 00 80 00 00 00  ff 67 09 12 00 00 00 00  |.........g......|
00000030  00 00 0c 00 00 00 00 00  2a f8 1a 00 00 00 00 00  |........*.......|
00000040  f6 00 00 00 01 00 00 00  0a 20 c5 a0 c7 f6 e4 da  |......... ......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200
1+0 record dentro
1+0 record fuori
512 byte (512 B) copiati, 0,0164121 s, 31,2 kB/s


```

---

### Post by arrange on 2010-06-05
As you can see, the backup sector looks OK. You can use it to overwrite the original sector, but _it is very risky_.

Have you backed up all your data?
I don't know how to use the *fixboot* command, but have you tried f.e. this?
[http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

---

### Post by oldfred on 2010-06-05
In the script in one place it says FAT and the blkid says NTFS, so which is it.

Try this command from -  man sfdisk
sudo sfdisk --print-id /dev/sda 2

It should return a 7 if it is NTFS.

---

### Post by mumble83 on 2010-06-05
I tried this and got the following output
> 
BootRec /fixmbr
The operation completed successfully.
BootRec  /fixboot
The volume does not contain a recognized file system.
Please  make sure that all required file system drives are loaded and that the  volume is not corrupted.

I really don't know how to tell him to apply it to volume C and to a certain partition.
I have backuped most of the data, I'll run a complete one now on.
How should i go ahead in order to use the backup sector and overwrite the original sector?

---

### Post by arrange on 2010-06-05
[COLOR="Silver"]How should i go ahead in order to use the backup sector and overwrite the original sector? [/COLOR]
```
sudo -s
dd if=/dev/sda2 bs=512 skip=302606335 count=1 | dd of=/dev/sda2 bs=512 count=1
```
But do this only if your only choice is reinstallation. Also you may want to wait for a second opinion on this from somebody.

Another thing: as you ran *BootRec /fixmbr* you will probably be able to boot into Windows only now unless you restore Grub.

---

### Post by mumble83 on 2010-06-05
> **arrange said:**
> [COLOR=Silver][/COLOR]
Another thing: as you ran *BootRec /fixmbr* you will probably be able to boot into Windows only now unless you restore Grub.
I can still boot into Linux yet, that's why I think it didn't really apply the command.
Any other expert using the bootrec commands?
Or giving me the second opinion?
Thank you

---

### Post by mumble83 on 2010-06-06
> **oldfred said:**
> In the script in one place it says FAT and the blkid says NTFS, so which is it.

Try this command from -  man sfdisk
sudo sfdisk --print-id /dev/sda 2

It should return a 7 if it is NTFS.

It returns 6. But booting from Windows Vista recovery CD and using "partimage" in Ubuntu it recognizes it as NTFS format.
Any suggestion?

---

### Post by oldfred on 2010-06-06
I have not done it but you can try this. I think it just changes the partition entry. See man sfdisk for more info.

sudo sfdisk --change-id /dev/sda 2 7

---

