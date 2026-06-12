---
title: "Ubuntu/Win7 dual boot - now Win7 won't load"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by rmm64 on 2010-12-31
Hi all, new user here hoping to get some help and save the day.

Some background. I was referred to Ubuntu 10.04 by a friend to fix a bad drive partition (not the boot drive) which worked great. I then also used it to recover some files that had accidentally been deleted. The Ubuntu utilities worked so well I decided to install and run a dual boot alongside Windows 7 Ultimate x64. Install went fine and Grub worked as it should, allowing the choice of which to boot at startup.

So after some time, I was notified upgrades were available, so I allowed them to install. After rebooting, Grub failed to load, thus I couldn't boot either OS. So, unsure what to do, I reinstalled Ubuntu again and was able to dual boot both OS again. Problem (semi) fixed and I was back in Win7 again for normal stuff.

So my computer freezes up overnight (while in Win7) and my wife restarts the computer not knowing about the previous probs. Now, no Grub loader, no OS boot, again. Rather than installing yet ANOTHER Ubuntu, I ran Testdisk off the CD and was able to fix the partition and get Grub to load again, only now I can only boot into Ubuntu. Selecting Windows 7 results in a load error forcing me to restart.

So right now I can only get into Ubuntu (which I've updated to v11.04 now.) I'm semi-certain it's either a problem with Grub or the MBR, but am unsure how to fix this without potentially messing it all up forcing me to reformat the drive and reinstall Win7 (there's a few valuable files I'd need to recover before doing that, as a very last resort.) It could be my installing Ubuntu twice now has messed up Grub too, but am unsure (it loaded either OS fine before the upgrade.)

I tried using Testdisk again to recover the partion, but either I'm not understanding the results shown, or the partition is missing (getting no results on the install drive, yet here I am using Ubuntu now.)

I'm hoping someone can help me figure this out and help me get my Win7 install to load again as I really need to recover some files before doing anything as drastic as reinstalling (plus the added pain of reinstalling all my software again.) I figured it was best to ask here before screwing something up even worse than it is (if I haven't already.) I've seen similar postings online with solutions, but was unsure of the suggested results as compared to my specific situation since there can be numerous variables.

I ran the boot_info_script as suggested in another thread, and can see Windows Vista/7 listed, so am hoping it's still recoverable and it's just a MBR or Grub error that can fixed. I do see where Grub 2 is installed into both sda and sdb, so maybe that's the issue too?

Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 3,907,026,943 3,907,024,896   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   977,290,203   977,288,156   7 HPFS/NTFS
/dev/sdb2         977,291,262 1,953,523,711   976,232,450   5 Extended
/dev/sdb5         977,291,264 1,929,746,431   952,455,168  83 Linux
/dev/sdb6       1,929,748,480 1,953,523,711    23,775,232  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdc1     ?             0            -1                   Unknown
/dev/sdc2     ?             0            -1                   Unknown
/dev/sdc3     ?             0            -1                   Unknown
/dev/sdc4     ?             0            -1                   Unknown


Drive: sdd ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdd1     ?             0            -1                   Unknown
/dev/sdd2     ?             0            -1                   Unknown
/dev/sdd3     ?             0            -1                   Unknown
/dev/sdd4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        66728F20728EF459                       ntfs       Samsung 2TB SATA              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C47C2ED67C2EC2D2                       ntfs       Western Digital 1TB SATA      
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        640e8599-2f10-4189-a953-980c1cd0895e   ext4                                     
/dev/sdb6        895f59a9-81be-4f97-a5e5-93ce6818b786   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc2: No such file or directory
error: /dev/sdc3: No such file or directory
error: /dev/sdc4: No such file or directory
error: /dev/sdd2: No such file or directory
error: /dev/sdd3: No such file or directory
error: /dev/sdd4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/Samsung_2TB_SATA  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/Western_Digital_1TB_SATA fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=640e8599-2f10-4189-a953-980c1cd0895e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=640e8599-2f10-4189-a953-980c1cd0895e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=640e8599-2f10-4189-a953-980c1cd0895e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=640e8599-2f10-4189-a953-980c1cd0895e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set 640e8599-2f10-4189-a953-980c1cd0895e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5ab0429bb0427d8f
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb5 :
UUID=640e8599-2f10-4189-a953-980c1cd0895e	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=66728F20728EF459	/media/Samsung_2TB_SATA	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdb1 :
UUID=C47C2ED67C2EC2D2	/media/Western_Digital_1TB_SATA	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdb6 :
UUID=895f59a9-81be-4f97-a5e5-93ce6818b786	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0



