---
title: "GRUB Windows 7 option is a loop"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by jinchuuriki_naruto on 2013-01-04
I recently updated my ubuntu to 12.04 in a machine where I had installed Windows 7 and Ubuntu 10.04. After this my boot was messed up, but I could "fix it" using the SGD ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)). The problem I am facing now is that whenever I choose Windows 7 on the GRUB menu, it loops back into the same menu, and using the SGD it also goes back to this.

I have searched google and this forums, and I found out that many people had the same problems as me, but the most common solution which is using the Windows 7 CD to repair the startup (using it three times) didn't work. So I would appreciate if someone can help me with this matter.

I also used the bootinfo script ([http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)) but I don't know anything about booting, but I guess this may be useful to try to solve this issue. This was my result:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1
                       and looks at sector 272929384 of the same hard drive
                       for core.img. core.img is at this location and looks
                       for (,msdos3)/boot/grub on this drive. No errors found
                       in the Boot Parameter Block.
    Operating System: 
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System: 
    Boot files:       

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb1 starts
                       at sector 0. But according to the info from fdisk,
                       sdb1 starts at sector 63.
    Operating System: 
    Boot files:       

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   209,715,199   209,508,352   7 NTFS / exFAT / HPFS
/dev/sda3         209,715,200   309,714,943    99,999,744  83 Linux
/dev/sda4         309,716,990   976,773,119   667,056,130   5 Extended
/dev/sda5         309,716,992   329,715,711    19,998,720  82 Linux swap / Solaris
/dev/sda6         329,717,760   976,773,119   647,055,360  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CC4237E34237D146                       ntfs      
/dev/sda2        26823AB2823A85F9                       ntfs       Windows
/dev/sda3        0b278842-032a-4883-becb-b68d3ede9a2a   ext4      
/dev/sda5        6201e185-e758-44ea-9ccf-c9512fcd46fc   swap      
/dev/sda6        d30631ad-890f-4bb0-81b2-ddda4ceeeb7d   ext3      
/dev/sdb1        F345-F8EC                              vfat       STORAGE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt/sda1                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/Windows           fuseblk    (ro,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext3       (rw)
/dev/sdb1        /media/STORAGE           vfat       (rw,uid=1000,gid=100)


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
search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
    linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=0b278842-032a-4883-becb-b68d3ede9a2a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
    echo    'Loading Linux 3.2.0-35-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=0b278842-032a-4883-becb-b68d3ede9a2a ro recovery nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-35-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=0b278842-032a-4883-becb-b68d3ede9a2a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=0b278842-032a-4883-becb-b68d3ede9a2a ro recovery nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0b278842-032a-4883-becb-b68d3ede9a2a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root CC4237E34237D146
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
proc                                       /proc           proc  nodev,noexec,nosuid                           0  0 
# / was on /dev/sda3 during installation
UUID=0b278842-032a-4883-becb-b68d3ede9a2a  /               ext4  errors=remount-ro                             0  1 
# /home was on /dev/sda6 during installation
UUID=d30631ad-890f-4bb0-81b2-ddda4ceeeb7d  /home           ext3  defaults                                      0  2 
# swap was on /dev/sda5 during installation
UUID=6201e185-e758-44ea-9ccf-c9512fcd46fc  none            swap  sw                                            0  0 
/dev/sda2                                  /media/Windows  ntfs  nls=iso8859-1,ro,umask=000,gid=users,uid=jin  0  0 
/dev/sda1                                  /mnt/sda1       ntfs  defaults                                      0  0 
/dev/sdb1                                  /media/STORAGE  vfat  uid=jin,gid=users                             0  0 
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           3
               =                boot/initrd.img-3.2.0-35-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-35-generic-pae              1
               =                initrd.img                                     3
               =                initrd.img.old                                 3
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```And here there is a screenshot with the configuration of my hard drives:

[IMG]http://img109.imageshack.us/img109/4869/42123135.png[/IMG]

---

### Post by oldfred on 2013-01-05
You installed grub2's boot loader to the Windows boot partitions partition boot sector. Windows has to have its boot code in NTFS partitions. NTFS does have a backup and testdisk can restore from backup if valid.

```
sda1: ____________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    [COLOR=Red]Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1
                       and looks at sector 272929384 of the same hard drive
                       for core.img. core.img is at this location and looks
                       for (,msdos3)/boot/grub on this drive. No errors found
                       in the Boot Parameter Block.[/COLOR]
    Operating System: 
    Boot files:        /bootmgr /Boot/BCD

```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Since you are only booting Ubuntu thru the grub install in the Windows partition you need to install grub to the MBR. Boot into Ubuntu and run this first:
       sudo grub-install /dev/sda

---

