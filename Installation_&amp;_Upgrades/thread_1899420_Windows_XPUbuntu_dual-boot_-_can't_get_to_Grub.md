---
title: "Windows XP/Ubuntu dual-boot - can't get to Grub"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by md20901 on 2011-12-23
I have a 2002 vintage Dell desktop w/ Windows XP on a 40GB hard drive.  About 5 years ago I made into a dual-boot system by adding a second hard drive (200 GB) and installing Fedora Core 5.  I found a tutorial which described how to do this.  The essential steps were as follows:
 

 1.  Install Fedora and GRUB on the 200 GB drive, leaving XP and the Windows boot loader untouched on the 40 GB drive.
 

 2.Copy the first 512 bytes of the Linux boot sector from the 200 GB drive to the Windows C: drive with the name “Fedora5.bin.”   
 

 3.  Add a line to the Windows boot.ini file pointing  to the Fedora5.bin file.
 

  This worked perfectly:  the Windows boot loader offered a choice between Windows and Fedora, and when I chose Fedora, I would get the GRUB menu and could boot into Linux.  
 

 Flash forward 5 years.   I wanted to update Linux on the older desktop and have been trying to turn it into a Ubuntu 11.04 /XP dual-boot and failing.   I'm following the same approach as I did 5 years ago – i.e. following steps 1,2,3 above.  (Substituting Ubuntu 11.04 for Fedora.)     I am using the graphical installer from the ubuntu-11.04-desktop-i386.iso dvd and as far as I can tell, Ubuntu is installing with no problems.  (One aspect about which I was uncertain is whether the Linux boot loader should be installed on /dev/sdb (the 200 GB drive) or /dev/sdb1 (the /boot partition on the 200GB  drive.  I chose /dev/sdb. )



  Windows still boots as before but when I choose Ubuntu from the Windows boot loader I am not presented with the GRUB menu.   Instead, after a few seconds I am returned to the Windows boot loader.
 

 The bios is old and does not offer an option to add the 200 GB drive to the list of boot devices, so I cannot simply choose to boot from the 200GB drive vice the 40 GB drive.   
 

 I've attached the output of the boot_info_script.sh, which I downloaded from sourceforge.
 

 Appreciate any guidance that anyone can offer.


Thanks,


Mark



                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub Legacy (v) in the file /FEDCORE5.BIN looks at 
                       sector 136257 on boot drive #2 for the stage2 file, 
                       but no stage2 files can be found at this location. 
                       Grub2 (v1.97-1.98) in the file /ubu1104.bin looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        /BOOT.INI /NTLDR /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        64,259        64,197   6 FAT16
/dev/sda2    *         64,260    78,108,029    78,043,770   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       391,167       389,120  83 Linux
/dev/sdb2             393,214   390,721,535   390,328,322   5 Extended
/dev/sdb5             393,216     4,296,703     3,903,488  82 Linux swap / Solaris
/dev/sdb6           4,298,752    23,828,479    19,529,728  83 Linux
/dev/sdb7          23,830,528   390,721,535   366,891,008  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07D2-030D                              vfat       DellUtility
/dev/sda2        A86CA9836CA94D3E                       ntfs       
/dev/sdb1        97c96e6a-6980-4654-bc4e-19f74a415774   ext2       
/dev/sdb5        1de0b9bd-bd11-4dfd-86c9-049c9749dc05   swap       
/dev/sdb6        d32e2ff4-a2fd-4a58-968c-09f2f8731be2   ext4       
/dev/sdb7        4ddc8688-d566-4bc1-b5d5-4bd1cabe7508   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda2/BOOT.INI: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
c:\fedcore5.bin="Fedora Core 5" 
c:\fedora15.bin="Fedora 15" 
c:\ubu1104.bin="Ubuntu 11.04"--------------------------------------------------------------------------------

