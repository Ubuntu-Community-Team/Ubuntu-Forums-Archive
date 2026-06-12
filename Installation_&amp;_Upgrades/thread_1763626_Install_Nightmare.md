---
title: "Install Nightmare"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by topdog2009 on 2011-05-20
I tried Ubuntu about 18 months ago but could not get online using a USB stick so went with Mepis which is still on my laptop. Decided to try Ubuntu again using the latest version.

I am running Windows XP on my desktop. The original hard drive on my computer was giving me problems so a new one was installed. The old one is still in place and usable. Windows Explorer shows the new HD as Drive C (which is partitioned to C & D) and the old drive as Drive F (partitioned as F,G,H). Drive E is the CD/DVD Drive. Having said that, windows BIOS thinks that the new drive is DRIVE D. Interesting. I have no idea how all this goes together, it was done for me.

Downloaded ISO and put on to CD.

Wanted to run Ubuntu alongside my Windows. Followed all the instructions. When it came to resizing partitions I gave Ubuntu 100GB. It said it might take a while. After just over three hours I decided something was wrong & came out of the install. Tried again, this time, it did not ask about partition but just loaded. 

When I reboot I get the use choice Windows or Ubuntu. Windows works. Ubuntu does not.

HELP!! Please be as specific as possible. 

Brian :confused:

---

### Post by IWantFroyo on 2011-05-20
Get a GParted CD and check to make sure it partitioned. Sometimes people just forget to push the apply button.

EDIT: Reread your post. I accidentally skipped over a detail. Try reburning and reinstalling Ubuntu. It could've been a disc problem.

---

### Post by jerome1232 on 2011-05-20
What error do you get when you try to boot Ubuntu?

---

### Post by topdog2009 on 2011-05-20
Will try to reinstall. The partition thing seemed to have worked.

Brian

---

### Post by topdog2009 on 2011-05-20
Not sure what message - am trying a reinstall first.

Thanks

Brian

---

### Post by topdog2009 on 2011-05-20
I reinstalled Ubuntu. This time it took somewhat longer in the install but the partition resizing did not take long.

I have the same problem. When booting up the computer i get the option to choose which operating system I want. Windows XP works fine.

With Ubuntu I get the following message :-
Windows could not start because the following file is missing or corrupt:-
<windows root>\syste32\hal.dll
Please reinstall a copy of the above file.

I do not think that a windows file would cause a problem with Ubuntu. I suspect that, because of the two hard drives I have on my computer, that the boot file is in the wrong place (or whatever it is called).

Brian

---

### Post by jerome1232 on 2011-05-20
Can you post the results of bootinfo script?

