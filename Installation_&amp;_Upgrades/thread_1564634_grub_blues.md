---
title: "grub blues"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2010-08-30
Hi,

I have a Thinkpad T23 with a 160GB drive. It had XP installed and I installed 10.04. Everything went fine with no errors. However when I boot it comes back with a message "out of disk" and the prompt "grub rescue>". The only recognised commands are "ls" and "set", for "ls" I get:

(hd0) (hd0,5) (hd0,1) (fd0)

and for "set" I get:
prefix=(hd0,5)/boot/grub
root=hd0,5

whenever I try listing some directories such as "ls /boot" it comes back with the same
message:

error: out of disk

I tried re-installing grub as shown in [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) , everything went fine, but the problem remains; I also tried the solution posted on

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

with the difference that I could only edit 00_header instead of 10_linux since that particular line is not found in the first file. Again, the problem remains. At this point I don't know what else to try. I'd appreciate any help.

Cheers,

Daniel :confused:

---

### Post by v1ad on 2010-08-30
if you installed from usb, reboot with usb plugged in and see if it will show u the proper grub menu, if it does let me know.

---

### Post by danielsender on 2010-08-30
no, i installed from a live CD

---

### Post by drs305 on 2010-08-30
There are quite a few things that can cause an "out of disk" error message.

Boot to the LiveCD and then please post the results of *meierfra's* boot info script. Follow the instructions on downloading and running the script found at this site:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Once you have generated a RESULTS.txt, please post the contents of the file here, between "code" tags. You can generate the tags by pressing the **#** icon in the post's top menu.

---

### Post by v1ad on 2010-08-30
hmm what i think happened is that the root is in the wrong partition && that it should be on (0,1) if you can please boot from the live cd again and go to System > Administration > Disk utility.

click on your hard drive and tell me what partitions are partitioned as what:(ext4, swap, ntfs)

so basically tell me:
(ext4 /dev/sda5)

something like that.
im late for class so i reply after, and maybe during. 6-10 gmt

---

### Post by danielsender on 2010-08-30
Here is the RESULTS.txt file

---

### Post by kansasnoob on 2010-08-30
I'm not seeing the problem but I'm quite tired, regardless many folks prefer seeing this in # tags so here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   253,820,929   253,820,867   7 HPFS/NTFS
/dev/sda2         253,822,974   312,580,095    58,757,122   5 Extended
/dev/sda5         253,822,976   310,065,151    56,242,176  83 Linux
/dev/sda6         310,067,200   312,580,095     2,512,896  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1037 MB, 1037615104 bytes
256 heads, 32 sectors/track, 247 cylinders, total 2026592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32     2,030,591     2,030,560   4 FAT16 <32M

/dev/sdb1 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0EC88E66C88E4C41                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        57fb2d70-b9bd-42af-a769-4ed83f20d03f   ext4                                     
/dev/sda6        9bbf493c-1cf3-4aa7-9388-bab5fd6f87d9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1                                               vfat       LEXAR MEDIA                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/LEXAR MEDIA       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 57fb2d70-b9bd-42af-a769-4ed83f20d03f
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 57fb2d70-b9bd-42af-a769-4ed83f20d03f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 57fb2d70-b9bd-42af-a769-4ed83f20d03f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=57fb2d70-b9bd-42af-a769-4ed83f20d03f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 57fb2d70-b9bd-42af-a769-4ed83f20d03f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=57fb2d70-b9bd-42af-a769-4ed83f20d03f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 57fb2d70-b9bd-42af-a769-4ed83f20d03f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 57fb2d70-b9bd-42af-a769-4ed83f20d03f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0ec88e66c88e4c41
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=57fb2d70-b9bd-42af-a769-4ed83f20d03f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9bbf493c-1cf3-4aa7-9388-bab5fd6f87d9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 156.2GB: boot/grub/core.img
 156.2GB: boot/grub/grub.cfg
 156.2GB: boot/initrd.img-2.6.32-21-generic
 156.2GB: boot/vmlinuz-2.6.32-21-generic
 156.2GB: initrd.img
 156.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  63 32 ba 30 7a a0 be e3  9c 9e bb fc 0e 16 44 b9  |c2.0z.........D.|
