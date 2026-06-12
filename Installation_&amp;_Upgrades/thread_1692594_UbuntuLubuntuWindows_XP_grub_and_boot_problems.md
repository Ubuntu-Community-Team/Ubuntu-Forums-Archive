---
title: "Ubuntu/Lubuntu/Windows XP grub and boot problems"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by j.biddy on 2011-02-21
I've had Ubuntu 8.10 and Lubuntu 10.04 running along side each other and recently decided to add an XP partition into the mix. 

I loaded the Windows XP installer from a boot CD and the install appeared to go off without a hitch. When the computer rebooted, I expected to see the Windows boot loader take over (I assumed I would just reinstall grub 2). Instead, I was greeted with what appears to be a grub 1 boot loader. It only sees Ubuntu 8.10  and Windows XP, but XP doesn't load, it gives an Error 13. Each operating system is on a different physical disk. I tried reinstalling grub 2 to the Lubuntu 10.04 disk, but nothing comes up but the old grub with no 10.04 and a bogus XP.

---

### Post by gufide on 2011-02-21
the installation of windows xp did not recognize ubuntu patition. if you erase a "not formatted partition" (for windows xp) windows xp may delete lubuntu 10.04.

for your error, I'm not very good in windows error, sorry

---

### Post by j.biddy on 2011-02-21
I installed it onto a different physical disk than the Lubuntu 10.04 or the Ubuntu 8.10 so I'm certain Windows XP didn't delete Lubuntu or Ubuntu. I am in the Ubuntu 8.10 install right now, as that is the only operating system currently working right now, so at least that OS is fully functioning. 

I assume what I need to do is remove/delete the grub bootloader that is currently dominant (probably the one from Ubuntu 8.10?) and then reinstall the latest grub (grub 2 from lubuntu 10.04) to the lubuntu disk. Presumably grub will autodetect the XP I've loaded onto the system?

---

### Post by j.biddy on 2011-02-22
UPDATE!

I changed the boot order so that the SATA drive (Lubuntu 10.04 install) is the second boot device after the CD device and that brought me back to the grub 2 boot menu so I am back to being able to boot into Lubuntu.

However, Windows XP is unable to boot into the operating system (primary IDE HDD). When I select Windows XP in the boot menu it goes to a dim black screen and hangs.

---

### Post by iAmthatguy on 2011-02-22
I am trying to try Ubuntu 10.10 on my laptop, and i have been going at this all day trying to find help besides asking for it, and i have finally succumbed to this. Right now i have tried using a live CD which i made from the iso file i downloaded off the website, and the Infra Recorder, then i tried booting, i moved the boot order so the cd/dvd drive was at the top. Then it didnt work and booted straight to windows. So i got a new cd and used the same iso file but i made it with iso recorded. The same thing happened with the windows booting. Now what i have down is used the suggested program to put the iso file on a thumb drive and boot from the thumb drive, i have already determinded my computer has this option. And again it booted straight to windows, at the moment the only things i can see that would be the problem would be that the iso file is corrupted in some way, or i need to do more to the thumb drive in order for it to actually be able to be booted from. Any help would be greatly appreciated. Also i am running Windows XP SP3, 32 bit, and i am trying to try out Ubuntu 10.10

---

### Post by j.biddy on 2011-02-22
> **iAmthatguy said:**
> I am trying to try Ubuntu 10.10 on my laptop, and i have been going at this all day trying to find help besides asking for it, and i have finally succumbed to this. Right now i have tried using a live CD which i made from the iso file i downloaded off the website, and the Infra Recorder, then i tried booting, i moved the boot order so the cd/dvd drive was at the top. Then it didnt work and booted straight to windows. So i got a new cd and used the same iso file but i made it with iso recorded. The same thing happened with the windows booting. Now what i have down is used the suggested program to put the iso file on a thumb drive and boot from the thumb drive, i have already determinded my computer has this option. And again it booted straight to windows, at the moment the only things i can see that would be the problem would be that the iso file is corrupted in some way, or i need to do more to the thumb drive in order for it to actually be able to be booted from. Any help would be greatly appreciated. Also i am running Windows XP SP3, 32 bit, and i am trying to try out Ubuntu 10.10

lol Alright, I'll try to help you as best I can. One of the things you can try is burning the ISO at a lower speed (like 4x or maybe 8x). 

Also, it's always good to ask, are you burning the ISO as a bootable image and not just burning the ISO as a file on a data CD? 

