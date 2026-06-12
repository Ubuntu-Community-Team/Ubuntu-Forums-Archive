---
title: "Windows won't boot ..."
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by scho on 2011-01-11
I have dual booting system which has Windows first installed. 
And, installed Ubuntu 9.10 later, and upgraded to 10.04 again.

I am mostly using Ubuntu, and I don't exactly recall when 
was the last time I was able to use Windows. Though, I am sure
I was able to use Windows before, but now, when I selected 
Windows in the GRUB menu, nothing is happening, and just getting 
back to GRUB window after the screen is flickering several times.

So, I am just wondering if there is anyway to fix this without
installing them again, or at least want to avoid ubuntu fresh 
install since I have many other applications installed. But, 
for Windows, I don't mind install it fresh since I have nothing
important in there.

---

### Post by Quackers on 2011-01-11
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by scho on 2011-01-11
--

---

### Post by scho on 2011-01-11
That's what I thought. The following is the file contents, and looks like,
there are some problems.

-> 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #5 for /grub/stage2 and /grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 180647141 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   144,536,804   144,536,742   7 HPFS/NTFS
/dev/sda2         144,536,805   253,907,324   109,370,520  83 Linux
/dev/sda3         253,907,325   312,496,379    58,589,055   5 Extended
/dev/sda5         253,907,388   312,496,379    58,588,992  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 897.0 GB, 896998047744 bytes
255 heads, 63 sectors/track, 109053 cylinders, total 1751949312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   113,547,419   113,531,355   f W95 Ext d (LBA)
/dev/sdb5              16,128   113,547,419   113,531,292   7 HPFS/NTFS
/dev/sdb2         113,547,420 1,751,936,444 1,638,389,025  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        28CCFB38CCFAFF3E                       ntfs                                     
/dev/sda2        e4c93c27-8126-47b9-900f-c0acf400acea   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        09eea583-a988-4e19-a81c-7ea1ce278cc2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        25b176b7-9951-4b6d-9846-16aa49af3b79   ext3                                     
/dev/sdb5        AE4051C1405190C7                       ntfs       MicroPET                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc10       6409c68e-1ec3-4023-98d8-69b1c206dd1f   ext3       ExtDrive                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)
/dev/sdb2        /home                    ext3       (rw)
/dev/sdc10       /media/ExtDrive          ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=e4c93c27-8126-47b9-900f-c0acf400acea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4c93c27-8126-47b9-900f-c0acf400acea
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 28ccfb38ccfaff3e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e4c93c27-8126-47b9-900f-c0acf400acea /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=25b176b7-9951-4b6d-9846-16aa49af3b79 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=09eea583-a988-4e19-a81c-7ea1ce278cc2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  92.4GB: boot/grub/core.img
  92.4GB: boot/grub/grub.cfg
  92.4GB: boot/initrd.img-2.6.31-22-generic
  92.4GB: boot/initrd.img-2.6.32-23-generic
  92.4GB: boot/initrd.img-2.6.32-24-generic
  92.4GB: boot/initrd.img-2.6.32-25-generic
  92.4GB: boot/initrd.img-2.6.32-26-generic
  92.4GB: boot/initrd.img-2.6.32-27-generic
  92.4GB: boot/vmlinuz-2.6.31-22-generic
  92.4GB: boot/vmlinuz-2.6.32-23-generic
  92.5GB: boot/vmlinuz-2.6.32-24-generic
  92.5GB: boot/vmlinuz-2.6.32-25-generic
  92.4GB: boot/vmlinuz-2.6.32-26-generic
  92.3GB: boot/vmlinuz-2.6.32-27-generic
  92.4GB: initrd.img
  92.4GB: initrd.img.old
  92.3GB: vmlinuz
  92.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  45 52 02 00 74 70 6d b0  00 00 00 00 00 00 00 00  |ER..tpm.........|
00000010  00 04 00 00 00 40 00 17  00 01 00 00 00 78 00 24  |.....@.......x.$|
00000020  ff ff 00 00 00 b0 00 15  07 01 00 00 00 e8 00 22  |..............."|
00000030  f8 ff 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


---

### Post by Quackers on 2011-01-11
I see you are having the same forum problems as others (me included). You can just highlight everything in your duplicate post and hit delete.

It seems that your Win XP boot files are complete, but as grub has been installed to that partition at some time, it may have affected them. This could be the reason why XP is not booting.
We can try re-installing grub to the mbr of sda and see if that clears the problem, but I wouldn't hold your breath :-)
We can also try restoring the Windows bootloader and then re-installing grub.
I take it you have a Windows XP repair or installation disc?

---

### Post by chris0108 on 2011-01-11
Dont know if this helps, but i had a similar problem with two linux distro's and found this thread on here

[http://ubuntuforums.org/showthread.php?t=1321149&highlight=grub+error+15]("http://ubuntuforums.org/showthread.php?t=1321149&highlight=grub+error+15")

I followed the instructions and it sorted out the grub booting issue

---

