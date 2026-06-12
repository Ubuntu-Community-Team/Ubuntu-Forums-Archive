---
title: "Dual boot problem, Ubuntu inactive!"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by gaargoyle on 2010-01-28
Hi guys... I hope you can help me, and that I've placed this the right  place.


**MY PROBLEM:** I had Ubuntu 9.10 installed on my hard drive, and  used Gparted to make a smaller partition, which I wanted Windows XP to  use. Nothing wrong so far. I then installed XP on the smaller partition,  and when everything was installed and fine, I tried rebooting. XP  started up. Fair enough. I restarted and went into boot selection. Every  time I tried choosing something different, it went into XP. I tried  booting from the Ubuntu disc, and Windows started. I tried running the  Ubuntu disc from within Windows, and got the box "*Windows - No Disk*"  popping up, with the message "*exception processing message c00013  parameters 75b6bf7c 4 75b6bf7c 75b6bf7c*". In other words, I can't even get into Grub. I've tried changing the  drive letter, as some site said could help, and I've tried going into  Disc Management to mark the Ubuntu-partition as active, but the option  is greyed out. It remains inactive.

Is anybody able to help?

---

### Post by Leppie on 2010-01-28
hi and welcome to the community,

could you [download and run meierfra's  script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt? you can do that using the ubuntu livecd.

---

### Post by presence1960 on 2010-01-28
Do what Leppie suggests so we can see exactly your setup & boot process. What most likely happened since windows & ububtu are on the same disk is that when you installed windows the GRUB bootloader on MBR was overwritten by the windows bootloader. It is a simple matter to restore GRUB to MBR but that info requested is needed.

---

### Post by gaargoyle on 2010-01-28
That would make a lot of sense... but as I mentioned, I can't run the ubuntu livecd from boot nor from within windows. Is there anything to do from within Windows?

---

### Post by audiomick on 2010-01-28
Have you been into the BIOS and put the cd-drive first in the boot sequence?

---

### Post by gaargoyle on 2010-01-28
I have, and I've even tried making the second and third parts of the booting sequence blank, but it still boots windows.

---

### Post by audiomick on 2010-01-28
OK, just to be sure:
when you are in windows, can you access anything at all from the CD drive? Play a CD, read a data CD, anything.
maybe the drive has a mechanical problem.

---

### Post by gaargoyle on 2010-01-28
Well, I was able to install Ubuntu a couple of days a go and XP earlier today, so nothing should be wrong with the drive.

I tried putting a music-CD and a film-DVD in it, and it took a while to open them, but it eventually did. It kept called them "install ubuntu" though, which might indicate that there's something wrong. Might it be a driver problem?

---

### Post by presence1960 on 2010-01-28
Run the script as Leppie suggests. That will do more towards getting the info we need than anything you can say.

It is loaded with info about the hard disks & boot process. here is mine so you can see the info it produces:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Testdisk is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   130,030,109   130,030,047   5 Extended
/dev/sda5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sda6           8,385,993    50,331,644    41,945,652  83 Linux
/dev/sda7          50,331,708    92,277,359    41,945,652  83 Linux
/dev/sda8          92,277,423   130,030,109    37,752,687  83 Linux
/dev/sda2         130,031,616   203,896,831    73,865,216   7 HPFS/NTFS
/dev/sda3         203,896,980   976,768,064   772,871,085  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a49f9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   104,854,377   104,852,330   7 HPFS/NTFS
/dev/sdc2         104,856,255   230,799,894   125,943,640   7 HPFS/NTFS
/dev/sdc3    *    230,801,408   312,578,047    81,776,640   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda2        280C57B90C5780AC                       ntfs       win-backup                    
/dev/sda3        b37b51c7-cc17-4401-a66c-4d43193d508a   ext3       backup                        
/dev/sda5        63538de2-1cc9-4451-ab42-5f8712695c89   swap                                     
/dev/sda6        e0b415e6-168b-49e7-b62b-0fc42c83a6d7   ext4       karmic                        
/dev/sda7        2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef   ext4       lucid                         
/dev/sda8        6d4ef10b-0252-44b1-aeaf-5730ff73bd99   ext4       sabayon                       
/dev/sdb1        8f5b8ecd-2930-46a1-8256-88235c860965   ext3       data                          
/dev/sdc1        1086EDD986EDBEFA                       ntfs       vista                         
/dev/sdc2        42D35EE6525751C9                       ntfs       win_data                      
/dev/sdc3        4E376602381A2ECA                       ntfs                                     

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

/dev/sda7        /                ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/data      ext3       (rw,nosuid,nodev,uhelper=devkit)


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
set root=(hd0,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro quiet splash
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 1086edd986edbefa
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
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/core.img
   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/initrd.img-2.6.31-18-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-18-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-11-generic" {
        recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-11-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-11-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single 
	initrd	/boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single 
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 1086edd986edbefa
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  25.7GB: boot/grub/core.img
  25.7GB: boot/grub/grub.cfg
  25.7GB: boot/initrd.img-2.6.32-10-generic
  25.7GB: boot/initrd.img-2.6.32-11-generic
  25.7GB: boot/vmlinuz-2.6.32-10-generic
  25.7GB: boot/vmlinuz-2.6.32-11-generic
  25.7GB: initrd.img
  25.7GB: initrd.img.old
  25.7GB: vmlinuz
  25.7GB: vmlinuz.old

========================== sda8/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/kernel-genkernel real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99
#          initrd /boot/initramfs-genkernel
#boot=sda8
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,0)
	chainloader +1
	savedefaulttitle Other Operating System - Microsoft Windows
	rootnoverify (hd2,0)
	chainloader +1
	savedefaulttitle Other Operating System - Microsoft Windows
	rootnoverify (hd0,1)
	chainloader +1
	savedefault
### Other detected distributions
title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic


=============================== sda8/etc/fstab: ===============================

UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 swap                    swap    defaults        0 0

=================== sda8: Location of files loaded by Grub: ===================


  47.2GB: boot/grub/grub.conf
  47.2GB: boot/grub/menu.lst
  47.2GB: boot/grub/stage2
  47.2GB: boot/initramfs-genkernel-x86_64-2.6.29-sabayon
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg
```

Refer to your machine's documentation as some makes such as Dell use F12 to choose the device to boot one time only (not permanent as in BIOS) without going into BIOS

---

### Post by gaargoyle on 2010-01-28
How do I run the script?

---

### Post by audiomick on 2010-01-28
I doubt it is a driver, but I am a bit out of my depth there.

This is just how I would go about problem solving, not based on any expert knowledge:

I would stick the XP install CD back in, and see if that wants to run.
I **do not** mean re-install XP. I am trying to find out how reliable the CD drive is. Assuming the installer starts, cancel out of it straight away.

---

### Post by presence1960 on 2010-01-28
> **gaargoyle said:**
> I have, and I've even tried making the second and third parts of the booting sequence blank, but it still boots windows.

I know this may be a dumb question, but you have to understand we have seen a lot in here. After selecting CD as first boot device did you Save Changes to CMOS?

---

### Post by audiomick on 2010-01-28
> **gaargoyle said:**
> How do I run the script?

Thats the thing, you have to have Ubuntu booted somehow, either a live CD or an install, and you can't right now, can you?

another option that I don't know how to do would be to  make a bootable USB and install from that. Maybe someone can point you to instructions for that.

---

### Post by presence1960 on 2010-01-28
> **audiomick said:**
> I doubt it is a driver, but I am a bit out of my depth there.

This is just how I would go about problem solving, not based on any expert knowledge:

[B][U]I would stick the XP install CD back in, and see if that wants to run.
I **do not** mean re-install XP. I am trying to find out how reliable the CD drive is. Assuming the installer starts, cancel out of it straight away[/U][/B].

I believe audiomick means boot the windows CD and see if the install process works. if it does just cancel.

Also just because you can read CD/DVDs doesn't mean that your optical drive is OK. It is a whole different animal booting  a bootable CD/DVD. before ruling the optical drive as defective I would clean it. I would also open the case and make sure all connections from the power supply to the CD/DVD drive & from the drive to the motherboard are seated firmly & properly.

You also should look at the documentation for your machine to see about setting BIOS to boot from CD. It is either a BIOS issue or a faulty optical drive. That is if you can test the ubuntu Live CD in another machine and verify it can be booted from the CD- not opened up from windows.

---

### Post by gaargoyle on 2010-01-28
Yes, I did save the changes to the CMOS.

And apparently the disc have no problems whatsoever with the Windows CD...

I'll shut it down once more and check the supplies, but I must admit that I don't know how to clean the optic drive.

---

### Post by audiomick on 2010-01-28
> **presence1960 said:**
> I believe audiomick means boot the windows CD and see if the install process works. if it does just cancel.

That's exactly what I mean. Did I get too colloquial? Sorry....

---

### Post by Leppie on 2010-01-28
> **gaargoyle said:**
> ...but I must admit that I don't know how to clean the optic drive.
best option is compressed air

---

### Post by presence1960 on 2010-01-28
> **Leppie said:**
> best option is compressed air

with the machine powered down. use a paper clip to open the optical drive. insert it into that pin hole under the tray and jiggle it. it will open the tray. 

Also if windows CD boots and the Ubuntu CD does not boot I would try burning another Live CD.

I have to go now. Time to bowl in my money league. You are in good hands with Leppie & audiomick. I will check back in 4 hours and hope to see you got it working.

---

### Post by gaargoyle on 2010-01-28
The power supplies are fine. Can I replace compressed air with simply blowing at it gently?

A thing I don't get is, if I try to run the Ubuntu "installer for windows" (I didn't know that option were there, before audiomick mentioned it) it comes with the same "Windows - No Disk" message, even though I'm trying to run a program I just downloaded, not a disc.

---

### Post by Leppie on 2010-01-28
> **presence1960 said:**
> I have to go now. Time to bowl in my money league. You are in good hands with Leppie & audiomick. I will check back in 4 hours and hope to see you got it working.
thanks for the trusting us, hopefully we don't make gaargoyle break the whole system :P

break a leg ;)

---

### Post by gaargoyle on 2010-01-28
I'll try to burn another installation, but I've run out of discs... so it'll have to wait to tomorrow

*sigh*

I hate Windows.

---

### Post by Leppie on 2010-01-28
> **gaargoyle said:**
> Can I replace compressed air with simply blowing at it gently?
not sure how you would reach the laser in the enclosure... it's important that you don't get saliva on the laser lens as this would only make things worse.

> **gaargoyle said:**
> A thing I don't get is, if I try to run the Ubuntu "installer for windows" (I didn't know that option were there, before audiomick mentioned it) it comes with the same "Windows - No Disk" message, even though I'm trying to run a program I just downloaded, not a disc.
this sounds very much like a misburn... do as audiomick said, download a new image, check the md5sum, burn the cd at a low speed (inferior to 10x) then check the md5sum again. if after this all is well, boot off the newly burned livecd

---

### Post by audiomick on 2010-01-28
> **Leppie said:**
> not sure how you would reach the laser in the enclosure... use a drinking straw
> 
it's important that you don't get saliva on the laser lens as this would only make things worse.
yes indeed.

> this sounds very much like a misburn... do as audiomick said, download a new image, check the md5sum, burn the cd at a low speed (inferior to 10x) then check the md5sum again. if after this all is well, boot off the newly burned livecd
did I say that? Good advice though.

---

### Post by Leppie on 2010-01-28
> **audiomick said:**
> use a drinking straw
nice one, hadn't thought of that :)

> **audiomick said:**
> did I say that? Good advice though.
you are way better than you realize ;)

---

### Post by gaargoyle on 2010-01-30
I bought an external disc drive today, and managed to boot into the "try Ubuntu without installing" option. I ran the Boot Info Script:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8dc831b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   855,091,754   855,091,692  83 Linux
/dev/sda2    *    855,091,755   958,630,679   103,538,925   7 HPFS/NTFS
/dev/sda3         958,630,680   976,768,064    18,137,385   5 Extended
/dev/sda5         958,630,743   976,768,064    18,137,322  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8914f1e3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8899a696-016e-4794-bc61-9329e1acc10c   ext4                                     
/dev/sda2        385C63495C63014C                       ntfs                                     
/dev/sda5        ff211524-953a-4917-a0be-9cceab900836   swap                                     
/dev/sdb1        F50A-A2E8                              vfat       Backup                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 8899a696-016e-4794-bc61-9329e1acc10c
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8899a696-016e-4794-bc61-9329e1acc10c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8899a696-016e-4794-bc61-9329e1acc10c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8899a696-016e-4794-bc61-9329e1acc10c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8899a696-016e-4794-bc61-9329e1acc10c ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8899a696-016e-4794-bc61-9329e1acc10c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8899a696-016e-4794-bc61-9329e1acc10c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8899a696-016e-4794-bc61-9329e1acc10c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8899a696-016e-4794-bc61-9329e1acc10c ro single 
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8899a696-016e-4794-bc61-9329e1acc10c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff211524-953a-4917-a0be-9cceab900836 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by oldfred on 2010-01-30
You should just have to reinstall grub2 to the MBR and update the config file to include windows.

While in the LiveCD, open terminal and run:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run: 
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Then reboot and in Ubuntu:
sudo update-grub  #should add windows to grub.cfg for next reboot.


Three ways (one above)  
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by gaargoyle on 2010-01-30
It worked! Thank you so much, guys! I owe you :)

---

### Post by alkh3myst on 2010-01-31
Honestly, are you guys really trying to help anybody, or are you just trying to show off how much jargon and buzzwords you can use? This script is a .sh file; several other people on this thread also can't use it! I had a Wubi installation that I put on it's own partition using LVPM, which also changed the formatting from EXT 4 to EXT 3. No matter ***what*** i do, the new Karmic installation will not boot. I've looked all through the GRUB 2 documentation, the documentation is all out of date! The commands in my help file are way different. I accidentally found how to do a command line boot, but 'the kernel's not loaded'. Everybody's so, so helpful, but none of your advice actually works. Now I see this script. It doesn't work either, and the thread in the forums on .sh files is all wrong too! Did I say that I'm new to Ubuntu/Linux? I keep hearing, "it's so simple"...WRONG! I don't know all 333,000 terminal commands yet (and I'm starting to think nobody else does either), but I was hoping to get Ubuntu on it's own partition so I could start learning. Eventually I think I'm going to have to uninstall, and get on with my life. I've wasted 4 days on this. I mean really, if I get incredibly detailed instructions on how to perform a standard computer file operation, and I cut and paste it verbatim, yet it doesn't work at all, what conclusion would any logical person draw? Do any of you ***really *** know what's going on? If so, can any of you actually help?

---

### Post by presence1960 on 2010-01-31
> **alkh3myst said:**
> Honestly, are you guys really trying to help anybody, or are you just trying to show off how much jargon and buzzwords you can use? This script is a .sh file; several other people on this thread also can't use it! I had a Wubi installation that I put on it's own partition using LVPM, which also changed the formatting from EXT 4 to EXT 3. No matter ***what*** i do, the new Karmic installation will not boot. I've looked all through the GRUB 2 documentation, the documentation is all out of date! The commands in my help file are way different. I accidentally found how to do a command line boot, but 'the kernel's not loaded'. Everybody's so, so helpful, but none of your advice actually works. Now I see this script. It doesn't work either, and the thread in the forums on .sh files is all wrong too! Did I say that I'm new to Ubuntu/Linux? I keep hearing, "it's so simple"...WRONG! I don't know all 333,000 terminal commands yet (and I'm starting to think nobody else does either), but I was hoping to get Ubuntu on it's own partition so I could start learning. Eventually I think I'm going to have to uninstall, and get on with my life. I've wasted 4 days on this. I mean really, if I get incredibly detailed instructions on how to perform a standard computer file operation, and I cut and paste it verbatim, yet it doesn't work at all, what conclusion would any logical person draw? Do any of you ***really *** know what's going on? If so, can any of you actually help?

OK fair enough. Now to be fair to us look at posts #9 & #25 of this thread. Then look thru the literally thousands of other threads in which this script was used successfully by people-some of them on their first day using linux. Obviously the script DOES work if done correctly. So let's see, did you do this:
1. download the boot info script? There is a link in my signature.
2. Once downloaded did you move the file to the desktop?
3. Now open a terminal and run the command?

It is not a difficult thing to do. Just follow the directions. I am sorry that you can't seem to figure it out.

---

### Post by raymondh on 2010-01-31
> **alkh3myst said:**
> Honestly, are you guys really trying to help anybody, or are you just trying to show off how much jargon and buzzwords you can use? This script is a .sh file; several other people on this thread also can't use it! I had a Wubi installation that I put on it's own partition using LVPM, which also changed the formatting from EXT 4 to EXT 3. No matter ***what*** i do, the new Karmic installation will not boot. I've looked all through the GRUB 2 documentation, the documentation is all out of date! The commands in my help file are way different. I accidentally found how to do a command line boot, but 'the kernel's not loaded'. Everybody's so, so helpful, but none of your advice actually works. Now I see this script. It doesn't work either, and the thread in the forums on .sh files is all wrong too! Did I say that I'm new to Ubuntu/Linux? I keep hearing, "it's so simple"...WRONG! I don't know all 333,000 terminal commands yet (and I'm starting to think nobody else does either), but I was hoping to get Ubuntu on it's own partition so I could start learning. Eventually I think I'm going to have to uninstall, and get on with my life. I've wasted 4 days on this. I mean really, if I get incredibly detailed instructions on how to perform a standard computer file operation, and I cut and paste it verbatim, yet it doesn't work at all, what conclusion would any logical person draw? Do any of you ***really *** know what's going on? If so, can any of you actually help?

Run the bootinfoscript and post the results.txt file.  It'll give the forum a chance to see what your HD contains....

---

### Post by oldfred on 2010-01-31
alkh3myst started his own thread which is better anyway.


[http://ubuntuforums.org/showthread.php?t=1394767](http://ubuntuforums.org/showthread.php?t=1394767)

---

