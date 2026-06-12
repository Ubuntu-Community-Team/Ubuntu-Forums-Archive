---
title: "can't get back into w7 after upgrade"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by skawars on 2010-05-11
I upgraded to lucid on the release date, and liked it from the beginning, but have ran into a couple of problems. 

Since upgrading, whenever i (rarely) boot into my w7 partition, i'm just presented with a blank screen, the windows loading bar never appears. I know this is very vague, but i'm stuck for ideas, all of the partitions look fine in disk utility.

It's frustrating as I rarely use the windows partition but it is essential for some of my needs

---

### Post by bumanie on 2010-05-11
This has been a common issue with 10.04 for some reason. Look[ here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") for guidance.

---

### Post by darkod on 2010-05-11
I think I know what happened but to confirm please run the boot info script in my signature. There are instructions in the link or ask if you need to. It will create results.txt file with more detailed info about your boot process.

Post the results of the first part here. It has the MBR bootloaders listed on top and then all partitions one by one with details of which OS is on them and boot files. This is what I need to see, the info for your win7 partition (and win7 boot partition if you have it).

---

### Post by darkod on 2010-05-11
> **bumanie said:**
> This has been a common issue with 10.04 for some reason. Look[ here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") for guidance.

That's what I had in mind. :)

---

### Post by skawars on 2010-05-11
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 604985288 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   589,641,727   589,434,880   7 HPFS/NTFS
/dev/sda3         623,370,195   625,137,344     1,767,150   5 Extended
/dev/sda5         623,386,260   625,137,344     1,751,085  82 Linux swap / Solaris
/dev/sda4         589,649,760   623,370,194    33,720,435  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        484A64914A647D96                       ntfs       System Reserved               
/dev/sda2        8A966AE2966ACDEF                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        e4ddd93c-ce66-4d65-bda5-74df79492c95   ext2                                     
/dev/sda5        081fa3ba-10d8-4ecb-a03d-7e148e013768   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext2       (rw,errors=remount-ro)
/dev/sda2        /media/w7                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set e4ddd93c-ce66-4d65-bda5-74df79492c95
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set e4ddd93c-ce66-4d65-bda5-74df79492c95
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set e4ddd93c-ce66-4d65-bda5-74df79492c95
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=e4ddd93c-ce66-4d65-bda5-74df79492c95 ro  splash vga=799 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set e4ddd93c-ce66-4d65-bda5-74df79492c95
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=e4ddd93c-ce66-4d65-bda5-74df79492c95 ro single  splash vga=799 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set e4ddd93c-ce66-4d65-bda5-74df79492c95
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set e4ddd93c-ce66-4d65-bda5-74df79492c95
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 484a64914a647d96
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=e4ddd93c-ce66-4d65-bda5-74df79492c95 / ext2 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=081fa3ba-10d8-4ecb-a03d-7e148e013768 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/w7 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/System\040Reserved ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sda4: Location of files loaded by Grub: ===================


 309.7GB: boot/grub/core.img
 309.7GB: boot/grub/grub.cfg
 309.5GB: boot/initrd.img-2.6.32-22-generic
 309.5GB: boot/vmlinuz-2.6.32-22-generic
 309.5GB: initrd.img
 309.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by darkod on 2010-05-11
Try moving the /grldr file from /dev/sda1. It's not part of the win7 boot process and has no business there. Not to my knowledge.

Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/grldr[/COLOR]
[COLOR=Black]
See if that helps it boot win7. Otherwise the boot sector of /dev/sda1 is good.
[/COLOR]

---

### Post by skawars on 2010-05-11
> **darkod said:**
> Try moving the /grldr file from /dev/sda1. It's not part of the win7 boot process and has no business there. Not to my knowledge.

Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/grldr[/COLOR]
[COLOR=Black]
See if that helps it boot win7. Otherwise the boot sector of /dev/sda1 is good.
[/COLOR]

sorry, could you explain how i do this? thanks

---

### Post by skawars on 2010-05-11
i forgot to mention this earlier, but i can tell the boot is unsuccessful instantly as i get the blinking cursor as normal, but no light flashing to indicate anything is actually happening

---

### Post by darkod on 2010-05-11
> **skawars said:**
> sorry, could you explain how i do this? thanks

Just boot ubuntu, click in Places and you should see the System Reserved label partition, that's /dev/sda1. Click on it to mount it (maybe it will ask for your ubuntu password).

In there should be grldr right away in the root. Just move the file in your Home for example.

If mounting that way doesn't work, another way to mount is in terminal:

mkdir /media/tmp
sudo mount /dev/sda1 /media/tmp

Then it will be in your /media/tmp folder.

---

### Post by skawars on 2010-05-11
> **darkod said:**
> Just boot ubuntu, click in Places and you should see the System Reserved label partition, that's /dev/sda1. Click on it to mount it (maybe it will ask for your ubuntu password).

In there should be grldr right away in the root. Just move the file in your Home for example.

If mounting that way doesn't work, another way to mount is in terminal:

mkdir /media/tmp
sudo mount /dev/sda1 /media/tmp

Then it will be in your /media/tmp folder.

thanks for all the help, but still exactly the same :(. It must be something to do with Grub as I received errors when upgrading to 10.04, any ideas?

---

### Post by angrymeat on 2010-05-11
I am having the same issue I upgraded to 10.4 and am no longer able to  boot into windows 7  I ran your script here is the output below . When I select windows 7 from the boot menu I goes black for a few seconds then returns to the grub menu  I also tried the testdisk with no luck . 

The windows xp entry is an old one  so im not worried about it the drive doesn't have xp on it anymore. 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=df4d67bd-a776-4eeb-8d02-00506d9028d9)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 729857574 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #724579758 on boot drive #2
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   724,579,694   724,579,632   7 HPFS/NTFS
/dev/sdb2         724,579,695   976,768,064   252,188,370   5 Extended
/dev/sdb5         724,579,758   966,438,269   241,858,512  83 Linux
/dev/sdb6         966,438,333   976,768,064    10,329,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70009E2A009DF6F6                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1C44A7FF44A7DA32                       ntfs       OS                            
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        8a6541f0-2cb0-4c11-b104-a001c98b85fa   ext4                                     
/dev/sdb6        1b4517b7-317e-4ae5-9c6b-7b28901a5ed9   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
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
search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8a6541f0-2cb0-4c11-b104-a001c98b85fa ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8a6541f0-2cb0-4c11-b104-a001c98b85fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8a6541f0-2cb0-4c11-b104-a001c98b85fa ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8a6541f0-2cb0-4c11-b104-a001c98b85fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(sd1,1)
chainloader +1
}
### END /etc/grub.d/11_windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8a6541f0-2cb0-4c11-b104-a001c98b85fa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 70009e2a009df6f6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 1c44a7ff44a7da32
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=8a6541f0-2cb0-4c11-b104-a001c98b85fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=1b4517b7-317e-4ae5-9c6b-7b28901a5ed9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 373.6GB: boot/grub/core.img
 386.2GB: boot/grub/grub.cfg
 372.1GB: boot/initrd.img-2.6.31-14-generic
 373.0GB: boot/initrd.img-2.6.32-22-generic
 371.5GB: boot/vmlinuz-2.6.31-14-generic
 371.8GB: boot/vmlinuz-2.6.32-22-generic
 373.0GB: initrd.img
 372.1GB: initrd.img.old
 371.8GB: vmlinuz
 371.5GB: vmlinuz.old

---

### Post by skawars on 2010-05-12
sorry is there still no solution to this problem? i tried booting from a w7 disk to repair it but no success. do i have to reinstall w7?

---

### Post by darkod on 2010-05-12
No need to reinstall. Give me few mins to study the results and I'll see what can be done.

---

### Post by darkod on 2010-05-12
OK, few things to fix.

1.

sdb1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sdb1  and 
                       looks at sector 729857574 of the same hard drive  for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying  to 
                       chain load sector #724579758 on boot drive #2[/COLOR]
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe  [COLOR=Red]/grldr[/COLOR]

This shouldn't be here.
If you can boot ubuntu, open /dev/sdb1 (should be in Places) and delete the grldr file. If you can't boot the hdd ubuntu you can do that from the live mode.
Then follow these instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

to remove Grub2 from your partition /dev/sdb1. Be careful to select the correct disk, /dev/sdb, and then the correct partition, #1.

After that is done you might run the script again and check to see if the fix worked. No need to post the results if it did.

2.

=> Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=[COLOR=Red]df4d67bd-a776-4eeb-8d02-00506d9028d9[/COLOR])/boot/grub.

/dev/sdb5        [COLOR=Red]8a6541f0-2cb0-4c11-b104-a001c98b85fa[/COLOR]

After the upgrade grub2 is looking at the wrong partition because it has a new UUID. Also, it's better to have grub2 in the MBR of /dev/sdb (not /dev/sda) because that's where ubuntu is.
Boot your ubuntu installation and execute:

sudo grub-install /dev/sdb

If you can't boot the hdd ubuntu, from the live mode the command is different:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Restart and you should be able to boot ubuntu without any problems. Be careful in BIOS the disk /dev/sdb to be first in hdd boot order. /dev/sda will still have the broken grub2 but we'll sort it out later, not a priority.

---

### Post by skawars on 2010-05-12
thanks for the lengthy reply, just checking you do know its the windows partition i can't access? the ubuntu one is working perfectly, just when i select windows i get a blank screen and no response from the laptop. note i am NOT getting an automatic restart at this point, which i noticed some other users have mentioned.

---

### Post by darkod on 2010-05-12
> **skawars said:**
> thanks for the lengthy reply, just checking you do know its the windows partition i can't access? the ubuntu one is working perfectly, just when i select windows i get a blank screen and no response from the laptop. note i am NOT getting an automatic restart at this point, which i noticed some other users have mentioned.

The wrong UUID I specified in point 2 should prevent you from booting ubuntu too. Strange...

However, point 1 is exactly for what you are describing. Grub2 needs to be removed from /dev/sdb1, your win7 partition. And the file /grldr if you already haven't done so.

So try doing just that, and see if it helps.

---

### Post by skawars on 2010-05-12
upon running sudo grub etc in terminal im faced with this error:

/usr/sbin/grub-setup: error: cannot open `/dev/sdb' while attempting to get disk size.

i've already done the testdisk a couple of times after original advice to no avail.

---

### Post by Kir_B on 2010-05-12
> **skawars said:**
> thanks for the lengthy reply, just checking you do know its the windows partition i can't access? the ubuntu one is working perfectly, just when i select windows i get a blank screen and no response from the laptop. note i am NOT getting an automatic restart at this point, which i noticed some other users have mentioned.


I too, am in the exact position as the original poster. Ubuntu runs fine, but when I try to boot into my vista, all I get is a blinking underscore.

I've downloaded the boot info script, but I 'm not sure of the proper procedure to run it. I thought it would be wise to ask one of you fine folks, as I really don't want to make things worse.
           Thanks. Kirby

---

### Post by darkod on 2010-05-12
> **skawars said:**
> upon running sudo grub etc in terminal im faced with this error:

/usr/sbin/grub-setup: error: cannot open `/dev/sdb' while attempting to get disk size.

i've already done the testdisk a couple of times after original advice to no avail.

Quick search about that error says something like this can help:

sudo grub-mkconfig && update-grub

---

### Post by darkod on 2010-05-12
> **Kir_B said:**
> I too, am in the exact position as the original poster. Ubuntu runs fine, but when I try to boot into my vista, all I get is a blinking underscore.

I've downloaded the boot info script, but I 'm not sure of the proper procedure to run it. I thought it would be wise to ask one of you fine folks, as I really don't want to make things worse.
           Thanks. Kirby

After downloading it place it on the desktop for example, and in terminal execute it with:

sudo bash ~/Desktop/boot_info_script*.sh

The results.txt file will appear on the desktop. But if the problem doesn't turn out to be identical we should proceed in a new thread, it's difficult helping out with different problems in the same thread.

Also when posting the results please include them in CODE tags. With the text selected hit the # button in the toolbar above when creating your post. Makes it easier for reading.

---

### Post by skawars on 2010-05-12
> **darkod said:**
> Quick search about that error says something like this can help:

sudo grub-mkconfig && update-grub

gave this a go, still no joy. there was a lot posted in the terminal that i could maybe paste into here that may help, but i'm gonna leave it till tomorrow. thanks again

---

### Post by Kir_B on 2010-05-14
> **darkod said:**
> After downloading it place it on the desktop for example, and in terminal execute it with:

sudo bash ~/Desktop/boot_info_script*.sh

The results.txt file will appear on the desktop. But if the problem doesn't turn out to be identical we should proceed in a new thread, it's difficult helping out with different problems in the same thread.

Also when posting the results please include them in CODE tags. With the text selected hit the # button in the toolbar above when creating your post. Makes it easier for reading.

Thanks so much darkod. I would've responded last night, but my internet went down right after I posted and I didn't get it working until very late last night (I just assumed, it was my crappy internet provider). It's always something stupid. The phone cord got unplugged :oops: which is usually the first thing I check, but this time, that's the last thing I checked ](*,). I _**will**_ remember next time #-o .

