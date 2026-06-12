---
title: "Grub errors - More than 1 Grub"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2010-12-22
I am having some boot problems.

The first is I seem to have 3 GRUB installs.  So whilst I update the one from my live session, the change does not appear in the boot up menu. I had installed 10.10 from a CD into a different partition (sda6), but that will not boot, so I have just deleted this and done another grub install and update.

The kernel I am using has just been updated from 10.04 to 10.10 too, and it is this that I use and the Grub I have been working on (sda5).

                     pre.western { font-family: "Times New Roman"; }pre.cjk { font-family: "Times New Roman"; }pre.ctl { font-family: "Times New Roman"; }p { margin-bottom: 0.21cm; }      [HTML]            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/mnt/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /etc/lilo.conf /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 319. But according to the info from fdisk, 
                       sdc5 starts at sector 16384.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   226,235,479   226,233,432   7 HPFS/NTFS
/dev/sda2         226,243,395   254,405,339    28,161,945  82 Linux swap / Solaris
/dev/sda3         254,405,401   625,141,759   370,736,359   5 Extended
/dev/sda5         254,405,403   449,354,114   194,948,712  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   206,772,614   206,772,552   7 HPFS/NTFS
/dev/sdb2         206,772,615 1,465,144,064 1,258,371,450   f W95 Ext d (LBA)
/dev/sdb5         206,772,678   416,501,189   209,728,512   7 HPFS/NTFS
/dev/sdb6         416,501,253   626,229,764   209,728,512   7 HPFS/NTFS
/dev/sdb7         626,229,828   835,958,339   209,728,512   7 HPFS/NTFS
/dev/sdb8         835,958,403 1,045,686,914   209,728,512   7 HPFS/NTFS
/dev/sdb9       1,045,686,978 1,255,415,489   209,728,512   7 HPFS/NTFS
/dev/sdb10      1,255,415,553 1,465,144,064   209,728,512   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdc5              16,384   110,318,354   110,301,971   7 HPFS/NTFS
/dev/sdc6         110,321,664 1,953,519,615 1,843,197,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EC72C80A72C7D78A                       ntfs       Vista OS                      
/dev/sda2        c8e0c69b-2926-4abf-b373-79797d4ffda3   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb   ext4       10.04                         
/dev/sda: PTTYPE="dos" 
/dev/sdb10       B22A9A262A99E81D                       ntfs       CHIARA                        
/dev/sdb1        9ABAAE68BAAE411D                       ntfs       BARONI                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64BE1AC0BE1A8AA6                       ntfs       RESOURCES                     
/dev/sdb6        0E84A48684A4723F                       ntfs       The Boys                      
/dev/sdb7        BE94ADB294AD6E19                       ntfs       Jonathan                      
/dev/sdb8        5830B68E30B6731C                       ntfs       Shared Files                  
/dev/sdb9        4E30A23730A225C5                       ntfs       Teaching                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        429E50419E503021                       ntfs       Backup Configs                
/dev/sdc6        50720F13720EFD8A                       ntfs       Master Backup                 
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Baroni            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/Resource          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/Monsters          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/Jonathan          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/Shared            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb9        /media/Teaching          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb10       /media/Chiara            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/Configs           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc6        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/Vista OS          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/etc/lilo.conf: =============================

paragon_jboot
image=/etc/psrdisk
label="###NdenHden"
initrd=/etc/psr.img
append="paragon_lang=en"

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################
=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro  quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro  quiet  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ec72c80a72c7d78a
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=c8e0c69b-2926-4abf-b373-79797d4ffda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Baroni ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb5 /media/Resource ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb6 /media/Monsters ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb7 /media/Jonathan ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb8 /media/Shared ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb9 /media/Teaching ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb10 /media/Chiara ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc5 /media/Configs ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc6 /media/Backup ntfs defaults,nls=utf8,umask=000,gid=46     0    0

=================== sda5: Location of files loaded by Grub: ===================


 130.4GB: boot/grub/core.img
 133.7GB: boot/grub/grub.cfg
 138.9GB: boot/initrd.img-2.6.32-26-generic-pae
 158.6GB: boot/initrd.img-2.6.35-24-generic-pae
 130.7GB: boot/vmlinuz-2.6.32-26-generic-pae
 131.5GB: boot/vmlinuz-2.6.35-24-generic-pae
 158.6GB: initrd.img
 131.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 00 00 00 00 00  f0 f2 16 08 80 fa ff ff  |................|
