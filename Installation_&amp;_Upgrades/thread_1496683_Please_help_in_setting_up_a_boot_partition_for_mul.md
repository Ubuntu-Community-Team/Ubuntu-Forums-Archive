---
title: "Please help in setting up a boot partition for multi boot + Lucid.."
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by killabee44 on 2010-05-29
Hi all,

I am currently running a dual boot setup with XP, and Kubuntu. A friend of mine set up a third operating system (Lucid, as I want to do) and had problems with Ubuntu messing up the grub. 

I would like to set up a three OS grub and have read that a boot partition is the best way to go about it. 

I've successfully set up all the partitions (boot, /, /home, swap) for Lucid on a separate hard drive and am confused as to how to properly set it up to use the boot partition and not messing up the grub.

At a site I read that you need to use the Lucid Server install image instead of the desktop one. 


That's where I'm confused and hopefully someone can shed some light as to the steps to get Lucid desktop set up properly. Or if you know a link to a tutorial I would really appreciate it. I could not find one.

---

### Post by darkod on 2010-05-29
Your friend experience shouldn't put you off so easily. First of all, it depends what actually happened because having a triple boot is no problem for grub2 that comes with Lucid.
Further more, if you already have one version of linux and grub installed, you don't need to install grub from your second linux install at all. Of course, in that case you need to know to edit your existing grub (especially for grub1 because it doesn't detect a new OS automatically like grub2) to add your third, new OS.

Also, using a /boot partition is absolutely not needed, and sometimes it can even lead to confusion. For example, if you set both Kubuntu and Ubuntu to share the same /boot, or different linux distro, you will run into trouble because the files are not always identical.

But having said all that, in your current setup, Kubuntu will not be using that /boot partition so go along and install Lucid with a separate /boot partition if you want to.

The server cd is for server installs and it's not true you have to use it for what you want. You can use the standard desktop cd, or live cd as it is called sometimes.
BUT, because you already have created partitions, you need to select in step 4 Manual Partitioning. Then click on each partition at a time, and the Change button, and set the correct filesystem and mount point that you want to use for that partition (/boot, /, etc).

All of that would be much easier if creating the partitions during the install, now you have to select them one by one and set the mount points anyway. Double work...

In the last screen on the installer, click on the Advanced button, and select where do you want grub2 to be installed, or don't install it at all if you plan to use the grub from Kubuntu that you currently have.
If you install grub2 from Lucid, I recommend installing on a disk MBR, not partition.

---

### Post by killabee44 on 2010-05-29
Ok, I guess I misread some info I found online.

Right now I have XP and Jaunty installed on a different drive using grub1. How would I go about doing this during and after the install? (I would like to install Grub2)

I have done it with the manual partitioning (as in step 4) before so that is no problem.

When you say: 

"I recommend installing on a disk MBR, not partition." 

What exactly do you mean? Do you mean a primary partition? Im not sure where the MBR resides.. Would it be on the partition that contains the C for XP? 

Thanks.

Edit: 

Ok, the MBR is at the beginning of each hard drive...

---

### Post by killabee44 on 2010-05-30
I went ahead with the install. I installed Lucid on the second HD and at the end clicked the advanced button and specified the mbr but selected the one that was going to contain Lucid, not the one that holds Windows and Kubuntu. 

I finished the install and rebooted. Grub1 came up with no option for Lucid. I realize now that I should have selected the MBR on the drive that contained XP and Kubuntu. 

So, now how do I go about fixing this so that I can use Grub2 to pop up with a triple boot option for these OS's?

