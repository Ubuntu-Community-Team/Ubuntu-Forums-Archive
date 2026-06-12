---
title: "Live USB 10.04 install. GRUB error"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by grimmscythe on 2010-12-17
Okay I reinstalled 10.04.(finally) on a single partition mounted as "/". everything went fine until I rebooted, GRUB began loading and then came back with "no modules name found". I found other postings with the same problem,[http://ubuntuforums.org/showthread.php?t=1343851](http://ubuntuforums.org/showthread.php?t=1343851) but this method doesn't work with the Dmraid. can anyone get me a "how to" or help me troubleshoot?

---

### Post by grimmscythe on 2010-12-17
No hints? No guesses? really want this back online. without GRUB working I have no computer.

---

### Post by grimmscythe on 2010-12-18
bump

---

### Post by sikander3786 on 2010-12-18
Hi.

Boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

As a side not, please don't bump your thread before 24 hours. There are members specifically looking for posts with '0' replies and they'll just pass-by your thread without even knowing that it hasn't yet been answered ;-)

---

### Post by grimmscythe on 2010-12-18
Thank you for your reply. I'm sorry for being Impatient, I'm rather frustrated at not having a computer working except the live USB. I will be more considerate in the future.
here is the Results.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_ebg and looks on the 
    same drive in partition #7 for /grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

pdc_ebg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

pdc_ebg2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_ebg5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_ebg6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

pdc_ebg3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         534,787,838   621,092,607    86,304,770   5 Extended
Invalid MBR Signature found
/dev/sda5     ?   534,787,838   534,787,837                   Unknown
/dev/sda6     ?   534,787,838   534,787,837                   Unknown
/dev/sda3         122,881,185   534,787,784   411,906,600   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2
/dev/sda3 ends after the last sector of /dev/sda

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sdc2          20,482,875    78,140,159    57,657,285   f W95 Ext d (LBA)
/dev/sdc5          20,482,938    61,448,624    40,965,687   7 HPFS/NTFS
/dev/sdc6          61,448,688    78,140,159    16,691,472   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2003 MB, 2003828736 bytes
43 heads, 42 sectors/track, 2167 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                 128     3,913,727     3,913,600   6 FAT16


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2003 MB, 2003828736 bytes
158 heads, 42 sectors/track, 589 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *              1     3,913,727     3,913,727  83 Linux


Drive: pdc_ebg ___________________ _____________________________________________________

Disk /dev/mapper/pdc_ebg: 318.0 GB, 317999939584 bytes
255 heads, 63 sectors/track, 38661 cylinders, total 621093632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_ebg1                 63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/mapper/pdc_ebg2        534,787,838   621,092,607    86,304,770   5 Extended
/dev/mapper/pdc_ebg5        534,787,840   538,787,839     4,000,000  82 Linux swap / Solaris
/dev/mapper/pdc_ebg6        538,788,096   621,092,607    82,304,512  83 Linux
/dev/mapper/pdc_ebg3        122,881,185   534,787,784   411,906,600   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_ebg1 5638134B3813298F                       ntfs                                     
/dev/mapper/pdc_ebg3 16E468EAE468CD95                       ntfs       games drive                   
/dev/mapper/pdc_ebg5 e1f11ee2-8c86-4846-b840-058e2b4323c8   swap                                     
/dev/mapper/pdc_ebg6 e5eeef9e-d554-4d75-b08d-12b51af3958b   ext3                                     
/dev/mapper/pdc_ebg: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        2E987DEF987DB645                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        CA68CE0D68CDF869                       ntfs                                     
/dev/sdc6        E09857AD98578148                       ntfs       data                          
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        E0FD-1813                              vfat       KINGSTON                      
/dev/sdd: PTTYPE="dos" 
/dev/sde1        0a776ac2-440b-4843-8e04-2cf26d23d810   ext3                                     
/dev/sde: PTTYPE="dos" 
error: /dev/mapper/pdc_ebg2: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_ebg
pdc_ebg1
pdc_ebg3
pdc_ebg5
pdc_ebg6

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   ext3       (ro,noatime,errors=continue,data=ordered)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/DragonAge         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect


============================== pdc_ebg1/boot.ini: ==============================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /fastdetect /usepmtimer /NoExecute=OptOut


========================= pdc_ebg6/boot/grub/grub.cfg: =========================

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
set root='(hd4,6)'
search --no-floppy --fs-uuid --set e5eeef9e-d554-4d75-b08d-12b51af3958b
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
set root='(hd4,6)'
search --no-floppy --fs-uuid --set e5eeef9e-d554-4d75-b08d-12b51af3958b
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd4,6)'
	search --no-floppy --fs-uuid --set e5eeef9e-d554-4d75-b08d-12b51af3958b
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e5eeef9e-d554-4d75-b08d-12b51af3958b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd4,6)'
	search --no-floppy --fs-uuid --set e5eeef9e-d554-4d75-b08d-12b51af3958b
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e5eeef9e-d554-4d75-b08d-12b51af3958b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd4,6)'
	search --no-floppy --fs-uuid --set e5eeef9e-d554-4d75-b08d-12b51af3958b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd4,6)'
	search --no-floppy --fs-uuid --set e5eeef9e-d554-4d75-b08d-12b51af3958b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows 2000 Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e987def987db645
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Professional x64 Edition (on /dev/mapper/pdc_ebg1)" {
	insmod ntfs
	set root='(hd4,1)'
	search --no-floppy --fs-uuid --set 5638134b3813298f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= pdc_ebg6/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_ebg6 /               ext3    errors=remount-ro 0       1
