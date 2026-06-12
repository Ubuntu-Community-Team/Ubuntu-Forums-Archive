---
title: "Error: No such disk"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by vegnarok on 2010-03-25
This came from old SOLVED thread and I was told to make new thread: [http://ubuntuforums.org/showthread.php?t=1437720](http://ubuntuforums.org/showthread.php?t=1437720)

---------------------------------

Okay, I'm mad that I'm getting this error and I researched and found  this thread. I wish you guys add more direction when u found a way to  fix. :sad:

Okay, I need step by step directions cuz I'm such a n00b to Linux. I  finished installed on my Vista cpu and apparently this only have one  hard drive. I dont have trouble with it. Now I want to install on this  XP cpu and it frakked up with this "Error: no such disk".

I wanted to install side-by-side with Windows. For first time, I noticed  it came up with second hard drive (500gb) but I didnt think it would  cause such a problem. I proceed to install it. That's how I got this  error. I couldn't boot into Window XP and I have files there I want to  keep. I dont want to format it. 

I made second attempt at re-installation and I noticed it's not on first  hard drive (80gb) instead of (500 gb). Ugh....well, I don't care which  hard drive I want to put ubuntu on it. Can u give me specific direction  on how to fix this? BTW, I am posting results.txt here to help me  further better:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=a4e75beb-58f2-4bbf-bbb5-c90f50860ba4)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: __________________________________________________   _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sdb6: __________________________________________________   _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sdb8: __________________________________________________   _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  __________________________________________________  ___

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b0b7b0b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


Drive: sdb ___________________  __________________________________________________  ___

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x420f7616

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   388,323,179   388,323,117   7 HPFS/NTFS
/dev/sdb2         388,323,180   976,768,064   588,444,885   5 Extended
/dev/sdb5         584,476,893   775,280,834   190,803,942  83 Linux
/dev/sdb6         960,783,453   976,768,064    15,984,612  82 Linux swap  / Solaris
/dev/sdb7         388,323,306   576,412,199   188,088,894  83 Linux
/dev/sdb8         576,412,263   584,476,829     8,064,567  82 Linux swap  / Solaris


blkid -c /dev/null: __________________________________________________   __________

Device           UUID                                   TYPE       LABEL                          

/dev/loop0                                              squashfs                                  
/dev/sda1        96FC163CFC1616D9                       ntfs                                      
/dev/sdb1        A6D03115D030ED65                       ntfs        Vegnarok500                   
/dev/sdb5        f946892f-0ffa-45fa-b52f-e1f976048c76   ext4                                      
/dev/sdb6        5f339524-bc51-4ac1-9c39-18fbd172b58b   swap                                      
/dev/sdb7        a4e75beb-58f2-4bbf-bbb5-c90f50860ba4   ext4                                      
/dev/sdb8        0a29a9e8-54cb-4a2e-9451-67f1bccc7819   swap                                      

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini:  ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW  S 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro  soft Windows XP Home  Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
set root=(hd1,5)
search --no-floppy --fs-uuid --set f946892f-0ffa-45fa-b52f-e1f976048c76
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
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
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set  f946892f-0ffa-45fa-b52f-e1f976048c76
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=f946892f-0ffa-45fa-b52f-e1f976048c76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set  f946892f-0ffa-45fa-b52f-e1f976048c76
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=f946892f-0ffa-45fa-b52f-e1f976048c76 ro single 
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
    search --no-floppy --fs-uuid --set 96fc163cfc1616d9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=f946892f-0ffa-45fa-b52f-e1f976048c76 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5f339524-bc51-4ac1-9c39-18fbd172b58b none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0

=================== sdb5: Location of files loaded by Grub:  ===================


 299.8GB: boot/grub/core.img
 299.8GB: boot/grub/grub.cfg
 299.8GB: boot/initrd.img-2.6.31-14-generic
 299.8GB: boot/vmlinuz-2.6.31-14-generic
 299.8GB: initrd.img
 299.8GB: vmlinuz

=========================== sdb7/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
set root=(hd1,7)
search --no-floppy --fs-uuid --set a4e75beb-58f2-4bbf-bbb5-c90f50860ba4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
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
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set  a4e75beb-58f2-4bbf-bbb5-c90f50860ba4
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=a4e75beb-58f2-4bbf-bbb5-c90f50860ba4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set  a4e75beb-58f2-4bbf-bbb5-c90f50860ba4
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=a4e75beb-58f2-4bbf-bbb5-c90f50860ba4 ro single 
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
    search --no-floppy --fs-uuid --set 96fc163cfc1616d9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set  f946892f-0ffa-45fa-b52f-e1f976048c76
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=f946892f-0ffa-45fa-b52f-e1f976048c76 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on  /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set  f946892f-0ffa-45fa-b52f-e1f976048c76
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=f946892f-0ffa-45fa-b52f-e1f976048c76 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=a4e75beb-58f2-4bbf-bbb5-c90f50860ba4 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=0a29a9e8-54cb-4a2e-9451-67f1bccc7819 none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0

