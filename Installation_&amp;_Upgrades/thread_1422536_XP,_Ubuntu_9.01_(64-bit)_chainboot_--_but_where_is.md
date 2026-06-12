---
title: "XP, Ubuntu 9.01 (64-bit) chainboot -- but where is the slave boot record?"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Erwacht on 2010-03-05
Hello, everybody.

I'm installing Ubuntu 9.10 on a new (2009) Dell Windows XP machine and trying to leave the Windows bootloader in charge.

To be honest, I found the technique here: 
[http://jamesmcdonald.id.au/gnu-linux/linux-tools/shrink-your-windows-xp-ntfs-partition-to-half-size-and-install-linux-while-keeping-the-nt-bootloader](http://jamesmcdonald.id.au/gnu-linux/linux-tools/shrink-your-windows-xp-ntfs-partition-to-half-size-and-install-linux-while-keeping-the-nt-bootloader)

And when it didn't work (as I shall describe shortly), I went hunting for answers and found this forum because of this message:
[http://ubuntuforums.org/showpost.php?p=8339045&postcount=2](http://ubuntuforums.org/showpost.php?p=8339045&postcount=2)
which describes the same procedure.

So, here's what I did. I shrunk my NTFS partition (with GParted). I let Windows boot two or three times for stability and consistency. I checked the C drive for consistency, then installed Ubuntu. For me, the new Linux partition is /dev/sda5, with the swap partition being /dev/sda6. I used the advanced option to install GRUB on /dev/sda5 rather than over the MBR. I dd'd the first 512 bytes of /dev/sda5. I went into Windows and placed the file in C:\ and edited the boot.ini file.

When it was done, I had an Ubuntu entry in the Windows alternative boot menu. Using it went to an upper-left-hand blinking cursor on a blank screen. (Neat trick, huh?)

Checking the 512 byte file I was using in C:\, it is all 00's.

Where did I go wrong?

I even went back and tried copying the 512 bytes from /dev/sda3 instead, being the "Extended" partition (and the only one for which the first 512 bytes aren't completely null).

Where can I get the right 512 bytes?

Oh, and here's all the technical information:

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa42d04a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   751,488,569   751,392,180   7 HPFS/NTFS
/dev/sda3         751,488,570   976,768,064   225,279,495   5 Extended
/dev/sda5         751,488,633   967,530,689   216,042,057  83 Linux
/dev/sda6         967,530,753   976,768,064     9,237,312  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,915,775     3,915,744   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D9-070A                              vfat       DellUtility                   
/dev/sda2        62ECFD32ECFD0159                       ntfs       OS                            
/dev/sda5        d6c1c06d-842d-4a27-ad9b-685655574cce   ext4                                     
/dev/sda6        0d4a7623-c872-4ddb-9a84-bd59adf21c61   swap                                     
/dev/sdb1        C2F8-E4F2                              vfat       Lexar                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/Lexar             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ubuntu91.bin="Ubuntu 9.01 Desktop 64-bit"

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set d6c1c06d-842d-4a27-ad9b-685655574cce
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d6c1c06d-842d-4a27-ad9b-685655574cce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d6c1c06d-842d-4a27-ad9b-685655574cce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d6c1c06d-842d-4a27-ad9b-685655574cce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d6c1c06d-842d-4a27-ad9b-685655574cce ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 62ecfd32ecfd0159
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d6c1c06d-842d-4a27-ad9b-685655574cce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0d4a7623-c872-4ddb-9a84-bd59adf21c61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 387.6GB: boot/grub/core.img
 387.6GB: boot/grub/grub.cfg
 385.3GB: boot/initrd.img-2.6.31-14-generic
 385.3GB: boot/vmlinuz-2.6.31-14-generic
 385.3GB: initrd.img
 385.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 3c 90 28 37 7a 3e 7d  49 48 43 00 02 40 02 00  |.<.(7z>}IHC..@..|
00000010  02 00 02 00 00 f8 ef 00  20 00 80 00 20 00 00 00  |........ ... ...|
00000020  e0 bf 3b 00 00 00 29 f2  e4 f8 c2 4e 4f 20 4e 41  |..;...)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200
```

Thanks,

Erwacht

---

### Post by stlsaint on 2010-03-05
Is there a particular reason you wish to leave windows mbr over grub. Windows cannot read linux filesystems thus you take a risk of messing up your system. Grub reads windows very well and has ALOT more features that are easier to customize over windows bootloader.

---

### Post by oldfred on 2010-03-05
Grub2 does not like to be installed to the partition. It looks like you did not install it as the script would show it as would your dd file. 

If you do not want to mess with your windows boot you could put grub on sdb. I prefer to have each operating system on a separate drive and that boot loader installed in the MBR of that drive. I use Ubuntu/grub to boot but the windows drive is still bootable if selected in BIOS.

---

### Post by Erwacht on 2010-03-05
Hey, thanks. That sdb, by the way, is the thumb drive I was using to save stuff to while running Ubuntu off the live CD. Yes, I know I could have written to the NTFS partition, but I didn't want to touch it from Linux during the process, until it was all done. It took enough courage as it was to shrink a partition and risk having to restore it!

I will delete the new Ubuntu installation and partitions, install it again in the same disk space, and make sure to install GRUB while I have the new installation running the first time ... unless someone knows a way to use the Live CD to boot the unreachable hdd installation?

Erwacht

---

### Post by oldfred on 2010-03-05
You just have to install grub to the MBR if that is what you want:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Erwacht on 2010-03-06
What does this mean?

grub-setup: error: Cannot read '/grub/core.img' correctly

---

