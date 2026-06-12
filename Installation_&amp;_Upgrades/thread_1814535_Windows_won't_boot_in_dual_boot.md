---
title: "Windows won't boot in dual boot"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by Jo22 on 2011-07-29
I hope this isn't too long, but I need to explain my whole situation.

I installed Ubuntu on my older laptop, running Windows XP last night.  After using Ubuntu for a bit, I decided to take it off my system.  I read how to do it, deleted Ubuntu from Windows disk management and had what I thought was my Windows XP dics ready so I could use the recovery console and use command fixmbr.  Well it turns out I have OEM discs, and it wouldn't go to recovery console for nothing.  I tried loading a Windows XP iso file, but no matter how many times I tried loading it on my flash drive my laptop would never boot.  It kept giving me a grub command prompt, something like grub error, or grub recover, but I could never do anything there.  So I decided I would just install Ubuntu again so I could at least access Windows & Ubuntu and try to make a recovery disc that would work.  I've reinstalled Ubuntu, this time it didn't ask for partition sizes because I had never gotten as far as getting rid of the partitions, just Ubuntu.  I have Ubuntu up and running, and I think I'll use it for a while.  Second time around and I'm starting to like it a bit more.  But I still need Windows access for some schooling programs that don't run on Ubuntu.  After I got Ubuntu set up, I rebooted my system and picked the Windows option of the dual boot menu.  Well this time it didn't go into windows, it when into the OEM recovery mode (which is different than the recovery console).  For the OEM recovery mode my only options are to reinstall Windows and completely format my hard drive.  Or re-install windows with a back up of everything on my hard drive.  Obviously I don't want to do either of those two options.  What did I do wrong that now when I try to boot into Windows it wants to go to OEM recovery?  Any help or suggestions would be greatly appreciated.  Thanks.

JoAnn

---

### Post by Quackers on 2011-07-29
Welcome to UF.
At the grub menu how many boot options are you given to choose from?
What are they?
Which one are you trying to boot Windows from?

---

### Post by Jo22 on 2011-07-29
I have 5 options on the dual boot, they look exactly the same as when I loaded it last night.  I don't remember the exact names, but there were two for Ubuntu, two memory ones and two for Windows.  One of the Ubuntu ones was a recovery mode, and the two Windows ones I used the first one.  I read in another thread about running a Boot info script, so I ran that, does that help?  Otherwise I can reboot my system and write down the exact names on the dual boot menu.

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    12,289,724    12,289,662   b W95 FAT32
/dev/sda2          12,289,725    60,033,630    47,743,906   7 NTFS / exFAT / HPFS
/dev/sda3          60,035,070    78,139,391    18,104,322   5 Extended
/dev/sda5          60,035,072    77,111,295    17,076,224  83 Linux
/dev/sda6          77,113,344    78,139,391     1,026,048  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6A5F-1690                              vfat       RECOVERY
/dev/sda2        205C79265C78F7BC                       ntfs       
/dev/sda5        dd47a20b-ff95-400f-91f9-22e790ed0e76   ext4       
/dev/sda6        559c272d-96d5-42a7-8e2a-791f9de0e5ca   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root dd47a20b-ff95-400f-91f9-22e790ed0e76
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root dd47a20b-ff95-400f-91f9-22e790ed0e76
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root dd47a20b-ff95-400f-91f9-22e790ed0e76
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=dd47a20b-ff95-400f-91f9-22e790ed0e76 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root dd47a20b-ff95-400f-91f9-22e790ed0e76
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=dd47a20b-ff95-400f-91f9-22e790ed0e76 ro single 
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root dd47a20b-ff95-400f-91f9-22e790ed0e76
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root dd47a20b-ff95-400f-91f9-22e790ed0e76
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a5f-1690
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 205C79265C78F7BC
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=dd47a20b-ff95-400f-91f9-22e790ed0e76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=559c272d-96d5-42a7-8e2a-791f9de0e5ca none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  30.985595703 = 33.270530048   boot/grub/core.img                             1
  28.856407166 = 30.984331264   boot/grub/grub.cfg                             1
  35.041015625 = 37.625004032   boot/initrd.img-2.6.38-8-generic               2
  30.983970642 = 33.268785152   boot/vmlinuz-2.6.38-8-generic                  1
  35.041015625 = 37.625004032   initrd.img                                     2
  30.983970642 = 33.268785152   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 22 00  |...RECOVERY...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  78 86 bb 00 cb 2e 00 00  00 00 00 00 02 00 00 00  |x...............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 90 16 5f 6a 20  20 20 20 20 20 20 20 20  |..).._j         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  cc 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 53 54 4c 44 52 20 20  |.f..f.F..STLDR  |
