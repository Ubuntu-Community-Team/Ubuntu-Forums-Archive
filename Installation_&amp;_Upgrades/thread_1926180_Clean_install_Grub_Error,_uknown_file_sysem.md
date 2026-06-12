---
title: "Clean install Grub Error, uknown file sysem"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by Paradox13 on 2012-02-15
As the title states I have gone ahead and done a clean install version of Ubuntu 11.10(64bit) on my secondary hard drive. My first hard drive currently has windows vista 32 bit installed on it and when I go to boot my vista(32bit) OS I receive an error message that some of you may be familiar with "GRUB error; unknown filesystem, grub rescue" I have searched for several solutions to fix this problem but no luck on resolving it. I would like to say that when I installed the Ubuntu I did leave my Vista HD unplugged so am now wondering if this may have caused the problem I have now when trying to boot windows vista. Also I am not given a selection on what OS to boot from as I must manually go into the bios to boot from whichever OS I wish to run. But given the error can only boot ubuntu and not vista. Any information on fixing this error would be greatly appreciated As I would like to not wipe my windows HD with my original files on it and re-install.

---

### Post by Paradox13 on 2012-02-15
Boot Info script Results


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   640,561,177   640,561,115   7 NTFS / exFAT / HPFS
/dev/sda2         640,563,198   976,771,071   336,207,874   5 Extended
/dev/sda5         968,388,608   976,771,071     8,382,464  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   616,755,199   616,753,152  83 Linux
/dev/sdb2         616,757,246   625,141,759     8,384,514   5 Extended
/dev/sdb5         616,757,248   625,141,759     8,384,512  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        581493B014938F9C                       ntfs       
/dev/sda5        31c245f1-6a99-48e7-b3a5-8df61603333d   swap       
/dev/sdb1        63964119-3be2-479c-be9b-1a5a06d9e0c7   ext4       
/dev/sdb5        f7bd74d6-23ad-494b-a392-92c6d2a363fa   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=63964119-3be2-479c-be9b-1a5a06d9e0c7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=63964119-3be2-479c-be9b-1a5a06d9e0c7 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=63964119-3be2-479c-be9b-1a5a06d9e0c7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=63964119-3be2-479c-be9b-1a5a06d9e0c7 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 63964119-3be2-479c-be9b-1a5a06d9e0c7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=63964119-3be2-479c-be9b-1a5a06d9e0c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f7bd74d6-23ad-494b-a392-92c6d2a363fa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  6d c7 99 65 ea 6d 7f b5  c3 d1 45 e9 48 5f 37 cb  |m..e.m....E.H_7.|
00000010  d0 d0 34 00 00 00 19 b7  62 1c 22 e8 75 8f e2 04  |..4.....b.".u...|
00000020  a2 67 27 30 dc 94 91 5a  10 86 c7 09 18 6a 68 b1  |.g'0...Z.....jh.|
00000030  81 2a 46 04 a3 44 c4 63  73 1e 0b 13 8d 08 18 06  |.*F..D.cs.......|
00000040  16 42 38 68 9d 92 66 13  34 4c 55 24 30 9c c8 20  |.B8h..f.4LU$0.. |
00000050  59 16 25 2d 35 73 38 90  60 aa d0 a8 c9 7d a7 7b  |Y.%-5s8.`....}.{|
00000060  87 fb b9 ff de 6d a0 c8  41 0b 29 e1 28 c4 b9 5a  |.....m..A.).(..Z|
00000070  81 52 c1 5d e6 c3 a8 b0  da 45 21 a3 aa 18 af dc  |.R.].....E!.....|
00000080  1d 75 16 e8 d9 b3 06 c4  55 59 30 e2 14 03 48 58  |.u......UY0...HX|
00000090  b2 d7 20 00 00 0a 97 a0  08 2d 74 04 b3 b4 f1 78  |.. ......-t....x|
000000a0  9d 40 b0 44 49 80 d9 aa  b9 87 1c 95 fc 38 06 83  |.@.DI........8..|
000000b0  05 b9 2c b9 e8 7a 20 e7  f1 bb 4f 4e 4d 4a e3 0f  |..,..z ...ONMJ..|
000000c0  ab 8c f9 be cc 8a 1e 70  e1 c7 a9 51 44 db ab f9  |.......p...QD...|
000000d0  13 84 a0 8d d4 07 29 47  e5 31 50 e5 82 a3 e7 63  |......)G.1P....c|
000000e0  a1 e3 67 70 c6 53 44 bd  6a a2 49 dd 56 3f 55 29  |..gp.SD.j.I.V?U)|
000000f0  55 2b 64 bc f7 fb 97 bd  de 3a 6d 8f ad ff fb a0  |U+d......:m.....|
00000100  64 35 86 05 6b 60 d8 3b  0c 36 42 5b 09 db 6a 3d  |d5..k`.;.6B[..j=|
00000110  22 6e 14 29 97 60 6c 30  d8 89 8d a7 2d 1c f4 89  |"n.).`l0....-...|
00000120  f8 6c fc 6e 7b f4 8a a6  94 79 f5 ed 1d 3f 3d 4b  |.l.n{....y...?=K|
00000130  da 1e a2 c9 8b 45 22 3f  b4 9b a8 c9 70 d2 88 95  |.....E"?....p...|
00000140  98 89 d2 f9 85 9b b4 53  85 ae 08 51 87 dd db dc  |.......S...Q....|
00000150  c3 f3 32 39 a1 b2 0e d6  fb 3f 5f 31 09 3a a5 da  |..29.....?_1.:..|
00000160  ff a7 a1 00 c0 80 00 00  52 fd 44 2d 3c d0 4d 1b  |........R.D-<.M.|
00000170  cc 96 36 06 bc 43 ee 27  19 0a 05 e1 af 24 89 93  |..6..C.'.....$..|
00000180  9e 8d a3 21 79 03 62 67  ca 72 ec e2 38 c9 04 18  |...!y.bg.r..8...|
00000190  fb e3 74 dc e6 7f 71 98  c6 d9 ac 91 58 87 74 65  |..t...q.....X.te|
000001a0  50 b9 ba 1a 8c 89 d2 c8  9a 3e f6 56 bb bd bd 6e  |P........>.V...n|
000001b0  db 6a a8 bf dd 1e d2 b5  51 d0 b4 02 ea fd 00 fe  |.j......Q.......|
000001c0  ff ff 82 fe ff ff 02 38  8a 13 00 e8 7f 00 00 00  |.......8........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by mikewhatever on 2012-02-15
Since you've had the Vista hdd unplugged when installing Ubuntu, Vista has not been detected. Try running **sudo update-grub** . That should find Vista.

PS: What I find odd is that Grub is in the MBRs of both HHDs. How did that happen?

---

### Post by Paradox13 on 2012-02-15
> **mikewhatever said:**
> Since you've had the Vista hdd unplugged when installing Ubuntu, Vista has not been detected. Try running **sudo update-grub** . That should find Vista.

PS: What I find odd is that Grub is in the MBRs of both HHDs. How did that happen?

Thank you for resolving my problem that I had as the information you provided me worked GREAT!!! As for the Grub being in both, well I tried using "Unetbootin" which may have created the file on my HD before I attempted a clean install.

---

### Post by mikewhatever on 2012-02-15
Glad it helped.

---

### Post by mbuell on 2012-02-16
While you have resolved your problem - so this thread is SOLVED :)  -- another one bites the dust! -- there is another aspect of this problem that is worth mentioning. Your title says "unknown file system", and there is another error that can occur that results in a similar message when using Grub to load the Windows installation. I think it likely that people will find this thread when looking to resolve such a problem. I'm adding this for them.

After grub passes control to Windows, at least in XP and earlier, Windows has references to the partition location for the Windows installation. In XP at least, I think this is in boot.ini. I tried to find my related post, and failed, or I would have just put the link to it here. If that file refers the wrong partition for Windows - Windows won't boot. It dumps you out to a black screen with errors such as "corrupt or missing boot.ini" or messages about problems with the file system. The error messages lead you in the wrong direction for fixing the problem. 

I believe I saw that Vista and 7, can have a similar problem, but with different files, since they don't use boot.ini any more. 

The essence of the problem is that grub passes command to the Windows loader, which in turn starts looking for files. When the file it looks to for direction on where to find those files is wrong - Windows then looks at the wrong partition - and the load fails. Fixing the problem for XP is a simple text file edit of boot.ini to correct the partition number. 

Although you also have to figure out which partition Windows will see as the "correct" partition number. That is actually the hardest part of the task. The only way to do that, that I know of, is to act like you are going to do a reinstall of windows with a setup CD. At some point it says "here, I found an NTFS file system on partition #x - do you want to install there?" At which point you make note of what partition it called it, and exit the Win install.

---

