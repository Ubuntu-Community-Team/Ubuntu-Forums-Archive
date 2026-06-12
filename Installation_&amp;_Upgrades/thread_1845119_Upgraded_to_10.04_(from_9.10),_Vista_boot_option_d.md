---
title: "Upgraded to 10.04 (from 9.10), Vista boot option disappeared from GRUB"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by osbeav on 2011-09-16
Hi. Still Linux newbie but definitely enjoying it!

Background: dual-booting Ubuntu and Vista on my old Dell laptop. No complaints.

Problem: was running 9.10 for awhile. Finally took the plunge to "update" to 10.04 last night. I just noticed that when I startup, grub no longer lists my Vista option and I'm asking for help to get it back (I use it sparingly).

Searched on the forums. Found similar threads:

[**Ubuntu not showing up in boot loader menu in dell inspiron 14r**]("http://ubuntuforums.org/showthread.php?t=1691744")

[**Grub/XP/Vista Bootloader**]("http://ubuntuforums.org/showthread.php?t=1014708")

... among others. So many that I honestly couldn't decipher which one(s) applied or not. Beauty of having great user community I guess. Thought I'd try my own thread and ask for your help.

Thanks in advance for all the help. My apologies if there's a better way I should have formatted my post or provided more information.

Thanks!

Ran the script, and here's the output of my RESULTS.txt:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

sda9: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,084,160   127,844,335   106,760,176   7 NTFS / exFAT / HPFS
/dev/sda4         127,845,331   234,438,655   106,593,325   f W95 Extended (LBA)
/dev/sda5         230,246,400   234,438,655     4,192,256  dd Dell Media Direct
/dev/sda6         127,845,333   149,324,174    21,478,842  83 Linux
/dev/sda7         149,324,238   168,859,214    19,534,977  83 Linux
/dev/sda8         168,859,278   176,666,804     7,807,527  82 Linux swap / Solaris
/dev/sda9         176,666,868   230,243,579    53,576,712   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-040D                              vfat       DellUtility
/dev/sda2        DC90DCC790DCA8F2                       ntfs       RECOVERY
/dev/sda3        8EDCE031DCE014ED                       ntfs       OS
/dev/sda5        58E4-35D3                              vfat       MEDIADIRECT
/dev/sda6        2dc378c8-b768-4e06-8e77-a0065bbeada9   ext4       
/dev/sda7        52e29675-6de7-40bb-9359-d3c7eb7feb73   ext4       
/dev/sda8        e19881c6-1615-4a95-872e-1de65cc62834   swap       
/dev/sda9        0C74-3C73                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


================================ sda5/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=2dc378c8-b768-4e06-8e77-a0065bbeada9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=2dc378c8-b768-4e06-8e77-a0065bbeada9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=2dc378c8-b768-4e06-8e77-a0065bbeada9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
    echo    'Loading Linux 2.6.31-23-generic ...'
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=2dc378c8-b768-4e06-8e77-a0065bbeada9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2dc378c8-b768-4e06-8e77-a0065bbeada9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-040d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 8EDCE031DCE014ED
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
    insmod fat
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 58e4-35d3
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=2dc378c8-b768-4e06-8e77-a0065bbeada9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=52e29675-6de7-40bb-9359-d3c7eb7feb73 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=e19881c6-1615-4a95-872e-1de65cc62834 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  61.397509098 = 65.925073408   boot/grub/core.img                             1
  63.235014439 = 67.898079744   boot/grub/grub.cfg                             1
  66.421267033 = 71.319292416   boot/initrd.img-2.6.31-23-generic              1
  66.410902500 = 71.308163584   boot/initrd.img-2.6.32-33-generic              1
  66.156176090 = 71.034653184   boot/vmlinuz-2.6.31-23-generic                 1
  66.460508823 = 71.361427968   boot/vmlinuz-2.6.32-33-generic                 1
  66.410902500 = 71.308163584   initrd.img                                     1
  66.421267033 = 71.319292416   initrd.img.old                                 1
  66.460508823 = 71.361427968   vmlinuz                                        1
  66.156176090 = 71.034653184   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 22 20  |.X.MSDOS5.0..." |
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 b9 0d  |........?....H..|
00000020  00 f8 3f 00 ef 0f 00 00  00 00 00 00 02 00 00 00  |..?.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 d3 35 e4 58 44  65 6c 6c 4d 44 33 70 6c  |..).5.XDellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
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


```

---

### Post by coffeecat on 2011-09-16
Don't worry - there's a bug in 10.04 grub which muddles recovery partitions and Windows C: drives. If you select "Windows Recovery Environment (loader) (on /dev/sda3)" it should boot you into Vista. 

I'm intrigued by the Windows XP on sda5, and the grub menu entry for it. Normally XP will only boot into a logical partition such as sda5 if there are Windows boot files in a primary partition for it. What happens when you select the "Microsoft Windows XP Embedded (on /dev/sda5)" item?

---

### Post by osbeav on 2011-09-16
@coffeecat... many thanks for your help!

You were correct - I do boot into Vista when I select the "Windows Recovery Environment (loader) (on /dev/sda3)" option. If it's a bug, is there a fix or corrected in a later distro? Maybe someday soon I'll get away from Windows entirely. :)

I also tried the Windows XP on sda5 option. It gave me an error that read: "Windows Boot Manager has experienced a problem". It's a black screen with white text. It then reads:

File: \Boot\BCD
Status: [didn't write it down]
Info: The Windows Boot Configuration Data File does not contain a valid OS entry

then goes on to read a little more but again I didn't copy it down. So, for the time being I think I'm ok with the help you provided. I'm not sure if I opened a new can of worms though.

Again, many thanks!
osbeav

---

### Post by coffeecat on 2011-09-16
> **osbeav said:**
> If it's a bug, is there a fix or corrected in a later distro?

I haven't seen a fix for 10.04. On my Sony laptop with 10.04, I have a directly bootable recovery partition. (Yours seems a bit different which is why there is no menu entry for it.) I've two grub entries, one for the recovery partition and one for Vista, except they're the wrong way round. I have to remember to select the "wrong" one. I *believe* this was fixed in Maverick (can't quite remember) but it's definitely fixed in Natty (11.04).

Good luck!

---

### Post by oldfred on 2011-09-16
The old fix was to copy the entries to 40_custom and edit them to be correct & then if they worked turn off os-prober so it does not have the original entries. I think grub customizer may now let you update titles, but have not used it.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Old manual way:
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

You can directly boot XP from a logical with grub. Windows only allows boot thru a  primary partition. You have to have all the XP boot files which you do, but you have to remove the Windows 7 bootmgr. You also will have to edit boot.ini to be partition 5 and may have to create a valid NTFS partition boot sector.

How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

---