I really appreciate the help, as I've only been using linux for six months and haven't needed to run a script until now. I love learning new things, even when I'm forced to and grub2 seems to be forcing me, once again, to do a little learning.

I'll post the results here, and if necessary, I'll post it in a new thread.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 297825330 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 296965826 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 297825522 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 297059058 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 297076258 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304    21,069,823    20,971,520   7 HPFS/NTFS
/dev/sda3          21,069,824   137,986,047   116,916,224   7 HPFS/NTFS
/dev/sda4         284,928,840   488,279,609   203,350,770   5 Extended
/dev/sda5         284,928,903   288,832,634     3,903,732  82 Linux swap / Solaris
/dev/sda6         288,832,698   318,135,194    29,302,497  83 Linux
/dev/sda7         318,135,258   488,279,609   170,144,352  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0815                              vfat       DellUtility                   
/dev/sda2        54823FF1823FD5E8                       ntfs       RECOVERY                      
/dev/sda3        2E560A97560A6047                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        664e2c4b-a1bf-4168-8d08-e03c2dfa485d   swap                                     
/dev/sda6        bc6db48c-e366-4bf9-b061-e97404dcb1c7   ext3                                     
/dev/sda7        39713d18-ed5b-47ed-98be-41c5e6f3ae11   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw,relatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
insmod png
if background_image /usr/share/images/grub/sag+linux_mascots-640x480-for_grub.png ; then
  set color_normal=light-cyan/black
  set color_highlight=light-magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro splash xforcevesa quiet vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro single splash xforcevesa quiet vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro splash xforcevesa quiet vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro single splash xforcevesa quiet vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro splash xforcevesa quiet vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro single splash xforcevesa quiet vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro splash xforcevesa quiet vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro single splash xforcevesa quiet vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro splash xforcevesa quiet vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    echo    'Loading Linux 2.6.31-16-generic ...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro single splash xforcevesa quiet vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro splash xforcevesa quiet vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    echo    'Loading Linux 2.6.28-16-generic ...'
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro single splash xforcevesa quiet vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.28-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bc6db48c-e366-4bf9-b061-e97404dcb1c7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-0815
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 54823ff1823fd5e8
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2e560a97560a6047
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=39713d18-ed5b-47ed-98be-41c5e6f3ae11 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=664e2c4b-a1bf-4168-8d08-e03c2dfa485d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 152.1GB: boot/grub/core.img
 152.1GB: boot/grub/grub.cfg
 152.1GB: boot/grub/stage2
 152.3GB: boot/initrd.img-2.6.28-16-generic
 152.1GB: boot/initrd.img-2.6.31-16-generic
 152.2GB: boot/initrd.img-2.6.31-17-generic
 152.2GB: boot/initrd.img-2.6.31-20-generic
 152.2GB: boot/initrd.img-2.6.31-21-generic
 152.7GB: boot/initrd.img-2.6.32-22-generic
 152.0GB: boot/vmlinuz-2.6.28-16-generic
 152.2GB: boot/vmlinuz-2.6.31-16-generic
 152.6GB: boot/vmlinuz-2.6.31-17-generic
 152.1GB: boot/vmlinuz-2.6.31-20-generic
 152.2GB: boot/vmlinuz-2.6.31-21-generic
 153.3GB: boot/vmlinuz-2.6.32-22-generic
 152.7GB: initrd.img
 152.2GB: initrd.img.old
 153.3GB: vmlinuz
 152.2GB: vmlinuz.old
