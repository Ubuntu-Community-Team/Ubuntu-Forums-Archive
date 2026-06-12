---
title: "XP lost after installing Ubuntu"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by luke stevens on 2011-04-29
Oh dear where to start

I recently thought it would be a good idea to install ubuntu on my home computer thats running XP home edition. Initially When running the live CD it asked me what partition I wanted it to go on. So I chose to share the one with windows on it assuming it would create a dual boot automatically. After Install of Ubuntu I restarted and It booted straight into ubuntu without the option of XP. After looking around on Ubuntu for some signs of Windows files I panicked and decided to put the XP disc in to see if I could fix the boot for windows. Big mistake! After some research on some forums to appeared to suggest running fixboot and fixmbr so I did with no joy.

After this nothing worked and when I put the live CD in again It just went into the virtual environment. So then I was left with no OS at all it seems. Panicking even more I tried to repair the original XP install but windows couldn't see the partition which seemed strange since the repair console finds the windows install.

The windows install is on the C drive which is a partition on a single no raid SATA drive. (Hope that makes sense).

After scratching my head and googling like crazy I found a few tutorials on Grub that suggested that you could insert the root of the XP install and it would boot fine.  As I am not familiar with Ubuntu this went a bit over my head. 

At this point I thought I didn't have much to lose and  Installed Ubuntu again on a new partition on another drive to have a go but I couldn't find where to find the root and even if I could I would know where to put it.

When I went into disc into disk utility it didn't even show the SATA volume anyway. It shows the adapter but no volume Im so confused and I feel like Im fumbling in the dark hoping to bump into the answer.

PLEASE PLEASE can someone help me restore my original setup of XP as stupidly I didn't back anything up. 

Hope this is coherent enough and people can follow what I am trying to get at.

---

### Post by lechien73 on 2011-04-29
Wow - I can understand why you're feeling panicked! Welcome to the forums, though.

To start with, it would be helpful to know what has happened to the partitions on your disk. Maybe you could go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and follow the instructions there to generate the results.txt file. When you have the file, please post it back here. This will help us understand your current disk structure and see if the XP partition is still there.

---

### Post by luke stevens on 2011-04-29
Hi Lechien73

Here is the report you requested. Hope It make sense to you as I am lost.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40021632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    38,262,783    38,260,736  83 Linux
/dev/sdb2          38,264,830    40,019,967     1,755,138   5 Extended
/dev/sdb5          38,264,832    40,019,967     1,755,136  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32     2,015,231     2,015,200   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2: PTTYPE="dos" 
/dev/sda5        08cc655c-ca1c-48ca-b763-0594e9d3d2e7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1caff100-10eb-465f-926c-d0ba8b5e9471   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a4e64bfe-ddca-4289-900e-4ae5671828bf   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        24EA-DDE9                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 1caff100-10eb-465f-926c-d0ba8b5e9471
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 1caff100-10eb-465f-926c-d0ba8b5e9471
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 1caff100-10eb-465f-926c-d0ba8b5e9471
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1caff100-10eb-465f-926c-d0ba8b5e9471 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 1caff100-10eb-465f-926c-d0ba8b5e9471
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1caff100-10eb-465f-926c-d0ba8b5e9471 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 1caff100-10eb-465f-926c-d0ba8b5e9471
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 1caff100-10eb-465f-926c-d0ba8b5e9471
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=1caff100-10eb-465f-926c-d0ba8b5e9471 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a4e64bfe-ddca-4289-900e-4ae5671828bf none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/core.img
   4.6GB: boot/grub/grub.cfg
  13.1GB: boot/initrd.img-2.6.35-22-generic
  17.3GB: boot/vmlinuz-2.6.35-22-generic
  13.1GB: initrd.img
  17.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8d aa ab c9 00 1e b9 ff  00 f5 d7 51 e1 12 b2 f8  |...........Q....|
