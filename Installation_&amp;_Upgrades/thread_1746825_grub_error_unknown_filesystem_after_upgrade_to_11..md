---
title: "grub error: unknown filesystem after upgrade to 11.04"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by endintears on 2011-05-02
Hi all,

I tried upgrading to 11.04 this morning and after rebooting grub left me at the grub rescue> prompt with the message 'error: unknown filesystem'.

I've tried purging and reinstalling grub using a live-cd but no joy.

Let me know what additional information to provide.

EDIT: Here is the output from the Boot Info Script

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for cbdc4.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for cbdc4.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdb2         204,796,620   586,083,329   381,286,710   f W95 Ext d (LBA)
/dev/sdb5         204,796,683   586,083,329   381,286,647   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000215724032 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953546336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sdd2         102,398,371 1,953,546,239 1,851,147,869   f W95 Ext d (LBA)
/dev/sdd5         102,398,373   687,906,292   585,507,920   7 HPFS/NTFS
/dev/sdd6         687,906,816 1,941,469,183 1,253,562,368  83 Linux
/dev/sdd7       1,941,471,232 1,953,546,239    12,075,008  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9638717038714FEB                       ntfs       TV                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        30902D2C902CF9CC                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        A820C8C120C897A8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8638549738548857                       ntfs       Backup                        
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        84D0C477D0C4714A                       ntfs       System                        
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        ECB61007B60FD14E                       ntfs       Data                          
/dev/sdd6        8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8   ext4                                     
/dev/sdd7        7262bb4e-a300-48a9-b9b3-5d8982d54760   swap                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd6        /media/8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sdd1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /3GB 

=========================== sdd6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdd,msdos6)'
search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos6)'
search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
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
    set root='(/dev/sdd,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdd1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 84D0C477D0C4714A
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

=============================== sdd6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd6 during installation
UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd7 during installation
UUID=7262bb4e-a300-48a9-b9b3-5d8982d54760 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd6: Location of files loaded by Grub: ===================


 500.5GB: boot/grub/core.img
 500.5GB: boot/grub/grub.cfg
 764.5GB: boot/initrd.img-2.6.35-28-generic
 766.5GB: boot/initrd.img-2.6.38-8-generic
 399.9GB: boot/vmlinuz-2.6.35-28-generic
 764.6GB: boot/vmlinuz-2.6.38-8-generic
 766.5GB: initrd.img
 764.5GB: initrd.img.old
 764.6GB: vmlinuz
 399.9GB: vmlinuz.old
```

---

### Post by endintears on 2011-05-02
Here's the output from the more up to date BIS:

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    -----
    search.fs_uuid 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    -----
    search.fs_uuid 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdd6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sdb2         204,796,620   586,083,329   381,286,710   f W95 Extended (LBA)
/dev/sdb5         204,796,683   586,083,329   381,286,647   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000215724032 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953546336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sdd2         102,398,371 1,953,546,239 1,851,147,869   f W95 Extended (LBA)
/dev/sdd5         102,398,373   687,906,292   585,507,920   7 NTFS / exFAT / HPFS
/dev/sdd6         687,906,816 1,941,469,183 1,253,562,368  83 Linux
/dev/sdd7       1,941,471,232 1,953,546,239    12,075,008  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9638717038714FEB                       ntfs       TV
/dev/sdb1        30902D2C902CF9CC                       ntfs       
/dev/sdb5        A820C8C120C897A8                       ntfs       
/dev/sdc1        8638549738548857                       ntfs       Backup
/dev/sdd1        84D0C477D0C4714A                       ntfs       System
/dev/sdd5        ECB61007B60FD14E                       ntfs       Data
/dev/sdd6        8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8   ext4       
/dev/sdd7        7262bb4e-a300-48a9-b9b3-5d8982d54760   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd6        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sdd1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /3GB 
--------------------------------------------------------------------------------

=========================== sdd6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8
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
--------------------------------------------------------------------------------

=============================== sdd6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd6 during installation
UUID=8ccc99da-e4ef-4db3-a8d0-e5e74e9bb3b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd7 during installation
UUID=7262bb4e-a300-48a9-b9b3-5d8982d54760 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 466.164344788 = 500.540153856  boot/grub/core.img                             1
 466.167980194 = 500.544057344  boot/grub/grub.cfg                             1
 712.069732666 = 764.579053568  boot/initrd.img-2.6.35-28-generic              2
 713.898643494 = 766.542831616  boot/initrd.img-2.6.38-8-generic               2
 372.472446442 = 399.939244032  boot/vmlinuz-2.6.35-28-generic                 1
 712.160461426 = 764.676472832  boot/vmlinuz-2.6.38-8-generic                  1
 713.898643494 = 766.542831616  initrd.img                                     2
 712.069732666 = 764.579053568  initrd.img.old                                 2
 712.160461426 = 764.676472832  vmlinuz                                        1
 372.472446442 = 399.939244032  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by kansasnoob on 2011-05-02
Please also post the output of:

```
sudo parted -l
```

BTW that's a lower case L :)

---

### Post by endintears on 2011-05-02
As requested:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs


Model: ATA Maxtor 6B300S0 (scsi)
Disk /dev/sdb: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      32.3kB  105GB  105GB  primary   ntfs         boot
 2      105GB   300GB  195GB  extended               lba
 5      105GB   300GB  195GB  logical   ntfs


Model: ATA ST31000528AS (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs


Model: ATA NetCell SyncRAID (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  52.4GB  52.4GB  primary   ntfs            boot
 2      52.4GB  1000GB  948GB   extended                  lba
 5      52.4GB  352GB   300GB   logical   ntfs
 6      352GB   994GB   642GB   logical   ext4
 7      994GB   1000GB  6182MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.

```

