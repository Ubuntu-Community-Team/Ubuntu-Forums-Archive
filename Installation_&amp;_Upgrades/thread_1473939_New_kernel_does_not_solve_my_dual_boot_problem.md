---
title: "New kernel does not solve my dual boot problem"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by weedwacker on 2010-05-05
Cannot dual boot between Ubuntu 10.04 and Windows XP - each on separate sata HDs as I could with Ubuntu Karmic 9.10.
Ext4 and Grub2 on both versions of Ubuntu.

Reinstalled both OSs independent of each other (pulled the sata cable for Windows HD when installing Ubuntu 10.04 so that the OS Prober could not see my Windows OS).

When new kernel update came through I thought "Oboy! Maybe this will work!" It did only partially: This time I could get into Ubuntu from the boot screen which I could not with the first kernel. But I could not get into Windows. I had to change my BIOS setting to boot into Windows. Then I had to change the BIOS setting to boot back into Ubuntu.

This is the result of the boot_info_script.sh: (I hope someone can identify why I can no longer dual boot. Thanks.)

The Results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   320,143,319   238,227,885   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372   7 HPFS/NTFS
/dev/sda6         163,830,933   320,143,319   156,312,387   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    23,438,834    23,438,772  83 Linux
/dev/sdb2          23,438,896   488,392,064   464,953,169   5 Extended
/dev/sdb5          23,438,898    33,204,522     9,765,625  83 Linux
/dev/sdb6         179,687,088   480,584,474   300,897,387  83 Linux
/dev/sdb7         480,584,538   488,392,064     7,807,527  82 Linux swap / Solaris
/dev/sdb8          33,206,272   179,685,375   146,479,104  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        88B49C77B49C6988                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        666C55CE6C55999F                       ntfs       MSDATA                        
/dev/sda6        E0A491FDA491D67E                       ntfs       MSDATA2                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        711f0ac9-9f07-4dcb-a774-d0d851007d35   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1eae315a-5bc2-456b-aba3-d85c37b2e886   ext4                                     
/dev/sdb6        a968328f-5733-4ebb-be75-3d24ffb4b57e   ext4       Data                          
/dev/sdb7        ac02f7cb-236a-4035-b8c8-0410b4281240   swap                                     
/dev/sdb8        42aeabb2-3bdf-4790-b6cd-9f2928bdc479   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /boot                    ext4       (rw)
/dev/sdb6        /media/data              ext4       (rw)
/dev/sdb8        /home                    ext4       (rw)
/dev/sda1        /media/88B49C77B49C6988  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=711f0ac9-9f07-4dcb-a774-d0d851007d35 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=1eae315a-5bc2-456b-aba3-d85c37b2e886 /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=42aeabb2-3bdf-4790-b6cd-9f2928bdc479 /home           ext4    defaults        0       2
# /media/data was on /dev/sda6 during installation
UUID=a968328f-5733-4ebb-be75-3d24ffb4b57e /media/data     ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=ac02f7cb-236a-4035-b8c8-0410b4281240 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: initrd.img
    .1GB: initrd.img.old
    .1GB: vmlinuz
    .1GB: vmlinuz.old

============================= sdb5/grub/grub.cfg: =============================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 711f0ac9-9f07-4dcb-a774-d0d851007d35
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1eae315a-5bc2-456b-aba3-d85c37b2e886
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1eae315a-5bc2-456b-aba3-d85c37b2e886
	linux	/vmlinuz-2.6.32-22-generic root=UUID=711f0ac9-9f07-4dcb-a774-d0d851007d35 ro   quiet splash
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1eae315a-5bc2-456b-aba3-d85c37b2e886
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/vmlinuz-2.6.32-22-generic root=UUID=711f0ac9-9f07-4dcb-a774-d0d851007d35 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1eae315a-5bc2-456b-aba3-d85c37b2e886
	linux	/vmlinuz-2.6.32-21-generic root=UUID=711f0ac9-9f07-4dcb-a774-d0d851007d35 ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1eae315a-5bc2-456b-aba3-d85c37b2e886
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=711f0ac9-9f07-4dcb-a774-d0d851007d35 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1eae315a-5bc2-456b-aba3-d85c37b2e886
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1eae315a-5bc2-456b-aba3-d85c37b2e886
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 88b49c77b49c6988
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb5: Location of files loaded by Grub: ===================


  14.4GB: grub/core.img
  14.4GB: grub/grub.cfg
  12.1GB: initrd.img-2.6.32-21-generic
  12.1GB: initrd.img-2.6.32-22-generic
  12.1GB: vmlinuz-2.6.32-21-generic
  12.1GB: vmlinuz-2.6.32-22-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  23 39 31 39 34 39 35 22  2c 0a 22 51 24 09 63 20  |#919495",."Q$.c |