Here are the results of boot_info_script055.sh from your sig:

    ```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70667066

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   681,846,794   681,846,732   7 HPFS/NTFS
/dev/sda2         681,846,856   976,768,064   294,921,209   f W95 Ext d (LBA)
/dev/sda5         681,846,858   765,818,549    83,971,692   7 HPFS/NTFS
/dev/sda6         765,818,613   804,888,629    39,070,017  83 Linux
/dev/sda7         804,888,693   945,521,639   140,632,947  83 Linux
/dev/sda8         945,521,703   953,329,229     7,807,527  82 Linux swap / Solaris
/dev/sda9         953,329,293   976,768,064    23,438,772   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x043f043e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   781,419,743   781,419,681   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05ec2e83

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    10,442,249    10,442,187  83 Linux
/dev/sdc3          10,442,311   133,323,434   122,881,124   5 Extended
/dev/sdc5          10,442,313    47,311,424    36,869,112  83 Linux
/dev/sdc6          47,311,488   129,226,859    81,915,372  83 Linux
/dev/sdc7         129,226,923   133,323,434     4,096,512  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x127589c5

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4c5d0935

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        5C108B76108B5644                       ntfs                                     
/dev/sda5        041CF2611CF24CE4                       ntfs                                     
/dev/sda6        9ad9b379-56ca-46b7-8b5e-802747ad6f37   ext3                                     
/dev/sda7        5ccf003e-a3ff-449a-b53e-463c8d372f99   ext3                                     
/dev/sda8        a9a028d4-46b3-4302-8886-9fd4073a25ff   swap                                     
/dev/sda9        BC4A-7D67                              vfat                                     
/dev/sdb1        6A2003182002EAC1                       ntfs       DShares                       
/dev/sdc1        7da942e3-c53e-4ae0-9eb2-fce99c412c28   ext3                                     
/dev/sdc5        d9ee156c-73e9-4835-81a0-58e7fd06db46   ext4                                     
/dev/sdc6        70654c20-ab48-4b64-8fe6-ffda45dd7146   ext4                                     
/dev/sdc7        0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1   swap                                     
/dev/sdd1        70B4D348B4D31008                       ntfs       250 Newsleecher               
/dev/sde1        B420A64C20A61600                       ntfs       250 Backup                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda9        /dos                     vfat       (rw,utf8,umask=007,gid=46)
/dev/sda7        /home                    ext3       (rw,relatime)
/dev/sda1        /media/C-Drive           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/D-Drive           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/DShares           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/Newsleecher       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1        /media/250Backup         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=6

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9ad9b379-56ca-46b7-8b5e-802747ad6f37

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

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic


title		Ubuntu 9.04, memtest86+
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=BC4A-7D67  /dos            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=5ccf003e-a3ff-449a-b53e-463c8d372f99 /home ext3    relatime        0       2
# /dev/sda8
UUID=a9a028d4-46b3-4302-8886-9fd4073a25ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#
UUID=5C108B76108B5644 /media/C-Drive ntfs defaults 0 0
#
UUID=041CF2611CF24CE4 /media/D-Drive ntfs defaults 0 0
#
UUID=6A2003182002EAC1 /media/DShares ntfs defaults 0 0
#
UUID=ACC0BC4BC0BC1E10 /media/MiscMovies ntfs defaults 0 0
#
UUID=70B4D348B4D31008 /media/Newsleecher ntfs defaults 0 0
#
UUID=B420A64C20A61600 /media/250Backup ntfs defaults 0 0

music and video 1.5TB
#UUID=2AA91D326971D565 /media/musicandvideo ntfs-3g user,defaults 0 0

#Video 400 
UUID=992ADF057FADABD5 /media/video400 ntfs-3g user,defaults 0 0

=================== sda6: Location of files loaded by Grub: ===================


 395.3GB: boot/grub/menu.lst
 395.4GB: boot/grub/stage2
 395.3GB: boot/initrd.img-2.6.27-14-generic
 395.4GB: boot/initrd.img-2.6.28-11-generic
 395.3GB: boot/initrd.img-2.6.28-12-generic
 395.3GB: boot/initrd.img-2.6.28-13-generic
 395.3GB: boot/initrd.img-2.6.28-14-generic
 395.4GB: boot/initrd.img-2.6.28-15-generic
 395.4GB: boot/initrd.img-2.6.28-16-generic
 395.4GB: boot/initrd.img-2.6.28-17-generic
 395.5GB: boot/initrd.img-2.6.28-18-generic
 395.3GB: boot/vmlinuz-2.6.27-14-generic
 395.3GB: boot/vmlinuz-2.6.28-11-generic
 395.4GB: boot/vmlinuz-2.6.28-12-generic
 395.3GB: boot/vmlinuz-2.6.28-13-generic
 395.4GB: boot/vmlinuz-2.6.28-14-generic
 395.4GB: boot/vmlinuz-2.6.28-15-generic
 395.4GB: boot/vmlinuz-2.6.28-16-generic
 395.4GB: boot/vmlinuz-2.6.28-17-generic
 395.4GB: boot/vmlinuz-2.6.28-18-generic
 395.5GB: initrd.img
 395.4GB: initrd.img.old
 395.4GB: vmlinuz
 395.4GB: vmlinuz.old

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
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
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5c108b76108b5644
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro single
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro single
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 /               ext4    errors=remount-ro 0       1
/dev/sdc6       /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=a9a028d4-46b3-4302-8886-9fd4073a25ff none            swap    sw              0       0
# swap was on /dev/sdc7 during installation
UUID=0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


   7.8GB: boot/grub/core.img
  14.4GB: boot/grub/grub.cfg
   7.8GB: boot/initrd.img-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-21-generic
   7.8GB: initrd.img
   7.7GB: vmlinuz 
```

