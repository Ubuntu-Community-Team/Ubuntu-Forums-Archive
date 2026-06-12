---
title: "Windows ubuntu dual boot, ubuntu not working after install Xp"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by inmank on 2012-01-27
Hi,
I am using ubantu and windows as dual boot for quite some time, just before I have reinstalled windows xp and after the installation is completed I am not able to see the boot menu Its always loading into windows XP I am confident I have not deleted or formatted the ubantu partition. Any help would be more helpfull.

---

### Post by darkod on 2012-01-27
On every install windows is writing the windows bootloader on the MBR of the disk without asking you. That will delete grub2 from the MBR.

After any windows install, you only need to reinstall (restore) your grub2 to the MBR. You can follow this guide (it has commands for grub2/grub1 and windows also):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by inmank on 2012-01-27
Hi Darko,
 
Thanks for your help. But I have One doubt, In the tutorial It saya how to restore the bootloader for different OS. I my case I am able to login only to windows xp. If do the steps given for windows XP, will it solve the problem. Will I get the boot menu with option to select ubantu also.

---

### Post by darkod on 2012-01-27
You will have to do the grub2 reinstall from ubuntu live mode (Try Ubuntu from the cd). If you don't have a cd you can download the image and burn a cd in windows. Then boot with it and you can reinstall grub2. It has to be with ubuntu cd or bootable usb stick.

---

### Post by inmank on 2012-01-27
Thanks, Just now burned a ubantu disk. i will try and let u know the result.

---

### Post by inmank on 2012-01-27
Hi,

I got the following error when tried to follow the steps given in the link.

Kindly help

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7bd3e3d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        3187    10241437+   7  HPFS/NTFS
/dev/sda3            3188       19456   130680321    f  W95 Ext'd (LBA)
/dev/sda4            5100       19456   115322571    7  HPFS/NTFS
/dev/sda5            3188        4525    10741760   83  Linux
/dev/sda6            4525        5099     4614144   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
ubuntu@ubuntu:~$

---

### Post by darkod on 2012-01-27
The last command is /dev/sda, without the '5'.

You mount /dev/sda5 but with the grub-install you install onto /dev/sda (the MBR).

---

### Post by inmank on 2012-01-27
Hi

This worked thanks. i was confused by this statement " Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.".

Thank you very much for your help. Let me boot from ubantu and let you know the result.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
ubuntu@ubuntu:~$

---

### Post by inmank on 2012-01-27
This s completely working now. 
Darko thank you very much for your help.

---

### Post by darkod on 2012-01-27
No problem. Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

### Post by inmank on 2012-01-27
Hi Darko

Now the ubantu is booting fine. But the other file systems were not shown and also the disk utilities is not working

While booting xp it shows error no such device :<some number>
and if i press enter It continues to load and works fine.

Can you help me on this.

---

### Post by darkod on 2012-01-27
The error no such device is from grub. But after selecting XP in the first grub2 boot menu there should not be another grub.

Follow the link in my signature to run the boot info script as explained there. Post the results here, again as explained. They will show more details.

---

### Post by inmank on 2012-01-27
Please find the result of the bash script

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda4 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda4 starts at sector 81915498.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 NTFS / exFAT / HPFS
/dev/sda2          30,716,280    51,199,154    20,482,875   7 NTFS / exFAT / HPFS
/dev/sda3          51,199,998   312,560,639   261,360,642   f W95 Extended (LBA)
Extended partition linking to another extended partition.
/dev/sda5          51,200,000    72,683,519    21,483,520  83 Linux
/dev/sda6          72,685,568    81,913,855     9,228,288  82 Linux swap / Solaris
/dev/sda4          81,915,498   312,560,639   230,645,142   7 NTFS / exFAT / HPFS

