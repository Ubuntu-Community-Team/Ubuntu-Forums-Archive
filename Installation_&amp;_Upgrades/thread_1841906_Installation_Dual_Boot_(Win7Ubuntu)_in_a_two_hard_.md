---
title: "Installation Dual Boot (Win7/Ubuntu) in a two hard disk laptop"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by Delosari on 2011-09-10
Hello everyone.

I have just bought an ASUS G53J and I would like to install ubuntu. I have done this in the past but now I have some troubles due to the fact this laptop has a two hard drive system.
I have successfully installed ubuntu but I guess, it is not right as the grub window does not appear. These are the discs configuration:

-Hard disc 1:

a) Primary Partition (20 Gb): This is where the partition where the factory set-up (windows 7, drivers, asus software...) for a hard reset is stored

b) Primary partition, boot, system (440Gb): Windows 7 partition.


-Hard disc 2:

c) Primary partition (200Gb): Personal disc
d) Primary partition (200Gb): Personal disc
d) Primary partition (2Gb): Swap
e) Primary partition (10Gb): /home
f) Primary partition, boot (20Gb): /

In the ubuntu 11.04 there is a new option in the "Something else" and "Advance" installation: "Device for boot loader animation" I chose the /drive and I guess this is the problem: Where should I put it without erasing previous contempt. 

One more thing I have never known if it matters: Which of the ubuntu partitions should be logical or primary? And which should be the order of installation (from left to right)?

Thanks a lot for your patience.

---

### Post by Hakunka-Matata on 2011-09-10
> **Delosari said:**
> Hello everyone.

I have just bought an ASUS G53J and I would like to install ubuntu. I have done this in the past but now I have some troubles due to the fact this laptop has a two hard drive system.
I have successfully installed ubuntu but I guess, it is not right as the grub window does not appear. These are the discs configuration:

-Hard disc 1:

a) Primary Partition (20 Gb): This is where the partition where the factory set-up (windows 7, drivers, asus software...) for a hard reset is stored

b) Primary partition, boot, system (440Gb): Windows 7 partition.


-Hard disc 2:

c) Primary partition (200Gb): Personal disc
d) Primary partition (200Gb): Personal disc
d) Primary partition (2Gb): Swap
e) Primary partition (10Gb): /home
f) Primary partition, boot (20Gb): /

In the ubuntu 11.04 there is a new option in the "Something else" and "Advance" installation: "Device for boot loader animation" I chose the /drive and I guess this is the problem: Where should I put it without erasing previous contempt. 

One more thing I have never known if it matters: Which of the ubuntu partitions should be logical or primary? And which should be the order of installation (from left to right)?

Thanks a lot for your patience.

Hi, Welcome to the forums.


[LIST]
[*] It sounds like you may have installed Grub to the / (root) partition.  It should be installed to the MBR of sda or sdb.  Without having more information, it's safe to say you can install in to the MBR of sdb, your *disc 2*
[*]Linux/Ubuntu happily lives on either Primary or Logical (contained within an Extended partition) partitions.
[*]Windows on the other hand, must be installed to a primary partition.
[/LIST]
 
Boot into Ubuntu and do the following please:

Post output of ```
sudo sfdisk -luM
```Please download, install, and run the program [boot_info_script.sh]("http://bootinfoscript.sourceforge.net/"):
post the text contents of file named RESULTS.txt between code tags (# icon).  That will reveal how your computer is attempting to boot.  With that information suggestions can be offered on how to fix.

---

### Post by Hakunka-Matata on 2011-09-10
Please post output of - excuse, never mind

---

### Post by Delosari on 2011-09-10
Thank you kindly for your reply: I think I have managed to do what you have asked. I have managed to load into ubuntu by going into bios and asking the computer to boot on the second disc.  

These are the results from the "sudo sfdisk -luM" command :

```
Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track 
 Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0 
  
    Device Boot Start   End    MiB    #blocks   Id  System 
 /dev/sda1         0+ 20002- 20003-  20482843+  1c  Hidden W95 FAT32 (LBA) 
 /dev/sda2   * 20002+ 476939- 456937- 467902684    7  HPFS/NTFS 
 /dev/sda3         0      -      0          0    0  Empty 
 /dev/sda4         0      -      0          0    0  Empty 
  
 Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track 
 Warning: extended partition does not start at a cylinder boundary. 
 DOS and Linux will interpret the contents differently. 
 Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0 
  
    Device Boot Start   End    MiB    #blocks   Id  System 
 /dev/sdb1         1  238459  238459  244182016    7  HPFS/NTFS 
 /dev/sdb2     238460  444169- 205710- 210646560+   7  HPFS/NTFS 
 /dev/sdb3   * 457409  476938  19530   19998720   83  Linux 
 /dev/sdb4     444169+ 457408  13240-  13556737    5  Extended 
 /dev/sdb5     444170  446122   1953    1999872   82  Linux swap / Solaris 
 /dev/sdb6     446124  457408  11285   11555840   83  Linux 
```And these are the results from the Script:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb3 
                       and looks at sector 971067320 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos3)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

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
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    40,965,749    40,965,687  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,965,752   976,771,119   935,805,368   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   488,366,079   488,364,032   7 NTFS / exFAT / HPFS
/dev/sdb2         488,366,080   909,659,200   421,293,121   7 NTFS / exFAT / HPFS
/dev/sdb3    *    936,773,632   976,771,071    39,997,440  83 Linux
/dev/sdb4         909,660,158   936,773,631    27,113,474   5 Extended
/dev/sdb5         909,660,160   913,659,903     3,999,744  82 Linux swap / Solaris
/dev/sdb6         913,661,952   936,773,631    23,111,680  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3E5F-3A2B                              vfat       RECOVERY
/dev/sda2        F424E8D124E8983E                       ntfs       Programas
/dev/sdb1        189AE80B9AE7E36C                       ntfs       Ocio
/dev/sdb2        60A4ED2DA4ED05FE                       ntfs       Data
/dev/sdb3        b3836543-c7b9-44f4-b0de-eb4e94dc207e   ext4       
/dev/sdb5        8d9dc53d-193b-4066-8d3f-dd5da058a642   swap       
/dev/sdb6        a8fb5709-b81d-4a7e-9939-0a6e70f57066   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb6        /home                    ext4       (rw,commit=0)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root b3836543-c7b9-44f4-b0de-eb4e94dc207e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root b3836543-c7b9-44f4-b0de-eb4e94dc207e
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
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root b3836543-c7b9-44f4-b0de-eb4e94dc207e
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b3836543-c7b9-44f4-b0de-eb4e94dc207e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root b3836543-c7b9-44f4-b0de-eb4e94dc207e
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b3836543-c7b9-44f4-b0de-eb4e94dc207e ro single 
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
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root b3836543-c7b9-44f4-b0de-eb4e94dc207e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root b3836543-c7b9-44f4-b0de-eb4e94dc207e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3e5f-3a2b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root F424E8D124E8983E
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=b3836543-c7b9-44f4-b0de-eb4e94dc207e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=a8fb5709-b81d-4a7e-9939-0a6e70f57066 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=8d9dc53d-193b-4066-8d3f-dd5da058a642 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 463.041007996 = 497.186496512  boot/grub/core.img                             1
 459.042186737 = 492.892794880  boot/grub/grub.cfg                             1
 447.961914062 = 480.995442688  boot/initrd.img-2.6.38-8-generic               2
 463.039279938 = 497.184641024  boot/vmlinuz-2.6.38-8-generic                  1
 447.961914062 = 480.995442688  initrd.img                                     2
 463.039279938 = 497.184641024  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 1e 08  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  37 16 71 02 0f 4e 00 00  00 00 00 00 02 00 00 00  |7.q..N..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 2b 3a 5f 3e 4e  4f 20 4e 41 4d 45 20 20  |..)+:_>NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
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


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```It maybe easier to reinstall ubuntu than to fix the Master Boot Record (I just checked the meaning of that :p). I am not as good as I am in linux as I would like to.

Must I choose the windows partition as the place for the "device for boot loader installation"?

Thanks again

---

### Post by lswartz on 2011-09-10
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

I used this tool today & it worked well. I just did a copy, pasted the cmd into the terminal & clicked onto the recommended repair button.

---

### Post by YesWeCan on 2011-09-10
It all looks fixable.
You really want Grub installed to the MBR of sdb...the disk that Ubuntu is installed on. Not your Windows disk.

So using live CD

```
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Then set your BIOS to boot sdb first.
Once booted into Ubuntu run
```
sudo update-grub
```
to add Windows to your boot menu

---

### Post by Delosari on 2011-09-11
Hi lswartz and YesWeCan:

Thank you very much for your replies: They seem easy enough for me to follow :)

I just would like to understand how this programming works so I can do it better in the future (October update)

1) when you are asked to where to installed the boot device, ubuntu will not delete any files in that partition?

2) there is the posibility to create a partition called "/boot". Is this the place where the boot loader, grub, MBR... will be stored? should i have done that?

Thanks again for your patience

---

### Post by YesWeCan on 2011-09-11
This might help, it is written for Grub-1 but is similar for Grub-2: [http://www.pixelbeat.org/docs/disk/](http://www.pixelbeat.org/docs/disk/)
> 1) when you are asked to where to installed the boot device, ubuntu will not delete any files in that partition?
Grub should not be installed to a partition. This is counter-intuitive because in an MBR multi-boot system the boot program is supposed to be installed to a partition. Grub does not comply and  circumvents the MBR system by replacing it.

The Ubuntu installer allows you to install to a partition but this should not be done because it is unreliable and because if you accidentally choose the wrong partition you could break the boot program of another OS, like Windows.

> 2) there is the posibility to create a partition called "/boot". Is this the place where the boot loader, grub, MBR... will be stored? should i have done that?
This doesn't help. Grub still won't work reliably even if you install its boot program to a dedicated boot partition. Which is unintuitive to say the least.

Ironically, it is possible to install Grub-1 reliably to a partition if it has an accommodating fs type like reiserfs. Unfortunately, Grub-2 does not support this.

---

### Post by Hakunka-Matata on 2011-09-11
> 1) when you are asked to where to installed the boot device, ubuntu will not delete any files in that [COLOR=Red]partition[/COLOR]?If you replace [COLOR=Red]partition[/COLOR] with MBR, the question can be answered.  Yes, installing the Grub boot loader will effectively erase the area it writes to.  For instance when you install Grub to the MBR of a disk, it writes to the first sector of the MBR HDD it is installed to.  It writes up to 512 bytes (one sector) worth of code.  Although it is not overwriting a file per se, it does overwrite whatever code was previously in that first sector.  That is how it will "break" windows boot loader if you install Grub to the MBR of a HDD that contains the windows OS.  That is not a really big problem though, because Windows Bootloader can be easily fixed with several different tools.  And Grub does reside (and function properly) in the first sector of the drive (MBR) that contains windows on a dual boot - Windows & Ubuntu - single HDD machine.  But that's only after Grub is installed properly and sudo update-grub is run after installation.

I'll take comments / corrections, if any discrepancies are spotted in the above text.

---

### Post by Delosari on 2011-09-13
Sorry for not replying!

I have managed to solve the booting problem: I changed the bios booting disc and GRUB handled the rest.

Thanks a lot for your replies, I learned a lot.

---

