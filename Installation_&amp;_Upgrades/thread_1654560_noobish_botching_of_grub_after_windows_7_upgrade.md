---
title: "noobish botching of grub after windows 7 upgrade"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by Gargtholomew on 2010-12-28
Ok, so first I want to thank everyone for their time and help. Really, thank you. 

Second, if you have a link that deals with this then by all means just post that, I dont want to take up more time then is needed from anyone. 

I bought a ssd last week and wanted to dual boot ubuntu and windows. Got that working with 10.10 and XP sp3 just fine. Then I got(!cough!) windows 7 ult x64 and decided to upgrade my XP. After that, obviously, my MBR was overwritten and so I could not load ubuntu. I ran rescatux to reload my GRUB2 and now my MBR reads the partition with windows 7 on it as XP and will not boot from it says im missing the KMLPR files or some such.

I have the ability (but not the desire) to REINSTALL everything if that is easier. I am not familiar with ubuntu but like what I have seen so far and so would like to continue to use it and get familiar with it.

Once again thank you for any aid you provide.

---

### Post by Rubi1200 on 2010-12-28
Hi and welcome to the forums :)

To give us a better overview of the current state of your system, please boot the computer with a LiveCD choosing to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here please.

Thanks.

---

### Post by Gargtholomew on 2010-12-28
Ok here ya go, 

I think i see the problem, my old old install of xp is still on one of my old spin drives and might be confusing GRUB2?

I should still ses the windows 7 boot option which i did not, though.

---

### Post by Gargtholomew on 2010-12-28
bumpity bump!

---

### Post by wilee-nilee on 2010-12-28
Hold on.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,000,062    80,000,000   7 HPFS/NTFS
/dev/sda2          80,001,022   117,229,567    37,228,546   5 Extended
/dev/sda5          80,001,024    88,000,511     7,999,488  82 Linux swap / Solaris
/dev/sda6          88,002,560   117,229,567    29,227,008  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9C603461603443F4                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        230cda2c-2411-460e-841f-c6255a4ecf41   swap                                     
/dev/sda6        118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5A98915298912D8F                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        323C38223C37E011                       ntfs       Local Disk                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 12384a53384a364f
	drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=118383f3-d21f-4f9e-bdb2-9f5f0a5cb6a5 /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  47.4GB: boot/grub/core.img
  47.4GB: boot/grub/grub.cfg
  47.6GB: boot/initrd.img-2.6.35-24-generic-pae
  47.4GB: boot/vmlinuz-2.6.35-24-generic-pae
  47.6GB: initrd.img
  47.4GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer
```

---

### Post by wilee-nilee on 2010-12-28
So sda1 is W7 and doesn't look like an upgrade but a install.

sdb1 has a bootflag and the boot files showing is it a XP install? If not from gparted in Ubuntu uncheck the boot flag=sdb1, and run sudo-update-grub in Ubuntu and see if that works. If it does work you will see a notation in the terminal for sda1

---

### Post by Gargtholomew on 2010-12-29
I updated my Grub2 and got it to work. Now I see all OS's, thank you for the suggestion wilee. 

I am now in the process of putting my other dirves into RAID 1 to hold all my files and then im going to partition that RAID/drive 64gb ubuntu/438gb Win7. Here goes nothing.

---