00000010  da 13 dd ef b6 96 ac 6d  ea fa 2a df 59 e6 e9 4f  |.......m..*.Y..O|
00000020  87 d2 73 2e c0 18 2a f0  46 9a 44 3d 8b f5 d0 9f  |..s...*.F.D=....|
00000030  89 44 cf dc 1b 73 5c ca  6f 23 e0 bb 86 20 60 79  |.D...s\.o#... `y|
00000040  c2 5e cb d4 88 95 6c ba  ea 5d 5a e3 70 e6 03 10  |.^....l..]Z.p...|
00000050  db 3c c1 cf 12 13 86 e3  05 36 8e 22 b4 72 29 f6  |.<.......6.".r).|
00000060  41 1c 93 6e 04 25 dc cf  c8 bd dd c8 01 89 44 2b  |A..n.%........D+|
00000070  20 60 a3 33 ef a5 a2 6a  08 29 30 0d 49 9b cb 08  | `.3...j.)0.I...|
00000080  6d 90 da 85 a9 15 13 04  59 d0 ee 08 c1 b9 3b 52  |m.......Y.....;R|
00000090  e0 56 a4 af 48 97 68 50  15 31 08 b6 e6 99 10 2f  |.V..H.hP.1...../|
000000a0  f3 82 f0 e1 2a f3 e6 68  59 eb ed f9 75 94 cf 29  |....*..hY...u..)|
000000b0  e8 05 35 30 ee 95 d0 c7  07 c4 95 97 71 a9 fe 2e  |..50........q...|
000000c0  c1 f6 66 8f 7b 8d 6f 4e  c3 a5 79 38 20 79 29 90  |..f.{.oN..y8 y).|
000000d0  45 91 04 dc f7 8f 11 41  f9 99 96 69 0d 4a dd 06  |E......A...i.J..|
000000e0  00 33 0b d6 d0 f1 06 48  d5 d2 70 9c 06 06 af a9  |.3.....H..p.....|
000000f0  42 60 01 21 b5 b1 a2 6f  49 a5 0d 27 1d 39 36 f8  |B`.!...oI..'.96.|
00000100  1d be ed 42 9c 6d 41 28  0a 8a f4 42 a9 17 0c d6  |...B.mA(...B....|
00000110  69 19 5d a5 bd 6a 3e 44  91 1e 37 0a 46 74 cf 88  |i.]..j>D..7.Ft..|
00000120  c2 5e 5e 9a 94 8e f8 fd  1c 21 65 80 cf ca 24 b8  |.^^......!e...$.|
00000130  88 a0 87 54 e2 66 d8 f1  ad 78 95 8b 6a 38 b0 76  |...T.f...x..j8.v|
00000140  dd 17 ed ea ab 22 46 1e  09 2c 62 f3 7c 7e 21 33  |....."F..,b.|~!3|
00000150  aa 1c 2f 57 38 94 ac e7  b9 6a e7 65 af 04 23 c4  |../W8....j.e..#.|
00000160  99 2f 6a 7b 15 36 7e 18  0c 83 c9 73 f2 d0 6a 66  |./j{.6~....s..jf|
00000170  1b f2 44 18 13 23 30 da  11 ea 2e 92 77 94 ac b5  |..D..#0.....w...|
00000180  62 2d e4 d6 45 19 3b be  9f 3b bd 1b b5 9f a6 b4  |b-..E.;..;......|
00000190  66 c8 f6 41 06 7e 1c b9  50 2f a6 4a 67 e7 16 c9  |f..A.~..P/.Jg...|
000001a0  e2 d5 ab c6 f0 58 53 24  80 a8 9c 43 8a 07 be bf  |.....XS$...C....|
000001b0  58 85 b6 ba e4 54 66 b8  52 ac d2 09 62 3c 00 fe  |X....Tf.R...b<..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 5a 03 00 fe  |...........0Z...|
000001d0  ff ff 05 fe ff ff 02 30  5a 03 00 60 26 00 00 00  |.......0Z..`&...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 20 01 00  |.<.MSWIN4.1.. ..|
00000010  02 00 02 00 00 f8 f8 00  20 00 00 01 20 00 00 00  |........ ... ...|
00000020  e0 fb 1e 00 80 01 29 00  00 00 00 4e 4f 20 4e 41  |......)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


```

---

### Post by drs305 on 2010-08-30
Thanks for posting the RESULTS.txt.

I don't see anything obviously wrong with what Grub2 sees. In cases like this, I recommend booting the LiveCD and completely removing and reinstalling Grub2. It normally solves the issue. Just be sure you have a steady power supply and Internet connection, as for a brief time you will not have a bootloader on your system. 

Since you unsuccessfully tried a normal reinstall, from the LiveCD desktop, purge Grub2 with the first command - it will remove grub-pc and grub-common. You will be warned that you won't have a bootloader - that's ok.

```
sudo apt-get purge grub-common
```

Next, reinstall both packages with the following command. Just tab to OK for the info message and accept the defaults for the command line by tabbing to "OK" and pressing ENTER.

For the partitioning section, tab to "sda" and press the spacebar to select it. Do NOT select a specific partition. Then tab to OK and press ENTER to install Grub 2.

```
sudo apt-get install grub-pc
```

Once installed, try rebooting. If it works, you may need to run "sudo update-grub" once more if Windows was not displayed on the Grub2 menu.

---

### Post by danielsender on 2010-08-30
I'm getting an error: in the window saying "GRUB install devices:" I selected /dev/sda (in red, first line) and type return, it comes back with a message:

Please specify the module with the option '--modules' explicitely.

and also:

GRUB failed to install to the following devices:

/dev/sda

Do you want to continue anyway? Ì you do, your computer may not start up properly

GRUB installation failed. Continue?

---

### Post by drs305 on 2010-08-30
Just to be clear about where you are...

You are using a recent LiveCD.

You should have been warned about uninstalling the bootloader. You advanced to the next page by tabbing to "OK" and pressing ENTER.
Next, you had a chance to add any command line options. Normally, none are needed so you tab to "OK" and again press ENTER.

Next you got to the partitioning section.  "sda" was highlighted, you pressed the spacebar which placed an asterisk next to "sda". That was the only device with an *. You then tabbed to highlight "OK" and then pressed ENTER.

And you got the error message you reported. Is that correct?

I would suggest exiting the script and trying the procedure again. If you have any questions just ask before running the series of commands again.

You may also want to open Gparted (System, Administration, Gparted) to see if Gparted sees your partitions correctly and with the proper formatting.

---

### Post by danielsender on 2010-08-30
Exactly. The live CD is 10.04 and I did as you wrote. I will try again.
Thanks.

Daniel

---

### Post by danielsender on 2010-08-30
I just repeated the procedure and got the same results. I checked gparted and all the partitions seem ok. As part of the long message of the error it says:

/usr/bin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)