=================== sdb5: Location of files loaded by Grub: ===================


 582.1GB: boot/grub/core.img
 552.1GB: boot/grub/grub.cfg
 501.4GB: boot/initrd.img-2.6.32-27-generic
 501.8GB: boot/initrd.img-2.6.35-24-generic
 582.1GB: boot/vmlinuz-2.6.32-27-generic
 582.1GB: boot/vmlinuz-2.6.35-24-generic
 501.8GB: initrd.img
 501.4GB: initrd.img.old
 582.1GB: vmlinuz
 582.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc


Unknown MBR on /dev/sdd


Unknown BootLoader  on sdb2

00000000  ff ff ff ff fd 9e 17 9d  aa 2e 9b 57 95 ea 97 2a  |...........W...*|
00000010  ff ff ff ff ff ff e1 ba  14 37 1a 6d 9a af a6 99  |.........7.m....|
00000020  2e 96 40 18 88 54 f9 a5  24 69 61 2e 78 58 40 a4  |..@..T..$ia.xX@.|
00000030  24 27 ea b8 91 b7 05 58  d6 d3 8d 96 10 52 e8 2c  |$'.....X.....R.,|
00000040  cf 45 dd 0b 0a f4 42 a4  bc 89 29 da 15 01 bc 7e  |.E....B...)....~|
00000050  a2 10 e4 7a 98 19 91 c4  7c 47 10 83 48 cf 25 63  |...z....|G..H.%c|
00000060  80 45 83 e0 02 91 78 84  0b b9 bc 75 29 85 80 62  |.E....x....u)..b|
00000070  2a 0e 73 ec 4d 48 69 c6  f1 76 83 26 e7 19 e8 2d  |*.s.MHi..v.&...-|
00000080  e7 f9 20 58 41 43 a2 a9  e9 02 3b 10 82 64 ce 56  |.. XAC....;..d.V|
00000090  25 48 5a 25 30 89 54 be  39 15 ca 64 6a 92 1b f6  |%HZ%0.T.9..dj...|
000000a0  ae a5 52 c6 b2 96 96 82  a8 4b 23 1a 94 ea cd b7  |..R......K#.....|
000000b0  ed aa 75 44 ef 75 b8 ec  70 b3 11 bb 6d 55 cb 2d  |..uD.u..p...mU.-|
000000c0  1f 33 66 1d 66 9f 70 21  da be 9e 3e af b8 9f 1a  |.3f.f.p!...>....|
000000d0  be e9 bc d2 15 75 bf 8d  53 76 c5 ed 8d ea bf d6  |.....u..Sv......|
000000e0  35 73 ad ff ed 9d ef 5b  ce 35 ad fa e7 fc ff ff  |5s.....[.5......|
000000f0  ff ff ff ff ff ff f1 ef  48 f1 9c 63 03 22 21 27  |........H..c."!'|
00000100  f8 d3 e5 c3 c8 00 a4 78  87 69 52 3b 10 0a 54 08  |.......x.iR;..T.|
00000110  b4 47 73 53 d9 c1 40 ee  55 23 63 1a a1 38 85 a2  |.GsS..@.U#c..8..|
00000120  98 13 c5 9a e1 75 0d 0e  2b 4e 56 37 cc 6a c6 c8  |.....u..+NV7.j..|
00000130  73 f9 d5 52 af bc 45 f7  f4 9d fc 78 6d 69 74 66  |s..R..E....xmitf|
00000140  d4 4e 4a 25 42 3e 3b a4  6e d5 69 f6 c7 06 05 72  |.NJ%B>;.n.i....r|
00000150  ea 31 34 6f 7a bf 06 1a  10 9b 53 43 8d 15 0a 33  |.14oz.....SC...3|
00000160  8b ad 24 52 b6 1c 2a e3  f9 2e cb 11 93 30 71 8a  |..$R..*......0q.|
00000170  cd af 02 ba be 31 48 8d  77 a4 b7 ff fb d0 44 3b  |.....1H.w.....D;|
00000180  00 06 d9 88 5b 86 3d e0  01 09 31 1b 20 cd 3c 00  |....[.=...1. .<.|
00000190  1a 1d e7 64 1d 87 80 0a  da 3c 2d 43 b0 90 01 ad  |...d.....<-C....|
000001a0  e0 45 8a d9 01 74 86 13  a3 b9 09 72 d5 1b 97 0c  |.E...t.....r....|
000001b0  e5 1d 87 6a 39 b2 89 c7  da 8f b2 d9 1a 6b 00 fe  |...j9........k..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 c5 38 00 fe  |...........P.8..|
000001d0  ff ff 05 fe ff ff 02 50  c5 38 00 d0 6a 01 00 00  |.......P.8..j...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3


Unknown BootLoader  on sdc4


Unknown BootLoader  on sdd1


Unknown BootLoader  on sdd2


Unknown BootLoader  on sdd3


Unknown BootLoader  on sdd4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc: Input/output error
hexdump: /dev/sdd: Input/output error
hexdump: /dev/sdc: Input/output error
hexdump: /dev/sdc: Input/output error
hexdump: /dev/sdd: Input/output error
hexdump: /dev/sdd: Input/output error
hexdump: /dev/sdc1: Input/output error
hexdump: /dev/sdc1: Input/output error
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdd1: Input/output error
hexdump: /dev/sdd1: Input/output error
hexdump: /dev/sdd2: No such file or directory
hexdump: /dev/sdd2: No such file or directory
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sdd4: No such file or directory
hexdump: /dev/sdd4: No such file or directory
```



Much thanks to any and all that can help me figure this out and (hopefully) solve it to get Win7 and Ubuntu dual booting as they should.

I'm hoping someone can give me a detailed, step-by-step instruction of what to do. I'm fairly tech-savvy, but am very intimidated making changes to base system settings such as the MBR.

And Happy New Year to all!

---

### Post by presence1960 on 2010-12-31
```
============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
[COLOR="Red"]partition #256[/COLOR] for /boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
[COLOR="Red"]partition #256[/COLOR] for /boot/grub.
=> No known boot loader is installed in the MBR of /dev/sdc
=> No known boot loader is installed in the MBR of /dev/sdd
```

Part of your problem is in red above.

Questions:

Do you have RAID set up?

What is dev sdc & sdd and what is on them?

---

### Post by rmm64 on 2010-12-31
> **presence1960 said:**
> ```
============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
[COLOR="Red"]partition #256[/COLOR] for /boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
[COLOR="Red"]partition #256[/COLOR] for /boot/grub.
=> No known boot loader is installed in the MBR of /dev/sdc
=> No known boot loader is installed in the MBR of /dev/sdd
```

Part of your problem is in red above.

Questions:

Do you have RAID set up?

What is dev sdc & sdd and what is on them?

No, not running a RAID setup.

I assume sdc & sdd are the other supplemental drives I have. I have a total of 4 internal HDs. One 80GB (the main drive where both Win7 and Ubuntu are installed), and three other drives (a 120GB, 1TB, and 2TB.) The 1TB drive was the one originally having partition probs that prompted me to try Ubuntu to get it fixed. I've since moved all the files off that drive to the new 2TB drive I installed, so now the 1TB is completely empty. I think it may still have some partition or bad sector issues, but I can deal with that later. I just really need to get Win7 loading and working properly.

If I can't get the dual boot working properly, I'd rather just wipe out the Ubuntu installs completely and get Win7 working correctly (again, ideally without having to reinstall.) I can always run Ubuntu off the CD when I need it.

Hope that helps clarify.

---

### Post by presence1960 on 2010-12-31
```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 2,048 3,907,026,943 3,907,024,896 7 HPFS/NTFS


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 2,048 977,290,203 977,288,156 7 HPFS/NTFS
/dev/sdb2 977,291,262 1,953,523,711 976,232,450 5 Extended
/dev/sdb5 977,291,264 1,929,746,431 952,455,168 83 Linux
/dev/sdb6 1,929,748,480 1,953,523,711 23,775,232 82 Linux swap / Solaris


Drive: sdc ___________________ __________________________________________________ ___

Partition Boot Start End Size Id System

Invalid MBR Signature found
/dev/sdc1 ? 0 -1 Unknown
/dev/sdc2 ? 0 -1 Unknown
/dev/sdc3 ? 0 -1 Unknown
/dev/sdc4 ? 0 -1 Unknown


Drive: sdd ___________________ __________________________________________________ ___

Partition Boot Start End Size Id System

Invalid MBR Signature found
/dev/sdd1 ? 0 -1 Unknown
/dev/sdd2 ? 0 -1 Unknown
/dev/sdd3 ? 0 -1 Unknown
/dev/sdd4 ? 0 -1 Unknown
```

sda is the 2 TB disk.
sdb is the 1 TB disk. Ubuntu is installed on this disk in sdb5 with swap on sdb6.

Your windows is not installed on either of these disks. You say your windows is installed on the 80 Gb disk. We need to try to fix whatever errors are on that disk, as it is either sdc or sdd. The errors are keeping the script from mounting that disk and reading it.

1. Reboot & go into BIOS and set the 80 Gb disk as first in the hard disk boot order. Save changes to CMOS and boot the windows 7 install DVD or the Recovery Console CD. Click repair, then choose command prompt. Type ```
chkdsk C: -r
```
Wait for it to finish, do not interrupt it, it may take a while. When completed try booting windows. If it doesn't boot repeat above until running chkdsk shows no errors.

If we can get windows running we can always fix GRUB.

---

### Post by presence1960 on 2010-12-31
also from the command prompt after chdsk is done you can try running:

```
bootrec.exe /fixboot
```

when that is completed run:

```
bootrec.exe /fixmbr
```

Then type exit and reboot without the CD/DVD leaving 80 Gb as first disk to boot and see if windows boots.

---

### Post by rmm64 on 2010-12-31
> **presence1960 said:**
> also from the command prompt after chdsk is done you can try running:

```
bootrec.exe /fixboot
```when that is completed run:

```
bootrec.exe /fixmbr
```Then type exit and reboot without the CD/DVD leaving 80 Gb as first disk to boot and see if windows boots.


Ok, I've tried as suggested rebooting with the Win7 install disc and running the command prompt repairs. First off, using the "chkdsk c: -r" prompted an invalid parameter -r response. I tried running it as just "chkdsk c:" which did scan the drive and reported no errors. I also tried the Startup Repair and System Repair options to  no avail. When prompting to load the drivers, the Windows install disc did see the installation, but reported the partition size as 0 and unknown. Also, changing the 80GB drive where Windows is gave an error as well. 

Now when Grub loads, Ubuntu fails to load as well, giving the following response:

Try (hd0,0): NTFS5: No wubildr
Try (hd0,1): invalid or null
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (hd1,0): NTFS5: 2
Try (hd1,1): invalid or null
Try (hd1,2): invalid or null
Try (hd1,3): invalid or null
Try (hd2,0): NTFS5, No wubildr
Try (hd2,1): invalid or null
Try (hd2,2): invalid or null
Try (hd2,3): invalid or null

Selecting Windows 7 from the Grub loader gives the same response as before:

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer
2. Choose your language settings and click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

Status: 0x0000225
Info: The boot selection failed because a required device is inaccessible.

If I'm understanding this right, it seems the partition is messed up on the main C drive and with the (re)install of Ubuntu to another drive, Grub is (or was now) looking in the wrong place for Windows (and now it seems Ubuntu too.)

Please tell me this can be saved. Perhaps I can use Testdisk to find and/or repair the partition info and get things set back to the way they were before?

I think I need to step away from this right now and take a break. Hopefully when I come back in a bit, someone will have some ideas or suggestions on what else I can try to salvage this and get things to work. At this point, I'd even be happy just to get Ubuntu working right again (NOT off the CD as I am now), and get access to the files on my C: drive so I can at least save what I need to reinstall Windows again. VERY frustrated.

Thanks for the help thus far. Looking forward to more options.

---

### Post by presence1960 on 2010-12-31
I think it is a good idea for you to take a breather. testdisk is an option to repair windows partition. I have not used it in a while. I will need to search for documentation to repair the windows MBR. I know I have it in a text file somewhere in my data disk.

maybe meierfra will be around when you come back. He is a whiz with windows and helped show me how to use test disk to repair an MBR. In my opinion he is a "go-to" guy in this type of situation. That is when I made the text file with the instructions. I hope I can find it for you.

---

### Post by presence1960 on 2010-12-31
A stroke of luck, found it quickly. here it is:

OK, I think we should use "testdisk" to check if your Windows XP boot sector needs fixing; first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:

```
sudo apt-get install testdisk
```

Next:

```
sudo testdisk
```

After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda1 partition (or whatever your's is), choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know, and we can work from there.

P.S. I know the verbiage says XP, but I just ran those instructions and it worked on my windows 7. It gave me the option to Rebuild BS which is what you want to see.

---

### Post by Herman on 2010-12-31
> chkdsk c: -rI think you mean CHKDSK C: /R

Often it can be abbreviated to CHKDSK /R
I think if we just type the command CHKDSK without any parameters it just does a scan and prints out the report.
CHKDSK /F gives a quick file system check and CHKDSK /R gives you a thorough file system check.

I always recommend CHKDSK /R, any less is a waste of time in my opinion. Sometimes it takes a long time to complete, but it's worth the wait when you know the job has been done properly. Sometimes it takes two or three runs of CHKDSK /R to clean up all file system errors in Windows. I don't know why.

---

### Post by presence1960 on 2010-12-31
> **Herman said:**
> I think you mean CHKDSK C: /R

Often it can be abbreviated to CHKDSK /R
I think if we just type the command CHKDSK without any parameters it just does a scan and prints out the report.
CHKDSK /F gices a quick file system check and CHKDSK /R gives you a thorough file system check.

I always recommend CHKDSK /R, any less is a waste of time in my opinion. Sometimes it takes a long time to complete, but it's worth the wait when you know the job has been done properly. Sometimes it takes two or three runs of CHKDSK /R to clean up all file system errors in Windows. I don't know why.

Yes, Herman. I guess I mistyped it. I had chkdsk C: -r. Thanks for catching that.

---

### Post by rmm64 on 2011-01-01
> **presence1960 said:**
> A stroke of luck, found it quickly. here it is:

OK, I think we should use "testdisk" to check if your Windows XP boot sector needs fixing; first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:

```
sudo apt-get install testdisk
```Next:

```
sudo testdisk
```After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda1 partition (or whatever your's is), choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know, and we can work from there.

P.S. I know the verbiage says XP, but I just ran those instructions and it worked on my windows 7. It gave me the option to Rebuild BS which is what you want to see.


Ok, have tried your suggestions, but no luck getting Win7 to load yet.

Did the Rebuild BS in testdisk with the following result:

Disc 1 /dev/sdb - 80GB
Partition: HPFS-NTFS
Boot Sector Status: OK
Backup Boot Sector Status: Bad
Sectors are not identical
A valid NTFS Boot sector must be present in order to access any data; even if the partition is not bootable

Also retried booting the Win7 install disc and running the repair again (with the correct parameter as was mentioned) with my 80GB drive listed first in boot list, just to be sure.

Was prompted to load the drivers (Win7 did not show in the list as an installed OS), so when I clicked to browse the drivers, imagine my surprise when my 120GB drive (formally a non-OS drive labeled as B) came up listed as my C: drive. All the programs and files I had stored there are intact, so that's good, but there's no OS installed on that drive.

I then exited the repair and rebooted (still with the 80GB drive first in boot priority), and immediately after POST, got the following message,

error: no such device
followed by a long string of numbers & letters and the following prompt:
grub rescue>

I obviously don't know what, if anything, 'grub rescue' expects me to type in at the prompt, so I just rebooted again and am back running Unbuntu off the CD to get back online.

With my limited understanding, it seems to me the partition is completely gone off my original C: drive since it's not loading at startup (though BIOS still sees it fine) so I believe the drive is ok, just not partitioned, or partitioned correctly. But that's just an semi-uneducated guess. It seems to me that something has screwed up the MBR and partitions, mixing what was my C: and B: drives, and maybe that is why Grub is unable to load Win7 as it's lost where it is? I'm also thinking that with the 120GB drive listed first in boot priority, that is when grub actually loads and I was (previously) able to load Ubuntu (though that's not working now either)

I'll tell ya, this is NOT how I wanted, nor expected, to be spending my New Year's weekend, but it is what it is. Here's hoping someone's out there with an answer tonight that isn't celebrating NYE.

Standing by.

---

### Post by rmm64 on 2011-01-01
I'm also wondering now if I installed Ubuntu for a 3rd time, if it might fix the Windows 7 loader (as before), just long enough for me to get back into Windows then remove all the Ubuntu installs and partitions from within Windows. Also curious as why my 80GB drive with the Win7 install was listed 2nd in the boot priority in BIOS (after the 120GB drive), but has been booting Win7 fine all this time. I previously had XP/Vista installed on that drive, but switched it with the 80GB drive when I installed Win7 a long time ago (right after Win7 was released.) I never really gave it any thought before, but if the 80GB was listed as a slave, and the 120GB as the master, it never seemed to cause any issues until this Ubuntu thing popped up the other day after running the Ubuntu updates, especially given I was dual booting both for about a week before letting it update. I dunno, just rambling now.

---

### Post by rmm64 on 2011-01-01
bumping this to be seen, with some updated info as well. Maybe some of this will help sort out the previous info I could provide and make better sense of what's going on and where/what everything is so someone can help.

I ran testdisk again this morning on the 80GB drive (sdb) (my old C: drive where Win7 was installed), tried to recover the partition but no luck. So I loaded up the NTFS Config utility so I can access the other internal drives I have.

I ran the Disk Utility to see what's what, and got the following results:[INDENT] The 120GB drive (sda) (formerly labeled as B: under Win7), seems to be intact with all the files that were there before. It's showing as an NTFS partition under device dsa1

My 80GB drive (sdb) shows it partitioned for NTFS with an unknown volume and no usage listed (unlike the others that are all listed as filesystem.

The 2TB drive (sdc) is intact, partitioned for NTFS with all files intact.

My 1TB drive (device sdd) (formerly labeled as D:) I'm assuming is where the 2nd install of Ubuntu got installed to on device. The drive was completely empty before with just a single partition, but now shows 500GB partitioned for NTFS (sdd1), 500GB extended partition (sdd2), 488GB for a Linux partition (sdd5), and a 12GB Linux swap partition (sdd6).
[/INDENT]I didn't find any other partitions for Linux, so don't know where the original install has gone. The reason I know the Linux install on the 1TB drive above is the 2nd one is because I'd begun setting up different user accounts in it and could see them in the folders on that partition. Also FYI, that install was loading fine until I tried running the chkdsk repairs yesterday off the Win7 install disk, but now the Grub loader sees Ubuntu installed (only when I have the 120GB listed first in boot priority), but won't load it (see previous post about the error message.

Right now I'm using PhotoRec to try and recover anything possible off the 80GB drive, just in case I end up having to reformat/reinstall Win7 to it again. At least I can hopefully salvage the files that were on there I need. Since it was only 80GB to start, I'm just letting it recover everything and save it into a folder I created on the 2TB drive. I can sort through the files it finds later once I have everything working again. I'm still hoping someone can offer a suggestion that will bring my computer back to a working Win7 install without having to start over and reinstall everything, but at least I'm taking some comfort in that it does seem to be recovering the files that were on there (currently about 20mins in reading sector 267XXXXX/156280257 with about 100K files found (and still going) and still another 1hr36mins to go.

So there ya go. I'm still holding onto slim hope of getting this fixed. Think it's time to go relax with some PS3 action while PhotoRec finishes pulling files off the old C: drive.

Looking forward to anymore suggestions. Much thanks for the help offered and anymore someone can think of. Hope you all had a great time last night for NYE and got home safely.

*update: ok, looks like pulling EVERYTHING off choked PhotoRec, gonna have to start over and select only the file types I know I need to save.*

---

### Post by rmm64 on 2011-01-01
ok, I'm getting a "Segmentation fault (core dumped)" message part way through trying to recover files with PhotoRec. It's getting some of the files, but erroring out with that message about 25 mins into the process (with 1hr17mins left to go), so it's obviously not recovering all the files.

Anyone have any suggestions for this? What could be causing it?

---

### Post by rmm64 on 2011-01-02
hey guys, bumping this again hoping to get a response.

also, slight update to my last post. Haven't been able to select ALL the files I need to recover without getting the error message from PhotoRec, but so far seem to be having some luck getting it to finish going through one filetype at a time. It's tedious process, but seems to be working at least. I've successfully recovered one filetype, now on my second (knock wood.) This actually works a little better anyway as now I can recover the files into separate folders which will make it easier later to sort through.

Now, if someone could read through the thread and see if there's anything else I could try to save my Win7 install without having to reformat, that would be wonderful. I know it's New Year's weekend, but there seems to be quite a bit activity here anyway (since my post was buried 4 pages back in under 20 hrs.) I figure if nobody has offered any other suggestions by the time I've gone through (one by one) and recovered the files I need, I'll have no other choice but to reformat/reinstall (ugh!) as I really need to get this system back to a working state again. I have clients waiting on work.

Any thoughts or suggestions?
PLEEEEEEEEEASE???

---

### Post by Herman on 2011-01-02
I think you need to start investigating your computer's hardware to try to determine if it's all okay or which part is faulty if any.

---

### Post by rmm64 on 2011-01-04
> **Herman said:**
> I think you need to start investigating your computer's hardware to try to determine if it's all okay or which part is faulty if any.

The hardware is fine. If you'd read the thread in its entirety, you'd have seen where I stated that chkdsk reported no errors at all on my C: drive (run 3 different times to verify.) 

Everything was working fine prior to Ubuntu running/installing updates (which was within 48 hours of installing it), that's when the problems began and it cascaded from there. Before installing it, I'd ran Win7 without a problem for 2+ years, so yes, I blame Ubuntu for being the cause of this, not a hardware issue. IMHO, it's no more stable or supported than the Win95 initial release, which is why it will NOT be installed on my computer again.

And I have to say that the lack of responses since my initial posting days ago has only reinforced my doubts about running an open source OS. At first I believed there was community support for the product and that I may be able to salvage my original setup, but aside from the few suggestions given (which all failed, and frankly, made things worse) there's been nothing despite my replies to bump the post to top of the thread. So much for a "community."

---

### Post by oldfred on 2011-01-04
When you had grub looking for partition #256 that is normally from a wubi install where it installs grub to the MBR when you really want the windows boot loader. But the boot script did not find any wubi install since it could not see all the partitions. Wubi is just a file inside the NTFS partition and uses the windows boot loader to boot. It relies on the NTFS partition, so if windows has problems the Ubuntu wubi install will also.

You then also had another Ubuntu install in sdd. But it seems like all your issues are related to windows issues. Wubi does have a bug that installs grub incorrectly but is easily fixed by reinstalling the windows boot loader.

---

