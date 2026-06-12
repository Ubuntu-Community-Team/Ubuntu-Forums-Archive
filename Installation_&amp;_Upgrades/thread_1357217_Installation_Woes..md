---
title: "Installation Woes."
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by hell_storm2004 on 2009-12-17
Hi Everyone,

    I installed Ubuntu 9.10. After many tries. But when i am facing some problems booting. I am getting and error which says:
Error: out of disk 
Press Any key to continue....

Could you please let me know what went wrong in the installation?
I am using a 500GB HDD which already has Windows XP installed in the first partition. I deleted a partition of 100GB from the end and installed Linux there.

---

### Post by presence1960 on 2009-12-17
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by hell_storm2004 on 2010-03-04
Sorry for not being around this thread. My internet connection was causing some headaches! 

Please take a look at by Boot Info:

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=bc6a3adc-9ab3-420d-8760-2fa8bbf12f3d)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

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
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf805c66

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,728,574   209,728,512   7 HPFS/NTFS
/dev/sda2         209,728,575 1,953,520,064 1,743,791,490   f W95 Ext d (LBA)
/dev/sda5         209,728,638   629,169,659   419,441,022   7 HPFS/NTFS
/dev/sda6         629,169,723   894,370,679   265,200,957   7 HPFS/NTFS
/dev/sda7         894,370,743 1,042,232,939   147,862,197  83 Linux
/dev/sda8       1,042,233,003 1,048,610,744     6,377,742  82 Linux swap / Solaris
/dev/sda9       1,048,610,808 1,468,051,829   419,441,022   7 HPFS/NTFS
/dev/sda10      1,468,051,893 1,821,176,594   353,124,702   7 HPFS/NTFS
/dev/sda11      1,821,176,658 1,948,025,834   126,849,177  83 Linux
/dev/sda12      1,948,025,898 1,953,520,064     5,494,167  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d2c0d2c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   964,703,249   964,703,187  83 Linux
/dev/sdb2         964,703,250   976,768,064    12,064,815   5 Extended
/dev/sdb5         964,703,313   976,768,064    12,064,752  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x191f842b

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       07C0252BE502AD10                       ntfs       ENTERTAINMENT 1               
/dev/sda1        160D66D64BC42A69                       ntfs       WINDOWS 1                     
/dev/sda11       a377ac54-1402-4042-84d3-90c1062b9843   ext4                                     
/dev/sda12       46cb2eab-f979-4712-bfe8-d621040b85f0   swap                                     
/dev/sda5        160D68ABE539C529                       ntfs       GAMES 1                       
/dev/sda6        5835A2AF94E714A4                       ntfs       SOFTWARE 1                    
/dev/sda7        2a4e430b-b4ce-47d7-abcd-2aa6d66b3192   ext4                                     
/dev/sda8        3c480dab-1875-40f5-a35f-3fe23fa70989   swap                                     
/dev/sda9        C678AE159FECB7C1                       ntfs       MOVIES 1                      
/dev/sdb1        2f4321b6-d0e9-42ac-9f2d-8f8709929c36   ext4                                     
/dev/sdb5        616ee61f-44eb-492e-84a9-367fd815aa29   swap                                     
/dev/sdc1        152750EF7D44E6E9                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda6        /media/SOFTWARE 1        fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=2a4e430b-b4ce-47d7-abcd-2aa6d66b3192 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=3c480dab-1875-40f5-a35f-3fe23fa70989 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

========================== sda11/boot/grub/grub.cfg: ==========================

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
set root=(hd0,11)
search --no-floppy --fs-uuid --set a377ac54-1402-4042-84d3-90c1062b9843
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
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set a377ac54-1402-4042-84d3-90c1062b9843
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a377ac54-1402-4042-84d3-90c1062b9843 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set a377ac54-1402-4042-84d3-90c1062b9843
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a377ac54-1402-4042-84d3-90c1062b9843 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 308ccb188ccad78c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb4)" {
    insmod ext2
    set root=(hd1,4)
    search --no-floppy --fs-uuid --set 6e595092-7708-42a6-b0e4-d6d33bca0a92
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6e595092-7708-42a6-b0e4-d6d33bca0a92 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb4)" {
    insmod ext2
    set root=(hd1,4)
    search --no-floppy --fs-uuid --set 6e595092-7708-42a6-b0e4-d6d33bca0a92
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6e595092-7708-42a6-b0e4-d6d33bca0a92 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda11 during installation
UUID=a377ac54-1402-4042-84d3-90c1062b9843 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=46cb2eab-f979-4712-bfe8-d621040b85f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda11: Location of files loaded by Grub: ===================


 943.1GB: boot/grub/core.img
 943.1GB: boot/grub/grub.cfg
 933.0GB: boot/initrd.img-2.6.31-14-generic
 932.9GB: boot/vmlinuz-2.6.31-14-generic
 933.0GB: initrd.img
 932.9GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 2f4321b6-d0e9-42ac-9f2d-8f8709929c36
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2f4321b6-d0e9-42ac-9f2d-8f8709929c36
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2f4321b6-d0e9-42ac-9f2d-8f8709929c36 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2f4321b6-d0e9-42ac-9f2d-8f8709929c36
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2f4321b6-d0e9-42ac-9f2d-8f8709929c36 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 160d66d64bc42a69
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda11)" {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set a377ac54-1402-4042-84d3-90c1062b9843
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a377ac54-1402-4042-84d3-90c1062b9843 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda11)" {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set a377ac54-1402-4042-84d3-90c1062b9843
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a377ac54-1402-4042-84d3-90c1062b9843 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=2f4321b6-d0e9-42ac-9f2d-8f8709929c36 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=616ee61f-44eb-492e-84a9-367fd815aa29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.6GB: boot/grub/core.img
  17.6GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz
