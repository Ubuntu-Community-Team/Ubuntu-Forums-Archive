---
title: "Installed ubuntu-netbook-10.10 on Toshiba NB-205 but does not boot"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by ryanabbott on 2011-01-17
Greetings,

I just installed ubuntu-netbook-10.10 on my Toshiba NB-205 netbook. Installation completed successfully, but booting the new installation fails. I have searched the forums and haven't found a solution.

I am running an ext4 root partition on /dev/sda5, swap on /dev/sda6, and ext2 /boot on /dev/sda7. The error message I get is

```
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/dcd974c1-4acc-4807-9745-4c51cd9aa4cd does not exist.
Dropping to a shell!

```

Here is the output from boot_info_script in RESULTS.txt:
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

I have spent quite a few hours trying to figure it out--thanks in advance for your help.

---

### Post by Quackers on 2011-01-17
Is this an HP machine, by any chance?

EDIT oops I see it isn't. I'll be back :-)

---

### Post by Quackers on 2011-01-17
I asked the question because I know this has happened with HP machines on occasions.
Sometimes, (maybe due to a HDD which is slow to get up to speed, perhaps) the system gives up looking for a UUID too quickly and fails to boot with an error similar to yours.
The fix in these circumstances is to boot from the live cd/usb and select "try ubuntu" and when the desktop loads to chroot into your installed system and edit /etc/default/grub and uncomment (take away the # sign) from the start of the line 
#GRUB_DISABLE_LINUX_UUID=true
then save the file and quit.
As you have a separate /boot partition the chroot commands will be slightly different. If you need help to do that come back.

Also, it's never a bad idea to wait for a second opinion :wink:

---

### Post by ryanabbott on 2011-01-18
I think you are on the right track, Quackers. I am chrooted into the installation now, and hard drive accesses are sometimes *verrry* delayed. Also, when I boot the liveCD, I have to hit <enter> a bunch of times to 'wake' the system up throughout the boot process.

I uncommented GRUB_DISABLE_LINUX_UUID=true, ran update-grub, hit <enter> a bunch of times to get it to proceed, and rebooted. I get the same error now, but with /dev/sda5 instead of the uuid:

```
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/sda5 does not exist.
Dropping to a shell!

```

Hmm, what next?

EDIT: I tried booting again, this time hitting <enter> many times, and it did boot.

---

### Post by Quackers on 2011-01-18
Hmm, that's not nice.
From the live cd desktop again, can you post a screenshot of the gparted screen for sda please?

---

### Post by ryanabbott on 2011-01-18
Here is that screenshot.

---

### Post by Quackers on 2011-01-18
I'm afraid that, other than to point one detail out, I'm not sure I can help you more. I notice that your /boot partition (sda7) is using the ext2 format. I would have expected to see ext4 for a modern Linux system. I don't know whether that is significant or not, though.
I see nothing wrong with your partition structure and I don't see any reason for it not being able to see sda5.
As the change we have made is a minor one (and easily irreversible) I am loathe to suggest anything else at this stage. It may be a wise move to see if anybody else has an idea as to why you are having this problem.
I would ask though, whether there is any reason for having a separate /boot partition. It can complicate things.

---

### Post by ryanabbott on 2011-01-18
Well, thanks for your help. I used an ext2 boot partition because of this problem, being uncertain whether grub had good ext4 support currently. Apparently it wasn't necessary.

Anyway, thanks again and I will keep trying to figure it out.

---

### Post by Quackers on 2011-01-18
I hope so.
There are many users here who are much better qualified than me to understand what has happened here. It is definitely worth waiting for one of them to appear :-)

---

### Post by Rubi1200 on 2011-01-18
As far as I know, the boot partition can use ext2/3/4 so I don't think that is the problem.

Question: why do you need a separate boot partition? In most cases, it is unnecessary.

Here is what I would try and do; reinstall GRUB:
Use method 3 - chroot.

Notice that you must also mount the boot partition.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by ryanabbott on 2011-01-18
I think Grub is working properly because I can get it to boot now. I have to hit <enter> scores of times, but it does boot.

It's a problem that shows up when running the LiveCD and also after booting the new installation. It seems to be associated with hard drive accesses (that's when I have to hit <enter> many times to get things to happen), so I think it's something to do with the hard drive controller; maybe a setting in the kernel.

I'll close this thread since it's no longer a boot problem and maybe open a new one focused on the hard drive.

Thanks for your suggestions guys! :popcorn:

---

### Post by Quackers on 2011-01-18
Well that's good - sort of. You could try an older kernel, or maybe even 10.04. Just a suggestion.

---

### Post by uqbar on 2011-01-20
The problem is with the netbook itself *and* Ubuntu 10.10.
The installation itself takes ages to finish because the system goes to sleep very often and you need to hit some key (I prefer SHIFT, CTRL or ALT instead of ENTER to avoid false confirmations).
You can see this during the boot and the installation.
The more you hit SHIFT, the more the HD led blinks.
I've browsed the BIOS options and there's none involving the power management (other than the CPU frequency).
Instead of Ubuntu 10.10 I've tried Mint Debian and PCLinuxOS with normal operations and no surprise at installation time or at the reboot.
I would say it's definitely a problem with Ubuntu kernel.

---

### Post by pnreddy on 2011-01-20
> **ryanabbott said:**
> I think Grub is working properly because I can get it to boot now. I have to hit <enter> scores of times, but it does boot.

It's a problem that shows up when running the LiveCD and also after booting the new installation. It seems to be associated with hard drive accesses (that's when I have to hit <enter> many times to get things to happen), so I think it's something to do with the hard drive controller; maybe a setting in the kernel.

I'll close this thread since it's no longer a boot problem and maybe open a new one focused on the hard drive.

Thanks for your suggestions guys! :popcorn:
I had a similar problem installing ubuntu 10.10. When I tried ubuntu 9.04, it went off without a hitch. Even here I had to prod the hdd by pressing a key to nudge the hdd

---

### Post by ryanabbott on 2011-01-20
Aha, thanks Uqbar and Pnreddy. I used to use Gentoo; in those days, I would have just recompiled the kernel. Now I'm rather too busy, though, which is why I gave up Gentoo.

---

