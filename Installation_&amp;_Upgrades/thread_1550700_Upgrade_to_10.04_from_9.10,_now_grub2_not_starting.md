---
title: "Upgrade to 10.04 from 9.10, now grub2 not starting."
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by davemar on 2010-08-11
I've just done an upgrade from 9.10 to 10.04 (64bit) and when I start my machine the grub2 menu doesn't appear and it just reboots. It finishes off the "Verifying DMI" message thing, but after that just reboots.

Am I right in assuming grub2 has got screwed? I've got a dual-boot machine with Windows XP on there too, but I can't imagine that could cause problems.
Grub2 is a mystery to me, I knew where I was with the old grub, but I haven't a clue where to start tackling this one. I can fire up a 9.10 LiveCD and mount the partition where the 10.04 installation lives, but not sure where to start investigating from there?

Cheers, Dave.

---

### Post by Rubi1200 on 2010-08-11
Hi,
since you have the LiveCD, boot the computer and then click on the link at the bottom of my post. 
Follow the instructions there and post the result back here using the # tag to wrap the text.

Also, what graphics card do you have installed?
Check using this:

```
lspci | grep VGA
```
Post the results please.

---

### Post by davemar on 2010-08-11
Thanks for the quick reply, hope there's some clues below. Here's the short output from lspci | grep VGA:

```
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
```

