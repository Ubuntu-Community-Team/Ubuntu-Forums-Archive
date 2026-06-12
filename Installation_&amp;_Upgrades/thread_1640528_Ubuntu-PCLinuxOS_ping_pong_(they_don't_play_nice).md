---
title: "Ubuntu-PCLinuxOS ping pong (they don't play nice)"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by spectre2028 on 2010-12-07
My goal is a tri-boot with WinXP on sda1, Ubuntu 10.10 on sda7, PCLinuxOS 2010 on sdb3.

I've been successfully dual-booting XP & Ubuntu for awhile. Now I'd like to add PCLOS for a KDE distro to play with (like it better than straight KUbuntu 10.1). 

Problem is that when I install PCLOS to sdb3, the grub it installs will allow me to boot PCLOS & XP okay, but the Ubuntu entry is screwed up because that only boots to a command prompt.

So I go the other way: Login to the Ubuntu command prompt and do a grub-install to try to correct the entries. I get the old grub options back now that will allow for correct graphical boot for Ubuntu and XP.  But now PCLOS doesn't even show up in the list.  Even running update-grub from within Ubuntu changes nothing.  PCLOS is missing in action.

Back to PCLOS: I boot from the install CD, chroot to the installed system on sdb3, and run the grub install & update commands.  Presto, I can now boot XP & PCLOS, but Ubuntu again defaults to the command prompt login.

This is a fun(?) game, but it's getting old.  I'm guessing there must be a fundamental difference between the way Ubuntu & PCLOS handle grub (different versions maybe) that's causing each of them to screw up the other's booting, but I sure can't figure it out.

Any takers?

---

### Post by oldfred on 2010-12-08
Since you have two drives you can put Ubuntu's grub in sda's MBR and  PCLinuxOS 2010's grub in sdb. Then you can chainboot from one to the other or use BIOS to choose which to boot. 

To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

With Ubuntu it adds links into root that allow you to directly boot a partition without knowing the kernel versions.

Example from Ranch Hand
Note that this does not define the kernel. It defines the partition. It boots the newest boatable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

If you boot sdb it becomes hd0, I boot sdc and then sda is hd1. So this was my chainload entry.

menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

---

### Post by spectre2028 on 2010-12-08
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 543282 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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
                       sda5 starts at sector 56258560.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 148537344.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb5 starts at sector 40965813.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb6 starts at sector 337927338.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  PCLinuxOS release 2010 
                       (PCLinuxOS) for i586 Kernel 2.6.33.7-pclos6.bfs on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    56,256,511    56,256,449   c W95 FAT32 (LBA)
/dev/sda2          56,258,558   312,580,095   256,321,538   f W95 Ext d (LBA)
/dev/sda5          56,258,560   148,535,295    92,276,736   b W95 FAT32
/dev/sda6         148,537,344   240,730,111    92,192,768   b W95 FAT32
/dev/sda7         240,732,160   260,261,887    19,529,728  83 Linux
/dev/sda8         260,263,936   262,215,679     1,951,744  82 Linux swap / Solaris
/dev/sda9         262,217,728   312,580,095    50,362,368  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     1,026,047     1,024,000  82 Linux swap / Solaris
/dev/sdb2          40,965,811   625,137,344   584,171,534   f W95 Ext d (LBA)
/dev/sdb5          40,965,813   337,927,274   296,961,462   b W95 FAT32
/dev/sdb6         337,927,338   625,137,344   287,210,007   b W95 FAT32
/dev/sdb3           1,026,048    40,964,095    39,938,048  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DC8C-1748                              vfat                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2BB4-1849                              vfat                                     
/dev/sda6        31FC-232B                              vfat                                     
/dev/sda7        28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a   ext4                                     
/dev/sda8        f7abe27e-ee5d-49eb-8392-9c38122b2bb0   swap                                     
/dev/sda9        73fde642-0331-4ac2-9973-1349087b9371   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4f92001e-6772-4d03-aa49-dc56d6a124a2   swap                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        a5bbc837-87a5-49fb-aea7-4004012cb6a1   reiserfs                                 
/dev/sdb5        2AB6-C1F3                              vfat                                     
/dev/sdb6        2F5C-A92C                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda9        /home                    ext4       (rw,commit=0)
/dev/sda5        /media/2BB4-1849___      vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb5        /media/2AB6-C1F3_        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /noguiboot /bootlog

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a

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

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-19-generic
uuid		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/vmlinuz-2.6.35-19-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro quiet splash 
initrd		/boot/initrd.img-2.6.35-19-generic

title		Ubuntu 10.10, kernel 2.6.35-19-generic (recovery mode)
uuid		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/vmlinuz-2.6.35-19-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro  single
initrd		/boot/initrd.img-2.6.35-19-generic

title		Chainload into GRUB 2
root		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
kernel		/boot/memtest86+.bin

title		PCLinuxOS 2010
root (hd1,2)
chainloader +1

	

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	echo	'Loading Linux 2.6.35-19-generic ...'
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dc8c-1748
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "linux (on /dev/sdb3)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set a5bbc837-87a5-49fb-aea7-4004012cb6a1
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=a5bbc837-87a5-49fb-aea7-4004012cb6a1 splash=silent vga=788
	initrd (hd1,2)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb3)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set a5bbc837-87a5-49fb-aea7-4004012cb6a1
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=a5bbc837-87a5-49fb-aea7-4004012cb6a1
	initrd (hd1,2)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb3)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set a5bbc837-87a5-49fb-aea7-4004012cb6a1
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=a5bbc837-87a5-49fb-aea7-4004012cb6a1 failsafe
	initrd (hd1,2)/boot/initrd.img
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=73fde642-0331-4ac2-9973-1349087b9371 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=f7abe27e-ee5d-49eb-8392-9c38122b2bb0 none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=4f92001e-6772-4d03-aa49-dc56d6a124a2 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 125.9GB: boot/grub/core.img
 132.2GB: boot/grub/grub.cfg
 132.2GB: boot/grub/menu.lst
 124.3GB: boot/initrd.img-2.6.35-19-generic
 125.0GB: boot/initrd.img-2.6.35-22-generic
 125.0GB: boot/initrd.img-2.6.35-23-generic
 125.5GB: boot/vmlinuz-2.6.35-19-generic
 126.0GB: boot/vmlinuz-2.6.35-22-generic
 126.0GB: boot/vmlinuz-2.6.35-23-generic
 125.0GB: initrd.img
 125.0GB: initrd.img.old
 126.0GB: vmlinuz
 126.0GB: vmlinuz.old

