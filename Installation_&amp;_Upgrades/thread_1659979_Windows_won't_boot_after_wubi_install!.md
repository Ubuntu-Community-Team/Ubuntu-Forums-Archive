---
title: "Windows won't boot after wubi install!"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by freshmeat20 on 2011-01-04
I left C: untouched during partitioning. In the beginning boot menu there wasnt any windows 7 selection. so I did sudo update-grub and it found the windows bootloader. But now when I try to load windows it says starting windows and flashes a blue screen then shuts down. Any ideas?

---

### Post by oldfred on 2011-01-04
You mention wubi and partitioning, one of the the advantages of wubi is that you do not have to partition as it runs inside the windows NTFS partition.

So we can see exactly what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by freshmeat20 on 2011-01-04
After a wubi install in windows 7 I can load ubuntu but when i try to start up windows it stops at the load screen with 'starting windows' then flashes a blue screen then reboots. Any ideas?

---

### Post by wilee-nilee on 2011-01-04
How full is the HD?

Have you kept W7 in shape by running a chkdsk every so often? Or have you ever?

Did you try the F8 safe boot?

Is the menu that Ubuntu is on, the Windows boot menu?

Do you have a W7 recovery or install disc to boot to run a chkdsk.

Do you have a Ubuntu live cd?

---

### Post by bcbc on 2011-01-04
Why don't you post the bootinfoscript as requested in your other thread. From your other two posts it's unclear if you have Wubi at all and we really need this information to help you.

---

### Post by freshmeat20 on 2011-01-05
I ran the boot info and it said this

 File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

What can i do to fix the startup?

---

### Post by freshmeat20 on 2011-01-05
It's loading the grub legacy with ubuntu 2 first. Inside that is the option to load the Windows 7 bootloader. Is it because the Windows bootloader isnt being loaded first? (Theres also an option for ubuntu in the windows 7 bootloader)

---

### Post by Rubi1200 on 2011-01-05
Hi,
without the **full** results of the boot info script that you were asked to post it will be extremely hard for us to advise you on the next step.

---

### Post by freshmeat20 on 2011-01-05
Sorry about that. Didn't know what to post.

here it is

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,918    30,801,919    30,720,002   5 Extended
/dev/sda5              81,920    30,801,919    30,720,000  83 Linux
/dev/sda3    *     30,801,920   620,974,767   590,172,848  42 SFS
/dev/sda4         620,974,768   625,140,399     4,165,632  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        2EF48DB4F48D7F39                       ntfs       OS                            
/dev/sda4        5d6833d0-c96f-4625-957c-20ddd768941b   swap                                     
/dev/sda5        e1b23dce-30ca-4962-bea2-89e04f709358   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e1b23dce-30ca-4962-bea2-89e04f709358
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
search --no-floppy --fs-uuid --set e1b23dce-30ca-4962-bea2-89e04f709358
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e1b23dce-30ca-4962-bea2-89e04f709358
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e1b23dce-30ca-4962-bea2-89e04f709358 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e1b23dce-30ca-4962-bea2-89e04f709358
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e1b23dce-30ca-4962-bea2-89e04f709358 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e1b23dce-30ca-4962-bea2-89e04f709358
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e1b23dce-30ca-4962-bea2-89e04f709358
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2ef48db4f48d7f39
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e1b23dce-30ca-4962-bea2-89e04f709358 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=5d6833d0-c96f-4625-957c-20ddd768941b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
  13.5GB: boot/grub/grub.cfg
   2.3GB: boot/initrd.img-2.6.32-24-generic
   2.3GB: boot/vmlinuz-2.6.32-24-generic
   2.3GB: initrd.img
   2.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3e e0 a8 ea 82 d9 cb ba  2b 53 bb 7c 73 da 71 cf  |>.......+S.|s.q.|