00000010  00 00 00 00 00 00 00 00  05 00 00 00 00 00 00 00  |................|
00000020  30 d2 25 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |0.%.............|
00000030  30 e2 26 03 80 f8 ff ff  70 dd 25 03 80 f8 ff ff  |0.&.....p.%.....|
00000040  70 d2 25 03 80 f8 ff ff  10 d2 25 03 80 f8 ff ff  |p.%.......%.....|
00000050  0f 00 00 00 01 00 00 00  01 00 00 00 00 00 00 00  |................|
00000060  e0 1c 3d 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |..=.............|
00000070  40 d1 25 03 80 f8 ff ff  01 00 00 00 01 00 00 00  |@.%.............|
00000080  01 00 00 00 00 00 00 00  10 d2 25 03 80 f8 ff ff  |..........%.....|
00000090  50 24 15 08 80 fa ff ff  00 00 00 00 00 00 00 00  |P$..............|
000000a0  00 00 00 00 00 00 00 00  00 60 00 00 00 00 00 00  |.........`......|
000000b0  b0 d2 25 03 80 f8 ff ff  b0 d2 25 03 80 f8 ff ff  |..%.......%.....|
000000c0  68 8f 3e 03 80 f8 ff ff  68 6f 40 03 80 f8 ff ff  |h.>.....ho@.....|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  80 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000110  10 d3 25 03 80 f8 ff ff  10 d3 25 03 80 f8 ff ff  |..%.......%.....|
00000120  00 00 00 00 00 00 00 00  00 00 70 00 03 80 08 00  |..........p.....|
00000130  00 00 00 00 00 00 00 00  6c 00 78 00 00 00 00 00  |........l.x.....|
00000140  10 50 92 08 80 f8 ff ff  52 00 00 00 00 00 00 00  |.P......R.......|
00000150  ad 0b 00 00 00 00 00 00  ad 0b 00 00 00 00 00 00  |................|
00000160  28 d4 25 03 80 f8 ff ff  78 6f 40 03 80 f8 ff ff  |(.%.....xo@.....|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  02 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  80 00 00 00 00 00 00 00  0b 07 e8 00 28 00 00 00  |............(...|
000001a0  e0 ee 24 03 80 f8 ff ff  e0 de 25 03 80 f8 ff ff  |..$.......%.....|
000001b0  d0 4b ea 02 80 f8 ff ff  00 00 00 00 00 00 00 fe  |.K..............|
000001c0  ff ff 83 fe ff ff 02 00  00 00 68 ae 9e 0b 00 00  |..........h.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd 
[/HTML]

---

### Post by Jonners59 on 2010-12-22
OK, since creating the report and submitting, I deleted the partition sda6 where the faulty 10.10 install resided and tried a reboot.  It now has no GRUB menu.  It boots into a blank screen with some text and a line "GRUB"

I can not mount the PC.  HELP!!!

---

### Post by Jonners59 on 2010-12-22
Fixed the menu and the booting crash in below replies by following below....  though in the current installs the window does not show the UUID facility and nor is it in properties.  A bit of an oversight.  Fortunatly I label partitions!

I still can not start the new install (10.10) from the GRUB Menu, even with the changing splash quiet for nomodeset....  so I boot in to 2.6.32-26 (10.04), but it states it is 10.10 in the about Ubuntu?????  I'm confused.

new report....
[HTML]   	 	 	 	pre.western { font-family: "Times New Roman"; }pre.cjk { font-family: "Times New Roman"; }pre.ctl { font-family: "Times New Roman"; }p { margin-bottom: 0.21cm; }                  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 319. But according to the info from fdisk, 
                       sdc5 starts at sector 16384.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    22,173,695    22,171,648  83 Linux
/dev/sda2          53,192,704   254,404,607   201,211,904  83 Linux
/dev/sda3         254,405,401   625,141,759   370,736,359   5 Extended
/dev/sda5         254,405,403   449,354,114   194,948,712  83 Linux
/dev/sda4          22,173,696    53,192,703    31,019,008  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   206,772,614   206,772,552   7 HPFS/NTFS
/dev/sdb2         206,772,615 1,465,144,064 1,258,371,450   f W95 Ext d (LBA)
/dev/sdb5         206,772,678   416,501,189   209,728,512   7 HPFS/NTFS
/dev/sdb6         416,501,253   626,229,764   209,728,512   7 HPFS/NTFS
/dev/sdb7         626,229,828   835,958,339   209,728,512   7 HPFS/NTFS
/dev/sdb8         835,958,403 1,045,686,914   209,728,512   7 HPFS/NTFS
/dev/sdb9       1,045,686,978 1,255,415,489   209,728,512   7 HPFS/NTFS
/dev/sdb10      1,255,415,553 1,465,144,064   209,728,512   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdc5              16,384   110,318,354   110,301,971   7 HPFS/NTFS
/dev/sdc6         110,321,664 1,953,519,615 1,843,197,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3657705d-3b51-436b-9e65-026a3567771f   ext4       Boot                          
/dev/sda2        5acab084-8137-4b8a-ae8f-e7f0ae4ae354   ext4       Spare                         
/dev/sda3: PTTYPE="dos" 
/dev/sda4        4c1e8820-9746-4319-b08b-9652a8526a91   swap       SWAP                          
/dev/sda5        b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb   ext4       10.04                         
/dev/sda: PTTYPE="dos" 
/dev/sdb10       B22A9A262A99E81D                       ntfs       CHIARA                        
/dev/sdb1        9ABAAE68BAAE411D                       ntfs       BARONI                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64BE1AC0BE1A8AA6                       ntfs       RESOURCES                     
/dev/sdb6        0E84A48684A4723F                       ntfs       The Boys                      
/dev/sdb7        BE94ADB294AD6E19                       ntfs       Jonathan                      
/dev/sdb8        5830B68E30B6731C                       ntfs       Shared Files                  
/dev/sdb9        4E30A23730A225C5                       ntfs       Teaching                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        429E50419E503021                       ntfs       Backup Configs                
/dev/sdc6        50720F13720EFD8A                       ntfs       Master Backup                 
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Baroni            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/Resource          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/Monsters          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/Jonathan          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/Shared            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb9        /media/Teaching          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb10       /media/Chiara            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/Configs           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc6        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro  quiet  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro single  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro  quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro single  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=c8e0c69b-2926-4abf-b373-79797d4ffda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Baroni ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb5 /media/Resource ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb6 /media/Monsters ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb7 /media/Jonathan ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb8 /media/Shared ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb9 /media/Teaching ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb10 /media/Chiara ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc5 /media/Configs ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc6 /media/Backup ntfs defaults,nls=utf8,umask=000,gid=46     0    0

=================== sda5: Location of files loaded by Grub: ===================


 130.4GB: boot/grub/core.img
 181.9GB: boot/grub/grub.cfg
 138.9GB: boot/initrd.img-2.6.32-26-generic-pae
 158.6GB: boot/initrd.img-2.6.35-24-generic-pae
 130.7GB: boot/vmlinuz-2.6.32-26-generic-pae
 131.5GB: boot/vmlinuz-2.6.35-24-generic-pae
 158.6GB: initrd.img
 131.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 00 00 00 00 00  f0 f2 16 08 80 fa ff ff  |................|
00000010  00 00 00 00 00 00 00 00  05 00 00 00 00 00 00 00  |................|
00000020  30 d2 25 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |0.%.............|
00000030  30 e2 26 03 80 f8 ff ff  70 dd 25 03 80 f8 ff ff  |0.&.....p.%.....|
00000040  70 d2 25 03 80 f8 ff ff  10 d2 25 03 80 f8 ff ff  |p.%.......%.....|
00000050  0f 00 00 00 01 00 00 00  01 00 00 00 00 00 00 00  |................|
00000060  e0 1c 3d 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |..=.............|
00000070  40 d1 25 03 80 f8 ff ff  01 00 00 00 01 00 00 00  |@.%.............|
00000080  01 00 00 00 00 00 00 00  10 d2 25 03 80 f8 ff ff  |..........%.....|
00000090  50 24 15 08 80 fa ff ff  00 00 00 00 00 00 00 00  |P$..............|
000000a0  00 00 00 00 00 00 00 00  00 60 00 00 00 00 00 00  |.........`......|
000000b0  b0 d2 25 03 80 f8 ff ff  b0 d2 25 03 80 f8 ff ff  |..%.......%.....|
000000c0  68 8f 3e 03 80 f8 ff ff  68 6f 40 03 80 f8 ff ff  |h.>.....ho@.....|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  80 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000110  10 d3 25 03 80 f8 ff ff  10 d3 25 03 80 f8 ff ff  |..%.......%.....|
00000120  00 00 00 00 00 00 00 00  00 00 70 00 03 80 08 00  |..........p.....|
00000130  00 00 00 00 00 00 00 00  6c 00 78 00 00 00 00 00  |........l.x.....|
00000140  10 50 92 08 80 f8 ff ff  52 00 00 00 00 00 00 00  |.P......R.......|
00000150  ad 0b 00 00 00 00 00 00  ad 0b 00 00 00 00 00 00  |................|
00000160  28 d4 25 03 80 f8 ff ff  78 6f 40 03 80 f8 ff ff  |(.%.....xo@.....|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  02 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  80 00 00 00 00 00 00 00  0b 07 e8 00 28 00 00 00  |............(...|
000001a0  e0 ee 24 03 80 f8 ff ff  e0 de 25 03 80 f8 ff ff  |..$.......%.....|
000001b0  d0 4b ea 02 80 f8 ff ff  00 00 00 00 00 00 00 fe  |.K..............|
000001c0  ff ff 83 fe ff ff 02 00  00 00 68 ae 9e 0b 00 00  |..........h.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/HTML]

---

### Post by psusi on 2010-12-22
It looks like your sda5 contains a 10.10 install, but for some reason you labeled it as "10.04".

---

### Post by dino99 on 2010-12-22
sudo dpkg-reconfigure grub-pc

---

### Post by darkod on 2010-12-22
I have a question.
In the first results file posted you had Vista on sda1. You can clearly see that and the Vista boot files were also on sda1.
In the second results file posted sda1 is ext4 and there is no sign of windows there.

Is this something you did on purpose? Are you aware of this?

Lets clear this out before continuing to do anything else. Because it's important whether you expect to have windows there or not.

---

### Post by Quackers on 2010-12-22
darkod is correct - no Windows on the second bootscipt.
There are other peculiarities too.
Grub2 is installed in the mbr of sda and looks in partition 5 for boot files. That's normal.
The Grub2 that is installed in the mbr of sdb is looking at a UUID for boot files. That UUID however is partition 5 of sda. 
Also sdb5,6,7,8,9 and 10 all start at sector 63. That looks dodgy :-)

---

### Post by psusi on 2010-12-22
> **Quackers said:**
> 
Also sdb5,6,7,8,9 and 10 all start at sector 63. That looks dodgy :-)

What?  No they don't.

---

### Post by Quackers on 2010-12-22
```
sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

```

---

### Post by psusi on 2010-12-22
Ahh, the windows boot sector is wrong.  That should not hurt anything, other than rendering windows unable to boot from that partition.

---

### Post by oldfred on 2010-12-22
It looks like the OP was copying his first partition to other partitions maybe as a way of backing up??

---

### Post by Jonners59 on 2010-12-22
Sorry guys, I have been out getting the Chrimbo shopping as it is looming and it's my birthday tomorrow....  It was a nightmare.

Anyway.  I am impatient, so I starting playing whilst waiting for responses, besides this is our main machine we use a s a server and so have all our files and the telephone system on it AND she that MUST be obeyed gives me that look!:neutral:

What did I do up to MY reply (3):
I fiddled and played about.

The partition labelled 10.04 on SDA5 is my main install and the one I use most of the time.  I have been having some DNLA share issues so decided to create a new install and slowly build and copy over stuff, hence I set up partition SDA6 with 10.10, but that did not work.  10.10 would not boot.  I'd get to the GRUB menu, select it and it would freeze with a blank screen and flashing cursor.  I search the forum and came up with changing "quiet" and "splash" being changed to "nomodeset", but that did not work either and seemed to change back each time.

I therefore updated 10.04 to 10.10 via the Update Manager on partition sda5 (10.04).

The install went flawlessly, but it was after this I could not boot...  hence starting this thread.

I used my CD to start up and followed a number of threads including some of my old ones to get things going, but it would not work - due, I believe to conflicting GRUB installs.  Decided that as it would not boot anyway I may as well delete  potential places where GRUB could have been installed using gparted... so I deleted the partition 10.10, sda6 and when that did not work, I deleted sda1 with my Vista install - don't use it any more and as noted it had a bad boot anyway.    

