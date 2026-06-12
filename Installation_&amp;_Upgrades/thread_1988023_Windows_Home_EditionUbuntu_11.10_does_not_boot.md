---
title: "Windows Home Edition/Ubuntu 11.10 does not boot"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by cerixon on 2012-05-26
Hello all, I have been using Ubuntu for almost a year and I love it.  I have been experiencing problems with my previous Win XP (don't we all), and so i went back to my original disk (Win XP Home Edition SP2).  i erased my hard drive, for the upteen time,  and began to install the Win XP. After the completion I downloaded all the upgrades for the Windows XP (home Edition SP2) and that included SP3. Then I proceeded to install the Ubuntu O/S, and it asked my to partition the drive and allocate space for Ubuntu,  after all was said and done, it seem everything went according to plan.  Then it asked to be resarted, and when it restarted I the missed seeing the “log in screen” that i was so used to seening where it ask your to select the Operating System.  And so it goes straight to logging into Windows.  I hope this is an easy fix.  Prievoiously i had been using Win XP/Pro (bootlegged copy) and always having problems.  Is there hope for me????  Looking forward to hearing from you great guys..


My Configuration:
Abit 52N – AMD Athlon 64X2 6000 Dual Core – Nividia GEForce 8400 GS 1GB – 4GB ram – 300GB Seagate Drive and 500GB Seagate Drive as Extra Storage only

Laptop – Toshiba Sattelite L 305-S5900– ATI Radeon X1250 – 128MB - Amd Athlon 64X2 - Ubuntu 11.10 – 4BG Ram – 500GB Seagate Drive and External Drive 250GB

---

### Post by darkod on 2012-05-26
Did you install with the manual option? If yes, where did you select to install the bootloader?

You can run the boot info script to show us more details. The link is in my signature. Post the results as explained there. You can do all that from live mode.

The fix should be easy, we just need to see whether only the part of grub2 for the MBR didn't get installed, or the whole of grub2.

---

### Post by cerixon on 2012-05-26
What do you mean by "Did you install with the manual option? If yes, where did you select to install the bootloader?"  cause that just went over my head (lol)

I looked at the 'boot info' and i see some very confusing word (sorry) :confused:

How do i get to that 'boot info',  cause when ever i turn on the computer it goes straight to the "Welcome to Windows XP" or something like that.

---

### Post by wilee-nilee on 2012-05-26
> **cerixon said:**
> What do you mean by "Did you install with the manual option? If yes, where did you select to install the bootloader?"  cause that just went over my head (lol)

I looked at the 'boot info' and i see some very confusing word (sorry) :confused:

Using a live ubuntu cd download this link extract it to your desktop and run the command. 

You will se a results.txt appear, copy all the the text and paste it to a reply.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by cerixon on 2012-05-26
> **wilee-nilee said:**
> Using a live ubuntu cd download this link extract it to your desktop and run the command. 

You will se a results.txt appear, copy all the the text and paste it to a reply.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```



I put in the live cd into the Desktop and started and it loaded to the screen that says "Try Ubuntu"  "Install Ubuntu" with the languages on the left.

Do i go to this link and burn it or download it to an cd or flash drv and then put in on the windows desktop??  I am doing all this writing on my laptop.

Thanks again in advance for your reply.

---

### Post by wilee-nilee on 2012-05-26
> **cerixon said:**
> I put in the live cd into the Desktop and started and it loaded to the screen that says "Try Ubuntu"  "Install Ubuntu" with the languages on the left.

Do i go to this link and burn it or download it to an cd or flash drv and then put in on the windows desktop??  I am doing all this writing on my laptop.

Thanks again in advance for your reply.

You choose try ubuntu from the live cd. You download the link. You click on the download and will be given a extract option, choose the desktop.

You open a terminal by clicking on the top button of the left panel and type terminal. In the terminal copy and paste the command.

A results.txt will appear on the desktop, click it to open it. HIghlight all the text and right click copy. Open a reply in the thread and paste all the text.

  Highlight all the text you have posted and in that reply click the # then hit submit reply.

That should do it, it is confusing at first. :)

---

### Post by cerixon on 2012-05-26
This was kinda easy, of-course i followed your instructions:

ubuntu@ubuntu:~$ sudo bash ~/Desktop/bootinfoscript

Boot Info Script 0.61      [1 April 2012]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/mapper/nvidia_fahdgede...
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching nvidia_fahdgede1 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".

ubuntu@ubuntu:~$ sudo bash ~/Desktop/bootinfoscript

---

### Post by wilee-nilee on 2012-05-26
> **cerixon said:**
> This was kinda easy, of-course i followed your instructions:

ubuntu@ubuntu:~$ sudo bash ~/Desktop/bootinfoscript

Boot Info Script 0.61      [1 April 2012]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/mapper/nvidia_fahdgede...
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching nvidia_fahdgede1 for information... 

[B]Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".[/B]

ubuntu@ubuntu:~$ sudo bash ~/Desktop/bootinfoscript

The highlighted part is what we want all the text from the results.txt that would have been on the desktop. ;)

---

### Post by cerixon on 2012-05-26
so Sorry, my bad:

```

"                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/nvidia_fahdgede and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 686ef367-1e72-44d4-8572-76c821bb248b root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvidia_fahdgede1: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   233,763,688   233,761,641   7 NTFS / exFAT / HPFS
/dev/sdb2         233,764,862   625,141,759   391,376,898   5 Extended
/dev/sdb5         233,764,864   616,755,199   382,990,336  83 Linux
/dev/sdb6         616,757,248   625,141,759     8,384,512  82 Linux swap / Solaris


Drive: nvidia_fahdgede _____________________________________________________________________

Disk /dev/mapper/nvidia_fahdgede: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_fahdgede1   *             63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/nvidia_fahdgede1 5C9431579431353C                       ntfs       DRV3_VOL1
/dev/sda                                                nvidia_raid_member 
/dev/sdb1        92B04FB8B04FA219                       ntfs       
/dev/sdb5        686ef367-1e72-44d4-8572-76c821bb248b   ext4       
/dev/sdb6        6b25f847-268c-4451-8d02-c1407c4be141   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
nvidia_fahdgede
nvidia_fahdgede1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer 
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 686ef367-1e72-44d4-8572-76c821bb248b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 686ef367-1e72-44d4-8572-76c821bb248b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 686ef367-1e72-44d4-8572-76c821bb248b
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=686ef367-1e72-44d4-8572-76c821bb248b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 686ef367-1e72-44d4-8572-76c821bb248b
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=686ef367-1e72-44d4-8572-76c821bb248b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 686ef367-1e72-44d4-8572-76c821bb248b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 686ef367-1e72-44d4-8572-76c821bb248b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 92B04FB8B04FA219
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=686ef367-1e72-44d4-8572-76c821bb248b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6b25f847-268c-4451-8d02-c1407c4be141 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  cb cd 1c f1 ad 99 f3 0e  6e 31 ab e6 81 9d a3 c5  |........n1......|
00000010  19 aa b8 5e 35 43 44 18  5e 35 19 68 53 f8 68 02  |...^5CD.^5.hS.h.|
00000020  9b e6 a2 1f 6a 56 da 69  67 d0 5e 22 85 35 7e 22  |....jV.ig.^".5~"|
00000030  a9 47 59 12 54 64 47 58  f5 02 2a 22 d8 09 90 27  |.GY.TdGX..*"...'|
00000040  40 15 be 89 3f 42 2b 8e  45 35 09 1a 6c 4a eb 11  |@...?B+.E5..lJ..|
00000050  3c 70 ad 4e 7c ca 36 29  32 43 f1 fa c2 e7 5a 16  |<p.N|.6)2C....Z.|
00000060  1e 7f 8c d1 ce 76 fe 00  44 84 76 7c 4f 44 16 08  |.....v..D.v|OD..|
00000070  be 16 78 7b 81 64 4d 1a  13 84 c7 81 de ed b8 50  |..x{.dM........P|
00000080  63 74 90 8a 6c 73 a8 f0  86 8c fd 1a ab 09 20 7d  |ct..ls........ }|
00000090  9f 6e c9 0c f0 08 69 56  99 6a 4f 92 04 ee cd 81  |.n....iV.jO.....|
000000a0  01 ac 69 59 67 3e 6d 9a  09 64 15 df 9f 7b aa 1e  |..iYg>m..d...{..|
000000b0  fb 5c 6c 52 d0 e6 e1 91  f3 95 6f 92 8d 80 b8 01  |.\lR......o.....|
000000c0  18 75 5c 33 64 f3 c8 d7  06 6c e2 f3 bd 34 1d 79  |.u\3d....l...4.y|
000000d0  62 c8 a6 3d 47 16 2b 32  46 16 6e 55 04 8e ae 9c  |b..=G.+2F.nU....|
000000e0  5a bc f6 1a 5a 90 02 59  be f2 34 76 80 b1 ed 74  |Z...Z..Y..4v...t|
000000f0  0e e4 b5 03 7d 06 e4 cb  a4 63 ed 36 ae 03 07 9c  |....}....c.6....|
00000100  0c 42 47 9c c8 1c b4 91  63 9e 18 e6 51 ef c8 5c  |.BG.....c...Q..\|
00000110  ce 91 7b 39 7d 47 3d 36  d4 7b 51 47 9d 30 35 0b  |..{9}G=6.{QG.05.|
00000120  2d 78 dc c8 09 90 31 50  3d ef 52 c6 96 ff b0 e3  |-x....1P=.R.....|
00000130  7f 63 56 8f 0a 32 a7 60  08 8d 02 d9 0f 9d 03 22  |.cV..2.`......."|
00000140  ae a0 b1 40 a6 46 43 18  39 0d b8 69 0e f7 40 04  |...@.FC.9..i..@.|
00000150  9d 8a f4 a8 e2 55 a7 22  05 3c 0c 3b 15 72 d4 b9  |.....U.".<.;.r..|
00000160  18 38 17 99 75 91 03 12  41 e3 a2 2a 00 0f 3a 19  |.8..u...A..*..:.|
00000170  29 94 94 ad fb 4e 47 e2  74 a4 56 47 ee 74 cc 8d  |)....NG.t.VG.t..|
00000180  8e cc ea 88 41 9b f4 9e  9f fd 5b eb 63 08 c4 3f  |....A.....[.c..?|
00000190  82 70 06 40 89 18 00 01  00 01 35 d1 cf 6f d3 30  |.p.@......5..o.0|
000001a0  14 07 70 39 89 93 a6 6d  da 26 fd c1 18 5a f9 31  |..p9...m.&...Z.1|
000001b0  a0 12 d2 3a c6 d0 90 90  38 4c 4c ec 82 34 00 fe  |...:....8LL..4..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f8 d3 16 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f8  d3 16 00 f8 7f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by wilee-nilee on 2012-05-26
So boot the live ubuntu cd again and open a terminal and run this command and post the results. The hd is being seen in a manner that we will want to be sure the commands I give are correct. **Don't reboot from the cd after you have posted the results**, I will have the commands for you immediately.

```
sudo fdisk -l
```the l is a small L

Please confirm as well that you are using a cd that is the same as the install, the same release.

---

### Post by cerixon on 2012-05-26
Reply:

```
"ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x031185c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004488a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   233763688   116880820+   7  HPFS/NTFS/exFAT
/dev/sdb2       233764862   625141759   195688449    5  Extended
/dev/sdb5       233764864   616755199   191495168   83  Linux
/dev/sdb6       616757248   625141759     4192256   82  Linux swap / Solaris

Disk /dev/mapper/nvidia_fahdgede: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x031185c0

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fahdgede1   *          63   976768064   488384001    7  HPFS/NTFS/exFAT

Disk /dev/mapper/nvidia_fahdgede1: 500.1 GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976768002 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fahdgede1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
/dev/mapper/nvidia_fahdgede1p2   ?  1917848077  2462285169   272218546+  73  Unknown
/dev/mapper/nvidia_fahdgede1p3   ?  1818575915  2362751050   272087568   2b  Unknown
/dev/mapper/nvidia_fahdgede1p4   ?  2844524554  2844579527       27487   61  SpeedStor

Partition table entries are not in disk order
ubuntu@ubuntu:~$

```
And yes i am using the same DVD that i burned the .11.10

---

### Post by wilee-nilee on 2012-05-26
Cool thanks so it may be as simple as you need the sdb hd moved to being read before the sda HD in the bios lets try that first.

The bios is generally accessed with a f2 key at powering on so go in and move the sdb HD above the sda and see if you get the grub menu to choose either operating system.

---

### Post by cerixon on 2012-05-26
Alright I held the "F2" key from the time it reboot till the time it went to the Windows Green Field (desktop).  Now what??

---

### Post by wilee-nilee on 2012-05-26
I think you are going to be better served by darkod with this situation, I am seeing a few things which make me wonder what the best way is to approach this.

---

### Post by cerixon on 2012-05-26
should i reformat my hard drive and begin again??

---

### Post by wilee-nilee on 2012-05-26
> **cerixon said:**
> should i reformat my hard drive and begin again??

No I think you're okay I just see a raid indicator on the sda hd and it is not showing up on the script as I would think it should, I don't think a reinstall will fix this, it probably just needs to be dealt with in a specific way. 

You can get into windows as of now so if you can hang for another's help you will probably be set.

I just try to be really careful with this stuff, so if I see something I'm not real sure on I stop and refer to another user more likely to get you the help to take care of it. :)

---

### Post by cerixon on 2012-05-26
Thanks for trying to help,  I do have my Laptop so i am not lost yet, lol.  I use Windows for Netflix only.

---

### Post by darkod on 2012-05-27
Do you have your problem on a desktop or on a laptop? I see in your fdisk results that you have two disks, and laptops usually have only one.

You see that /dev/mapper device in the fdisk results? That means raid meta data info on the disk. That 500GB disk was used in raid earlier and the meta data is not yet removed. Windows ignores this but ubuntu doesn't and it's confused whether the disk is part of raid array or not.

Since it seems you are not running raid, because there is only one 500GB disk, not two, boot again with the ubuntu cd in live mode and do:
```
sudo dmraid -E -r /dev/sda
```

Confirm to remove the meta data. NOTE: Do this only if you are not running a raid array!

After that install grub2 to /dev/sdb with:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Restart and set the 320GB disk to be first hdd option to boot from, you should see the grub2 boot menu.

---

### Post by cerixon on 2012-05-27
:D  Thank you Darko;  I followed your instruction to the letter and "Viola!!!!"  i saw that wonderful color or purple and the screen that request if i want to select Ubuntu or Windows.

Thanks a million, 
cerixon

---

### Post by darkod on 2012-05-27
No problem.

Please mark the thread as Solved. You can do this in Thread Tools above the first post.

---

