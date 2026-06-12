---
title: "Dual Boot - XP SP3 /Ubuntu 10.4 - No XP boot after install Ubuntu 10.04"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by josel2820@gmail.com on 2010-08-31
Hello Guys, I cannot boot XP in my laptop , someone can help me please:
The history is:
I recently install Ubuntu 10.04 in my  Dell inspiron 6400(hard disk  of 80GB) laptop , after that I install Ubuntu , XP does not appear in the Grub menu when I power on my laptop.

I add an entry to the /boot/grub/grub.cfg  ( I read that in [http://www.cyberciti.biz/faq/grubconf-for-windows-vista-or-xp-dual-boot/](http://www.cyberciti.biz/faq/grubconf-for-windows-vista-or-xp-dual-boot/) ) with the follow information :
title Microsoft Windows XP
root (hd0,5)
savedefault
makeactive
chainloader +1
The entry added  appears in the grub menu but when I access this entry XP does not boot(appear an black screen  with a cursor).
I also  read that running the command sudo update-grub, it might make bootable(that XP appears in the Grub menu and that  it boot)  xp but it did not work.

NOTE: The path for the lost   Windows XP is  /dev/sda5 and is labeled like "nuevo_windows".

I have downloaded the bash script in [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)  , the output of the script is in **[http://pastebin.com/VYzu9K8r](http://pastebin.com/VYzu9K8r) **or this  can be found in this post:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Recovery: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    47,198,969    47,102,580   7 HPFS/NTFS
/dev/sda3          47,199,031   149,998,904   102,799,874   5 Extended
/dev/sda5          47,199,033    68,163,794    20,964,762   7 HPFS/NTFS
/dev/sda6          68,163,860   130,110,434    61,946,575  83 Linux
/dev/sda7         130,110,498   141,902,144    11,791,647  83 Linux
/dev/sda8         141,902,208   145,805,939     3,903,732  82 Linux swap / Solaris
/dev/sda9         145,806,003   149,998,904     4,192,902  dd Dell Media Direct
/dev/sda4         149,998,905   156,296,384     6,297,480  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,397,167   488,397,105   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-021B                              vfat       DellUtility                   
/dev/sda2        4CA0E2FAA0E2EA02                       ntfs       datos                         
/dev/sda3: PTTYPE="dos" 
/dev/sda4                                               vfat       DellRestore                   
/dev/sda5        18DC0741DC071920                       ntfs       nuevo_windows                 
/dev/sda6        a9bb6950-0667-4d37-b48d-0144ab499075   ext3                                     
/dev/sda7        99019f61-27f8-464c-8cbe-b2b54f752f2a   ext3                                     
/dev/sda8        2b4e1438-2691-4a3b-a1dd-1c629134d8e1   swap                                     
/dev/sda9        07D7-021B                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5E6C87096C86DB63                       ntfs       bits_portables                
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro)
/dev/sda6        /home                    ext3       (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(8)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(8)\WINDOWS="xpk" xpk 
multi(0)disk(0)rdisk(0)partition(8)\WINDOWS=""  
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 99019f61-27f8-464c-8cbe-b2b54f752f2a
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 99019f61-27f8-464c-8cbe-b2b54f752f2a
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
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 99019f61-27f8-464c-8cbe-b2b54f752f2a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=99019f61-27f8-464c-8cbe-b2b54f752f2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 99019f61-27f8-464c-8cbe-b2b54f752f2a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=99019f61-27f8-464c-8cbe-b2b54f752f2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 99019f61-27f8-464c-8cbe-b2b54f752f2a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 99019f61-27f8-464c-8cbe-b2b54f752f2a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-021b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda9)" {
    insmod fat
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 07d7-021b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=99019f61-27f8-464c-8cbe-b2b54f752f2a /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=a9bb6950-0667-4d37-b48d-0144ab499075 /home           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=2b4e1438-2691-4a3b-a1dd-1c629134d8e1 none            swap    sw              0       0
none /proc/bus/usb usbfs devgid=1002,devmode=666 0 0

=================== sda7: Location of files loaded by Grub: ===================


  68.4GB: boot/grub/core.img
  68.4GB: boot/grub/grub.cfg
  68.3GB: boot/initrd.img-2.6.32-21-generic
  68.4GB: boot/vmlinuz-2.6.32-21-generic
  68.3GB: initrd.img
  68.4GB: vmlinuz

================================ sda9/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  1c 28 09 cc 3d 7b e8 8b  f0 b3 f6 00 a8 e5 26 14  |.(..={........&.|
00000010  77 fe 9f ac 77 b0 f6 f1  21 08 d4 82 77 19 73 7c  |w...w...!...w.s||
00000020  5d 92 8a 4d 41 fb 54 42  b1 5f bb 33 17 32 47 4f  |]..MA.TB._.3.2GO|
00000030  93 e1 4c 1d de 88 4b 42  1e b4 9a d4 da 34 69 f6  |..L...KB.....4i.|
00000040  d6 c2 d6 db 89 f9 8a ba  4a 15 4e 53 ba 1f 77 26  |........J.NS..w&|
00000050  c4 32 61 6d d0 0f 9e e1  84 07 9d 41 9e 76 c2 9b  |.2am.......A.v..|
00000060  53 f8 42 eb fd c1 78 af  d6 da 47 83 14 19 60 ef  |S.B...x...G...`.|
00000070  d4 8f 55 48 90 70 25 c0  40 be d9 96 dc 6c e3 60  |..UH.p%.@....l.`|
00000080  37 c1 45 48 c2 a7 eb 7c  b4 41 0b 1a 50 68 0a 7b  |7.EH...|.A..Ph.{|
00000090  09 ec f2 08 e9 1a aa 65  d3 3e 9a d5 37 34 03 47  |.......e.>..74.G|
000000a0  84 81 c2 ed 70 aa eb f1  d7 a4 db 53 39 83 4f fe  |....p......S9.O.|
000000b0  85 cb 50 8d 2a 52 f9 9d  a3 3f d5 b3 c3 d0 08 e2  |..P.*R...?......|
000000c0  51 04 34 4b 2f 51 56 39  23 a5 10 40 0f f2 39 db  |Q.4K/QV9#..@..9.|
000000d0  a7 46 e9 74 22 46 9a 41  60 53 95 85 c0 ac fa 60  |.F.t"F.A`S.....`|
000000e0  f1 d9 c0 2c d3 0b f0 78  ee 24 31 02 9b c9 16 f1  |...,...x.$1.....|
000000f0  b6 5d 97 6a c5 46 2f 11  f6 57 1a f9 39 53 74 79  |.].j.F/..W..9Sty|
00000100  b0 75 e6 ad e5 4d ed b2  9c 87 d2 2a 3f 0d ac 01  |.u...M.....*?...|
00000110  cd 72 ea 77 fd c5 df 59  b1 ee 59 9c b5 42 23 ef  |.r.w...Y..Y..B#.|
00000120  50 cc 54 33 4d fc d1 25  31 f1 5c 13 82 1c 63 f4  |P.T3M..%1.\...c.|
00000130  5b 16 cd 03 86 c9 21 8d  20 8e 9e e7 12 6a a0 ce  |[.....!. ....j..|
00000140  7e af 3c a6 ee 0f 6f 54  46 a5 96 1f 84 d6 7a 30  |~.<...oTF.....z0|
00000150  03 79 8b 23 9e 33 1d 9d  54 95 ee 77 63 98 b3 8a  |.y.#.3..T..wc...|
00000160  22 b1 27 2e fd f2 36 6b  23 c6 47 94 3c 5e 95 68  |".'...6k#.G.<^.h|
00000170  4d da 8e 59 4d 01 db 7b  32 f2 33 16 2d ac 33 ae  |M..YM..{2.3.-.3.|
00000180  a7 82 91 15 d6 29 e5 d6  47 f3 55 b0 dc 9f 6c cc  |.....)..G.U...l.|
00000190  3b f0 95 d6 d5 1b 8c a2  a0 56 e3 75 2f ca 61 2a  |;........V.u/.a*|
000001a0  ee 29 13 f9 53 2a e9 bd  1d bf 93 43 76 a7 d3 82  |.)..S*.....Cv...|
000001b0  ae de cd 06 30 ed 42 9d  3b 02 c9 91 1b bb 00 fe  |....0.B.;.......|
000001c0  ff ff 07 fe ff ff 02 00  00 00 9a e5 3f 01 00 fe  |............?...|
000001d0  ff ff 05 fe ff ff 9c e5  3f 01 10 3b b1 03 00 00  |........?..;....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Thanks in advance.

---

### Post by Stolen on 2010-08-31
You might want to change the root to:
```

root (hd0,2)

```

---

### Post by josel2820@gmail.com on 2010-08-31
I  apologize for the lack of this important detail:
NOTE: The path for the lost   Windows XP is  /dev/sda5 and is labeled  like "nuevo_windows".

---

### Post by oldfred on 2010-08-31
Windows only boots thru a primary partition. The only grub entry that will work is to sda2. You cannot directly boot windows in extended installs (some experts here did get XP to boot with much effort but windows does not support it).

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You need to have grub linking to sda2 and you need to have 
/ntldr /NTDETECT.COM in that partition. You can copy from your sda9 partition. You may also have to repair your sda2 partition to make sure it has windows in the boot sector correctly.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

Some of the advanced info:
How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
[http://ubuntuforums.org/showthread.php?p=5726832](http://ubuntuforums.org/showthread.php?p=5726832)

---

### Post by josel2820@gmail.com on 2010-09-01
Thanks for your help.
I have reinstalled XP  in the primary partition  sda2.

---

