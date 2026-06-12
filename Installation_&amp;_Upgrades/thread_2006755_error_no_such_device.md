---
title: "error: no such device"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by xabilo on 2012-06-19
I successfully installed Ubuntu 12.04 using the 3rd method of partitions. I created them myself: everything on my SSD of 80 GB (not touching my 2nd internal drive of 1 TB). So: /dev/sda1 : ntfs : 42000 MB : that contains windows 7.
/dev/sda2 : swap : 4613 MB
/dev/sda3 : ext4 : / (my root dir) : 4614 MB
/dev/sda4 : ext4 : /home : 28797 MB

After I got some software updates, I was told by the system that I only had 189 MB left in my root directory. And the available space kept shrinking by using Firefox, etc. Then I decided to enlarge my root directory with the build-in partition program of the Live CD of Ubuntu 12.04 (AMD64). I removed the root and the home partition, and created the new partitions
/dev/sda3 : ext4 : / (root) : 14000 MB
/dev/sda4 : ext4 : /home : 19408 MB

When i restarted my PC, I got this message:
```
error: no such device: b4fc040a-...
grub rescue>
```

I've already done some research on Grub2 and Grub Rescue, and also done the command
ls
and it gives: (hd0) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos4) (hd1,msdos3) (hd1,msdos2) (hd1,msdos1) (fd0)
When I tried the command
ls (hd1,msdos3)
it gives: error: bad filename
ls (hd1,msdos4)
it gives: error: bad filename

I also have the results file of bootinfoscript:

                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and uses an
    embedded config file:
   
    ---------------------------------------------------------------------------
    search.fs_uuid b4fc040a-a8ad-4e87-a944-9517e40c8985 root
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:      
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3
                       and looks at sector 113237976 of the same hard drive
                       for core.img. core.img is at this location and looks
                       for (,msdos3)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System: 
    Boot files:       

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:       

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    82,033,297    82,031,250   7 NTFS / exFAT / HPFS
/dev/sda2          82,034,688    91,046,405     9,011,718  82 Linux swap / Solaris
/dev/sda3          91,047,936   118,390,783    27,342,848  83 Linux
/dev/sda4         118,390,784   156,301,311    37,910,528  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   242,394,347   242,187,500   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs  
/dev/sda1        341E3B4A1E3B0500                       ntfs      
/dev/sda3        a7a74f33-6aa3-43f9-bd98-e72afeca238e   ext4      
/dev/sda4        4ba7c8d9-7dd6-45af-8243-66c17fbe8f62   ext4      
/dev/sdb1        BC80392F8038F20E                       ntfs       Door systeem gereserveerd
/dev/sdb2        DE4684D74684B1B7                       ntfs       Data
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/a7a74f33-6aa3-43f9-bd98-e72afeca238e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root a7a74f33-6aa3-43f9-bd98-e72afeca238e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root a7a74f33-6aa3-43f9-bd98-e72afeca238e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root a7a74f33-6aa3-43f9-bd98-e72afeca238e
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=a7a74f33-6aa3-43f9-bd98-e72afeca238e ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root a7a74f33-6aa3-43f9-bd98-e72afeca238e
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=a7a74f33-6aa3-43f9-bd98-e72afeca238e ro recovery nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root a7a74f33-6aa3-43f9-bd98-e72afeca238e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root a7a74f33-6aa3-43f9-bd98-e72afeca238e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root BC80392F8038F20E
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a7a74f33-6aa3-43f9-bd98-e72afeca238e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=4ba7c8d9-7dd6-45af-8243-66c17fbe8f62 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
#UUID=092ac53c-b349-45f2-bf3a-2b8364598192 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               1
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

"Door systeem gereserveerd" means "Reserved by the system".

It is clearly shown in this script that all the required files for Ubuntu reside in dev/sda3 (hd1,msdos3). No menu is shown when booting the PC. So this can only be solved using Grub Rescue, I assume. What is the correct order of the commands that I need to give?

---

### Post by wilee-nilee on 2012-06-19
Couple of problems, you have part of the windows boot on sdb.
**sdb1: **__________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:        **/bootmgr /Boot/BCD**

This should be in the sda1 partition.

Is the sda HD set as the first read HD in the bios?

You have grub in both HD's mbr's

---

### Post by darkod on 2012-06-19
When you delete the partition and create a new one, it's created with a new UUID and it doesn't match any more.

Boot with the ubuntu cd in live mode, open terminal and execute:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart. Go into BIOS and make sure the SSD is first in the boot order, not the HDD.

