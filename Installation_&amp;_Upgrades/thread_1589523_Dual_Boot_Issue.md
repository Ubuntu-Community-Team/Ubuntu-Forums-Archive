---
title: "Dual Boot Issue"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by robertww on 2010-10-06
I am trying to set up a dual-boot with windows 7 (installed first) and ubuntu. The partitioning and installation went smoothly. However, every time I start my computer up it takes me straight into windows. There is no option to boot into the ubuntu system. Wasn't ubuntu supposed to set up a bootloader automatically? Does anybody know how to fix this? All suggestions are much appreciated, thanks!!!

---

### Post by Rubi1200 on 2010-10-06
Hi and welcome to the forums :)

Please use the Ubuntu CD to boot the computer and choose to try not install.

Then, post the results of the boot-script linked at the bottom of my post.

If there is an issue with the bootloader, the results should tell us and we can advise you as to how to fix this.

Thanks.

---

### Post by robertww on 2010-10-06
[LEFT]All right, here's what it spit out:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,911   332,414,975   332,208,065   7 HPFS/NTFS
/dev/sda3         600,088,576   625,139,711    25,051,136   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,519,669,607 1,519,669,545   7 HPFS/NTFS
/dev/sdb2       1,519,671,294 1,953,523,711   433,852,418   5 Extended
/dev/sdb5       1,519,671,296 1,936,146,431   416,475,136  83 Linux
/dev/sdb6       1,936,148,480 1,953,523,711    17,375,232  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A9C41249C410BBF                       ntfs       SYSTEM                        
/dev/sda2        22DCFB56DCFB2329                       ntfs       HP                            
/dev/sda3        DCA8B7C2A8B79A0A                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ACDCA6F1DCA6B54C                       ntfs       Iomega HDD                    
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        b9a325c5-8c1d-474b-9b5d-f144b4009bb9   ext4                                     
/dev/sdb6        690f6f7b-fa40-4636-96c9-0459948ee30a   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set b9a325c5-8c1d-474b-9b5d-f144b4009bb9
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set b9a325c5-8c1d-474b-9b5d-f144b4009bb9
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b9a325c5-8c1d-474b-9b5d-f144b4009bb9
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=b9a325c5-8c1d-474b-9b5d-f144b4009bb9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b9a325c5-8c1d-474b-9b5d-f144b4009bb9
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=b9a325c5-8c1d-474b-9b5d-f144b4009bb9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b9a325c5-8c1d-474b-9b5d-f144b4009bb9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b9a325c5-8c1d-474b-9b5d-f144b4009bb9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4a9c41249c410bbf
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set dca8b7c2a8b79a0a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=b9a325c5-8c1d-474b-9b5d-f144b4009bb9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=690f6f7b-fa40-4636-96c9-0459948ee30a none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 855.5GB: boot/grub/core.img
 950.1GB: boot/grub/grub.cfg
 855.5GB: boot/initrd.img-2.6.32-25-generic-pae
 855.5GB: boot/vmlinuz-2.6.32-25-generic-pae
 855.5GB: initrd.img
 855.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
[/LEFT]

---

### Post by Rubi1200 on 2010-10-06
I would try first changing the boot order in BIOS to enable booting into Ubuntu on the external drive.

---