000001b0  20 20 20 20 0d 0a 49 6e  76 61 6c 69 64 20 53 79  |    ..Invalid Sy|
000001c0  73 74 65 6d 20 44 69 73  6b 20 6f 72 0d 0a 44 69  |stem Disk or..Di|
000001d0  73 6b 20 49 2f 4f 20 65  72 72 6f 72 0d 0a 50 72  |sk I/O error..Pr|
000001e0  65 73 73 20 61 20 6b 65  79 20 74 6f 20 72 65 73  |ess a key to res|
000001f0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 55 aa  |tart..........U.|
00000200

Unknown BootLoader on sda3

00000000  0f 02 01 0f 80 06 18 36  df e0 01 60 2b 32 00 01  |.......6...`+2..|
00000010  08 02 0e 00 02 5a 14 80  01 2c 80 01 01 01 0b 00  |.....Z...,......|
00000020  02 44 00 79 6e 61 6d 69  63 20 44 94 53 54 01 09  |.D.ynamic D.ST..|
00000030  00 83 57 04 00 81 11 60  a8 31 df 01 03 80 0a 01  |..W....`.1......|
00000040  32 32 d8 30 30 39 01 10  81 57 88 00 28 81 05 02  |22.009...W..(...|
00000050  c4 82 03 0a 00 06 00 05  00 68 17 00 3b 80 00 e7  |.........h..;...|
00000060  00 17 81 18 05 0b 01 0f  82 01 f8 80 11 68 40 df  |.............h@.|
00000070  01 c9 89 2b 00 32 89 2b  31 30 01 14 a1 2b ab c9  |...+.2.+10...+..|
00000080  19 c9 13 50 cb 13 31 fd  13 a0 cb 13 b5 81 94 00  |...P..1.........|
00000090  e3 27 04 c6 41 c9 27 f0  cb 13 52 33 fd 27 40 33  |.'..A.'...R3.'@3|
000000a0  ca 4f 34 fd 13 58 02 34  c5 13 df 01 32 30 31 37  |.O4..X.4....2017|
000000b0  d6 90 c0 17 c9 2f b0 cb  1b 35 d7 1b c7 3f 58 00  |...../...5...?X.|
000000c0  00 03 ca 85 c9 13 00 c6  1b 00 4a 00 c0 1b 36 fd  |..........J...6.|
000000d0  2f 08 35 ea 17 39 c3 e1  17 e1 4e c8 3f df 01 ff  |/.5..9....N.?...|
000000e0  36 f7 14 9a a8 eb 14 38  ff 14 e3 5f 06 00 f3 40  |6......8..._...@|
000000f0  32 c0 ea 14 32 31 e1 14  e1 85 6c 68 00 01 00 48  |2...21....lh...H|
00000100  3b df 01 61 26 6c b7 29  ff 15 f7 15 58 e6 0b e1  |;..a&l.)....X...|
00000110  2a 32 07 f8 6a f7 34 e5  a8 04 00 00 80 e5 04 07  |*2..j.4.........|
00000120  00 20 19 00 00 01 00 df  00 01 4c 61 73 74 45 6e  |. ........LastEn|
00000130  74 34 72 79 60 41 70 60  00 e1 16 00 f5 08 f7 01  |t4ry`Ap`........|
00000140  30 60 00 68 08 70 b3 97  ff 16 eb 16 e3 0c 0a e1  |0`.h.p..........|
00000150  0b 80 d9 e6 0c 60 00 00  46 69 72 04 0d a1 2d 00  |.....`..Fir...-.|
00000160  54 00 c0 e0 87 88 e0 90  e0 60 00 30 d5 e0 68 80  |T........`.0..h.|
00000170  60 00 d0 60 00 20 60 10  e1 27 56 e0 e0 00 e1 11  |`..`. `..'V.....|
00000180  88 60 35 30 60 00 38 d5  60 20 d8 e0 00 f0 e0 00  |.`50`.8.` ......|
00000190  88 60 00 e5 a5 88 86 4f  83 e6 a5 60 6d 9e 83 0b  |.`.....O...`m...|
000001a0  8f a0 00 c0 0b 42 00 21  96 b0 74 de ff a5 bd f8  |.....B.!..t.....|
000001b0  a5 d8 e0 ad a1 9f e4 a5  e6 64 2c 01 02 9f 00 fe  |.........d,.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 04 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff c2 92  04 01 40 ad 0f 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by Jo22 on 2011-07-29
I replied, but didn't reply directly to you, sorry.  New here, trying to get use to how it works.  :)

---

### Post by Quackers on 2011-07-29
The second Windows entry (ending in /dev/sda2) should boot the normal Windows system.
The first entry is supposed to boot the recovery partition.

---

### Post by Jo22 on 2011-07-29
Really?  I used the first one last night and it ran fine.  But I will try it.  Thanks.

---

### Post by Jo22 on 2011-07-29
I tried the 2nd one like you said and I got the following error message:

Windows could not start because the following file is missing or corrupt:

<Windows root>\system32\hal.dll

Please re-install a copy of the above file.

---

### Post by madjr on 2011-07-29
hello, i suggest that next time if you want to "test" ubuntu in your computer and you know you wont use it permanently for now, is better to install it via **Wubi**, its easier and faster for quick tests.

anyway i hope you can solve your issue.

> <Windows root>\system32\hal.dll

Please re-install a copy of the above file.

i think you could get a copy of that dll online.

but always backup your important stuff first with the ubuntu live-cd.

---

### Post by Jo22 on 2011-07-29
I tried downloading and install a new hal.dll file and it still doesn't work.  Any other suggestions anyone?

---

### Post by madjr on 2011-07-29
> **Jo22 said:**
> I tried downloading and install a new hal.dll file and it still doesn't work.  Any other suggestions anyone?


this might help:

[http://forums.techguy.org/windows-xp/553625-windows-root-system32-hal-dll-2.html](http://forums.techguy.org/windows-xp/553625-windows-root-system32-hal-dll-2.html)

it happened to me once years back (when i didnt even had linux), windows is super fragile and usually hard to fix as you know...

it can be a lengthy process and may not work, so keep cd handy in case you need to reinstalling.

also, as i mentioned before, get the ubuntu live-cd , boot to the live desktop, access your drive and backup your important files, prior to continuing..

good luck

---

### Post by bcbc on 2011-07-29
Your /dev/sda2 boot.ini looks like this:
> [boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
This is suggesting that it should go to /dev/sda1 and boot whatever is on there. But /dev/sda1 is labelled your recovery partition - and also there's no windows boot sector, and no boot.ini. Interestingly /dev/sda1 also has the boot flag set - which is unusual for a recovery partition.

That hal.dll error can mean a lot of things - even just a typo in boot.ini. So not sure what has happened here.

This is what one of my machines looks like:
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Based on that I'd suggest you edit the one on /dev/sda2 and try this (first back it up):

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
```

