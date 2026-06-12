---
title: "Lucid alpha 3: GRUB complains &quot;file not found&quot;"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Piotr.Sniady on 2010-03-07
Ubuntu Lucid Alpha 3.
After seemingly succesful install, the machine fails to boot with the following error message:
```

GRUB loading.
error: file not found
grub_rescue> 
```
The output of the command "set" is:
```

prefix=(hd0,3)/grub
root=hd0,3 
```
The machine uses a LVM setup with a separate /home partition in LVM and wth /boot on a separate partition.
This machine has used succesfully this setup for several years, with an upgrade to the next Ubuntu/Kubuntu version after every new release.
The location of the GRUB was selected to be the default one.
This is a fresh install ("alternate") from a USB stick.

The output of the boot script (obtained via LiveCD session) is attached.

---

### Post by VMC on 2010-03-07
grub.cfg is not pointing to your /boot partition, sdb1:

```
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 23417df1-4c76-4339-9b00-9a8e98fc9c8f
	linux	/vmlinuz-2.6.32-14-generic root=/dev/mapper/representation-root ro   quiet splash
	initrd	/initrd.img-2.6.32-14-generic
}
```

Also your linux line says you kernel is at the root of sda3, unless that's a symlink, which I doubt. See what's in the root dir of sda3. 

Also check and see if in fact your /boot partition has the needed kernels.

---

### Post by Piotr.Sniady on 2010-03-07
> **VMC said:**
> grub.cfg is not pointing to your /boot partition, sdb1:


Actually, sdb1 seems to be the pendrive with the LiveCD from which the boot script was run. So this seems to be irrelevant.

---

### Post by Piotr.Sniady on 2010-03-08
> **VMC said:**
> 
Also your linux line says you kernel is at the root of sda3, unless that's a symlink, which I doubt. See what's in the root dir of sda3. 

```
=================== sda3: Location of files loaded by Grub: ===================
  20.1GB: grub/grub.cfg
  20.0GB: initrd.img-2.6.32-14-generic
  20.0GB: vmlinuz-2.6.32-14-generic
```
Well, it seems that the kernel is really there. 

The question is, which file GRUB is complaining about.  Since I do not see the GRUB menu, in my opinion it is not the kernel that is missing, but the file grub.cfg. I do not understand from the log how is it possible that GRUB is not able to get it.

---

### Post by kansasnoob on 2010-03-08
What has me puzzled is the lack of an fstab?????

---

### Post by kansasnoob on 2010-03-08
As far as your Linux partitions:

> sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

I'm quite puzzled because I've never used LVM, but also no SWAP?

And here's my output of my Lucid w/grub2:

> sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [B][COLOR="Red"]Ubuntu lucid (development 
                       branch)[/COLOR][/B]
    Boot files/dirs:   [B][COLOR="Red"]/boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img[/COLOR][/B]


All around puzzling and I thought fstab might give me some answers but there is no fstab. And it doesn't even list the OS.

---

### Post by kansasnoob on 2010-03-08
Please post the output of:

```
sudo parted /dev/sda print
```

Just because it's more "human" readable to me than fdisk :)

---

### Post by Piotr.Sniady on 2010-03-08
Update: I installed LVM2 in the LiveCD so now I have a better access to the LVM. Now the output of the boot info script should contain more information.

Comment: Logical Volume "root-koala" was not used in this install.