---

### Post by drs305 on 2010-08-30
I'm not sure another approach would work since I can't give you an explanation of why Grub isn't seeing the device. But my next recommendation would be to try one of the three installation methods detailed in the Grub2 community documentation.

One or more may be the one you tried from the Grub2 wiki. I helped a bit on the Grub2 wiki but am not familiar with what it now contains as compared to the Grub 2 community doc.
[Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Added: Just so you know, I just purged and reinstalled G2 on my Lucid install and it worked as advertised, so there doesn't appear to be a bug issue with the current files.

---

### Post by danielsender on 2010-08-30
The methods listed in that page assume that grub-pc is already ínstalled ("grub-install"). Since I purged grub I don't have it anymore and it refuses to install. With the method you describe, do I need to mount /dev somewhere or the installation of grub-pc knows about it?

Thanks,

Daniel

---

### Post by oldfred on 2010-08-31
Do you have a BIOS that has a lockout on the MBR?

A few BIOS have a setting to prevent overwriting the mbr and that has to be unset or allowed to write a new MBR.

---

### Post by danielsender on 2010-08-31
I don't think that is the problem. When I installed 10.04, it changed whatever was in the mbr, since it was displaying the "grub rescue>" prompt. Without knowing anything about grub, it seems that it does not "see" where the grub files are, for example when I type:

grub rescue> ls /

it lists all the stuff below / , but if I do:

grub rescue> ls /etc

it responds with the dreadful:

out of disk

Unfortunately I don't have anything anymore, since I purged grub and now the installer refuses to write on /dev , I wonder if I have to mount /dev when I install from the live CD, 
or the installer knows about /dev.

---

### Post by drs305 on 2010-08-31
> **danielsender said:**
> 
Unfortunately I don't have anything anymore, since I purged grub and now the installer refuses to write on /dev , I wonder if I have to mount /dev when I install from the live CD, 
or the installer knows about /dev.

The Ubuntu and Grub installer definitely know about /dev when working properly. The chroot method I linked to in the Grub2 doc mounts what is needed to install the boot files. Using that method would at least immediately show problems if you try to mount, for instance, /dev  or /dev/pts and are unable to do so.

If you can't do that, other than possibly fixing things by running fsck on /dev/sda via the LiveCD, the only other thing I can recommend is reinstalling Ubuntu. I know you would lose your customizations and data you have in /home - can you mount /dev/sda5 and copy files via the LiveCD?

---

### Post by danielsender on 2010-08-31
I htink that running apt-get from the live CD is not working. I ran:

sudo apt-get purge grub-common
ubuntu@ubuntu:~$ sudo apt-get purge grub-common

and got this:

```
ubuntu@ubuntu:~$ sudo apt-get purge grub-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 6,615kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129800 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
```

after I ran it again, and got:

```
ubuntu@ubuntu:~$ sudo apt-get purge grub-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package grub-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Apparently everything is OK, however when I re-booted the machine with the live CD and ran the command again, I got the same first response, as if it was actually removing the package. So I mounted /dev/sda5 and the whole grub was still there (/boot/grub), so in effect nothing was removed. So I suspect that that is the same reason why it couldn't write on /dev , or am I missing something?

Daniel

---

### Post by drs305 on 2010-08-31
The fault is mine - I didn't give you good enough instructions. In your case, you need to chroot into your normal installation. Running the command the way you did uninstalled grub-pc from your LiveCD running, but not from your actual installation. That's why it was there again when you rebooted the LiveCD.

You will need to follow the chroot commands from the Grub2 documentation. Once you have chroot'ed into your real partition after mounting the /dev files, *only then* will you run the purge and reinstall commands so they act on the partition files and not the LiveCD setup.

---

### Post by danielsender on 2010-08-31
This is getting quite frustrating. I did chroot, but then the installer couldn't log on the system even having a good internet connection. So in desperation I re-installed the whole system with the live CD, but everything is the same... "out of disk", "grub rescue>" any ideas???

Thanks,

Daniel

---

### Post by T3kG33k on 2010-09-01
I'm getting the same trouble.  I had a working 9.04 installation on a latitude d610 with a 320GB HDD and a working 9.10 installation on a latitude d630 with a 80GB HDD.  I completely reformatted and installed 10.04 on ext4 file system without issue.  My d610 won't boot at all under ext4 with 9.10 or 10.04.

I'm either booting into grub rescue or receivingout of disk error with 10.04.  With 9.04 I'm receiving "error: no such device."  "failed to boot default entries"

I've searched and tried everything I can find on google including the steps listed in this thread I'm not getting anywhere.  Could it be that there's a compatibility issue?

I'm going to attempt an install of 10.04 with ext3 and post my results.

EDIT:  Well I just finished installing again.  No change.  Back to Grub Rescue and out of disk on an ext3 file system.

---

### Post by drs305 on 2010-09-01
T3kG33k,

Even though your situation may be similar to the OP's, your best course of action is to monitor this thread but also to create a new post of your own.

Explain your situation, and include the contents of the RESULTS.txt generated by the boot info script downloaded and run by following *meierfra's* instructions on this site:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by drs305 on 2010-09-01
I keep coming back to this thread. At the moment, the only two things that come to mind - fix the partition problem with sdb (/dev/sdb1 ends after the last sector of /dev/sdb). You might be able to use Test Disk to clean it up from the LiveCD. Here is a link to using Test Disk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

A simpler thing to try would be to press "e" at the Grub menu and delete the "recordfail" line by holding down the DEL key. You can see if bypassing the recordfail check might allow G2 to boot the OS.

---

### Post by danielsender on 2010-09-01
I ran testdisk and it comes back with the message:

"Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)

Is this important? Does it have anything to do with grub? If it has to be fixed, how to I do it? From reading in some website about the "out of disk" issue, they say that BURG does not have the problem, well I tried and get the same thing, so I uninstalled BURG and went back to GRUB. Should I throw the towel now?...

Daniel

---

### Post by drs305 on 2010-09-01
I've successfully used Test Disk to recover from several pretty major disk problems but I'm no expert in its use - any instructions I gave you would be from searches via Google. Test Disk sometimes 'guesses' and before you start messing with repairs that may or may not be required consider the following.

Before throwing in the towel, here are two things I might try first:

1. Disconnect the second drive to see if the disk error is what is causing all the problems. If Grub still didn't boot after disconnecting it, you might try reinstalling Grub and running through the initial setup again (without the second drive connected).

2. Give up on Grub for the moment and see if Windows will still run. You can restore the Windows MBR via this link:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708").

If you don't have the Windows CD, you can also put restore the MBR by using the LiveCD and *lilo*. 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
When installing lilo it will complain a bit about a full installation, but just ignore the warning. You aren't really going to use lilo as the bootloader, only to rewrite the MBR. 

3. If neither of the above works, Google probably has enough information to help you throw in the towel. That is not to say that someone doesn't have the answer, it just means that I probably don't.  ](*,)

---

### Post by danielsender on 2010-09-01
I don't have a second drive. The 2 systems (xp and 10.04) are placed side-by-side on a 160GB HD. I experimented with an old 20GB disk that I had sitting there and installed 10.04 by itself (no windows). Everything went fine (except for some pkg installation error), the system boots properly, however since it is not a dual system the grub menu does not appear. I wonder if this is an indication that is not a bios problem. I would really like to have xp on the system so I wonder if the problem is related to having 2 systems side-by-side.

---

### Post by drs305 on 2010-09-01
The results.txt shows an "sdb". It is perhaps just a thumb drive - remove it and any other type of removable storage devices you have attached to the system and reboot.

The side-by-side setup in and of itself should not be a problem. The link and/or instructions I gave on how to restore the MBR so Windows (at least) boots should work.

---

