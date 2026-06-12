---
title: "Ubuntu 10.04 and Grub"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by corowakid on 2010-05-07
Hi all, perhaps some kind person can sort out my problem(s).

I had Ubuntu 9.10 on my PC and decided to use a downloaded CD of 10.04 Live CD to install it by removing 9.10 and installing 10.04. My PC has 2 HDD and an external drive, both HDD partitioned into 2.

The installer on the Live CD is different to previous, but I went through with it, using the "do you want to run both systems alongside (or similar wording)" I took this to be the Windows/Ubuntu co-existence that I originally had using Grub at bootup. Things went OK with the install (or so I thought) with the Live CD reporting all had been installed, including updates downloaded from the 'Net.

I closed down and re-booted, and Grub came up like normal, but before the splash screen could appear I got the message "error: no such device: 07162612-383e-4afe-bc01-ad3cfe04bc44" on line one, then "grub rescue" as a prompt. No way could I get anything to boot.

I used the Live CD again, and Gparted, and here's the report:

SDB
Unallocated    7.8Mb
/dev/sdb2 extended  465.75Gb
//dev/sdb5 ntfs  62.90Gb
/dev/sdb9  ext4  54.74Gb
unallocated  1.00Mb
/dev/sdb10 Linux Swap  2.37Gb
/dev/sdb6 ntfs  120.01
/dev/sdb7 ntfs  120.01
/dev/sdb8 ntfs  10573Gb

/dev/sda1  ntfs  74.51Gb
/dev/sda3  ext3  20.49Gb
/dev/sda2  extended  137.88Gb
/dev/sda6  fat32  21.22Gb (this is my Linux Home partition)
/dev/sda7  linux swap  988.34Mb
/dev/sda5  fat32  115.69Gb

From all this I think I now have Windows and 2 versions of Ubuntu, the original 9.10 and the new 10.03. It also seems to me that the new version is installed on the external disk, as when I remove it, the SDB references disappear in Gparted. I'm now stuck, as that's the extent of my knowledge of Linux/Grub and dual installs.

