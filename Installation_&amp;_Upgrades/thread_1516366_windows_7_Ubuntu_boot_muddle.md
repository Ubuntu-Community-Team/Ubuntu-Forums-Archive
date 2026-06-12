---
title: "windows 7/ Ubuntu boot muddle"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by elusive_elf on 2010-06-23
Hi all,

I have a bit of a problem. I have just installed Ubuntu on... a slightly complex drive model. Here's the sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac10f44c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60050   482348223    7  HPFS/NTFS
/dev/sda2           95356      121601   210820995    7  HPFS/NTFS
/dev/sda3           60050       95355   283589633    5  Extended
/dev/sda5           60050       93920   272059392   83  Linux
/dev/sda6           93920       95355    11529216   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18141814

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2           25497      121600   771955380    f  W95 Ext'd (LBA)
/dev/sdb5           50993      121600   567158728+   7  HPFS/NTFS


/dev/sda2 is my windows 7 boot partition. However, after I installed ubuntu, it doesn't see the win7 partition, and will only boot into ubuntu. I need to be able to boot into the win7 partition. Can anyone help me add it to the boot options?

Thanks!

---

### Post by wilee-nilee on 2010-06-23
Run in the terminal.
```
sudo update-grub
```

If this does not get windows to boot post the readout from running the bootscript in my signature in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by elusive_elf on 2010-06-23
I ran the grub update and rebooted. No change, still booted straight into Ubuntu.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  64   964,696,509   964,696,446   7 HPFS/NTFS
/dev/sda2    *  1,531,878,075 1,953,520,064   421,641,990   7 HPFS/NTFS
/dev/sda3         964,698,110 1,531,877,375   567,179,266   5 Extended
/dev/sda5         964,698,112 1,508,816,895   544,118,784  83 Linux
/dev/sda6       1,508,818,944 1,531,877,375    23,058,432  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2         409,593,240 1,953,503,999 1,543,910,760   f W95 Ext d (LBA)
/dev/sdb5         819,186,543 1,953,503,999 1,134,317,457   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B8901B4E901B128C                       ntfs       New Volume                    
/dev/sda2        B474773A7476FF04                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        717c0483-73fa-4a06-814b-bff58d29b3a0   ext4                                     
/dev/sda6        1f587b3c-deff-4555-8d3d-33b338fa8731   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64ECB0FDECB0CB16                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 717c0483-73fa-4a06-814b-bff58d29b3a0
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 717c0483-73fa-4a06-814b-bff58d29b3a0
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 717c0483-73fa-4a06-814b-bff58d29b3a0
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=717c0483-73fa-4a06-814b-bff58d29b3a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 717c0483-73fa-4a06-814b-bff58d29b3a0
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=717c0483-73fa-4a06-814b-bff58d29b3a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 717c0483-73fa-4a06-814b-bff58d29b3a0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 717c0483-73fa-4a06-814b-bff58d29b3a0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=717c0483-73fa-4a06-814b-bff58d29b3a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1f587b3c-deff-4555-8d3d-33b338fa8731 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 768.9GB: boot/grub/core.img
 670.1GB: boot/grub/grub.cfg
 768.9GB: boot/initrd.img-2.6.32-21-generic
 768.9GB: boot/vmlinuz-2.6.32-21-generic
 768.9GB: initrd.img
 768.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

---

### Post by wilee-nilee on 2010-06-23
Is the sda HD first in the boot list in bios? 

In your first post the fdisk showed sda1 as having the boot flag, the script now shows sda2 as having the boot flag, did you move it in between, and did it boot before from sda1 having the flag on it. sda1 is missing a boot file setup is why I ask.

---

### Post by darkod on 2010-06-23
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

You have no win7 boot files. You are missing /bootmgr and /boot/BCD. Not sure if you had the 100MB win7 boot partition and deleted it, or they just went missing from /dev/sda2.

Use your win7 install dvd and run the /fixboot command manually as explained here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have win7 dvd, get an image for a repair cd here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You need to get your win7 boot files sorted out, after that it will be fine.

---

### Post by elusive_elf on 2010-06-23
no, it's second in the bios

---

### Post by wilee-nilee on 2010-06-23
> **elusive_elf said:**
> no, it's second in the bios

Follow darkod's advice they are correct.

---

### Post by elusive_elf on 2010-06-24
That's great, fixing the boot record worked!

one problem. I have to go into bios options in order to get it to work. Is there any way that I can get win7 and ubuntu onto a single menu on start up without having to tell the bios which HD to boot from?

---

### Post by darkod on 2010-06-24
> **elusive_elf said:**
> That's great, fixing the boot record worked!

one problem. I have to go into bios options in order to get it to work. Is there any way that I can get win7 and ubuntu onto a single menu on start up without having to tell the bios which HD to boot from?

Depending what happened during the repair of the windows boot files, and whether grub2 is on /dev/sda or /dev/sdb set one or the other disk as first boot option in BIOS until the computer boots into ubuntu directly.

That means you are booting the disk with grub2. It couldn't detect win7 without the boot files, but now once you boot into ubuntu just execute:

sudo update-grub

and it should be fine. You will get a grub2 boot menu at start. Right now it thinks ubuntu is the only OS and naturally doesn't show any menu.

---

