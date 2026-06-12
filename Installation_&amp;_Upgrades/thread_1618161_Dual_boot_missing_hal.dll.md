---
title: "Dual boot missing hal.dll"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by BRRFOC on 2010-11-10
Just installed Lucid on dual boot machine, Linux is OK but tried booting to Windows XP from grub2, missing hal.dll (this is apparently a common problem and I found many many posts on this topic).

Boot.ini contents below:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="/fastdetect" 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="" 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\="Unidentified operating system on drive C." 

On my machine I have one hard drive, Windows OS is sda1 and XP filesystem is sda5 (so previously I had drive E:\ as my XP shell), note that boot.ini shows C:\="Unidentified operating system on drive C." Both appear to be untouched by Linux install, and files seem to be intact, so I'm guessing the problem is either MBR or grub.cfg, automatically generated contents for this entry below:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d8-0702
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


Current grub.cfg shows
    set root='(hd0,1)'

Searching for solutions, looks like most appropriate solution is to load the Recovery Console from XP setup disk, delete boot.ini, restart the Recovery Console and run:
    C:\
    Bootcfg /Rebuild

Any suggestions?

---

### Post by Rubi1200 on 2010-11-10
Did you ever have a Wubi install prior to installing Ubuntu to the hard-drive?
[https://wiki.ubuntu.com/WubiGuide#Windows%20Missing%20hal.dll](https://wiki.ubuntu.com/WubiGuide#Windows%20Missing%20hal.dll)

From within Ubuntu, post the results of the boot info script linked at the bottom of my post please.

Thanks.

---

### Post by BRRFOC on 2010-11-10
Thanks for prompt reply, RESULTS.TXT are attached, note that boot partition is sda1 but Windows XP is sda5, not sure if this is part of the problems.

I'm pretty sure I did not use wubi for the install, typically I use live CD although I did perform upgrades on a couple occasions, which may account for multiple partitions listed in boot.ini.

Look forward to any suggestions you may have, I tried Recovery Console and Bootcfg /Rebuild, no luck so far. Looks like boot.ini is located on different partition than XP partition loaded with Recovery Console.

---

### Post by Mark Phelps on 2010-11-10
Text files are REALLY HARD to read! 

Please post the results of the script INSIDE your reply, surrounding the text with QUOTES.  You do that by pasting the text into your reply, highlighting the text, and then selecting the balloon-like icon on the second menu bar -- fourth item from the right.

---

### Post by BRRFOC on 2010-11-10
Sorry about that, see below. I've tried Recovery Console, Bootcfg /Rebuild, chkdisk, and from Linux dosfsck. Latter reports difference between "original" and "backup" but this is apparently not unusual. Data/files on Windows partitions appear to be intact. I suspect boot.ini may be part of the problem, but I was unable to change attributes (Windows prompted 'run chkdsk' which did not seem to help). Also suspect is partition table.

RESULTS.TXT

"                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,209,029     4,208,967   b W95 FAT32
/dev/sda2           4,209,091   232,736,767   228,527,677   f W95 Ext d (LBA)
/dev/sda5           4,209,093    82,349,189    78,140,097   7 HPFS/NTFS
/dev/sda6          82,350,080    83,324,927       974,848  83 Linux
/dev/sda7          83,326,976    98,949,119    15,622,144  83 Linux
/dev/sda8          98,951,168   177,074,175    78,123,008  83 Linux
/dev/sda9         177,076,224   180,979,711     3,903,488  83 Linux
/dev/sda10        180,981,760   188,792,831     7,811,072  83 Linux
/dev/sda11        188,794,880   204,417,023    15,622,144  83 Linux
/dev/sda12        204,419,072   227,854,335    23,435,264  83 Linux
/dev/sda13        227,856,384   232,736,767     4,880,384  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       44c1fe54-438d-45da-b85c-b830b7f39da6   ext4                                     
/dev/sda1        07D8-0702                              vfat       OS                            
/dev/sda11       fce49b51-1bee-4b73-a8f9-43e4c35f44b3   ext4                                     
/dev/sda12       9e8c44a5-54f2-4dbe-925d-b6f6f29f4793   ext4                                     
/dev/sda13       1cb24118-d2ec-44b5-aa96-557f81cc6a55   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        023C042E3C041EF3                       ntfs                                     
/dev/sda6        074c098a-e613-4922-9587-acbf07609d2f   ext4                                     
/dev/sda7        1c0d249a-2f5a-42c4-959f-dae7527e3429   ext4                                     
/dev/sda8        cd8df926-eef5-47c1-9127-f338638d0942   ext4                                     
/dev/sda9        48ba632d-b387-41a0-81f0-2fefc6df50bc   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda9        /tmp                     ext4       (rw)
/dev/sda12       /archive                 ext4       (rw)
/dev/sda6        /boot                    ext4       (rw)
/dev/sda8        /home                    ext4       (rw)
/dev/sda11       /usr                     ext4       (rw)
/dev/sda10       /var                     ext4       (rw)
/dev/sr0         /media/XP_PRO_SP2_ENG    iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1020,gid=1020,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1        /media/OS                vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1020,gid=1020,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /media/023C042E3C041EF3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="/fastdetect" 

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="" 

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\="Unidentified operating system on drive C." 


============================= sda6/grub/grub.cfg: =============================

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
set root='(hd0,11)'
search --no-floppy --fs-uuid --set fce49b51-1bee-4b73-a8f9-43e4c35f44b3
if loadfont /share/grub/unicode.pf2 ; then
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
search --no-floppy --fs-uuid --set 074c098a-e613-4922-9587-acbf07609d2f
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 074c098a-e613-4922-9587-acbf07609d2f
	linux	/vmlinuz-2.6.32-25-generic-pae root=UUID=1c0d249a-2f5a-42c4-959f-dae7527e3429 ro   quiet splash
	initrd	/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 074c098a-e613-4922-9587-acbf07609d2f
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/vmlinuz-2.6.32-25-generic-pae root=UUID=1c0d249a-2f5a-42c4-959f-dae7527e3429 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 074c098a-e613-4922-9587-acbf07609d2f
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 074c098a-e613-4922-9587-acbf07609d2f
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d8-0702
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda6: Location of files loaded by Grub: ===================


  42.3GB: grub/core.img
  42.3GB: grub/grub.cfg
  42.1GB: initrd.img-2.6.32-25-generic-pae
  42.1GB: vmlinuz-2.6.32-25-generic-pae

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# /archive was on /dev/sda12 during installation
UUID=9e8c44a5-54f2-4dbe-925d-b6f6f29f4793 /archive        ext4    defaults        0       2
/dev/sda6       /boot           ext4    defaults        0       2
/dev/sda8       /home           ext4    defaults        0       2
/dev/sda9       /tmp            ext4    defaults        0       2
# /usr was on /dev/sda11 during installation
UUID=fce49b51-1bee-4b73-a8f9-43e4c35f44b3 /usr            ext4    defaults        0       2
# /var was on /dev/sda10 during installation
UUID=44c1fe54-438d-45da-b85c-b830b7f39da6 /var            ext4    defaults        0       2
# swap was on /dev/sda13 during installation
UUID=1cb24118-d2ec-44b5-aa96-557f81cc6a55 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  42.6GB: initrd.img
  42.6GB: vmlinuz:

---

### Post by Quackers on 2010-11-10
Hmm, I'm not sure you've got enough partitions there! :-) :-) :-)