Here's the rather long RESULTS.txt file (I've got a lot of partitions!):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 156264255.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 483840000.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009bd1d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,551,104    19,551,042   c W95 FAT32 (LBA)
/dev/sda2    *     19,551,105    58,637,249    39,086,145   7 HPFS/NTFS
/dev/sda3          58,637,250   312,576,704   253,939,455   5 Extended
/dev/sda5          58,637,313    97,723,394    39,086,082  83 Linux
/dev/sda6          97,723,458   136,809,539    39,086,082  83 Linux
/dev/sda7         136,809,603   175,895,684    39,086,082  83 Linux
/dev/sda8         175,895,748   254,035,844    78,140,097  83 Linux
/dev/sda9         254,035,908   265,763,294    11,727,387  82 Linux swap / Solaris
/dev/sda10        265,763,358   312,576,704    46,813,347  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d6d0d6c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,264,254   156,264,192   c W95 FAT32 (LBA)
/dev/sdb2         156,264,255   312,528,509   156,264,255   c W95 FAT32 (LBA)
/dev/sdb3         312,528,510   976,768,064   664,239,555   5 Extended
/dev/sdb5         312,528,573   507,862,844   195,334,272  83 Linux
/dev/sdb6         507,862,908   703,197,179   195,334,272  83 Linux
/dev/sdb7         703,197,243   839,926,394   136,729,152  83 Linux
/dev/sdb8         839,926,458   976,768,064   136,841,607  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c44df03

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   483,839,999   483,839,937  83 Linux
/dev/sdc2         483,840,000   976,760,063   492,920,064   c W95 FAT32 (LBA)


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System
/dev/sdc1  1,268,076,847,111,864,354148,878,270,369,402,846-1,119,198,576,742,461,507 -
/dev/sdc2               02,537,810,637,961,811,4552,537,810,637,961,811,456 -
/dev/sdc9  4,150,450,982,744,264,6713,229,270,046,746,660,830-921,180,935,997,603,840 -

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       a556c9cc-3030-44a2-bf49-47f1c15a60a9   ext3                                     
/dev/sda1        4835-16C4                              vfat                                     
/dev/sda2        CAA813F5A813DF2F                       ntfs                                     
/dev/sda5        f5a3dd20-b25d-4a95-978a-14b6a6fedb53   ext3                                     
/dev/sda6        235877d7-717d-441f-a1ad-9dea86cb9902   ext3                                     
/dev/sda7        9bfb61b6-b1e9-41c2-8471-c166144d1a38   ext3                                     
/dev/sda8        6c059840-e090-4190-8a7e-4a1e91c9bcc4   ext3                                     
/dev/sda9        b7e0f44e-0ace-4c71-ae5a-b93b779d6029   swap                                     
/dev/sdb1        4839-9D6F                              vfat                                     
/dev/sdb2        4839-9D72                              vfat                                     
/dev/sdb5        2cb4725e-ab32-4950-b8f0-b306df9cf672   ext3                                     
/dev/sdb6        9e0f1b8e-142d-475c-b56c-1ecf712e675d   ext3                                     
/dev/sdb7        fceba13d-483e-4859-9c70-b8c61a5781b5   ext3                                     
/dev/sdb8        7cfeefd1-e97c-4a01-bc4c-930f320e0b9e   ext3                                     
/dev/sdc1        3a1d07e2-a419-45c5-931a-32eb732fb7e6   ext3                                     
/dev/sdc2        19BA-83F4                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Unidentified operating system on drive C."


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		30

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
# kopt=root=UUID=f5a3dd20-b25d-4a95-978a-14b6a6fedb53 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-24-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=f5a3dd20-b25d-4a95-978a-14b6a6fedb53 ro quiet splash 5
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title       Ubuntu 8.04, kernel 2.6.24-24-rt
root        (hd0,4)
kernel      /boot/vmlinuz-2.6.24-24-rt root=UUID=f5a3dd20-b25d-4a95-978a-14b6a6fedb53 ro quiet splash 5
initrd      /boot/initrd.img-2.6.24-24-rt
quiet

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.10
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.31-14-generic root=/dev/sda6 ro quiet splash 5
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Microsoft 98SE
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other linux booting modes:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Failsafe -- openSUSE 10.2 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.18.2-34-default root=/dev/sda6 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd-2.6.18.2-34-default
savedefault
boot

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f5a3dd20-b25d-4a95-978a-14b6a6fedb53 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (framebuffer only)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f5a3dd20-b25d-4a95-978a-14b6a6fedb53 ro vga=884 2
initrd		/boot/initrd.img-2.6.24-17-generic


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=f5a3dd20-b25d-4a95-978a-14b6a6fedb53 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=6c059840-e090-4190-8a7e-4a1e91c9bcc4 /home           ext3    relatime        0       2
# /dev/sda9
UUID=b7e0f44e-0ace-4c71-ae5a-b93b779d6029 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /fat1           vfat    defaults,umask=000        0       0
/dev/sdb2       /fat2           vfat    defaults,umask=000        0       0
/dev/sdb5       /project        ext3    defaults        0       0
/dev/sdb6       /data1          ext3    defaults        0       0
/dev/sdb7       /data2          ext3    defaults        0       0
/dev/sdb8       /data3          ext3    defaults        0       0
pc01:/win1      /mnt/temp       nfs     rsize=8192,wsize=8192,timeo=14,intr              0       0