I tried again and it started.  BUT I am not convinced I have removed ALL the GRUB installs, the audit mentions one in sdc somewhere and I have created a partition, sda1 that I have called Boot and would like the GRUB install to be in there.

I also, still can not mount in to 2.6.35-24

---

### Post by oldfred on 2010-12-22
If grub gets you to a menu, it is not a grub issue but an issue with Ubuntu booting. That you can boot the old kernel leads me to believe you have only partially updated. Are you still able to boot with the old kernel into a working system?

Also if you have video issues with a new install of 10.10, you are likely to have the same issue with the upgrade. What video card do you have. I have Nvidia and the nomodeset worked for me, but there are settings for others as well.

---

### Post by psusi on 2010-12-22
> **Jonners59 said:**
> BUT I am not convinced I have removed ALL the GRUB installs, the audit mentions one in sdc somewhere and I have created a partition, sda1 that I have called Boot and would like the GRUB install to be in there.

Don't worry about it; it isn't hurting anything.

> **Jonners59 said:**
> I also, still can not mount in to 2.6.35-24

Then worry about figuring out what is wrong there.  Boot that kernel with the nosplash noquiet options and see what happens.

---

### Post by Jonners59 on 2010-12-22
> **oldfred said:**
> 
If grub gets you to a menu, it is not a grub issue but an issue with Ubuntu booting. That you can boot the old kernel leads me to believe you have only partially updated. Are you still able to boot with the old kernel into a working system?

I think it was a GRUB issue when I started the thread but all my playing about earlier has moved on to what caused me to mess up the GRUB in the first place, that 10.10 will not boot.  To answer your question, I can get in to an old kernel.

> **oldfred said:**
> 
Also if you have video issues with a new install of 10.10, you are  likely to have the same issue with the upgrade. What video card do you  have. I have Nvidia and the nomodeset worked for me, but there are  settings for others as well.

I use nVidea, and always have upgrade issues, as you know.  The nomodeset did not work for me other than on the install of 10.10 via the CD - BUT I had to also select F6 and tick it in the options there along with the top item (I do not recall what it was called).  It then mounted and installed 10.10 from the CD, did an update and everything.  Looked good until I tried to get back in.  I think I even activated the nVidia driver as requested

> **psusi said:**
> 
Don't worry about it; it isn't hurting anything.
Then worry about figuring out what is wrong there.  Boot that kernel  with the nosplash noquiet options and see what happens.

I tried a couple of time.  It fails still.  I changed in both normal and recovery, but each time it stopped.  In normal it just showed a blank screen with curser and recovery it stopped at freeing initid memory - or something like that.......

---

### Post by psusi on 2010-12-22
The exact text that it shows when it gets stuck when you boot with the noquiet and nosplash options is needed to get a clue about what is going wrong.

---

### Post by Jonners59 on 2010-12-22
> **psusi said:**
> The exact text that it shows when it gets stuck when you boot with the noquiet and nosplash options is needed to get a clue about what is going wrong.
in normal kernal it shows none, just blank screen..

In recovery mode, it stops at the same place it did when installing on the CD before I did F6 and changed the setting...

 [299.948965]  freeing initrd memory: 10476k freed

---

### Post by oldfred on 2010-12-22
Try the editing of the grub lines for both standard and recovery modes with nomodeset.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

If you do not have Nvidia try some of these. Some have found the Generic  xforcevesa works.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Jonners59 on 2010-12-22
> **oldfred said:**
> Try the editing of the grub lines for both standard and recovery modes with nomodeset.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

If you do not have Nvidia try some of these. Some have found the Generic  xforcevesa works.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Oldfred
Tried this before many times...  It does not work, and as below gets to the ```
[299.948965]  freeing initrd memory: 10476k freed
``` line in recovery mode before stopping.....

In normal is just shows a blank screen with curser.

When I go back in and try again my settings have not been saved.

---

### Post by darkod on 2010-12-23
Are you still having issues with this?

You said the CD didn't work either until you hit F6 and ticked the options at the top. Boot with the CD again, look what the options are and select them again. Then try booting the CD in live mode. If that worked, boot without the CD, in the grub menu hit e while the normal mode entry is highlighted, and at the end of the line starting with linux add the same options you selected with F6.

I think they are acpi=off and/or noacpi, etc. Hit Ctrl+X to boot (if I remember correctly).

This is only temporary setting to try to boot. If that boots fine, you have to add them to the grub boot lines to make it permanent. You do this by editing /etc/default/grub with

gksudo gedit /etc/default/grub

Add the same commands in the line:
GRUB_CMDLINE_LINUX=""

You can add any commands you want to be executed in the grub boot sequence between the "". You have to run:
sudo update-grub

after that. That will make it permanent. But you first have to find out what makes it work, which commands/settings.

Couple of things:
1. What you call having more than 1 grub is irrelevant. Which bootloader you have on the MBR of which disk (and how many of them) means nothing usually. All you care is to have the correct, functioning bootloader on the MBR of the disk that you have set as first boot option in BIOS. For Ubuntu and Grub2 it is recommended grub2 to be installed on the same disk as the ubuntu installation, which means also that disk should be first in the boot order in BIOS.

2. When a new version does NOT boot the CD into live mode correctly, or does NOT work when installed on test partition (like you did), NEVER UPGRADE your current, working (older) system. In my limited Ubuntu experience, you will just make it unbootable (like you noticed).
If live mode or the test install does not work as expected, there is some glitch with your hardware. Until you find out what it is and how to solve it, upgrading your older version will just create the same glitch and the same unbootable situation.

One final thing. I think you mentioned using this as some type of server, or not? For machines that have important roles usually you wouldn't go around upgrading every 6 months just because a new release is out. In fact, in most cases important machines are only installed (and later upgraded) with LTS release, like the 10.04 was. Unless there is something in 10.10 that you need and no way to use it otherwise, don't upgrade your important systems until the next LTS is out, which should be 12.04 (in 2012) I guess.

---

### Post by Jonners59 on 2010-12-23
Darko
Many thanks for this, apologies for not getting back sooner.  My excuse is it's my birthday and have spent the day out in London's Wonderland with the family - GREAT and the wife bought me my childhood fantasy, an Airfix 1:24 scale DH Mosquito to build...  Back to reality!

> **darkod said:**
> 
Are you still having issues with this?
 

Yes, still problems, but as I can open in the old kernel now it is not panic stations.

Lots of tips and things to do here, so very grateful.

Point 1. 

> **darkod said:**
> Are you still having issues with this?

You said the CD didn't work either until you hit F6 and ticked the  options at the top. Boot with the CD again, look what the options are  and select them again. Then try booting the CD in live mode. If that  worked, boot without the CD, in the grub menu hit e while the normal  mode entry is highlighted, and at the end of the line starting with  linux add the same options you selected with F6.

I think they are acpi=off and/or noacpi, etc. Hit Ctrl+X to boot (if I remember correctly).

This is only temporary setting to try to boot. If that boots fine, you  have to add them to the grub boot lines to make it permanent. You do  this by editing /etc/default/grub with

gksudo gedit /etc/default/grub

Add the same commands in the line:
GRUB_CMDLINE_LINUX=""

You can add any commands you want to be executed in the grub boot sequence between the "". You have to run:
sudo update-grub

after that. That will make it permanent. But you first have to find out what makes it work, which commands/settings.

OK, makes sense, also explains why my changes did not stay when I did so in the GRUB menu.  No one had explained that yet.  So far I have also been suggested to change the quiet and splash bit to nomodeset.  Do I do this by replacing the q & s in this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

or add to this:

GRUB_CMDLINE_LINUX=""

> **darkod said:**
> 
Couple of things:
1. What you call having more than 1 grub is irrelevant. Which bootloader  you have on the MBR of which disk (and how many of them) means nothing  usually. All you care is to have the correct, functioning bootloader on  the MBR of the disk that you have set as first boot option in BIOS. For  Ubuntu and Grub2 it is recommended grub2 to be installed on the same  disk as the ubuntu installation, which means also that disk should be  first in the boot order in BIOS.

I do not agree with you experts in this.  One of the problems I found was I was updating the GRUB via sudo update-grub, but the menu on start never changed...  It could only be another GRUB that I was not accessing, so having more than one CAN be a problem, and why also have that complexity, just keep things tidy.  Remove anything not required and save any possibility of errors.  This also means that re the above suggestion, I still do not know if I will be correcting the correct GRUB conf!!!!  I have eliminated two possibilities, so I hope so.

