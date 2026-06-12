---
title: "GRUB2 and windows XP blank boot screen"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by sab_fossy on 2009-11-13
hi all

I am using Ubuntu 9.10 64-bit, and recently i tried to boot to windows XP. Grub2 has detected my Windoze partition properly. But when i hit enter to boot from windoze option, it comes up with a blank screen. 
I have no problem booting to Ubuntu though. The following steps were taken but didn't resolve the issue:

- re-installation of GRUB2
- boot sector recovery from windoze boot cd (fixmbr, fixboot, bootcfg)
- a full recovery of my windoze installation and re-installing grub

Any idea/help is highly appreciated.
Cheers
Sab

---

### Post by presence1960 on 2009-11-13
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sab_fossy on 2009-11-14
Here is the output:

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 129760372 
    on boot drive #-111 for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   413,850,464   413,848,417   7 HPFS/NTFS
/dev/sda2         413,850,465   625,137,344   211,286,880   5 Extended
/dev/sda5         413,850,528   619,145,099   205,294,572  83 Linux
/dev/sda6         619,145,163   625,137,344     5,992,182  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002d5dc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="84902BAF902BA6A0" TYPE="ntfs" 
/dev/sda5: UUID="c9db08d3-9ece-42a2-9bda-fbcab4fe69d6" TYPE="ext4" 
/dev/sda6: UUID="c882b537-f276-488f-8d77-bb387f1da336" TYPE="swap" 
/dev/sdb1: LABEL="" UUID="CCCE-8A8F" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/saber/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=saber)
/dev/sdb1 on /media/CCCE-8A8F type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr1 on /media/XP_HOME_SP2 type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="WinXP" 

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set c9db08d3-9ece-42a2-9bda-fbcab4fe69d6
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c9db08d3-9ece-42a2-9bda-fbcab4fe69d6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c9db08d3-9ece-42a2-9bda-fbcab4fe69d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c9db08d3-9ece-42a2-9bda-fbcab4fe69d6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c9db08d3-9ece-42a2-9bda-fbcab4fe69d6 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c9db08d3-9ece-42a2-9bda-fbcab4fe69d6
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=c9db08d3-9ece-42a2-9bda-fbcab4fe69d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c9db08d3-9ece-42a2-9bda-fbcab4fe69d6
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=c9db08d3-9ece-42a2-9bda-fbcab4fe69d6 ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows XP" {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 84902baf902ba6a0
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
# / was on /dev/sda5 during installation
UUID=c9db08d3-9ece-42a2-9bda-fbcab4fe69d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c882b537-f276-488f-8d77-bb387f1da336 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 211.8GB: boot/grub/grub.cfg
 211.8GB: boot/initrd.img-2.6.31-11-generic
 211.8GB: boot/initrd.img-2.6.31-14-generic
 211.8GB: boot/vmlinuz-2.6.31-11-generic
 211.8GB: boot/vmlinuz-2.6.31-14-generic
 211.8GB: initrd.img
 211.8GB: initrd.img.old
 211.8GB: vmlinuz
 211.8GB: vmlinuz.old