00000010  21 c1 c9 04 93 01 1e a9  14 21 3b 1d 23 5d 95 a3  |!........!;.#]..|
00000020  e1 2c 65 bb b6 da 6e f8  68 4d 46 bb e5 28 72 a9  |.,e...n.hMF..(r.|
00000030  46 dc fd 4c 45 fb 6c e5  63 d5 84 dd 03 5f a0 cd  |F..LE.l.c...._..|
00000040  5a c0 f4 b3 2f 76 23 bf  3d 05 6f b8 29 dd d5 29  |Z.../v#.=.o.)..)|
00000050  05 49 ce 33 09 14 44 83  5a 81 07 ce 14 84 74 d6  |.I.3..D.Z.....t.|
00000060  c5 21 08 51 5a 13 e2 fd  9f d1 02 a8 ce e7 4a ed  |.!.QZ.........J.|
00000070  9c 19 39 b3 0b 90 9a 0a  92 72 4e ed 93 3a 8c 3d  |..9......rN..:.=|
00000080  de 95 4a 60 ae 5d ba 06  c0 c0 9c 3d 08 84 3d e0  |..J`.].....=..=.|
00000090  a5 07 ba c7 da 81 6e d7  05 b9 f0 d8 3b a9 53 9c  |......n.....;.S.|
000000a0  3d 00 9c 1c 27 f4 06 ee  a9 c7 bd c6 6a 90 db b2  |=...'.......j...|
000000b0  de 9f fb 6c fb 1b 53 d4  2c 77 bb 39 43 f0 f8 43  |...l..S.,w.9C..C|
000000c0  df d7 70 e0 1e f2 fb 9d  c7 ca 6e 28 76 c7 bb c6  |..p.......n(v...|
000000d0  6a ce 74 a7 28 eb 93 90  06 f8 67 79 c0 08 4a d1  |j.t.(.....gy..J.|
000000e0  9d f9 84 8c 00 0d 78 0a  dc 72 3b 7d 35 f1 a9 e8  |......x..r;}5...|
000000f0  2c 42 ba 45 f3 2d d9 ef  14 ea d4 6e b2 12 9e d8  |,B.E.-.....n....|
00000100  5b 06 41 4e ae 47 75 03  f9 66 c2 1a 22 78 00 5d  |[.AN.Gu..f.."x.]|
00000110  a8 55 19 cf 7b 55 fd ce  a4 a6 66 ee 7b b5 da b3  |.U..{U....f.{...|
00000120  9c b0 1d 4e 40 77 39 4c  a3 ab 23 e0 ac 18 d0 d0  |...N@w9L..#.....|
00000130  53 a9 07 96 a9 3f 15 7d  d1 66 b3 80 7d cf 42 e8  |S....?.}.f..}.B.|
00000140  7a 11 dd d8 76 07 a0 c7  55 93 0c fd 55 9d 93 df  |z...v...U...U...|
00000150  09 81 60 d7 50 31 5c 1e  f3 22 a5 ef 79 1a 18 00  |..`.P1\.."..y...|
00000160  98 c1 76 4e a8 d1 f5 13  a4 0c b0 aa 38 dd 0e 58  |..vN........8..X|
00000170  81 18 12 b9 ae 07 14 97  d0 f0 ce e4 f8 a3 24 08  |..............$.|
00000180  0c 0d 07 98 94 89 17 e5  87 71 8a 53 aa e1 72 67  |.........q.S..rg|
00000190  01 34 ec 4f 42 fa 0b 0b  e8 8f 3f 68 19 5d e1 f7  |.4.OB.....?h.]..|
000001a0  80 0a b8 7c 8d 0a d3 dd  e0 b5 69 b2 1a 10 bb 4a  |...|......i....J|
000001b0  bb c3 39 d2 dc ab 95 40  4f 60 58 67 41 6e 00 19  |..9....@O`XgAn..|
000001c0  15 05 83 fe ff ff 02 00  00 00 00 c0 d4 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda3/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200
```

---

### Post by bcbc on 2011-01-05
you have a normal install of ubuntu. There is a partial wubi install but the root.disk is uninitialized so you only partially installed. Did you ever boot Windows after doing your full partition install?

Why don't you boot from your win7 disk and use it's automatic repair functions. (This will likely replace the bootloader, so you'll need to reinstall grub2's bootloader afterwards to get back your current Ubuntu on /dev/sda5).

PS you're not using grub legacy. It's grub2.

---

### Post by freshmeat20 on 2011-01-05
Is there any way to restore without the boot cd? I don't have a cdrom. I just used ms-sys and now it says invalid partition table.

---

### Post by oldfred on 2011-01-05
ms-sys and probalby lilo will not work as you have SFS partition. You must have in windows tried to create more than 4 primary partitions. Windows does not use the standard extended partition but converts to a proprietary logical volume manager and gives you a message that you cannot convert back. Ubuntu is not compatible with windows in a SFS partition.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)

---

### Post by freshmeat20 on 2011-01-06
Thanks helped alot. Got windows running after the conversion.

---