> **darkod said:**
> 
 2. When a new version does NOT boot the CD into live mode correctly, or  does NOT work when installed on test partition (like you did), NEVER  UPGRADE your current, working (older) system. In my limited Ubuntu  experience, you will just make it unbootable (like you noticed).
 If live mode or the test install does not work as expected, there is  some glitch with your hardware. Until you find out what it is and how to  solve it, upgrading your older version will just create the same glitch  and the same unbootable situation.
 

I think I agree with this, learning the hard way!  I expected it to keep the configs and setting and so just work with the new bits...

> **darkod said:**
> 
 One final thing. I think you mentioned using this as some type of  server, or not? For machines that have important roles usually you  wouldn't go around upgrading every 6 months just because a new release  is out. In fact, in most cases important machines are only installed  (and later upgraded) with LTS release, like the 10.04 was. Unless there  is something in 10.10 that you need and no way to use it otherwise,  don't upgrade your important systems until the next LTS is out, which  should be 12.04 (in 2012) I guess.

Actually, I had the same issue when I upgraded to 10.04, but I do take your point, again lesson learned....  HOWEVER, I was looking at a fresh install as I was having some issues with DNLA shares, but I managed to sort that out today, so all red herring in the end.

Cheers and many thanks

I will try these out after Christmas...  Bets wishes to all

---

### Post by darkod on 2010-12-23
> 
OK, makes sense, also explains why my changes did not stay when I did so  in the GRUB menu.  No one had explained that yet.  So far I have also  been suggested to change the quiet and splash bit to nomodeset.  Do I do  this by replacing the q & s in this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

or add to this:

GRUB_CMDLINE_LINUX=""


If nomodeset helps, you would always simply add it to the boot line. Basically you can add it to either of the lines you quoted. I don't know why but the developers have decided to create one "default" command line, and another "for everything else". All commands get appended together.
Usually you would add to the second one and leave the default one alone, but it works either way.
Note: the advice to replace quiet & splash with nomodeset is not exactly that. If nomodeset helps, it will work with just adding it too.
The removal of q & s is suggested as temporary while doing your troubleshooting. You wouldn't delete them from the /etc/default/grub permanently unless you prefer to see the scrolling text on every boot.

So adding nomodeset (or other parameters like acpi=off) and temporarily deleting q & s are two different steps. You don-t actually need to replace q & s.

Cheers and Merry Christmas!

---

### Post by Jonners59 on 2010-12-24
Ah, excellent....  I will add the apti bit, try, then the nomodeset and only if that does not work take out Q&S...  I'll have a go in a cople of days.

Cheers have a great Chrimbo  :popcorn:

---

### Post by Jonners59 on 2010-12-27
> **darkod said:**
> If nomodeset helps, you would always simply add it to the boot line. Basically you can add it to either of the lines you quoted. I don't know why but the developers have decided to create one "default" command line, and another "for everything else". All commands get appended together.
Usually you would add to the second one and leave the default one alone, but it works either way.
Note: the advice to replace quiet & splash with nomodeset is not exactly that. If nomodeset helps, it will work with just adding it too.
The removal of q & s is suggested as temporary while doing your troubleshooting. You wouldn't delete them from the /etc/default/grub permanently unless you prefer to see the scrolling text on every boot.

So adding nomodeset (or other parameters like acpi=off) and temporarily deleting q & s are two different steps. You don-t actually need to replace q & s.

Cheers and Merry Christmas!


Hi Darkod
I hope you had a great Christmas...  Ours was hectic, and not quite over yet.

Re this project.  The time has made me rethink and I realise that before I plunge in I do need to ask some questions to reassure myself.

I went in to the config you suggested and noticed that the line items are for only one kernel, but the settings for the old do not work on the new, so IF I change them which kernel will it change them for and how will it affect the other?

I guess I am a little confused as to which I am affecting in this mod and need assurances that all will be OK.

I hope this makes sense.

---

### Post by dino99 on 2010-12-27
sorry i've not read the whole thread but is dkms installed (check with synaptic, if not, install it) ?

when things goes wrong on my end, i do this: remove/purge then reinstall the package (in your case: grub-pc)

---

### Post by darkod on 2010-12-27
> **Jonners59 said:**
> Hi Darkod
I hope you had a great Christmas...  Ours was hectic, and not quite over yet.

Re this project.  The time has made me rethink and I realise that before I plunge in I do need to ask some questions to reassure myself.

I went in to the config you suggested and noticed that the line items are for only one kernel, but the settings for the old do not work on the new, so IF I change them which kernel will it change them for and how will it affect the other?

I guess I am a little confused as to which I am affecting in this mod and need assurances that all will be OK.

I hope this makes sense.

I am only 95% sure but I think adding parameters to the lines in the grub config file mentioned above is for all versions of ubuntu you have.

If I understood right, actually with this change we are trying to make the kernel that doesn't work, work. Right?

So, as explained earlier, you should follow this general procedure:
1. In the grub boot menu, highlight the newer kernel (10.10), but don't hit Enter. Hit 'e' instead.
2. You will see the boot lines for that particular kernel version. Position the cursor (with the arrows keys) at the end of the line starting with 'linux' (after quiet & splash) and add what ever parameters you think help, like 'nomodeset', 'acpi=off', 'noacpi', etc. Sorry, I don't know them all on top of my head, rarely use them.
3. Hit Ctrl+X to try to boot the kernel with this temp change of the boot lines.
4. If that didn't work, you either need to try with another parameter, so try again. Or the kernel can't work what ever you do. In that case there is no need to continue with this.

5. Once you find the parameter(s) that helped the kernel boot successfully, just open the config files as discussed and add that parameter where we said.

Any more doubts, ask first. You are doing the right thing by asking first.

There is another thing I noticed but it's not urgent and we can discuss it later. First make the 10.10 boot with the correct parameter.

---

### Post by Jonners59 on 2010-12-27
Thanks Darkod....

I'll try tomorrow and keep you posted

---

### Post by Jonners59 on 2010-12-28
> **darkod said:**
> I am only 95% sure but I think adding parameters to the lines in the grub config file mentioned above is for all versions of ubuntu you have.

If I understood right, actually with this change we are trying to make the kernel that doesn't work, work. Right?

So, as explained earlier, you should follow this general procedure:
1. In the grub boot menu, highlight the newer kernel (10.10), but don't hit Enter. Hit 'e' instead.
2. You will see the boot lines for that particular kernel version. Position the cursor (with the arrows keys) at the end of the line starting with 'linux' (after quiet & splash) and add what ever parameters you think help, like 'nomodeset', 'acpi=off', 'noacpi', etc. Sorry, I don't know them all on top of my head, rarely use them.
3. Hit Ctrl+X to try to boot the kernel with this temp change of the boot lines.
4. If that didn't work, you either need to try with another parameter, so try again. Or the kernel can't work what ever you do. In that case there is no need to continue with this.

5. Once you find the parameter(s) that helped the kernel boot successfully, just open the config files as discussed and add that parameter where we said.

Any more doubts, ask first. You are doing the right thing by asking first.

There is another thing I noticed but it's not urgent and we can discuss it later. First make the 10.10 boot with the correct parameter.

BRILLIANT!!!

Worked a treat.

I deleted "quiet" and "splash" from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and made it "nomodeset"

I then changed GRUB_CMDLINE_LINUX="      splash"  			 		to "acpi=off"

And it boots up.  It IS very slow and it did, though I suggest this is the actual upgrade, cause problems with my Sun Virtual Box install.  Needed an extra item installed and a cmd line, and am having boot issues with the VM.....  But all that is another problem to resolve

Many thanks for the fix  Have a great New Year....

---

### Post by darkod on 2010-12-28
Great. Glad it worked out. But I have to notice the usual way would be to leave the LINUX_DEFAULT value as "quiet splash" and just to change the LINUX line to "nomodeset acpi=off".

Another thing I noticed from your second boot info script results, is that it seems you have a "broken" grub installed on sda, and you are probably booting from the grub installed on sdb even though your ubuntu install is on sda5.

Booting with grub installed on a different disk than the ubuntu installation can lead to some delays (not always).

Why I think the grub from sda doesn't work is because it says in the results it is looking for (msdos)/boot/grub and 'msdos' is not an UUID and does not seem to be any label.

The grub from sdb is looking for the correct UUID/boot/grub and should be working fine.

If you feel like tackling this, there is easy way to test how you boot. If your board has a Quick Boot menu, and most newer boards have, you usually access it by hitting F12 during boot.
If you can, select to boot from sda, the 320GB disk. It should load a "broken" grub.
If you do the same but select to boot from sdb it should load your working grub.

Even without doing any tests it's easy to reinstall grub to the MBR of sda and that way you are sure you have a working grub on sda. Just boot your ubuntu like you do right now, and in terminal execute:

sudo grub-install /dev/sda

That will install it to the MBR of sda (NOTE: There should NOT be a number in it, like /dev/sda5, only /dev/sda)

Then in your BIOS make sure sda is the first disk to boot from. With grub reinstalled there it should work fine. And the fastest way to boot with grub (the current grub2 actually) is if it's on the same disk as the ubuntu installation.

---

### Post by Jonners59 on 2010-12-29
> **darkod said:**
> Great. Glad it worked out. But I have to notice the usual way would be to leave the LINUX_DEFAULT value as "quiet splash" and just to change the LINUX line to "nomodeset acpi=off".

OK, done this.  Changed to suggested...  See comment at the end.

> **darkod said:**
> 
Another thing I noticed from your second boot info script results, is  that it seems you have a "broken" grub installed on sda, and you are  probably booting from the grub installed on sdb even though your ubuntu  install is on sda5.

Booting with grub installed on a different disk than the ubuntu installation can lead to some delays (not always).

Why I think the grub from sda doesn't work is because it says in the  results it is looking for (msdos)/boot/grub and 'msdos' is not an UUID  and does not seem to be any label.

The grub from sdb is looking for the correct UUID/boot/grub and should be working fine.

If you feel like tackling this, there is easy way to test how you boot.  If your board has a Quick Boot menu, and most newer boards have, you  usually access it by hitting F12 during boot.
If you can, select to boot from sda, the 320GB disk. It should load a "broken" grub.
If you do the same but select to boot from sdb it should load your working grub.

Even without doing any tests it's easy to reinstall grub to the MBR of  sda and that way you are sure you have a working grub on sda. Just boot  your ubuntu like you do right now, and in terminal execute:

sudo grub-install /dev/sda

That will install it to the MBR of sda (NOTE: There should NOT be a number in it, like /dev/sda5, only /dev/sda)

Then in your BIOS make sure sda is the first disk to boot from. With  grub reinstalled there it should work fine. And the fastest way to boot  with grub (the current grub2 actually) is if it's on the same disk as  the ubuntu installation.

This is exactly what this thread is about and what I had issue with.  I kept being told it did not matter....  But every time I installed or updated grub I never knew which it was affecting and in many cases did not change the one I wanted, so I wanted to get rid of them, and leave one.

So, I have done as you have suggested, though I'd like to completly remove all irrelevent instances, i.e. the one on sdb.

The effect of this change.

The first is it opened the GRUB menu a little quicker, but the default was "mem test", which I have subsequently changed (I hope, depends which the config is affecting).
Then it starts to load...  Now the trouble starts.
It hangs for about 1 minute per window...  So blank screen, then Ubuntu logo with mauve background, then just mauve background, then the splash...  so in all about 3 to 4 minutes to load!  Needless to say my heart stopped at each window when it did not seem to want to move on.

Then on shut down it also takes for ever...  in the end I had to force it to shut down by hitting the hard restart button on the PC.

The reboot was the same as the 1st boot, very slow.....

new GRUB conf:
  	 	 	 	pre.western { font-family: "Times New Roman"; }pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.21cm; }  [HTML]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset acpi=off"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"[/HTML] 

new Scrip output:
  	 	 	 	pre.western { font-family: "Times New Roman"; }pre.cjk { font-family: "Times New Roman"; }pre.ctl { font-family: "Times New Roman"; }p { margin-bottom: 0.21cm; }                [HTML]  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 319. But according to the info from fdisk, 
                       sdc5 starts at sector 16384.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    22,173,695    22,171,648  83 Linux
/dev/sda2          53,192,704   254,404,607   201,211,904  83 Linux
/dev/sda3         254,405,401   625,141,759   370,736,359   5 Extended
/dev/sda5         254,405,403   449,354,114   194,948,712  83 Linux
/dev/sda4          22,173,696    53,192,703    31,019,008  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   206,772,614   206,772,552   7 HPFS/NTFS
/dev/sdb2         206,772,615 1,465,144,064 1,258,371,450   f W95 Ext d (LBA)
/dev/sdb5         206,772,678   416,501,189   209,728,512   7 HPFS/NTFS
/dev/sdb6         416,501,253   626,229,764   209,728,512   7 HPFS/NTFS
/dev/sdb7         626,229,828   835,958,339   209,728,512   7 HPFS/NTFS
/dev/sdb8         835,958,403 1,045,686,914   209,728,512   7 HPFS/NTFS
/dev/sdb9       1,045,686,978 1,255,415,489   209,728,512   7 HPFS/NTFS
/dev/sdb10      1,255,415,553 1,465,144,064   209,728,512   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdc5              16,384   110,318,354   110,301,971   7 HPFS/NTFS
/dev/sdc6         110,321,664 1,953,519,615 1,843,197,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3657705d-3b51-436b-9e65-026a3567771f   ext4       Boot                          
/dev/sda2        5acab084-8137-4b8a-ae8f-e7f0ae4ae354   ext4       Spare                         
/dev/sda3: PTTYPE="dos" 
/dev/sda4        4c1e8820-9746-4319-b08b-9652a8526a91   swap       SWAP                          
/dev/sda5        b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb   ext4       10.04                         
/dev/sda: PTTYPE="dos" 
/dev/sdb10       B22A9A262A99E81D                       ntfs       CHIARA                        
/dev/sdb1        9ABAAE68BAAE411D                       ntfs       BARONI                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64BE1AC0BE1A8AA6                       ntfs       RESOURCES                     
/dev/sdb6        0E84A48684A4723F                       ntfs       The Boys                      
/dev/sdb7        BE94ADB294AD6E19                       ntfs       Jonathan                      
/dev/sdb8        5830B68E30B6731C                       ntfs       Shared Files                  
/dev/sdb9        4E30A23730A225C5                       ntfs       Teaching                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        429E50419E503021                       ntfs       Backup Configs                
/dev/sdc6        50720F13720EFD8A                       ntfs       Master Backup                 
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Baroni            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/Resource          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/Monsters          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/Jonathan          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/Shared            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb9        /media/Teaching          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb10       /media/Chiara            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/Configs           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc6        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro nomodeset acpi=off  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro single nomodeset acpi=off
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=c8e0c69b-2926-4abf-b373-79797d4ffda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Baroni ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb5 /media/Resource ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb6 /media/Monsters ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb7 /media/Jonathan ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb8 /media/Shared ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb9 /media/Teaching ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb10 /media/Chiara ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc5 /media/Configs ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc6 /media/Backup ntfs defaults,nls=utf8,umask=000,gid=46     0    0

=================== sda5: Location of files loaded by Grub: ===================


 130.3GB: boot/grub/core.img
 181.9GB: boot/grub/grub.cfg
 147.7GB: boot/initrd.img-2.6.35-24-generic-pae
 131.5GB: boot/vmlinuz-2.6.35-24-generic-pae
 147.7GB: initrd.img
 131.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 00 00 00 00 00  f0 f2 16 08 80 fa ff ff  |................|
00000010  00 00 00 00 00 00 00 00  05 00 00 00 00 00 00 00  |................|
00000020  30 d2 25 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |0.%.............|
00000030  30 e2 26 03 80 f8 ff ff  70 dd 25 03 80 f8 ff ff  |0.&.....p.%.....|
00000040  70 d2 25 03 80 f8 ff ff  10 d2 25 03 80 f8 ff ff  |p.%.......%.....|
00000050  0f 00 00 00 01 00 00 00  01 00 00 00 00 00 00 00  |................|
00000060  e0 1c 3d 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |..=.............|
00000070  40 d1 25 03 80 f8 ff ff  01 00 00 00 01 00 00 00  |@.%.............|
00000080  01 00 00 00 00 00 00 00  10 d2 25 03 80 f8 ff ff  |..........%.....|
00000090  50 24 15 08 80 fa ff ff  00 00 00 00 00 00 00 00  |P$..............|
000000a0  00 00 00 00 00 00 00 00  00 60 00 00 00 00 00 00  |.........`......|
000000b0  b0 d2 25 03 80 f8 ff ff  b0 d2 25 03 80 f8 ff ff  |..%.......%.....|
000000c0  68 8f 3e 03 80 f8 ff ff  68 6f 40 03 80 f8 ff ff  |h.>.....ho@.....|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  80 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000110  10 d3 25 03 80 f8 ff ff  10 d3 25 03 80 f8 ff ff  |..%.......%.....|
00000120  00 00 00 00 00 00 00 00  00 00 70 00 03 80 08 00  |..........p.....|
00000130  00 00 00 00 00 00 00 00  6c 00 78 00 00 00 00 00  |........l.x.....|
00000140  10 50 92 08 80 f8 ff ff  52 00 00 00 00 00 00 00  |.P......R.......|
00000150  ad 0b 00 00 00 00 00 00  ad 0b 00 00 00 00 00 00  |................|
00000160  28 d4 25 03 80 f8 ff ff  78 6f 40 03 80 f8 ff ff  |(.%.....xo@.....|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  02 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  80 00 00 00 00 00 00 00  0b 07 e8 00 28 00 00 00  |............(...|
000001a0  e0 ee 24 03 80 f8 ff ff  e0 de 25 03 80 f8 ff ff  |..$.......%.....|
000001b0  d0 4b ea 02 80 f8 ff ff  00 00 00 00 00 00 00 fe  |.K..............|
000001c0  ff ff 83 fe ff ff 02 00  00 00 68 ae 9e 0b 00 00  |..........h.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/HTML]

---

### Post by darkod on 2010-12-29
Removing grub2 from sdb is very easy, but if that's the only one working for you it can leave you with unbootable system. So lets not do anything about that yet.

I'm still confused why the results say:

```

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for [COLOR=Red](,msdos5)[/COLOR]/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb)/boot/grub.