=========================== sdb3/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,2)/boot/gfxmenu
default 0

title linux
kernel (hd1,2)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=a5bbc837-87a5-49fb-aea7-4004012cb6a1 splash=silent vga=788
initrd (hd1,2)/boot/initrd.img

title linux-nonfb
kernel (hd1,2)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=a5bbc837-87a5-49fb-aea7-4004012cb6a1 
initrd (hd1,2)/boot/initrd.img

title failsafe
kernel (hd1,2)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=a5bbc837-87a5-49fb-aea7-4004012cb6a1 failsafe
initrd (hd1,2)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title		Ubuntu 10.10 (10.10) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.35-19-generic root=/dev/sda7 
initrd		/boot/initrd.img-2.6.35-19-generic
savedefault
boot


# This is a divider, added to separate the menu items below from the PCLINUXOS standard grub entries
title		Other operating systems:


# This entry automatically added by the PCLinuxOS redo-mbr for an existing
# linux installation on /dev/sda7.
title		Ubuntu 10.10 (10.10) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.35-19-generic root=/dev/sda7 
initrd		/boot/initrd.img-2.6.35-19-generic
savedefault
boot


=============================== sdb3/etc/fstab: ===============================

# Entry for /dev/sdb3 :
UUID=a5bbc837-87a5-49fb-aea7-4004012cb6a1 / reiserfs defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda8 :
UUID=f7abe27e-ee5d-49eb-8392-9c38122b2bb0 swap swap defaults 0 0
# Entry for /dev/sdb1 :
UUID=4f92001e-6772-4d03-aa49-dc56d6a124a2 swap swap defaults 0 0
none /dev/pts devpts defaults 0 0