Details on where to get it and how to use can be found here
[http://ubuntuforums.org/showpost.php?p=8104352&postcount=1](http://ubuntuforums.org/showpost.php?p=8104352&postcount=1)

You can use it from a live cd.

---

### Post by topdog2009 on 2011-05-21
Here it is.

Brian

---

### Post by rudie81 on 2011-05-21
hey, i have the exact the same problem!!

this in the output to 'wubildr' on my ubuntu partition

[I]Press   to start GRUB, any other key to boot previous MBR ... 
Timeout :      
Invalid previous MBR. Press any key to start GRUB ... 
Cannot find GRLDR.  to hold the screen, any other key to boot previous MBR ... 
Error while reading MBR of  drive (hd0 )  
Invalid boot indicator in partition table of  
Invalid sectors_per_track in partition table of  
Invalid start_sector in partition table of  
Invalid end_sector in partition table of  
No boot signature in partition table of  
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart. 

[/I]

---

### Post by topdog2009 on 2011-05-28
Hey guys

After sending in the requested information, the help on this seems to have dried up. I do not mind if you cannot assist any further but please let me know so that I can discard Ubuntu from the computer.

Thanks

Brian

---

### Post by Hedgehog1 on 2011-05-28
Let me post the results in an easier to read fashion:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 9 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.........79...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 4941856 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    71,682,029    71,681,967   c W95 FAT32 (LBA)
/dev/sda2          71,682,030   156,296,384    84,614,355   f W95 Extended (LBA)
/dev/sda5          71,682,093   123,009,704    51,327,612   7 NTFS / exFAT / HPFS
/dev/sda6         123,009,768   156,296,384    33,286,617   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   286,286,552   286,286,490   7 NTFS / exFAT / HPFS
/dev/sdb2         286,287,870   976,751,983   690,464,114   f W95 Extended (LBA)
/dev/sdb5         819,202,608   976,751,983   157,549,376   7 NTFS / exFAT / HPFS
/dev/sdb6         692,562,276   819,202,544   126,640,269  83 Linux
/dev/sdb7         495,388,672   690,470,911   195,082,240  83 Linux
/dev/sdb8         690,472,960   692,561,919     2,088,960  82 Linux swap / Solaris
/dev/sdb9         286,287,872   493,295,615   207,007,744  83 Linux
/dev/sdb10        493,297,664   495,380,479     2,082,816  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4003 MB, 4003463168 bytes
84 heads, 19 sectors/track, 4899 cylinders, total 7819264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064     7,819,263     7,811,200   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4398-2599                              vfat       
/dev/sda5        11F38050F0F13FB1                       ntfs       
/dev/sda6        11F382FB14682581                       ntfs       
/dev/sdb1        7EC4B2EFC4B2A8B3                       ntfs       
/dev/sdb10       058ea482-66cd-43a9-9e9c-f875d757a015   swap       
/dev/sdb5        C4B099C8B099C0FA                       ntfs       Saved Stuff
/dev/sdb6        c8f30839-d2da-4baa-b079-43420f13c3f0   ext2       
/dev/sdb7        874345ae-8ca3-491c-8db5-7ca668cb3f0d   ext4       
/dev/sdb8        c2e3597f-fac7-45d9-9cae-888a24333c6c   swap       
/dev/sdb9        617d5dc9-a1df-43ed-b21e-859e4f7a0557   ext4       
/dev/sdc1        03B9-7FD7                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

=========================== sdb7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=874345ae-8ca3-491c-8db5-7ca668cb3f0d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=874345ae-8ca3-491c-8db5-7ca668cb3f0d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4398-2599
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 7EC4B2EFC4B2A8B3
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
--------------------------------------------------------------------------------

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=874345ae-8ca3-491c-8db5-7ca668cb3f0d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=c2e3597f-fac7-45d9-9cae-888a24333c6c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 324.353763580 = 348.272201728  boot/grub/core.img                             1
 256.394176483 = 275.301150720  boot/grub/grub.cfg                             1
 254.516601562 = 273.285120000  boot/initrd.img-2.6.38-8-generic               2
 324.352031708 = 348.270342144  boot/vmlinuz-2.6.38-8-generic                  1
 254.516601562 = 273.285120000  initrd.img                                     2
 324.352031708 = 348.270342144  vmlinuz                                        1

=========================== sdb9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos9)'
search --no-floppy --fs-uuid --set=root 617d5dc9-a1df-43ed-b21e-859e4f7a0557
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos9)'
search --no-floppy --fs-uuid --set=root 617d5dc9-a1df-43ed-b21e-859e4f7a0557
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos9)'
	search --no-floppy --fs-uuid --set=root 617d5dc9-a1df-43ed-b21e-859e4f7a0557
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=617d5dc9-a1df-43ed-b21e-859e4f7a0557 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos9)'
	search --no-floppy --fs-uuid --set=root 617d5dc9-a1df-43ed-b21e-859e4f7a0557
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=617d5dc9-a1df-43ed-b21e-859e4f7a0557 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos9)'
	search --no-floppy --fs-uuid --set=root 617d5dc9-a1df-43ed-b21e-859e4f7a0557
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos9)'
	search --no-floppy --fs-uuid --set=root 617d5dc9-a1df-43ed-b21e-859e4f7a0557
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4398-2599
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 7EC4B2EFC4B2A8B3
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=874345ae-8ca3-491c-8db5-7ca668cb3f0d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root 874345ae-8ca3-491c-8db5-7ca668cb3f0d
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=874345ae-8ca3-491c-8db5-7ca668cb3f0d ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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
--------------------------------------------------------------------------------

=============================== sdb9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=617d5dc9-a1df-43ed-b21e-859e4f7a0557 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=058ea482-66cd-43a9-9e9c-f875d757a015 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 220.646732330 = 236.917624832  boot/grub/core.img                             1
 138.706108093 = 148.934549504  boot/grub/grub.cfg                             1
 137.926757812 = 148.097728512  boot/initrd.img-2.6.38-8-generic               2
 220.645000458 = 236.915765248  boot/vmlinuz-2.6.38-8-generic                  1
 137.926757812 = 148.097728512  initrd.img                                     2
 220.645000458 = 236.915765248  vmlinuz                                        1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg sdh sdi 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Hedgehog1 on 2011-05-28
It appears you have installed Ubuntu several times on your PC:

```
/dev/sdb6         692,562,276   819,202,544   126,640,269  83 Linux
/dev/sdb7         495,388,672   690,470,911   195,082,240  83 Linux
/dev/sdb8         690,472,960   692,561,919     2,088,960  82 Linux swap / Solaris
``````

/dev/sdb9         286,287,872   493,295,615   207,007,744  83 Linux
/dev/sdb10        493,297,664   495,380,479     2,082,816  82 Linux swap / Solaris
```