=================== sda5: Location of files loaded by Grub: ===================


  39.5GB: boot/grub/menu.lst
  39.4GB: boot/grub/stage2
  39.5GB: boot/initrd.img-2.6.24-16-generic
  39.4GB: boot/initrd.img-2.6.24-16-generic.bak
  39.4GB: boot/initrd.img-2.6.24-17-generic
  39.4GB: boot/initrd.img-2.6.24-17-generic.bak
  39.4GB: boot/initrd.img-2.6.24-18-generic
  39.4GB: boot/initrd.img-2.6.24-18-generic.bak
  39.4GB: boot/initrd.img-2.6.24-19-generic
  39.5GB: boot/initrd.img-2.6.24-19-generic.bak
  39.5GB: boot/initrd.img-2.6.24-21-generic
  39.4GB: boot/initrd.img-2.6.24-21-generic.bak
  39.5GB: boot/initrd.img-2.6.24-22-generic
  39.5GB: boot/initrd.img-2.6.24-22-generic.bak
  39.5GB: boot/initrd.img-2.6.24-23-generic
  39.5GB: boot/initrd.img-2.6.24-23-generic.bak
  39.5GB: boot/initrd.img-2.6.24-24-generic
  39.5GB: boot/initrd.img-2.6.24-24-generic.bak
  39.5GB: boot/initrd.img-2.6.24-24-rt
  39.5GB: boot/initrd.img-2.6.24-24-rt.bak
  39.7GB: boot/initrd.img-2.6.24-25-generic
  39.7GB: boot/initrd.img-2.6.24-25-generic.bak
  39.8GB: boot/initrd.img-2.6.24-25-rt
  39.7GB: boot/initrd.img-2.6.24-25-rt.bak
  39.4GB: boot/vmlinuz-2.6.24-16-generic
  39.4GB: boot/vmlinuz-2.6.24-17-generic
  39.4GB: boot/vmlinuz-2.6.24-18-generic
  39.4GB: boot/vmlinuz-2.6.24-19-generic
  39.5GB: boot/vmlinuz-2.6.24-21-generic
  39.5GB: boot/vmlinuz-2.6.24-22-generic
  39.4GB: boot/vmlinuz-2.6.24-23-generic
  39.7GB: boot/vmlinuz-2.6.24-24-generic
  39.5GB: boot/vmlinuz-2.6.24-24-rt
  39.8GB: boot/vmlinuz-2.6.24-25-generic
  39.8GB: boot/vmlinuz-2.6.24-25-rt
  39.8GB: initrd.img
  39.7GB: initrd.img.old
  39.8GB: vmlinuz
  39.8GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod uhci
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
if terminal_input usb_keyboard ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal usb_keyboard
fi
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=235877d7-717d-441f-a1ad-9dea86cb9902 ro   nomodeset
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=235877d7-717d-441f-a1ad-9dea86cb9902 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=235877d7-717d-441f-a1ad-9dea86cb9902 ro   nomodeset
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	echo	'Loading Linux 2.6.31-16-generic ...'
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=235877d7-717d-441f-a1ad-9dea86cb9902 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	linux	/boot/vmlinuz-2.6.31-11-rt root=UUID=235877d7-717d-441f-a1ad-9dea86cb9902 ro   nomodeset
	initrd	/boot/initrd.img-2.6.31-11-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	echo	'Loading Linux 2.6.31-11-rt ...'
	linux	/boot/vmlinuz-2.6.31-11-rt root=UUID=235877d7-717d-441f-a1ad-9dea86cb9902 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-11-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 235877d7-717d-441f-a1ad-9dea86cb9902
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4835-16c4
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set caa813f5a813df2f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=235877d7-717d-441f-a1ad-9dea86cb9902 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=6c059840-e090-4190-8a7e-4a1e91c9bcc4 /home           ext3    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=b7e0f44e-0ace-4c71-ae5a-b93b779d6029 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /fat1           vfat    defaults,umask=000        0       0
/dev/sdb2       /fat2           vfat    defaults,umask=000        0       0
/dev/sdb5       /project        ext3    defaults        0       0
/dev/sdb6       /data1          ext3    defaults        0       0
/dev/sdb7       /data2          ext3    defaults        0       0
/dev/sdb8       /data3          ext3    defaults        0       0
/dev/sdc1       /big_e          ext3    defaults        0       0
/dev/sdc2       /big_f          vfat    defaults,umask=000        0       0

=================== sda6: Location of files loaded by Grub: ===================


  51.4GB: boot/grub/core.img
  51.4GB: boot/grub/grub.cfg
  51.9GB: boot/initrd.img-2.6.31-11-rt
  51.8GB: boot/initrd.img-2.6.31-16-generic
  52.1GB: boot/initrd.img-2.6.32-24-generic
  51.9GB: boot/vmlinuz-2.6.31-11-rt
  50.4GB: boot/vmlinuz-2.6.31-16-generic
  52.1GB: boot/vmlinuz-2.6.32-24-generic
  52.1GB: initrd.img
  51.9GB: initrd.img.old
  52.1GB: vmlinuz
  51.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  f2 13 f4 bb fc b2 bf da  ff bf a2 98 f2 19 0a 64  |...............d|