=================== sdb3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/initrd-2.6.33.7-pclos6.bfs.img
    ??GB: boot/initrd.img
    ??GB: boot/vmlinuz
    ??GB: boot/vmlinuz-2.6.33.7-pclos6.bfs
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  29 4a f6 a1 2d 1a dd 69  29 6e 18 39 a3 61 4c 31  |)J..-..i)n.9.aL1|
00000010  8d d2 78 33 ac 35 87 99  31 c7 0e 0e 0c 0f 0c df  |..x3.5..1.......|
00000020  00 c0 53 55 10 51 2e 6c  a2 66 02 83 9d 4a 18 d5  |..SU.Q.l.f...J..|
00000030  d0 90 ea c0 ff c1 eb 2a  34 e6 10 81 1f 26 46 d4  |.......*4....&F.|
00000040  3b 23 63 8a 41 4e a8 4f  b9 d1 67 30 94 10 53 0f  |;#c.AN.O..g0..S.|
00000050  26 d0 e4 25 20 82 b0 2b  81 81 0d 01 94 87 75 05  |&..% ..+......u.|
00000060  81 17 23 24 98 81 c6 04  13 e9 69 5d 4a 26 f4 ab  |..#$......i]J&..|
00000070  80 71 64 90 3e ef cf c3  7a 75 37 e8 71 84 dd 32  |.qd.>...zu7.q..2|
00000080  6d 18 00 41 10 19 e4 ec  87 3e d2 df 8c 67 c3 30  |m..A.....>...g.0|
00000090  08 44 6f 2f c5 df 4c 99  74 c1 9d 8b 9a 51 f9 c2  |.Do/..L.t....Q..|
000000a0  2f bd a5 e8 b2 50 21 02  a3 35 b3 7e 7f 72 cc fb  |/....P!..5.~.r..|
000000b0  a8 10 20 bb b2 60 f7 e6  8f e4 32 5c 9a 7d 21 b2  |.. ..`....2\.}!.|
000000c0  48 88 84 d2 25 cf 68 2b  32 e1 59 46 20 0e d4 d9  |H...%.h+2.YF ...|
000000d0  f6 97 58 7e a1 33 b4 32  f3 a9 b6 1a 03 81 90 00  |..X~.3.2........|
000000e0  22 23 40 82 8b b9 82 65  3c 98 65 b2 14 d8 8b 4b  |"#@....e<.e....K|
000000f0  13 74 49 90 d5 19 8f 23  44 da b4 44 4d bb 3d 2a  |.tI....#D..DM.=*|
00000100  15 65 48 82 82 80 4e 5f  2d 48 c0 10 7f 88 51 26  |.eH...N_-H....Q&|
00000110  47 4b fe 67 fe e7 04 84  91 57 ff d7 f2 8e 67 f1  |GK.g.....W....g.|
00000120  3c 68 90 95 05 1a 45 79  87 6e 92 dd d2 ca 0a 8c  |<h....Ey.n......|
00000130  82 43 ff fb 47 52 10 af  a5 bf 6a 4d ab 23 b9 12  |.C..GR....jM.#..|
00000140  38 6e 57 da 48 b1 21 55  fb 57 bf e9 8b a5 d1 d4  |8nW.H.!U.W......|
00000150  c5 36 28 51 d6 5b d4 54  00 91 4e 44 ff 2b 29 bc  |.6(Q.[.T..ND.+).|
00000160  8a b8 bb f1 78 72 fa 78  ce ee 54 a3 c2 e4 a1 34  |....xr.x..T....4|
00000170  6d 34 42 84 1e 32 1a 14  09 5e 64 83 a1 48 4c 4a  |m4B..2...^d..HLJ|
00000180  46 70 f4 1e 8d 1b 41 5c  8c 72 43 bd c7 b5 2e 82  |Fp....A\.rC.....|
00000190  c4 9c b0 55 3a ac 91 ea  c4 d1 91 ad 24 ce 71 08  |...U:.......$.q.|
000001a0  9d d1 50 63 b9 64 65 8c  5f 7d c0 59 35 2d 93 91  |..Pc.de._}.Y5-..|
000001b0  24 eb 52 77 65 59 c4 14  8b 24 56 91 22 97 00 fe  |$.RweY...$V."...|
000001c0  ff ff 0b fe ff ff 02 00  00 00 00 08 80 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff a0 0e  80 05 62 c1 7e 05 00 00  |..........b.~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by oldfred on 2010-12-09
It looks like Ubuntu's grub2 found XP and PCLinuxOS, so if you boot sda, you can choose anything. You still have a menu.lst from grub legacy, sometimes that confused grub2.

It looks like PCLinuxOS has an Ubuntu entry. I assume you added it as grub legacy was not good at finding other systems. I do not see a XP entry. 

What works? What does not. Have you tried booting both the 160GB & 320GB drives from BIOS?

---

### Post by spectre2028 on 2010-12-09
> **oldfred said:**
> It looks like Ubuntu's grub2 found XP and PCLinuxOS, so if you boot sda, you can choose anything. You still have a menu.lst from grub legacy, sometimes that confused grub2.

It looks like PCLinuxOS has an Ubuntu entry. I assume you added it as grub legacy was not good at finding other systems. I do not see a XP entry. 

What works? What does not. Have you tried booting both the 160GB & 320GB drives from BIOS?

Never tried booting from drive 2, but I should have corrected my initial post.  I was inaccurate when I said that Grub2 allows Ubuntu & XP to boot, but doesn't find PCLOS.  It actually does list PCLOS, but when selected, the boot of PCLOS runs for about a dozen lines, then just stops.  (no obvious errors, just a bunch of technical verbiage that's 'above my pay grade')

Also, before posting the results.txt above, I had gone over to look around on the PCLOS forum for clues.  I found a thread that very specifically said that PCLOS and many other popular distros (e.g. Fedora) use Grub Legacy, but Ubuntu & variants use Grub2, and apparently these two are completely incompatible.  I kind of picked up a vibe that there might be some bad blood between the distros insisting on Grub 2 vs. the other Grub Legacy distros.

Anyway, after finding that out, I booted into Ubuntu and used Synaptic to replace grub2 with grub legacy, thinking that might solve my problems, assuming it was smart enough to see all installed O/S's.  That didn't work either, so I changed back to Grub2, and that may be why you now see a hodgepodge of mixed grub files left behind by trying the two different versions.

---

### Post by oldfred on 2010-12-09
What does not work well is having grub legacy & grub2 installed on the same system. You may want to uninstall both grub & grub2 and cleanly reinstall grub2. Also older versions (before Ubuntu went to ext4 with 9.04) and different distributions of grub legacy (all v.97) will not see a ext4 partition.

If you can boot into Ubuntu you do not have to chroot:
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I have chainloaded from grub legacy to grub2 back when grub2 first came out, so it worked then. I chainload from one drive to the MBR of another drive to boot that without the specific entires otherwise required.

It turns out grub considers the boot drive as drive 0, so numbering with multiple drives can be an issue.

My grub chainload entries where I had all three drives and found depending on which drive I booted the other drives would not always be the same number.
```