---

### Post by kansasnoob on 2011-05-02
OK, based on your error and the fact that grub is already installed in sda, sdb, and sdc let's do this, from a live CD/USB (please copy-n-paste):

```
sudo mount /dev/sdd6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
apt-get install --reinstall grub-pc
```

That may trigger a process that presents a few debconf windows similar to this:

[ATTACH]190819[/ATTACH]

Those windows are generally manipulated with the use of the Tab key, arrow keys, and to select/de-select "grub-install" devices you use the spacebar.

Remember you want to install grub to sda, sdb, and sdd.

Whether those appear or not let's play things safe and continue:

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

```
grub-install /dev/sdd
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Don't worry if that last command spits any errors, just reboot and keep your fingers crossed :)

---

### Post by endintears on 2011-05-02
Thanks for the suggestions. Unfortunately the problem remains. Any other ideas?

---

### Post by kansasnoob on 2011-05-02
I do have a couple of ideas but I have to be out of the house for several hours (medical stuff). Regardless it would be much easier to work on this if we could get you booted into Ubuntu.

If it's not terribly inconvenient for you DL and burn this disc:

[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

It's really not designed to fix anything but just to help boot unbootable OS's, and I'd prefer not fixing this with anything but Ubuntu's own grub anyway.

I've had very good luck with the Detect any OS option. Expect it to be slow, like maybe even a couple of minutes slow booting :)

Hopefully that can serve as a temporary solution so you can get some work done, and I'll get back ASAP.

My first thought is trying my "Deep and dirty grub2 purge & replace", but I call it that for a reason :)

Also I've noticed too many of these failures so we may have to try reverting to the Maverick 'grub-pc' and 'grub-common' packages :(

I've had no problem on my own machines but we need to try and figure out why there are so many boot failures.

---

### Post by kansasnoob on 2011-05-02
If someone else wants to see my "dirty" notes here they are, but they're sloppy and incomplete :(

[ATTACH]190835[/ATTACH]

---

### Post by endintears on 2011-05-02
Thanks, much appreciated. Using the boot CD and 'Detect any OS' I've been able to successfully boot.

Let me know (when you have the time) your other ideas for a permanent solution but in the interim I'll take a look at your notes.

---

### Post by kansasnoob on 2011-05-02
> **endintears said:**
> Thanks, much appreciated. Using the boot CD and 'Detect any OS' I've been able to successfully boot.

Let me know (when you have the time) your other ideas for a permanent solution but in the interim I'll take a look at your notes.

Great! I know it's a PITA to have to use that to boot right now but I have a few non-puter things nipping at my heels :(

It could be either very late tonight or tomorrow morning before I can get back to this, so please accept my apologies :redface:

Just to give me a head start I'd like the output of these commands while booted into your installed Ubuntu:

```
ls /etc/grub.d
```

```
ls /etc/default
```

```
uname -m
```

I do know we can fix this :D

---

### Post by endintears on 2011-05-03
No apology necessary! Here is the output you requested:

```
$ ls /etc/grub.d
00_header        10_linux      20_memtest86+  40_custom  README
05_debian_theme  20_linux_xen  30_os-prober   41_custom
```

```
$ ls /etc/default
acpid         console-setup  halt           ntpdate            tmpfs
acpi-support  cron           irqbalance     pulseaudio         ufw
alsa          cups           kerneloops     rcS                useradd
apport        dbus           keyboard       rsync              virtualbox-ose
avahi-daemon  devpts         locale         rsyslog            winbind
bootlogd      google-chrome  mediatomb      sabnzbdplus
brltty        grub           mumble-server  saned
cacerts       grub.ucf-dist  nss            speech-dispatcher
```

```
$ uname -m
i686
```

---

### Post by kansasnoob on 2011-05-03
Sorry to take so long but besides trying to get you fixed I'm trying to understand what might be wrong so we can truly get it fixed :)

Step #1: This is totally optional but it may help to figure out what's going wrong, not just for you, but with Maverick to Natty upgrades in general (regarding grub). But it could be time consuming so if you opt out of this it's OK.

If you're game to filing a bug report regarding this open a terminal and run:

```
ubuntu-bug grub-pc
```

If you have a Launchpad account you'll be asked to login, or you'll be asked to create an account. If you chose to do this I'd suggest a simple bug title like, "Upgrade to Natty renders computer unbootable". Ignore suggestions of being a duplicate and insist it's a new bug.

Then in the text explain very briefly what went wrong and what you've done to fix it, including a link to this thread. No need to get into great detail although it would be good if you could provide a link to the guide you followed when in post #1 you said:

> I've tried purging and reinstalling grub using a live-cd but no joy.


Then if you post the bug report link I'll sign up and try to take care of things going forward as best I can. If you choose not to do this it's OK with me :D

I realize it can be just a further PITA so it's 100% optional and in no way effects the level of help you'll get from me.

Step #2: I have serious doubts that this will work based on what's happened so far but we really do need to try this. Please copy-n-paste:

```
sudo mv /boot/grub /boot/grub_OLD
```

```
sudo mkdir /boot/grub
```

```
sudo mv /etc/default/grub /etc/default/grub_OLD
```

```
sudo rm -R /etc/grub.d
```

Some of these commands will return a message like "not installed, so not removed" or "E: Unable to locate package", that's OK. You'll need to confirm removal of most packages by typing "y". (NOTE: It's also safe to reinstall 'grub-customizer', 'startupmanager', and 'ubuntu-tweak' after you know that grub 2 is restored and booting properly. But it is NOT safe to install the package 'grub'!) **When you "purge grub-pc" you'll be asked if you're sure you want to remove all grub files so you'll have to confirm that by using the Tab key to select Yes.**

```
sudo apt-get remove startupmanager
```

```
sudo apt-get remove grub-customizer
```

```
sudo apt-get remove ubuntu-tweak
```

```
sudo apt-get purge grub
```

```
sudo apt-get purge grub-pc
```

```
sudo apt-get purge grub-common
```

Reinstalling grub 2 would hopefully require only one command:

```
sudo apt-get install grub-pc
```

More debconf windows, just do as explained in post #5 :)

If we're lucky that will boot now, if not move on to step #3 after the requisite amount of cursing and once again using the SGD2 disc.

Step #3: If you're here step #2 failed so we're going to try downgrading to Maverick grub packages.

[COLOR="Red"]NOTE: these are 32 bit packages, I knew that's what was needed from the output of "uname -m", to others attempting this - ask for help first![/COLOR]

```
sudo rm -R /boot/grub
``` 

```
sudo mkdir /boot/grub
```

```
sudo rm -R /etc/default/grub
```

```
sudo rm -R /etc/grub.d
```

```
sudo apt-get purge grub-pc
```

```
sudo apt-get purge grub-common
```

```
wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/grub2/grub-common_1.98+20100804-5ubuntu3_i386.deb