If I decide to get rid of my Kubuntu install, how would I go about doing that? Im not trying to rush... but it's some info I need for later on. Thanks.

---

### Post by 23dornot23d on 2010-05-30
From what I can see .........

Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

Looking at this and the fact that the grub boot options exist on sbc5


You could just change the boot settings in the bios ......

and boot from your 120 gig drive ...... sdc ........

and your new grub 2 menu should work .....

Its just a case of pressing F2 or F11 at boot time ,,,,

(Check the web for how to change the BIOS too ...... it may save you a lot of messing about)

F2 will let you go into the BIOS and alter the boot sequence usually ..... 
F11 may let you choose your boot device to do a quick check .....

look at your screen as it boots up there is usually a option pops up
( it can go very quickly depending on how quickly your computer boots up )

Each computer is different ,,,,, but I think they have tried to
standardize the key press nowadays for multi boot .....

If it does work you do not need to change anything ..... other than to accept
the boot from sdc in the BIOS and save settings .......

If it does not work just change or let the BIOS .... boot from sda again ,,,, 
the 500 gig drive ,,,, 

( I have seen where you can chainload to another grub too but I have not done this manually
maybe if it does not work - someone else can tell you how to do this ...... )

---

### Post by darkod on 2010-05-30
Yes, you did good. Like the previous poster said, to use your grub2 from Lucid installed in the MBR of /dev/sdc, just make it first in hdd boot order in BIOS. So, that is your 120GB disk.

With that disk as first option, the system will load grub2 from it, and the menu is already created for the triple boot.

Later for removing Kubuntu. If you keep booting from /dev/sdc, simply deleting the Kubuntu partition(s) will not break anything. Then use that space for ntfs partition for windows, or what ever.

That will leave your current grub1 on /dev/sda broken (because the config files from Kubuntu will be gone), but if you keep booting grub2 from /dev/sdc you won't even notice it at first. And it's easy to sort it out later.

After removing it, in Lucid just run:

sudo update-grub

and it will be gone from the boot menu.

---

### Post by killabee44 on 2010-05-30
Ok that did it. Thanks for your help guys. For me, this os has been the smoothest running version of ubuntu yet. Much appreciated.

---

### Post by darkod on 2010-05-30
So nothing was messed up right? And grub2 is just fine for triple booting? ;)

Like I said, don't get put off by other peoples mistakes. You did the right thing and searched for information before hand. And all worked out all right.

---