```Again, thanks a lot. Kirby :)

---

### Post by darkod on 2010-05-14
@Kir_B

As you could notice if you browsed the info in the file (I know, there is much info), you have:
/dev/sda1 Dell Utility partition
/dev/sda2 Recovery partition
/dev/sda3 Vista system partition (even though in the grub menu it might be called recovery environment, don't know why)
/dev/sda6 Ubuntu root

You need to use this fix:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

on both /dev/sda2 and /dev/sda3, one at a time. If you want the dell utility partition present in grub menu and available to be selected, do it for /dev/sda1 too.

You can run that fix from your ubuntu which you should be able to boot. If not, you can run it from the cd live mode too.

After that you should be able to boot windows.

---

### Post by Kir_B on 2010-05-14
Thanks darko. Your absolutely right, Grub2 is a little confused. It should be "dell partition utility" on sad/1, "vista recovery environment" on sda/2 and the "vista boot loader" on sda/3. As I've said elsewhere, **grub2 isn't quite ready for prime time**. 

I'll give it a go and post the results.

Thanks again darko, and everyone else that has contributed to fixing these problems.
                     Kirby

---

### Post by darkod on 2010-05-14
> **Kir_B said:**
>  As I've said elsewhere, **grub2 isn't quite ready for prime time**. 


You're being a bit too harsh. Grub2 just detects the windows boot files and according to them tries to guess what it found. On some occasions it will guess wrong.

I would take grub2 even with its "mistakes" any time over windows bootloader that doesn't see any other OS. :) How are you supposed to boot another OS? Using EasyBCD, a third party software? :confused:

---

### Post by Kir_B on 2010-05-14
> **darkod said:**
> You're being a bit too harsh. Grub2 just detects the windows boot files and according to them tries to guess what it found. On some occasions it will guess wrong.

I would take grub2 even with its "mistakes" any time over windows bootloader that doesn't see any other OS. :) How are you supposed to boot another OS? Using EasyBCD, a third party software? :confused:

You are absolutely right, in that I'd also take lilo, grub, or grub2 over the windows boot-loader, or windoze any day, period! But then, why would the monopoly that is windoze give anyone the ability to boot another OS, as from what I've seen from them, there isn't another OS in existence to boot, at least as far as they're concerned. Pretty arrogant indeed! I'd kick that OS off of my hard drive in a heart beat, if I knew that I wouldn't need it again someday, but I just know that the day that I give it the old heave ho, is the day that I 'll need it for something or other and I won't contribute another penny to that criminal empire/monopoly.
 
 I have very limited first hand experience with grub1, or lilo, but I've read  quite a bit about grub2's issues ever since I upgraded from jaunty to  karmic and decided to complete the upgrade by installing grub2 ([COLOR=#000099] [my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR] ). I haven't  seen very many problems with grub1, or lilo, but as I've said, I've only been  using the alternative to windoze for six months now. Please don't assume that I'm not grateful for everyone's efforts that went into grub2, but I do think that it should have came with a very big warning for rookies, like myself. Please accept my humble apology if I gave that impression.
 
I have a quick question for you. On the sixth screen, Im supposed to choose to "BackupBS", but it doesn't have that choice.

Below are my choices:
"[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]"

Am I right in guessing that "[Org. BS ]" is "BackupBS"?

Thanks again. Kirby

P.S. long live the Grand unified boot-loader.

---

### Post by darkod on 2010-05-14
> **Kir_B said:**
> You are absolutely right, in that I'd also take lilo, grub, or grub2 over the windows boot-loader, or windoze any day, period! But then, why would the monopoly that is windoze give anyone the ability to boot another OS, as from what I've seen from them, there isn't another OS in existence to boot, at least as far as they're concerned. Pretty arrogant indeed! I'd kick that OS off of my hard drive in a heart beat, if I knew that I wouldn't need it again someday, but I just know that the day that I give it the old heave ho, is the day that I 'll need it for something or other and I won't contribute another penny to that criminal empire/monopoly.
 
 I have very limited first hand experience with grub1, or lilo, but I've read  quite a bit about grub2's issues ever since I upgraded from jaunty to  karmic and decided to complete the upgrade by installing grub2 ([COLOR=#000099] [my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR] ). I haven't  seen very many problems with grub1, or lilo, but as I've said, I've only been  using the alternative to windoze for six months now. Please don't assume that I'm not grateful for everyone's efforts that went into grub2, but I do think that it should have came with a very big warning for rookies, like myself. Please accept my humble apology if I gave that impression.
 
I have a quick question for you. On the sixth screen, Im supposed to choose to "BackupBS", but it doesn't have that choice.

Below are my choices:
"[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]"

Am I right in guessing that "[Org. BS ]" is "BackupBS"?

Thanks again. Kirby

P.S. long live the Grand unified boot-loader.

I have never needed to use that fix, fortunately. I just have it bookmarked for people with that problem. I have no idea how the screens look like. :(

But that page also says: 'If  the sixth  screen did not have  a "BackupBS"  tab,  it usually means  that the original and backup boot sector are identical, and you are  probably suffering from a different problem. But it could also mean that  your backup boot sector is corrupted, in which case you will of to use  "fixboot" from a Windows CD to repair the boot sector.'

Without giving a direct answer what to do in that case. If I had to guess, my choice would be RebuildBS rather than Org.BS.

---

### Post by Kir_B on 2010-05-14
Thanks Darko. 

I'll research the issue further before I continue. I suspect what has happened, is that grub2 got placed in the wrong partition.

Kirby

---