```

Cheers
Sab

---

### Post by meierfra. on 2009-11-14
> Grub1.97 is installed in the MBR of /dev/sda and looks at sector 129760372 
    on boot drive #-111 for core.img, but core.img can not be found at this 
    location.

This message is probably due to a bug in the boot info script.   I'm currently trying to fix the bug. Could you download and run the boot info script again and post the new RESULTS.txt?
Thanks.

---

### Post by jtmink1 on 2009-11-26
I to have this problem. I, however, am using windows 7. Has a fix been found for this yet?

---

### Post by presence1960 on 2009-11-26
> **jtmink1 said:**
> I to have this problem. I, however, am using windows 7. Has a fix been found for this yet?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by uruty on 2010-05-23
Well, same issue for me too. I can boot from the Grub2 menu on Lucid without problem but when I try to:
- boot from the auto discovered Windows menu -> get beeps and no escape
- boot from a self created custom entry (07_custom) -> blank screen with blicking cursor.
I get that problem since re-installing Ubuntu 10.04 on top of 9.10 and  upgrading Grub2 -> dual booting Ubuntu/XP installed on separate disks used to work fine.

Even though that thread is dated Nov2009 for its last update, I didn't find any solution to this issue anywhere else.

Interesting enough, if I change the boot sequence from Bios to start from the disk where Windows xp is to be found, XP boots-up fine.

Before it's asked, find hereafter the result of the boot info script...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 144980710 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 144981702 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065   144,697,454   144,681,390   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 300.1 Go, 300069052416 octets
255 têtes, 63 secteurs/piste, 36481 cylindres, total 586072368 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   418,188,014   418,187,952   7 HPFS/NTFS
/dev/sdb2         418,189,310   586,072,063   167,882,754   5 Extended
/dev/sdb5         418,189,312   427,954,175     9,764,864  82 Linux swap / Solaris
/dev/sdb6         427,956,224   586,072,063   158,115,840  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disque /dev/sdc: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4A5C538B5C5370A5                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A5C538B5C5370A5                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        40ac76fa-2c68-41f0-93f6-1bc07d2ecb47   swap                                     
/dev/sdb6        546570ff-e126-45ff-9d9d-26bfd46a613c   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4B65-B1BD                              vfat       D2_SATA                       
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/D2_SATA           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/4A5C538B5C5370A5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/4A5C538B5C5370A5_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect /usepmtimer 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
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
search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
set locale_dir=($root)/boot/grub/locale
set lang=fr
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

### BEGIN /etc/grub.d/07_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP Professionnel (on /dev/sda1) WD1600-position3" {
    insmod ntfs
    set root='(hd1,1)'
    chainloader +1
}
### END /etc/grub.d/07_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=546570ff-e126-45ff-9d9d-26bfd46a613c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
    echo    'Chargement de Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=546570ff-e126-45ff-9d9d-26bfd46a613c ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=546570ff-e126-45ff-9d9d-26bfd46a613c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
    echo    'Chargement de Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=546570ff-e126-45ff-9d9d-26bfd46a613c ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 546570ff-e126-45ff-9d9d-26bfd46a613c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4a5c538b5c5370a5
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professionnel (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 4a5c538b5c5370a5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 249.3GB: boot/grub/core.img
 249.5GB: boot/grub/grub.cfg
 249.3GB: boot/initrd.img-2.6.32-21-generic
 249.4GB: boot/initrd.img-2.6.32-22-generic
 249.3GB: boot/vmlinuz-2.6.32-21-generic
 219.6GB: boot/vmlinuz-2.6.32-22-generic
 249.4GB: initrd.img
 249.3GB: initrd.img.old
 219.6GB: vmlinuz
 249.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by darkod on 2010-05-23
This is your problem:
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sdb1[/COLOR] and 
                       looks at sector 144980710 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Use this fix on partition #1 on disk /dev/sdb:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

There seems to be small confusion about the names of your disks in the results file also. Were you recently swapping disks around?

---

### Post by Mechero on 2010-08-13
Hello,

I am experiencing the same problem, my results.txt file is:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 388339245.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,126   245,746,304   245,730,179   f W95 Ext d (LBA)
/dev/sda5              16,128   245,746,304   245,730,177   7 HPFS/NTFS
/dev/sda2    *    245,747,712   382,466,047   136,718,336  83 Linux
/dev/sda3         388,339,245   485,998,379    97,659,135   b W95 FAT32
/dev/sda4         382,466,048   388,337,663     5,871,616  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        5920a57a-008d-435b-b1ff-98622ab84884   ext4                                     
/dev/sda3        49CE-0545                              vfat                                     
/dev/sda4        9ca692df-50ba-4dc1-a269-1ffa02f88bb7   swap                                     
/dev/sda5        8070CE0B70CE083C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5920a57a-008d-435b-b1ff-98622ab84884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
    echo    'Cargando Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5920a57a-008d-435b-b1ff-98622ab84884 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5920a57a-008d-435b-b1ff-98622ab84884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
    echo    'Cargando Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5920a57a-008d-435b-b1ff-98622ab84884 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5920a57a-008d-435b-b1ff-98622ab84884
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
menuentry "Windows XP" {
          insmod ntfs
          set root=(hd0,5)
      chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=9ca692df-50ba-4dc1-a269-1ffa02f88bb7 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 130.2GB: boot/grub/core.img
 186.7GB: boot/grub/grub.cfg
 130.2GB: boot/initrd.img-2.6.32-21-generic
 130.4GB: boot/initrd.img-2.6.32-24-generic
 126.2GB: boot/vmlinuz-2.6.32-21-generic
 130.3GB: boot/vmlinuz-2.6.32-24-generic
 130.4GB: initrd.img
 130.2GB: initrd.img.old
 130.3GB: vmlinuz
 126.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  a4 81 00 00 c2 03 00 00  e5 a8 01 4b 0f aa 01 4b  |...........K...K|
00000010  44 b0 e6 4a 00 00 00 00  00 00 01 00 08 00 00 00  |D..J............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 8d 36 04 00  |.............6..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 5d 44 50 3e  00 00 00 00 00 00 00 00  |....]DP>........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 2c 56 33 5c  00 00 00 00 3c 33 24 91  |....,V3\....<3$.|
00000090  0f aa 01 4b 2c 56 33 5c  00 00 00 00 00 00 00 00  |...K,V3\........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  ed 81 00 00 40 26 00 00  e5 a8 01 4b 0f aa 01 4b  |....@&.....K...K|
00000110  58 b0 e6 4a 00 00 00 00  00 00 01 00 18 00 00 00  |X..J............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  03 00 00 00 8e 36 04 00  |.............6..|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 5e 44 50 3e  00 00 00 00 00 00 00 00  |....^DP>........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 28 4e e7 76  00 00 00 00 3c 33 24 91  |....(N.v....<3$.|
00000190  0f aa 01 4b 2c 56 33 5c  00 00 00 00 00 00 00 00  |...K,V3\........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 01  |................|
000001c0  01 01 07 fe ff ff 02 00  00 00 81 8b a5 0e 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by presence1960 on 2010-08-13
```
[COLOR="Red"]sda5:[/COLOR] __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda5 starts
at sector 63.
Operating System: Windows XP
[COLOR="Red"]Boot files/dirs: [/COLOR]

