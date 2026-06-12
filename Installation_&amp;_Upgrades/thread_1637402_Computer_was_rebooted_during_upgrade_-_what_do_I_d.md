---
title: "Computer was rebooted during upgrade - what do I do"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by Trevor Burton on 2010-12-04
Hi,
 
My daughter rebooted my computer while it was upgrading from Karmic to Lucid.
 
Now, of course, it won't reboot 
 
"[    0.683646]Kernel panic - not syncing: - VFS: Unable to mount root fs on unknown-block(0,0)"
 
I do have a very current backup of /home
 
I don't have a backup of any configuration files (/etc/conf and so on?)
 
I think that I will have to overwrite the whole installation and then restore my /home directory, which will mean tweaking all my software installations again?
 
Is this my best plan of action?
 
Thanks in advance

---

### Post by Trevor Burton on 2010-12-04
hmmmm

---

### Post by smo0th on 2010-12-04
that's a nasty one, you'd be better off with a fresh install and disconnecting the reset button like I did =)

---

### Post by Trevor Burton on 2010-12-04
> **smo0th said:**
> that's a nasty one, you'd be better off with a fresh install and disconnecting the reset button like I did =)

Yes, I was gutted, especially as she just wanted to listen to some music using Windows!  As she said "But I only switched users, and then it wouldn't work so I shutdown and restarted with Windows!"

Here are the results of my bootinfo script.  Thought I'd hold off in case a wizard looked in.
I was running dual boot with (I think) - this is what I think the partitions were, looking through the results.txt file ...

Windows XP on /sda2
Karmic / was on /sda5 (now it shows lucid - what I was upgrading to)
Karmic /home was on /sda6
Karmic swap was on /sda7
/sdb1 is my eSATA attached backup drive

Would love to get away with a few command line spells but obviously if I have to I'll install fresh.

Trevor

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 397263670 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  1b Hidden W95 FAT32
/dev/sda2    *     16,370,235   387,471,734   371,101,500   7 HPFS/NTFS
/dev/sda3         387,471,735   625,137,344   237,665,610   5 Extended
/dev/sda5         387,471,798   428,485,679    41,013,882  83 Linux
/dev/sda6         428,485,743   619,273,619   190,787,877  83 Linux
/dev/sda7         619,273,683   625,137,344     5,863,662  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        44D7-70B8                              vfat       BACKUP                        
/dev/sda2        4A38F4AD38F498E1                       ntfs       HDD                           
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ee0e6cff-7dc9-4379-88ce-7965f273fda2   ext4                                     
/dev/sda6        7387ae1c-ee8b-42e7-ba4a-5d06050037f7   ext4                                     
/dev/sda7        e9ac70ad-427d-4eeb-b25b-dd0af2f8eec7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6EDEDBBFDEDB7E31                       ntfs       Elrond                        
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/ee0e6cff-7dc9-4379-88ce-7965f273fda2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /media/7387ae1c-ee8b-42e7-ba4a-5d06050037f7 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons 
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..." 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="9"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
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
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 ro   quiet splash
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 ro single 
}
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee0e6cff-7dc9-4379-88ce-7965f273fda2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 44d7-70b8
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 4a38f4ad38f498e1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# / was on /dev/sda5 during installation
UUID=ee0e6cff-7dc9-4379-88ce-7965f273fda2 /               ext4    errors=remount-ro 0       1
#
# /home was on /dev/sda6 during installation
UUID=7387ae1c-ee8b-42e7-ba4a-5d06050037f7 /home           ext4    defaults        0       2
#
# swap was on /dev/sda7 during installation
UUID=e9ac70ad-427d-4eeb-b25b-dd0af2f8eec7 none            swap    sw              0       0
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
# Elrond is the drive connected by eSATA
/dev/sdb1  /media/Elrond      ntfs    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 201.8GB: boot/grub/core.img
 199.3GB: boot/grub/grub.cfg
 200.0GB: boot/initrd.img-2.6.31-14-generic
 200.6GB: boot/initrd.img-2.6.31-21-generic
 203.1GB: boot/initrd.img-2.6.31-22-generic
 199.9GB: boot/vmlinuz-2.6.31-14-generic
 200.4GB: boot/vmlinuz-2.6.31-21-generic
 207.6GB: boot/vmlinuz-2.6.31-22-generic
 203.1GB: boot/vmlinuz-2.6.32-26-generic
 203.1GB: initrd.img
 200.6GB: initrd.img.old
 207.6GB: vmlinuz
 200.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```Trevor

---

### Post by Habeouscorpus on 2010-12-04
I agree with smo0th. The system's unstable now because of that. If it were me, I'd back up, run chkdsk on a Windows Machine (because it was interrupted during a data write), and do a fresh install.

---

### Post by ToFue on 2010-12-04
if /home is a seperate partition, it should be a less painful experience - 
get a list of installed packages with:
```

dpkg -l > path/to/BackupU/destintation/filename.txt

```

Do a fresh install, using the same partition for /home, keeping the same filesystem type, WITHOUT formating that partition.. the other linux partitions should be fair game for reconfig & you'll want to format those. The install should also recognize the windows bootloader and auto-configure on install.

if you don't have a seperate /home partition, then use the good ole' copy to a backup disk using the live cd & 
```

sudo nautilus

```
to do the copy w/out permission issues..

or you can 
```

$ sudo cp -fR /home/* /destination/backup/folder

```

then copy back after new install & relabel permissions as appropriate & reinstall the packages you need/use by refering to the list you made earlier

Note: if you copy using root permissions, the new files will be owned by root, so you'll have to 
```

sudo chown ${USER}: /home/${USER}*

```
to restore ownership of the copied files.. adjust the target path accordingly for specific files, and if more than one user, adjust ${USER} to whatever other user you're changing for. ${USER} is environment variable for the current user logged in to the terminal.

---

