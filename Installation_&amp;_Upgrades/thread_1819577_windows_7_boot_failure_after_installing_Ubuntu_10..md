---
title: "windows 7 boot failure after installing Ubuntu 10.10"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by bars123 on 2011-08-06
Hi,


I installed Ubuntu Maverick Meerkat (10.10) on my HP G72 B66US laptop, which came with windows 7 preloaded.

 I reduced the partition size in windows using disk management and  later using GParted, I created partitions for installing Ubuntu.

The installation was successful and I was able to log on to Ubuntu. However, When I try to log on to windows, I get "Starting Windows" for a few seconds and then the system restarts. GRUB shows windows 7 loader and windows vista loader on sda 2 and sda 3 respectively ( I dont have vista on my laptop). 

I can access the windows 7 drive (c:  ) from ubuntu, though i can't log on to windows 7. Please help me regain access to windows. 

I am attaching a screenshot of my partitions

Thanks,
Bharadwaj.

---

### Post by oldfred on 2011-08-06
Post this from Ubuntu to see if something looks out of place. But normally if grub has passed control to windows then it is a windows issue.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by bars123 on 2011-08-07
thanks oldfred for responding. here is the output.


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985   7 NTFS / exFAT / HPFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   479,401,983   478,992,384  42 SFS
/dev/sda4         479,404,030   976,773,119   497,369,090   f W95 Extended (LBA)
/dev/sda5         479,404,032   929,964,031   450,560,000  83 Linux
/dev/sda6         929,966,080   934,062,079     4,096,000  82 Linux swap / Solaris
/dev/sda7         934,064,128   976,773,119    42,708,992  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        4AFC0060FC0048A1                       ntfs       SYSTEM
/dev/sda3        EE2E10DB2E109F21                       ntfs       
/dev/sda5        be124fef-b574-4188-9c11-c095a7ef9779   ext3       
/dev/sda6        5f7028c9-6639-4176-aaa2-de11f9d8d577   swap       
/dev/sda7        920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /home                    ext3       (rw,commit=0)
/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)


=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
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
menuentry 'Ubuntu, with Linux 2.6.39.3-candela' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	linux	/boot/vmlinuz-2.6.39.3-candela root=UUID=920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c ro acpi_backlight=vendor  quiet splash acpi_backlight=vendor
	initrd	/boot/initrd.img-2.6.39.3-candela
}
menuentry 'Ubuntu, with Linux 2.6.39.3-candela (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	echo	'Loading Linux 2.6.39.3-candela ...'
	linux	/boot/vmlinuz-2.6.39.3-candela root=UUID=920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c ro single acpi_backlight=vendor
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39.3-candela
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c ro acpi_backlight=vendor  quiet splash acpi_backlight=vendor
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c ro single acpi_backlight=vendor
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c ro acpi_backlight=vendor  quiet splash acpi_backlight=vendor
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c ro single acpi_backlight=vendor
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4AFC0060FC0048A1
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set EE2E10DB2E109F21
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=920bd46d-8dc1-4e81-a9d8-6a3ac366cd5c /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=be124fef-b574-4188-9c11-c095a7ef9779 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=5f7028c9-6639-4176-aaa2-de11f9d8d577 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 451.341907501 = 484.624683008  boot/grub/core.img                             1
 451.349987030 = 484.633358336  boot/grub/grub.cfg                             1
 451.383232117 = 484.669054976  boot/initrd.img-2.6.35-22-generic              5
 451.393417358 = 484.679991296  boot/initrd.img-2.6.35-28-generic              5
 451.407360077 = 484.694962176  boot/initrd.img-2.6.39.3-candela              11
 451.361495972 = 484.645715968  boot/vmlinuz-2.6.35-22-generic                 3
 451.368072510 = 484.652777472  boot/vmlinuz-2.6.35-28-generic                 4
 451.332408905 = 484.614483968  boot/vmlinuz-2.6.39.3-candela                  3
 451.393417358 = 484.679991296  initrd.img                                     5
 451.383232117 = 484.669054976  initrd.img.old                                 5
 451.368072510 = 484.652777472  vmlinuz                                        4
 451.361495972 = 484.645715968  vmlinuz.old                                    3


```

---

### Post by oldfred on 2011-08-07
It looks like you have boot files in both sda2 & sda3. You might try booting sda3.

But you used windows to create more than 4 partitions. It then converted to dynamic which per windows cannot be converted back without full backups and total reinstall. Some third party tools may work if you have not used the dynamic to work across actual physical partitions. Dynamic or SFS partitions are like LVM in Linux or logical partitions.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

### Post by bars123 on 2011-08-08
> **oldfred said:**
> 
But you used windows to create more than 4 partitions. It then converted to dynamic which per windows cannot be converted back without full backups and total reinstall. 

Some third party tools may work if you have not used the dynamic to work across actual physical partitions. Dynamic or SFS partitions are like LVM in Linux or logical partitions.



I used Gparted to create the partitions, not windows 7. all i did in windows was shrinking the c: drive.

regarding 3rd party tools, i am not able to log on to windows 7, how can i use them. i tried repairing using windows 7 dvd, but to no avail.

when i tried commands like scanOS, etc in windows recovery console, it says that there is no OS. i even tried installing windows 7 again, the dvd is not able to detect any hard disk to install the OS
 :(

---

### Post by oldfred on 2011-08-08
Some windows tools do not work with window proprietary SFS/dynamic logical volume system.

If you have good backups as this is more risky.

Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)

---

### Post by bars123 on 2011-08-09
how can i install them if i am not able to log on to windows OS?

Can i run this from CD at system boot?



> **oldfred said:**
> Some windows tools do not work with window proprietary SFS/dynamic logical volume system.

If you have good backups as this is more risky.

Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)

---

### Post by oldfred on 2011-08-09
Testdisk is easily run from an Ubuntu liveCD or is already installed in many Linux based computer repairCDs.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by bars123 on 2011-08-10
i ran testdisk. please guide me.

please take a look at the screenshots.

---

### Post by oldfred on 2011-08-10
I am not sure what sda1 is/was. Perhaps a vendor recovery partition? I might try the rebuild BS to see it that will put a valid boot sector in sda1.

But the boot issues are with the boot partition sda2 and the main partition sda3. What does testdisk say about them? Same second screen that shows boot sector & backup bs.

---

### Post by bars123 on 2011-08-11
> **oldfred said:**
> I am not sure what sda1 is/was. Perhaps a vendor recovery partition? I might try the rebuild BS to see it that will put a valid boot sector in sda1.

But the boot issues are with the boot partition sda2 and the main partition sda3. What does testdisk say about them? Same second screen that shows boot sector & backup bs.

rebuildOS does nothing :(

i tried changing it from dynamic to HPFS-NTFS but it does not happen. Please see "screenshot1". At the bottom of the console it says that "Change Type,this setting cannot be saved on disk"

How can i make a permanent change from SFS to HPFS-NTFS?

---

### Post by oldfred on 2011-08-11
We have seen several users use the Minitool I have linked to in post #4. You might want to try that. You convert from SFS or Dynamic to Basic.

---