00000010  03 40 da 8a 0d 3d 49 51  0e 91 27 8e 03 40 da 8c  |.@...=IQ..'..@..|
00000020  00 00 00 04 b2 74 62 96  ff bf a2 8c 04 8c b7 99  |.....tb.........|
00000030  b2 74 5e ea fb af 45 d1  00 5b a0 05 b2 74 20 9f  |.t^...E..[...t .|
00000040  00 0b 07 03 a8 4d 40 d9  00 00 00 02 88 b2 93 8d  |.....M@.........|
00000050  a8 4d 40 db 77 4e 75 74  00 0b 45 02 57 b2 fd 21  |.M@.wNut..E.W..!|
00000060  00 00 00 00 00 b1 cc ee  00 03 5a f0 00 00 00 00  |..........Z.....|
00000070  00 95 03 10 00 00 fc 00  00 b1 cc ef 00 b1 cc ef  |................|
00000080  00 01 13 98 1e dd c7 ad  00 56 9e a4 cd 1d cf d9  |.........V......|
00000090  e0 33 82 88 98 e1 d7 cf  d3 c0 08 c9 4b 24 03 2a  |.3..........K$.*|
000000a0  ff 20 06 58 ff bf a4 20  ff 98 4f 7c cb aa ac f4  |. .X... ..O|....|
000000b0  ff 98 4e 8c cb 92 3f e8  00 56 97 48 00 00 06 7f  |..N...?..V.H....|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 01  |................|
000000d0  00 24 cf ff 00 00 fc 00  00 00 00 00 00 00 00 00  |.$..............|
000000e0  00 00 00 00 00 00 00 01  00 56 9b 80 00 00 00 00  |.........V......|
000000f0  fe ee 40 0c 00 00 00 00  00 00 00 00 00 00 00 00  |..@.............|
00000100  00 01 2e 1c ff 3a 20 00  ff bf a3 50 fe ee 2f 34  |.....: ....P../4|
00000110  ff 20 06 58 00 00 00 0f  ff bf a3 60 ff 1b 6c 24  |. .X.......`..l$|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 01  |................|
00000130  00 24 cf ff 00 00 fc 00  00 00 00 10 00 00 00 00  |.$..............|
00000140  00 00 00 00 00 00 00 00  00 00 00 01 00 5b a6 08  |.............[..|
00000150  00 00 00 0f 00 00 00 00  00 00 00 00 ff 3a 20 00  |.............: .|
00000160  00 00 00 10 00 00 00 00  ff bf a3 b0 fe ee 31 34  |..............14|
00000170  ff 2d 40 00 00 00 00 00  ff bf a3 c0 fe ee 32 10  |.-@...........2.|
00000180  ff 30 05 48 0f 6e fb 65  00 00 00 42 ff 30 04 78  |.0.H.n.e...B.0.x|
00000190  00 24 cf ff 00 00 fc 00  00 00 00 10 ff 2d 42 ec  |.$...........-B.|
000001a0  00 24 cf ff 00 00 ff 00  00 00 00 03 00 00 df 03  |.$..............|
000001b0  03 df 44 3c df cf 24 00  03 df 44 3c 00 03 00 01  |..D<..$...D<....|
000001c0  01 00 83 ff ff ff 3f 00  00 00 c1 cf d6 1c 00 ff  |......?.........|
000001d0  ff ff 0c ff ff ff 00 d0  d6 1c 00 5d 61 1d 00 00  |...........]a...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown GPT Partiton Type
cebabdd1d10b6dd499a608002d4e2f76
Unknown GPT Partiton Type
000123ddf0b3751c000005742f2f5da1
Unknown GPT Partiton Type
366ca0d1d10b6dd599a608002d4e2f77

```

---

### Post by davemar on 2010-08-22
I changed  /etc/defaults/grub so it looked like this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

GRUB_PRELOAD_MODULES=uhci
#GRUB_TERMINAL_INPUT=at_keyboard
GRUB_TERMINAL_INPUT=usb_keyboard 
```

So it now displays the menu, but now the keyboard is disabled, so I can't select any other OS apart from the first one. It does now boot from there though. Another oddity is that the 10s countdown doesn't start for about 20 seconds.

---

### Post by oldfred on 2010-08-22
Often the keyboard issue in grub is a BIOS setting. It turns out that up until now windows & grub ignored a BIOS setting for USB keyboard and mouse. Now they are using it and because you said in BIOS you have ps/2 keyboard it does not work. Check your BIOS settings.

---

### Post by srs5694 on 2010-08-23
Much snippage in the below quote....

> **davemar said:**
> ```
Drive: sdc ___________________ _____________________________________________________
...
GUID Partition Table detected, but does not seem to be used.
...
Unknown GPT Partiton Type
cebabdd1d10b6dd499a608002d4e2f76
Unknown GPT Partiton Type
000123ddf0b3751c000005742f2f5da1
Unknown GPT Partiton Type
366ca0d1d10b6dd599a608002d4e2f77

```

This suggests to me that the disk was once partitioned using the GUID Partition Table (GPT) scheme, perhaps on a Macintosh, and is now being used with the older Master Boot Record (MBR) system. I don't know how GRUB 2 responds to this sort of situation, but it's possible that GRUB 2 is getting confused by the contradictory partition information.

Assuming the MBR data is correct and the GPT data is old, I recommend you get rid of the latter. AFAIK, the simplest way to do this is with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program. Launch it on the affected disk (/dev/sdc), and gdisk should complain that it found a valid MBR and GPT data, and it asks which to use. It doesn't matter which you choose. Type "x" to enter the experts' menu, then type "z" to "zap" (destroy) the GPT data. Answer "y" to the question about proceeding, but *answer "n" to the question about blanking the MBR data.* Repeat: *do not* let the program wipe out your MBR!

After you do this, it's conceivable you'll need to re-install GRUB 2. This should be possible with your Ubuntu install CD/DVD, but I don't recall the exact steps to do it. OTOH, it's conceivable it'll start working as soon as you've removed the confusing GPT data.

---

### Post by oldfred on 2010-08-23
If you have gpt & msdos (MBR) drives:

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by davemar on 2010-08-24
I ran gdisk to clear up the GDT issue on /dev/sdc, and now it only has MBR on there. None of my drives has GDTs on them now. I also checked the BIOS and that was OK as far as I can see with the keyboard set to USB (which I'm using). Even after checking/fixing these things there is still no improvement - no keyboard, and a long delay.

---

### Post by oldfred on 2010-08-24
If you look in system, administration, log file viewer do any show long delays between commands or repeated trying to load something and then timing out? I look at messages & syslog first but check all the others.

---

### Post by davemar on 2010-09-04
The message log (AFAIK) only shows things that are happening after the OS is selected in grub, my problems are before the OS is chosen.

---

### Post by oldfred on 2010-09-04
We had one user who left a CD in and for whatever reason it was running chkdsk on the Cd.

Some have had floppy configured in BIOS but no floppy drive, so system went looking for a while. Also what device is set to boot first. If you have CD, Floppy, USB then hard drive it has to go through all those devices first.

I have a lot of partitions and drives it takes a bit longer for me to boot because of that.

Some have had issues with USB flash drives plugged in. Try removing all removeable devices ( except of course mouse & keyboard)  and see if that makes any difference.

Is your BIOS up to date?

---

