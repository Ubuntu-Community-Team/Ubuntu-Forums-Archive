---
title: "Re-installing XP with a two disk dual boot"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Dadof4 on 2010-02-17
Hello, I have been running Ubuntu 9.10 and Win XP Professional as a dual boot system, with each OS on its own HDD, smoothly and seamlessly since the release of 9.10. Yesterday one of my kids got a video file from a friend and it had a virus along with it. Long story short, in the process of trying to repair it Windows shuddered it last agonizing breath. 

Now I have to re-install Windows because some of the programs the schools make them use require Windows. How do I go about doing this without damaging my Ubuntu installation? Will re-installing on a second drive affect GRUB? What kind of problems am I looking at here?

Thanks in advance.

---

### Post by gordintoronto on 2010-02-17
After you reinstall Windows, you will have to reinstall Grub.  Here's instructions:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by oldfred on 2010-02-17
It depends on how your were booting. My preferred way with two drives is to have windows and the windows boot loader in one drive and grub/Ubuntu on the other drive. But some installs see the windows drive as the boot drive and put grub on that drive.

You should make sure you have grub installed to the Ubuntu drive. Then set the windows drive first in the BIOS so windows only installs on that drive, then switch back and run the sudo update-grub so it can find the new windows install on the (now) second drive. The sda, sdb settings do not change when you change boot order. The drive order seems to be the order plugged into the ports, and normally does not need to be changed.

If you want to see your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

results.txt will tell you where grub is installed and all sorts of info on the boot process.

---

### Post by Ceiber Boy on 2010-02-17
all good advice, just a thought will the software your school uses run with WINE?

---

### Post by Dadof4 on 2010-02-18
I'm using two individual drives. I ran the boot info and have the results but I don't know what to post, what to highlight, etc...I'm real new to Ubuntu and to forums in general.



  ```
=> Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d7a1d7a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d199d19

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   224,829,674   224,829,612  83 Linux
/dev/sdb2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sdb5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4638E82A38E81B27                       ntfs                                     
/dev/sdb1        8daee8c9-9cc4-42ab-a2ff-3e4d92184278   ext4                                     
/dev/sdb5        0456963e-06fa-422d-8234-e4c1f751bc66   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/4638E82A38E81B27  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
 
[spybotsd] 
timeout.old=30 
 

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
search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
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
    search --no-floppy --fs-uuid --set 4638e82a38e81b27
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0456963e-06fa-422d-8234-e4c1f751bc66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   9.4GB: boot/grub/core.img
   1.3GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
    .7GB: boot/initrd.img-2.6.31-15-generic
   1.0GB: boot/initrd.img-2.6.31-16-generic
   1.2GB: boot/initrd.img-2.6.31-17-generic
   1.3GB: boot/initrd.img-2.6.31-18-generic
   1.3GB: boot/initrd.img-2.6.31-19-generic
   1.3GB: boot/initrd.img-2.6.31-20-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-15-generic
    .8GB: boot/vmlinuz-2.6.31-16-generic
   1.0GB: boot/vmlinuz-2.6.31-17-generic
   1.2GB: boot/vmlinuz-2.6.31-18-generic
   1.3GB: boot/vmlinuz-2.6.31-19-generic
   1.3GB: boot/vmlinuz-2.6.31-20-generic
   1.3GB: initrd.img
   1.3GB: initrd.img.old
   1.3GB: vmlinuz
   1.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by oldfred on 2010-02-19
You do have the MBR's reversed with the operating systems. I would boot into Ubuntu and reinstall grub2 to sdb. Set sdb as first to boot in BIOS and make sure it works. Then reset in BIOS the windows drive as first and reinstall windows. Switch BIOS back and boot  Ubuntu and run sudo update-grub to find the new windows install.

reinstall from working system - first find Ununtu drive: 
sudo fdisk -l 
if it's "/dev/sdb"  then just run: 
sudo grub-install /dev/sdb
If that returns any errors run: 
sudo grub-install --recheck /dev/sdb 
Then: 
sudo update-grub

---

### Post by Dadof4 on 2010-02-19
Ok, I tried that and this is where I am at. I can't boot in to Ubuntu. I have the drive listed first in the BIOS and the computer boots right to Windows. I tried disconnecting the drive Windows is installed on and I get an error stating that there is not a bootable drive. It worked well before I re-installed Windows. I ran the Boot Info Script and this is what I get. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d7a1d7a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d199d19

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   224,829,674   224,829,612  83 Linux
/dev/sdb2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sdb5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5ADC9E46DC9E1C77                       ntfs                                     
/dev/sdb1        8daee8c9-9cc4-42ab-a2ff-3e4d92184278   ext4                                     
/dev/sdb5        0456963e-06fa-422d-8234-e4c1f751bc66   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

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
search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8daee8c9-9cc4-42ab-a2ff-3e4d92184278
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 ro single 
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
    search --no-floppy --fs-uuid --set 4638e82a38e81b27
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=8daee8c9-9cc4-42ab-a2ff-3e4d92184278 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0456963e-06fa-422d-8234-e4c1f751bc66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.3GB: boot/grub/core.img
   1.3GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
    .7GB: boot/initrd.img-2.6.31-15-generic
   1.0GB: boot/initrd.img-2.6.31-16-generic
   1.2GB: boot/initrd.img-2.6.31-17-generic
   1.3GB: boot/initrd.img-2.6.31-18-generic
   1.3GB: boot/initrd.img-2.6.31-19-generic
   1.3GB: boot/initrd.img-2.6.31-20-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-15-generic
    .8GB: boot/vmlinuz-2.6.31-16-generic
   1.0GB: boot/vmlinuz-2.6.31-17-generic
   1.2GB: boot/vmlinuz-2.6.31-18-generic
   1.3GB: boot/vmlinuz-2.6.31-19-generic
   1.3GB: boot/vmlinuz-2.6.31-20-generic
   1.3GB: initrd.img
   1.3GB: initrd.img.old
   1.3GB: vmlinuz
   1.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by meierfra. on 2010-02-20
Some bios refuse to boot a hard drive without a boot flag. So type

```
sudo sfdisk -A1 /dev/sdb
```

to put the boot flag onto the Ubuntu partition.

---

### Post by Dadof4 on 2010-02-20
HA! It worked! Thank you everyone for your help!

---

### Post by meierfra. on 2010-02-20
> HA! It worked! 
Great. Have fun with Windows and Ubuntu.

---

