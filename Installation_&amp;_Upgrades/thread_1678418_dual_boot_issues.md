---
title: "dual boot issues"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by stompy11 on 2011-01-30
hello and thank you for reading my post,
I am attempting to dual boot my desktop(amd cpu, ati vid card[hd2900gt], 4 gigs of memory. so first off the only way i can install ubuntu is with the alternet cd(so no live cd). also i can format and reinstall no problem. now what i have done is removed all partitions from the HDD then made a partition using 50% of the drive and installed windows 7 64 ultimate, at this point everything is working great. after a few reboots to test it I install meerkat on the unpartitioned space, used grub2 and restarted. at this point ubuntu works perfectly and grub shows all OS's so then i try to run win7 and all i get is a blinking cursor, I pop in my 7 disk and run startup repair, no problems found, so i run fixmbr and fixboot. as you would imagine i can now only boot into windows but it works perfectly. so i put my ubuntu cd back in and fix grub using the recover broken system and the auto fix for grub. and i am back to linux working but windows giving me a blinking cursor.
P.S. during this i cannot access the f6 menu to try safemode. I think the problem resides in grub not mounting the hdd properly but i truly dont know.

---

### Post by Quackers on 2011-01-30
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2011-01-30
While you have Ubuntu booting please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by stompy11 on 2011-01-30
thank you for the quick reply i am repairing grub right now to run this command i will get back with you as soon as that is done.

---

### Post by stompy11 on 2011-01-30
sorry i failed to mention that i am using kubuntu, but when i run the "boot_info_script" thing i get "bash: /home/(username)/desktop/boot_info_script*.sh: No such file or directory"

---

### Post by Quackers on 2011-01-30
Is the boot script on your desktop? If not, copy/paste it there first.

---

### Post by kansasnoob on 2011-01-30
What directory is the script in?

I always just use cd to navigate to the proper directory and then run "sudo bash boot_info_script055.sh".

Example:

```
lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ sudo bash boot_info_script055.sh
[sudo] password for lance: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Finished. The results are in the file RESULTS2.txt located in /mnt/sda7

```

If it were on the Desktop I'd "cd Desktop".

---

### Post by stompy11 on 2011-01-30
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1465143295 sectors, but according to the info from 
                       fdisk, it has 1465144001 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   146,524,159   146,317,312   7 HPFS/NTFS
/dev/sda3         146,526,206   293,046,271   146,520,066   5 Extended
/dev/sda5         146,526,208   286,984,191   140,457,984  83 Linux
/dev/sda6         286,986,240   293,046,271     6,060,032  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,465,144,064 1,465,144,002  42 SFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8168 MB, 8168931328 bytes
39 heads, 4 sectors/track, 102275 cylinders, total 15954944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192    15,954,942    15,946,751   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        58E060DAE060C03C                       ntfs       System Reserved               
/dev/sda2        8E9463B594639E89                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        d450123a-fa26-4294-85a5-7233f52b3c8f   ext4                                     
/dev/sda6        19202b66-978e-4492-86ab-26bc6ffbf8ba   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        26F2DC2DF2DC034B                       ntfs       videos                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        CCF8-BB8C                              vfat       NO LABEL                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Kubuntu 10.10 amd64 iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/NO LABEL          vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b67cd3407cd2f9d7
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=d450123a-fa26-4294-85a5-7233f52b3c8f	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=B67CD3407CD2F9D7	/media/System_Reserved	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=1E6CDEE96CDEBAAB	/media/sda2	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=19202b66-978e-4492-86ab-26bc6ffbf8ba	none	swap	sw	0	0



=================== sda5: Location of files loaded by Grub: ===================


 115.9GB: boot/grub/core.img
 135.3GB: boot/grub/grub.cfg
  76.0GB: boot/initrd.img-2.6.35-22-generic
  76.0GB: boot/initrd.img-2.6.35-25-generic
 115.9GB: boot/vmlinuz-2.6.35-22-generic
 115.9GB: boot/vmlinuz-2.6.35-25-generic
  76.0GB: initrd.img
  76.0GB: initrd.img.old
 115.9GB: vmlinuz
 115.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  aa aa 85 31 65 31 5f ff  ee aa 85 31 65 31 d5 ff  |...1e1_....1e1..|
00000010  ff bb 85 31 65 31 ff bf  be aa 65 29 85 39 aa aa  |...1e1....e).9..|
00000020  aa aa 85 31 65 31 f7 7f  7f 5f 65 31 45 29 80 80  |...1e1..._e1E)..|
00000030  a8 00 65 31 45 29 aa 2a  02 00 65 31 85 31 a8 a8  |..e1E).*..e1.1..|
00000040  aa aa 66 39 85 31 ff ff  ff f7 66 39 85 31 ff ff  |..f9.1....f9.1..|
00000050  ff ff 65 31 24 29 80 c0  e0 e0 65 31 24 29 d8 72  |..e1$)....e1$).r|
00000060  e3 ff 65 31 24 29 ea af  0d a5 65 31 24 29 ab 3f  |..e1$)....e1$).?|
00000070  be ff 65 31 24 29 ff fa  e0 f8 65 31 44 29 ab ea  |..e1$)....e1D)..|
00000080  fb 83 65 31 44 29 fa e3  8b 2b 65 31 45 29 a2 8b  |..e1D)...+e1E)..|
00000090  2b a8 65 31 44 29 fa 2a  aa 80 65 31 24 29 0b aa  |+.e1D).*..e1$)..|
000000a0  e2 82 65 31 24 29 aa f8  c2 0a 65 31 24 29 f8 e2  |..e1$)....e1$)..|
000000b0  0b 2e 65 31 24 29 80 0b  2e be 85 31 24 29 0f fe  |..e1$).....1$)..|
000000c0  fa fa 65 31 44 29 fe 78  c2 0b 65 31 24 29 a0 a2  |..e1D).x..e1$)..|
000000d0  0f 3e 65 31 44 29 03 2e  aa a8 85 31 24 29 ba 78  |.>e1D).....1$).x|
000000e0  f8 8b 86 39 44 29 5e f9  0d 83 85 31 24 29 c2 f0  |...9D)^....1$)..|
000000f0  fc bf a6 39 44 29 b5 8f  6b 7a 86 39 44 29 fc bf  |...9D)..kz.9D)..|
00000100  0f 83 a6 39 65 31 75 5a  57 d5 a6 39 65 31 95 85  |...9e1uZW..9e1..|
00000110  7a 56 a6 39 65 31 56 d5  0d c9 a6 39 65 31 6d 52  |zV.9e1V....9e1mR|
00000120  54 55 a5 39 65 31 55 55  bf 7b a6 39 65 31 f5 5a  |TU.9e1UU.{.9e1.Z|
00000130  f7 f5 a6 39 65 31 fd fb  ea fe a6 39 85 31 c3 e2  |...9e1.....9.1..|
00000140  ad bd a6 39 85 31 69 8a  fa bc a6 39 65 31 0b 0b  |...9.1i....9e1..|
00000150  02 02 c6 39 86 39 af 2f  2a 2f e7 41 a6 39 fd ff  |...9.9./*/.A.9..|
00000160  ff ff e7 41 c6 39 ff ff  ff fe c6 39 e7 41 a8 8a  |...A.9.....9.A..|
00000170  aa aa e7 41 c6 39 aa 2a  0a 02 e6 41 e8 39 aa aa  |...A.9.*...A.9..|
00000180  aa aa e7 41 e6 39 2a 8a  0a 0a e7 41 07 42 a0 a8  |...A.9*....A.B..|
00000190  aa aa e7 41 07 42 aa aa  aa aa 07 42 e7 41 af af  |...A.B.....B.A..|
000001a0  af af e8 49 07 42 ff ff  ff ff 08 4a 07 42 f7 ff  |...I.B.....J.B..|
000001b0  ff ff 08 4a 07 42 ff ff  ff ff 27 4a e8 41 00 fe  |...J.B....'J.A..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 5f 08 00 fe  |...........8_...|
000001d0  ff ff 05 fe ff ff ca 3b  5f 08 38 7c 5c 00 00 00  |.......;_.8|\...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-01-30
According to the boot script output you have 2 hard drives. A 150GB drive, which has Win 7 on the first 2 partitions, and Ubuntu 10.10 on sda5 with a swap partition on sda6.
The second hard drive is  750GB and has a problem. It shows only one partition with a SFS or dynamic disk. This is often caused by creating a fifth primary partition on an mbr partitioned disc. In these circumstances Win 7 will convert your windows partitions to dynamic disks (SFS) and be unreadable to other operating systems, making it impossible to install.

I take it that your 150GB drive is set to boot first in your bios settings, is that correct? Is the machine a Dell, by any chance? If so, do you have Dell Data Safe installed?

---

### Post by stompy11 on 2011-01-30
ok first no not a dell, i built this myself... as for the second drive my apologies i connected my second drive and before i fixed grub this time i will disconnect it, fix grub and deliver the output, at this time i am just trying to get the 150GB drive fully going then i can format the 750 and go from there.
sorry for the confusion the 750 was involved while i was trying to do this the first time myself.
again thank you for all the help.

---

### Post by Quackers on 2011-01-30
No problem. Have fun :-)
Do you have any software installed in Windows that writes to the mbr of the drive? Photoshop can do it, I believe, and certain other programs, like Flexnet. This could be why every time you boot Windows, you need to re-install grub to boot Ubuntu.

---

### Post by stompy11 on 2011-01-30
new and improved boot info!!!

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   146,524,159   146,317,312   7 HPFS/NTFS
/dev/sda3         146,526,206   293,046,271   146,520,066   5 Extended
/dev/sda5         146,526,208   286,984,191   140,457,984  83 Linux
/dev/sda6         286,986,240   293,046,271     6,060,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        58E060DAE060C03C                       ntfs       System Reserved               
/dev/sda2        8E9463B594639E89                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        d450123a-fa26-4294-85a5-7233f52b3c8f   ext4                                     
/dev/sda6        19202b66-978e-4492-86ab-26bc6ffbf8ba   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Kubuntu 10.10 amd64 iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d450123a-fa26-4294-85a5-7233f52b3c8f ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set d450123a-fa26-4294-85a5-7233f52b3c8f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b67cd3407cd2f9d7
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=d450123a-fa26-4294-85a5-7233f52b3c8f	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=B67CD3407CD2F9D7	/media/System_Reserved	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=1E6CDEE96CDEBAAB	/media/sda2	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=19202b66-978e-4492-86ab-26bc6ffbf8ba	none	swap	sw	0	0



=================== sda5: Location of files loaded by Grub: ===================


 115.9GB: boot/grub/core.img
 135.3GB: boot/grub/grub.cfg
  76.0GB: boot/initrd.img-2.6.35-22-generic
  76.0GB: boot/initrd.img-2.6.35-25-generic
 115.9GB: boot/vmlinuz-2.6.35-22-generic
 115.9GB: boot/vmlinuz-2.6.35-25-generic
  76.0GB: initrd.img
  76.0GB: initrd.img.old
 115.9GB: vmlinuz
 115.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  aa aa 85 31 65 31 5f ff  ee aa 85 31 65 31 d5 ff  |...1e1_....1e1..|
00000010  ff bb 85 31 65 31 ff bf  be aa 65 29 85 39 aa aa  |...1e1....e).9..|
00000020  aa aa 85 31 65 31 f7 7f  7f 5f 65 31 45 29 80 80  |...1e1..._e1E)..|
00000030  a8 00 65 31 45 29 aa 2a  02 00 65 31 85 31 a8 a8  |..e1E).*..e1.1..|
00000040  aa aa 66 39 85 31 ff ff  ff f7 66 39 85 31 ff ff  |..f9.1....f9.1..|
00000050  ff ff 65 31 24 29 80 c0  e0 e0 65 31 24 29 d8 72  |..e1$)....e1$).r|
00000060  e3 ff 65 31 24 29 ea af  0d a5 65 31 24 29 ab 3f  |..e1$)....e1$).?|
00000070  be ff 65 31 24 29 ff fa  e0 f8 65 31 44 29 ab ea  |..e1$)....e1D)..|
00000080  fb 83 65 31 44 29 fa e3  8b 2b 65 31 45 29 a2 8b  |..e1D)...+e1E)..|
00000090  2b a8 65 31 44 29 fa 2a  aa 80 65 31 24 29 0b aa  |+.e1D).*..e1$)..|
000000a0  e2 82 65 31 24 29 aa f8  c2 0a 65 31 24 29 f8 e2  |..e1$)....e1$)..|
000000b0  0b 2e 65 31 24 29 80 0b  2e be 85 31 24 29 0f fe  |..e1$).....1$)..|
000000c0  fa fa 65 31 44 29 fe 78  c2 0b 65 31 24 29 a0 a2  |..e1D).x..e1$)..|
000000d0  0f 3e 65 31 44 29 03 2e  aa a8 85 31 24 29 ba 78  |.>e1D).....1$).x|
000000e0  f8 8b 86 39 44 29 5e f9  0d 83 85 31 24 29 c2 f0  |...9D)^....1$)..|
000000f0  fc bf a6 39 44 29 b5 8f  6b 7a 86 39 44 29 fc bf  |...9D)..kz.9D)..|
00000100  0f 83 a6 39 65 31 75 5a  57 d5 a6 39 65 31 95 85  |...9e1uZW..9e1..|
00000110  7a 56 a6 39 65 31 56 d5  0d c9 a6 39 65 31 6d 52  |zV.9e1V....9e1mR|
00000120  54 55 a5 39 65 31 55 55  bf 7b a6 39 65 31 f5 5a  |TU.9e1UU.{.9e1.Z|
00000130  f7 f5 a6 39 65 31 fd fb  ea fe a6 39 85 31 c3 e2  |...9e1.....9.1..|
00000140  ad bd a6 39 85 31 69 8a  fa bc a6 39 65 31 0b 0b  |...9.1i....9e1..|
00000150  02 02 c6 39 86 39 af 2f  2a 2f e7 41 a6 39 fd ff  |...9.9./*/.A.9..|
00000160  ff ff e7 41 c6 39 ff ff  ff fe c6 39 e7 41 a8 8a  |...A.9.....9.A..|
00000170  aa aa e7 41 c6 39 aa 2a  0a 02 e6 41 e8 39 aa aa  |...A.9.*...A.9..|
00000180  aa aa e7 41 e6 39 2a 8a  0a 0a e7 41 07 42 a0 a8  |...A.9*....A.B..|
00000190  aa aa e7 41 07 42 aa aa  aa aa 07 42 e7 41 af af  |...A.B.....B.A..|
000001a0  af af e8 49 07 42 ff ff  ff ff 08 4a 07 42 f7 ff  |...I.B.....J.B..|
000001b0  ff ff 08 4a 07 42 ff ff  ff ff 27 4a e8 41 00 fe  |...J.B....'J.A..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 5f 08 00 fe  |...........8_...|
000001d0  ff ff 05 fe ff ff ca 3b  5f 08 38 7c 5c 00 00 00  |.......;_.8|\...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by stompy11 on 2011-01-30
as far as i know, no i dont it is a freash install with nothing but updates ran, I rebooted after updates and got no change.

---

### Post by Quackers on 2011-01-30
That looks fine. I can't see why you should have any booting problems.
The only thing is, as mentioned above, if you have any software installed in Windows, which writes to the mbr of the drive, it can over-write grub every time.

An anti-virus may cause it too.

---

### Post by stompy11 on 2011-01-30
i am booting windows, after post grub2 comes up, options 4 ubuntu choices, 2 memtest and windows 7 (loader) (on /dev/sda1). one second after selecting, the screen turns off for about .5 seconds then i get a black screen with a blinking cursor in the top left corner.


edit: I remember when i was doing this with several drives that i could not access the drive that kubuntu was partitioned on.
also microsoft security essentials is installed.

---

### Post by Quackers on 2011-01-30
All I can think of is fix the Windows bootloader again and then try running a chkdsk on the C: partition.
```
chkdsk C: /r
```
from the command prompt in the recovery console would do that. If it reports any errors run it again until no errors are reported.
It's an odd one though.

---

### Post by stompy11 on 2011-01-30
I'm going to reinstall starting with kubuntu first and see if that helps.

---

### Post by stompy11 on 2011-01-30
ok so i reinstalled both os's(kubuntu first), restored grub and now it goes directly to kubuntu, i dont even see grub.

ran "sudo update-grub"
now i am back to the blinking cursor. :(

finished chkdsk, no errors.

---

