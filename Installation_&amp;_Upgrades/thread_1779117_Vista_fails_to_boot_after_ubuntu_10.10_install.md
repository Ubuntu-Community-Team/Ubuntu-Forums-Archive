---
title: "Vista fails to boot after ubuntu 10.10 install"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by kph01 on 2011-06-10
Hi, 

I searched this forum, and did not find one with similar error message, so please help.

On my Dell Inspiron-15 laptop, there is a C: drive of 250 GB with Vista SP2 installed, and an external  USB WD drive of 500 GB.

After booting into  a Ubuntu 10.10 live CD, I chose the "Install Ubuntu" option to install Ubuntu. As the install progresses, it gets to the partition screen, and I accidentally selected the USB drive (instead of the C: drive) where the linux partition is to be added, and in this case, I allocated 30 GB for the new partition. The install continued until it ended with a number of messages showing up on the screen, which did not stay long enough for me to write down the actual message.

After the Ubuntu install, I have not been able to boot into Vista since. On a re-start, I always get the following error message:

reloc offset is out of the segment. Aborted. Press any key to exit.

When I press any key, it booted into CD and the "Try Ubuntu" & "Installl Ubuntu" screen comes up. When I exited this screen, the Ubuntu booted up. I read from some threads that running the boot_info_script will be useful to help in the debugging, so I have copied the RESULTS.txt file created from running that script, as follows:

------------------------------------------                 

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc.

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
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     30,801,920   488,395,119   457,593,200   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   917,276,528   917,276,466   c W95 FAT32 (LBA)
/dev/sdc2         917,276,670   976,771,071    59,494,402   5 Extended
/dev/sdc5         917,276,672   974,227,455    56,950,784  83 Linux
/dev/sdc6         974,229,504   976,771,071     2,541,568  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        FA6045A960456E07                       ntfs       RECOVERY
/dev/sda3        CE5447E85447D1BF                       ntfs       OS
/dev/sdc1        8543-3F4A                              vfat       
/dev/sdc5        94ee9ab7-496e-4923-8201-db70ab0d1fbc   ext4       
/dev/sdc6        c7fc5074-8037-4498-9057-e265f17eb356   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/8543-3F4A         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc5        /media/94ee9ab7-496e-4923-8201-db70ab0d1fbc ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 94ee9ab7-496e-4923-8201-db70ab0d1fbc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 94ee9ab7-496e-4923-8201-db70ab0d1fbc
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 94ee9ab7-496e-4923-8201-db70ab0d1fbc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=94ee9ab7-496e-4923-8201-db70ab0d1fbc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 94ee9ab7-496e-4923-8201-db70ab0d1fbc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=94ee9ab7-496e-4923-8201-db70ab0d1fbc ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 94ee9ab7-496e-4923-8201-db70ab0d1fbc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 94ee9ab7-496e-4923-8201-db70ab0d1fbc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ce5447e85447d1bf
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=94ee9ab7-496e-4923-8201-db70ab0d1fbc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=c7fc5074-8037-4498-9057-e265f17eb356 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 445.524936676 = 478.378758144  boot/grub/core.img                             1
 461.542209625 = 495.577174016  boot/grub/grub.cfg                             1
 451.782226562 = 485.097472000  boot/initrd.img-2.6.35-22-generic              2
 445.523479462 = 478.377193472  boot/vmlinuz-2.6.35-22-generic                 1
 451.782226562 = 485.097472000  initrd.img                                     2
 445.523479462 = 478.377193472  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 5a 00  |.Z.MSWIN4.1..@Z.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  32 87 ac 36 57 b5 01 00  00 00 00 00 38 e3 0f 00  |2..6W.......8...|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 4a 3f 43 85 4e  4f 20 4e 41 4d 45 20 20  |..)J?C.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

-----------------------------------

Q1: What do I need to do  to boot  back into Vista? I hope Vista has not been corrupted.

Q2: After I get back to Vista, I still wish to set up dual boot with both VIsta and Ubuntu. Do I have to re-install  Ubuntu again, this time on the C: drive?

Please help.

Thanks,
kph01

---

### Post by hashbrowns707 on 2011-06-10
Don't worry about your Vista partition, it's all there. I dual boot, and something like this always seems to happen to me whenever I switch distros.

Yup, here's the problem:
> Windows is installed in the MBR of /dev/sdc.

but later, we read in the Drive/Partition info...
> Disk /dev/sdc: 500.1 GB, 500107862016 bytes
And you said that your external drive was 500GB. Grub is just looking in the wrong place.

Try re-installing Grub, that's probably the easiest way to solve the problem. There's even a handy gui now. [https://help.ubuntu.com/community/Grub2#Use%20Boot-Repair%20Graphical%20Tool]("https://help.ubuntu.com/community/Grub2#Use%20Boot-Repair%20Graphical%20Tool")

---