```
                                                 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

representation-swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

representation-root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

representation-home: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

representation-root-koala: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017   7 HPFS/NTFS
/dev/sda2         301,659,120   312,575,759    10,916,640  12 Compaq diagnostics
/dev/sda3          39,070,080    39,648,419       578,340  83 Linux
/dev/sda4          39,648,420   301,652,504   262,004,085   5 Extended
/dev/sda5          39,648,483   301,652,504   262,004,022  8e Linux LVM


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4127 MB, 4127195136 bytes
127 heads, 62 sectors/track, 1023 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     8,055,101     8,055,040   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       cf5f2d03-1db1-45da-9e7f-82a17e5b7b9a   ext3                                     
/dev/mapper/representation-home 1d3b8770-9a65-4691-90c1-185fb65509d8   ext3                                     
/dev/mapper/representation-root c6e9b334-d230-45f9-8e6e-ab9e9d7d906d   ext4                                     
/dev/mapper/representation-root--koala 2c848dc5-dddc-412f-9aa6-d78a8a399a75   ext4                                     
/dev/mapper/representation-swap bb7ceaeb-0a9c-4554-b230-cddf20cd8b7a   swap                                     
/dev/sda1        349C27289C26E458                       ntfs       Preload                       
/dev/sda2        F032-4C88                              vfat       SERVICEV001                   
/dev/sda3        23417df1-4c76-4339-9b00-9a8e98fc9c8f   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        aL5Ffx-0zTO-CnYk-TiHI-Otpw-wSvs-ioGSo8 LVM2_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A7CE-0B19                              vfat                                     
/dev/sdb: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
representation-home
representation-root
representation-root--koala
representation-swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================ sda2/boot.ini: ================================

[boot loader]
timeout=0
default=C:\
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\ = "PC-DOS"

============================= sda3/grub/grub.cfg: =============================

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
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 23417df1-4c76-4339-9b00-9a8e98fc9c8f
	linux	/vmlinuz-2.6.32-14-generic root=/dev/mapper/representation-root ro   quiet splash
	initrd	/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 23417df1-4c76-4339-9b00-9a8e98fc9c8f
	echo	Loading Linux 2.6.32-14-generic ...
	linux	/vmlinuz-2.6.32-14-generic root=/dev/mapper/representation-root ro single 
	echo	Loading initial ramdisk ...
	initrd	/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 23417df1-4c76-4339-9b00-9a8e98fc9c8f
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 23417df1-4c76-4339-9b00-9a8e98fc9c8f
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


  20.1GB: grub/grub.cfg
  20.0GB: initrd.img-2.6.32-14-generic
  20.0GB: vmlinuz-2.6.32-14-generic

======================== representation-root/etc/fstab: ========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/representation-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=23417df1-4c76-4339-9b00-9a8e98fc9c8f /boot           ext4    defaults        0       2
/dev/mapper/representation-home /home           ext3    defaults        0       2
/dev/mapper/representation-swap none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on representation-root-koala



=============================== StdErr Messages: ===============================

  skip_dev_dir: Couldn't split up device name representation-root-koala
  Volume group "representation-root-koala" not found
  Skipping volume group representation-root-koala
  skip_dev_dir: Couldn't split up device name representation-root-koala
  Volume group "representation-root-koala" not found
  Skipping volume group representation-root-koala
  skip_dev_dir: Couldn't split up device name representation-root-koala
  Volume group "representation-root-koala" not found
  Skipping volume group representation-root-koala
hexdump: /dev/mapper/representation-root-koala: No such file or directory
hexdump: /dev/mapper/representation-root-koala: No such file or directory

```

---

### Post by Piotr.Sniady on 2010-03-08
```
 sudo parted /dev/sda print

Model: ATA WDC WD1600BEVS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  20.0GB  20.0GB  primary   ntfs         boot
 3      20.0GB  20.3GB  296MB   primary   ext4
 4      20.3GB  154GB   134GB   extended
 5      20.3GB  154GB   134GB   logical                lvm
 2      154GB   160GB   5589MB  primary   fat32
```

---

### Post by Piotr.Sniady on 2010-03-08
> **kansasnoob said:**
>  I'm quite puzzled because I've never used LVM, but also no SWAP?
All around puzzling and I thought fstab might give me some answers but there is no fstab. And it doesn't even list the OS.
Swap is one of the Logical Volumes inside LVM; on the new printout it should be visible. The same holds true for fstab; since the root filesystem was on a Logical Volume it was not visible on the first printout.

---

### Post by Piotr.Sniady on 2010-03-08
> **kansasnoob said:**
> Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /grub/core.img 
/boot/grub/core.img
It is a good point, it seems that core.img is missing. So maybe **this** is the missing file and not grub.cfg. This would explain a lot. I will continue the investigation.

---

### Post by Piotr.Sniady on 2010-03-09
[http://grub.enbug.org/Grub2LiveCdInstallGuide]("http://grub.enbug.org/Grub2LiveCdInstallGuide") saved my day. Nevertheless it seems there is some bug in Lucid.

---

