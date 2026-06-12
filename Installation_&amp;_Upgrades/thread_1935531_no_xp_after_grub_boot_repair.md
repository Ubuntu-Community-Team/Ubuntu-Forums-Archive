---
title: "no xp after grub boot repair"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by panronnie on 2012-03-04
after installing a second sata disk 1 terabyte and installing ubuntu on it 
 i can no longer boot win xp on the orginal sata drive 130 gig 
also during installing ubuntu xp was never detected 
the xp drive is first in bios boot 
i have run boot repair to fix it and used of the advanced settings MBR fix on sda 
that got me to boot win xp again but without the grub2 window/choice menu 
booting from the cd and installing/running boot repair fixes ubuntu and the grub startup but 
without win xp again 
kind off out  idea,s here  :popcorn:

---

### Post by raja.genupula on 2012-03-04
do ```
sudo update-grub
```
what its giving ?

please post the output of bootinfoscript(in my signature) .
thank you .

---

### Post by panronnie on 2012-03-04
[sudo] password for ronald: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done
ronald@ronald-desktop:~$

---

### Post by darkod on 2012-03-04
There seems to be some corruption or error in finding your XP boot files. If ubuntu can't detect them, it doesn't create a boot entry.

In your case it's best to run the boot info script as described in the link in my signature. It will show more details about the boot and the OSs, including boot files. You can post the results as explained there.

---

### Post by panronnie on 2012-03-05
boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/mapper/pdc_bjijacfeh...
Searching sda1 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching pdc_bjijacfeh1 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ronald/".

ronald@ronald-desktop:~$ 

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/pdc_bjijacfeh and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 1 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Apparaat of hulpbron is bezig
fuse: mount failed: Apparaat of hulpbron is bezig

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_bjijacfeh1: ________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cilinders, totaal 240121728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   240,091,424   240,091,362   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,949,331,455 1,949,329,408  83 Linux
/dev/sdb2       1,949,333,502 1,953,523,711     4,190,210   5 Extended
/dev/sdb5       1,949,333,504 1,953,523,711     4,190,208  82 Linux swap / Solaris


Drive: pdc_bjijacfeh _____________________________________________________________________

Disk /dev/mapper/pdc_bjijacfeh: 122.9 GB, 122942259200 bytes
255 koppen, 63 sectoren/spoor, 14946 cilinders, totaal 240121600 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_bjijacfeh1   *             63   240,091,424   240,091,362   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6C74A7BD74A78902                       ntfs       
/dev/sdb1        e299110f-7241-4946-8579-f0a5f1fc3c1d   ext4       
/dev/sdb5        12b614f1-1453-4d83-b689-28a5bedcb086   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=e299110f-7241-4946-8579-f0a5f1fc3c1d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=e299110f-7241-4946-8579-f0a5f1fc3c1d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e299110f-7241-4946-8579-f0a5f1fc3c1d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e299110f-7241-4946-8579-f0a5f1fc3c1d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root e299110f-7241-4946-8579-f0a5f1fc3c1d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e299110f-7241-4946-8579-f0a5f1fc3c1d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=12b614f1-1453-4d83-b689-28a5bedcb086 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 770.133533478 = 826.924584960  boot/grub/core.img                             1
 770.135238647 = 826.926415872  boot/grub/grub.cfg                             1
   1.177890778 = 1.264750592    boot/initrd.img-3.0.0-12-generic               1
   1.811107635 = 1.944662016    boot/initrd.img-3.0.0-16-generic               8
 770.133441925 = 826.924486656  boot/vmlinuz-3.0.0-12-generic                  1
   1.235767365 = 1.326895104    boot/vmlinuz-3.0.0-16-generic                  1
   1.811107635 = 1.944662016    initrd.img                                     8
   1.811107635 = 1.944662016    initrd.img.old                                 8
   1.235767365 = 1.326895104    vmlinuz                                        1
   1.235767365 = 1.326895104    vmlinuz.old                                    1

=========================== pdc_bjijacfeh1/boot.ini: ===========================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error

---

### Post by darkod on 2012-03-05
The XP disk has a raid meta data leftover. It was used in raid earlier. You can remove this meta data by running in ubuntu in terminal:
sudo dmraid -E -r /dev/sda

After that do the:
sudo update-grub

again. If the above dmraid command complains that it can't find it, run it from ubuntu live mode, it is included in live mode.

---

### Post by panronnie on 2012-03-05
problem solved
thank you veeeeeeeeeeeery much :D

---