```
It looks as though you installed Ubuntu on a partition that had your windows boot files. Your XP is on a logical partition (sda5) and will never boot because of that. You need to use gparted to create a primary partition to install windows onto. Windows must be on a primary partition.

---

### Post by Mechero on 2010-08-14
Thank you!

Then, is there any possibility to recover my windows installation? Or maybe the only solution is to delete it and reinstall?

---

### Post by presence1960 on 2010-08-14
> **Mechero said:**
> Thank you!

Then, is there any possibility to recover my windows installation? Or maybe the only solution is to delete it and reinstall?

I would remove the logical & extended partitions and make the unallocated space from deleting them a **_primary NTFS partition_**. You can then install windows onto that NTFS partition.

To do this boot into ubuntu and use gparted. First delete sda5. Then delete sda1. You will then see unallocated space. Create a **_primary NTFS partition_** from the unallocated space. Install windows onto that **_primary NTFS partition_**.

You will then have to reinstall GRUB after windows is installed because windows will over write GRUB on the MBR with it's own bootloader.

---

### Post by phalantice on 2012-05-03
> **presence1960 said:**
>  Your XP is on a logical partition (sda5) and will never boot because of that.

Technically thats not correct,  I have been booting nt4- xp on logicals.  Though it is not recomended/supported.  not sure if grub2 cares though grub 1 booted them like a champ. used to have 14 os's booting when I supported the older ones. :lolflag:


sda4  is a clone of sdb2 just in a larger partition, neither one will boot unless i select booting from sdb which boots straight to xp there.  I have a uefi based bios and until i updated grub it worked fine.  I havent tried the amd64 version of grub2 yet but will probably do so in the next few days.  I just updated grub to add a vmware server capible kernel so things might not match up 100%

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on boot 
    drive #2 in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 89851545.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 128909312.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb7 starts at sector 80035893.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    78,125,055    78,123,008  83 Linux
/dev/sda2          78,125,056    89,843,711    11,718,656  82 Linux swap / Solaris
/dev/sda3          89,851,545   128,905,559    39,054,015   7 NTFS / exFAT / HPFS
/dev/sda4         128,909,310 2,930,270,207 2,801,360,898   5 Extended
/dev/sda5         128,909,312   180,109,311    51,200,000   b W95 FAT32
/dev/sda6         180,111,360 2,930,270,207 2,750,158,848  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    20,482,874    20,482,812   7 NTFS / exFAT / HPFS
/dev/sdb2          20,482,875    39,005,819    18,522,945  83 Linux
/dev/sdb3          39,005,820    40,965,749     1,959,930  82 Linux swap / Solaris
/dev/sdb4          40,965,811   976,768,064   935,802,254   5 Extended
/dev/sdb5          40,965,813    60,500,789    19,534,977  83 Linux
/dev/sdb6          60,500,853    80,035,829    19,534,977  83 Linux
/dev/sdb7          80,035,893   138,624,884    58,588,992   b W95 FAT32
/dev/sdb8         138,624,948   976,768,064   838,143,117  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   781,417,664   781,417,602   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ec928bd7-5a4f-4c5b-8229-7381a4897d97   ext4       
/dev/sda2        b7f4922a-f28e-48c3-acf9-1fa6d189925d   swap       
/dev/sda3        D8C0FF3EC0FF2204                       ntfs       XP32
/dev/sda5        FB6B-8D13                              vfat       GAMES1
/dev/sda6        45a44380-2cba-409b-8ae8-cb879f47e00d   ext4       Store
/dev/sdb1        D8C0FF3EC0FF2204                       ntfs       XP32
/dev/sdb2        953b4e83-988e-43cb-a76f-341892ae18b4   ext4       ubuntu10.4
/dev/sdb3        32b95253-97c0-4c39-b81e-b94bc6ec939e   swap       
/dev/sdb5        9279a9f6-42d5-4ff1-a16e-57fa24e79c75   ext3       LFS
/dev/sdb6        c8e8c0fc-fa26-4f75-993c-ffc03569a415   ext3       HomesOld1
/dev/sdb7        4920-7ED1                              vfat       STEAM
/dev/sdb8        3076bab1-4eb2-435f-88e4-a9c44fd3918d   ext3       Store1
/dev/sdc1        90441AAE441A9756                       ntfs       Back TMP

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Store             ext4       (rw,commit=0)
/dev/sdb1        /media/XP32_             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
insmod tga
if background_image /boot/grub/Windbuchencom.tga; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38.8-custom-13-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
    linux    /boot/vmlinuz-2.6.38.8-custom-13-pae root=UUID=ec928bd7-5a4f-4c5b-8229-7381a4897d97 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38.8-custom-13-pae
}
menuentry 'Ubuntu, with Linux 2.6.38.8-custom-13-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
    echo    'Loading Linux 2.6.38.8-custom-13-pae ...'
    linux    /boot/vmlinuz-2.6.38.8-custom-13-pae root=UUID=ec928bd7-5a4f-4c5b-8229-7381a4897d97 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38.8-custom-13-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
    linux    /boot/vmlinuz-2.6.38-13-generic-pae root=UUID=ec928bd7-5a4f-4c5b-8229-7381a4897d97 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
    echo    'Loading Linux 2.6.38-13-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-13-generic-pae root=UUID=ec928bd7-5a4f-4c5b-8229-7381a4897d97 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root ec928bd7-5a4f-4c5b-8229-7381a4897d97
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root D8C0FF3EC0FF2204
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root D8C0FF3EC0FF2204
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.37.2 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 953b4e83-988e-43cb-a76f-341892ae18b4
    linux /boot/vmlinuz-2.6.37.2 root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.37.2
}
menuentry "Ubuntu, with Linux 2.6.37.2 (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 953b4e83-988e-43cb-a76f-341892ae18b4
    linux /boot/vmlinuz-2.6.37.2 root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro single
    initrd /boot/initrd.img-2.6.37.2
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 953b4e83-988e-43cb-a76f-341892ae18b4
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 953b4e83-988e-43cb-a76f-341892ae18b4
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro single
    initrd /boot/initrd.img-2.6.32-29-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ec928bd7-5a4f-4c5b-8229-7381a4897d97 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=b7f4922a-f28e-48c3-acf9-1fa6d189925d none            swap    sw              0       0
solaris:/store/kendrick    /srv/nfs/solaris     nfs    rw    0    0
solaris:/store/server /srv/nfs/solsrv        nfs    rw    0    0
# set up extra drives
UUID=45a44380-2cba-409b-8ae8-cb879f47e00d /media/Store    ext4 defaults

--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.128131866 = 21.612417024   boot/grub/core.img                             1
  34.434005737 = 36.973232128   boot/grub/grub.cfg                             1
  18.965065002 = 20.363583488   boot/initrd.img-2.6.38-13-generic-pae          2
  28.786266327 = 30.909018112   boot/initrd.img-2.6.38.8-custom-13-pae         2
  11.575641632 = 12.429250560   boot/vmlinuz-2.6.38-13-generic-pae             2
  23.009197235 = 24.705937408   boot/vmlinuz-2.6.38.8-custom-13-pae            2

================================ sda3/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
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
menuentry 'Ubuntu, with Linux 2.6.37.2' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
    linux    /boot/vmlinuz-2.6.37.2 root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.37.2
}
menuentry 'Ubuntu, with Linux 2.6.37.2 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
    echo    'Loading Linux 2.6.37.2 ...'
    linux    /boot/vmlinuz-2.6.37.2 root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.37.2
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=953b4e83-988e-43cb-a76f-341892ae18b4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 953b4e83-988e-43cb-a76f-341892ae18b4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set B2603CEC603CB8C5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=953b4e83-988e-43cb-a76f-341892ae18b4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=32b95253-97c0-4c39-b81e-b94bc6ec939e none            swap    sw              0       0

# Home partition. 
UUID=81e25d00-e41e-4a8c-adb8-aa88f80209cf /mnt/HOMES      ext4      defaults       0    0

# Store partitions
UUID=04bae7dc-1c4c-4553-a98d-e0987e8d348e /media/Store      ext4    defaults        0     0
UUID=3076bab1-4eb2-435f-88e4-a9c44fd3918d /media/Store_      ext3    defaults        0     0
10.1.1.1:/mnt/store/data/manga /mnt/srver nfs soft,intr,rsize=8192,wsize=8192,rw
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.072583675 = 12.962838016   boot/grub/core.img                             1
  10.014489651 = 10.752976384   boot/grub/grub.cfg                             1
  11.485372066 = 12.332324352   boot/initrd.img-2.6.32-29-generic              5
  18.492867947 = 19.856565760   boot/initrd.img-2.6.37.2                       7
  16.432450771 = 17.644209664   boot/vmlinuz-2.6.32-29-generic                 4
  18.305734158 = 19.655632384   boot/vmlinuz-2.6.37.2                          1
  11.485372066 = 12.332324352   initrd.img                                     5
  16.432450771 = 17.644209664   vmlinuz                                        4

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

---

### Post by oldos2er on 2012-05-04
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