=================== sdb7: Location of files loaded by Grub:  ===================


 199.0GB: boot/grub/core.img
 199.0GB: boot/grub/grub.cfg
 199.0GB: boot/initrd.img-2.6.31-14-generic
 199.0GB: boot/vmlinuz-2.6.31-14-generic
 199.0GB: initrd.img
 199.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard  drive==============

sdc                      
```And finally, I got reply from oldfred:

> vegnarok
I do not see anything obviously wrong with your results.txt. It shows  that you did install twice and eventually you should convert the first  install back to a data or /home partition.

Is it that you can boot Ubuntu but not windows? 

I prefer to have the boot loader on the same drive as the operating  system so each drive could if necessary boot on its own. I would from  Ubuntu reinstall grub to sdb and install a windows boot loader to sda  and confirm that windows boots ok with sda selected in BIOS, then change  BIOS to boot sdb.

To put a windows boot loader in sda.

Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

To reinstall grub2 to sdb from your working install.
reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sdb"  then just run: 
sudo grub-install /dev/sdb 
If that returns any errors run: 
sudo grub-install --recheck /dev/sdb
Then: 
sudo update-grub

Then reboot with sda (80GB) drive still first in BIOS. Windows should  boot or give windows errors that you have to repair from windows.

Once windows boots ok, go into BIOS and set sdb (500gb) as primary  master or boot drive. Ubuntu should boot.

I always make sure I have working liveCD and/or bootable USB just in  case I have to do repairs from that because something did not work  correctly.

Edit: Windows uses a boot flag and linux does not, but some BIOS need to  see a boot flag to work (assumes windows). Add a boot flag to a  partition on sdb using gparted right click on partition and manage  flags.
Or
 set boot flag on for sdb7 (off on others)
sudo sfdisk -B7 /dev/sdaMy attempt to fix from:

> Restore basic windows boot loader
 sudo apt-get install lilo
 sudo lilo -M /dev/sda mbrIt did work, forcing it to boot into window xp. Yay! But no ubuntu boot choice in the menu. :-( But, I'm gonna try second suggestion. I need to know how to remove second install of ubuntu? Can I get directions on remove all installations of ubuntu, just in case I don't want on it? I did research and I found many methods and I'd rather hear it from you linux experts cuz I hate to mess up my computer even worse.

I decided I don't want to install ubuntu on my second hard drive (500gb) and want to put it on 80 gb main hard drive to avoid further complication and I want to have choice to choose between xp and ubuntu, exactly like i have on my vista cpu which ubuntu worked side-by-side well with windows without any problems.

---

### Post by vegnarok on 2010-03-25
Attempting second suggestion:

> To reinstall grub2 to sdb from your working install.
reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sdb"  then just run: 
sudo grub-install /dev/sdb 
If that returns any errors run: 
sudo grub-install --recheck /dev/sdb
Then: 
sudo update-grubI got:

/dev/sdb1 HPFS/NTFS
/dev/sdb2 Extended
/dev/sdb5 Linux
/dev/sdb6 Linux swap / solaris
/dev/sdb7 Linux
/dev/sdb8 Linux swap / solaris 

I'm kinda still lost on this one except I understand the concept of re-installing. I think it might be better to uninstall all ubuntu and then attempt to do re-installation of ubuntu as a fresh installation? Like I said, i need proper direction on how to uninstall all ubuntu since I found many solutions to this and I'm afraid to damage my computer further? How do I make sure  to install ubuntu on my main drive (80gb)?

Also, I havent really use BIOS very often so i'm little clueless on how to reconfigure the BIOS?

---

### Post by oldfred on 2010-03-25
You can go back and reinstall Ubuntu to your 80GB drive but it will put grub in the MBR and you boot windows thru grub which everyone with one drive does. To me the advantage of two drives is two MBRs and you can install an operating system on each. Your choice.

You need to use gparted from the liveCD to delete partitions. You do need to know which partitions have data you want since it is just about impossible to recover once deleted.

Since you did not reinstall grub to sdb before installing the windows boot loader to sda you will have to use a liveCD to install grub to sdb if you still want to boot the install in sdb7. It looks like sdb5 & sdb6 was your earlier install.

To install grub2 from liveCD:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

reinstall from live cd adjusted for your sdb7 install to sdb:
sudo mount /dev/sdb7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

In BIOS you should have a setting for primary master which is the drive the computer uses to boot. You can go in and review your version of the BIOS and exit without changes if concerned. Usually del key or f2 right at the very startup of the computer gets you into BIOS.

---

