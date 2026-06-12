---
title: "Samsung N220 Plus GRUB2 problems - can't find Windows 7"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by sirsmegalot105 on 2010-11-22
Hi,

I have a Samsung N220 Plus netbook - it comes pre-installed with Windows 7 Starter, and there is also a Samsung Recovery partition. My goal was to install both XP SP3 and Ubuntu 10 Netbook, in addition the original OS, so a triple boot situation.

Upon initial boot of Windows 7, C: and D: were created. Using GParted on a live USB I deleted and re-partitioned D: (/dev/sda5) in to the scheme below:

[ATTACH]176259[/ATTACH]

So to summarise the partitioning scheme (first 3 are as is only sda5 got re-chunked for XP / Ubuntu installs):

/dev/sda1 - Recovery partition
/dev/sda2 - System partition
/dev/sda3 - Windows 7 partition
/dev/sda4 - Extended
 /dev/sda5 - XP partition 
 /dev/sda6 - Storage partition
 /dev/sda7 - Ubuntu partition
 /dev/sda8 - Ubuntu swap partition

Upon installing XP and restarting, it booted in to XP which was expected. I then installed UNR 10.10 from live USB to sda7 and sda8 for the swap. Although there was an initial issue with Grub not loading, the link in this [post]("http://ubuntuforums.org/showpost.php?p=8582333&postcount=3") resolved it for me.

This is how XP sees the world (XP installation created its base drive as D: instead of C:):

[ATTACH]176261[/ATTACH]

However this is the Grub menu that I get:

[ATTACH]176260[/ATTACH]

What is interesting about these options is that (aside from the first 4 entries created by Ubuntu install):

- 'Windows Vista (Loader) (on /dev/sda1)' - this loads Samsung Recovery Solution
- 'Windows 7 (loader) (on /dev/sda2)' - this loads the Windows XP installation

So the problem here is that I can't find boot up the original Windows 7 installation. I have tried various solutions on Ubuntu Forums for adding a custom entry to 40_custom file, and using sudo update-grub and sudo grub-mkconfig etc, but this resulted in "A disk read error has occurred. Press Ctrl Alt Del to reboot'. Grub's OS probe doesn't find the Windows 7. 

Here is the output of BootInfoScript:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /BOOT/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    41,945,087    41,943,040  27 Hidden HPFS/NTFS
/dev/sda2    *     41,945,088    42,149,887       204,800   7 HPFS/NTFS
/dev/sda3          42,149,888   128,133,119    85,983,232   7 HPFS/NTFS
/dev/sda4         128,135,166   488,394,751   360,259,586   f W95 Ext d (LBA)
/dev/sda5         128,135,168   210,055,167    81,920,000   7 HPFS/NTFS
/dev/sda6         210,057,216   414,857,215   204,800,000   7 HPFS/NTFS
/dev/sda7         414,859,264   482,443,263    67,584,000  83 Linux
/dev/sda8         482,445,312   488,394,751     5,949,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A987A88987A7255                       ntfs       RECOVERY                      
/dev/sda2        D0BC4922BC490506                       ntfs       SYSTEM                        
/dev/sda3        A0EE7E12EE7DE0C8                       ntfs       7                             
/dev/sda4: PTTYPE="dos" 
/dev/sda5        A8A8A63DA8A609C0                       ntfs       xp                            
/dev/sda6        3DD1C42C44739CF6                       ntfs       storage                       
/dev/sda7        9f6b5560-45f1-46d2-bb59-b815badffa3b   ext4                                     
/dev/sda8        9b9e9545-5f4f-4f09-9820-b8c0e304d061   swap       swap                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=600)


================================ sda2/boot.ini: ================================

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set 9f6b5560-45f1-46d2-bb59-b815badffa3b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9f6b5560-45f1-46d2-bb59-b815badffa3b
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9f6b5560-45f1-46d2-bb59-b815badffa3b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9f6b5560-45f1-46d2-bb59-b815badffa3b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9f6b5560-45f1-46d2-bb59-b815badffa3b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9f6b5560-45f1-46d2-bb59-b815badffa3b ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9f6b5560-45f1-46d2-bb59-b815badffa3b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9f6b5560-45f1-46d2-bb59-b815badffa3b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0a987a88987a7255
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d0bc4922bc490506
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.backup ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.backup ###

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
UUID=9f6b5560-45f1-46d2-bb59-b815badffa3b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9b9e9545-5f4f-4f09-9820-b8c0e304d061 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 240.4GB: boot/grub/core.img
 214.9GB: boot/grub/grub.cfg
 217.4GB: boot/initrd.img-2.6.35-22-generic
 240.4GB: boot/vmlinuz-2.6.35-22-generic
 217.4GB: initrd.img
 240.4GB: vmlinuz

```

Thanks in advance for any assistance ;)

---

### Post by sirsmegalot105 on 2010-11-27
For the benefit of anyone reading this, I wasn't able to resolve this issue. I believe it could have been caused by the number of primary partitions or the fact that XP was installed after 7. Due to lack of N220 drivers for XP (the 7 drivers did not work), I removed XP and am now in a dual boot situation with 7 and UNR 10.10.

I would still love to know how this issue could be sorted in GRUB for future reference, so if anyone knows... :popcorn:

---