```

When it is looking on the same disk, as in the case on sda, it should just say 'in partition #5 for /boot/grub'.
Unless this is something introduced with 10.10 (I'm still using 10.04).

When using the grub2 from sda, it knows to look in partition #5 and in there it should immediately look for the folder /boot/grub, not for anything in the path in front of it.
When using grub2 from sdb, it correctly locates sda5 by its UUID, and again looking directly for the folder /boot/grub. In other words, not for UUID/(,msdos5)/boot/grub.

Why is there (,msdos5) in the first case I have no idea. This might, or might not have something to do with booting with grub2 from sda not working.

Before all of this, when you also had vista, were you trying some setup different from the default, like using EasyBCD or similar? There might be remains of earlier setups.

Also, it is strange that you have Lilo bootloader on sdc too, any idea how it got there?

For the time being boot your computer from sdb because that works if I got it right.

Concerning the grub2 config files. You do have grub2 installed on both sda and sdb but that is just the first part of the package. It looks for the second part (stages) at the same location, sda5/boot/grub so you do not have two different grubs in effect. Also, you have only one single ubuntu installation. So any changes done to the config files should work regardless whether booting from sda or sdb. At least in theory.

Also the grub.cfg file in the 10_linux section does say that it's setting the root as (hd0,msdos5) which is also weird. Again, if this is not something they introduced in 10.10, this value should be (hd0,5), not (hd0,msdos5).

Was the 10.04 you had before upgrading to 10.10 a clean install or upgrade from earlier version? Ubuntu started using grub2 since 9.10 and if you had upgraded your system from previos version (like 9.04, 8.10 etc) one by one, there might be remains of grub1 together with grub2. But the boot info script does not seem to locate any such remains.

---

### Post by Jonners59 on 2010-12-29
> **darkod said:**
> Removing grub2 from sdb is very easy, but if that's the only one working for you it can leave you with unbootable system. So lets not do anything about that yet.

OK, I'm happy with that.  I just want it clean so that it works well, is easy to maintain and future upgrades do not cause this issue.


> **darkod said:**
> 
I'm still confused why the results say:

```

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for [COLOR=Red](,msdos5)[/COLOR]/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb)/boot/grub.

