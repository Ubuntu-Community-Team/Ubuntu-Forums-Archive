---
title: "Missing file"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by sanosuke_takashi on 2009-11-21
I installed Ubuntu 9.10, but whenever I rebooted my computer it just sat there at the "GRUB Loading" screen for ever. I asked one of my friends and it turns out that my menu.list file from were I'm trying to dual with xp isn't there. So, can anyone help me by sending me the file or something of that nature. I know it's supposed to be in the grub folder, but it just isn't. And as a second question would it just be better to downgrade to 9.04? Thanks for any help in advance.

---

### Post by presence1960 on 2009-11-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.35 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sanosuke_takashi on 2009-11-21
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=922fb216-f52d-44e2-9c38-a1ad7409b325)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Recovery:Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4fa9eb4f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,067,839    11,067,777   b W95 FAT32
/dev/sda2    *     11,067,840   156,280,319   145,212,480   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c74ae42

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   181,903,994   181,903,932   c W95 FAT32 (LBA)
/dev/sdd2         323,356,320   625,137,344   301,781,025   5 Extended
/dev/sdd5         329,461,083   498,159,584   168,698,502  83 Linux
/dev/sdd6         616,092,813   625,137,344     9,044,532  82 Linux swap / Solaris
/dev/sdd7         323,356,446   329,461,019     6,104,574  82 Linux swap / Solaris
/dev/sdd8         498,159,648   611,192,924   113,033,277  83 Linux
/dev/sdd9         611,192,988   616,092,749     4,899,762  82 Linux swap / Solaris
/dev/sdd3    *    181,903,995   323,356,319   141,452,325  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="0127-0A71" TYPE="vfat" 
/dev/sda2: UUID="34802E70802E38AE" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sdb1: LABEL="Cruzer" UUID="8002-13AC" TYPE="vfat" 
/dev/sdd1: LABEL="EXTERNAL" UUID="05BE-171E" TYPE="vfat" 
/dev/sdd3: UUID="9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd5: UUID="dcee709d-6089-4670-8e20-36dc4fe99ee3" TYPE="ext4" 
/dev/sdd6: UUID="ae18c0e2-4de9-493b-9a54-9f7f0320d4d4" TYPE="swap" 
/dev/sdd7: UUID="45f3d621-5a2b-4355-a2f4-c98520b6efb8" TYPE="swap" 
/dev/sdd8: UUID="922fb216-f52d-44e2-9c38-a1ad7409b325" TYPE="ext4" 
/dev/sdd9: UUID="8cc90f03-6b80-43a1-90e2-b7115cd8f7c2" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda2/boot.ini: ================================

[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdd5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,5)
search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0127-0a71
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 34802e70802e38ae
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=ae18c0e2-4de9-493b-9a54-9f7f0320d4d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 168.6GB: boot/grub/grub.cfg
 168.6GB: boot/initrd.img-2.6.31-14-generic
 168.6GB: boot/vmlinuz-2.6.31-14-generic
 168.6GB: initrd.img
 168.6GB: vmlinuz

=========================== sdd8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,8)
search --no-floppy --fs-uuid --set 922fb216-f52d-44e2-9c38-a1ad7409b325
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 922fb216-f52d-44e2-9c38-a1ad7409b325
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=922fb216-f52d-44e2-9c38-a1ad7409b325 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 922fb216-f52d-44e2-9c38-a1ad7409b325
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=922fb216-f52d-44e2-9c38-a1ad7409b325 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0127-0a71
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 34802e70802e38ae
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c
    linux /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro quiet splash
    initrd /boot/initrd.img-2.6.20-15-generic
}
menuentry "Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c
    linux /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro single
    initrd /boot/initrd.img-2.6.20-15-generic
}
menuentry "Ubuntu, memtest86+ (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=922fb216-f52d-44e2-9c38-a1ad7409b325 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=8cc90f03-6b80-43a1-90e2-b7115cd8f7c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd8: Location of files loaded by Grub: ===================


 255.0GB: boot/grub/grub.cfg
 255.0GB: boot/initrd.img-2.6.31-14-generic
 255.0GB: boot/vmlinuz-2.6.31-14-generic
 255.0GB: initrd.img
 255.0GB: vmlinuz

=========================== sdd3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd2,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd2,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd2,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdd3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb7
UUID=45f3d621-5a2b-4355-a2f4-c98520b6efb8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdd3: Location of files loaded by Grub: ===================


  93.1GB: boot/grub/menu.lst
  93.1GB: boot/grub/stage2
  93.1GB: boot/initrd.img-2.6.20-15-generic
  93.1GB: boot/initrd.img-2.6.20-15-generic.bak
  93.1GB: boot/vmlinuz-2.6.20-15-generic
  93.1GB: initrd.img
  93.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by presence1960 on 2009-11-21
