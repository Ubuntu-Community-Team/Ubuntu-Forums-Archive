---
title: "Ubuntu upgrade renamed sdb to sdc"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2011-09-30
This machine had sda and sdb. After upgrade from Lucid to Maverick there is no more sdb, it has been renamed to sdc !  Grub shows sdc, so does gparted, BUT  fstab still shows sdb.  What happened?

Also Ubuntu now now asks me if I want “display or execute” text and .RTF files. How do I fix that?

Thank you.

---

### Post by oldos2er on 2011-09-30
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Can you follow the instructions at the above link, and post your RESULTS.txt file here? It should help explain what's going on with your system.

---

### Post by Rebelli0us on 2011-10-03
> **oldos2er said:**
> [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Can you follow the instructions at the above link, and post your RESULTS.txt file here? It should help explain what's going on with your system.

Thank you, here it is. 

[http://ubuntuforums.org/attachment.php?attachmentid=203488&stc=1&d=1317664129]("http://ubuntuforums.org/attachment.php?attachmentid=203488&stc=1&d=1317664129")

It confirms my OP in way too much detail, but doesn't explain why the upgrade deleted sdb and created sdc in its place.

---

### Post by Rubi1200 on 2011-10-03
For those concerned:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /bootsect.lnx looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /bootsect.lnx looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   270,341,819   270,341,757   7 NTFS / exFAT / HPFS
/dev/sdc2         270,342,142   312,580,095    42,237,954   5 Extended
/dev/sdc5         270,342,144   310,732,799    40,390,656  83 Linux
/dev/sdc6         310,734,848   312,580,095     1,845,248  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        52C0E0CFC0E0BA7D                       ntfs       1_1
/dev/sdc1        3276C14B76C11111                       ntfs       2_1
/dev/sdc5        b0ceb045-659b-421c-962d-4642128bd5c7   ext4       
/dev/sdc6        f855a9f0-ba34-4937-ae8f-f7d8a75ff23c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/1_1               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/2_1               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional on 1_1 Hitachi 149 GB" /fastdetect /usepmtimer
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows 2000 Recovery Console" /cmdcons
multi(0)disk(0)rdisk(1)partition(1)\WINNT="Microsoft Windows 2000 Professional on 2_1 Toshiba 128 GB" /fastdetect /usepmtimer
--------------------------------------------------------------------------------

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional on 2_1 Toshiba 128 GB" /fastdetect /usepmtimer
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows 2000 Recovery Console" /cmdcons
C:\bootsect.lnx="Ubuntu Linux"

--------------------------------------------------------------------------------

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=b0ceb045-659b-421c-962d-4642128bd5c7 ro  splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=b0ceb045-659b-421c-962d-4642128bd5c7 ro single  splash quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=b0ceb045-659b-421c-962d-4642128bd5c7 ro  splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=b0ceb045-659b-421c-962d-4642128bd5c7 ro single  splash quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b0ceb045-659b-421c-962d-4642128bd5c7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 52C0E0CFC0E0BA7D
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows 2000 Professional on 2_1 Toshiba 128 GB (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 3276C14B76C11111
    drivemap -s (hd0) ${root}
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb5 :
UUID=b0ceb045-659b-421c-962d-4642128bd5c7    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=52C0E0CFC0E0BA7D    /media/1_1    ntfs-3g    defaults,uid=1000,umask=077,locale=en_US.utf8    0    0
#Entry for /dev/sdb1 :
UUID=3276C14B76C11111    /media/2_1    ntfs-3g    defaults,uid=1000,umask=077,locale=en_US.utf8    0    0
#Entry for /dev/sdb6 :
UUID=f855a9f0-ba34-4937-ae8f-f7d8a75ff23c    none    swap    sw    0    0


--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 139.045097351 = 149.298536448  boot/grub/core.img                             1
 131.130783081 = 140.800606208  boot/grub/grub.cfg                             1
 132.457782745 = 142.225461248  boot/initrd.img-2.6.32-34-generic              1
 132.786659241 = 142.578589696  boot/initrd.img-2.6.35-30-generic              2
 139.301593781 = 149.573947392  boot/vmlinuz-2.6.32-34-generic                 1
 139.309185028 = 149.582098432  boot/vmlinuz-2.6.35-30-generic                 1
 132.786659241 = 142.578589696  initrd.img                                     2
 132.457782745 = 142.225461248  initrd.img.old                                 1
 139.309185028 = 149.582098432  vmlinuz                                        1
 139.301593781 = 149.573947392  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 



```

---

### Post by presence1960 on 2011-10-03
Did you have a flash disk or external drive attached during the upgrade? The reason fstab shows sdb is that is what it was originally. You can still mount the disk because Ubuntu uses UUID rather than sda, sdb, etc in fstab. I stay away from upgrades as I have seen way too many things can happen during an upgrade that can make it not worth it because of all the time and effort consumed fixing problems created during an upgrade. On the other hand lots do upgrades with no problems. My choice is why chance it.

I know this is not going to help now, but for future reference it is much better to do a clean install. There is a way to create a file so when the clean install is finished all your software from repositories will be reinstalled. If you back up your /home you can then move the folders that belong to software to new /home as these have the settings for your programs. I will link you with a page that will show you how to do this. Once I found this I have never done an upgrade but rather a clean install to the next version of ubuntu. And it takes less time than an upgrade. here is the link:

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by oldfred on 2011-10-03
Is your sdc an external drive or did you mount an external drive and unmount it at some point. Ubuntu's fstab shows  sdb, but uses UUIDs so it still works.

But you have installed grub to the Windows NTFS partitions in sda1 & (Now) sdc1. NTFS partitions keep a backup boot sector which you can easily recover if the backup is still good.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Rebelli0us on 2011-10-03
> **presence1960 said:**
> Did you have a flash disk or external drive attached during the upgrade? The reason fstab shows sdb is that is what it was originally. You can still mount the disk because Ubuntu uses UUID rather than sda, sdb, etc in fstab. I stay away from upgrades as I have seen way too many things can happen during an upgrade that can make it not worth it because of all the time and effort consumed fixing problems created during an upgrade. On the other hand lots do upgrades with no problems. My choice is why chance it.

I know this is not going to help now, but for future reference it is much better to do a clean install. There is a way to create a file so when the clean install is finished all your software from repositories will be reinstalled. If you back up your /home you can then move the folders that belong to software to new /home as these have the settings for your programs. I will link you with a page that will show you how to do this. Once I found this I have never done an upgrade but rather a clean install to the next version of ubuntu. And it takes less time than an upgrade. here is the link:

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Yes there is a USB flash drive, but I don’t see why that should cause renaming of the Linux disk. I still think in terms of Windows, and Windows would never change the drive letter of its boot disk, so I was worried about a million broken links to sdb/...

And I agree, my Ubuntu upgrades usually self-destruct. This one appeared hung during the upgrade, most people would have reset the machine. There was a message box asking for something but the window was in the background and would not come to the foreground so you can read it. The upgrade took hours (while I did other things), and by the time I noticed the hung message box all the windows had lost their title bar and the OS was non-responsive. I gave the message box focus (by tabbing, or something) and blindly pressed Enter, and it proceeded form there. 

I will probably delete the partition and do a clean install, but I thought I’d try the upgrade, Linux has been making giant leaps recently.

---

### Post by Rebelli0us on 2011-10-03
> **oldfred said:**
> Is your sdc an external drive or did you mount an external drive and unmount it at some point. Ubuntu's fstab shows  sdb, but uses UUIDs so it still works.

But you have installed grub to the Windows NTFS partitions in sda1 & (Now) sdc1. NTFS partitions keep a backup boot sector which you can easily recover if the backup is still good.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Thank you, sdc is an internal drive, so is sda, both plugged on SATA.

I see what you mean. If this diagnostic script thinks that Grub is on sda then it’s wrong. On the original installation I made sure grub went on sdb, so sda was untouched and Windows booted on it’s own **and it still does!** So I don’t understand the part about grub on sda.

If the upgrader messed with the MBR on the the 1st disk, then that’s bad. I don’t see why upgrading the OS should affect the existing boot setup. This is definitely my last upgrade, it takes 15 mins to do a clean install and many hours to do an upgrade that usually self-destructs. Also the devs stop the install and wait for replies before proceeding... really who’s gonna sit for hours and watch this? Upgades should run unattended.

---

