---
title: "Installation of Ubuntu netbook successful but does not boot"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by thewill2live on 2010-12-30
Hey guys, Ubuntu noob here so I apologize in advance for any faux paux I may make. I recently installed a new SATA 500 GB hard drive into my Toshiba NB205-N310\BN netbook (my old one died). The installation of Ubuntu netbook remix goes through all the way but when it says that its complete and I must restart I do so and all i see is a black screen with a cursor that never goes away. I hit any button and then I see [this]("http://i.imgur.com/ejbov.jpg"). I've read through some other forums and people say just type 'exit' after a while and they say it solves the problem but that doesnt work for me no matter how long I wait. I think it might have something to do with the fact that I have a brand new blank HD?

---

### Post by Quackers on 2010-12-31
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by thewill2live on 2011-01-10
Quackers: hey, sorry for the late response, I've been without internet for the past week while i was on vacation. I have run that already and I had posted the results [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10299621&posted=1#post10299621") as a part of another thread in efforts to get help from them too. Please let me know if you'd liek me to repost it here. thanks.

-Will

---

### Post by ryanabbott on 2011-01-17
I have this same result with my Toshiba nb-205 netbook. Here is my result of the boot_info_script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   168,411,808   165,337,761   7 HPFS/NTFS
/dev/sda3         168,413,182   312,580,095   144,166,914   5 Extended
/dev/sda5         168,413,184   308,385,791   139,972,608  83 Linux
/dev/sda6         308,387,840   312,385,535     3,997,696  82 Linux swap / Solaris
/dev/sda7         312,387,584   312,580,095       192,512  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 503 MB, 503316480 bytes
30 heads, 32 sectors/track, 1024 cylinders, total 983040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32       983,039       983,008   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7EECAC8FECAC42EF                       ntfs       System                        
/dev/sda2        9C52D22B52D20A42                       ntfs       TI103127W0E                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        dcd974c1-4acc-4807-9745-4c51cd9aa4cd   ext4                                     
/dev/sda6        f7fae5a6-f108-4330-8450-a3085f75a90e   swap                                     
/dev/sda7        b4e77357-cf8b-49ed-b395-165df3b73003   ext2                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FAFC-DC90                              vfat       ROBS DRIVE                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ROBS DRIVE        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
UUID=dcd974c1-4acc-4807-9745-4c51cd9aa4cd /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=b4e77357-cf8b-49ed-b395-165df3b73003 /boot           ext2    defaults        0       2
# /media/Windows7 was on /dev/sda2 during installation
UUID=9C52D22B52D20A42 /media/Windows7 ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=f7fae5a6-f108-4330-8450-a3085f75a90e none            swap    sw              0       0

============================= sda7/grub/grub.cfg: =============================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set dcd974c1-4acc-4807-9745-4c51cd9aa4cd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set b4e77357-cf8b-49ed-b395-165df3b73003
set locale_dir=($root)/grub/locale
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b4e77357-cf8b-49ed-b395-165df3b73003
	linux	/vmlinuz-2.6.35-22-generic root=UUID=dcd974c1-4acc-4807-9745-4c51cd9aa4cd ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b4e77357-cf8b-49ed-b395-165df3b73003
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=dcd974c1-4acc-4807-9745-4c51cd9aa4cd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b4e77357-cf8b-49ed-b395-165df3b73003
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b4e77357-cf8b-49ed-b395-165df3b73003
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7eecac8fecac42ef
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9c52d22b52d20a42
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

=================== sda7: Location of files loaded by Grub: ===================


 160.0GB: grub/core.img
 160.0GB: grub/grub.cfg
 159.9GB: initrd.img-2.6.35-22-generic
 159.9GB: vmlinuz-2.6.35-22-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  53 00 43 00 41 00 4e 00  39 00 2e 00 44 00 41 00  |S.C.A.N.9...D.A.|