```
```
wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/grub2/grub-pc_1.98+20100804-5ubuntu3_i386.deb
```

```
sudo dpkg -i grub-common_1.98+20100804-5ubuntu3_i386.deb
```

```
sudo dpkg -i grub-pc_1.98+20100804-5ubuntu3_i386.deb
```

Again more debconf windows. When complete reboot. If that works then you'll want to keep those packages from upgrading:

```
echo grub-common hold | sudo dpkg --set-selections
```

```
echo grub-pc hold | sudo dpkg --set-selections
```

I'm dying of curiosity to see what works. I won't say yet but I have a sneaking suspicion where things went wrong ........ maybe.

---

### Post by endintears on 2011-05-04
Just to let you know I have read this. I just need to try to find the time to dedicate to it, and I intend to fill out the bug report as well, it's the least I can do in return.

---

### Post by endintears on 2011-05-05
Bug report is here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/778059](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/778059)

---

### Post by endintears on 2011-05-05
And to confirm that yes, **downgrading to the Maverick grub packages fixed the problem!**

---

### Post by kansasnoob on 2011-05-05
> **endintears said:**
> And to confirm that yes, **downgrading to the Maverick grub packages fixed the problem!**

But only running step #2 did not?

---

### Post by kansasnoob on 2011-05-05
Many thanks BTW :)

I'm lousy tired ATM, nursing a sick dog post surgery, so if I make little sense I'm sorry.

---

### Post by endintears on 2011-05-06
Yes, sorry, to clarify, running step #2 did not work, and I had to again use the SGD to boot.

---

### Post by ais77 on 2011-05-31
Fresh installed Natty frozen at Grub menu after several reboots - with no response from keyboard. With no chances to boot.
Only downgrading to Maverick Grub solved the problem.
Thank you for HOWTO.

---

