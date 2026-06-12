---
title: "Grub error: Unknown filesystem and Grub error: No such disc"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by sphlanx on 2010-11-23
Hello everyone, 

I have a dual boot system with ubuntu 9.10 x64 and Windows 7. Everything has been working fine for a a long time but yesterday I tried to delete an unused partition through the Disk Utility in ubuntu (System->Adminstration->Disk Utility) and everything was messed up. I used to get the "Grub error: Unknown filesystem". I managed to create an ubuntu bootable usb and followed some tutorials for fixing grub but all i managed to do is to get another error: "Grub error: No such disc". After some experimentation i got 
"Grub stage 1.5" which gave me a grub> command prompt.

Any help will be appreciated since I am totally lost and I have no idea about how hard drives and boot record work.

I will post my boot info script results here. If you need any more information please ask me to provide it. Thanks in advance!

/dev/sda is the drive containing Windows and Ubuntu.

```
[                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 981530204 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 981530204 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /Boot/BCD /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   980,179,833   979,972,986   7 HPFS/NTFS
/dev/sda3         980,189,910 1,250,242,559   270,052,650   f W95 Ext d (LBA)
/dev/sda5       1,242,052,608 1,250,242,559     8,189,952   7 HPFS/NTFS
/dev/sda6         980,190,036 1,081,993,814   101,803,779  83 Linux
/dev/sda7       1,081,993,878 1,086,427,754     4,433,877  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4007 MB, 4007624704 bytes
32 heads, 63 sectors/track, 3882 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,826,111     7,826,049   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        A6D68118D680EA3F                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        023C9DF93C9DE845                       ntfs       &#925;&#941;&#959;&#962; &#964;&#972;&#956;&#959;&#962;           
/dev/sda6        35b37184-7e13-4ef5-930f-9dc15d1a26ce   ext4                                     
/dev/sda7        03a7a9ee-1ba0-487d-83f5-db05470271a8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3E5C558C5C553FB7                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2C6F-4CD5                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/A6D68118D680EA3F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/35b37184-7e13-4ef5-930f-9dc15d1a26ce ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 35b37184-7e13-4ef5-930f-9dc15d1a26ce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 92b07db9b07da47f
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3e5c558c5c553fb7
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=35b37184-7e13-4ef5-930f-9dc15d1a26ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=03a7a9ee-1ba0-487d-83f5-db05470271a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 505.6GB: boot/grub/core.img
 505.8GB: boot/grub/grub.cfg
 502.5GB: boot/grub/stage2
 502.5GB: boot/initrd.img-2.6.31-14-generic
 503.5GB: boot/initrd.img-2.6.31-16-generic
 507.1GB: boot/initrd.img-2.6.31-17-generic
 544.1GB: boot/initrd.img-2.6.31-20-generic
 544.1GB: boot/initrd.img-2.6.31-22-generic
 502.4GB: boot/vmlinuz-2.6.31-14-generic
 503.2GB: boot/vmlinuz-2.6.31-16-generic
 503.0GB: boot/vmlinuz-2.6.31-17-generic
 538.4GB: boot/vmlinuz-2.6.31-20-generic
 538.4GB: boot/vmlinuz-2.6.31-22-generic
 544.1GB: initrd.img
 544.1GB: initrd.img.old
 538.4GB: vmlinuz
 538.4GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.1 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.1="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by drs305 on 2010-11-23
You have a mixture of Grub legacy and Grub2. It appears you have intact Grub2 files in sda6, but with the mixture you have it might be best just to start again.

From the LiveCD, use the chroot procedure found in the following link to remove all traces of grub and reinstall Grub2. The device you want to mount in the instructions will be **sda6** and install grub to the **sda** drive. If you copy the commands it's a very simple process and only takes a few minutes. Just be sure you have an Internet connection before purging your bootloader.

You don't need the background, so you can go directly to Step 1 if you wish.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by sphlanx on 2010-11-23
Thanks for the fast answer. I have read though that the chroot  procedure wont work because I have 64bit version in the partition and I am running a 32bit live CD.

---

### Post by garvinrick4 on 2010-11-23
###Given that you cannot boot into sdb with Windows Professional installed:
#Get sdb with Windows on it to boot with lilo then download the correct architecture of Ubuntu and Burn to disc and use the previous instructions:

#Use live cd and run this code to get lilo into sdb windows professional:
```
sudo apt-get install lilo
```                  ```
sudo lilo -M /dev/sdb mbr 
```#Use Bios to get sdb to boot before sda and then use Windows to make a new Ubuntu CD.
of right architecture:
#Now use drs305 instructions:

---

### Post by drs305 on 2010-11-23
I don't have access to my laptop at the moment, but I believe if your Grub2 files are intact, this may boot your system. 

From the USB Grub menu, try going to the command prompt by pressing "c".
You can confirm it's sda6 (it could be sdb6) with:
```
ls (hd0,6)/home/
```

```

configfile (hd0,6)/boot/grub/grub.cfg

```
When you press ENTER, it should show your normal Ubuntu menu.

It can't be much simpler (if it works). If it does, it should present your Ubuntu sda6 Grub menu. Select the top entry and see if it boots. If so, then I'd still purge and reinstall grub - you just wouldn't have to use the 'chroot' procedure.

---

### Post by sphlanx on 2010-11-23
Ok, I have managed to create a USB startup disk with ubuntu 64bit version. I am going to try drs305 advice and then the chroot procedure. I will post my results here. Thanks again for the fast replies.

---

