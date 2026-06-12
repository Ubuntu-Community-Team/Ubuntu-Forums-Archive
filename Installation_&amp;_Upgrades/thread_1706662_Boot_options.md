---
title: "Boot options"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by asramasarma on 2011-03-14
I have installed Windows 7 Enterprise N(64 bit) and then I have installed Ubuntu 10.10. I have couple of HDDs. UBUNTU installation completed successfully however when I started the system there are no boot options directly windows is getting started. 

Help is much appreciated.

Thanks,
Seetharam.

---

### Post by Hakunka-Matata on 2011-03-14
If you have Ubuntu on a different Hard Drive, change the 'Boot order' in BIOS.  In other words, tell BIOS to boot your machine from the Ubuntu Drive instead of the Windows drive.  That is a POSSIBILITY.  If that does not work, come back here.

---

### Post by asramasarma on 2011-03-14
I have tried installing in both hard disks and the result is same :(. I have changed the boot order also.

---

### Post by Hakunka-Matata on 2011-03-14
open the bootinfoscript link in my signature, download the script file, run the scripfile, and post the output of the scriptfile into a reply.  Copy the entire output of the scriptfile, "highlight" and copy, and paste into the reply post BETWEEN CODE TAGS.  That will show us how your bootloader is configured, so we can help you.


Another way of saying it.
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted into the post, highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by asramasarma on 2011-03-14
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sdb5 starts at sector 266102784.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,126   488,409,087   488,392,962   f W95 Ext d (LBA)
/dev/sda5              16,128   281,567,891   281,551,764   7 HPFS/NTFS
/dev/sda6         281,569,280   479,909,887   198,340,608  83 Linux
/dev/sda7         479,911,936   488,409,087     8,497,152  82 Linux swap / Solaris
/dev/sda2         488,409,088   976,769,023   488,359,936   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   266,102,528   265,895,681   7 HPFS/NTFS
/dev/sdb3         266,102,782   488,396,799   222,294,018   5 Extended
/dev/sdb5         266,102,784   488,394,751   222,291,968   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        22B4B01CB4AFF109                       ntfs       Sreelu                        
/dev/sda5        6A9C0F599C0F1EE7                       ntfs       Seetharam                     
/dev/sda6        591594c9-d942-4de5-b58c-47ba4c3a0696   ext4                                     
/dev/sda7        c887e79c-5fa2-429f-9bd2-0b64e4a1d18e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E81C481A1C47E1E4                       ntfs       System Reserved               
/dev/sdb2        64AC4DE9AC4DB678                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        68B4D3C8B4D39742                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/591594c9-d942-4de5-b58c-47ba4c3a0696 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 591594c9-d942-4de5-b58c-47ba4c3a0696
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 591594c9-d942-4de5-b58c-47ba4c3a0696
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 591594c9-d942-4de5-b58c-47ba4c3a0696
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=591594c9-d942-4de5-b58c-47ba4c3a0696 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 591594c9-d942-4de5-b58c-47ba4c3a0696
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=591594c9-d942-4de5-b58c-47ba4c3a0696 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 591594c9-d942-4de5-b58c-47ba4c3a0696
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 591594c9-d942-4de5-b58c-47ba4c3a0696
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e81c481a1c47e1e4
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
UUID=591594c9-d942-4de5-b58c-47ba4c3a0696 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c887e79c-5fa2-429f-9bd2-0b64e4a1d18e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 232.3GB: boot/grub/core.img
 170.0GB: boot/grub/grub.cfg
 144.7GB: boot/initrd.img-2.6.35-22-generic
 232.3GB: boot/vmlinuz-2.6.35-22-generic
 144.7GB: initrd.img
 232.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by kansasnoob on 2011-03-14
Please also post the output of:

```
sudo parted -l
```

BTW that's a lower case L.

---

### Post by kansasnoob on 2011-03-14
A couple of things confuse me, /dev/sda appears to begin with an extended partition, and a boot flag is set on it:

```
Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

**[COLOR="Red"]/dev/sda1 * 16,126 488,409,087 488,392,962 f W95 Ext d (LBA)[/COLOR]**
/dev/sda5 16,128 281,567,891 281,551,764 7 HPFS/NTFS
/dev/sda6 281,569,280 479,909,887 198,340,608 83 Linux
/dev/sda7 479,911,936 488,409,087 8,497,152 82 Linux swap / Solaris
/dev/sda2 488,409,088 976,769,023 488,359,936 7 HPFS/NTFS

```

But you'll see it has some Win stuff on it:

```
sda5: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda5 starts
at sector 63.
Operating System: Windows 7
Boot files/dirs: /Windows/System32/winload.exe

```

Yet /dev/sdb appears to have a full Win 7 install :confused:

And it may have a problem:

```
sdb5: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: [B][COLOR="Red"]According to the info in the boot sector, sdb5 starts
at sector 2. But according to the info from fdisk,
sdb5 starts at sector 266102784.[/COLOR][/B]
Operating System:
Boot files/dirs:
```

Did you run this puter through a blender :)

---

### Post by asramasarma on 2011-03-14
sudo parted -l:

Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      8257kB  250GB  250GB   extended                  boot, lba
 5      8258kB  144GB  144GB   logical   ntfs
 6      144GB   246GB  102GB   logical   ext4
 7      246GB   250GB  4351MB  logical   linux-swap(v1)
 2      250GB   500GB  250GB   primary   ntfs


Model: ATA ST3250318AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  106MB  105MB  primary   ntfs         boot
 2      106MB   136GB  136GB  primary   ntfs
 3      136GB   250GB  114GB  extended
 5      136GB   250GB  114GB  logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by asramasarma on 2011-03-15
Please suggest to fix this problem.

---

### Post by Hakunka-Matata on 2011-03-16
check unmounted, and unmountable, partitions using GParted:  highlight partition, right button, CHECK

---

### Post by kansasnoob on 2011-03-16
OK, if you're booting straight to Windows, then the 250GB drive must be set to boot first in BIOS.

I would think if the 500GB drive is set to boot first in BIOS you'd see the grub menu and be able to boot either Ubuntu or Windows using grub.

---

