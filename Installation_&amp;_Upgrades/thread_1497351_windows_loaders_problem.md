---
title: "windows loaders problem"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by YaPloNo1 on 2010-05-30
i had a vista/windows 7 dual boot until recently...then i removed windows 7 and installed ubuntu...problem is when grub loads up if i select windows vista it wont boot but if i select windows 7 it will boot into windows vista...is there a way i can sort this?

---

### Post by garvinrick4 on 2010-05-30
> **YaPloNo1 said:**
> i had a vista/windows 7 dual boot until recently...then i removed windows 7 and installed ubuntu...problem is when grub loads up if i select windows vista it wont boot but if i select windows 7 it will boot into windows vista...is there a way i can sort this?
Post results of these two lines of code on this thread.

```
sudo fdisk -l

```
```
sudo blkid
```

---

### Post by YaPloNo1 on 2010-05-30
> **garvinrick4 said:**
> Post results of these two lines of code on this thread.

```
sudo fdisk -l

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd53fcee4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       10327    72457208    7  HPFS/NTFS
/dev/sda3           10327       19458    73346049    5  Extended
/dev/sda5           10327       12163    14748672   82  Linux swap / Solaris
/dev/sda6           12163       15810    29297664   83  Linux
/dev/sda7           15810       19458    29297664   83  Linux
yaplono1@Garry-Samsung-R510-Laptop:~$ 

```
sudo blkid
```

/dev/sda1: LABEL="RECOVERY" UUID="74F4E106F4E0CC04" TYPE="ntfs" 
/dev/sda2: UUID="B8D2E2CCD2E28DC6" TYPE="ntfs" 
/dev/sda5: UUID="037d129e-442d-4867-979d-282114dca0ab" TYPE="swap" 
/dev/sda6: UUID="eaac22f4-bfab-4909-9d83-1b0c577a35e8" TYPE="ext4" 
/dev/sda7: UUID="bb037032-aaf0-4dc1-beca-59302a408e73" TYPE="ext4" 
yaplono1@Garry-Samsung-R510-Laptop:~$


Hope This Is OK!

---

### Post by garvinrick4 on 2010-05-30
Vista keeps its recovery in sda1 and sda2 is OS.
the rest of yours is linux. So it seems like a vista install.

Windows 7 most of time recovery will be in sda4 and mbr in sda1. When dual boot.

I would say you need to;

```
sudo update-grub
```If that did not solve go to this site download this script to Desktop (make sure Desktop)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

then run this.
```

 sudo bash ~/Desktop/boot_info_script*.sh 
```copy and paste to this thread and it will tell everything about your drive.

---

### Post by YaPloNo1 on 2010-06-02
> **garvinrick4 said:**
> Vista keeps its recovery in sda1 and sda2 is OS.
the rest of yours is linux. So it seems like a vista install.

Windows 7 most of time recovery will be in sda4 and mbr in sda1. When dual boot.

I would say you need to;

```
sudo update-grub
```If that did not solve go to this site download this script to Desktop (make sure Desktop)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

then run this.
```

 sudo bash ~/Desktop/boot_info_script*.sh 
```copy and paste to this thread and it will tell everything about your drive.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   165,887,983   144,914,416   7 HPFS/NTFS
/dev/sda3         165,887,998   312,580,095   146,692,098   5 Extended
/dev/sda5         165,888,000   195,385,343    29,497,344  82 Linux swap / Solaris
/dev/sda6         195,387,392   253,982,719    58,595,328  83 Linux
/dev/sda7         253,984,768   312,580,095    58,595,328  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        74F4E106F4E0CC04                       ntfs       RECOVERY                      
/dev/sda2        B8D2E2CCD2E28DC6                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        037d129e-442d-4867-979d-282114dca0ab   swap                                     
/dev/sda6        eaac22f4-bfab-4909-9d83-1b0c577a35e8   ext4                                     
/dev/sda7        bb037032-aaf0-4dc1-beca-59302a408e73   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E4CAC19ECAC16CFC                       ntfs       My Book                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        643295053294DD7C                       ntfs       My Book                       
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sdb1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/My Book_          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
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
search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=eaac22f4-bfab-4909-9d83-1b0c577a35e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=eaac22f4-bfab-4909-9d83-1b0c577a35e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=eaac22f4-bfab-4909-9d83-1b0c577a35e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=eaac22f4-bfab-4909-9d83-1b0c577a35e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set eaac22f4-bfab-4909-9d83-1b0c577a35e8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 74f4e106f4e0cc04
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set b8d2e2ccd2e28dc6
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=eaac22f4-bfab-4909-9d83-1b0c577a35e8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=bb037032-aaf0-4dc1-beca-59302a408e73 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=037d129e-442d-4867-979d-282114dca0ab none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 125.9GB: boot/grub/core.img
 126.1GB: boot/grub/grub.cfg
 126.1GB: boot/initrd.img-2.6.32-21-generic
 126.2GB: boot/initrd.img-2.6.32-22-generic
 126.0GB: boot/vmlinuz-2.6.32-21-generic
 126.1GB: boot/vmlinuz-2.6.32-22-generic
 126.2GB: initrd.img
 126.1GB: initrd.img.old
 126.1GB: vmlinuz
 126.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd

---

### Post by darkod on 2010-06-02
The Vista entry in grub menu is your recovery partition. Not sure why it doesn't kick off (or maybe it does, but you expect to see vista loading not a recovery partition) but don't play with it too much in case the restore process kicks in because it might wipe everything.

The windows 7 entry is probably recognized as win7 because you had both systems and in that case windows combines the boot files. So even though now only vista is there, the boot files might get detected as win7 boot files.

---

### Post by YaPloNo1 on 2010-06-03
> **darkod said:**
> The Vista entry in grub menu is your recovery partition. Not sure why it doesn't kick off (or maybe it does, but you expect to see vista loading not a recovery partition) but don't play with it too much in case the restore process kicks in because it might wipe everything.

The windows 7 entry is probably recognized as win7 because you had both systems and in that case windows combines the boot files. So even though now only vista is there, the boot files might get detected as win7 boot files.

ive a samsung r510 as you can tell from my comp name so it came with a 10gb vista recovery partition, good idea i think, and my remaining 150 gb split it c: and d: drives...so vista was installed on c:, then 7 installed on d: but after removing 7 i then deleted the windows 7 option from the boot menu and then i deleted the partition and expanded c: drive to 150gb by using the unallocated space...is it possibly during this process that the boot files have been combined?...however i get the overall message, this is all working fine and i should leave it and be grateful its working...so thanks both of you for your help, ya!

---