00000010  54 00 00 00 00 00 54 00  83 07 33 89 00 00 00 00  |T.....T...3.....|
00000020  6d 07 33 89 00 00 00 00  6d 07 33 89 00 00 00 00  |m.3.....m.3.....|
00000030  68 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |h...........@...|
00000040  00 00 00 00 00 00 00 00  0b 00 0b 00 28 00 20 00  |............(. .|
00000050  48 00 20 00 18 00 01 00  08 01 00 00 02 00 02 00  |H. .............|
00000060  01 33 00 00 00 00 00 00  01 33 0c 00 00 00 00 00  |.3.......3......|
00000070  00 00 2e 16 00 00 00 00  d0 74 2b 16 00 00 00 00  |.........t+.....|
00000080  d0 74 2b 16 00 00 00 00  00 00 26 02 00 00 00 00  |.t+.......&.....|
00000090  00 00 2e 16 00 00 00 00  78 74 2b 16 00 00 00 00  |........xt+.....|
000000a0  d0 74 2b 16 00 00 00 00  00 00 26 02 00 00 00 00  |.t+.......&.....|
000000b0  96 07 33 89 00 00 00 00  83 07 33 89 00 00 00 00  |..3.......3.....|
000000c0  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
000000d0  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
000000e0  1b 00 01 00 28 00 00 00  28 00 00 00 18 00 00 00  |....(...(.......|
000000f0  00 00 00 00 00 00 02 00  00 00 00 00 00 00 00 00  |................|
00000100  70 3c 39 aa 90 f9 c1 8a  a1 07 33 89 00 00 00 00  |p<9.......3.....|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  98 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |............@...|
00000130  00 00 00 00 00 00 00 00  14 00 14 00 28 00 38 00  |............(.8.|
00000140  60 00 38 00 84 08 01 00  00 00 d0 09 00 00 08 00  |`.8.............|
00000150  00 00 00 00 00 00 00 00  fb f0 1c 00 00 00 00 00  |................|
00000160  00 40 5c d7 74 4a cb 01  00 40 5c d7 74 4a cb 01  |.@\.tJ...@\.tJ..|
00000170  df 64 75 e6 01 4b cb 01  00 40 5c d7 74 4a cb 01  |.du..K...@\.tJ..|
00000180  00 30 09 00 00 00 00 00  22 26 09 00 00 00 00 00  |.0......"&......|
00000190  20 20 00 00 00 00 00 00  52 85 5c e6 01 4b cb 01  |  ......R.\..K..|
000001a0  9d c8 74 e6 01 4b cb 01  ce 3d 75 e6 01 4b cb 01  |..t..K...=u..K..|
000001b0  7f ba 68 e6 01 4b cb 01  00 30 09 00 00 00 00 fe  |..h..K...0......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 57 08 00 fe  |............W...|
000001d0  ff ff 05 fe ff ff 02 d0  57 08 00 08 3d 00 00 00  |........W...=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda7

00000000  63 75 22 8b 84 22 68 64  f2 16 dc 5b 78 26 94 8f  |cu".."hd...[x&..|
00000010  3f 82 77 0e 41 13 91 b5  64 c9 dd 86 d2 ba 5d 8f  |?.w.A...d.....].|
00000020  67 e8 1d e5 44 44 fc 54  3b e4 19 03 80 af 80 ed  |g...DD.T;.......|
00000030  fa b1 0f f9 98 e5 c9 4e  70 4d ba cc 86 f6 f8 90  |.......NpM......|
00000040  cb bd 4f 70 53 c2 e7 9d  06 11 b9 ff f1 88 ac 85  |..OpS...........|
00000050  0d 2a ea 46 5d 04 50 44  ee 2a fd 71 9e 69 c5 e1  |.*.F].PD.*.q.i..|
00000060  8b e9 da 7d c2 a3 24 50  21 7f 92 54 ab a5 3b 8c  |...}..$P!..T..;.|
00000070  6d f3 22 05 7c 88 36 9d  a3 38 8f 72 0b 36 13 92  |m.".|.6..8.r.6..|
00000080  ad 68 ce d9 71 be ba 4c  80 50 db f5 b6 1e 3c ec  |.h..q..L.P....<.|
00000090  33 1b bc fc cb 5c 7a 4c  b1 c8 81 d7 cb 6b b1 83  |3....\zL.....k..|
000000a0  0a 40 0b 79 83 48 9d 98  3a 92 7d fd 1f fa 74 9a  |.@.y.H..:.}...t.|
000000b0  48 a0 ac 4b 9c 90 1f 4e  28 a8 b4 75 e5 ea 92 d6  |H..K...N(..u....|
000000c0  d6 64 99 75 07 2c e6 43  58 0c 6b 54 e6 2c 05 90  |.d.u.,.CX.kT.,..|
000000d0  be 87 f0 04 be 04 ff a9  e8 cb 49 82 4b b9 d0 9c  |..........I.K...|
000000e0  fa ef 86 d4 c2 5c 7f 4a  cb de a3 0b 0e b1 ff f3  |.....\.J........|
000000f0  73 a8 8c 06 22 f6 4e 51  f9 4a 50 e8 17 e8 70 98  |s...".NQ.JP...p.|
00000100  6c c9 cf 89 d7 d6 77 b5  91 1a 48 02 71 8f 43 99  |l.....w...H.q.C.|
00000110  a7 39 76 58 e3 23 f6 5e  85 2c 8e 9c 33 72 67 ee  |.9vX.#.^.,..3rg.|
00000120  27 03 7b 91 54 bc b0 59  b1 9f 2f 77 43 ba d6 9b  |'.{.T..Y../wC...|
00000130  15 22 c5 26 06 a3 ea bc  35 64 25 99 ae 60 b0 ad  |.".&....5d%..`..|
00000140  4f 7d 60 f3 1a e5 67 6d  1e 90 73 27 6e 4b e6 00  |O}`...gm..s'nK..|
00000150  d7 58 64 33 80 7c 29 78  64 ef 25 01 86 a3 53 b5  |.Xd3.|)xd.%...S.|
00000160  ba 76 b5 a1 4d 86 58 d9  f0 c5 1a 2a e6 2b 35 bc  |.v..M.X....*.+5.|
00000170  f1 d8 62 88 4d bd d3 92  e9 d3 6f ae a4 1e 43 2a  |..b.M.....o...C*|
00000180  9d a9 64 b4 c3 52 9d 93  12 56 16 a2 a7 6b cb ca  |..d..R...V...k..|
00000190  74 c4 bd 4e 73 49 c1 f2  a5 20 25 d2 18 0d 98 e1  |t..NsI... %.....|
000001a0  aa 2f 5f 18 96 91 56 96  93 2d 66 4b d5 07 d3 31  |./_...V..-fK...1|
000001b0  41 10 5e 4c 01 40 27 a7  d6 9b 1e 3e e0 4a 3d f5  |A.^L.@'....>.J=.|
000001c0  2a 2a a3 db af 22 41 05  71 77 0f 59 62 ea 12 02  |**..."A.qw.Yb...|
000001d0  7a 9c 56 bf be 7b d4 b0  55 9e 74 ff 1d ec 42 50  |z.V..{..U.t...BP|
000001e0  19 56 54 fa 3a 0c ad d3  96 14 21 d4 2f 23 c6 1b  |.VT.:.....!./#..|
000001f0  f7 8a bc 7e 02 12 d7 2f  38 c8 10 13 a6 c2 a3 1d  |...~.../8.......|
00000200



```


And the error I get when I boot is:
```
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/dcd974c1-4acc-4807-9745-4c51cd9aa4cd does not exist.
Dropping to a shell!

```

Help would be greatly appreciated.

EDIT: Reposted as a separate thread at [http://ubuntuforums.org/showthread.php?t=1669601]("http://ubuntuforums.org/showthread.php?t=1669601")

---

### Post by Quackers on 2011-01-17
For the record here is your boot script, thewill2live
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   964,485,119   964,483,072  83 Linux
/dev/sda2         964,487,166   976,771,071    12,283,906   5 Extended
/dev/sda5         964,487,168   976,771,071    12,283,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8115 MB, 8115978240 bytes
199 heads, 32 sectors/track, 2489 cylinders, total 15851520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,851,519    15,851,488   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7db222d0-d7cd-4d65-95fc-3868038a12e0   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b9dab59e-1cd7-4404-9e72-8a5b43c44547   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1B12-133D                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7db222d0-d7cd-4d65-95fc-3868038a12e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7db222d0-d7cd-4d65-95fc-3868038a12e0
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7db222d0-d7cd-4d65-95fc-3868038a12e0
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7db222d0-d7cd-4d65-95fc-3868038a12e0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7db222d0-d7cd-4d65-95fc-3868038a12e0
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7db222d0-d7cd-4d65-95fc-3868038a12e0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7db222d0-d7cd-4d65-95fc-3868038a12e0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7db222d0-d7cd-4d65-95fc-3868038a12e0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b9dab59e-1cd7-4404-9e72-8a5b43c44547 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 249.2GB: boot/grub/core.img
 163.3GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
 249.2GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
 249.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 df f1 00 5a 3c 00 00  00 00 00 00 02 00 00 00  |....Z<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3d 13 12 1b 4e  4f 20 4e 41 4d 45 20 20  |..)=...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 dc 78 00 00  66 ba 00 00 00 00 bb 00  |}.f..x..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```
I'll take a look and get back to you.

ryanabbott, please start a new thread giving details of what has happened. You have a separate boot partition and may have a different problem.

---

### Post by Quackers on 2011-01-17
thewill2live, all your boot files are ok, but for some reason etc/fstab is looking for your /root partition in sdb1 and your swap partition in sdb5, whereas your actual root partition is sda1 and your swap partition is sda5.
From the live cd you should chroot into your actual installation and edit /etc/fstab file to reflect these partitions, taking care to match the UUID's of both correctly.

---