title       Ubuntu 9.04 Jaunty 32 bit @ sdb
root        (hd1)
chainloader +1

title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

title       Ubuntu 10.04 Lucid alpha/beta @ sda
root        (hd0)
chainloader +1

```A grub2 entry that should work for you if grub2 is booted from sda or hd0:
```

menuentry "PCLinuxOS on sdb (from sda) Chainboot" {
set root=(hd1)
chainloader +1
}

```

Edit:

Your current entry that the osprober found will probably work with this change. The prober copies entries and when copying from grub legacy the partition number is one less so it is wrong. I have seen this with other systems using old grub also. The hdx,y entry in initrd line is not required after the set root anyway.

initrd (hd1,[COLOR=Red]2[/COLOR])/boot/initrd

The correct entry is :
initrd /boot/initrd

If you copy the osprober's version to 40_custom and edit as above it should work also. I might copy both the chainload and the above edited stanza and test both. (But that is because I like to know what works.)

---

### Post by spectre2028 on 2010-12-09
> **oldfred said:**
> What does not work well is having grub legacy & grub2 installed on the same system. You may want to uninstall both grub & grub2 and cleanly reinstall grub2. Also older versions (before Ubuntu went to ext4 with 9.04) and different distributions of grub legacy (all v.97) will not see a ext4 partition.

If you can boot into Ubuntu you do not have to chroot:
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I have chainloaded from grub legacy to grub2 back when grub2 first came out, so it worked then. I chainload from one drive to the MBR of another drive to boot that without the specific entires otherwise required.

It turns out grub considers the boot drive as drive 0, so numbering with multiple drives can be an issue.

My grub chainload entries where I had all three drives and found depending on which drive I booted the other drives would not always be the same number.
```

