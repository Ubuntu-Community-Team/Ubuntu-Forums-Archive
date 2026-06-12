---
title: "Ubuntu inactive in dual boot with Windows 7"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by atulsingh7890 on 2011-03-20
I have dual boot system with windows 7 and ubuntu 10.04
There was a trojan showing up in windows trojan/aluron 
in order to remove that i have to fix mbr and rebulid bcd...But when i did this  my boot meny disappeared..

and only window boots.
i  have all other related post 

my boot_info_script yields result.txt as



---------------------------BOOT INFO SCRIPT--------------------------------------




                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2021. But according to the info from fdisk, 
                       sda5 starts at sector 174086144.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    61,442,047    61,440,000   7 HPFS/NTFS
/dev/sda2          61,442,048   143,362,047    81,920,000   7 HPFS/NTFS
/dev/sda3         143,364,094   225,279,999    81,915,906   f W95 Ext d (LBA)
/dev/sda5         174,086,144   225,279,999    51,193,856   7 HPFS/NTFS
/dev/sda6         143,364,096   143,753,215       389,120  83 Linux
/dev/sda7         143,755,264   174,079,999    30,324,736  83 Linux
/dev/sda4         225,282,048   312,575,999    87,293,952   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3999 MB, 3999268864 bytes
124 heads, 62 sectors/track, 1016 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,811,007     7,810,946   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       31266f51-6a78-4ea5-8684-2364d9b84c79   ext3                                     
/dev/sda1        B0E6D61BE6D5E1A0                       ntfs                                     
/dev/sda2        1C60B67160B650EE                       ntfs       wallpapaers & documents       
/dev/sda3: PTTYPE="dos" 
/dev/sda4        D01438391438253E                       ntfs       New Volume                    
/dev/sda5        422642D02642C51F                       ntfs       ACCUMULATER                   
/dev/sda6        78f68c47-cdf0-4382-a012-cd0d4a8a47a5   ext4                                     
/dev/sda7        32b44181-ae1f-4c57-806f-fa22e35375f4   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        528A-1C9B                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/sda6              ext4       (rw)
/dev/sda7        /media/sda7              ext4       (rw)
/dev/loop1       /media/31266f51-6a78-4ea5-8684-2364d9b84c79 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/B0E6D61BE6D5E1A0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda6/grub/grub.cfg: =============================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 32b44181-ae1f-4c57-806f-fa22e35375f4
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 78f68c47-cdf0-4382-a012-cd0d4a8a47a5
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 78f68c47-cdf0-4382-a012-cd0d4a8a47a5
    linux    /vmlinuz-2.6.32-21-generic root=UUID=32b44181-ae1f-4c57-806f-fa22e35375f4 ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 78f68c47-cdf0-4382-a012-cd0d4a8a47a5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=32b44181-ae1f-4c57-806f-fa22e35375f4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 78f68c47-cdf0-4382-a012-cd0d4a8a47a5
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 78f68c47-cdf0-4382-a012-cd0d4a8a47a5
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b0e6d61be6d5e1a0
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda6: Location of files loaded by Grub: ===================


  73.4GB: grub/core.img
  73.4GB: grub/grub.cfg
  73.4GB: initrd.img-2.6.32-21-generic
  73.4GB: vmlinuz-2.6.32-21-generic

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=32b44181-ae1f-4c57-806f-fa22e35375f4 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=78f68c47-cdf0-4382-a012-cd0d4a8a47a5 /boot           ext4    defaults        0       2

=================== sda7: Location of files loaded by Grub: ===================


  82.4GB: boot/grub/core.img

---

### Post by atulsingh7890 on 2011-03-20
i have done all these things
as i have my boot  partition saperate

[COLOR=Red]mounting root and boot 
sudo grub-install --root-directory=media/sda7 /dev/sda7[/COLOR]

and this
[COLOR=Red]sudo grub-install --recheck --root-directory=media/sda7 /dev/sda7[/COLOR]



but it doesn't worked...

when i have done this again it gives error 
[COLOR=Red]mkdir: cannot create directory `media/sda7/boot': No such file or directory[/COLOR]



please tell how make grub as it was earlier

---

### Post by Quackers on 2011-03-20
As you seem to have a few mis-placed boot files here and there, I would probably decide to purge then re-install grub following this guide, by drs305.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

As you seem to have a separate boot partition (/dev/sda6) you should follow the "Why chroot" sections of that guide which deal with those setups. In other words both /dev/sda6 AND /dev/sda7 should be mounted first.
Grub2 should be installed to /dev/sda  (not a partition like /dev/sda7)

Does Windows boot ok? /grldr should not be in with Windows boot files on /dev/sda1. That could be removed at some time too.

---

