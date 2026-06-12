---
title: "Ubuntu 11.04 boots to Busybox in Dual Boot  with multiple drive system"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by joearein on 2011-05-19
I have been struggling for a week with various installation techniques without complete success. Internet searches have provided part of the answer but not a complete solution. :(

I have an IBM xSeries eServer with windows installed on the primary IDE drive C (sda1). 
I have 5 SCSI drives associated with windows E: F: G: H: I:
I have installed UBUNTU 11.04 on SCSI drive sdb (J) with two partitions sdb1(/) and sdb2 (swap)
Grub boot loader is installed on sda1 (c)

When I boot I get a good boot menu giving the choice of windows XP, Ubuntu and various ubuntu options.
Selecting Windows results in a good boot of windows XP.
Selecting Ubuntu results in a blank screen for 60 + seconds and than the BusyBox shell appears.
If I type EXIT at the busybox prompt a good boot of Ubuntu results.

Can anyone offer suggestions how to rid myself of the BusyBox prompt?

Below are the results given by Boot_Info_script.sh

  ```
               Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid e5af79e3-88a0-4c36-b962-fca58e4a743b root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/sdf.
 => Windows is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    58,593,279    58,591,232  83 Linux
/dev/sdb2          58,593,280    71,094,271    12,500,992  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 36.4 GB, 36420075008 bytes
255 heads, 63 sectors/track, 4427 cylinders, total 71132959 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    71,119,754    71,119,692   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63    71,087,624    71,087,562   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63    71,087,624    71,087,562   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63    71,087,624    71,087,562   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1                  63    71,087,624    71,087,562   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FCA0BE3CA0BDFD68                       ntfs       
/dev/sdb1        e5af79e3-88a0-4c36-b962-fca58e4a743b   ext4       
/dev/sdb2        aa05a875-1513-4300-94a8-f3b6c2a18e30   swap       
/dev/sdc1        12F09244F0922DCB                       ntfs       Disk 2
/dev/sdd1        5010A45F10A44DB2                       ntfs       Drive 3
/dev/sde1        5C84996484994206                       ntfs       Drive 4
/dev/sdf1        2A24ED2E24ECFDA7                       ntfs       Drive 5
/dev/sdg1        642C72462C721372                       ntfs       Drive 6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=60 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

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
set default="Microsoft Windows XP Professional (on /dev/sda1)"
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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e5af79e3-88a0-4c36-b962-fca58e4a743b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280 x 1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e5af79e3-88a0-4c36-b962-fca58e4a743b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root FCA0BE3CA0BDFD68
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/10_os-prober ###

### BEGIN /etc/grub.d/20_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e5af79e3-88a0-4c36-b962-fca58e4a743b
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=e5af79e3-88a0-4c36-b962-fca58e4a743b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e5af79e3-88a0-4c36-b962-fca58e4a743b
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=e5af79e3-88a0-4c36-b962-fca58e4a743b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/20_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e5af79e3-88a0-4c36-b962-fca58e4a743b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e5af79e3-88a0-4c36-b962-fca58e4a743b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/30_memtest86+ ###

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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e5af79e3-88a0-4c36-b962-fca58e4a743b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=aa05a875-1513-4300-94a8-f3b6c2a18e30 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.224636078 = 21.716037632   boot/grub/core.img                             1
   8.200565338 = 8.805289984    boot/grub/grub.cfg                             1
   3.880088806 = 4.166213632    boot/initrd.img-2.6.38-8-generic-pae           1
   3.032653809 = 3.256287232    boot/vmlinuz-2.6.38-8-generic-pae              1
   3.880088806 = 4.166213632    initrd.img                                     1
   3.032653809 = 3.256287232    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```Any and all suggestions are welcome. Thanks in advance.:)

---

### Post by joearein on 2011-05-20
In desperation I decided to try something that had no reasonable chance of success; BUT IT WORKED. 

I physically removed all drives from the server accept the Windows C: drive and the Ubuntu sdb drive.
I then did the following.
1) Booted to ubuntu and was taken to the Grub Rescue prompt. :(
2) Did a hard reset of the server forcing a boot sequence.
3) Successfully booted to windows xp. :p
3) Shut down windows xp gracefully and started a new boot sequence
4) Successfully booted to ubuntu :p
5) Shut down ubuntu gracefully and powered off the server.
6) Reinstalled the five drives that I removed earlier and powered on the system 
7) Successfully booted to ubuntu. 8) 
8) Shut down ubuntu and started another boot sequence.
9) Successfully booted to windows xp

DUAL BOOT SYSTEM NOW WORKS AS IT SHOULD; BUT DON'T ASK ME WHY!!!:popcorn:

---