PS if that works I'd recommend setting the boot flag to /dev/sda2 as well.

---

### Post by Jo22 on 2011-07-30
Thanks for your thoughts.  I did edit the boot.ini to try that yesterday and I stopped get the hal.dll error and started getting load needed DLL's for kernal.  Not sure how to address that one.

---

### Post by bcbc on 2011-07-30
> **Jo22 said:**
> Thanks for your thoughts.  I did edit the boot.ini to try that yesterday and I stopped get the hal.dll error and started getting load needed DLL's for kernal.  Not sure how to address that one.

If you have specific error text it might help to narrow it down - however, this is getting into Windows only territory. I'm not sure what could have caused this problem - except maybe when you selected to boot the recovery partition. Ubuntu doesn't mess with these things - but grub sometimes does a poor job distinguishing between the actual windows and the recovery partition.

---

### Post by Jo22 on 2011-07-30
What's weird is I can get the error message to change for not finding or corrupt HAL.DLL file to not being able to find any DLL kernal files if I change the number for the partition in boot.ini.  That's why I don't think there is really and error, I just think I don't have it pointing where it needs to go.  But at this point I'm leaning towards win xp just reformating the whole system.  Not my first choice, but not sure how else to solve this.

---

### Post by bcbc on 2011-07-30
> **Jo22 said:**
> What's weird is I can get the error message to change for not finding or corrupt HAL.DLL file to not being able to find any DLL kernal files if I change the number for the partition in boot.ini.  That's why I don't think there is really and error, I just think I don't have it pointing where it needs to go.  But at this point I'm leaning towards win xp just reformating the whole system.  Not my first choice, but not sure how else to solve this.

