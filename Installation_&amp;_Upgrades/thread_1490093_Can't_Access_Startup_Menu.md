---
title: "Can't Access Startup Menu"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by pewterbot9 on 2010-05-21
Hello, I just fresh-install upgraded from Jaunty Jackalope to Lucid Lynx, on my dual-boot netbook. Now, the startup menu does appear when I boot up, but only for a fraction of a second! Default bootup is of course, Ubuntu, but since the menu flashes by so fast, there's no way I can access the other choices, including Windoze Expee. 

So I installed Startup Manager, and set the timeout to 10 seconds. (And to "show text during boot".) Still, the startup menu flashed by, no delay at all, not even a second! Tried setting timeout to 100 seconds, and once more, this did not help. (Examining grub.cfg shows the timeout was changed to my specs...I just viewed the file.)

I searched for bootup problems in ubuntu forums, but did not find any problem similar to mine. My situation seems to be that I simply can't get the startup menu to delay, so I might access it.

How do I manage to correct this? TIA.

---

### Post by darkod on 2010-05-21
If you follow these instructions and post the content of the results file, it will show more:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by pewterbot9 on 2010-05-21
> **darkod said:**
> If you follow these instructions and post the content of the results file, it will show more:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Here it is, for your delectation, thanks:

--begin RESULTS.txt:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,193,149     8,193,087  12 Compaq diagnostics
/dev/sda2    *      8,193,150    90,124,649    81,931,500   7 HPFS/NTFS
/dev/sda3          90,124,650   270,855,899   180,731,250   c W95 FAT32 (LBA)
/dev/sda4         270,855,961   312,576,704    41,720,744   5 Extended
/dev/sda5         270,855,963   311,468,219    40,612,257  83 Linux
/dev/sda6         311,468,283   312,576,704     1,108,422  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8166 MB, 8166309888 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15949824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    15,936,479    15,936,417   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00C6-B478                              vfat       WINRE                         
/dev/sda2        F21CC8FE1CC8BEBB                       ntfs       OS_Install                    
/dev/sda3        1D05-213F                              vfat       FAT32                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        a9b4dd38-1c9c-46e8-b531-d009a1555999   ext4                                     
/dev/sda6        a7cc1653-3c3f-489d-9ab4-f27190a4da22   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F1E7-28C1                              vfat       8G class 6                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/sda2              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/8G class 6        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set a9b4dd38-1c9c-46e8-b531-d009a1555999
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
search --no-floppy --fs-uuid --set a9b4dd38-1c9c-46e8-b531-d009a1555999
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=25
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a9b4dd38-1c9c-46e8-b531-d009a1555999
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a9b4dd38-1c9c-46e8-b531-d009a1555999 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a9b4dd38-1c9c-46e8-b531-d009a1555999
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a9b4dd38-1c9c-46e8-b531-d009a1555999 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a9b4dd38-1c9c-46e8-b531-d009a1555999
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a9b4dd38-1c9c-46e8-b531-d009a1555999
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00c6-b478
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f21cc8fe1cc8bebb
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a7cc1653-3c3f-489d-9ab4-f27190a4da22 none            swap    sw              0       0
UUID=F21CC8FE1CC8BEBB /media/sda2 ntfs-3g users 0 0

=================== sda5: Location of files loaded by Grub: ===================


 149.6GB: boot/grub/core.img
 150.6GB: boot/grub/grub.cfg
 150.7GB: boot/initrd.img-2.6.32-22-generic
 150.6GB: boot/vmlinuz-2.6.32-22-generic
 150.7GB: initrd.img
 150.6GB: vmlinuz

--end RESULTS.txt

---

### Post by darkod on 2010-05-22
It all looks good. Sorry, I have no idea why it wouldn't show you the menu properly. :(

---

### Post by pewterbot9 on 2010-05-22
> **darkod said:**
> It all looks good. Sorry, I have no idea why it wouldn't show you the menu properly. :(

Well thanks for giving it your best shot. And that's what I posted originally: my problem isn't the same as other bootup issues I've found in these forums.

Once I use Startup Manager to make Windoze Expee the default, I will lose my access to Linux. But then I can find a Windoze-based dual-boot utility, to resolve this problem.

Perhaps someone else will chime in, with an answer to this problem. Strangely, I've never had a Linux problem resolved through this board, or any other. So I'm kinda used to it.

---

### Post by pewterbot9 on 2010-05-22
Hey darkod, you'll be glad to know I resolved my bootup problem by using a 3rd-party bootmanager:

GAG, the Graphical Boot Manager
[http://sourceforge.net/projects/gag/](http://sourceforge.net/projects/gag/)

Works like a charm, very user friendly. I highly recommend this application for anyone else, should Ubuntu's GRUB fail them.

---