title       Ubuntu 9.04 Jaunty 32 bit @ sdb
root        (hd1)
chainloader +1

title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

title       Ubuntu 10.04 Lucid alpha/beta @ sda
root        (hd0)
chainloader +1

```A grub2 entry that should work for you if grub2 is booted from sda or hd0:
```

menuentry "PCLinuxOS on sdb (from sda) Chainboot" {
set root=(hd1)
chainloader +1
}

```

Edit:

Your current entry that the osprober found will probably work with this change. The prober copies entries and when copying from grub legacy the partition number is one less so it is wrong. I have seen this with other systems using old grub also. The hdx,y entry in initrd line is not required after the set root anyway.

initrd (hd1,[COLOR=Red]2[/COLOR])/boot/initrd

The correct entry is :
initrd /boot/initrd

If you copy the osprober's version to 40_custom and edit as above it should work also. I might copy both the chainload and the above edited stanza and test both. (But that is because I like to know what works.)

You're over my head now.  I'll have to do some studying up on GRUB and check out the post you mentioned.  Thanks.

---

### Post by oldfred on 2010-12-09
If you do not know how to edit 40_custom.

Copy the the  entries from this and edit as desired:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

Then do:
sudo update-grub

Reboot to test that entries work. But you will have the old entries from osprober.

Once you know new entries work you can turn off osprober so you do not have the duplicate incorrect entries:
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
Then:
sudo update-grub

---

### Post by spectre2028 on 2010-12-09
The linked post detailing a clean Grub2 install didn't look too hairy, so I might try that tonight.  Would that be better than your option above of editing that one file?  

By the way, when I was going back & forth between grub2 and legacy, it looked pretty much like Ubuntu was uninstalling the current one before installing the other, so there shouldn't be both on the drives at the same time. (unless legacy is still on sdb, from the initial PCLOS install)

---

### Post by oldfred on 2010-12-09
It is really only installing the MBR and does not change the boot loader for PCLOS which is in the MBR of the other drive. The software and settings are still in the Ubuntu partition.

---

### Post by spectre2028 on 2010-12-09
> **oldfred said:**
> It is really only installing the MBR and does not change the boot loader for PCLOS which is in the MBR of the other drive. The software and settings are still in the Ubuntu partition.

Okay, tried these steps, in this order:

1. Boot from sdb: 'Some' kind of grub was found -unbootable, but with a very limited commandline option, useless to me.

2. Perform the procedure in the linked post to uninstall & reinstall grub.  This resulted in exactly the same setup as before - it finds PCLOS but this would not boot (the phrase "kernel panic" was included in the verbiage).

3. Attempt to copy some of the grub.cfg into the 40_custom file, and make changes, per your suggestions.  Apparently I did not understand what alterations to enter into the latter file, as there was no change in ability to boot PCLOS.

4. I came up with the idea to boot with the PCLOS CD, do a chroot, and try to install its version of grub to sdb.  The process seemed to go through okay. Results were not successful: Booting from sdb, Grub gave me the options to boot PCLOS & Windows, but none of them actually worked when I selected them.

5. What I consider the more draconian measure: I did a complete reinstall on PCLOS. When it asked where to put grub, I specified sdb.  I now have more or less what I was looking for, but it's not as 'convenient' as I would have liked: If I boot from sda, I can go into Windows or Ubuntu.  If I boot from sdb, I can go into Windows or PCLOS successfully.  Just have the extra step of going into the BIOS to change boot drives.

---

### Post by ImDougy on 2010-12-09
i had this problem yesterday trying to triple boot ubuntu, opensuse, and mandriva. dual booting opensuse and mandriva will work but ubuntu uses a different version of grub so it won't work with ones that use grub 2 like those and pclos

---

### Post by oldfred on 2010-12-09
If you want to post a new run of the boot script, I can see what you put into 40_custom and what other changes you have now made. 

Or you have to select in BIOS to boot one drive or the other, a few do this intentionally but I think fixing grub is better.

---

### Post by spectre2028 on 2010-12-10
> **oldfred said:**
> If you want to post a new run of the boot script, I can see what you put into 40_custom and what other changes you have now made. 

Or you have to select in BIOS to boot one drive or the other, a few do this intentionally but I think fixing grub is better.
This is what I tried today.  Did different combinations of the set root parameters, to no avail.  This is all that'd added to 40_custom.


menuentry "PCLOS 2010" {

set root=(hd1,3)

chainloader +1

}

---

### Post by oldfred on 2010-12-10
If you have installed PCLOS's grub into the partition boot sector PBR  (in addition or instead of the MBR) then the chainload to a partition will work. Same type of entry works for windows since it has a lot of its boot code in the windows PBR.

---

### Post by spectre2028 on 2010-12-11
> **oldfred said:**
> If you have installed PCLOS's grub into the partition boot sector PBR  (in addition or instead of the MBR) then the chainload to a partition will work. Same type of entry works for windows since it has a lot of its boot code in the windows PBR.
That's the thing - it did not work. On the PCLOS reinstall, I had it install Grub legacy to sdb, so I assume that was in the second drive's boot sector. Put different numbers in the set root line above, trying to "compensate" for the fact that it may or may not start counting from 0.  Nothing worked.  

Thanks for the suggestions to try, but I'm just going to assume that these two cannot be both installed and booted from grub in the same HD.

So the 'solution' to my dilemma is just to install one on sda with Windows, the other on sdb by itself.  Then change booting in the BIOS to get whichever distro I want to run at a give moment.

Or install a Kubuntu alternative on sdb, which will play nice with Ubuntu.

---

### Post by oldfred on 2010-12-11
The chainload entry has to be where you installed grub. If you install it to a drive sda or sdb then the chain entry is (hd1) or (hd2) or possibly (hd0), but the boot drive always seems to be hd0, but drive mapping may change that. I have had to experiment to know for sure.

If you install grub to a partition like sdb4, then you can chainload to (hd1,4) from grub2 or (hd1,3) if from grub.

Note that the boot stanzas are totally different between grub and grub2. Partition numbering has changed grub legacy's hd0,0 is in grub2 hd0,1 and root or rootnoverify is in grub2 set root. So it depends greatly on whether you are adding a boot stanza to a menu.lst or a 40_custom.

---

