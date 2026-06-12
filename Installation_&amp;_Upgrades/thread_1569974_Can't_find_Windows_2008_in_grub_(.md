---
title: "Can't find Windows 2008 in grub :("
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by Barty on 2010-09-07
Hello,

I used to have dualboot with Win7 and Ubuntu 10.04, well i still have but i recently installed win 2008 server on another disk. After that i had to reinstall grub and everything works except that i cant find my 2008 install. But i can still find my win7.

I found a script that prints a lot of information about my disk conf :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: okänd filsystemstyp ""

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000,2 GB, 1000204886016 byte
255 huvuden, 63 sektorer/spår, 121601 cylindrar, totalt 1953525168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   972,814,335   972,607,488   7 HPFS/NTFS
/dev/sda3         972,814,336 1,939,611,647   966,797,312  83 Linux
/dev/sda4       1,939,613,694 1,953,523,711    13,910,018   5 Extended
/dev/sda5       1,939,613,696 1,953,523,711    13,910,016  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250,1 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar, totalt 488397168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sdb2         209,717,248   488,394,751   278,677,504   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250,1 GB, 250059350016 byte
240 huvuden, 63 sektorer/spår, 32301 cylindrar, totalt 488397168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,391,119   488,391,057   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        427CAFEA7CAFD6C7                       ntfs       Reserverad av systemet        
/dev/sda2        6E2CC17B2CC13EB9                       ntfs                                     
/dev/sda3        593d77ea-49f5-49f7-b83b-ffe2a3b89ff0   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5b4ff92d-4a77-4d8e-8a58-9455dba016d7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C83A4C133A4C0144                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        EAACC831ACC7F65B                       ntfs       Barty                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home/barty/hdd1         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /home/barty/hdd2         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /home/barty/hdd3         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
set locale_dir=($root)/boot/grub/locale
set lang=sv
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

### BEGIN /etc/grub.d/06_custom ###
menuentry "Windows 2008 x64" {
    set root=(hd1,1)
    chainloader +1   
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, med Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=593d77ea-49f5-49f7-b83b-ffe2a3b89ff0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, med Linux 2.6.32-24-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	echo	'Läser in Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=593d77ea-49f5-49f7-b83b-ffe2a3b89ff0 ro single 
	echo	'Läser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, med Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=593d77ea-49f5-49f7-b83b-ffe2a3b89ff0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, med Linux 2.6.32-23-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	echo	'Läser in Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=593d77ea-49f5-49f7-b83b-ffe2a3b89ff0 ro single 
	echo	'Läser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, med Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=593d77ea-49f5-49f7-b83b-ffe2a3b89ff0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, med Linux 2.6.32-21-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	echo	'Läser in Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=593d77ea-49f5-49f7-b83b-ffe2a3b89ff0 ro single 
	echo	'Läser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 593d77ea-49f5-49f7-b83b-ffe2a3b89ff0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 427cafea7cafd6c7
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=593d77ea-49f5-49f7-b83b-ffe2a3b89ff0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5b4ff92d-4a77-4d8e-8a58-9455dba016d7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Mina fina Mountningar
UUID=6E2CC17B2CC13EB9 /home/barty/hdd1 ntfs-3g defaults 0 0
UUID=C83A4C133A4C0144 /home/barty/hdd2 ntfs-3g defaults 0 0
UUID=EAACC831ACC7F65B /home/barty/hdd3 ntfs-3g defaults 0 0

=================== sda3: Location of files loaded by Grub: ===================


 607.7GB: boot/grub/core.img
 694.6GB: boot/grub/grub.cfg
 607.7GB: boot/initrd.img-2.6.32-21-generic
 607.7GB: boot/initrd.img-2.6.32-23-generic
 609.7GB: boot/initrd.img-2.6.32-24-generic
 607.7GB: boot/vmlinuz-2.6.32-21-generic
 498.5GB: boot/vmlinuz-2.6.32-23-generic
 607.8GB: boot/vmlinuz-2.6.32-24-generic
 609.7GB: initrd.img
 607.7GB: initrd.img.old
 607.8GB: vmlinuz
 498.5GB: vmlinuz.old
``` 

Hope somneone can help me!

//Barty

---

### Post by Mark Phelps on 2010-09-08
To see what you have available, I suggest you download and install EasyBCD from the NeoSmart Technology forums into Win7.

Then, run it and look to see what entries are there in the BCD.

You should see entries for both Win7 and Srvr 2008.

If that's the case, you will have to select the "Win7" entry in GRUB and then select the MS OS using the MS menu.  GRUB is not able to select entries from INSIDE the MS OS menu.

---