/dev/sda3 overlaps with /dev/sda4

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        36F8522EF851EC9D                       ntfs       
/dev/sda2        66FC2924FC28F04B                       ntfs       
/dev/sda4        0C6CBD2E6CBD1404                       ntfs       
/dev/sda5        2173d1e0-2e57-4442-98d1-2b3cc360d504   ext3       
/dev/sda6        3ecc97af-2003-4c41-9fe1-d6e9d39ee688   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=2173d1e0-2e57-4442-98d1-2b3cc360d504 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=2173d1e0-2e57-4442-98d1-2b3cc360d504 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=2173d1e0-2e57-4442-98d1-2b3cc360d504 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=2173d1e0-2e57-4442-98d1-2b3cc360d504 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2173d1e0-2e57-4442-98d1-2b3cc360d504
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 5454E99C54E980DA
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
/dev/sda6       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=3ecc97af-2003-4c41-9fe1-d6e9d39ee688 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             2
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-10-generic              5
               =                boot/initrd.img-3.0.0-12-generic               9
               =                boot/vmlinuz-2.6.38-10-generic                 4
               =                boot/vmlinuz-3.0.0-12-generic                  5
               =                initrd.img                                     9
               =                initrd.img.old                                 5
               =                vmlinuz                                        5
               =                vmlinuz.old                                    4

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  a1 ce 0b 03 6d 42 30 19  cf 85 59 e0 74 d0 66 ff  |....mB0...Y.t.f.|
00000010  fa 41 eb 85 83 c7 ff d0  8a 66 b5 91 ad c9 0b 20  |.A.......f..... |
00000020  4d b1 c7 8b 63 88 e3 e9  fe 63 c2 c8 1e 74 28 d1  |M...c....c...t(.|
00000030  7b 68 4d 14 3d 04 31 c0  03 d9 60 2c 27 5f 3e cd  |{hM.=.1...`,'_>.|
00000040  54 30 03 ea 91 d8 30 ff  fb 40 2f b0 0f a1 e6 54  |T0....0..@/....T|
00000050  80 19 1c 4f b0 19 aa 73  08 e3 a3 76 5c b5 01 aa  |...O...s...v\...|
00000060  11 85 fc dd e9 6a 51 02  de a0 63 40 06 d0 a8 dd  |.....jQ...c@....|
00000070  ed d7 42 21 9f 31 40 11  98 14 b9 c0 68 f0 1f 18  |..B!.1@.....h...|
00000080  47 fc e2 0c 8c 2f 13 f3  e6 9d 78 66 cb 3f f6 1c  |G..../....xf.?..|
00000090  4f 80 5e 06 ea 42 7e 1e  06 ef e7 76 23 90 26 c4  |O.^..B~....v#.&.|
000000a0  97 03 a0 76 c6 1a 06 a4  ba 5d 1f 33 8f fb 03 4f  |...v.....].3...O|
000000b0  ff d4 60 f5 91 2b 2f 70  01 7f e4 19 8e 4e 27 b9  |..`..+/p.....N'.|
000000c0  d6 93 f7 22 be 03 97 90  e7 ef cd 09 1e 46 83 9a  |...".........F..|
000000d0  a3 36 74 2c 2f 66 c4 f6  98 92 61 16 f6 17 83 8f  |.6t,/f....a.....|
000000e0  20 de 5e 65 87 b9 11 56  33 77 3c 5e c6 b4 b5 75  | .^e...V3w<^...u|
000000f0  91 c1 a7 ff ee 20 60 cf  f6 c7 87 8e 8e 5e 80 f0  |..... `......^..|
00000100  0d 25 73 40 d4 4a 46 43  33 73 6f 87 d4 66 c3 08  |.%s@.JFC3so..f..|
00000110  2b 9b b7 fc 8b 95 08 cc  1d 80 d4 39 88 a4 10 01  |+..........9....|
00000120  ed 12 3a d4 1d fa b4 b3  98 1d bf fe 84 84 67 ce  |..:...........g.|
00000130  03 58 d3 a3 00 dc 6d 46  76 cb 92 d6 3c 07 d6 e7  |.X....mFv...<...|
00000140  7b a2 89 a0 84 98 07 08  12 dd c2 a0 65 ff f8 51  |{...........e..Q|
00000150  04 0d 57 01 7d 14 46 0c  6b b8 a6 58 89 2c 4b 7e  |..W.}.F.k..X.,K~|
00000160  00 36 87 eb 1d 45 16 81  00 38 02 02 c0 a8 20 ff  |.6...E...8.... .|
00000170  18 60 0e b8 0e 8d 04 5f  fa 2c b0 30 56 0f f8 b6  |.`....._.,.0V...|
00000180  80 7b c8 11 30 0c 14 03  b4 94 82 cb 01 4e 60 92  |.{..0........N`.|
00000190  d0 01 58 cc 70 fc 76 d3  a5 d8 63 8a ff ab 39 3e  |..X.p.v...c...9>|
000001a0  30 6b 93 b6 75 5c a2 60  06 40 0e 80 42 4d 00 70  |0k..u\.`.@..BM.p|
000001b0  00 d0 02 e0 1d 00 c4 35  7b 77 e9 29 c3 76 00 0d  |.......5{w.).v..|
000001c0  da ff 05 56 ea ff 01 00  00 00 01 d0 47 01 00 00  |...V........G...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

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

### Post by darkod on 2012-01-27
There is some confusion in the partition table.
/dev/sda4 is marked as primary partition but it seems it should be logical, inside the /dev/sda3 extended partition.
Do you remember if /dev/sda4 was logical or not?

A utility called fixparts should be able to repair issues like this.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Also I'm not sure how ubuntu boots successfully when /etc/fstab seems to be wrong, it says /dev/sda6 is your root when in fact it's /dev/sda5.
But if /dev/sda4 was a logical partition before, it might have been labeled /dev/sda5 so your root and swap would be sda6 and sda7. With sda4 marked as logical now, the numbers of root and swap changed.

---

### Post by inmank on 2012-01-27
I got the following output when I tried the steps given in that link.

I remember before installing xp i split the 26 GB partition into 15 and 10 GB and installed xp in 15GB partition.

 ```
MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 312581808 sectors (149.1 GiB)
MBR disk identifier: 0x7BD3E3D6
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             63     30716279   primary              Y      0x07
   2              30716280     51199154   primary              Y      0x07
   4              81915498    312560639   primary     Y        Y      0x07
   5              51200000     72683519   logical     Y               0x83
   6              72685568     81913855   logical     Y               0x82

MBR command (? for help): ^Ckarthik@Karthik-HomePC:~$ 

```

Kindly help me what needs to be fixed in this.

---

### Post by darkod on 2012-01-27
Well, we don't know for sure if #4 was earlier logical, but you can try setting it as logical with fixparts. I have never used it, but the command help says you use 'l' (small L) to set a partition to logical.

So, in the fixparts screen you posted, when it's asking you for a command try:
l

Not sure if it will ask you about the partition number later or you need to use something like:
l 4

To tell it to set #4 as logical.

After that print the table again with:
p

And see if #4 has changed status to logical. Note that the number might change because 1-4 is only reserved for primary partitions. Look at the start/end sector numbers, that way you can recognize partitions too, not only with their number.

If the type is changed to logical, try writing the new table with:
w

---

### Post by inmank on 2012-01-27
Please find the output. i will restart and let you know the result.

```
karthik@Karthik-HomePC:~$ sudo fixparts /dev/sda
[sudo] password for karthik: 
FixParts 0.8.0

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 312581808 sectors (149.1 GiB)
MBR disk identifier: 0x7BD3E3D6
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             63     30716279   primary              Y      0x07
   2              30716280     51199154   primary              Y      0x07
   4              81915498    312560639   primary     Y        Y      0x07
   5              51200000     72683519   logical     Y               0x83
   6              72685568     81913855   logical     Y               0x82

MBR command (? for help): ?
a	toggle the active/boot flag
c	recompute all CHS values
l	set partition as logical
o	omit partition
p	print the MBR partition table
q	quit without saving changes
r	set partition as primary
s	sort MBR partitions
t	change partition type code
w	write the MBR partition table to disk and exit

MBR command (? for help): l 4
Partition to set as logical: 
Specified change is not legal! Aborting change!

MBR command (? for help): l
Partition to set as logical: 4

MBR command (? for help): p

Disk size is 312581808 sectors (149.1 GiB)
MBR disk identifier: 0x7BD3E3D6
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             63     30716279   primary              Y      0x07
   2              30716280     51199154   primary              Y      0x07
   4              81915498    312560639   logical     Y        Y      0x07
   5              51200000     72683519   logical     Y        Y      0x83
   6              72685568     81913855   logical     Y               0x82

MBR command (? for help): w

Final checks complete. About to write MBR data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
Done writing data!
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot.
karthik@Karthik-HomePC:~$ 

```

---

### Post by inmank on 2012-01-27
Hi,

This approach fails. I got error unknown partition and even the grub boot loader screen is also not available. 
I am rolling the changes back. 
Is there anything else we can do to this.

---

### Post by darkod on 2012-01-27
I'm out of ideas, sorry. Maybe someone else will jump in.

---

### Post by inmank on 2012-01-27
Any way thank you for your help, so far. Also please find the output of the reverse operation of the fdisk command.

Kindly help me to understand one final step, will reinstalling ubantu solve this problem? Else it will affect the loading of windows xp.

```
ubuntu@ubuntu:~/Documents$ sudo sfdisk -f /dev/sda < parts.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1911    1912-  15358108+   7  HPFS/NTFS
/dev/sda2       1912    3186    1275   10241437+   7  HPFS/NTFS
        start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3       3187+  19455   16269- 130680320+   f  W95 Ext'd (LBA)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       3187+   4524-   1338-  10741760   83  Linux
/dev/sda6       4524+   5098-    575-   4614144   82  Linux swap / Solaris
/dev/sda7       5099+  19455   14357- 115322571    7  HPFS/NTFS
        start: (c,h,s) expected (1023,254,63) found (1023,1,1)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  30716279   30716217   7  HPFS/NTFS
/dev/sda2      30716280  51199154   20482875   7  HPFS/NTFS
/dev/sda3      51199998 312560639  261360642   f  W95 Ext'd (LBA)
/dev/sda4      81915498 312560639  230645142   7  HPFS/NTFS
/dev/sda5      51200000  72683519   21483520  83  Linux
/dev/sda6      72685568  81913855    9228288  82  Linux swap / Solaris
Warning: partition 3 does not start at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~/Documents$ 

```

---

### Post by inmank on 2012-01-28
Hi 

I don't know how it works but this is what I did.

In my last thread I restore the fdisk partition value to the old values. But still the Grub boot loader not displayed.

Then I use ubantu live CD and followed the steps to re installed the grub2 bootloader. Then I restarted the PC. It works Fine now.

Thank you very much for Darko for helping me on this.

---