/dev/mapper/pdc_ebg5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= pdc_ebg6: Location of files loaded by Grub: =================


 286.6GB: boot/grub/core.img
 286.6GB: boot/grub/grub.cfg
 286.6GB: boot/initrd.img-2.6.32-24-generic
 286.6GB: boot/vmlinuz-2.6.32-24-generic
 286.6GB: initrd.img
 286.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda3


Unknown BootLoader  on sdc2

00000000  5e ba 49 12 c0 61 3f 60  f1 bf 3f 52 40 00 00 00  |^.I..a?`..?R@...|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 77 d4 a6  |.............w..|
00000020  a6 d1 6e 23 40 41 a2 cd  b3 d1 c3 07 40 00 00 00  |..n#@A......@...|
00000030  00 00 00 00 00 02 00 00  00 02 00 00 00 59 58 2f  |.............YX/|
00000040  dd 70 91 e1 40 fc 01 00  00 20 ba c3 0a cc 46 d9  |.p..@.... ....F.|
00000050  0b c7 d5 12 41 d0 10 3b  67 5f 6a 07 41 7d 3f 35  |....A..;g_j.A}?5|
00000060  5e ba 49 12 c0 eb 4d 5e  cb f8 7f 75 40 00 00 00  |^.I...M^...u@...|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 a2 89 d2  |................|
00000080  01 23 5e ff bf 67 16 54  8d 1a 59 1b 40 00 00 00  |.#^..g.T..Y.@...|
00000090  00 00 00 00 00 02 00 00  00 02 00 00 00 59 58 2f  |.............YX/|
000000a0  dd 70 91 e1 40 fd 01 00  00 20 ba c3 0a d9 38 3c  |.p..@.... ....8<|
000000b0  55 6a 00 13 41 b9 0b c6  7a 39 a8 06 41 7d 3f 35  |Uj..A...z9..A}?5|
000000c0  5e ba 49 12 c0 af f5 62  cb f8 7f 75 40 00 00 00  |^.I....b...u@...|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 be 56 c5  |..............V.|
000000e0  bd 0e 5e ff bf 31 63 1b  e2 08 59 1b 40 00 00 00  |..^..1c...Y.@...|
000000f0  00 00 00 00 00 02 00 00  00 02 00 00 00 8a 60 db  |..............`.|
00000100  f9 72 91 e1 40 05 00 00  00 20 ba c3 0a 17 8f 1f  |.r..@.... ......|
00000110  d0 32 6c 06 41 6f d5 92  89 1d 04 10 41 02 4d db  |.2l.Ao......A.M.|
00000120  4a b0 9c 8c 40 5f ea c6  0a 74 a9 71 40 3e 73 ea  |J...@_...t.q@>s.|
00000130  08 a7 32 dc bf 00 00 00  00 00 00 00 00 37 b7 16  |..2..........7..|
00000140  99 23 70 66 c0 81 62 6a  3e 1b 3d 3c 40 12 c3 58  |.#pf..bj>.=<@..X|
00000150  ac bf ea e7 3f 02 00 00  00 02 00 00 00 1d 79 df  |....?.........y.|
00000160  4f 79 91 e1 40 f5 01 00  00 20 ba c3 0a 96 f4 26  |Oy..@.... .....&|
00000170  dd 82 f8 07 41 e4 b1 9c  e6 c2 97 11 41 7d 3f 35  |....A.......A}?5|
00000180  5e ba 49 12 c0 ff ff ff  ff ff ff 51 40 00 00 00  |^.I........Q@...|
00000190  00 00 00 00 80 00 00 00  00 00 00 00 00 7a a7 a5  |.............z..|
000001a0  29 d9 53 23 40 c9 e2 70  0b 9d 1e 09 40 00 00 00  |).S#@..p....@...|
000001b0  00 00 00 00 00 02 00 00  00 02 00 00 00 1d 00 01  |................|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 37 16 71 02 00 00  |......?...7.q...|
000001d0  c1 ff 05 fe ff ff 76 16  71 02 4f b1 fe 00 00 00  |......v.q.O.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on pdc_ebg2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/pdc_ebg2: No such file or directory
hexdump: /dev/mapper/pdc_ebg2: No such file or directory
```
pdc_ebg6 is my new 10.04 install, sde is the boot-able live USB

---

### Post by sikander3786 on 2010-12-19
Ok. That seems pretty messy. I have not much experience with dmraid setups so I've requested some senior members to take a look and advise here. They'll be coming soon. Please hang in there :-)

---

### Post by grimmscythe on 2011-02-15
It finally fixed itself by updating GRUB with one of the ubuntu updates. the bootloader works now. still unsure of the original problem.

---