00000010  23 41 30 41 33 41 33 22  2c 0a 22 52 24 09 63 20  |#A0A3A3",."R$.c |
00000020  23 41 30 41 34 41 34 22  2c 0a 22 53 24 09 63 20  |#A0A4A4",."S$.c |
00000030  23 42 34 42 38 42 39 22  2c 0a 22 54 24 09 63 20  |#B4B8B9",."T$.c |
00000040  23 42 39 42 43 42 45 22  2c 0a 22 55 24 09 63 20  |#B9BCBE",."U$.c |
00000050  23 43 46 44 34 44 35 22  2c 0a 22 56 24 09 63 20  |#CFD4D5",."V$.c |
00000060  23 45 36 39 31 37 41 22  2c 0a 22 57 24 09 63 20  |#E6917A",."W$.c |
00000070  23 45 31 36 46 35 38 22  2c 0a 22 58 24 09 63 20  |#E16F58",."X$.c |
00000080  23 43 44 35 39 35 41 22  2c 0a 22 59 24 09 63 20  |#CD595A",."Y$.c |
00000090  23 42 36 42 39 42 42 22  2c 0a 22 5a 24 09 63 20  |#B6B9BB",."Z$.c |
000000a0  23 42 34 42 37 42 39 22  2c 0a 22 60 24 09 63 20  |#B4B7B9",."`$.c |
000000b0  23 43 30 43 33 43 35 22  2c 0a 22 20 25 09 63 20  |#C0C3C5",." %.c |
000000c0  23 39 42 39 43 39 44 22  2c 0a 22 2e 25 09 63 20  |#9B9C9D",.".%.c |
000000d0  23 41 43 41 45 41 44 22  2c 0a 22 2b 25 09 63 20  |#ACAEAD",."+%.c |
000000e0  23 45 42 45 42 45 42 22  2c 0a 22 40 25 09 63 20  |#EBEBEB",."@%.c |
000000f0  23 42 38 42 41 42 39 22  2c 0a 22 23 25 09 63 20  |#B8BAB9",."#%.c |
00000100  23 37 39 37 42 37 41 22  2c 0a 22 24 25 09 63 20  |#797B7A",."$%.c |
00000110  23 41 41 41 44 41 45 22  2c 0a 22 25 25 09 63 20  |#AAADAE",."%%.c |
00000120  23 42 35 42 38 42 38 22  2c 0a 22 26 25 09 63 20  |#B5B8B8",."&%.c |
00000130  23 42 38 42 41 42 43 22  2c 0a 22 2a 25 09 63 20  |#B8BABC",."*%.c |
00000140  23 43 41 43 46 44 31 22  2c 0a 22 3d 25 09 63 20  |#CACFD1",."=%.c |
00000150  23 43 38 39 38 39 37 22  2c 0a 22 2d 25 09 63 20  |#C89897",."-%.c |
00000160  23 44 32 36 34 36 33 22  2c 0a 22 3b 25 09 63 20  |#D26463",.";%.c |
00000170  23 42 44 42 32 42 32 22  2c 0a 22 3e 25 09 63 20  |#BDB2B2",.">%.c |
00000180  23 43 37 43 43 43 43 22  2c 0a 22 2c 25 09 63 20  |#C7CCCC",.",%.c |
00000190  23 42 43 42 45 43 30 22  2c 0a 22 27 25 09 63 20  |#BCBEC0",."'%.c |
000001a0  23 41 42 41 45 41 46 22  2c 0a 22 29 25 09 63 20  |#ABAEAF",.")%.c |
000001b0  23 39 46 41 32 41 32 22  2c 0a 22 21 25 09 00 fe  |#9FA2A2",."!%...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 f9 02 95 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 41 28  50 09 aa 54 ef 11 00 00  |......A(P..T....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by weedwacker on 2010-05-05
Anyone? Things are at the point of reverting to legacy Grub.

Any help would be most appreciated.

---