> **sanosuke_takashi said:**
> ```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=922fb216-f52d-44e2-9c38-a1ad7409b325)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Recovery:Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4fa9eb4f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,067,839    11,067,777   b W95 FAT32
/dev/sda2    *     11,067,840   156,280,319   145,212,480   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c74ae42

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   181,903,994   181,903,932   c W95 FAT32 (LBA)
/dev/sdd2         323,356,320   625,137,344   301,781,025   5 Extended
/dev/sdd5         329,461,083   498,159,584   168,698,502  83 Linux
/dev/sdd6         616,092,813   625,137,344     9,044,532  82 Linux swap / Solaris
/dev/sdd7         323,356,446   329,461,019     6,104,574  82 Linux swap / Solaris
/dev/sdd8         498,159,648   611,192,924   113,033,277  83 Linux
/dev/sdd9         611,192,988   616,092,749     4,899,762  82 Linux swap / Solaris
/dev/sdd3    *    181,903,995   323,356,319   141,452,325  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="0127-0A71" TYPE="vfat" 
/dev/sda2: UUID="34802E70802E38AE" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sdb1: LABEL="Cruzer" UUID="8002-13AC" TYPE="vfat" 
/dev/sdd1: LABEL="EXTERNAL" UUID="05BE-171E" TYPE="vfat" 
/dev/sdd3: UUID="9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd5: UUID="dcee709d-6089-4670-8e20-36dc4fe99ee3" TYPE="ext4" 
/dev/sdd6: UUID="ae18c0e2-4de9-493b-9a54-9f7f0320d4d4" TYPE="swap" 
/dev/sdd7: UUID="45f3d621-5a2b-4355-a2f4-c98520b6efb8" TYPE="swap" 
/dev/sdd8: UUID="922fb216-f52d-44e2-9c38-a1ad7409b325" TYPE="ext4" 
/dev/sdd9: UUID="8cc90f03-6b80-43a1-90e2-b7115cd8f7c2" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda2/boot.ini: ================================

[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdd5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,5)
search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0127-0a71
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 34802e70802e38ae
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=ae18c0e2-4de9-493b-9a54-9f7f0320d4d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 168.6GB: boot/grub/grub.cfg
 168.6GB: boot/initrd.img-2.6.31-14-generic
 168.6GB: boot/vmlinuz-2.6.31-14-generic
 168.6GB: initrd.img
 168.6GB: vmlinuz

=========================== sdd8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,8)
search --no-floppy --fs-uuid --set 922fb216-f52d-44e2-9c38-a1ad7409b325
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 922fb216-f52d-44e2-9c38-a1ad7409b325
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=922fb216-f52d-44e2-9c38-a1ad7409b325 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 922fb216-f52d-44e2-9c38-a1ad7409b325
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=922fb216-f52d-44e2-9c38-a1ad7409b325 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0127-0a71
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 34802e70802e38ae
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c
    linux /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro quiet splash
    initrd /boot/initrd.img-2.6.20-15-generic
}
menuentry "Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c
    linux /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro single
    initrd /boot/initrd.img-2.6.20-15-generic
}
menuentry "Ubuntu, memtest86+ (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set dcee709d-6089-4670-8e20-36dc4fe99ee3
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=dcee709d-6089-4670-8e20-36dc4fe99ee3 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=922fb216-f52d-44e2-9c38-a1ad7409b325 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=8cc90f03-6b80-43a1-90e2-b7115cd8f7c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd8: Location of files loaded by Grub: ===================


 255.0GB: boot/grub/grub.cfg
 255.0GB: boot/initrd.img-2.6.31-14-generic
 255.0GB: boot/vmlinuz-2.6.31-14-generic
 255.0GB: initrd.img
 255.0GB: vmlinuz

=========================== sdd3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd2,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd2,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd2,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdd3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=9b1208bc-7e2c-43c8-92e5-a29e3b9d6f7c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb7
UUID=45f3d621-5a2b-4355-a2f4-c98520b6efb8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdd3: Location of files loaded by Grub: ===================


  93.1GB: boot/grub/menu.lst
  93.1GB: boot/grub/stage2
  93.1GB: boot/initrd.img-2.6.20-15-generic
  93.1GB: boot/initrd.img-2.6.20-15-generic.bak
  93.1GB: boot/vmlinuz-2.6.20-15-generic
  93.1GB: initrd.img
  93.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc
```

next time you paste a lot of text on here highlight the text and click **#** on the toolbar to place code tags around the text please. See above.

You have 2 Ubuntu karmic installs on sdd at sdd5 & sdd8. You have a 7.10 install at sdd3. You have 3 swap partitions when only one is needed. I would sort that out first if I were you. At the minimum get rid of one karmic install and possibly the 7.10 also.

Then set sdd as first hard disk to boot in the hard disk boot order in BIOS. Then boot the 9.10 Live CD/USB and install GRUB 2 to sdd. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") for instructions on doing that.

---

### Post by sanosuke_takashi on 2009-11-22
...about that, I'm a noob at Linux. this is the first time I have tried to use it so I have no idea on how to do any of that. So, a little help with that too?

---

