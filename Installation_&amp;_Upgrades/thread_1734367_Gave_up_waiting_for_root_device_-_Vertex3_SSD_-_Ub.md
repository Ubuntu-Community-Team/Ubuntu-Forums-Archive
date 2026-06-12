---
title: "Gave up waiting for root device - Vertex3 SSD - Ubuntu 10.10"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by ahebah on 2011-04-20
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]About a week ago I changed the hard disk setup of my desktop PC. I installed a new SSD and changed the set-up of my old hard disks. Since I installed the SSD I have not been able to boot Ubuntu from it.
 
When I reboot and chose Ubuntu at the grub menu then it ends with the following error: 'Gave up waiting for root device' and '/dev/disk/by-uuid/[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]2bef4d2f-db0e-44b3-9e85-2065fad6f4a0[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2] does not exist. Dropping to Shell!'[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2] 
I have made a description of my current set-up and the changes made last week and I have copied the output from boot_info_script as well.
&#12288;
Old setup:
Asus P5Q-Pro mainboard
3x Samsung Spinpoint F1 750GB with
2 drives in a (fake)raid 0 setup using Intel Matrix Raid Storage from the ICH10R chipset
with 4 partitions: a system partition for Windows 7, a system partition for Ubuntu, a data storage partition for Windows and a linux swap partition
1 drive not in a raid array and split in 2 partitions:
1 ext4 partition used for my /home folder (since the Ubuntu system partition was not intented to be used to store documents)
1 ntfs partition used to backup documents, pictures/photo's and music from the Windows data partition on the raid array
Since release 10.04 Ubuntu would install properly on the raid array. Before release 10 I had to use the alternate cd installation and install grub manually to avoid messing up the boot process.
&#12288;
New setup:
Asus P5Q-Pro mainboard
Disk setup in the bios set to RAID (rather then AHCI or IDE)
1x OCZ Vertex3 240GB used as:
system disk for Windows 7 (split by WIndows in a small boot partition and the system partition)
system disk for Ubuntu
swap partition for Ubuntu
3x Samsung Spinpoint F1 750GB:
3 drives in a (fake)raid 5 setup using Intel Matrix Raid Storage from the ICH10R chipset split in 2 partitions: 1 data partition for windows and 1 data (or /home) partition for Linux. The linux /home folder is currently still on the system partition on the SSD with the intention to move it after installation.
I left the 'disk setup' setting in the bios set to RAID as I had planned to use the 3 hard disks in a raid 5 setup after installation of windows and linux was done on the SSD. Changing that setting now to AHCI will cause Windows to abend during start-up (which I expected). Installing windows and ubuntu was done, at least at first, with only the SSD attached and all 3 hard disks temporarily disconnected:
1. installed Windows on the SSD using the complete disk -> this resulted in 2 partitions on the SSD, a 100MB 'boot' partition with the rest of the drive used as windows disk.
2. installed Ubuntu on the SSD and manually changed to 4 partitions, the 2 windows partitions now followed by an ext4 partition and a swap partition. Grub installed on the ssd (on /dev/sda).
-> Windows boots without problems but I have not been able to boot Ubuntu from the SSD (except for one exception and I don't seem to be able to recreate that situation)
If I start-up an Ubuntu Live session from an USB disk then it will recognize all drives and partitions correctly (with correct uuid's for each partition). I have re-installed Ubuntu now several times and I have tried several different setup's. In the mean time I have created the raid 5 array but when I reconnected the disks the old array was still valid. I could boot to Windows from that old setup (now with the SSD installed as well) but had the same problem when trying to boot to Ubuntu from the old setup. I had been running a dual boot on that old setup for a long time and never had a problem to boot to Ubuntu before.
 
I have tried to put the /boot folder on the raid 5 array but without result (I actually believe the situation got worse and it blocked me from booting to Windows).
I have been searching for a possible solution I think I will be asked to run boot_info_script055.sh and post the RESULT.TXT file before anyone can give me any sensible advice. To make sure that none of the grub files have been messed up by changes I tried to make I first installed Ubuntu and immediately after rebooting I ran the boot_info_script.
 
I have tried to remove the 'search' line using ctrl-e at the grub menu -> didn't help
I have tried to change the UUID reference for /boot/vmlinuz to /dev/sda3 -> didn't help
when I let the system boot with quiet splash removed I can see that it reports that 'ata1 link is slow' followed by a 'softreset failed' several times and then drops to BusyBox. After the dropout using ls /dev/disk/by-uuid will only show the uuid of the windows boot partition and one more (I believe the windows data partition). The uuid of the Ubuntu system partition is not shown.
 
There is a newer bios version available for my mainboard and I can update the bios if it is expected to help solve the issue.
 
Anyone any idea what I can do to solve my boot problem ?
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Hedgehog1 on 2011-04-20
I put the script results in the 'CODE' tags to make ti easier to read:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/mapper/isw_dgjbiadbjc_Data7 and 
    looks on the same drive in partition #5 for (,msdos5)/grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

isw_dgjbiadbjc_Data71: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_dgjbiadbjc_Data72: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_dgjbiadbjc_Data75: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   371,300,597   371,093,750   7 HPFS/NTFS
/dev/sda3         371,302,400   460,871,679    89,569,280  83 Linux
/dev/sda4         460,871,680   468,860,927     7,989,248  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4013 MB, 4013948928 bytes
1 heads, 24 sectors/track, 326656 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,128     7,839,743     7,823,616   b W95 FAT32


Drive: isw_dgjbiadbjc_Data7 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dgjbiadbjc_Data7: 1500.3 GB, 1500308045824 bytes
255 heads, 63 sectors/track, 182402 cylinders, total 2930289152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dgjbiadbjc_Data71              2,048 2,252,802,047 2,252,800,000   7 HPFS/NTFS
/dev/mapper/isw_dgjbiadbjc_Data72      2,252,804,094 2,930,288,639   677,484,546   5 Extended
/dev/mapper/isw_dgjbiadbjc_Data75      2,252,804,096 2,930,288,639   677,484,544  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dgjbiadbjc_Data71 923E19FF3E19DCD3                       ntfs       Data7                         
/dev/mapper/isw_dgjbiadbjc_Data75 062ec250-5226-44db-bdb0-fe741f1b7f42   ext4       Rico                          
/dev/mapper/isw_dgjbiadbjc_Data7: PTTYPE="dos" 
/dev/sda1        B2D4A4ECD4A4B3CF                       ntfs       Door systeem gereserveerd     
/dev/sda2        02DEA6C1DEA6AC7B                       ntfs       System7                       
/dev/sda3        2bef4d2f-db0e-44b3-9e85-2065fad6f4a0   ext4                                     
/dev/sda4        8dddc119-a06e-416c-bc57-a330ede8a2b4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        84A0-D10F                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                isw_raid_member                               
/dev/sdd                                                isw_raid_member                               
/dev/sde                                                isw_raid_member                               
error: /dev/mapper/isw_dgjbiadbjc_Data72: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dgjbiadbjc_Data7
isw_dgjbiadbjc_Data71
isw_dgjbiadbjc_Data75

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 2bef4d2f-db0e-44b3-9e85-2065fad6f4a0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 2bef4d2f-db0e-44b3-9e85-2065fad6f4a0
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2bef4d2f-db0e-44b3-9e85-2065fad6f4a0
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2bef4d2f-db0e-44b3-9e85-2065fad6f4a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2bef4d2f-db0e-44b3-9e85-2065fad6f4a0
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2bef4d2f-db0e-44b3-9e85-2065fad6f4a0 ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2bef4d2f-db0e-44b3-9e85-2065fad6f4a0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2bef4d2f-db0e-44b3-9e85-2065fad6f4a0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b2d4a4ecd4a4b3cf
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=2bef4d2f-db0e-44b3-9e85-2065fad6f4a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=8dddc119-a06e-416c-bc57-a330ede8a2b4 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 213.8GB: boot/grub/core.img
 229.0GB: boot/grub/grub.cfg
 229.3GB: boot/initrd.img-2.6.35-22-generic
 213.8GB: boot/vmlinuz-2.6.35-22-generic
 229.3GB: initrd.img
 213.8GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 6e 04  |.X.SYSLINUX...n.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 3f 00 00  |........?....?..|
00000020  00 61 77 00 c9 1d 00 00  00 00 00 00 02 00 00 00  |.aw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0f d1 a0 84 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 78 f7 15 00  66 ba 00 00 00 00 bb 00  |}.f.x...f.......|
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

Unknown BootLoader  on isw_dgjbiadbjc_Data72



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_dgjbiadbjc_Data72: No such file or directory
hexdump: /dev/mapper/isw_dgjbiadbjc_Data72: No such file or directory
```

Notes:
/dev/mapper/isw_dgjbiadbjc_Data72      2,252,804,094 2,930,288,639   677,484,546   5 Extended
error: /dev/mapper/isw_dgjbiadbjc_Data72: No such file or directory

---

### Post by ahebah on 2011-04-20
Thanks for putting the result.txt file in a readable code window.

'Extended error: /dev/mapper/isw_dgjbiadbjc_Data72: No such file or directory' 
I was wondering about this error myself and I have no clue what has caused it.  I made a new raid 5 array, which should erase all previous data on the disks, and then created 2 partions on that array.  One partition of approximately 1TB for Windows and one of 320GB for Linux.

Anyway, the raid array cannot be the cause of the boot problem.  I first installed Windows and Linux on the SSD before I attached the other disks.  I couldn't boot Ubuntu at that time either.  Should I get this error fixed ?  (attached a screenshot of the disks/partitions as shown in Windows disk management - text in Dutch unfortunately)

---

