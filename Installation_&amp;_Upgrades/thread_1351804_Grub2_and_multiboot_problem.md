---
title: "Grub2 and multiboot problem"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Savta Simcha on 2009-12-10
I installed Ubuntu 9.10 on my computer to dual-boot with Windows XP. I had Ubuntu 9.04 previously with Windows XP and had no problems. Grub2 somehow lost things and only after using Super Grub Disk was I able to boot into Ubuntu and configure grub to let me dual-boot. 
Now I decided to install Kubuntu in a separate partition, but after the install, I received on booting: "error: no such disk      grub rescue>"
Super Grub2 Disk helped me boot into Ubuntu and I reinstalled grub, but the grub menu doesn't seem to find the Kubuntu installation.

I ran the Boot Info Script and got the following:

Any ideas as to how to correct the situation?

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ubuntu/winboot/wubildr.mbr

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

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

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdc7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdc8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

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
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf1e6b92

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    42,042,104    42,042,042   7 HPFS/NTFS
/dev/sda2          42,042,105   561,295,034   519,252,930   f W95 Ext d (LBA)
/dev/sda5          42,042,168   561,295,034   519,252,867   7 HPFS/NTFS
/dev/sda3    *    561,295,035   625,137,344    63,842,310  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36331667

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   915,640,739   915,624,675   f W95 Ext d (LBA)
/dev/sdb5              16,128   912,925,754   912,909,627   7 HPFS/NTFS
/dev/sdb6         912,925,818   915,640,739     2,714,922  82 Linux swap / Solaris
/dev/sdb2    *    915,640,740   976,768,064    61,127,325  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2cad2ca

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    32,885,054    32,884,992   7 HPFS/NTFS
/dev/sdc2          32,885,055   625,137,344   592,252,290   f W95 Ext d (LBA)
/dev/sdc5          32,885,118    71,987,264    39,102,147   c W95 FAT32 (LBA)
/dev/sdc6          71,987,328   102,446,504    30,459,177   c W95 FAT32 (LBA)
/dev/sdc7         102,446,568   132,006,104    29,559,537   c W95 FAT32 (LBA)
/dev/sdc8         132,006,168   215,528,039    83,521,872   c W95 FAT32 (LBA)
/dev/sdc9         215,528,103   461,290,409   245,762,307   7 HPFS/NTFS
/dev/sdc10        461,290,473   625,137,344   163,846,872   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
1 heads, 63 sectors/track, 4961616 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a5b1d34

Partition  Boot         Start           End          Size  Id System

/dev/sdd2              16,128   312,580,673   312,564,546   f W95 Ext d (LBA)
/dev/sdd5              16,191   312,576,704   312,560,514   7 HPFS/NTFS
/dev/sdd6         312,576,706   312,580,611         3,906  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F44C21964C215520" LABEL="XPSATA" TYPE="ntfs" 
/dev/sda3: UUID="42ad32af-ca87-4df3-8246-13e700b004fc" TYPE="ext4" 
/dev/sda5: UUID="327C6BA97C6B6697" LABEL="SATA" TYPE="ntfs" 
/dev/sdb2: LABEL="Kubuntu" UUID="bc681013-a257-4c5b-beaf-1413bf3d4afa" TYPE="ext4" 
/dev/sdb5: UUID="947495CD7495B28A" LABEL="VIDEOS" TYPE="ntfs" 
/dev/sdb6: UUID="ce18e058-7bd7-428c-8b7b-ce2f637381c3" TYPE="swap" 
/dev/sdc1: UUID="F44C21964C215520" LABEL="XP" TYPE="ntfs" 
/dev/sdc5: LABEL="BIGDRIVE" UUID="4746-035F" TYPE="vfat" 
/dev/sdc6: LABEL="IVORY2" UUID="1266-0BEB" TYPE="vfat" 
/dev/sdc7: LABEL="IVORY3" UUID="2E4A-0BF1" TYPE="vfat" 
/dev/sdc8: LABEL="IVORY4" UUID="2F0E-0BF8" TYPE="vfat" 
/dev/sdc9: UUID="0820EF2220EF158A" LABEL="RABENU" TYPE="ntfs" 
/dev/sdc10: LABEL="GIANT" UUID="4E18-4EF8" TYPE="vfat" 
/dev/sdd5: UUID="DE2CD9752CD94963" LABEL="BRESLEV" TYPE="ntfs" 
/dev/sdd6: UUID="79b42267-ef71-4d05-bf91-5a4e4874663a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shulamit/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shulamit)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin 

================================ sda5/boot.ini: ================================