I do notice that a couple of grub boot files are in sda6 (which is where grub is looking for them) but etc/fstab and the Ubuntu operating system is in sda7.
I don't know if that's significant or not. Other than that I wouldn't know where to start! Sorry.

---

### Post by oldfred on 2010-11-11
In your boot.ini they refer to partition 3, but windows is in partition 1 and partition 5?

If you have a lot of partitions it helps to label them. You can use gparted when you create them or disk utility to add labels.

---

### Post by BRRFOC on 2010-11-12
Correct oldfred, this has to do with original Windows install, and somehow I ended up with mapping XP filesystem to E:\ rather than C:\. I like your suggestion about using labels, but I'm not familiar enough with Windows to know whether or not these labels can be placed in boot.ini.

I'm assuming that my boot.ini is incorrect, I tried editing and pointing to partition 5 rather than 3, no luck there. Boot.ini, ntldr, ntdetect are in the 1st partion, but the filesystem is in the 5th.

---

### Post by oldfred on 2010-11-12
All your boot files are in sda1 if you look at the boot info script. Windows has to be installed to a primary partition to boot from. Second installs of windows can be in a logical partition but only can boot thru the install in the primary partition.

Lot of detail but pictures pictures explain a lot:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

The labeling is in a partition and can be used in Linux fstab instead of sda1 or UUID, and labels are listed with the blkid and other commands so it helps to know what is where.

---

### Post by efflandt on 2010-11-12
A corrupt or missing HAL.DLL is a confusing error that may not really mean that it is corrupt or missing, just that it cannot be found on the partition boot.ini is pointing to.  I ran into that problem when trying to image a drive with PING (Part Image is not Ghost), which did not know how to handle a Dell recovery partition, so it changed boot.ini to one partition lower before making the image, thinking that you would not reinstall the recovery partition.  But it forgot to change boot.ini back to normal afterwards, which resulted in the HAL.DLL error when trying to boot the existing system.

I am not certain of a correct boot.ini entry for booting a logical partition, especially when for some reason the boot sector of sda5 thinks it starts at sector 63 (when it does not).

---

### Post by oldfred on 2010-11-12
I think efflandt has it with the boot sector issue. Was sda5 a copy from sda1? The boot sector has to have correct windows code. I am not sure windows even repairs boot sectors in logical partitions, but testdisk may rebuild it.

If the partition was copied then the backup boot sector is also wrong but testdisk has a rebuild bootsector function.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