Try this first: [http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184)

---

### Post by Jo22 on 2011-07-30
That's my original problem.  See when I first originally deleted Ubuntu, thinking I could put my Windows XP disc in, run the recovery console and I could get the windows MBR back, it wasn't mentioned that it only works with Original Windows XP discs, not the OEM discs that came with my Gateway.  So the only thing my OEM Windows discs want to do is format my hard drive.  I've been searching for a way to make a recovery disc, through Ubuntu (since that's working) so I could get to that point of being able to boot from it and get the recovery console, but everything I've read says I have to run something in Windows to make the cd's.  No help since I can get to Windows files through Ubuntu but I can't run windows.  I even tried making an Win XP iso (downloaded from online) to install like I did with Ubuntu, but I can't get it to work on my flash drive.  Wintoflash won't put it on there saying it's not the right files, and UNetbootini puts me in a loop of saying it wants to pick default but never does anything.

This is why I think I am at my last string.  I had studied this before installing Ubuntu on dual boot, if only what I had read would have specified OEM discs won't work.  I have since found that, but my original search and studying of it never said that.  Thanks for all your help.

---

### Post by bcbc on 2011-07-30
Maybe your oem disks are just a system image restore, not the actual OS disk. I think it's pretty ridiculous you can't get an install DVD when you buy a computer.  

Maybe you can find someone to lend you a windows xp dvd? There must be a gazillion copies out there in the bozonosphere.

---

### Post by Jo22 on 2011-07-30
I know, I hate that I don't get original discs anymore.  I don't think I know anyone who still runs XP, but I will have to think about it.  Thanks.

---

### Post by madjr on 2011-07-30
> **Jo22 said:**
> I know, I hate that I don't get original discs anymore.  I don't think I know anyone who still runs XP, but I will have to think about it.  Thanks.

yeah totally feel you, i've been in that situation when you plan something and there's always that 1 darn detail... :/

anyway, what programs you need specific to XP ?

maybe if ubuntu is working for you, you could get most of those running in ubuntu with Wine or they might have a substitute.

you can check alternatives here:
[http://alternativeto.net/software/?profile=linux](http://alternativeto.net/software/?profile=linux)
[http://www.osalt.com/](http://www.osalt.com/)

and tons of guides and apps here:
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)
[http://www.webupd8.org/](http://www.webupd8.org/)

in case there arent then i would lean to reinstalling xp, but having ubuntu (or another ubuntu spin) in my second partition has always been of benefit to me.

---

### Post by Jo22 on 2011-07-30
Well the two main programs are for my children's schooling (we homeschool), it's their math & spelling program, there's no alternatives.  But I might see if I can get them to work with Wine.  That's my biggest 'ugh', I do want to keep using Ubuntu, because after all of this, now that I know my way around Ubuntu, I do like it.  But with those two programs, and family members that still like Windows, I need both.  So I will go through this whole formatting thing, and then just partition it again.  But first I will figure out how to make the discs I need so I won't go through this again.  Just need to search on how to make non-OEM discs from XP.

Thanks for those links though.  I am going to check them out and see what other software is on there.  :)

---

### Post by oldfred on 2011-07-30
Do you have any other XP full install disks? Any XP disk should be able to run the repair console.

---

### Post by Jo22 on 2011-07-30
Nope the only XP discs I recieved with my system is OEM discs, and all they want to do is go into Gateway recovery mode which only gives the option of formatting the hard drive.  It won't go into recovery console mode from the discs I have.  Which is the problem.

---

