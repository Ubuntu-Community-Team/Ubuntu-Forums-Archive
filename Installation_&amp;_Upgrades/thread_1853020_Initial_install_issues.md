---
title: "Initial install issues"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by sasjzl on 2011-10-01
Hi all,

This is my first post and I was able to install and see Ubuntu running a few times and it looked very cool but
now I cannot boot up into it.  Tell me what other information I need to give in addition to the below.

MY NARRATION:
I have just installed Ubuntu from a flash drive and it came up fine 3 or 4 times.
Now it gets started and stops with this line:
(initramfs)  Can not mount /dev/loop1 on /cow

It shows me the correct syntax for the mount command and I have tried alot of things but none have worked.

I Hit Enter then it goes to the prompt only as below:
(initramfs)  

From here the only thing I can think of that does anything is to type in 'exit'.
It keeps churning and I see an i/o message for a moment that I have written down to the best of my memory below:
End_Request  i/o error on disk fao

Next thing I see is 
[  260.xxxx panic occurred.  Switching back to text console 

Then I see the lights on my keyboard blinking quickly and that is all she wrote.

I am going to try installing it on a CD.

Thanks very much,
Jim Lee

---

### Post by Mark Phelps on 2011-10-01
> **sasjzl said:**
> I am going to try installing it on a CD.

You mean FROM a CD, right?  You can't install TO a CD.

---

### Post by sasjzl on 2011-10-03
Right.  From a cd.  

But I have made some progress.  I was able to install from a USB drive but my only and Ubuntu comes up consistently but when it starts up I have to choose to run it from the same USB thumb drive.  If I pull the USB drive out it will not start up.

The sequence of events, very roughly, was a two part deal where I first bought up Ubuntu and then clicked on the icon to install to my hard drive.  It ran about a 10 minute install and I told it to partition the disk which it did without complaint.  So it spent all that time writing to the hard drive but for some reason it still needs the USB drive to be in there to run.

Thanks very much,
Jim Lee

---

### Post by presence1960 on 2011-10-03
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by sasjzl on 2011-10-03
Thanks so much.  This is an incredibly responsive community.  I am coming from Windows World where everyone sort of looks the same.

I was able to boot up without the thumb drive inserted but I am going to study the Results.txt file very carefully.  Is all that code Ubuntu specific?

I see this line which I assume is for my Windows Wine stuff.   

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP WINDOWS" /fastdetect /NoExecute=OptIn

I ended up installing Ubuntu after hearing a passing reference to it in a YouTube video.  I was replacing a hard drive and in the midst of my struggle to get Windows reinstalled (don't ask) I thought I would try this.

It is very, very nice.  The support is even nicer.

I am very impressed with how Windows like this is.  All the good without the bad it looks like.

Thanks very much,
Jim Lee :smile:
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   238,043,135   238,041,088  83 Linux
/dev/sda2         238,045,182   240,119,807     2,074,626   5 Extended
/dev/sda5         238,045,184   240,119,807     2,074,624  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ff3449cb-2b6b-4e21-9daf-b5162b54387f   ext4       
/dev/sda5        2b9b9012-8bf5-4250-81f8-8945fc29f299   swap       
/dev/sdb1        AC60437E60434DF0                       ntfs       FreeAgent Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/Quicken 2011      iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff3449cb-2b6b-4e21-9daf-b5162b54387f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff3449cb-2b6b-4e21-9daf-b5162b54387f
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ff3449cb-2b6b-4e21-9daf-b5162b54387f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ff3449cb-2b6b-4e21-9daf-b5162b54387f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ff3449cb-2b6b-4e21-9daf-b5162b54387f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ff3449cb-2b6b-4e21-9daf-b5162b54387f ro single 
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ff3449cb-2b6b-4e21-9daf-b5162b54387f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ff3449cb-2b6b-4e21-9daf-b5162b54387f
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2b9b9012-8bf5-4250-81f8-8945fc29f299 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.135009766 = 23.767285760   boot/grub/core.img                             1
  22.135017395 = 23.767293952   boot/grub/grub.cfg                             1
   0.922851562 = 0.990904320    boot/initrd.img-2.6.38-8-generic               2
  22.133281708 = 23.765430272   boot/vmlinuz-2.6.38-8-generic                  1
   0.922851562 = 0.990904320    initrd.img                                     2
  22.133281708 = 23.765430272   vmlinuz                                        1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[Boot Loader] 
Timeout=10 
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[Operating Systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP WINDOWS" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  31 21 15 00 02 00 00 10  8f 89 02 0c 07 91 12 9b  |1!..............|
00000010  d1 07 58 4d b1 9c 55 81  36 21 91 0d 58 91 a6 d8  |..XM..U.6!..X...|
00000020  c0 92 67 5f 82 f0 47 14  d3 29 e5 57 6f 69 c0 ed  |..g_..G..).Woi..|
00000030  8d 29 47 ee 38 1e aa 8c  69 c3 c6 b1 92 77 1c 13  |.)G.8...i....w..|
00000040  a4 ce 47 e7 a4 57 28 7d  07 ca f3 79 be 97 e7 9a  |..G..W(}...y....|
00000050  4c 6a f7 ab c1 09 42 b7  46 81 9a 2b 8d 24 39 28  |Lj....B.F..+.$9(|
00000060  2c 5b 19 c7 16 b9 e2 9c  32 0e c3 e3 9b 63 1a 38  |,[......2....c.8|
00000070  92 93 94 32 9e 37 92 5c  8b 10 c8 83 47 12 50 e3  |...2.7.\....G.P.|
00000080  e7 3c 6b 37 63 c1 15 84  5b 28 96 08 7c 00 c4 71  |.<k7c...[(..|..q|
00000090  00 00 d3 55 54 02 f1 2b  0b 49 d9 31 23 15 00 01  |...UT..+.I.1#...|
000000a0  45 00 10 a1 89 02 70 13  91 14 9d d1 1a c3 21 1c  |E.....p.......!.|
000000b0  c7 7a 3e 24 6e e3 e8 92  50 23 98 ef 4a 50 92 77  |.z>$n...P#..JP.w|
000000c0  74 82 f0 47 14 d3 29 d1  e2 9e 3c 90 3e 28 bf b5  |t..G..)...<.>(..|
000000d0  f0 f7 1d 73 6b 21 d6 f5  c7 91 bb 8f 1c e9 4e 73  |...sk!........Ns|
000000e0  c7 1e 33 93 24 55 a1 16  ca 1f 41 f2 bc de 6f 37  |..3.$U....A...o7|
000000f0  cf 34 94 7f 16 17 63 02  c6 09 68 4d b1 8e 4b 0b  |.4....c...hM..K.|
00000100  d2 86 88 d6 19 3c 49 28  22 b1 08 f8 98 f1 3b 42  |.....<I(".....;B|
00000110  42 a6 24 6c 68 45 87 33  3e 19 d3 9c 8e 62 0b 1a  |B.$lhE.3>....b..|
00000120  f1 d1 30 bf b5 16 44 32  3c 04 75 a4 d1 4b ce 58  |..0...D2<.u..K.X|
00000130  d5 ec 97 32 4f 0e 50 96  08 7c 00 63 65 40 00 c9  |...2O.P..|.ce@..|
00000140  58 54 02 f1 90 9d 07 ef  1e 93 f2 c9 00 dc f7 00  |XT..............|
00000150  00 00 0b 10 04 00 a4 7e  ed d9 31 17 30 00 01 30  |.......~..1.0..0|
00000160  00 10 a7 89 02 b2 03 91  0b 8f dd 17 bc 88 44 dd  |..............D.|
00000170  3b 64 49 00 92 70 68 82  f0 47 14 d3 29 ba 32 43  |;dI..ph..G..).2C|
00000180  c1 6f 24 7c 4e dd c6 e8  f1 a2 c0 f2 c5 65 04 5e  |.o$|N........e.^|
00000190  e3 e8 e7 80 e9 75 bd 53  28 7d 07 ca f3 79 bd 7f  |.....u.S(}...y..|
000001a0  3c d2 c5 5a 56 5a e0 ad  23 59 12 82 cf 06 04 51  |<..ZVZ..#Y.....Q|
000001b0  da e3 96 8b 18 5d 8f 16  48 98 e2 92 22 c6 00 fe  |.....]..H..."...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 1f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by Blasphemist on 2011-10-03
Is it possible your boot order in bios has the usb first? The grub boot loader is installed to the mbr of sda and the files it needs for the next stage seem to be where they should be. If is still failing to boot when the usb is not connected, is it a different error and/or prompt than in the first post?

---

