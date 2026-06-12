---
title: "Windows XP / Ubuntu 11.04 dual boot problem - windows won't boot"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by brugelfresh on 2012-01-05
Hi, 

I installed Ubuntu 11.04 recently and now Windows XP won't boot. I've tried editing the Grub 2 boot script but I don't really know what I'm doing so I need some help.

I had XP installed in a partition that windows designated as the D: drive and a small amount of memory formatted to fat32 that was designated as the C: drive. The C: drive may have had some files of an older windows installation on it and perhaps this confused the Ubuntu installation. Also no free partition showed up in the installation menu where you choose where to install Ubuntu. Another partition F: drive, formatted to NTFS, was just free space so I deleted this partition hoping to install Ubuntu onto this. After this, the ubuntu installation CD chose the installation destination automatically and everything seemed fine. But then when I tried to select the Windows XP option in the grub menu it wouldn't boot.

I have a 2nd hard drive (G: ) where I keep more files etc. This was plugged in at the time of the Ubuntu installation.

Can someone please tell me how I might alter the Grub script to get XP to boot?

Here are the results of a boot info script program:

 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *    380,756,565   412,305,392    31,548,828  1c Hidden W95 FAT32 (LBA)
/dev/sda2         412,308,286 1,465,127,999 1,052,819,714   f W95 Extended (LBA)
/dev/sda5         412,308,288 1,465,127,999 1,052,819,712   7 NTFS / exFAT / HPFS
/dev/sda3               2,048   372,371,455   372,369,408  83 Linux
/dev/sda4         372,371,456   380,755,967     8,384,512  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/ramzswap0                                          swap       
/dev/sda1        2537-14F5                              vfat       OLD SECTION
/dev/sda3        d9fcdbe9-6864-44b1-8824-d7b819fe7597   ext4       
/dev/sda4        d8a4fdb4-1e4b-468d-aac9-67205b028cad   swap       
/dev/sda5        8EA489C4A489AF71                       ntfs       Nerve Centre
/dev/sdb1        4ED80930D80917BB                       ntfs       Big Daddy

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/Nerve Centre      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
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
menuentry 'Ubuntu, with Linux 2.6.38-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    linux    /boot/vmlinuz-2.6.38-12-generic-pae root=UUID=d9fcdbe9-6864-44b1-8824-d7b819fe7597 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    echo    'Loading Linux 2.6.38-12-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-12-generic-pae root=UUID=d9fcdbe9-6864-44b1-8824-d7b819fe7597 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=d9fcdbe9-6864-44b1-8824-d7b819fe7597 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=d9fcdbe9-6864-44b1-8824-d7b819fe7597 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d9fcdbe9-6864-44b1-8824-d7b819fe7597 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d9fcdbe9-6864-44b1-8824-d7b819fe7597 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root d9fcdbe9-6864-44b1-8824-d7b819fe7597
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2537-14f5
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d9fcdbe9-6864-44b1-8824-d7b819fe7597 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=d8a4fdb4-1e4b-468d-aac9-67205b028cad none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 174.146354675 = 186.988224512  boot/grub/core.img                             1
   0.197475433 = 0.212037632    boot/grub/grub.cfg                             1
   2.630126953 = 2.824077312    boot/initrd.img-2.6.38-12-generic              3
   2.698482513 = 2.897473536    boot/initrd.img-2.6.38-12-generic-pae          3
   2.657226562 = 2.853175296    boot/initrd.img-2.6.38-8-generic               3
   1.802066803 = 1.934954496    boot/vmlinuz-2.6.38-12-generic                 1
   1.056095123 = 1.133973504    boot/vmlinuz-2.6.38-12-generic-pae             2
   2.223937988 = 2.387935232    boot/vmlinuz-2.6.38-8-generic                  1
   2.657226562 = 2.853175296    initrd.img                                     3
   2.630126953 = 2.824077312    initrd.img.old                                 3
   2.223937988 = 2.387935232    vmlinuz                                        1
   1.802066803 = 1.934954496    vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by darkod on 2012-01-05
Was XP always installed on a logical partition? It seems to be on /dev/sda5 which is a logical partition. Usually windows installs on a primary partition although it can work from a logical as far as the boot files are on a primary.

The entry in boot.ini says partition(2) which could be right, but could be wrong too. Number 2 is the extended partition, not sure if windows would refer to /dev/sda5 as 2 or 5. You can try editing the boot.ini and changing it to partition(5) to see what happens.

---

### Post by brugelfresh on 2012-01-06
Thanks Darko, that was a great tip. Once I figured out how to find the boot.ini file (in the Ubuntu OS the drive was hidden for some reason so I used Gparted to unhide it) I just opened it in a simple text program and changed the partition number - 5 didn't work, so I tried 3, then 4, and 4 was the winner. Not sure what system Windows uses to number the partitions, but I'll changed the thread to solved. 
 
Thanks again!

---