Note that you will still continue to have a broken grub2 on the HDD so if you ever try to boot from it it will give you an error. If you would like to add grub2 to the MBR of the HDD too, when doing the above commands from live mode execute this one too:
```
sudo grub-install --root-directory=/mnt /dev/sdb
```

That will install grub2 to both /dev/sda and /dev/sdb so in reality it doesn't matter which one you boot first.

---

### Post by darkod on 2012-06-19
> **wilee-nilee said:**
> Couple of problems, you have part of the windows boot on sdb.
**sdb1: **__________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:        **/bootmgr /Boot/BCD**

This should be in the sda1 partition.

Is the sda HD set as the first read HD in the bios?

You have grub in both HD's mbr's

This is rare, but not a problem on itself. Windows always puts the boot files where the boot flag is, so I guess the boot flag was on sdb1 and the boot files were copied there, while the system partition for windows is still sda1.
It should work fine as long as you have both disks in your system.
If in future you take away the HDD for example, win7 will stop booting.

---

### Post by wilee-nilee on 2012-06-19
> **darkod said:**
> This is rare, but not a problem on itself. Windows always puts the boot files where the boot flag is, so I guess the boot flag was on sdb1 and the boot files were copied there, while the system partition for windows is still sda1.
It should work fine as long as you have both disks in your system.
If in future you take away the HDD for example, win7 will stop booting.

As a rephrase that is a problem waiting to happen, especially for an unaware user. ;)

---

### Post by xabilo on 2012-06-19
> **darkod said:**
> When you delete the partition and create a new one, it's created with a new UUID and it doesn't match any more.

Boot with the ubuntu cd in live mode, open terminal and execute:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Restart. Go into BIOS and make sure the SSD is first in the boot order, not the HDD.

Note that you will still continue to have a broken grub2 on the HDD so if you ever try to boot from it it will give you an error. If you would like to add grub2 to the MBR of the HDD too, when doing the above commands from live mode execute this one too:
```
sudo grub-install --root-directory=/mnt /dev/sdb
```That will install grub2 to both /dev/sda and /dev/sdb so in reality it doesn't matter which one you boot first.

Thanks very much, Darko. Ok, that solved the problem. I installed grub2 to both /dev/sda and /dev/sdb. So I didn't have to go into the BIOS. 

Before I've read your answers, I checked out the thread [http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980) and saw the screenshot of Boot Repair with the button 'Recommended Repair', and in answer 8, there's another screenshot 'Repair the boot of the computer' : OS to boot by default, etc. I was able to burn the downloaded ISO with Brasero while running Ubuntu 12.04 off the live CD. Just wondering if that also would have solved my problem.

---

### Post by wilee-nilee on 2012-06-19
> **xabilo said:**
> Thanks very much, Darko. Ok, that solved the problem. I installed grub2 to both /dev/sda and /dev/sdb. So I didn't have to go into the BIOS. 

Before I've read your answers, I checked out the thread [http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980) and saw the screenshot of Boot Repair with the button 'Recommended Repair', and in answer 8, there's another screenshot 'Repair the boot of the computer' : OS to boot by default, etc. I was able to burn the downloaded ISO with Brasero while running Ubuntu 12.04 off the live CD. Just wondering if that also would have solved my problem.

This is the sort of answer which had me warning about the problems that could happen.

When you half fix stuff, you are in more danger later trying to figure out what you have done instead of getting the basic skills together to understand where you're at now and setting this up correctly.

It may work, but it is not really correct, and you don't really understand why.

---

### Post by YannBuntu on 2012-06-20
Hi 
For information, Boot-Repair here would:
1) reinstall GRUB in both MBRs (=darkod's suggestion which solved the problem)
2) and copy the /bootmgr /Boot/BCD on sda1 (which would solve the "problem waiting to happen" ;) ).

---

### Post by xabilo on 2012-06-20
> **wilee-nilee said:**
> This is the sort of answer which had me warning about the problems that could happen.

When you half fix stuff, you are in more danger later trying to figure out what you have done instead of getting the basic skills together to understand where you're at now and setting this up correctly.

It may work, but it is not really correct, and you don't really understand why.

I'm even more confused now. I explain what I've done: 

Boot with the ubuntu cd in live mode, open terminal and execute:
 
sudo mount /dev/sda3 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --root-directory=/mnt /dev/sdb

and I restarted my PC. The menu appeared with Ubuntu on top, and could access and use Ubuntu.

Jimmy

---

