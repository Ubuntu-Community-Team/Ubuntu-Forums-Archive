---
title: "Dual Boot Installation/Grub help needed."
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by yoog on 2011-07-31
I have Windows Vista Ultima on a 500GB (RAID mirror) drive and then I  have installed UBUNTU 11.04 on a 100 GB drive that has two partition:  80GB formatted as root and 18GB as SWAP. After installation, when I  reboot the computer it straight away goes to window. Some how during  installation I forgot to point GRUB to be installed on a drive/partition  where Vista is installed.

What should I do so that I can have have GRUB with dual boot option?

Here is the RESULTS.txt file content.
---------------------------------------------------------------------------------------------------------------------------------
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 1ed266c9-e971-48a3-9530-84c7be7f1512 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/mapper/isw_dgfabiibgb_Vista64.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_dgfabiibgb_Vista641: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   157,902,884   157,902,822  83 Linux
/dev/sda2         157,902,946   195,800,219    37,897,274   5 Extended
/dev/sda5         157,902,948   195,800,219    37,897,272  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: isw_dgfabiibgb_Vista64 _____________________________________________________________________

Disk /dev/mapper/isw_dgfabiibgb_Vista64: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_dgfabiibgb_Vista641   *          2,048   976,764,927   976,762,880   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dgfabiibgb_Vista64p1 C800B0A400B09AC0                       ntfs       VistaRAID
/dev/sda1        9c91da60-473d-4be9-89a6-9987ad0010e7   ext4       
/dev/sda5        46a4ab36-5358-4223-8acf-85a9dddea40a   swap       
/dev/sdb                                                isw_raid_member 
/dev/sdc                                                isw_raid_member 
/dev/sdd1        E66E874F6E871787                       ntfs       NewSegate

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dgfabiibgb_Vista64
isw_dgfabiibgb_Vista64p1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/dm-2        /media/VistaRAID         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9c91da60-473d-4be9-89a6-9987ad0010e7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9c91da60-473d-4be9-89a6-9987ad0010e7
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9c91da60-473d-4be9-89a6-9987ad0010e7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9c91da60-473d-4be9-89a6-9987ad0010e7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9c91da60-473d-4be9-89a6-9987ad0010e7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9c91da60-473d-4be9-89a6-9987ad0010e7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9c91da60-473d-4be9-89a6-9987ad0010e7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9c91da60-473d-4be9-89a6-9987ad0010e7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/mapper/isw_dgfabiibgb_Vista64p1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set=root C800B0A400B09AC0
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.134063244 = 8.733883904    boot/grub/core.img                             1
  68.137004375 = 73.161551360   boot/grub/grub.cfg                             1
   0.434073925 = 0.466083328    boot/initrd.img-2.6.38-8-generic               1
   8.132335186 = 8.732028416    boot/vmlinuz-2.6.38-8-generic                  1
   0.434073925 = 0.466083328    initrd.img                                     1
   8.132335186 = 8.732028416    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_dgfabiibgb_Vista641



=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/mapper/isw_dgfabiibgb_Vista641: No such file or directory
hexdump: /dev/mapper/isw_dgfabiibgb_Vista641: No such file or directory
-----------------------------------------------------------------------------------------------------------------------------------

---

### Post by YesWeCan on 2011-07-31
Hi there. If it boots straight into Windows then I'd make sure your bios is set to boot your 100GB disk first, before it boots your Windows RAID. It looks like the 100GB disk is set up ok.

---

### Post by yoog on 2011-08-02
That did the trick. I wonder why I can't install GRUB on Vista Drive MBR. Anyway, thanks.

---

### Post by YesWeCan on 2011-08-02
AFAIK the Grub boot program cannot be installed to the MBRs of a Windows RAID.
Don't forget to mark this as solved in [COLOR=Red]**thread tools**[/COLOR].

---

### Post by YannBuntu on 2011-08-03
Hi

> **YesWeCan said:**
> Grub boot program cannot be installed to the MBRs of a Windows RAID.

For my information (and help developping a GNU tool), please could you provide me more information (links..) about this subject ?

---