This creates a very confusing Partition layout.

Would it be OK if we consolidated this down to a single install?

***The Hedge***

:KS

---

### Post by topdog2009 on 2011-05-28
I certainly installed an earlier version of Ubuntu (9.x) about 18 months ago but could not connect to the web using a USB stick - so I removed it.

I recently loaded the latest and greatest and had the problem of getting it to load so was advised to reinstall it - which I did.

We (or rather you - ;)) can certainly lead me into a consolidation which would make it work.

Brian

---

### Post by Hedgehog1 on 2011-05-28
OK - First a quick note that 'reinstall' means install-over-the-old install, but unless you know how to make the installer do that, you will get 'install another instance' of Ubuntu.

I am going to ask you to boot from your LiveCD/LiveUSB, select 'TRY' then then run the Gparted partition manager tool.

I would like you to right click on partitions /dev/sdb6 to /dev/sdb10 and mark them to be deleted. Be aware that the SWAP partition(s) may be in use, and you may have to select 'swapoff' in the right-click menu first, and then mark them to be deleted.

**If a partition says it is NTFS - DO NOT delete it** :D

Press the check mark button to make the deletes real.

Next, you need to create 3 partitions in gparted:

/dev/sda6 - ext4 '/' (root) about 20 gigs
/dev/sda7 - Linux swap (Size of RAM plus 10%
/dev/sda8 - ext4 '/home' all the space left on the disk.

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to the **Disk Space Allocation** screen.  

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda6 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-28
The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

Here is a view of the final layout of the partitions:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

[IMG]http://img97.imageshack.us/img97/8240/deathparionshishdd.png[/IMG]

---

### Post by topdog2009 on 2011-05-28
Thanks.

I have to sign off now. I will return to this tomorrow.

Brian

---

### Post by skeebs on 2011-05-28
This is a really unhelpful reply as I can't offer anything else, but is it vital you have both types of OS on your computer? If it's not needed then why not make life simpler and just have ubuntu? (told you it wasn't helpful as I've bet you've thought of that already :) )

---

### Post by Hedgehog1 on 2011-05-28
Skeebs - If someone really does not need to dual boot, then it is much simple to install Ubuntu by itself:

/dev/sda1 - EXT 4 '/' (root)
/dev/sda2 - EXT 4 '/Home'
/dev/sda3 - Swap

But, almost everyone I know has to run some Windows applications for work, or they have a few key Windows programs with no Linux equivalent (yet).

***The Hedge***

:KS

---

### Post by skeebs on 2011-05-28
> **Hedgehog1 said:**
> or they have a few key Windows programs with no Linux equivalent (yet).



oh yeah! Forgot about that! :lol:

---

### Post by topdog2009 on 2011-05-29
Hi Hedgehog

Starting to delete partitions and getting ready to make new ones. You indicate using /dev/sda rather than /dev/sdb 

I want to confirm that before doing it. I have two hard drives in my computer, The initial drive was giving me grief so a new drive (500gb) was installed. To the best of my knowledge, the computer boots to this new drive which is where I want Ubuntu installed. Please check my initial posts that describe what i think is going on.

Thanks

Brian

---

### Post by oldfred on 2011-05-29
I do not think Hedgehog1 has his nice screen shots for every configuration. 

Not sure how soon he may be back, but to confirm your Ubuntu installs are in sdb. The highest number is sda6 on your sda drive and be sure not to delete any of those sda partitions.

---

### Post by topdog2009 on 2011-05-29
Thanks - I realise that Ubuntu was on sdb (it is now gone the way of the do do bird, my problem is knowing what to do with the next step i.e. partitioning. Hedgehog indicated it should be sda but I think i should be on sdb. That being said, if I partition sdb instead of sda does everything else in the response from Hedgehog have to refer to sdb and not sda.

I am patient, I can wait,

Thanks again

Brian

---

### Post by oldfred on 2011-05-29
I copy & paste most of my responses as I find the same questions. So I often have the wrong partitions. If you want to reinstall to sdb then you need to use sdb. 

One thing we have found is that you do have to pay attention to what drive is what as a few systems change drive letters on reboot. This seems to happen a lot on mixed IDE/SATA systems and some BIOS promote a Flash drive to sda and confuse drive numbering.

---

### Post by Hedgehog1 on 2011-05-30
Thanks oldfred!  

This weekend is:

* Formula 1 in Monte Carlo
* INDY 500
* Nascar 600
* Rolex Sportscar Series

Somehow, the forums have to take a back seat for a few days :D

My DVR is calling....

***The 'Motor-Sports-Nut' Hedge***

:KS

---