```

---

### Post by presence1960 on 2010-03-04
You have an install of 9.10 on both sda & sdb. The install on sda has /etc/fstab on it's own partition. The install on sdb looks better. GRUB is installed on both MBRs (sda & sdb) The GRUB on sda points to a non-existant UUID.

I would go into BIOS and set the 500 GB disk (sdb) as first hard disk to boot in the hard disk boot order. The GRUB on sdb's MBR does point to the correct partition (sdb1). Save changes to CMOS and continue booting. Boot into Ubuntu and open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```Hit enter at all windows until you get to the window where you can choose sda and/or sdb. Use the arrow keys to navigate to sda, then hit the spacebar to deselect it if it is already selected. If sda is unselected use the arrow key to navigate to sdb. Hit the spacebar to select sdb. Hit tab to get to OK at the bottom and hit Enter. This will set it up so any grub-pc (GRUB 2) updates go to sdb.

---

### Post by hell_storm2004 on 2010-03-05
My BIOS setting is set to boot from the 500GB HDD. Even after that i get the error. Anyways, I will do as you said and let you know. 
 
Also would like to know that how come the GRUB got into sda on which i never isntalled Ubuntu? :(

---

### Post by hell_storm2004 on 2010-03-05
Well here's what i did:
1. I could not boot into Ubuntu because that's something which I am not able to do. When I select Ubuntu from the OS selection list I get the error:
```
Error: out of disk 
Press Any key to continue....
```
And when I press any key, I get the list of OS options again.
So i booted from my CD and selected, "try ubuntu without any changes" and opened Terminal and did what you said (I selected 'sdb'), I got this error:
```
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

Is what i did correct? Or there am I missing something here?  :cry:

---

### Post by presence1960 on 2010-03-05
I am lost now. You said you never installed ubuntu on sda but there are numerous references to an Ubuntu install being on sda. See this:

```
=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# [COLOR="Red"]/ was on /dev/sda9 during installation
UUID=2a4e430b-b4ce-47d7-abcd-2aa6d66b3192 /               ext4 [/COLOR]   errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=3c480dab-1875-40f5-a35f-3fe23fa70989 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

========================== [COLOR="Red"]sda11/boot/grub/grub.cfg:[/COLOR] ==========================

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
set root=(hd0,11)
search --no-floppy --fs-uuid --set a377ac54-1402-4042-84d3-90c1062b9843
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
[COLOR="Red"]menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,11)[/COLOR]
    search --no-floppy --fs-uuid --set a377ac54-1402-4042-84d3-90c1062b9843
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a377ac54-1402-4042-84d3-90c1062b9843 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
[COLOR="Red"]menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set [/COLOR]a377ac54-1402-4042-84d3-90c1062b9843
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a377ac54-1402-4042-84d3-90c1062b9843 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 308ccb188ccad78c
    drivemap -s (hd0) ${root}
    chainloader +1
}
[COLOR="Blue"]menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb4)" {
    insmod ext2
    set root=(hd1,4)
    search --no-floppy --fs-uuid --set 6e595092-7708-42a6-b0e4-d6d33bca0a92
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6e595092-7708-42a6-b0e4-d6d33bca0a92 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic[/COLOR]
}
[COLOR="Blue"]menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb4)" {
    insmod ext2
    set root=(hd1,4)
    search --no-floppy --fs-uuid --set 6e595092-7708-42a6-b0e4-d6d33bca0a92
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6e595092-7708-42a6-b0e4-d6d33bca0a92 ro single
    initrd /boot/initrd.img-2.6.31-14-generic[/COLOR]
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== [COLOR="Red"]sda11/etc/fstab:[/COLOR] ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#[COLOR="Red"] / was on /dev/sda11 during installation
UUID=a377ac54-1402-4042-84d3-90c1062b9843 /               ext4  [/COLOR]  errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=46cb2eab-f979-4712-bfe8-d621040b85f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

===================[COLOR="Red"] sda11: Location of files loaded by Grub:[/COLOR] ===================


 943.1GB: boot/grub/core.img
 943.1GB: boot/grub/grub.cfg
 933.0GB: boot/initrd.img-2.6.31-14-generic
 932.9GB: boot/vmlinuz-2.6.31-14-generic
 933.0GB: initrd.img
 932.9GB: vmlinuz
```

I think there is a lot about this situation that you are omitting from telling us. To me it looks like you installed ubuntu multiple times, deleted some partitions or maybe even added a hard disk.

---

### Post by hell_storm2004 on 2010-03-08
I have tried installinh Ubuntu many time, but all the time i have used the 500GB HDD, because i wanted windows to stay on the 1TB HDD. Even i think so i maybe not be posting something which may tell you something.

Should i try removing the 1TB HDD and reinstalling Ubuntu? After the installation is done, i would attach the 1TB HDD again. Would that work?

---