```When it is looking on the same disk, as in the case on sda, it should just say 'in partition #5 for /boot/grub'.
Unless this is something introduced with 10.10 (I'm still using 10.04).

When using the grub2 from sda, it knows to look in partition #5 and in  there it should immediately look for the folder /boot/grub, not for  anything in the path in front of it.
When using grub2 from sdb, it correctly locates sda5 by its UUID, and  again looking directly for the folder /boot/grub. In other words, not  for UUID/(,msdos5)/boot/grub.

Why is there (,msdos5) in the first case I have no idea. This might, or  might not have something to do with booting with grub2 from sda not  working.

Before all of this, when you also had vista, were you trying some setup  different from the default, like using EasyBCD or similar? There might  be remains of earlier setups

No, but IF I RECALL CORRECTLY, I may have done my first install via Wubi....  Maybe?  But otherwise I install from CD, obtained from the online ordering (do not trust myself to do it properly) or upgrade via Upgrade Manager and let it tell me what to do.


> **darkod said:**
> Also, it is strange that you have Lilo bootloader on sdc too, any idea how it got there?

For the time being boot your computer from sdb because that works if I got it right.

Concerning the grub2 config files. You do have grub2 installed on both  sda and sdb but that is just the first part of the package. It looks for  the second part (stages) at the same location, sda5/boot/grub so you do  not have two different grubs in effect. Also, you have only one single  ubuntu installation. So any changes done to the config files should work  regardless whether booting from sda or sdb. At least in theory.

Also the grub.cfg file in the 10_linux section does say that it's  setting the root as (hd0,msdos5) which is also weird. Again, if this is  not something they introduced in 10.10, this value should be (hd0,5),  not (hd0,msdos5).

None what so ever.  This has been my concern and the pint of the Thread.....I did try earlier versions, but could not get on with them.  My first successful install was 9.10, which I was happy with.  I did have a problem and did try and clear all out - I can not recall the circumstances, but what I do remember is that it prevented me from being able to install any new, but then I completely uninstalled/deleted the disk since, which is how I finally managed to get 9.10 working, and then 10.04...  So a bit lost on this one.


> **darkod said:**
> 
  Was the 10.04 you had before upgrading to 10.10 a clean install or  upgrade from earlier version? Ubuntu started using grub2 since 9.10 and  if you had upgraded your system from previos version (like 9.04, 8.10  etc) one by one, there might be remains of grub1 together with grub2.  But the boot info script does not seem to locate any such  remains.

I tried the CD, but it would not work, then found changing the boot script to nomodeset and acpi=off I could get it to boot and install, which I completed.  I then found I could not get in to it after the reboot.

I then changed the update manager settings and the option for upgrade came up so I tried that way hoping it would keep my settings and be able to boot ( a lesson learnt, it does not).  That is when I tried to get a fix, and raised two threads.  One for the boot and this one for the multi GRUB.  In my frustration to get this going I deleted the CD install, I then deleted the Vista partition, before I started getting support responses.  Hence I managed to clear out a few boot devices, but still when I updated GRUB from within the Ubuntu the new config did not match the menu I got, it does now incidentally.

FYI:  all the threads I have relating to this machine and booting, including the current.
  	 	 	 	p { margin-bottom: 0.21cm; }a:link {  }  [http://ubuntuforums.org/showthread.php?t=1613644](http://ubuntuforums.org/showthread.php?t=1613644)
 

 [http://ubuntuforums.org/showthread.php?t=1577860](http://ubuntuforums.org/showthread.php?t=1577860)
 

 [http://ubuntuforums.org/showthread.php?t=1467211](http://ubuntuforums.org/showthread.php?t=1467211)
 

 [http://ubuntuforums.org/showthread.php?t=1466166](http://ubuntuforums.org/showthread.php?t=1466166)
 

 [http://ubuntuforums.org/showthread.php?t=1467225](http://ubuntuforums.org/showthread.php?t=1467225)
 

Hope this helps

---

### Post by darkod on 2010-12-29
PS.

In your post #30 you explained the problems when trying to boot from sda, basically it doesn't work.

Before trying to boot from sda, did you execute the grub-install command I suggested or not?

I'm asking just out of curiosity because if you did NOT execute it, I already said I expected the grub2 on sda to be broken.

But if you DID execute it first, and booting from sda doesn't work after that too, I'm puzzled why not.

Relating to your latest post, I will have to read it in detail and think about it later, but on first sight there is nothing 'bad' or 'wrong' in it. Doesn't help understand about that (,msdos5) thing.

---

### Post by Jonners59 on 2010-12-29
> **darkod said:**
> PS.

In your post #30 you explained the problems when trying to boot from sda, basically it doesn't work.

Before trying to boot from sda, did you execute the grub-install command I suggested or not?

I'm asking just out of curiosity because if you did NOT execute it, I already said I expected the grub2 on sda to be broken.

But if you DID execute it first, and booting from sda doesn't work after that too, I'm puzzled why not.

Yes, I did, though I had done it before, I repeated as requested just to keep the flow, as it were.

> **darkod said:**
> 
Relating to your latest post, I will have to read it in detail and think  about it later, but on first sight there is nothing 'bad' or 'wrong' in  it. Doesn't help understand about that (,msdos5) thing.
Yes, sorry it was so long but I tried to give you all I can to figure this out.  You can always ignore stuff.  PS. also note that in an old thread I raise the same issue of multi Grub.  Same machine.

If I knew half what you know I'd be contented, so please take your time, it is appreciated.  I am just trying to clear a backlog of IT bits before work gets manic again next week.

---

### Post by darkod on 2010-12-29
I can't figure it out. :(

At this point I would suggest:
1. Open a new thread with title asking for grub2 help, and post the latest results.txt file you have. Especially since you already marked this thread as solved.
2. Your other threads mention lots of problems but they are from April/May. If I can suggest, in this new thread ask only about this grub2 issue, don't mention anything else. Some people are put off by that. We are all here for free. Stick to the point and be precise, don't add too many other issues too. Besides, I think we ironed out most of them, this silly grub2 issue is the main problem now.

Sorry I can't help more right now, I hope someone else might have an idea seeing your new thread. Cheers.

---

### Post by darkod on 2010-12-29
I don't think it will help but we might as well try to reinstall grub2 to sda as if ubuntu couldn't boot at all. In other words, from live mode.

Boot your computer with your ubuntu cd or usb stick in live mode (the Try Ubuntu option). Not the hdd installed ubuntu.

In live mode the commands to reinstall grub2 are slightly different because you need to tell it where to find the ubuntu install. In terminal execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Note that in the first line it is /dev/sda5 and in the second /dev/sda. This is NOT a mistake, there should NOT be a '5' in the second line.

After that reboot and try to boot from sda, not from sdb as usual. Lets see if it helps.

---

### Post by Jonners59 on 2010-12-29
Sorry, darkod
Tried it and failed...

I mount sda5, no problems

I then do the install cmd and get the error message (almost exact words).
/user/sbin/grub-probe : error: can't find a device for boot-grub (is dev mounted?)

I check by using gparted and it is shown as mounted.  I shut down gParted and tried again.

I then tried shutting down the terminal and unmounting via gParted
I then went in to external devices in "Places" and mounted other partitions on that drive (sda5 was not listed at first).  It then appeared after the others had mounted, so I tried to mount from there without success, so I mounted from gParted.

I then opened the terminal again and tried all over.  Still would not install, same message.

I have rebooted the machine.....

---

### Post by darkod on 2010-12-30
So, it's complaining it can't find the folder /boot/grub even though it's on /dev/sda5 (at least it should be).

One option is if the disk has changed the name from sda, for example if using a usb stick it can become sda and push the hdd 'names' by one letter.

You can check this in live mode with:

sudo fdisk -l (small L)

It will list all disks, including and usb sticks. Double check that sda is what we think it is, the 320GB disk.
If you used a CD, forget about this.

Otherwise this message might give us a direction for troubleshooting, but I don't know grub2 that good to know what it is complaining about right away.

Also I notice that the sda1 partition is labeled Boot, why? You didn't have a separate /boot partition created while installing ubuntu originally, right? Because when separate /boot partition is used some grub files go there and that might be a reason why it complains that it can't find them on sda5. But the script results don't report anything of this kind on sda1.

---

### Post by Jonners59 on 2010-12-30
> **darkod said:**
> So, it's complaining it can't find the folder /boot/grub even though it's on /dev/sda5 (at least it should be).

One option is if the disk has changed the name from sda, for example if using a usb stick it can become sda and push the hdd 'names' by one letter.

You can check this in live mode with:

sudo fdisk -l (small L)

It will list all disks, including and usb sticks. Double check that sda is what we think it is, the 320GB disk.
If you used a CD, forget about this.

Otherwise this message might give us a direction for troubleshooting, but I don't know grub2 that good to know what it is complaining about right away.

Also I notice that the sda1 partition is labeled Boot, why? You didn't have a separate /boot partition created while installing ubuntu originally, right? Because when separate /boot partition is used some grub files go there and that might be a reason why it complains that it can't find them on sda5. But the script results don't report anything of this kind on sda1.

This machine has no external storage devices attached, all are internal Hard drives;
sda = 350Gb                OS
sdb = 750GB and         Storage/Docs
sdc=1T                        Backup + Configs

The Boot partition, if I recall was post install.  I am trying to get more sophisticated in my install and upgrades, plus as I had been having problems I was planning to move GRUB there, so that in the event of an upgrade or new build, the GRUB was not affected, just needed a reconfig.

Likewise I want to do the same with etc and home, and any other directory that can be extracted and so not affected by upgrades.

As all this is conceptual and experimental, nothing has been done as yet, so if you feel it should go, it can.

PS.  Why was I not be able to install grub in the live mode with the installed kernel.  I assume I am making sense.  Why did I have to reboot in to the CD?

---

### Post by darkod on 2010-12-30
We tried installing grub2 to sda when the hdd installation was booted, but it didn't make any change. You said it can't boot from sda after that too.
So the idea was to try install with the cd running in live mode, if it made any change. But in this case it didn't even want to install grub2 which is very strange.

I'm not even sure if the grub's on sda and sdb are now mixed up and from the two different installs (the 10.04 you had and the new 10.10 you tried).

Which bring me to another tip: In case you didn't know, if you already have one linux and grub installed (like you had 10.04), with any future installation you do NOT need to install the grub bootloader. In Ubuntu, this option is on the last installation screen, just before clicking the Install button click the Advanced button first. It will give you options to select on which hdd to install grub2, or unselect to install it at all.

If the new version that you are adding comes with a more advanced version of grub that you want to use, you will probably want to install it. But otherwise, just leave the grub you have to run the show. In your second, third, etc install you can safely select not to install a bootloader.

In that case, after the install you simply boot your first version (the first time it will still be the only one in the boot menu, don't worry), and once loaded just execute the update-grub command which will locate the new OS installed and update the boot menu.

Back to your issue. At this point of time I wonder if it's worth continuing. You can boot the system, which is what we wanted to achieve, and now you know which parameters to add so that you can boot fine (you might need to use them in future versions too).
Think whether you are happy with things as they are, although not ideal, and either let it go for now, or create new thread specifically about this grub2 issue.

If you are happy as it is, I would leave it until your next clean install (not upgrade). A clean install doesn't care what you had or did earlier, that's why it's called that. :)

---

### Post by Jonners59 on 2010-12-30
I'll take your advise, and leave for now, but for one thing...  You mention a new install may do the trick, well I have a spare partition on sda which would PROBABLY create as sda6...  If I install from the CD in to there and ask for a new Grub Bootloader.....  that may work?

I can always delete it later.  My only real concern is that there is this rogue installer on sdb which keeps cropping up.....

If you think the installing a new partition would work then I'll give it a go, if not I'll leave it for now.

---

### Post by darkod on 2010-12-30
The same idea popped into my mind too.
Just a small note: If I recall correctly, you do NOT have a spare partition, you have unallocated (unpartitioned) space after you deleted the partition that was there. There is a big difference between unallocated space and partition.

If the space is unallocated, you have two options when installing. One is to use the guided option Use Largest Available Free space, and the other is to use the Manual (Advanced) option.

In the manual option you select the unallocated space and create the partition yourself. I prefer the manual way because you have total control, but it's up to you.

If you decide to go the manual way, here is a quick guide (some of options might be called differently, don't remember the exact text but it's easy when you have the window in front of you, you'll get it):
1. Select the unallocated space, and create a new partition from it.
2. For the partition, select it to be logical, ext4 filesystem, and mount point /.
3. The existing swap partition should be picked up and selected for swap automatically, but just make sure in the disk/partitions list that it's marked to be used as swap.

Which ever way you decide to install, in the last screen before clicking Install click on the Advanced button and select grub2 to be installed on /dev/sda to make sure it goes to disk sda. This should overwrite the broken grub2 there but we don't care about it.

On the first boot don't forget you will need to do the hit 'e' procedure and add 'nomodeset acpi=off' and later after the system boots to add them permanently in /etc/default/grub as you did once already. This will be brand new installation and will not have them by default.

That should be it.

---

### Post by Jonners59 on 2010-12-30
OK, done

I some how missed or it is no longer there, the "Advanced" settings, and thought I may have to do the install again, but I noticed in the script as it installed it said "Bootloader install sda..."..  so sat it out.

It starts faster, but seems to slow down as the kernel itself loads, so even as the desktop appears.

Below is the new report/log.  It seems to have worked.  What are your thoughts?:guitar:

Would be nice, now to remove the boot loader on sdb




  	 	 	 	pre.western { font-family: "Times New Roman"; }pre.cjk { font-family: "Times New Roman"; }pre.ctl { font-family: "Times New Roman"; }p { margin-bottom: 0.21cm; }               [HTML]   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 319. But according to the info from fdisk, 
                       sdc5 starts at sector 16384.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    22,173,695    22,171,648  83 Linux
/dev/sda2          53,192,704   254,404,607   201,211,904  83 Linux
/dev/sda3         254,405,401   625,141,759   370,736,359   5 Extended
/dev/sda5         254,405,403   449,354,114   194,948,712  83 Linux
/dev/sda6         449,355,776   625,141,759   175,785,984  83 Linux
/dev/sda4          22,173,696    53,192,703    31,019,008  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   206,772,614   206,772,552   7 HPFS/NTFS
/dev/sdb2         206,772,615 1,465,144,064 1,258,371,450   f W95 Ext d (LBA)
/dev/sdb5         206,772,678   416,501,189   209,728,512   7 HPFS/NTFS
/dev/sdb6         416,501,253   626,229,764   209,728,512   7 HPFS/NTFS
/dev/sdb7         626,229,828   835,958,339   209,728,512   7 HPFS/NTFS
/dev/sdb8         835,958,403 1,045,686,914   209,728,512   7 HPFS/NTFS
/dev/sdb9       1,045,686,978 1,255,415,489   209,728,512   7 HPFS/NTFS
/dev/sdb10      1,255,415,553 1,465,144,064   209,728,512   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdc5              16,384   110,318,354   110,301,971   7 HPFS/NTFS
/dev/sdc6         110,321,664 1,953,519,615 1,843,197,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3657705d-3b51-436b-9e65-026a3567771f   ext4       Boot                          
/dev/sda2        5acab084-8137-4b8a-ae8f-e7f0ae4ae354   ext4       Spare                         
/dev/sda3: PTTYPE="dos" 
/dev/sda4        4c1e8820-9746-4319-b08b-9652a8526a91   swap                                     
/dev/sda5        b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb   ext4       Ubuntu 1                      
/dev/sda6        116e4495-c362-4bf0-b802-d0cf28687b6d   ext4       Ubuntu 2                      
/dev/sda: PTTYPE="dos" 
/dev/sdb10       B22A9A262A99E81D                       ntfs       CHIARA                        
/dev/sdb1        9ABAAE68BAAE411D                       ntfs       BARONI                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64BE1AC0BE1A8AA6                       ntfs       RESOURCES                     
/dev/sdb6        0E84A48684A4723F                       ntfs       The Boys                      
/dev/sdb7        BE94ADB294AD6E19                       ntfs       Jonathan                      
/dev/sdb8        5830B68E30B6731C                       ntfs       Shared Files                  
/dev/sdb9        4E30A23730A225C5                       ntfs       Teaching                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        429E50419E503021                       ntfs       Backup Configs                
/dev/sdc6        50720F13720EFD8A                       ntfs       Master Backup                 
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Baroni            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/Resource          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/Monsters          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/Jonathan          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/Shared            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb9        /media/Teaching          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb10       /media/Chiara            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/Configs           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc6        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro nomodeset acpi=off  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro single nomodeset acpi=off
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=c8e0c69b-2926-4abf-b373-79797d4ffda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Baroni ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb5 /media/Resource ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb6 /media/Monsters ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb7 /media/Jonathan ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb8 /media/Shared ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb9 /media/Teaching ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdb10 /media/Chiara ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc5 /media/Configs ntfs defaults,nls=utf8,umask=000,gid=46     0    0
/dev/sdc6 /media/Backup ntfs defaults,nls=utf8,umask=000,gid=46     0    0

=================== sda5: Location of files loaded by Grub: ===================


 130.3GB: boot/grub/core.img
 181.9GB: boot/grub/grub.cfg
 147.7GB: boot/initrd.img-2.6.35-24-generic-pae
 131.5GB: boot/vmlinuz-2.6.35-24-generic-pae
 147.7GB: initrd.img
 131.5GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 116e4495-c362-4bf0-b802-d0cf28687b6d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 116e4495-c362-4bf0-b802-d0cf28687b6d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 116e4495-c362-4bf0-b802-d0cf28687b6d
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=116e4495-c362-4bf0-b802-d0cf28687b6d ro nomodeset splash acpi=off  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 116e4495-c362-4bf0-b802-d0cf28687b6d
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=116e4495-c362-4bf0-b802-d0cf28687b6d ro single nomodeset splash acpi=off
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 116e4495-c362-4bf0-b802-d0cf28687b6d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 116e4495-c362-4bf0-b802-d0cf28687b6d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro nomodeset acpi=off quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb ro single nomodeset acpi=off
	initrd /boot/initrd.img-2.6.35-24-generic-pae
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=116e4495-c362-4bf0-b802-d0cf28687b6d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=4c1e8820-9746-4319-b08b-9652a8526a91 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 275.3GB: boot/grub/core.img
 307.5GB: boot/grub/grub.cfg
 231.1GB: boot/initrd.img-2.6.35-24-generic-pae
 275.3GB: boot/vmlinuz-2.6.35-24-generic-pae
 231.1GB: initrd.img
 275.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 00 00 00 00 00  f0 f2 16 08 80 fa ff ff  |................|
00000010  00 00 00 00 00 00 00 00  05 00 00 00 00 00 00 00  |................|
00000020  30 d2 25 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |0.%.............|
00000030  30 e2 26 03 80 f8 ff ff  70 dd 25 03 80 f8 ff ff  |0.&.....p.%.....|
00000040  70 d2 25 03 80 f8 ff ff  10 d2 25 03 80 f8 ff ff  |p.%.......%.....|
00000050  0f 00 00 00 01 00 00 00  01 00 00 00 00 00 00 00  |................|
00000060  e0 1c 3d 03 80 f8 ff ff  00 00 00 00 00 00 00 00  |..=.............|
00000070  40 d1 25 03 80 f8 ff ff  01 00 00 00 01 00 00 00  |@.%.............|
00000080  01 00 00 00 00 00 00 00  10 d2 25 03 80 f8 ff ff  |..........%.....|
00000090  50 24 15 08 80 fa ff ff  00 00 00 00 00 00 00 00  |P$..............|
000000a0  00 00 00 00 00 00 00 00  00 60 00 00 00 00 00 00  |.........`......|
000000b0  b0 d2 25 03 80 f8 ff ff  b0 d2 25 03 80 f8 ff ff  |..%.......%.....|
000000c0  68 8f 3e 03 80 f8 ff ff  68 6f 40 03 80 f8 ff ff  |h.>.....ho@.....|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  80 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000110  10 d3 25 03 80 f8 ff ff  10 d3 25 03 80 f8 ff ff  |..%.......%.....|
00000120  00 00 00 00 00 00 00 00  00 00 70 00 03 80 08 00  |..........p.....|
00000130  00 00 00 00 00 00 00 00  6c 00 78 00 00 00 00 00  |........l.x.....|
00000140  10 50 92 08 80 f8 ff ff  52 00 00 00 00 00 00 00  |.P......R.......|
00000150  ad 0b 00 00 00 00 00 00  ad 0b 00 00 00 00 00 00  |................|
00000160  28 d4 25 03 80 f8 ff ff  78 6f 40 03 80 f8 ff ff  |(.%.....xo@.....|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  02 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  80 00 00 00 00 00 00 00  0b 07 e8 00 28 00 00 00  |............(...|
000001a0  e0 ee 24 03 80 f8 ff ff  e0 de 25 03 80 f8 ff ff  |..$.......%.....|
000001b0  d0 4b ea 02 80 f8 ff ff  00 00 00 00 00 00 00 fe  |.K..............|
000001c0  ff ff 83 fe ff ff 02 00  00 00 68 ae 9e 0b 00 fe  |..........h.....|
000001d0  ff ff 05 fe ff ff 6a ae  9e 0b 7d 4e 7a 0a 00 00  |......j...}Nz...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
[/HTML]

---

### Post by darkod on 2010-12-31
Looks fine.
There is no need to remove grub2 from sdb, it is still functional and can be used if it becomes necessary. Just don't forget that now the grub2 on sda is "connected" to the ubuntu on sda6, and the grub2 on sdb with the ubuntu on sda5. But either of them can boot both systems.

You will need to do the update-grub command the first time you boot the sda5 because at this moment it doesn't know about the new system on sda6. After that you can boot both systems with either grub2.

And if you keep booting from sda the other grub2 on sdb is just sitting there, no harm done.

---

### Post by Jonners59 on 2011-01-01
I did the update-grub straight away...

Still sounds confusing...  How does it know which to use at bootup?  I only use sda5, 6 was only to fix the bootloader issue, a test bed, and for a backup to use instead of CD should I need it

PS:  Happy New Year, wishing you and yours the very best for 2011

---

