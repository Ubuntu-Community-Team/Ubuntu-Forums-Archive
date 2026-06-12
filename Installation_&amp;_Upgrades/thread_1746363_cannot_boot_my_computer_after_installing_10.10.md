---
title: "cannot boot my computer after installing 10.10"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by uli on 2011-05-01
Greetings!
I recently installed Ubuntu 10.10 to my second hard drive. Windows 7 resides on the other hard drive. When I try to boot into my computer, neither Windows 7 nor Ubuntu 10.10 are listed - only a blinking cursor in the left upper corner of a black screen.
I can start my computer only from the CD with Ubuntu 10.10 iso on it.
Here is the boot_info_script:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,925,593,087 1,925,386,240   7 HPFS/NTFS
/dev/sda3       1,925,593,088 1,953,122,303    27,529,216   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   938,375,167   938,373,120  83 Linux
/dev/sdb2         938,377,214   976,771,071    38,393,858   5 Extended
/dev/sdb5         938,377,216   976,771,071    38,393,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6C7475C874759594                       ntfs       SYSTEM                        
/dev/sda2        7474A84874A80F44                       ntfs       OS                            
/dev/sda3        F6AED64EAED606D1                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        935fd42c-4572-4688-8996-acffbe258270   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f39430e6-0074-4131-aa24-35be499e5a02   swap                                     
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
/dev/sdb1        /media/935fd42c-4572-4688-8996-acffbe258270 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=935fd42c-4572-4688-8996-acffbe258270 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=935fd42c-4572-4688-8996-acffbe258270 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6c7475c874759594
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set f6aed64eaed606d1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/935fd42c-4572-4688-8996-acffbe258270 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/f39430e6-0074-4131-aa24-35be499e5a02 ext4	(rw,nosuid,nodev,uhelper=udisks)
/dev/loop0                                              squashfs                                 
/dev/sda1        6C7475C874759594                       ntfs       SYSTEM                        
/dev/sda2        7474A84874A80F44                       ntfs       OS                            
/dev/sda3        F6AED64EAED606D1                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        935fd42c-4572-4688-8996-acffbe258270   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f39430e6-0074-4131-aa24-35be499e5a02   swap                                     
/dev/sdb: PTTYPE="dos" 


=================== sdb1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-28-generic-pae
 141.8GB: boot/vmlinuz-2.6.35-28-generic-pae
    .7GB: initrd.img
 141.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

When I try to sudo update-grub I get the following error:
cannot find a device for / (is /dev mounted?)

I am too inexperienced to know what to do now.
BTW: the Windows 7 is a OEM installation and I do not have a CD for it.

Thanks for your help.
Uli

---

### Post by uli on 2011-05-02
Hello all!

This is a follow-up to my thread (above) started yesterday.
I found the excellent post by drs305 ([http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) ) and followed his instructions precisely by copying and pasting. To no avail. I still can only boot my computer using the Ubuntu 10.10 iso CD (Live CD).

By mounting /media/SYSTEM of the Windows installation I can see that the grub.cfg file is not in the boot sector.

I can also mount /media/935fd42c-4572-4688-8996-acffbe258270 to get into my Linux installation and I can find the 'grub' sub-folder in the 'boot' folder there. I tried to paste the 'grub' sub-folder into the Windows 'Boot' folder, but that did not do the trick, either (obviously too naive an approach.)
 
( One little oddity: When I am in my Linux installation I have to use "cd etc" rather than "cd /etc" to get into that folder. If I use "cd /etc" I am returned to the Ubuntu "Live CD".) 

I hope that someone can help me to revive my "dead" computer.

Thank you!
Uli

---

### Post by garvinrick4 on 2011-05-02
Take your Windows Recovery CD or install Cd and run the two commands from this link:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
That will get your Windows booting: Edit you do not have disk use next post:

In a live CD (install Ubuntu Cd using Try Ubuntu) open a terminal and run this
There are many ways to do this and I am going to use a way that puts ubuntu and Windows
to boot (your choice) in this drive right now and your Windows drive will just boot windows right now
with updating grub in live cd: Copy and paste these:
                          ```
sudo mount /dev/sdb1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 
``````
grub-install /dev/sdb
``````
update-grub
``````
exit
```                           ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
```You must select which drive you want to boot off of at any particular time. If you leave it on Ubuntu drive in BIOS you can boot either

EDIT: I see you do not have your Windows disk: . I will find you web site to download a Windows 7 recovery disk:
If not we can use Lilo to boot disk sda (windows disk) lilo is a different grub. will work if needed: See next post for lilo run first and then Ubuntu on sdb:

---

### Post by garvinrick4 on 2011-05-02
In Live CD with internet working run these two commands to get Windows booting:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Now run the code with Ubuntu CD in previous post:
Will say error in lilo do not worry all we need is the mbr part:
###All you did wrong at install was put grub2 in sda instead of sdb which is the Ubuntu drive:

---

### Post by garvinrick4 on 2011-05-02
Here is a couple of ways to get your Windows repair disk: 

[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

---

### Post by uli on 2011-05-03
Thanks for your help.
Since I do not have a Windows7 CD I tried to go the LILO route.
After installing lilo I tried to configure it and I got the following message:
Your /etc/fstab configuration file gives device aufs as the root          &#9474; 
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block       &#9474; 
 &#9474; device. Either your fstab is broken and you should fix it, or you are     &#9474; 
 &#9474; using hardware (such as a RAID array) which this simple configuration     &#9474; 
 &#9474; program does not handle.   

What should I do?

---

### Post by uli on 2011-05-03
As you might guess, nothing happened when I tried to boot without the installation (Ubuntu) CD since LILO never got configured.

However, I forgot to post the re-run boot_info_script after installing lilo. 
Here it is:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,925,593,087 1,925,386,240   7 HPFS/NTFS
/dev/sda3       1,925,593,088 1,953,122,303    27,529,216   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   938,375,167   938,373,120  83 Linux
/dev/sdb2         938,377,214   976,771,071    38,393,858   5 Extended
/dev/sdb5         938,377,216   976,771,071    38,393,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6C7475C874759594                       ntfs       SYSTEM                        
/dev/sda2        7474A84874A80F44                       ntfs       OS                            
/dev/sda3        F6AED64EAED606D1                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        935fd42c-4572-4688-8996-acffbe258270   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f39430e6-0074-4131-aa24-35be499e5a02   swap                                     
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
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/935fd42c-4572-4688-8996-acffbe258270 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=935fd42c-4572-4688-8996-acffbe258270 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=935fd42c-4572-4688-8996-acffbe258270 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 935fd42c-4572-4688-8996-acffbe258270
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6c7475c874759594
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set f6aed64eaed606d1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/935fd42c-4572-4688-8996-acffbe258270 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/f39430e6-0074-4131-aa24-35be499e5a02 ext4	(rw,nosuid,nodev,uhelper=udisks)
/dev/loop0                                              squashfs                                 
/dev/sda1        6C7475C874759594                       ntfs       SYSTEM                        
/dev/sda2        7474A84874A80F44                       ntfs       OS                            
/dev/sda3        F6AED64EAED606D1                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        935fd42c-4572-4688-8996-acffbe258270   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f39430e6-0074-4131-aa24-35be499e5a02   swap                                     
/dev/sdb: PTTYPE="dos" 


=================== sdb1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
 154.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-28-generic-pae
 141.8GB: boot/vmlinuz-2.6.35-28-generic-pae
    .7GB: initrd.img
 141.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

Now I seem to have lilo in the mbr (of /dev/sda) and grub in the /boot/grub folder of /dev/sdb1. Should I un-install one of them?

---

### Post by garvinrick4 on 2011-05-03
Run the Ubuntu live Cd instructions given earlier the 5 lines of code to install grub in sdb.
and make sure the Bios is set to boot off of that drive:

---

### Post by uli on 2011-05-03
Thank you, garvinrick4. It was actually your first reply to my thread that worked. 
What I had omitted initially was to change the boot sequence in my BIOS to the hard drive that contained my Ubuntu distribution. 
Now I can boot into both, Windows 7 and Ubuntu 10.10
Thanks again for your help!

Uli

---

### Post by garvinrick4 on 2011-05-03
If you notice in original boot script no grub2 in sdb and grub2 installed in sda. You just
installed ubuntu and put the grub2 in wrong drive sda and it overwrote the Windows grub.
So then nothing booted. Lilo was going to show errors but works, always shows errors.
Then we put grub2 into sdb (ubuntu drive) and updated grub so it added windows to grub
menu and when booted off of would now boot Ubuntu and Windows. You had no windows disks so lilo was only way and errors freaked you out abit but was anticapated. All code actually did what it was suppose to do and works when done right as you did. Just happy you are up and running and all is well. Mark as Solved in thread tools if you would please. Enjoy your Ubuntu and have a nice day.

---

### Post by uli on 2011-05-03
Thank you, garvinrick4, for the reminder to close this thread.
However, I do not know how to do this.
Maybe one of the moderators can block this thread. Bye! ):P

---

