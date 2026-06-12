---
title: "can't boot to windows after upgrading to 10.04 lts"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by gdawgster on 2010-06-04
I'm a total novice and I've upgraded to 10.04 and now although windows is shown on the grub loader if I select it all I get is a blinking cursor and windows will not load Ubuntu loads fine and is the default. Any help appreciated!
Gary

---

### Post by darkod on 2010-06-04
Unless you know for sure which is your windows partition, run the boot info script as explained here to show us that first:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of the results file as explained.

---

### Post by gdawgster on 2010-06-04
Thanks for the quick reply, I hope this is what's needed?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 270879 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows XP
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 270879 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   206,097,884   206,097,822   7 HPFS/NTFS
/dev/sda2         206,097,885   321,669,494   115,571,610   f W95 Ext d (LBA)
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,687,184   964,687,122  83 Linux
/dev/sdb2         964,687,185   976,768,064    12,080,880   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8074 MB, 8074035200 bytes
72 heads, 7 sectors/track, 31288 cylinders, total 15769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  24    15,769,599    15,769,576   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8074 MB, 8074035200 bytes
72 heads, 7 sectors/track, 31288 cylinders, total 15769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  24    15,769,599    15,769,576   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B8689A226899E004                       ntfs       office2                       
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ed6a4de8-692f-4c7b-9b43-e3d200be3d28   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        66f7c47d-37a1-4086-ae09-007490669de0   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0002-DA2E                              vfat       KINGSTON                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        3433-3231                              vfat       MOVIES                        
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /media/MOVIES            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ed6a4de8-692f-4c7b-9b43-e3d200be3d28 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ed6a4de8-692f-4c7b-9b43-e3d200be3d28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=ed6a4de8-692f-4c7b-9b43-e3d200be3d28 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=ed6a4de8-692f-4c7b-9b43-e3d200be3d28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ed6a4de8-692f-4c7b-9b43-e3d200be3d28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b8689a226899e004
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=ed6a4de8-692f-4c7b-9b43-e3d200be3d28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=66f7c47d-37a1-4086-ae09-007490669de0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  19.5GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.31-20-generic-pae
   2.4GB: boot/initrd.img-2.6.32-22-generic-pae
    .5GB: boot/vmlinuz-2.6.31-20-generic-pae
    .8GB: boot/vmlinuz-2.6.32-22-generic-pae
   2.4GB: initrd.img
    .8GB: vmlinuz

```

---

### Post by oldfred on 2010-06-04
When the instructions said all drives they meant sda, sdb etc not partitions sda1, sda2 sdb1 etc. You overwrote the windows boot sector in the windows partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by darkod on 2010-06-04
Just to add to what oldfred said, you need to apply the fix from his first link on /dev/sda1 partition. So, that's partition #1 on disk /dev/sda.

After that windows should boot fine.

It seems you have extra boot files on the windows partition too, but first get rid of grub2 on it, we'll see later of anything more is needed.

---

### Post by gdawgster on 2010-06-04
Thanks! easiest fix I've ever tackled!

---

### Post by gdawgster on 2010-06-04
> **darkod said:**
> Just to add to what oldfred said, you need to apply the fix from his first link on /dev/sda1 partition. So, that's partition #1 on disk /dev/sda.

After that windows should boot fine.

It seems you have extra boot files on the windows partition too, but first get rid of grub2 on it, we'll see later of anything more is needed.

My first outing with Ubuntu I installed to a new partition on my 160 gig hardrive and then uninstalled since then I haven't been able to "merge" the two partitions back together that may be what you are seeing. Do you guys know of a fix for that? [-o<

---

### Post by oldfred on 2010-06-04
I always create partitions in advance with gparted from a Ubuntu liveCD or gparted liveCD. Then you can edit, destroy or add partitions at will. I try to plan what partitions I will need now and in the near future but recognize my needs change over time and may want more changes later.
Besure to have good backups before any partition changing. While there is not a huge risk of loss of data some times we make a mistake and delete something we really did not want to delete and rarely drives corrupt some data.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by gdawgster on 2010-06-04
thanks oldfred
I'll take a look at that.

---

### Post by darkod on 2010-06-04
> **gdawgster said:**
> My first outing with Ubuntu I installed to a new partition on my 160 gig hardrive and then uninstalled since then I haven't been able to "merge" the two partitions back together that may be what you are seeing. Do you guys know of a fix for that? [-o<

The windows boot files I am talking about have nothing to do with ubuntu, or how many times you installed it or where.

This is from your results file before you repaired your partition boot sector:

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 270879 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:[COLOR=Blue]   /boot.ini[/COLOR] /bootmgr /Boot/BCD [COLOR=Blue]/ntldr /NTDETECT.COM[/COLOR]

If things work as they are, don't bother with it right now. But I was just thinking aloud because only the files in blue above are from XP. One explanation might be that you also had vista or 7 in addition to XP and the boot files got combined. After removing the other version, /bootmgr and /boot/BCD stayed there.

As I said, if it works, leave it as it is at the moment. I was just wondering what the other two files are doing there.

---