[operating systems] 
[boot loader] 
timeout=30 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f44c21964c215520
    drivemap -s (hd1) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set bc681013-a257-4c5b-beaf-1413bf3d4afa
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=bc681013-a257-4c5b-beaf-1413bf3d4afa ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set bc681013-a257-4c5b-beaf-1413bf3d4afa
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=bc681013-a257-4c5b-beaf-1413bf3d4afa ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set f44c21964c215520
    drivemap -s (hd1) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc10)" {
    insmod fat
    set root=(hd2,10)
    search --no-floppy --fs-uuid --set 4e18-4ef8
    drivemap -s (hd1) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdd5)" {
    insmod ntfs
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set de2cd9752cd94963
    drivemap -s (hd1) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Kubuntu" {
   set root=(hd1,2,b)
   chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=42ad32af-ca87-4df3-8246-13e700b004fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=79b42267-ef71-4d05-bf91-5a4e4874663a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 287.3GB: boot/grub/grub.cfg
 287.3GB: boot/initrd.img-2.6.31-14-generic
 287.3GB: boot/initrd.img-2.6.31-16-generic
 287.3GB: boot/vmlinuz-2.6.31-14-generic
 287.3GB: boot/vmlinuz-2.6.31-16-generic
 287.3GB: initrd.img
 287.3GB: initrd.img.old
 287.3GB: vmlinuz
 287.3GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set bc681013-a257-4c5b-beaf-1413bf3d4afa
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
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set bc681013-a257-4c5b-beaf-1413bf3d4afa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bc681013-a257-4c5b-beaf-1413bf3d4afa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set bc681013-a257-4c5b-beaf-1413bf3d4afa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bc681013-a257-4c5b-beaf-1413bf3d4afa ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f44c21964c215520
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro single
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 42ad32af-ca87-4df3-8246-13e700b004fc
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=42ad32af-ca87-4df3-8246-13e700b004fc ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set f44c21964c215520
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc10)" {
    insmod fat
    set root=(hd2,10)
    search --no-floppy --fs-uuid --set 4e18-4ef8
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdd5)" {
    insmod ntfs
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set de2cd9752cd94963
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=bc681013-a257-4c5b-beaf-1413bf3d4afa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=ce18e058-7bd7-428c-8b7b-ce2f637381c3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 468.8GB: boot/grub/grub.cfg
 468.8GB: boot/initrd.img-2.6.31-14-generic
 468.8GB: boot/vmlinuz-2.6.31-14-generic
 468.8GB: initrd.img
 468.8GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin 

=============================== sdc10/boot.ini: ===============================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(7)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(7)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

=============================== sdc10/BOOT.INI: ===============================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(7)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(7)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

================================ sdd5/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc10

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.X.MSWIN4.1..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 e9 bb 7e 1b  |........?.....~.|
00000020  d8 1a c4 09 1c 4e 00 00  00 00 00 00 02 00 00 00  |.....N..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f8 4e 18 4e 18  01 02 01 02 14 00 00 00  |..).N.N.........|
00000050  15 00 46 41 54 33 32 20  20 20 00 00 18 00 00 00  |..FAT32   ......|
00000060  19 00 00 00 1a 00 00 00  1b 00 00 00 1c 00 00 00  |................|
00000070  1d 00 00 00 1e 00 00 00  1f 00 00 00 20 00 00 00  |............ ...|
00000080  21 00 00 00 22 00 00 00  23 00 00 00 24 00 00 00  |!..."...#...$...|
00000090  25 00 00 00 26 00 00 00  27 00 00 00 28 00 00 00  |%...&...'...(...|
000000a0  29 00 00 00 2a 00 00 00  2b 00 00 00 2c 00 00 00  |)...*...+...,...|
000000b0  2d 00 00 00 2e 00 00 00  2f 00 00 00 30 00 00 00  |-......./...0...|
000000c0  31 00 00 00 32 00 00 00  33 00 00 00 34 00 00 00  |1...2...3...4...|
000000d0  35 00 00 00 36 00 00 00  37 00 00 00 38 00 00 00  |5...6...7...8...|
000000e0  39 00 00 00 3a 00 00 00  3b 00 00 00 3c 00 00 00  |9...:...;...<...|
000000f0  3d 00 00 00 3e 00 00 00  3f 00 00 00 40 00 00 00  |=...>...?...@...|
00000100  41 00 00 00 42 00 00 00  43 00 00 00 44 00 00 00  |A...B...C...D...|
00000110  45 00 00 00 46 00 00 00  47 00 00 00 48 00 00 00  |E...F...G...H...|
00000120  49 00 00 00 4a 00 00 00  4b 00 00 00 4c 00 00 00  |I...J...K...L...|
00000130  4d 00 00 00 4e 00 00 00  4f 00 00 00 50 00 00 00  |M...N...O...P...|
00000140  51 00 00 00 52 00 00 00  53 00 00 00 54 00 00 00  |Q...R...S...T...|
00000150  55 00 00 00 56 00 00 00  57 00 00 00 58 00 00 00  |U...V...W...X...|
00000160  59 00 00 00 5a 00 00 00  5b 00 00 00 5c 00 00 00  |Y...Z...[...\...|
00000170  5d 00 00 00 5e 00 00 00  5f 00 00 00 60 00 00 00  |]...^..._...`...|
00000180  61 00 00 00 62 00 00 00  63 00 00 00 64 00 00 00  |a...b...c...d...|
00000190  65 00 00 00 66 00 00 00  67 00 00 00 68 00 00 00  |e...f...g...h...|
000001a0  69 00 00 00 6a 00 00 00  6b 00 00 00 6c 00 00 00  |i...j...k...l...|
000001b0  6d 00 00 00 6e 00 00 00  6f 00 00 00 70 00 00 00  |m...n...o...p...|
000001c0  71 00 00 00 72 00 00 00  73 00 00 00 74 00 00 00  |q...r...s...t...|
000001d0  75 00 00 00 76 00 00 00  77 00 00 00 78 00 00 00  |u...v...w...x...|
000001e0  79 00 00 00 7a 00 00 00  7b 00 00 00 7c 00 00 00  |y...z...{...|...|
000001f0  7d 00 00 00 7e 00 00 00  7f 00 00 00 80 00 00 00  |}...~...........|
00000200

---

### Post by oldfred on 2009-12-11
It may be all you need to do is to rerun the osprober
sudo update-grub

but since you used supergrub and may have some mixed data, you may want to try which reinstalls and lets you choose which drive to install the boot loader and reruns the osprober.
sudo grub-mkconfig
[http://techblog.ribouxj.org/2009/10/17/restore-windows-boot-option-in-grub-2-menu-after-installing-ubuntu-karmic-koala-9-10/](http://techblog.ribouxj.org/2009/10/17/restore-windows-boot-option-in-grub-2-menu-after-installing-ubuntu-karmic-koala-9-10/)

---