Also, for anyone out there looking to help me, upon reviewing posts I found the Boot Info Script so here is some output from that:```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    86,285,114    86,285,052   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    51,568,649    51,568,587  83 Linux
/dev/sdb2          51,568,650   312,576,704   261,008,055   5 Extended
/dev/sdb5          51,568,713    56,709,449     5,140,737  82 Linux swap / Solaris
/dev/sdb6          56,709,513   312,576,704   255,867,192   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    84,919,589    84,919,527   7 HPFS/NTFS
/dev/sdc2          84,920,318   234,440,703   149,520,386   5 Extended
/dev/sdc5          84,920,320   228,429,823   143,509,504  83 Linux
/dev/sdc6         228,431,872   234,440,703     6,008,832  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     7,831,551     7,831,489   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7C90E5FA90E5BAB2                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        93d51bce-1cbe-4aab-943d-8ebb8f2f231d   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0ee6d54f-e154-4c18-abae-6d2cbd8d2932   swap                                     
/dev/sdb6        F070-62CC                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4f802d25-10f5-49ef-9f9b-5b9b7c719d9a   ext4       Empty Space                   
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        16aed4fe-0f3a-4e40-b08a-cfaed54a96e2   ext4                                     
/dev/sdc6        1328172a-9381-4a28-87ee-d5465c7577aa   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        866D-3A99                              vfat       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=93d51bce-1cbe-4aab-943d-8ebb8f2f231d

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

title		Ubuntu 8.10, kernel 2.6.27-17-generic
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode)
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 8.10, kernel 2.6.27-15-generic
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc6 :
UUID=F070-62CC /windows vfat utf8,umask=007,gid=46 0 1
# Entry for /dev/sdc5 :
UUID=0ee6d54f-e154-4c18-abae-6d2cbd8d2932 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults 0 0
/dev/sdc1 /media/sdc1 ext3 defaults 0 0
/dev/sdc5 /media/sdc5 swap defaults 0 0
/dev/sdc6 /media/sdc6 vfat defaults 0 0
/dev/sdd1 /media/sdd1 ntfs-3g defaults 0 0
/dev/sde2 /media/sde2 vfat defaults 0 0

/home/biddy/Shared /export/Shared none bind 0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/menu.lst
    .7GB: boot/grub/stage2
    .6GB: boot/initrd.img-2.6.27-11-generic
    .6GB: boot/initrd.img-2.6.27-14-generic
    .6GB: boot/initrd.img-2.6.27-15-generic
    .6GB: boot/initrd.img-2.6.27-17-generic
    .6GB: boot/initrd.img-2.6.27-7-generic
    .6GB: boot/vmlinuz-2.6.27-11-generic
    .6GB: boot/vmlinuz-2.6.27-14-generic
    .6GB: boot/vmlinuz-2.6.27-15-generic
    .6GB: boot/vmlinuz-2.6.27-17-generic
    .6GB: boot/vmlinuz-2.6.27-7-generic
    .6GB: initrd.img
    .6GB: initrd.img.old
    .6GB: vmlinuz
    .6GB: vmlinuz.old

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 16aed4fe-0f3a-4e40-b08a-cfaed54a96e2
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 16aed4fe-0f3a-4e40-b08a-cfaed54a96e2
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 16aed4fe-0f3a-4e40-b08a-cfaed54a96e2
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=16aed4fe-0f3a-4e40-b08a-cfaed54a96e2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 16aed4fe-0f3a-4e40-b08a-cfaed54a96e2
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=16aed4fe-0f3a-4e40-b08a-cfaed54a96e2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 16aed4fe-0f3a-4e40-b08a-cfaed54a96e2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 16aed4fe-0f3a-4e40-b08a-cfaed54a96e2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 885cec1d5cec0830
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.27-17-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-17-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash
	initrd /boot/initrd.img-2.6.27-17-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-17-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro single
	initrd /boot/initrd.img-2.6.27-17-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro single
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro single
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdc1)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 93d51bce-1cbe-4aab-943d-8ebb8f2f231d
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
# / was on /dev/sda5 during installation
UUID=16aed4fe-0f3a-4e40-b08a-cfaed54a96e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1328172a-9381-4a28-87ee-d5465c7577aa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  65.0GB: boot/grub/core.img
  65.1GB: boot/grub/grub.cfg
  65.1GB: boot/initrd.img-2.6.32-21-generic
  65.1GB: boot/vmlinuz-2.6.32-21-generic
  65.1GB: initrd.img
  65.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  17 f3 79 2d 30 3e 25 3c  7e 3f aa 94 fa 7a 8e e4  |..y-0>%<~?...z..|
00000010  eb d5 f0 e0 f3 12 e9 b1  25 54 67 06 83 e0 24 51  |........%Tg...$Q|
00000020  dd 5a 95 e7 18 78 97 2a  96 14 bd bc 9b 76 d4 01  |.Z...x.*.....v..|
00000030  91 7a a5 43 cb c5 60 5f  56 8e 0f 87 6e de 29 ce  |.z.C..`_V...n.).|
00000040  a4 3e 24 e5 ce aa bd 68  9c 03 c0 f8 f9 55 f5 f1  |.>$....h.....U..|
00000050  76 e5 d5 35 38 ad 48 fd  59 7d da ae db 6a 23 c1  |v..58.H.Y}...j#.|
00000060  f0 43 7e cc e5 72 b8 af  fe 9a 3e 16 2b aa fd bd  |.C~..r....>.+...|
00000070  bd 9c 68 e2 f3 a3 ba 33  0f 81 c7 06 03 be dc aa  |..h....3........|
00000080  87 2e ad b4 2b 03 e2 46  fd 23 78 56 9d d8 3a aa  |....+..F.#xV..:.|
00000090  3f 3a 17 93 21 95 2a 03  83 a5 7a a1 72 6f df 62  |?:..!.*...z.ro.b|
000000a0  4a d3 ff a7 4c 75 03 c0  93 76 91 21 4e ba 48 af  |J...Lu...v.!N.H.|
000000b0  b5 08 2a 3c 68 02 12 86  e6 38 74 7d 43 59 6c 3d  |..*<h....8t}CYl=|
000000c0  41 30 21 83 18 a0 0b c7  44 a2 20 d1 80 f2 9e 13  |A0!.....D. .....|
000000d0  14 7f 24 79 d3 e0 73 c8  7a e9 f3 a1 9a 43 44 0f  |..$y..s.z....CD.|
000000e0  87 3d bc 70 ec 45 76 86  72 c0 63 81 60 c6 00 ab  |.=.p.Ev.r.c.`...|
000000f0  f5 58 d7 45 87 48 30 67  5f fc 3e 1f 43 9c ba 03  |.X.E.H0g_.>.C...|
00000100  1d dc f4 3d f1 18 74 65  51 d7 87 c0 5e 10 41 b7  |...=..teQ...^.A.|
00000110  ff ea bb 78 64 bb fe a2  5d bf fe 90 7c 7b 16 38  |...xd...]...|{.8|
00000120  a1 49 7a bc 1f 01 cc ea  96 12 3c 3e 24 d1 ff aa  |.Iz.......<>$...|
00000130  a8 da 27 5f 7d 52 dc 7f  fd 28 33 5a db 27 b8 a3  |..'_}R...(3Z.'..|
00000140  95 e1 f0 38 fc b4 0b 4f  5b a3 4d ff 54 6e d6 b1  |...8...O[.M.Tn..|
00000150  dd b7 7c 0c 63 ca 73 ca  c7 82 3d 11 48 83 e1 9f  |..|.c.s...=.H...|
00000160  cd 36 7e cf 8e b9 07 63  ae d2 69 85 ff fa b8 22  |.6~....c..i...."|
00000170  08 b5 b8 6b de 97 f8 3b  e7 ff 72 01 65 4d 6a 5a  |...k...;..r.eMjZ|
00000180  30 0f 8b 0e a6 0e cb c7  76 dc 92 19 2f 54 3a fc  |0.......v.../T:.|
00000190  2f f2 b5 0a 3c 3b 4c 19  ee 6d b3 2e ee 73 73 09  |/...<;L..m...ss.|
000001a0  33 d1 92 f9 37 83 c6 84  c1 f4 56 66 f3 fd 5e f3  |3...7.....Vf..^.|
000001b0  4b 21 53 c1 0d 50 f6 03  2c ad 57 4b be 9c 00 fe  |K!S..P..,.WK....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 8d 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  8d 08 00 b8 5b 00 00 00  |............[...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Quackers on 2011-02-22
If you make sdc (your 120GB, Ubuntu 10.04 drive) the first bootable hard drive in your bios, then, when Ubuntu loads up run ```
sudo update-grub
``` in a terminal, you should see all 3 operating systems found as grub.cfg is run.
After that all 3 OSes should be bootable from the grub menu.

---