00000010  fa 35 59 0a 9f b3 b7 ca  bf c2 a7 b8 f5 35 cf 27  |.5Y..........5.'|
00000020  a3 3b 62 b9 97 2a dc e9  ae d8 4f aa 3c 20 05 29  |.;b..*....O.< .)|
00000030  82 b8 1d 45 6a c7 2c c3  70 65 3e 66 72 b8 18 c5  |...Ej.,.pe>fr...|
00000040  71 cc d6 50 69 a2 85 f0  3b 99 1a 3c c9 c9 2c 4f  |q..Pi...;..<..,O|
00000050  7a c5 9a d1 67 82 33 2b  b0 72 b9 0b 9e 86 92 2d  |z...g.3+.r.....-|
00000060  c5 cb 46 c9 ed 6d 8a 58  aa 02 ac c4 e5 c1 5f eb  |..F..m.X......_.|
00000070  56 a0 81 a0 88 9d e8 87  85 61 8c 9c 7d 6a ae 2e  |V........a..}j..|
00000080  5e 56 92 1b 73 99 0e 03  ac 8a 47 ca 37 74 f7 ac  |^V..s.....G.7t..|
00000090  54 b7 51 39 8c a9 04 f2  48 e9 4f 9b 5d 04 e2 35  |T.Q9....H.O.]..5|
000000a0  08 8e 5d 8a 9b 82 a9 3c  70 4f a7 35 d3 e9 93 a4  |..]....<pO.5....|
000000b0  f0 04 8c 33 01 8d e4 0e  86 89 26 28 b5 7b 16 a3  |...3......&(.{..|
000000c0  88 45 13 bc 4e 42 03 82  7f fa d5 c7 5d 5c 06 8c  |.E..NB......]\..|
000000d0  07 95 d7 76 5b 68 5e b4  41 a6 15 11 6a 09 23 97  |...v[h^.A...j.#.|
000000e0  62 00 ca 48 e0 96 e4 fb  d6 ed 98 10 e1 54 7c c7  |b..H.........T|.|
000000f0  9c 9e f8 f7 a4 ef 71 25  d4 86 e2 10 93 34 6b 2e  |......q%.....4k.|
00000100  01 6e 10 8c 8f 73 4e 5b  40 eb 26 d6 31 b9 f9 72  |.n...sN[@.&.1..r|
00000110  0e 32 05 0f 4d 83 95 95  a3 50 51 5c 31 72 dc 80  |.2..M....PQ\1r..|
00000120  dd ab 16 f5 4b c8 56 42  a8 40 ce 09 eb 44 5d de  |....K.VB.@...D].|
00000130  a5 c9 59 0b 1c 24 cc a0  b0 55 55 1b 54 76 3e b5  |..Y..$...UU.Tv>.|
00000140  6d ca 42 c8 d9 c8 ce 4e  3b 55 37 73 24 dd b5 32  |m.B....N;U7s$..2|
00000150  f4 ef df ea b2 c8 59 99  43 74 c7 5a ed 9e ea 39  |......Y.Ct.Z...9|
00000160  64 78 d4 15 db d7 da a5  a2 e0 d6 cc e5 56 d4 43  |dx...........V.C|
00000170  0b 88 c6 e6 c9 6e 1b 81  ff 00 d7 ab 57 cf 8f 28  |.....n......W..(|
00000180  46 1b 6f 50 b9 e9 45 ee  10 8e 8c 75 b5 d0 8a 76  |F.oP..E....u...v|
00000190  44 05 8a 9e 0f ad 6a 5f  83 79 64 22 79 7e 63 ce  |D.....j_.yd"y~c.|
000001a0  38 1b 87 a7 d2 86 0f 5f  43 9c 93 0e 42 b1 24 2f  |8......_C...B.$/|
000001b0  62 70 3f fa f5 d0 d8 45  e7 43 1a a8 53 21 00 fe  |bp?....E.C..S!..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  00 48 6a d3 49 24 9a 49  2c 37 80 ce 2d 85 56 b0  |.Hj.I$.I,7..-.V.|
00000010  72 a8 60 b3 38 c1 91 a8  46 da a3 9c af ad 5f 6b  |r.`.8...F....._k|
00000020  2a c7 0d 55 1f 9c fc ab  37 76 dd ee 9e 57 a0 e6  |*..U....7v...W..|
00000030  ee 85 b2 0f d5 e4 e4 41  24 b0 a7 58 a5 49 be a6  |.......A$..X.I..|
00000040  87 aa 91 12 d3 52 f5 37  28 65 52 c1 50 a6 3c b3  |.....R.7(eR.P.<.|
00000050  da e9 02 8e 2e 12 06 d4  92 46 c4 60 60 ab 83 a1  |.........F.``...|
00000060  2b a2 ea 00 8b 30 df 8e  24 fd b6 ba d9 62 69 58  |+....0..$....biX|
00000070  d0 64 8d 22 09 24 00 03  d5 01 62 40 90 2b 28 0f  |.d.".$....b@.+(.|
00000080  dc 22 b5 8b 3b a6 d4 27  15 ca 7f 62 80 d7 8f 86  |."..;..'...b....|
00000090  04 24 2d a0 f3 ad fa 1c  12 12 a0 81 87 b8 8d cb  |.$-.............|
000000a0  64 d8 98 dd cd 75 c9 1f  1c 4f f7 23 fa 88 d4 19  |d....u...O.#....|
000000b0  ea 7a 8c 89 ce 1f 3c ed  96 a8 e8 26 49 ae 14 49  |.z....<....&I..I|
000000c0  24 a2 41 39 60 44 8e f2  2e d7 eb ae 8c a2 8a 86  |$.A9`D..........|
000000d0  b4 a0 b3 73 6b 3f 37 92  75 e4 1f 1e 86 00 4c 29  |...sk?7.u.....L)|
000000e0  b0 97 cb 63 5f ad e3 d1  43 34 06 b6 04 c8 33 70  |...c_...C4....3p|
000000f0  49 28 9a 8f 26 0d ad 13  06 76 60 42 d8 54 13 e7  |I(..&....v`B.T..|
00000100  72 32 5b 1d 3e 6b 3a 7e  d9 3c b5 a3 86 10 6d 22  |r2[.>k:~.<....m"|
00000110  89 0a 42 48 47 61 ea 82  c5 a1 ca a5 6a 15 71 08  |..BHGa......j.q.|
00000120  c7 e1 a4 29 32 8a 05 44  c1 24 92 12 49 4b 24 42  |...)2..D.$..IK$B|
00000130  40 e6 6c a6 e2 b0 95 2c  39 fd 65 a3 47 38 9a 7d  |@.l....,9.e.G8.}|
00000140  14 26 79 85 88 8a af f5  f7 d8 b5 86 46 1e 7c 14  |.&y.........F.|.|
00000150  00 91 b9 d3 6d 7f dc 81  6c 9f 46 41 18 b0 fc 4a  |....m...l.FA...J|
00000160  58 91 52 40 26 68 31 74  bd b5 d3 7a 9e 54 24 c8  |X.R@&h1t...z.T$.|
00000170  c0 00 82 49 20 1a 55 00  fb 9a 02 1b ff fb 92 60  |...I .U........`|
00000180  bd 80 03 7c 3d db e9 e9  42 e8 4b 62 4b 5d 31 27  |...|=...B.KbK]1'|
00000190  37 0d 44 f9 6b ac 24 6b  a1 1f 09 2d f4 c4 1c da  |7.D.k.$k...-....|
000001a0  3f 94 74 72 68 f4 b2 5f  64 63 e4 fb 1c f7 4d d5  |?.trh.._dc....M.|
000001b0  cb 49 af 05 09 cc d2 7b  d9 07 61 08 c5 aa 00 fe  |.I.....{..a.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1a 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```


Thanks for your help

---

### Post by Dutch70 on 2011-04-29
Hi and welcome to UF

Please put your boot script between [CODE][ /CODE] tags if you want someone to take a serious look at it. Without doing that, you lose the formatting and it's too difficult to read, among other problems.

To put it between "code" tags, use the # symbol in the toolbar.

Edit: BTW, please don't post another one, just edit that post.

---

### Post by lechien73 on 2011-04-30
I'm prepared to be corrected by any of the other (far more knowledgeable) gurus on here, but I'm afraid I'm not seeing any Windows partitions in the results you posted.

Ubuntu does have the option to install side-by-side with Windows. Can you remember exactly which option you picked?

---

### Post by Dutch70 on 2011-04-30
Try running the following commands from the live cd or usb stick. 
```
sudo mount /dev/sdb1 /mnt
```
and...
```
sudo grub-install --root-directory=/mnt /dev/sdb
```

Then reboot.

If it gets you to the grub menu, choose Ubuntu & run this command from the terminal.
```
sudo update-grub
```

Btw, it looks like you have a fat16 & a swap partition on sda, this is one of your hard drives.

sdb is another hard drive & appears to have Ubuntu installed on it. The commands above are reinstalling Grub2 to sdb1, where Ubuntu is installed.

sdc appears to be your usb stick.

It looks like you when you tried to install Ubuntu to the same partition as windows, which is the wrong file system for starters. It probably wiped windows out. You can find out for sure when you get booted to Ubuntu.

---

### Post by Bravo.I on 2011-05-01
Use gparted and see what really happened to your partitions. Whether they really are gone or its missing from view only.

---

### Post by Dutch70 on 2011-05-01
> **Bravo.I said:**
> Use gparted and see what really happened to your partitions. Whether they really are gone or its missing from view only.

His partitions aren't missing at all. They are right there in the boot script. What I think lechien73 meant is that the windows install is missing from his partitions.

@lechien73, my guess is that the OP did use the side by side install, which is a little tricky with version 10.10.

---

### Post by lechien73 on 2011-05-01
> **Dutch70 said:**
> His partitions aren't missing at all. They are right there in the boot script. What I think lechien73 meant is that the windows install is missing from his partitions.

@lechien73, my guess is that the OP did use the side by side install, which is a little tricky with version 10.10.

Yes, that's what I was meaning. The partitions clearly still exist, but I could see no evidence of a Windows installation.

---

### Post by luke stevens on 2011-05-01
Thanks for all your suggestions guys. I really appreciate it. To answer Lechien73 when I initially installed ubuntu I chose to install it side by side. As I mentioned in my original post I had foolishly assumed this would create a dual boot.

Apologies if I don't use the right terminology. 

I can boot into Ubuntu Ok as I have installed it on another drive hence why there might be more than one install showing on that report I posted.

As I am a newb could Bravo.I or someone tell me how to run gparted.

From what I have learn from reading bit and pieces from various forums is that I need to manually insert the root of windows into grub if that makes sense. What I guess I need to know is how to do that if infact windows is still on there which sdc1: seems to suggest.

Hope this helps

luke

---

### Post by luke stevens on 2011-05-01
when I was messing with window repair console I may have inadvertently put a MBR on the usb. Could that explain the windows xp showing up on sdc1?

Cheers

---

### Post by frank cox on 2012-02-26
> **luke stevens said:**
> when I was messing with window repair console I may have inadvertently put a MBR on the usb. Could that explain the windows xp showing up on sdc1?

Cheers


yes it could


you need to install gparted

sudo apt-get install gparted

then you can just type gparted to open it

---

### Post by PapaGary on 2012-02-26
> **frank cox said:**
> yes it could


you need to install gparted

sudo apt-get install gparted

then you can just type gparted to open it
Uh, Mr. Stevens hasn't been on the forum since May 2, 2011 so either he has solved his problem (and neglected to mark it SOLVED) or he gave up.

---