Can anyone suggest what I can do to get things right? I want 10.04 only on the machine, and on an internal HDD (replacing 9.10 that's on SDA) not the external. I know I can go the route of total reformat and install Windows then Ubuntu, but I'm not sure how I'd do that either.

So, there's my dilemma. I've mucked up beforte, and these forums have been my constant reference. I hope someone can give me a solution or workaround, or a Grub lesson. TIA for any help.

---

### Post by lechien73 on 2010-05-07
Using a Live CD, can you download and run [boot_info_script]("http://bootinfoscript.sourceforge.net/")? Post the contents of the RESULTS.txt file here surrounded by CODE tags (highlight the text and click the # button at the top of the post).

That will help us to see what disk the UUID you quoted belongs to.

Thanks

---

### Post by dino99 on 2010-05-07
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14 

sudo grub-mkconfig && update-grub

---

### Post by corowakid on 2010-05-07
> **lechien73 said:**
> Using a Live CD, can you download and run [boot_info_script]("http://bootinfoscript.sourceforge.net/")? Post the contents of the RESULTS.txt file here surrounded by CODE tags (highlight the text and click the # button at the top of the post).

That will help us to see what disk the UUID you quoted belongs to.

Thanks

Appreciate your help, but I can't get any response to the boot info. I know that v10.04 in installed on /dev/sdb9, which has a descriptor of /media/07162612-383e-4afe-bc01-ad3cfe04bc44. In it is a folder called "Boot" and in that is a folder called "Grub". I also found a UUID of 07162612-383e-4afe-bc01-ad3cfe04bc44. But for the life of me I can't access any of the folders through terminal - all I get is "no such directory". Can you give me any clue as to how I locate the information you mentioned in your post? I've spent an hour on this and got no where, except for seeing the UUID. Seems like I'm on a magical mystery toour. Any help appreciated.

---

### Post by corowakid on 2010-05-07
> **corowakid said:**
> Appreciate your help, but I can't get any response to the boot info. I know that v10.04 in installed on /dev/sdb9, which has a descriptor of /media/07162612-383e-4afe-bc01-ad3cfe04bc44. In it is a folder called "Boot" and in that is a folder called "Grub". I also found a UUID of 07162612-383e-4afe-bc01-ad3cfe04bc44. But for the life of me I can't access any of the folders through terminal - all I get is "no such directory". Can you give me any clue as to how I locate the information you mentioned in your post? I've spent an hour on this and got no where, except for seeing the UUID. Seems like I'm on a magical mystery toour. Any help appreciated.

Disregard this please. My bad. I now know what I've got to do, will get back here asap. Thanks

---

### Post by dino99 on 2010-05-07
simply do the command into post 3

---

### Post by corowakid on 2010-05-07
> **corowakid said:**
> Disregard this please. My bad. I now know what I've got to do, will get back here asap. Thanks

I hope this is what you referred to:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 245762433.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb10: _________________________________________________________________________

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,264,254   156,264,192   7 HPFS/NTFS
/dev/sda2         199,238,254   488,392,064   289,153,811   5 Extended
/dev/sda5         245,762,433   488,392,064   242,629,632   b W95 FAT32
/dev/sda6         199,238,256   243,738,179    44,499,924   b W95 FAT32
/dev/sda7         243,738,243   245,762,369     2,024,127  82 Linux swap / Solaris
/dev/sda3         156,264,255   199,238,129    42,973,875  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,126   976,768,064   976,751,939   5 Extended
/dev/sdb5              16,128   131,918,200   131,902,073   7 HPFS/NTFS
/dev/sdb6         251,690,418   503,364,644   251,674,227   7 HPFS/NTFS
/dev/sdb7         503,364,708   755,038,934   251,674,227   7 HPFS/NTFS
/dev/sdb8         755,038,998   976,768,064   221,729,067   7 HPFS/NTFS
/dev/sdb9         131,919,872   246,708,223   114,788,352  83 Linux
/dev/sdb10        246,710,272   251,688,959     4,978,688  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    31,588,351    31,588,289   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8C28275928274216                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        ee1276be-9160-47e5-a140-5855fcd72509   ext3                                     
/dev/sda5        4705-4B9F                              vfat                                     
/dev/sda6        2A3A-26FA                              vfat                                     
/dev/sda7        4024aec8-9244-1bbc-5af6-5a40efb0f1cb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       c1c78101-f014-4a87-8de1-1755a4792586   swap                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        82FCB95CA400CF59                       ntfs       Disk1                         
/dev/sdb6        4E200D9A200D89E3                       ntfs       Disk2                         
/dev/sdb7        8D4F841F908BAD4B                       ntfs       Disk3                         
/dev/sdb8        9AAEED314D80369A                       ntfs       Disk4                         
/dev/sdb9        07162612-383e-4afe-bc01-ad3cfe04bc44   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        70FD-0AEB                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb9        /media/07162612-383e-4afe-bc01-ad3cfe04bc44 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb7        /media/Disk3             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/Disk4             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/Disk1             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/Disk2             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/70FD-0AEB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ee1276be-9160-47e5-a140-5855fcd72509

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ee1276be-9160-47e5-a140-5855fcd72509 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2A3A-26FA  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=4024aec8-9244-1bbc-5af6-5a40efb0f1cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  95.9GB: boot/grub/menu.lst
  95.8GB: boot/grub/stage2
  95.5GB: boot/initrd.img-2.6.31-14-generic
  95.5GB: boot/initrd.img-2.6.31-19-generic
  95.5GB: boot/initrd.img-2.6.31-20-generic
  95.5GB: boot/vmlinuz-2.6.31-14-generic
  95.5GB: boot/vmlinuz-2.6.31-19-generic
  95.4GB: boot/vmlinuz-2.6.31-20-generic
  95.5GB: initrd.img
  95.5GB: initrd.img.old
  95.4GB: vmlinuz
  95.5GB: vmlinuz.old

=========================== sdb9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
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
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c28275928274216
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=c1c78101-f014-4a87-8de1-1755a4792586 none            swap    sw              0       0

=================== sdb9: Location of files loaded by Grub: ===================


  76.2GB: boot/grub/core.img
  91.7GB: boot/grub/grub.cfg
  76.2GB: boot/initrd.img-2.6.32-21-generic
  76.2GB: boot/vmlinuz-2.6.32-21-generic
  76.2GB: initrd.img
  76.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1b 1c 1d 1e 1f 20 21 22  23 24 25 26 27 28 29 2a  |..... !"#$%&'()*|
00000010  2b 2c 2d 2e 2f 30 31 32  33 34 35 36 37 38 39 3a  |+,-./0123456789:|
00000020  3b 3c 3d 3e 3f 40 41 42  43 44 45 46 47 48 49 4a  |;<=>?@ABCDEFGHIJ|
00000030  4b 4c 4d 4e 4f 50 51 52  53 54 55 56 57 58 59 5a  |KLMNOPQRSTUVWXYZ|
00000040  5b 5c 5d 5e 5f 60 61 62  63 64 65 66 67 68 69 6a  |[\]^_`abcdefghij|
00000050  6b 6c 6d 6e 6f 70 71 72  73 74 75 76 77 78 79 7a  |klmnopqrstuvwxyz|
00000060  7b 7c 7d 7e 7f 80 81 82  83 84 85 86 87 88 89 8a  |{|}~............|
00000070  8b 8c 8d 8e 8f 90 91 92  93 94 95 96 97 98 99 9a  |................|
00000080  9b 9c 9d 9e 9f a0 a1 a2  a3 a4 a5 a6 a7 a8 a9 aa  |................|
00000090  ab ac ad ae af b0 b1 b2  b3 b4 b5 b6 b7 b8 b9 ba  |................|
000000a0  bb bc bd be bf c0 c1 c2  c3 c4 c5 c6 c7 c8 c9 ca  |................|
000000b0  cb cc cd ce cf d0 d1 d2  d3 d4 d5 d6 d7 d8 d9 da  |................|
000000c0  db dc dd de df e0 e1 e2  e3 e4 e5 e6 e7 e8 e9 ea  |................|
000000d0  eb ec ed ee ef f0 f1 f2  f3 f4 f5 f6 f7 f8 f9 fa  |................|
000000e0  fb fc fd fe ff 00 01 02  03 04 05 06 07 08 09 0a  |................|
000000f0  0b 0c 0d 0e 0f 10 11 12  13 14 15 16 17 18 19 1a  |................|
00000100  1b 1c 1d 1e 1f 20 21 22  23 24 25 26 27 28 29 2a  |..... !"#$%&'()*|
00000110  2b 2c 2d 2e 2f 30 31 32  33 34 35 36 37 38 39 3a  |+,-./0123456789:|
00000120  3b 3c 3d 3e 3f 40 41 42  43 44 45 46 47 48 49 4a  |;<=>?@ABCDEFGHIJ|
00000130  4b 4c 4d 4e 4f 50 51 52  53 54 55 56 57 58 59 5a  |KLMNOPQRSTUVWXYZ|
00000140  5b 5c 5d 5e 5f 60 61 62  63 64 65 66 67 68 69 6a  |[\]^_`abcdefghij|
00000150  6b 6c 6d 6e 6f 70 71 72  73 74 75 76 77 78 79 7a  |klmnopqrstuvwxyz|
00000160  7b 7c 7d 7e 7f 80 81 82  83 84 85 86 87 88 89 8a  |{|}~............|
00000170  8b 8c 8d 8e 8f 90 91 92  93 94 95 96 97 98 99 9a  |................|
00000180  9b 9c 9d 9e 9f a0 a1 a2  a3 a4 a5 a6 a7 a8 a9 aa  |................|
00000190  ab ac ad ae af b0 b1 b2  b3 b4 b5 b6 b7 b8 b9 ba  |................|
000001a0  bb bc bd be bf c0 c1 c2  c3 c4 c5 c6 c7 c8 c9 ca  |................|
000001b0  cb cc cd ce cf d0 d1 d2  d3 d4 d5 d6 d7 d8 00 fe  |................|
000001c0  ff ff 0b fe ff ff 13 e7  c5 02 00 3c 76 0e 00 fe  |...........<v...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 d5 03 a7 02 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  64 65 20 63 6c 61 73 73  3d 22 66 69 6c 65 6e 61  |de class="filena|
00000010  6d 65 22 3e 2f 65 74 63  2f 6d 61 69 6c 2f 73 65  |me">/etc/mail/se|
00000020  6e 64 6d 61 69 6c 2e 6d  63 3c 2f 63 6f 64 65 3e  |ndmail.mc</code>|
00000030  20 61 6e 64 20 63 68 61  6e 67 65 20 74 68 65 0a  | and change the.|
00000040  20 20 20 20 20 20 3c 63  6f 64 65 20 63 6c 61 73  |      <code clas|
00000050  73 3d 22 6f 70 74 69 6f  6e 22 3e 44 41 45 4d 4f  |s="option">DAEMO|
00000060  4e 5f 4f 50 54 49 4f 4e  53 3c 2f 63 6f 64 65 3e  |N_OPTIONS</code>|
00000070  20 6c 69 6e 65 20 74 6f  20 61 6c 73 6f 20 6c 69  | line to also li|
00000080  73 74 65 6e 20 6f 6e 20  6e 65 74 77 6f 72 6b 0a  |sten on network.|
00000090  20 20 20 20 20 20 64 65  76 69 63 65 73 2c 20 6f  |      devices, o|
000000a0  72 20 63 6f 6d 6d 65 6e  74 20 6f 75 74 20 74 68  |r comment out th|
000000b0  69 73 20 6f 70 74 69 6f  6e 20 65 6e 74 69 72 65  |is option entire|
000000c0  6c 79 20 75 73 69 6e 67  20 74 68 65 0a 20 20 20  |ly using the.   |
000000d0  20 20 20 3c 63 6f 64 65  20 63 6c 61 73 73 3d 22  |   <code class="|
000000e0  6c 69 74 65 72 61 6c 22  3e 64 6e 6c 3c 2f 63 6f  |literal">dnl</co|
000000f0  64 65 3e 20 63 6f 6d 6d  65 6e 74 20 64 65 6c 69  |de> comment deli|
00000100  6d 69 74 65 72 2e 20 54  68 65 6e 20 69 6e 73 74  |miter. Then inst|
00000110  61 6c 6c 20 74 68 65 0a  20 20 20 20 20 20 3c 73  |all the.      <s|
00000120  70 61 6e 20 63 6c 61 73  73 3d 22 70 61 63 6b 61  |pan class="packa|
00000130  67 65 22 3e 73 65 6e 64  6d 61 69 6c 2d 63 66 3c  |ge">sendmail-cf<|
00000140  2f 73 70 61 6e 3e 20 70  61 63 6b 61 67 65 20 61  |/span> package a|
00000150  6e 64 20 72 65 67 65 6e  65 72 61 74 65 0a 20 20  |nd regenerate.  |
00000160  20 20 20 20 3c 63 6f 64  65 20 63 6c 61 73 73 3d  |    <code class=|
00000170  22 66 69 6c 65 6e 61 6d  65 22 3e 2f 65 74 63 2f  |"filename">/etc/|
00000180  6d 61 69 6c 2f 73 65 6e  64 6d 61 69 6c 2e 63 66  |mail/sendmail.cf|
00000190  3c 2f 63 6f 64 65 3e 20  62 79 20 72 75 6e 6e 69  |</code> by runni|
000001a0  6e 67 20 74 68 65 0a 20  20 20 20 20 20 66 6f 6c  |ng the.      fol|
000001b0  6c 6f 77 69 6e 67 20 63  6f 6d 6d 61 6e 64 00 01  |lowing command..|
000001c0  01 01 07 fe ff ff 02 00  00 00 79 aa dc 07 00 fe  |..........y.....|
000001d0  ff ff 05 fe ff ff 75 3e  00 0f b2 3e 00 0f 00 00  |......u>...>....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Doe this show what you expected me to produce? TIA for help

---

### Post by corowakid on 2010-05-07
> **dino99 said:**
> simply do the command into post 3

Thanks for that. I got the following reply to the command:

usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

This is beyond my knowledge, so can you offer any suggestions?

I remember reading a post for fixing the MBR using the Windows disk. If I did this, I'd at least be able to access Windoze. From there I'd seek suggestions on how I can remove both Linux versions (with the MBR changed, would using Gparted to delete all Linux partitions work? - then I could start with a new setup and only instal 01.04)

Would really appreciate your comments.

---

### Post by vijaycegcse on 2010-05-08
I have a similar problem with the dual boot in Grub2, when I upgraded from 9.10 to 10.04. Infact, the dual boot worked perfectly in 9.10, which I installed from a cd, but when I upgraded this morning, I found that I could not enter into Windows XP through the grub menu. Though an entry is there, it is not getting into the Windows OS, I am able to enter only into Ubuntu.  The contents in grub.cfg are :

I think the hard disk partition (hd0,1) is correct where I have installed XP, and (hd0,9) is the Linux installed partition. Please help me out. :-(

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set dc38-f7d2
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

**_DISK INFORMATION:_**

root@vijay-desktop:/home/vijay# fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46164616

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2480    19920568+   c  W95 FAT32 (LBA)
/dev/sda2            2481        9729    58227592+   f  W95 Ext'd (LBA)
/dev/sda5            2481        4960    19920568+   b  W95 FAT32
/dev/sda6            4961        7440    19920568+   b  W95 FAT32
/dev/sda7            7441        8460     8193118+   b  W95 FAT32
/dev/sda8            8461        8584      995998+  82  Linux swap / Solaris
/dev/sda9            8585        9729     9197181   83  Linux

The Output of my GPARTED is as follows:

[IMG]http://www.postimage.org/image.php?v=aVsvMN0[/IMG]

[http://www.postimage.org/image.php?v=aVsvMN0](http://www.postimage.org/image.php?v=aVsvMN0)

---

### Post by kansasnoob on 2010-05-08
You have Win XP on sda1, Ubuntu 9.10 on sda3, and Ubuntu 10.04 on sdb9. The easiest way to get all three booting would be to boot an Ubuntu Live CD and from the Live Desktop run:

```
sudo mount /dev/sdb9 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

Note if either of the above shows errors use the command:

```
grub-install --recheck /dev/sdX
```

Of course replace the X with the proper drive designation.

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

But while you're in the Live Desktop you should also go to Gparted and remove the boot flag on sdb2:

```
Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    **[COLOR="Red"]*[/COLOR]**         16,126   976,768,064   976,751,939   5 Extended
/dev/sdb5              16,128   131,918,200   131,902,073   7 HPFS/NTFS
/dev/sdb6         251,690,418   503,364,644   251,674,227   7 HPFS/NTFS
/dev/sdb7         503,364,708   755,038,934   251,674,227   7 HPFS/NTFS
/dev/sdb8         755,038,998   976,768,064   221,729,067   7 HPFS/NTFS
/dev/sdb9         131,919,872   246,708,223   114,788,352  83 Linux
/dev/sdb10        246,710,272   251,688,959     4,978,688  82 Linux swap / Solaris
```

Does sdb even have any primary partitions?

---

### Post by kansasnoob on 2010-05-08
> **vijaycegcse said:**
> I have a similar problem with the dual boot in Grub2, when I upgraded from 9.10 to 10.04. Infact, the dual boot worked perfectly in 9.10, which I installed from a cd, but when I upgraded this morning, I found that I could not enter into Windows XP through the grub menu. Though an entry is there, it is not getting into the Windows OS, I am able to enter only into Ubuntu.  The contents in grub.cfg are :

I think the hard disk partition (hd0,1) is correct where I have installed XP, and (hd0,9) is the Linux installed partition. Please help me out. :-(

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set dc38-f7d2
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

**_DISK INFORMATION:_**

root@vijay-desktop:/home/vijay# fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46164616

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2480    19920568+   c  W95 FAT32 (LBA)
/dev/sda2            2481        9729    58227592+   f  W95 Ext'd (LBA)
/dev/sda5            2481        4960    19920568+   b  W95 FAT32
/dev/sda6            4961        7440    19920568+   b  W95 FAT32
/dev/sda7            7441        8460     8193118+   b  W95 FAT32
/dev/sda8            8461        8584      995998+  82  Linux swap / Solaris
/dev/sda9            8585        9729     9197181   83  Linux

The Output of my GPARTED is as follows:

[IMG]http://www.postimage.org/image.php?v=aVsvMN0[/IMG]

[http://www.postimage.org/image.php?v=aVsvMN0](http://www.postimage.org/image.php?v=aVsvMN0)

Every grub problem is different to a degree, you should start your own thread and include the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It sounds like it might be this problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But we can only know for sure when we see that output.

---

### Post by oldfred on 2010-05-08
Kansasnoob's instructions reinstalling grub2 to sda will get you  booting but grub2 will be in sda and boot the install in sdb. I like to have the MBR of a drive have its boot loader in the same drive.

If you do not want your install in sdb, you will have to use gparted to delete it.

You should use manual install if you want to install/overwrite your existing partitions in sda. Just be sure to have everything backed up first. I like to alternate install partitions so I have an old copy and the current copy. With manual install be sure to use the advanced button on screen #8 "Ready to Install" to make sure where grub is installed.

You mention a /home but you are not mounting any /home and the partition you mention is FAT. Ubuntu needs a linux partition for both root & home as permissions & ownership are not supported in windows partitions.

---

### Post by corowakid on 2010-05-08
> **kansasnoob said:**
> You have Win XP on sda1, Ubuntu 9.10 on sda3, and Ubuntu 10.04 on sdb9. The easiest way to get all three booting would be to boot an Ubuntu Live CD and from the Live Desktop run:

```
sudo mount /dev/sdb9 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

Note if either of the above shows errors use the command:

```
grub-install --recheck /dev/sdX
```

Of course replace the X with the proper drive designation.

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

But while you're in the Live Desktop you should also go to Gparted and remove the boot flag on sdb2:

```
Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    **[COLOR="Red"]*[/COLOR]**         16,126   976,768,064   976,751,939   5 Extended
/dev/sdb5              16,128   131,918,200   131,902,073   7 HPFS/NTFS
/dev/sdb6         251,690,418   503,364,644   251,674,227   7 HPFS/NTFS
/dev/sdb7         503,364,708   755,038,934   251,674,227   7 HPFS/NTFS
/dev/sdb8         755,038,998   976,768,064   221,729,067   7 HPFS/NTFS
/dev/sdb9         131,919,872   246,708,223   114,788,352  83 Linux
/dev/sdb10        246,710,272   251,688,959     4,978,688  82 Linux swap / Solaris
```

Does sdb even have any primary partitions?

SDB doesn't have any primaries - its an external HDD 500Gb.

Did the scripting - first time round I got the same error on rebooting. Went back in to Terminal and deleted the space I'd put in first line between --bind /dev /mnt/dev && sudo, to &&sudo.

This time root couldn't find Grub, looked into the system and loaded it eventually. The other commands reported no error.

Shut down and on restart I got:
Grub Loading Stage1.5
Grub Loading please wait...
Error 21

Got no further. Seems the fix you gave me almost got me over the line. Can you hazard a guess at what I did wrong?

---

### Post by kansasnoob on 2010-05-08
> Did the scripting - first time round I got the same error on rebooting. Went back in to Terminal and deleted the space I'd put in first line between --bind /dev /mnt/dev && sudo, to &&sudo.

So you're typing commands? Please, please, please copy-n-paste! That's the whole purpose of placing them in code tags.

Just double click to highlight, right click to copy, and right click again to paste!

**[COLOR="Red"]But let me type a new set of commands![/COLOR]** I did not know that sdb was an external drive!

If my method did succeed you'd only be able to boot with the external plugged in. In fact do you even want 10.04 on the external?

---

### Post by kansasnoob on 2010-05-08
I first need to clear up my own confusion here. You said, "My PC has 2 HDD and an external drive, both HDD partitioned into 2."

fdisk shows:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
Disk /dev/sdc: 16.2 GB, 16173236224 bytes

Also sdc is NOT "partitioned into 2":

> Disk /dev/sdc: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    31,588,351    31,588,289   c W95 FAT32 (LBA)

So your internal drives are sda and sdc? It's unusual to see an internal with a higher designation than an internal. That said the OS's are where I said they are:

> You have Win XP on sda1, Ubuntu 9.10 on sda3, and Ubuntu 10.04 on sdb9.

Now since your Karmic has legacy grub:

> sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

To restore the grub mbr on sda you'll either need to use a Jaunty (9.04) or earlier Live CD and follow the steps here:

> How to restore the Ubuntu grub bootloader (9.04 and older)

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or if you don't have an older CD you can use a Karmic or Lucid Live CD and (just be sure to copy-n-paste):

```
sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
sudo grub
```

```
root (hd0,2)
```

```
setup (hd0)
```

```
quit
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

If you want to keep the Lucid install on the external and make it bootable only when the external is plugged in you'll first need to adjust the boot order in your BIOS so the USB drive boots before the internal drive(s). I usually keep mine set to boot from CD first, USB second, and hard drive third. Then from the Live Desktop with the external plugged in:

```
sudo mount /dev/sdb9 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

If that returns any errors also:

```
grub-install --recheck /dev/sdb
```

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Sorry for the misunderstanding.

---

### Post by corowakid on 2010-05-09
Please do not offer apologies - without you pesevering I'd be up s**t creek without a paddle. I have the 9.04 Live CD and I'll go through the procedure tonight. I'm printing all comments on this thread so I improve my knowledge base. No doubt about it, Ubuntu adherents are the most accommodating to newbies. I live in a really small town, and help oldies like me with Windows education. I've got 2 of them using Ubuntu at the moment, unaware they are on Linux, as the things they do are seamless to the way they do it in Windows.

Many thanks for your help, and if its OK with you I'll come back after I finish digesting and doing the suggested steps. Hopefully you'll also see [Solved] as well!

---

### Post by corowakid on 2010-05-09
Thanks Kansasnoob - used the 9.04 live cd and got back to where I started. Lost nothing!

Now, I assume I can reformat my external HDD where I had 10.04 installed? (I've backed up all the partition info except for the 10.04 partitions). I shouldn't then see any remains of the 10.04 instal, should I?

And then I assume I can do the update that 9.10 shows as the 10.04 instal. Would that be the way to go, or should I go through the process of installing 10.04 from the live CD, except this time reading the instructions *thoroughly*. I'm still missing something in my knowledge of Grub 2 so I can do the reading before I instal 10.04.

Many thanks again for your help, seems the forums once again saved my skin. And added to my knowledge base. Great work! Regards and thanks.

---

### Post by kansasnoob on 2010-05-09
> used the 9.04 live cd and got back to where I started. Lost nothing!

Great, so you're booting with 9.10 now, eh?

> Now, I assume I can reformat my external HDD where I had 10.04 installed? (I've backed up all the partition info except for the 10.04 partitions). I shouldn't then see any remains of the 10.04 instal, should I?

No need to reformat the whole drive. It looks like sdb9 (the 10.04 root partition) and sdb10 (SWAP) are on the very end of the drive. (Although fdisk does not always show partitions in their actual order).

But I'd guess the auto-partitioning simply shrunk sdb8 so you should be able to just use Gparted to delete sdb9 and sdb10, then "resize" sda8 again to regain that space.

Have you ever used Gparted? It's on the Ubuntu Live CD in System > Administration:

[ATTACH]156245[/ATTACH]

It's really a sweet, reliable tool. But never use it for resizing Vista or Win 7, use only their own tools for resizing them :)

> And then I assume I can do the update that 9.10 shows as the 10.04 instal. Would that be the way to go, or should I go through the process of installing 10.04 from the live CD, except this time reading the instructions *thoroughly*. I'm still missing something in my knowledge of Grub 2 so I can do the reading before I instal 10.04.

Well, upgrades are always a crap shoot. Sometimes they work out well and others not, also the average upgrade takes 2 1/2 to 3 hours whereas a fresh install takes about 30 minutes + configuration time + adding apps, etc. As you can see in that screenshot of Gparted I multi-boot a lot.

I just built this machine a few weeks ago so I'm still just getting it up to speed but you can see I have Ubuntu Karmic, Lucid, and Maverick (of course Maverick is in very early development), and also Debian Lenny and Squeeze, and the newest Mint.

You'll also notice that each has it's own small /home which contains most personal settings, Mozilla and Opera profiles, etc. Most people would want a much larger /home because it also contains all of the Folders like Documents, Pictures, Downloads, etc, but I symlink separate partitions for that so I have the same folders shared by all the operating systems.

Anyway I'm straying, but I've always preferred a fresh "parallel" install if disc space allows it. The advantages are obvious:

1) If the new install is "buggy" you can still use the old install and take your time working things out.

2) If you used the same username and password you can easily move data from one install to the other.

3) You can always have the "latest and greatest" Ubuntu but still have an older OS that you know "just works".

4) When the next new release comes out you can just "overwrite" whichever OS you're least satisfied with. For instance Karmic never would run well on my VIA hardware so I kept Jaunty as my stable OS and replaced it's Karmic with Lucid.

Of course I can't tell how much free space you have on sda without a screenshot of Gparted, if you posted one I'd be willing to make some suggestions.

Another thought however, unless having that Lucid on the external just completely ticks you off, you could leave it there for now, install it's grub2 to the mbr of sdb and try it out for a while.

If you want to make lucid bootable when the external is plugged in just plug it in while booted into Karmic and run these commands from Karmic:

```
sudo mount /dev/sdb9 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

And only if that returns any errors:

```
grub-install --recheck /dev/sdb
```

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Now if your BIOS is set to boot the USB drive before the internals you'll get Lucid's grub2 menu when the external is plugged in, but when the external is not plugged in you'll get Karmic's grub menu.

Of course that may not be what you want :confused:

Finally, this may be very helpful, with any complex partitioning layout I'd never use any of Ubuntu's "auto-partitioning" installation methods! NEVER!

I prefer creating my partitions ahead of time using Gparted and then choosing the "manual/advanced" option like shown here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

I don't really care for Herman's exact partition layout but he has excellent illustrated guides:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

If you have more questions that's cool :)

Planning in advance is always the best way to go.

---

### Post by corowakid on 2010-05-13
This is for Kansasnoob

Thanks for the suggestions, I'm a bit late responding, but I wanted to grasp the moves before I went ahead.

I loaded the Karmic CD again and plugged in the USB external hdd, a Freeagent Seagate 500Gb. Seems a real good idea to access 10.04 and 9.10 before I finally make a decision. Went thru the Copy & Paste method of compiling the commands in Terminal (thanks for the heads-up about highlight/copy/paste. I do this in Windows so I should have been able to remember to do it in Linux!). The command went thru OK, no errors, so I didn't need to run the alternative script.

I went into the BIOS and made sure the external HDD was the 1st item (shown as "removable disk" in the BIOS), then made it CD then internal HDD as suggested. I re-started but only got the Grub 1.5 splash screen - no sign of the external HDD. I went through the process again, no errors reported, and still can't get Grub 2 to come up.

From all this, is there any way you can determine why I'm having this problem? I want to send the Gparted screen to you, but don't know how to capture it - I assume I put it in tags like I did the outputs I sent. Can you tell me how to do this.

I realise you're not here to teach me Linux, but these steps are all linked to my forum request, so any help would really be appreciated. In the worst case scenario I assume I delete the 2 partitions on SDB, format the free space to FAT - and I assume the Grub 2 file won't be seen (do I delete it, or does that happen when I make the changes to the external HDD.

---

### Post by oldfred on 2010-05-13
Rerun the boot_info script as it will tell you where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by corowakid on 2010-05-14
Here are the results of my boot info script. Can anyone help me identify how to get Ubuntu 10.04 to boot via Grub please? thanks

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 245762433.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb10: _________________________________________________________________________

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac2dac2d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,264,254   156,264,192   7 HPFS/NTFS
/dev/sda2         199,238,254   488,392,064   289,153,811   5 Extended
/dev/sda5         245,762,433   488,392,064   242,629,632   b W95 FAT32
/dev/sda6         199,238,256   243,738,179    44,499,924   b W95 FAT32
/dev/sda7         243,738,243   245,762,369     2,024,127  82 Linux swap / Solaris
/dev/sda3         156,264,255   199,238,129    42,973,875  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00035d98

Partition  Boot         Start           End          Size  Id System

/dev/sdb2              16,126   976,768,064   976,751,939   5 Extended
/dev/sdb5              16,128   131,918,200   131,902,073   7 HPFS/NTFS
/dev/sdb6         251,690,418   503,364,644   251,674,227   7 HPFS/NTFS
/dev/sdb7         503,364,708   755,038,934   251,674,227   7 HPFS/NTFS
/dev/sdb8         755,038,998   976,768,064   221,729,067   7 HPFS/NTFS
/dev/sdb9         131,919,872   246,708,223   114,788,352  83 Linux
/dev/sdb10        246,710,272   251,688,959     4,978,688  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    31,588,351    31,588,289   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8C28275928274216                       ntfs                                     
/dev/sda3        ee1276be-9160-47e5-a140-5855fcd72509   ext3                                     
/dev/sda5        4705-4B9F                              vfat                                     
/dev/sda6        2A3A-26FA                              vfat                                     
/dev/sda7        4024aec8-9244-1bbc-5af6-5a40efb0f1cb   swap                                     
/dev/sdb10       c1c78101-f014-4a87-8de1-1755a4792586   swap                                     
/dev/sdb5        82FCB95CA400CF59                       ntfs       Disk1                         
/dev/sdb6        4E200D9A200D89E3                       ntfs       Disk2                         
/dev/sdb7        8D4F841F908BAD4B                       ntfs       Disk3                         
/dev/sdb8        9AAEED314D80369A                       ntfs       Disk4                         
/dev/sdb9        07162612-383e-4afe-bc01-ad3cfe04bc44   ext4                                     
/dev/sdc1        70FD-0AEB                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda6        /windows                 vfat       (rw,utf8,umask=007,gid=46)
/dev/sdb9        /media/07162612-383e-4afe-bc01-ad3cfe04bc44 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb5        /media/Disk1             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb7        /media/Disk3             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb6        /media/Disk2             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb8        /media/Disk4             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /media/70FD-0AEB         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ee1276be-9160-47e5-a140-5855fcd72509

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ee1276be-9160-47e5-a140-5855fcd72509 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2A3A-26FA  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=4024aec8-9244-1bbc-5af6-5a40efb0f1cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  95.9GB: boot/grub/menu.lst
  95.8GB: boot/grub/stage2
  95.5GB: boot/initrd.img-2.6.31-14-generic
  95.5GB: boot/initrd.img-2.6.31-19-generic
  95.5GB: boot/initrd.img-2.6.31-20-generic
  95.5GB: boot/initrd.img-2.6.31-21-generic
  95.5GB: boot/vmlinuz-2.6.31-14-generic
  95.5GB: boot/vmlinuz-2.6.31-19-generic
  95.5GB: boot/vmlinuz-2.6.31-20-generic
  95.5GB: boot/vmlinuz-2.6.31-21-generic
  95.5GB: initrd.img
  95.5GB: initrd.img.old
  95.5GB: vmlinuz
  95.5GB: vmlinuz.old

=========================== sdb9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
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
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c28275928274216
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ee1276be-9160-47e5-a140-5855fcd72509
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=c1c78101-f014-4a87-8de1-1755a4792586 none            swap    sw              0       0

=================== sdb9: Location of files loaded by Grub: ===================


  76.2GB: boot/grub/core.img
  91.7GB: boot/grub/grub.cfg
  76.1GB: boot/grub/stage2
  76.2GB: boot/initrd.img-2.6.32-21-generic
  76.2GB: boot/vmlinuz-2.6.32-21-generic
  76.2GB: initrd.img
  76.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1b 1c 1d 1e 1f 20 21 22  23 24 25 26 27 28 29 2a  |..... !"#$%&'()*|
00000010  2b 2c 2d 2e 2f 30 31 32  33 34 35 36 37 38 39 3a  |+,-./0123456789:|
00000020  3b 3c 3d 3e 3f 40 41 42  43 44 45 46 47 48 49 4a  |;<=>?@ABCDEFGHIJ|
00000030  4b 4c 4d 4e 4f 50 51 52  53 54 55 56 57 58 59 5a  |KLMNOPQRSTUVWXYZ|
00000040  5b 5c 5d 5e 5f 60 61 62  63 64 65 66 67 68 69 6a  |[\]^_`abcdefghij|
00000050  6b 6c 6d 6e 6f 70 71 72  73 74 75 76 77 78 79 7a  |klmnopqrstuvwxyz|
00000060  7b 7c 7d 7e 7f 80 81 82  83 84 85 86 87 88 89 8a  |{|}~............|
00000070  8b 8c 8d 8e 8f 90 91 92  93 94 95 96 97 98 99 9a  |................|
00000080  9b 9c 9d 9e 9f a0 a1 a2  a3 a4 a5 a6 a7 a8 a9 aa  |................|
00000090  ab ac ad ae af b0 b1 b2  b3 b4 b5 b6 b7 b8 b9 ba  |................|
000000a0  bb bc bd be bf c0 c1 c2  c3 c4 c5 c6 c7 c8 c9 ca  |................|
000000b0  cb cc cd ce cf d0 d1 d2  d3 d4 d5 d6 d7 d8 d9 da  |................|
000000c0  db dc dd de df e0 e1 e2  e3 e4 e5 e6 e7 e8 e9 ea  |................|
000000d0  eb ec ed ee ef f0 f1 f2  f3 f4 f5 f6 f7 f8 f9 fa  |................|
000000e0  fb fc fd fe ff 00 01 02  03 04 05 06 07 08 09 0a  |................|
000000f0  0b 0c 0d 0e 0f 10 11 12  13 14 15 16 17 18 19 1a  |................|
00000100  1b 1c 1d 1e 1f 20 21 22  23 24 25 26 27 28 29 2a  |..... !"#$%&'()*|
00000110  2b 2c 2d 2e 2f 30 31 32  33 34 35 36 37 38 39 3a  |+,-./0123456789:|
00000120  3b 3c 3d 3e 3f 40 41 42  43 44 45 46 47 48 49 4a  |;<=>?@ABCDEFGHIJ|
00000130  4b 4c 4d 4e 4f 50 51 52  53 54 55 56 57 58 59 5a  |KLMNOPQRSTUVWXYZ|
00000140  5b 5c 5d 5e 5f 60 61 62  63 64 65 66 67 68 69 6a  |[\]^_`abcdefghij|
00000150  6b 6c 6d 6e 6f 70 71 72  73 74 75 76 77 78 79 7a  |klmnopqrstuvwxyz|
00000160  7b 7c 7d 7e 7f 80 81 82  83 84 85 86 87 88 89 8a  |{|}~............|
00000170  8b 8c 8d 8e 8f 90 91 92  93 94 95 96 97 98 99 9a  |................|
00000180  9b 9c 9d 9e 9f a0 a1 a2  a3 a4 a5 a6 a7 a8 a9 aa  |................|
00000190  ab ac ad ae af b0 b1 b2  b3 b4 b5 b6 b7 b8 b9 ba  |................|
000001a0  bb bc bd be bf c0 c1 c2  c3 c4 c5 c6 c7 c8 c9 ca  |................|
000001b0  cb cc cd ce cf d0 d1 d2  d3 d4 d5 d6 d7 d8 00 fe  |................|
000001c0  ff ff 0b fe ff ff 13 e7  c5 02 00 3c 76 0e 00 fe  |...........<v...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 d5 03 a7 02 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  64 65 20 63 6c 61 73 73  3d 22 66 69 6c 65 6e 61  |de class="filena|
00000010  6d 65 22 3e 2f 65 74 63  2f 6d 61 69 6c 2f 73 65  |me">/etc/mail/se|
00000020  6e 64 6d 61 69 6c 2e 6d  63 3c 2f 63 6f 64 65 3e  |ndmail.mc</code>|
00000030  20 61 6e 64 20 63 68 61  6e 67 65 20 74 68 65 0a  | and change the.|
00000040  20 20 20 20 20 20 3c 63  6f 64 65 20 63 6c 61 73  |      <code clas|
00000050  73 3d 22 6f 70 74 69 6f  6e 22 3e 44 41 45 4d 4f  |s="option">DAEMO|
00000060  4e 5f 4f 50 54 49 4f 4e  53 3c 2f 63 6f 64 65 3e  |N_OPTIONS</code>|
00000070  20 6c 69 6e 65 20 74 6f  20 61 6c 73 6f 20 6c 69  | line to also li|
00000080  73 74 65 6e 20 6f 6e 20  6e 65 74 77 6f 72 6b 0a  |sten on network.|
00000090  20 20 20 20 20 20 64 65  76 69 63 65 73 2c 20 6f  |      devices, o|
000000a0  72 20 63 6f 6d 6d 65 6e  74 20 6f 75 74 20 74 68  |r comment out th|
000000b0  69 73 20 6f 70 74 69 6f  6e 20 65 6e 74 69 72 65  |is option entire|
000000c0  6c 79 20 75 73 69 6e 67  20 74 68 65 0a 20 20 20  |ly using the.   |
000000d0  20 20 20 3c 63 6f 64 65  20 63 6c 61 73 73 3d 22  |   <code class="|
000000e0  6c 69 74 65 72 61 6c 22  3e 64 6e 6c 3c 2f 63 6f  |literal">dnl</co|
000000f0  64 65 3e 20 63 6f 6d 6d  65 6e 74 20 64 65 6c 69  |de> comment deli|
00000100  6d 69 74 65 72 2e 20 54  68 65 6e 20 69 6e 73 74  |miter. Then inst|
00000110  61 6c 6c 20 74 68 65 0a  20 20 20 20 20 20 3c 73  |all the.      <s|
00000120  70 61 6e 20 63 6c 61 73  73 3d 22 70 61 63 6b 61  |pan class="packa|
00000130  67 65 22 3e 73 65 6e 64  6d 61 69 6c 2d 63 66 3c  |ge">sendmail-cf<|
00000140  2f 73 70 61 6e 3e 20 70  61 63 6b 61 67 65 20 61  |/span> package a|
00000150  6e 64 20 72 65 67 65 6e  65 72 61 74 65 0a 20 20  |nd regenerate.  |
00000160  20 20 20 20 3c 63 6f 64  65 20 63 6c 61 73 73 3d  |    <code class=|
00000170  22 66 69 6c 65 6e 61 6d  65 22 3e 2f 65 74 63 2f  |"filename">/etc/|
00000180  6d 61 69 6c 2f 73 65 6e  64 6d 61 69 6c 2e 63 66  |mail/sendmail.cf|
00000190  3c 2f 63 6f 64 65 3e 20  62 79 20 72 75 6e 6e 69  |</code> by runni|
000001a0  6e 67 20 74 68 65 0a 20  20 20 20 20 20 66 6f 6c  |ng the.      fol|
000001b0  6c 6f 77 69 6e 67 20 63  6f 6d 6d 61 6e 64 00 01  |lowing command..|
000001c0  01 01 07 fe ff ff 02 00  00 00 79 aa dc 07 00 fe  |..........y.....|
000001d0  ff ff 05 fe ff ff 75 3e  00 0f b2 3e 00 0f 00 00  |......u>...>....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Thanks

---

### Post by kansasnoob on 2010-05-14
The problem is very obvious:

> => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

That's legacy grub but the following shows sdb9 has grub2:

> sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


So I need you to do some troubleshooting for me by running the following commands:

```
sudo mount /dev/sdb9 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

```
ls /boot
```

```
ls /boot/grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then I need you to copy-n-paste that full terminal output back here just like I'm doing in this example:

```
lance@lance-desktop:~$ sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
root@lance-desktop:/# grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
grub-install (GNU GRUB 0.97)
Package: grub
State: installed
Automatically installed: no
Version: 0.97-29ubuntu59
Package: grub-pc
State: not installed
Version: 1.97~beta4-1ubuntu4.1
Priority: extra
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.97~beta4-1ubuntu4.1
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.35
root@lance-desktop:/# ls /boot
abi-2.6.31-14-generic	      memtest86+.bin
abi-2.6.31-20-generic	      System.map-2.6.31-14-generic
abi-2.6.31-21-generic	      System.map-2.6.31-20-generic
config-2.6.31-14-generic      System.map-2.6.31-21-generic
config-2.6.31-20-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-21-generic      vmcoreinfo-2.6.31-20-generic
grub			      vmcoreinfo-2.6.31-21-generic
grub_backup		      vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-20-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-21-generic
initrd.img-2.6.31-21-generic
root@lance-desktop:/# ls /boot/grub
default  grubenv  menu.lst  menu.lst~  menu.lst.backup	splashimages
root@lance-desktop:/# exit
exit
lance@lance-desktop:~$ sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt

```

NOTE: I used sda3 in my example so don't you use that! The OS you want to mount is on sdb9 :)

I would guess that packages got messed up on sdb9 when trying unsuccessfully to restore grub in Karmic. I'll know when I see that output.

You can still boot Karmic and Windows with the USB drive unplugged can't you?

---

### Post by corowakid on 2010-05-15
```
barrie@barrie-linux:~$ sudo mount /dev/sdb9 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
[sudo] password for barrie: 
root@barrie-linux:/# grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
grub-install (GNU GRUB 0.97)
Package: grub
State: installed
Automatically installed: no
Version: 0.97-29ubuntu60
Package: grub-pc
State: not installed
Version: 1.98-1ubuntu6
Priority: optional
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu5
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.38
root@barrie-linux:/# ls /boot
abi-2.6.32-21-generic
config-2.6.32-21-generic
grub
initrd.img-2.6.32-21-generic
memtest86+.bin
System.map-2.6.32-21-generic
vmcoreinfo-2.6.32-21-generic
vmlinuz-2.6.32-21-generic
root@barrie-linux:/# ls boot/grub
915resolution.mod
acpi.mod
affs.mod
afs_be.mod
afs.mod
aout.mod
ata.mod
ata_pthru.mod
at_keyboard.mod
befs_be.mod
befs.mod
biosdisk.mod
bitmap.mod
bitmap_scale.mod
blocklist.mod
boot.img
boot.mod
bsd.mod
bufio.mod
cat.mod
cdboot.img
chain.mod
charset.mod
cmp.mod
command.lst
configfile.mod
core.img
cpio.mod
cpuid.mod
crc.mod
crypto.lst
crypto.mod
datehook.mod
date.mod
datetime.mod
default
device.map
diskboot.img
dm_nv.mod
drivemap.mod
e2fs_stage1_5
echo.mod
efiemu32.o
efiemu64.o
efiemu.mod
elf.mod
example_functional_test.mod
ext2.mod
extcmd.mod
fat.mod
fat_stage1_5
font.mod
fshelp.mod
fs.lst
functional_test.mod
gcry_arcfour.mod
gcry_blowfish.mod
gcry_camellia.mod
gcry_cast5.mod
gcry_crc.mod
gcry_des.mod
gcry_md4.mod
gcry_md5.mod
gcry_rfc2268.mod
gcry_rijndael.mod
gcry_rmd160.mod
gcry_seed.mod
gcry_serpent.mod
gcry_sha1.mod
gcry_sha256.mod
gcry_sha512.mod
gcry_tiger.mod
gcry_twofish.mod
gcry_whirlpool.mod
gettext.mod
gfxmenu.mod
gfxterm.mod
gptsync.mod
grldr.img
grub.cfg
grubenv
gzio.mod
halt.mod
handler.lst
handler.mod
hashsum.mod
hdparm.mod
hello.mod
help.mod
hexdump.mod
hfs.mod
hfsplus.mod
installed-version
iso9660.mod
jfs.mod
jfs_stage1_5
jpeg.mod
kernel.img
keystatus.mod
linux16.mod
linux.mod
lnxboot.img
load.cfg
loadenv.mod
locale
loopback.mod
lsmmap.mod
ls.mod
lspci.mod
lvm.mod
mdraid.mod
memdisk.mod
memrw.mod
minicmd.mod
minix.mod
minix_stage1_5
mmap.mod
moddep.lst
msdospart.mod
multiboot2.mod
multiboot.mod
normal.mod
ntfscomp.mod
ntfs.mod
ohci.mod
part_acorn.mod
part_amiga.mod
part_apple.mod
part_gpt.mod
partmap.lst
part_msdos.mod
part_sun.mod
parttool.lst
parttool.mod
password.mod
password_pbkdf2.mod
pbkdf2.mod
pci.mod
play.mod
png.mod
probe.mod
pxeboot.img
pxecmd.mod
pxe.mod
raid5rec.mod
raid6rec.mod
raid.mod
read.mod
reboot.mod
reiserfs.mod
reiserfs_stage1_5
relocator.mod
scsi.mod
search_fs_file.mod
search_fs_uuid.mod
search_label.mod
search.mod
serial.mod
setjmp.mod
setpci.mod
sfs.mod
sh.mod
sleep.mod
stage1
stage2
tar.mod
terminal.lst
terminal.mod
terminfo.mod
test.mod
tga.mod
trig.mod
true.mod
udf.mod
ufs1.mod
ufs2.mod
uhci.mod
usb_keyboard.mod
usb.mod
usbms.mod
usbtest.mod
vbeinfo.mod
vbe.mod
vbetest.mod
vga.mod
vga_text.mod
video_fb.mod
video.lst
video.mod
videotest.mod
xfs.mod
xfs_stage1_5
xnu.mod
xnu_uuid.mod
zfsinfo.mod
zfs.mod
root@barrie-linux:/# exit
exit
barrie@barrie-linux:~$ sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
barrie@barrie-linux:~$ ^C
barrie@barrie-linux:~$ 

```

First, I can't boot into 9.10 at normal resolution of 1680x1200. Message is only low resolution is available because config file can't be found.

Obviously I can't understand what I just did, other than following your instructions - the output is beyond me.

I'd appreciate your advice as to what you see that might be the problem. Regards

---

### Post by oldfred on 2010-05-15
You may want to start a new thread as those with better understanding of video issues will look a video issue title, but not a grub issue.

For me I just had to install the nvidia drives and it worked. I have seen others that had to do something with config files, but have not paid close attention. You can also search forum from google with your video card and 
Just append site:ubuntuforums.org to your search terms.

---

### Post by kansasnoob on 2010-05-15
Just as expected:

> root@barrie-linux:/# grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
**[COLOR="Red"]grub-install (GNU GRUB 0.97)[/COLOR]**
[B][COLOR="Red"]Package: grub
State: installed[/COLOR][/B]
Automatically installed: no
Version: 0.97-29ubuntu60
[B][COLOR="Red"]Package: grub-pc
State: not installed[/COLOR][/B]
Version: 1.98-1ubuntu6
Priority: optional
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu5
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.38


Just so you know, both legacy grub and grub2 use the package "grub-common". The package "grub" is legacy grub and the package "grub-pc" is grub2. So, since the package "grub" was installed rather than "grub-pc" you ended up with a legacy grub mbr instead of a grub2 mbr.

It appears that if someone tries to follow the "grub restore" directions for legacy grub on a grub2 install packages can get messed up due to erroneous suggestions made in terminal. But it doesn't matter how it got that way :)

We can fix that pretty easy, just give me a bit to slurp some more coffee, and I'll parse everything again and give you a knew set of commands.

Regarding that graphics problem we'll need to see the output of:

```
lspci | grep VGA
```

That'll tell us what graphics card you have.

---

### Post by kansasnoob on 2010-05-15
Since we have to remove and install packages we need to add more commands to the mount and chroot procedure. Just so you have some idea what we're doing you might want to browse this:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

And off to the races we go:

```
sudo mount /dev/sdb9 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
apt-get update
```

```
apt-get remove grub
```

```
apt-get install grub-pc
```

Note: as "grub-pc" installs you'll probably get a couple of prompts! Something about "grub terminal command" - just press enter, next about "where" to install grub - remember you want to **[COLOR="Red"]install grub to /dev/sdb only![/COLOR]**

```
grub-install /dev/sdb
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

That should be it, but **[COLOR="Red"]if you encounter any errors at all post the full terminal output here[/COLOR]**. That's the only way I can see what's happening on your end :)

---

### Post by corowakid on 2010-05-16
Well, thanks for the help post. Did all the steps you outlined, using the installed 9.10 OS - everything went through, with no errors reported. SDB was the destination for Grub2 as you mentioned.

I re-booted, and got:

error: no such device: 07162612-383e-4afe-bc01-ad3cfe04bc44" on line one, then "grub rescue" as a prompt.

This is the same reference as I originally reported, and seems to suggest there's some underlying reason behind the problems I'm having.

Rather than waste your time further (and by that I mean you've gone above and beyond what I would have expected), I'm of a mind to delete 9.10 and 10.04 and make the partitions free space and make a better selection of where both programs reside. But I don't know if I'll still get this error because Grub is in the MBR or somesuch. Can you tell me the best way for me delete all the Linux partitions, and the Grub entries. I think I'll then re-install 9.10, which has worked flawlessly since I installed it last year, and I'll wait a while before I download 10.04.

I'm sorry to have wasted your time, I really appreciate the interest and help you've provided. But rather than have this as a long-standing issue, I think you, and I, would be better served by doing what I think is preferable.

Given that, any help on the Grub removal/change etc would be greatly appreciated. TIA for your comment.

---

### Post by kansasnoob on 2010-05-16
> **corowakid said:**
> Well, thanks for the help post. Did all the steps you outlined, using the installed 9.10 OS - everything went through, with no errors reported. SDB was the destination for Grub2 as you mentioned.

I re-booted, and got:

error: no such device: 07162612-383e-4afe-bc01-ad3cfe04bc44" on line one, then "grub rescue" as a prompt.

This is the same reference as I originally reported, and seems to suggest there's some underlying reason behind the problems I'm having.

Rather than waste your time further (and by that I mean you've gone above and beyond what I would have expected), I'm of a mind to delete 9.10 and 10.04 and make the partitions free space and make a better selection of where both programs reside. But I don't know if I'll still get this error because Grub is in the MBR or somesuch. Can you tell me the best way for me delete all the Linux partitions, and the Grub entries. I think I'll then re-install 9.10, which has worked flawlessly since I installed it last year, and I'll wait a while before I download 10.04.

I'm sorry to have wasted your time, I really appreciate the interest and help you've provided. But rather than have this as a long-standing issue, I think you, and I, would be better served by doing what I think is preferable.

Given that, any help on the Grub removal/change etc would be greatly appreciated. TIA for your comment.

**Please take time to read this all** :)

OK, I need to digest this and try to understand what went amiss. Back at your post #17 you said:

> used the 9.04 live cd and got back to where I started. Lost nothing!

So after that you had Windows and Karmic both booting properly, right?

If so why would you now want to wipe Karmic?

The graphics problem? If so I never did see the output of:

```
lspci | grep VGA
```

And as oldfred said that may be best addressed in a separate thread titled to draw the attention of those who best understand graphics issues.

Anyway, can you at least still boot Windows and Karmic with the external drive unplugged?

And you only get that boot error when the external is plugged in?

I realize you're frustrated but you'd be doing me a big favor if you'd post a new output of the Boot Info Script. That's how we learn :)

But as far as making Windows boot again with no Ubuntu installed you can always restore a Windows mbr following this guide:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

or what I do is just use an Ubuntu Live CD and run:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sd**[COLOR="Red"]X[/COLOR]** mbr
```

Of course **[COLOR="Red"]X[/COLOR]** must be replaced by the proper drive designation letter (your Windows is on /dev/sda).

As far as proper partitioning I suppose my biggest concern is that you have no primary partition at all on sdb. Even though it's not intended to have an OS on that drive I've always believed that a drive should begin with at least one primary partition.

Some general info:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning](http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning)

I multi-boot a lot so I have an "odd" setup:

[ATTACH]157149[/ATTACH]

I always use a separate /home to make reinstalling easier but most people would want a much larger /home! The reason I use a small /home is that I symlink my Documents, Downloads, etc so they're easily accessible from any of my OS's.

Before I made any personal recommendations I'd want to see some Gparted screenshots of both drives, an explanation of what you want, how much total space you want to dedicate to Ubuntu, total size of RAM, etc.

As far as this error:

> error: no such device: 07162612-383e-4afe-bc01-ad3cfe04bc44" on line one, then "grub rescue" as a prompt.

[B]error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
This error is the result of a failure of the GRUB 2 search function. There are various bugs associated with the search function. To boot into your system, highlight the OS you want to boot. Press "e" to edit the menuentry. Delete the entire "search ..." line, then CTRL-x to boot.

Once you have booted into the system, you will modify the /usr/lib/grub/grub-mkconfig_lib file in accordance with this link:[/B]

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

That is taken from:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

BTW I checked and your UUID's look fine.

I'll be here, and I'll keep checking back :)

---

### Post by corowakid on 2010-05-17
For kansasboob.

I've been into and out of Ubuntu 9.04 Live CD the last couple of days, and the graphics problem hasn't surfaced again. So I think that can be discounted for the present, and if it recurs I'll start another thread to get ideas on the cause.

As to the other items on your post - I'm going to digest them tonight and come back. Doing the Boot Info Script will be first. I'll do that in a single post. As for the rest, well all this is adding to my knowledge base. As to Grub2 I did some searching and it seems my problem is well known, and the developers haven't come up with a revision as yet.

Thanks for your time in helping me - I'm not frustrated, merely not wanting to take you away from other duties in the forum. I'll stick it as long as you're willing to help. Regards

---

### Post by corowakid on 2010-05-17
OK here's the Results.txt file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #9 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 245762433.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb10: _________________________________________________________________________

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

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac2dac2d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,264,254   156,264,192   7 HPFS/NTFS
/dev/sda2         199,238,254   488,392,064   289,153,811   5 Extended
/dev/sda5         245,762,433   488,392,064   242,629,632   b W95 FAT32
/dev/sda6         199,238,256   243,738,179    44,499,924   b W95 FAT32
/dev/sda7         243,738,243   245,762,369     2,024,127  82 Linux swap / Solaris
/dev/sda3         156,264,255   199,238,129    42,973,875  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00035d98

Partition  Boot         Start           End          Size  Id System

/dev/sdb2              16,126   976,768,064   976,751,939   5 Extended
/dev/sdb5              16,128   131,918,200   131,902,073   7 HPFS/NTFS
/dev/sdb6         251,690,418   503,364,644   251,674,227   7 HPFS/NTFS
/dev/sdb7         503,364,708   755,038,934   251,674,227   7 HPFS/NTFS
/dev/sdb8         755,038,998   976,768,064   221,729,067   7 HPFS/NTFS
/dev/sdb9         131,919,872   246,708,223   114,788,352  83 Linux
/dev/sdb10        246,710,272   251,688,959     4,978,688  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.1 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    31,588,351    31,588,289   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8C28275928274216                       ntfs                                     
/dev/sda3        ee1276be-9160-47e5-a140-5855fcd72509   ext3                                     
/dev/sda5        4705-4B9F                              vfat                                     
/dev/sda6        2A3A-26FA                              vfat                                     
/dev/sda7        4024aec8-9244-1bbc-5af6-5a40efb0f1cb   swap                                     
/dev/sdb10       c1c78101-f014-4a87-8de1-1755a4792586   swap                                     
/dev/sdb5        82FCB95CA400CF59                       ntfs       Disk1                         
/dev/sdb6        4E200D9A200D89E3                       ntfs       Disk2                         
/dev/sdb7        8D4F841F908BAD4B                       ntfs       Disk3                         
/dev/sdb8        9AAEED314D80369A                       ntfs       Disk4                         
/dev/sdb9        07162612-383e-4afe-bc01-ad3cfe04bc44   ext4                                     
/dev/sdc1        70FD-0AEB                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb9        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5        /media/Disk1             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb8        /media/Disk4             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb7        /media/Disk3             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6        /media/Disk2             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/disk-1            vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ee1276be-9160-47e5-a140-5855fcd72509

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee1276be-9160-47e5-a140-5855fcd72509 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		ee1276be-9160-47e5-a140-5855fcd72509
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ee1276be-9160-47e5-a140-5855fcd72509 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2A3A-26FA  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=4024aec8-9244-1bbc-5af6-5a40efb0f1cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  95.9GB: boot/grub/menu.lst
  95.8GB: boot/grub/stage2
  95.5GB: boot/initrd.img-2.6.31-14-generic
  95.5GB: boot/initrd.img-2.6.31-19-generic
  95.5GB: boot/initrd.img-2.6.31-20-generic
  95.5GB: boot/initrd.img-2.6.31-21-generic
  95.5GB: boot/vmlinuz-2.6.31-14-generic
  95.5GB: boot/vmlinuz-2.6.31-19-generic
  95.5GB: boot/vmlinuz-2.6.31-20-generic
  95.5GB: boot/vmlinuz-2.6.31-21-generic
  95.5GB: initrd.img
  95.5GB: initrd.img.old
  95.5GB: vmlinuz
  95.5GB: vmlinuz.old

=========================== sdb9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
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
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set 07162612-383e-4afe-bc01-ad3cfe04bc44
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c28275928274216
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=07162612-383e-4afe-bc01-ad3cfe04bc44 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=c1c78101-f014-4a87-8de1-1755a4792586 none            swap    sw              0       0

=================== sdb9: Location of files loaded by Grub: ===================


  76.2GB: boot/grub/core.img
  97.7GB: boot/grub/grub.cfg
  76.1GB: boot/grub/stage2
  76.2GB: boot/initrd.img-2.6.32-21-generic
  76.2GB: boot/vmlinuz-2.6.32-21-generic
  76.2GB: initrd.img
  76.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1b 1c 1d 1e 1f 20 21 22  23 24 25 26 27 28 29 2a  |..... !"#$%&'()*|
00000010  2b 2c 2d 2e 2f 30 31 32  33 34 35 36 37 38 39 3a  |+,-./0123456789:|
00000020  3b 3c 3d 3e 3f 40 41 42  43 44 45 46 47 48 49 4a  |;<=>?@ABCDEFGHIJ|
00000030  4b 4c 4d 4e 4f 50 51 52  53 54 55 56 57 58 59 5a  |KLMNOPQRSTUVWXYZ|
00000040  5b 5c 5d 5e 5f 60 61 62  63 64 65 66 67 68 69 6a  |[\]^_`abcdefghij|
00000050  6b 6c 6d 6e 6f 70 71 72  73 74 75 76 77 78 79 7a  |klmnopqrstuvwxyz|
00000060  7b 7c 7d 7e 7f 80 81 82  83 84 85 86 87 88 89 8a  |{|}~............|
00000070  8b 8c 8d 8e 8f 90 91 92  93 94 95 96 97 98 99 9a  |................|
00000080  9b 9c 9d 9e 9f a0 a1 a2  a3 a4 a5 a6 a7 a8 a9 aa  |................|
00000090  ab ac ad ae af b0 b1 b2  b3 b4 b5 b6 b7 b8 b9 ba  |................|
000000a0  bb bc bd be bf c0 c1 c2  c3 c4 c5 c6 c7 c8 c9 ca  |................|
000000b0  cb cc cd ce cf d0 d1 d2  d3 d4 d5 d6 d7 d8 d9 da  |................|
000000c0  db dc dd de df e0 e1 e2  e3 e4 e5 e6 e7 e8 e9 ea  |................|
000000d0  eb ec ed ee ef f0 f1 f2  f3 f4 f5 f6 f7 f8 f9 fa  |................|
000000e0  fb fc fd fe ff 00 01 02  03 04 05 06 07 08 09 0a  |................|
000000f0  0b 0c 0d 0e 0f 10 11 12  13 14 15 16 17 18 19 1a  |................|
00000100  1b 1c 1d 1e 1f 20 21 22  23 24 25 26 27 28 29 2a  |..... !"#$%&'()*|
00000110  2b 2c 2d 2e 2f 30 31 32  33 34 35 36 37 38 39 3a  |+,-./0123456789:|
00000120  3b 3c 3d 3e 3f 40 41 42  43 44 45 46 47 48 49 4a  |;<=>?@ABCDEFGHIJ|
00000130  4b 4c 4d 4e 4f 50 51 52  53 54 55 56 57 58 59 5a  |KLMNOPQRSTUVWXYZ|
00000140  5b 5c 5d 5e 5f 60 61 62  63 64 65 66 67 68 69 6a  |[\]^_`abcdefghij|
00000150  6b 6c 6d 6e 6f 70 71 72  73 74 75 76 77 78 79 7a  |klmnopqrstuvwxyz|
00000160  7b 7c 7d 7e 7f 80 81 82  83 84 85 86 87 88 89 8a  |{|}~............|
00000170  8b 8c 8d 8e 8f 90 91 92  93 94 95 96 97 98 99 9a  |................|
00000180  9b 9c 9d 9e 9f a0 a1 a2  a3 a4 a5 a6 a7 a8 a9 aa  |................|
00000190  ab ac ad ae af b0 b1 b2  b3 b4 b5 b6 b7 b8 b9 ba  |................|
000001a0  bb bc bd be bf c0 c1 c2  c3 c4 c5 c6 c7 c8 c9 ca  |................|
000001b0  cb cc cd ce cf d0 d1 d2  d3 d4 d5 d6 d7 d8 00 fe  |................|
000001c0  ff ff 0b fe ff ff 13 e7  c5 02 00 3c 76 0e 00 fe  |...........<v...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 d5 03 a7 02 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  64 65 20 63 6c 61 73 73  3d 22 66 69 6c 65 6e 61  |de class="filena|
00000010  6d 65 22 3e 2f 65 74 63  2f 6d 61 69 6c 2f 73 65  |me">/etc/mail/se|
00000020  6e 64 6d 61 69 6c 2e 6d  63 3c 2f 63 6f 64 65 3e  |ndmail.mc</code>|
00000030  20 61 6e 64 20 63 68 61  6e 67 65 20 74 68 65 0a  | and change the.|
00000040  20 20 20 20 20 20 3c 63  6f 64 65 20 63 6c 61 73  |      <code clas|
00000050  73 3d 22 6f 70 74 69 6f  6e 22 3e 44 41 45 4d 4f  |s="option">DAEMO|
00000060  4e 5f 4f 50 54 49 4f 4e  53 3c 2f 63 6f 64 65 3e  |N_OPTIONS</code>|
00000070  20 6c 69 6e 65 20 74 6f  20 61 6c 73 6f 20 6c 69  | line to also li|
00000080  73 74 65 6e 20 6f 6e 20  6e 65 74 77 6f 72 6b 0a  |sten on network.|
00000090  20 20 20 20 20 20 64 65  76 69 63 65 73 2c 20 6f  |      devices, o|
000000a0  72 20 63 6f 6d 6d 65 6e  74 20 6f 75 74 20 74 68  |r comment out th|
000000b0  69 73 20 6f 70 74 69 6f  6e 20 65 6e 74 69 72 65  |is option entire|
000000c0  6c 79 20 75 73 69 6e 67  20 74 68 65 0a 20 20 20  |ly using the.   |
000000d0  20 20 20 3c 63 6f 64 65  20 63 6c 61 73 73 3d 22  |   <code class="|
000000e0  6c 69 74 65 72 61 6c 22  3e 64 6e 6c 3c 2f 63 6f  |literal">dnl</co|
000000f0  64 65 3e 20 63 6f 6d 6d  65 6e 74 20 64 65 6c 69  |de> comment deli|
00000100  6d 69 74 65 72 2e 20 54  68 65 6e 20 69 6e 73 74  |miter. Then inst|
00000110  61 6c 6c 20 74 68 65 0a  20 20 20 20 20 20 3c 73  |all the.      <s|
00000120  70 61 6e 20 63 6c 61 73  73 3d 22 70 61 63 6b 61  |pan class="packa|
00000130  67 65 22 3e 73 65 6e 64  6d 61 69 6c 2d 63 66 3c  |ge">sendmail-cf<|
00000140  2f 73 70 61 6e 3e 20 70  61 63 6b 61 67 65 20 61  |/span> package a|
00000150  6e 64 20 72 65 67 65 6e  65 72 61 74 65 0a 20 20  |nd regenerate.  |
00000160  20 20 20 20 3c 63 6f 64  65 20 63 6c 61 73 73 3d  |    <code class=|
00000170  22 66 69 6c 65 6e 61 6d  65 22 3e 2f 65 74 63 2f  |"filename">/etc/|
00000180  6d 61 69 6c 2f 73 65 6e  64 6d 61 69 6c 2e 63 66  |mail/sendmail.cf|
00000190  3c 2f 63 6f 64 65 3e 20  62 79 20 72 75 6e 6e 69  |</code> by runni|
000001a0  6e 67 20 74 68 65 0a 20  20 20 20 20 20 66 6f 6c  |ng the.      fol|
000001b0  6c 6f 77 69 6e 67 20 63  6f 6d 6d 61 6e 64 00 01  |lowing command..|
000001c0  01 01 07 fe ff ff 02 00  00 00 79 aa dc 07 00 fe  |..........y.....|
000001d0  ff ff 05 fe ff ff 75 3e  00 0f b2 3e 00 0f 00 00  |......u>...>....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

As before, I'm lost in all this - hopefully it will mean something to you.

---

### Post by corowakid on 2010-05-17
Apologies for not including this in the post above.

I did have the Grub loader, and it did allow me to boot into Windows or 9.10. But it not working that way now - I can only bring up the Error message as before. Regards

---

### Post by corowakid on 2010-05-17
Sorry kansasnoob, I really should have put all my actions/outcomes in one post, rather than piecemeal.

I can't see how I can get Gparted shots if I can't boot the computer. How do I do it?

2nd - your post included:

"error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
This error is the result of a failure of the GRUB 2 search function. There are various bugs associated with the search function. To boot into your system, highlight the OS you want to boot. Press "e" to edit the menuentry. Delete the entire "search ..." line, then CTRL-x to boot.

Once you have booted into the system, you will modify the /usr/lib/grub/grub-mkconfig_lib file in accordance with this link:"

I can't see any option to highlight an OS, all I get on the screen is the Error message I showed in my earlier post. I can't boot into any OS as it stands.

erhaps you can explain it to me?

---

### Post by oldfred on 2010-05-17
Actuallly you should always use the liveCD or download and use a gparted liveCd for all editing of partitions. All partitions have to be unmounted to edit. Within Ubuntu installs gparted is not normally included for that reason. But I like to download it just to review partition. They have improved disk utility so it does show more.

The Second is when you get to the grub menu on booting you can choose your boot line and then edit the commands it uses to boot. At that screen it shows the commands you can use, e gets you into the edit mode.

---

### Post by kansasnoob on 2010-05-17
Well, first I can see that you can't boot the internal again, huh? You did end up with grub2 back on /dev/sda :(

>  => **[COLOR="Red"]Grub 2 is installed in the MBR of /dev/sda[/COLOR]** and looks on the same drive in 
    partition #9 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #9 for /boot/grub.

I also realize it says, "and looks on the same drive in partition #9 for /boot/grub" but that's a flaw in the Boot Info Script. I have discussed that with the author of the script and it's just a tough bug to crack.

What you need is Karmic's legacy grub on sda, and Lucid's grub2 on sdb. You're half way there, as Lucid's grub2 is now on the mbr of sdb :)

Now let's put Karmic's legacy grub back on the mbr of sda. Since you have a 9.04 Live CD you can just boot it, go to terminal, and run:

NOTE: this will NOT work with a 9.10 or 10.04 CD!

```
sudo grub
```

```
find /boot/grub/stage1
```

That should show (hd0,2) so then:

```
root (hd0,2)
```

```
setup (hd0)
```

Wait for that to say done, then:

```
quit
```

Now you should be able to boot Karmic and XP again with the external drive unplugged.

Now, just to recap a couple of things. Your BIOS must be set to boot the USB drive before the internal drive to be able to boot the USB drive. Have you checked that? Do you know how?

I usually have mine set to boot CD first, USB second, and Hard drive third. Once in a while I have to change it to boot USB first, CD second, then Hard Drive depending on what I'm doing.

In my next post I'll try to better explain how to edit the externals grub2 boot to try and get past that error. Or do you even still want to try and get Lucid booting on the external?

---

### Post by kansasnoob on 2010-05-17
Oh, and just because the graphics/display is working well in the 9.04 Live Desktop is no indication that it will be in the Karmic Desktop once you get it booting again.

Some graphics problems I understand a bit (VIA and Intel) but others I know nothing about :(

I also had an idea about getting Lucid to boot on the external. It may be a dumb idea :(

Since there is no primary partition on the external it may help to set a "boot flag" on sdb9. You can see below (highlighted in red) that there is a boot flag on the Windows partition:

```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac2dac2d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    **[COLOR="Red"]*[/COLOR]**             63   156,264,254   156,264,192   7 HPFS/NTFS
/dev/sda2         199,238,254   488,392,064   289,153,811   5 Extended
/dev/sda5         245,762,433   488,392,064   242,629,632   b W95 FAT32
/dev/sda6         199,238,256   243,738,179    44,499,924   b W95 FAT32
/dev/sda7         243,738,243   245,762,369     2,024,127  82 Linux swap / Solaris
/dev/sda3         156,264,255   199,238,129    42,973,875  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00035d98

Partition  Boot         Start           End          Size  Id System

/dev/sdb2              16,126   976,768,064   976,751,939   5 Extended
/dev/sdb5              16,128   131,918,200   131,902,073   7 HPFS/NTFS
/dev/sdb6         251,690,418   503,364,644   251,674,227   7 HPFS/NTFS
/dev/sdb7         503,364,708   755,038,934   251,674,227   7 HPFS/NTFS
/dev/sdb8         755,038,998   976,768,064   221,729,067   7 HPFS/NTFS
/dev/sdb9         131,919,872   246,708,223   114,788,352  83 Linux
/dev/sdb10        246,710,272   251,688,959     4,978,688  82 Linux swap / Solaris
```

**Leave that alone, Windows won't boot without it!** But you could also set a "boot flag" on sdb9 using gparted:

[ATTACH]157261[/ATTACH]

Notice there I've clicked on my sdb1 to highlight it, then a right click brings up a menu where I can select "Manage Flags". If you click on that you can then select "Boot". You'll notice in the right hand column that it displays "Flags", and I selected "boot".

That may or may not help, but it won't do any harm.

As oldfred said most work with gparted should be done using the Live CD, but for setting flags, creating labels, and a few other things you can use it from your installed Ubuntu, but it's not installed by default, so to install it either go to Synaptic or from terminal:

```
sudo apt-get install gparted
```

To post screenshots, of course first take them using the tool in Accessories, then click on the paper clip thingy at the top of these reply boxes. A new window will open, click on Browse and navigate to the screenshot location (usually Desktop by default) and you should then see a list of screenshots. Just double click and then on the right hand side of that window you'll see an upload button. One more click on the paper clip thingy will let you attach :)

---

### Post by corowakid on 2010-05-18
> **kansasnoob said:**
> Well, first I can see that you can't boot the internal again, huh? You did end up with grub2 back on /dev/sda :(



I also realize it says, "and looks on the same drive in partition #9 for /boot/grub" but that's a flaw in the Boot Info Script. I have discussed that with the author of the script and it's just a tough bug to crack.

What you need is Karmic's legacy grub on sda, and Lucid's grub2 on sdb. You're half way there, as Lucid's grub2 is now on the mbr of sdb :)

Now let's put Karmic's legacy grub back on the mbr of sda. Since you have a 9.04 Live CD you can just boot it, go to terminal, and run:

NOTE: this will NOT work with a 9.10 or 10.04 CD!

```
sudo grub
```

```
find /boot/grub/stage1
```

That should show (hd0,2) so then:

```
root (hd0,2)
```

```
setup (hd0)
```

Wait for that to say done, then:

```
quit
```

Now you should be able to boot Karmic and XP again with the external drive unplugged.

Now, just to recap a couple of things. Your BIOS must be set to boot the USB drive before the internal drive to be able to boot the USB drive. Have you checked that? Do you know how?

I usually have mine set to boot CD first, USB second, and Hard drive third. Once in a while I have to change it to boot USB first, CD second, then Hard Drive depending on what I'm doing.

In my next post I'll try to better explain how to edit the externals grub2 boot to try and get past that error. Or do you even still want to try and get Lucid booting on the external?

I've done this, and will now re-boot. One thing: the find /boot/grub/stage1 showed (hd0,2) ,but also (hd1,8). Would this mean someting else is incorrect?

Also, I have changed the Boot options to boot in order - USB external Drive, CD-Rom, HDD.

Now I'm off to re-start!

---

### Post by corowakid on 2010-05-18
Well, the good news - Windows and Karmic boot from the Grub 1.5 screen as before.

Here's the screenshots of sda

[ATTACH]157358[/ATTACH]

and sdb

[ATTACH]157359[/ATTACH]

Wow, that's a good learning curve!

I'd like to follow your suggestion of having the latest, and the prior version of Ubuntu on the system. Should I re-bbot with the USB external drive connected and see what goes? Or are there more steps required.

From all this it seems to me that the end is nigh - do you agree?

---

### Post by corowakid on 2010-05-18
> **oldfred said:**
> Actuallly you should always use the liveCD or download and use a gparted liveCd for all editing of partitions. All partitions have to be unmounted to edit. Within Ubuntu installs gparted is not normally included for that reason. But I like to download it just to review partition. They have improved disk utility so it does show more.

The Second is when you get to the grub menu on booting you can choose your boot line and then edit the commands it uses to boot. At that screen it shows the commands you can use, e gets you into the edit mode.

Thanks for that oldfred. I have a gParted Live CD disk, and used this to take the creenshots of sda and sdb. I managed the boot flag using the gParted entry in Karmic, as kansasnoob advised this could be done. So far, so good.

---

### Post by corowakid on 2010-05-19
For kansasnoob. Here's the results for the graphics card:

```
barrie@barrie-linux:~$ lspci | grep VGA
04:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
barrie@barrie-linux:~$ 
```

I'm still getting the normal resolution after a dozen start-ups. Regards

---

