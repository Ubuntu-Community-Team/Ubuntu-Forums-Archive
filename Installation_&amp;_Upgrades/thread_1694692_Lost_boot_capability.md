---
title: "Lost boot capability"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2011-02-24
I had a dual boot windows xp / ubuntu system. I needed to put more disk space on my system so I had the win xp system disk cloned. After doing that my ubuntu installation no longer appears.

The Ubuntu system was and is on a separate hard drive. So I am fairly sure that it is intact.

Is there someway I can restore the boot information?

---

### Post by oldfred on 2011-02-24
Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by vchapman on 2011-02-24
> **oldfred said:**
> Post this:

Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdc1 and looks 
                       at sector 157336730 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc3 and 
                       looks at sector 162666492 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   819,202,544   819,202,482   7 HPFS/NTFS
/dev/sda2         819,202,545   976,768,064   157,565,520  17 Hidden HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,172,289    78,172,227   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   153,597,464   153,597,402   c W95 FAT32 (LBA)
/dev/sdc2         153,597,465   162,385,019     8,787,555  82 Linux swap / Solaris
/dev/sdc3         162,385,020   240,107,489    77,722,470  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 3996 MB, 3996614144 bytes
255 heads, 63 sectors/track, 485 cylinders, total 7805887 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63     7,791,524     7,791,462   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6A8401E88401B799                       ntfs       Victor2002                    
/dev/sda2        E27003755B41D310                       ntfs       WINDOW BACKUP                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6A8401E88401B799                       ntfs       Victor2002                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        60C4-9A80                              vfat       DATA DISK                     
/dev/sdc2        b7b02dff-90b9-4fbf-8229-1c7e34cec8f7   swap                                     
/dev/sdc3        de833a9a-0024-4fc4-a97c-c78262323fc3   ext4                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        55D123D9E79ABF54                       ntfs       OneTouch4                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        AC49-D212                              vfat       ADATA UFD                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdc3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="10"
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
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set de833a9a-0024-4fc4-a97c-c78262323fc3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6a8401e88401b799
    drivemap -s (hd0) ${root}
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

=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=de833a9a-0024-4fc4-a97c-c78262323fc3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=b7b02dff-90b9-4fbf-8229-1c7e34cec8f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc3: Location of files loaded by Grub: ===================


  83.2GB: boot/grub/core.img
  86.7GB: boot/grub/grub.cfg
  90.2GB: boot/initrd.img-2.6.35-22-generic
  90.9GB: boot/initrd.img-2.6.35-23-generic
  98.6GB: boot/initrd.img-2.6.35-24-generic
  87.3GB: boot/initrd.img-2.6.35-25-generic
  84.3GB: boot/vmlinuz-2.6.35-22-generic
  88.3GB: boot/vmlinuz-2.6.35-23-generic
  88.1GB: boot/vmlinuz-2.6.35-24-generic
  87.9GB: boot/vmlinuz-2.6.35-25-generic
  87.3GB: initrd.img
  98.6GB: initrd.img.old
  87.9GB: vmlinuz
  88.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  ee 55 83 25 00 00 80 01  |.........U.%....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200









```

---

### Post by oldfred on 2011-02-25
When you cloned drive you copied everything, which makes drive identical. But then it has the same UUIDs which are unique so system gets confused. Unplug one or the other drive. Or change UUID that that may cause other issues on clone working.

```
/dev/sda1        [COLOR=Red]6A8401E88401B799[/COLOR]                       ntfs       Victor2002                    
/dev/sda2        E27003755B41D310                       ntfs       WINDOW BACKUP                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        [COLOR=Red]6A8401E88401B799  [/COLOR]                     ntfs   


```I like to the the MBR contain the boot loader of the system on the drive. So can you set BIOS to  boot with grub2 on sdc or the 122GB drive?

You also have grub installed to one of the clones and several partitions. the install to the partition was not necessary but will not cause any issues unless you install it to a windows partition. You may want to reinstall windows boot loader to the clone in sdb, so it will boot windows.

---

### Post by vchapman on 2011-02-25
This is quickly getting beyond my pay grade.

I did not clone the disk myself I paid to have it done -- I am not sure that I received good value for my money!

Here is what I think happened.

The operating system was originally on the 40 gb drive that I think is referred to as sdb1.

The os was cloned to sda1. In addition, a copy was made to sda2. I don't know why it was done this way.

After I got my computer home, I was not happy with the way it was working so I ran the Win XP install / repair feature. This restored the system back to SP2. So it took another day to get it back to being an up-to-date system. At that point it looked pretty good from the outside. However, it was still loading some stuff that I didn't want. The suggested fix required that I edit the registry. At that point I discovered that at least some of the programs being reference in the registry were being pulled from the original operating system (sdb1). Anyway the fix that I applied seems to have worked.

This is a round about way of telling you that if I unplug the 40 gb drive, I don't think the system will boot.

The 120 gb drive that has my data and Ubuntu was not touched in the clonning process. 

Back to you.

---

### Post by vchapman on 2011-02-25
In the BIOS, I switched to boot from the hard drive that has Ubuntu. This threw up the familiar grub menu. I was able to access my Ubuntu install. Then I rebooted and selected the Win XP install. It was described, I think, as /dev/sda1/. Which looked correct. However, it actually booted the original copy of Win XP from the 40 gb hard drive. 

So I guess the question now becomes how do I point the Win XP menu item to correct version of Win XP.

Or how do I load the grub menu into the MBR for the correct version of Win XP.

---

### Post by oldfred on 2011-02-25
That is part of the issue of a duplicate UUID, sometimes it may update one or the other partition, or even boot the other. You now do not have a clone, but two different versions. But as long as the UUID is the same your system has issues and they will get worse. Of course if one drive fails, both drives fail as now some info is missing from the failed drive.

You should back up both separately even though they are mostly still identical.
A couple of users have posted windows backup suggestions. I have not used them:
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Then you are going to have to perform major surgery to separate your co-joined twins. You will have to manually try to restore the cloned drives to full clone state, by figuring out which drive has the newer info you want to keep and updating the other.  Then you need to disconnect one and see if it the other works ok.

A clone is not meant to be part of a working system, but a backup.

I would be tempted to just backup important data and reinstall windows & reconfigure. But that is what I now do with Ubuntu every 6 months with the new version and I have semi-automated it to make it easy. Windows is not so easy, especially reinstalling apps. In Ubuntu I give it a list of apps from my previous install and 20 minutes later I have it done. With windows each app takes a long time because of the number of reboots required.

In my XP I used to use Belarc Advisor as it listed installed apps & serial numbers. Sometimes I did not save all that for each app. Not sure it that is still a good way to document a windows system as I use XP so little.

---

