---
title: "GRUB failing me"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Atraitus on 2010-11-11
Alright, so after having fiddled with this for the better part of 24 hours and having exhausted Google and this forum, I decided to post my own thread.  Here's a bit of background on my issue:

For about a year now, I've been running Windows 7 on a lone SATA HDD.  A couple of days ago, I threw in an IDE HDD that I had laying around, to put 10.10 on it.  I formatted it and installed, everything happened normally (except that to see the drive I had to turn off dmraid from the Live CD, not sure what was going on there).  It all worked fine, so I rebooted to the install.  GRUB booted to Ubuntu just fine, so I restarted to see if I could still boot to 7.  That didn't work so well; the GRUB menu disappeared and a flashing cursor appeared on my screen, with my HDD light constantly on.  No Windows boot.  I tried uninstalling and reinstalling GRUB, I tried to restore my Windows 7 bootloader, etc.  Everything failed on some stage, and GRUB slowly degraded to the point of utter unusability.  Now when I boot I just get a GRUB prompt (which I don't really know how to use; I'm a fairly casual Ubuntu user).  I'm posting from the Live CD right now, and can't boot to either OS.  I've tried GRUB legacy and GRUB 2 both, with no results.  As I'm sure will be requested, here's the current results of the boot info script: 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/boot/grub.
 => Grub 2 is installed in the MBR of /dev/mapper/nvidia_bdagjddb and looks on 
    the same drive in partition #1 for (,msdos1)/boot/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

nvidia_bdagjddb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

nvidia_bdagjddb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   300,292,095   300,290,048  83 Linux
/dev/sda2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sda5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   625,139,711   624,932,864   7 HPFS/NTFS


Drive: nvidia_bdagjddb ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_bdagjddb: 320.1 GB, 320072908800 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_bdagjddb1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/nvidia_bdagjddb2            206,848   625,139,711   624,932,864   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_bdagjddb1 8A68E76B68E7548B                       ntfs       System Reserved               
/dev/mapper/nvidia_bdagjddb2 DE144F13144EEDD9                       ntfs                                     
/dev/mapper/nvidia_bdagjddb: PTTYPE="dos" 
/dev/sda1        81d4055b-7399-4138-b9bc-ce87634d60d9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3571b564-81a2-485c-b2ea-b2807d3aea41   swap                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        8A68E76B68E7548B                       ntfs       System Reserved               
/dev/sdb2        DE144F13144EEDD9                       ntfs                                     
/dev/sdb                                                nvidia_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 81d4055b-7399-4138-b9bc-ce87634d60d9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 81d4055b-7399-4138-b9bc-ce87634d60d9
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 81d4055b-7399-4138-b9bc-ce87634d60d9
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=81d4055b-7399-4138-b9bc-ce87634d60d9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 81d4055b-7399-4138-b9bc-ce87634d60d9
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=81d4055b-7399-4138-b9bc-ce87634d60d9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 81d4055b-7399-4138-b9bc-ce87634d60d9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 81d4055b-7399-4138-b9bc-ce87634d60d9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=81d4055b-7399-4138-b9bc-ce87634d60d9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3571b564-81a2-485c-b2ea-b2807d3aea41 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  38.7GB: boot/grub/core.img
 116.1GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  38.7GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  38.7GB: vmlinuz
```

I'm about to give up and reinstall Windows 7, resulting in a loss of data.  Hopefully you gurus can aid a relative newcomer.

---

### Post by psusi on 2010-11-11
You appear to have leftover fakeraid signatures on the drives from past use in an nvidia and promise fakeraid controller.  You need to remove those.  Run sudo dmraid -E /dev/sda /dev/sdb.

---

### Post by Atraitus on 2010-11-11
> **psusi said:**
> You appear to have leftover fakeraid signatures on the drives from past use in an nvidia and promise fakeraid controller.  You need to remove those.  Run sudo dmraid -E /dev/sda /dev/sdb.

I just gave that a try, it spit back the following:

```
ERROR: option missing/invalid option combination with -E
```

I noticed there were leftover signatures when I installed; it wouldn't see the drives unless I disabled dmraid.  I wasn't sure what to do about that, so I disabled dmraid and installed.

---

### Post by psusi on 2010-11-11
Ohh, yea, you need to do one disk at a time; can't put both into the same command.

---

### Post by Atraitus on 2010-11-13
Alright, problem solved.  I ran ```
sudo dmraid -E /dev/sda
``` and ```
sudo dmraid -E /dev/sdb
```.  Then I reinstalled Win7, then reinstalled 10.10, and GRUB works out of the box now.

---

