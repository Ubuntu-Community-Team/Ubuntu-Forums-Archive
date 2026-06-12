---
title: "winxp does not boot after Ubuntu installation"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by vikram999 on 2011-06-19
Hello Friends,

I will start in chronological order.

1> Win XP pro 2002 installed on my pc in C drive, the pc has 4 partitions
2>Booted from the ubuntu 11.04 desktop i386 CD, went into the demo mode to have a look at the OS, chose the option to install the OS from the icon on the desktop.
3>system hanged during installation (I don't know at which stage)
4>I Reboot the system, win XP started smoothly, all partitions intact
5>I restarted the system, boot from ubuntu CD and installed the OS (I think it got installed on drive d:, as the the drive D was earlier 41 GB and now it has become 21 GB)
6>Now, whenever I start my PC, PC takes some more time than it usd to take, during this delay the monitor displays "Hz?" to indicate no input.
7>After some time, ubuntu starts and works properly.

My problem: Right now I cannot boot to XP anyhow, I want option to choose the OS on startup for both XP and Ubuntu.

Plz help,

Thankx,

Vikram

---

### Post by ajgreeny on 2011-06-19
1.  From ubuntu open a terminal and run ```
sudo fdisk -l 
```lower case L at the end, and report back the output from that.

2.  Run command ```
sudo blkid
``` and again report back the output.

3.  Go to the boot-info-script in my signature and follow the instructions to run the script.  Copy the RESULTS.txt file and paste it between code tags (the # icon in toolbar at top of entry box).

That should give us plenty of information so that we can see what has happened and suggest what to do next.

---

### Post by vikram999 on 2011-06-19
vikram@vikram-System-Product-Name:~$ sudo fdisk -l
[sudo] password for vikram: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56465f53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19456   115322572    f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686    7  HPFS/NTFS
/dev/sda6           10199       12777    20710898    7  HPFS/NTFS
/dev/sda7           15298       19456    33407136    7  HPFS/NTFS
/dev/sda8           12777       15183    19329024   83  Linux
/dev/sda9           15183       15297      915456   82  Linux swap / Solaris

Partition table entries are not in disk order
vikram@vikram-System-Product-Name:~$ sudo blkid
/dev/sda1: UUID="46A437DAA437CB67" TYPE="ntfs" 
/dev/sda5: UUID="7000B5E600B5B386" TYPE="ntfs" 
/dev/sda6: UUID="1EF8BD58F8BD2EC1" TYPE="ntfs" 
/dev/sda7: UUID="B8508B7B508B3EDE" TYPE="ntfs" 
/dev/sda8: UUID="1f617b25-1372-4f82-9b19-c2f42ec7611d" TYPE="ext4" 
/dev/sda9: UUID="c392e9a0-85c6-4ee1-9736-8e5b3417e1c6" TYPE="swap" 
vikram@vikram-System-Product-Name:~$ 

                  > Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda2          81,915,496   312,560,639   230,645,144   f W95 Extended (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda6         163,830,933   205,252,728    41,421,796   7 NTFS / exFAT / HPFS
/dev/sda7         245,746,368   312,560,639    66,814,272   7 NTFS / exFAT / HPFS
/dev/sda8         205,254,656   243,912,703    38,658,048  83 Linux
/dev/sda9         243,914,752   245,745,663     1,830,912  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        46A437DAA437CB67                       ntfs       
/dev/sda5        7000B5E600B5B386                       ntfs       
/dev/sda6        1EF8BD58F8BD2EC1                       ntfs       
/dev/sda7        B8508B7B508B3EDE                       ntfs       
/dev/sda8        1f617b25-1372-4f82-9b19-c2f42ec7611d   ext4       
/dev/sda9        c392e9a0-85c6-4ee1-9736-8e5b3417e1c6   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 1f617b25-1372-4f82-9b19-c2f42ec7611d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 1f617b25-1372-4f82-9b19-c2f42ec7611d
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 1f617b25-1372-4f82-9b19-c2f42ec7611d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1f617b25-1372-4f82-9b19-c2f42ec7611d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 1f617b25-1372-4f82-9b19-c2f42ec7611d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1f617b25-1372-4f82-9b19-c2f42ec7611d ro single 
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 1f617b25-1372-4f82-9b19-c2f42ec7611d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 1f617b25-1372-4f82-9b19-c2f42ec7611d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 46A437DAA437CB67
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=1f617b25-1372-4f82-9b19-c2f42ec7611d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=c392e9a0-85c6-4ee1-9736-8e5b3417e1c6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 102.237831116 = 109.777035264  boot/grub/core.img                             1
 113.998374939 = 122.404823040  boot/grub/grub.cfg                             1
  99.010189056 = 106.311380992  boot/initrd.img-2.6.38-8-generic               2
 102.236103058 = 109.775179776  boot/vmlinuz-2.6.38-8-generic                  1
  99.010189056 = 106.311380992  initrd.img                                     2
 102.236103058 = 109.775179776  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  7f ff 7f ff 1f 1f ff fa  fd ff f8 ff 8d f3 20 32  |.............. 2|
00000010  33 cc 41 06 6f 31 1e 33  4c c1 9c 64 19 92 0c 86  |3.A.o1.3L..d....|
00000020  79 73 20 da e6 23 a4 6a  45 5f 93 ff ff ff 08 3b  |ys ..#.jE_.....;|
00000030  5b 50 a1 06 a1 30 83 04  18 41 84 1e 83 08 30 83  |[P...0...A....0.|
00000040  c2 0c 10 33 f8 4c 10 3c  10 33 d1 71 9a 0a 7e 2e  |...3.L.<.3.q..~.|
00000050  46 83 cd e7 32 e3 34 19  7c d6 33 3c c1 04 1e 5c  |F...2.4.|.3<...\|
00000060  8a 08 cf 3c 8c 46 b3 28  19 d3 4c d4 79 99 9d 72  |...<.F.(..L.y..r|
00000070  32 21 b3 ac 74 f3 4c ab  5f f4 e3 e3 4e 23 4d 34  |2!..t.L._...N#M4|
00000080  e3 4f 8b 4e 34 30 9c 5a  71 0d 0e e2 d0 d0 71 7e  |.O.N40.Zq.....q~|
00000090  98 41 da 6a 48 90 61 33  f0 54 19 78 26 72 33 b0  |.A.jH.a3.T.x&r3.|
000000a0  83 3f 29 22 04 18 41 82  0c 10 6a 08 19 4e 21 fc  |.?)"..A...j..N!.|
000000b0  b8 cd 07 92 23 f1 ff 23  8c fe 66 35 23 8f a2 fb  |....#..#..f5#...|
000000c0  04 18 28 24 5e 39 3c 27  6e 6e a3 73 45 e6 4e da  |..($^9<'nn.sE.N.|
000000d0  36 30 c2 93 b6 8b c7 09  17 99 76 e4 f1 a2 ed c9  |60........v.....|
000000e0  45 17 7e 4e 1a 26 f4 5c  39 27 7c 8c 76 89 8f e3  |E.~N.&.\9'|.v...|
000000f0  8b 96 ee 3a d3 fd 38 e2  c2 61 34 34 d3 8b 43 6d  |...:..8..a44..Cm|
00000100  56 2e c2 71 7e ae b8 49  37 54 e9 37 ba 57 4e 90  |V..q~..I7T.7.WN.|
00000110  6e a9 e9 e1 53 a0 9e 9e  9b 84 f4 fd 07 84 1d 20  |n...S.......... |
00000120  f0 83 86 14 20 e8 20 6f  82 97 cd 04 1b 82 0c 2d  |.... . o.......-|
00000130  1b 9f e8 be 70 a4 f3 2e  dc bb 68 bb a2 ed a2 f1  |....p.....h.....|
00000140  c9 db 45 df be 4a 1e 89  bb 91 bb ea f5 f4 ff fd  |..E..J..........|
00000150  74 f5 ff 5a 4d d7 ed fa  4f b6 93 f5 a4 f4 dd 7d  |t..ZM...O......}|
00000160  37 4f d6 fb d7 a5 ff 5c  2a 6d 04 da 09 d2 7a 7a  |7O.....\*m....zz|
00000170  7a 74 9f f8 4f c2 0f 08  3f af ff eb 4b 1f 1f 4a  |zt..O...?...K..J|
00000180  ff fd 27 4b a6 f7 af ff  f4 bf eb ab ea ba eb f6  |..'K............|
00000190  ff af fd f6 e9 f7 fa eb  bd 2a f4 ae bf b7 f5 f5  |.........*......|
000001a0  f1 9a 0b fe ff ff ff fa  7f bf ff ff fa ff e2 bf  |................|
000001b0  e3 f8 f5 5a 5a 5f e2 3f  ee eb f7 ef ff ff 00 01  |...ZZ_.?........|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 ec ed e1 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff ee ed  e1 04 23 0c 78 02 00 00  |..........#.x...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by vikram999 on 2011-06-19
FYI, I don't know why the script shows date as 17 May 2011, my system date is 19 June 2011.

---

### Post by vikram999 on 2011-06-19
one more point  - last week I formatted my hard disk as my XP crashed, while partitioning my 160 GB HD, I chose 40 GB as first partition and it got created, after creating the second partition of 40 GB I see that 8 MB of HD is shown separately and that I cannot do anything with it as "it is very small size for a partition" (mentioning this point as I guess it will be reported in the text posted above)

---

### Post by YesWeCan on 2011-06-19
You appear to have 4 installations of XP. Seems a lot.

Anyhow, someone else had a similar problem the other day. That is where grub.cfg has a menu entry for XP in sda1 but you never see the menu at boot time. That thread is not solved yet.
[http://ubuntuforums.org/showpost.php?p=10950572&postcount=1](http://ubuntuforums.org/showpost.php?p=10950572&postcount=1)

Try this anyhow. Boot Ubuntu, edit /etc/default/grub and comment out (put a # in front) the line GRUB_HIDDEN_TIMEOUT=0. That is meant to force the menu to appear.
Then [COLOR="Navy"]sudo update-grub[/COLOR]
and [COLOR="Navy"]sudo grub-install /dev/sda[/COLOR]

See if this makes any difference.

---

### Post by vikram999 on 2011-06-19
The # was already present in the beginning of the line GRUB_HIDDEN_TIMEOUT=0
1> [COLOR=Navy]sudo update-grub was run on terminal
2> [/COLOR][COLOR=Navy]sudo grub-install /dev/sda - this command was first run half "[/COLOR][COLOR=Navy]sudo grub-install"
3>[/COLOR][COLOR=Navy]sudo grub-install /dev/sda command was run on the terminal
4>Restarted the PC, did not get the dual boot options
[/COLOR]

---

### Post by vikram999 on 2011-06-20
can you recommend a very good and free tool/utility for formating and partitioning.  Till now I have used what winxp boot CD offered and this is the result of that that I have 4 installation of xp, if solution to my problem is not easy, I would think of complete format, partition, xp installation and lastly Ubuntu installation to get the dual boot option i want.

Thankx.

---