============================= sdb1/grub/grub.cfg: ==============================

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
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root d32e2ff4-a2fd-4a58-968c-09f2f8731be2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 97c96e6a-6980-4654-bc4e-19f74a415774
set locale_dir=($root)/grub/locale
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
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 97c96e6a-6980-4654-bc4e-19f74a415774
    linux    /vmlinuz-2.6.38-8-generic root=UUID=d32e2ff4-a2fd-4a58-968c-09f2f8731be2 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 97c96e6a-6980-4654-bc4e-19f74a415774
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=d32e2ff4-a2fd-4a58-968c-09f2f8731be2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 97c96e6a-6980-4654-bc4e-19f74a415774
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 97c96e6a-6980-4654-bc4e-19f74a415774
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root A86CA9836CA94D3E
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
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.073821068 = 0.079264768    grub/core.img                                  2
   0.075798035 = 0.081387520    grub/grub.cfg                                  1
   0.025168419 = 0.027024384    initrd.img-2.6.38-8-generic                   53
   0.012210846 = 0.013111296    vmlinuz-2.6.38-8-generic                      20

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=d32e2ff4-a2fd-4a58-968c-09f2f8731be2 /               ext4    errors=remount-ro 0       1
/dev/sdb1       /boot           ext2    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=4ddc8688-d566-4bc1-b5d5-4bd1cabe7508 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=1de0b9bd-bd11-4dfd-86c9-049c9749dc05 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 44 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.D.Dell 4.1.....|
00000010  02 00 02 00 00 f8 3f 00  3f 00 ff 00 3f 00 00 00  |......?.?...?...|
00000020  c5 fa 00 00 80 00 29 0d  03 d2 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 fa b8  00 00 8e c0 8e d0 bc fc  |................|
00000050  7b fb 0e 1f fc be ae 7d  e8 cd 00 e8 1d 01 0f 82  |{......}........|
00000060  b9 00 66 0f b7 06 16 7c  66 d1 e0 66 0f b7 1e 0e  |..f....|f..f....|
00000070  7c 66 03 c3 66 03 06 1c  7c 66 a3 3e 7c a1 11 7c  ||f..f...|f.>|..||
00000080  ba 20 00 f7 e2 bb 00 02  f7 f3 8b e8 bb 00 05 e8  |. ..............|
00000090  a5 00 0f 82 85 00 ba 10  00 b9 0b 00 be ef 7d 8b  |..............}.|
000000a0  fb f3 a6 74 13 83 c3 20  4a 75 ee 66 ff 06 3e 7c  |...t... Ju.f..>||
000000b0  4d 75 d9 be e3 7d eb 6b  66 0f b7 06 11 7c 66 ba  |Mu...}.kf....|f.|
000000c0  20 00 00 00 66 f7 e2 66  0f b7 0e 0b 7c 66 03 c1  | ...f..f....|f..|
000000d0  66 48 66 f7 f1 66 01 06  3e 7c 66 a1 3e 7c 66 26  |fHf..f..>|f.>|f&|
000000e0  a3 fc 7b 66 26 0f b7 47  1a 8b f8 2d 02 00 66 0f  |..{f&..G...-..f.|
000000f0  b6 1e 0d 7c 66 f7 e3 66  01 06 3e 7c bb 00 07 bd  |...|f..f..>|....|
00000100  04 00 e8 32 00 72 14 81  c3 00 02 66 ff 06 3e 7c  |...2.r.....f..>||
00000110  4d 75 ef bd 00 7c ea 00  02 70 00 be d6 7d eb 03  |Mu...|...p...}..|
00000120  be e3 7d e8 02 00 eb fe  ac 3c 00 74 09 b4 0e bb  |..}......<.t....|
00000130  07 00 cd 10 eb f2 c3 66  a1 3e 7c 66 33 d2 66 0f  |.......f.>|f3.f.|
00000140  b7 0e 18 7c 66 f7 f1 66  42 88 16 45 7c 66 33 d2  |...|f..fB..E|f3.|
00000150  66 0f b7 0e 1a 7c 66 f7  f1 88 16 44 7c a3 42 7c  |f....|f....D|.B||
00000160  b8 01 02 8b 0e 42 7c c0  e5 06 0a 2e 45 7c 86 e9  |.....B|.....E|..|
00000170  8a 36 44 7c 8a 16 24 7c  cd 13 c3 26 80 3e c2 07  |.6D|..$|...&.>..|
00000180  06 74 2a b8 01 02 bb 00  06 b9 01 00 b6 00 8a 16  |.t*.............|
00000190  24 7c cd 13 72 17 26 c6  06 c2 07 06 b8 01 03 bb  |$|..r.&.........|
000001a0  00 06 b9 01 00 b6 00 8a  16 24 7c cd 13 c3 0d 0a  |.........$|.....|
000001b0  42 6f 6f 74 69 6e 67 20  66 72 6f 6d 20 75 74 69  |Booting from uti|
000001c0  6c 69 74 79 20 70 61 72  74 69 74 69 6f 6e 2e 2e  |lity partition..|
000001d0  2e 0d 0a 0d 0a 00 44 69  73 6b 20 65 72 72 6f 72  |......Disk error|
000001e0  0d 0a 00 4e 6f 20 6c 6f  61 64 65 72 0d 0a 00 49  |...No loader...I|
000001f0  4f 20 20 20 20 20 20 53  59 53 00 00 00 00 55 aa  |O      SYS....U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by darkod on 2011-12-23
And why is it a problem to install grub2 from ubuntu to the MBR of sda and use it to boot your system?

---

### Post by flemur13013 on 2011-12-23
> This worked perfectly: the Windows boot loader offered a choice between Windows and Fedora, ...  Heh - I didn't think the windows loader would acknowledge anything else. Are you sure it's windows?  > I chose /dev/sdb.   >  => Windows is installed in the MBR of /dev/sda. => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks for (,msdos1)/grub on this drive.   Put grub on /dev/sda.

---

### Post by oldfred on 2011-12-23
Added code tags which you add by going advanced from edit menu to get the full edit panel at the top, highlight code & click on #. It makes it easier to review & helps preserve formating.

The easiest way is to use grub2's boot loader in the MBR of sda when you cannot boot from sdb. The way you are doing it works with grub legacy and I am not sure if you can make it work with grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

You need to mount both your /boot & your / (root) partitions and then reinstall grub2's boot loader to sda. Some instructions do not mention the separate /boot or just have it as a footnote.

#If separate /boot before grub 1.99
$ sudo mount /dev/sdb6 /mnt
$ sudo mount /dev/sdb1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

#If separate /boot & Natty or later - grub 1.99
$ sudo mount /dev/sdb6 /mnt
$ sudo mount /dev/sdb1 /mnt/boot
$ sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by md20901 on 2011-12-23
[SIZE=4][FONT=Comic Sans MS]Thanks oldfred.  I was hoping to leave the MBR on the XP drive alone but I guess I'll have to get over it.

regards,

Mark
[/FONT][/SIZE]

---

