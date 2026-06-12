---
title: "Grub2 - MBR code: /dev/sda vs. /dev/sdb are different, why?"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by Hakunka-Matata on 2011-08-25
Machine has 3 HDD - sda, sdb, sdc.  Everything works, no problems. 


[LIST]
[*]All three drives have Grub2 (v1.99) installed to their MBRs (See RESULTS.txt)
[*] Made backup of MBR code of all three drives for testing & recovery if necessary:  used **sudo dd if=/dev/sda, b, c of=MBRsda, b, c.bin bs=512 count=1**, to generate the backup files.
[*]when I compare **fcomp -BINary MBRsda.bin MBRsdb.bin & ****MBRsdc.bin**I get a bunch of differences, why?  Because[COLOR=Red] [COLOR=Black]/dev/sda[/COLOR] [/COLOR][COLOR=Red]core.img is at this location and looks for (,msdos8)/boot/grub on this drive.[/COLOR]  And sdb and sdc's corr.img files are in different locations on those respective drives?
[*]If this is true, then must I keep a separate backup MBR.bin file for each individual drive?
[*]I see all the time where the MBR can be repaired with this or that tool?
[*]Is there a generic portion of the MBR code that I can copy and use to restore corrupted MBRs?
[*]staring before or after byte #446 or something along those lines, (that's from memory, a guess)
[/LIST]
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. [COLOR=Red]core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.[/COLOR]
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Puppy Linux Linux 2.6.30.5 
                       [i686 arch]
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  MEPIS Linux 8.5
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb2 
                       and looks at sector 124334592 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos2)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  FAT16
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    40,965,749    40,965,687  83 Linux
/dev/sda2          40,966,144   122,879,999    81,913,856  83 Linux
/dev/sda3         122,881,185   204,796,619    81,915,435  83 Linux
/dev/sda4         204,796,744   488,396,799   283,600,056   5 Extended
/dev/sda5         204,796,746   245,762,369    40,965,624  83 Linux
/dev/sda6         245,762,433   286,728,119    40,965,687  83 Linux
/dev/sda7         484,096,000   488,396,799     4,300,800  82 Linux swap / Solaris
/dev/sda8         286,730,240   327,690,239    40,960,000  83 Linux
/dev/sda9         327,692,288   368,652,287    40,960,000  83 Linux
/dev/sda10        368,654,336   484,093,951   115,439,616  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    53,229,567    53,229,505   7 NTFS / exFAT / HPFS
/dev/sdb2          77,819,904   154,255,359    76,435,456  83 Linux
/dev/sdb3         154,255,360   156,301,311     2,045,952  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sdc2         102,398,310   201,680,009    99,281,700  83 Linux
/dev/sdc3         304,078,320   488,392,064   184,313,745   5 Extended
/dev/sdc5         304,078,383   345,044,069    40,965,687  83 Linux
/dev/sdc6         345,047,040   353,433,599     8,386,560  82 Linux swap / Solaris
/dev/sdc4         201,680,010   304,078,319   102,398,310  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01e2ae96-7804-4da9-a8b6-52b9f62a48af   ext4       1004
/dev/sda10       a9f5d94a-6571-4016-a267-1b425da6382f   ext4       sda10_home_data
/dev/sda2        beba3cf3-e1e1-424c-bb79-92fe1a447734   ext4       sda2
/dev/sda3        4556b6fd-c494-4200-9d85-3e4c96ea9609   ext4       Puppy 4.3.1
/dev/sda5        0c40042e-9f49-42b9-b724-974bda9c3264   ext3       sda5-Mepis
/dev/sda6        7337c5df-44c6-4ee5-b72d-6fd187db55f7   ext4       sda6
/dev/sda7        339ad7c0-32c0-489d-a013-3c36d2181d73   swap       
/dev/sda8        497a14e5-d299-43c7-ae42-3e835a4fce5a   ext4       Natty-32-LiveCD
/dev/sda9        188f97ee-c01a-4f9d-a3e7-5603a3401ed8   ext4       Xubuntu
/dev/sdb1        C0B4A5D4B4A5CD6A                       ntfs       
/dev/sdb2        a62cccf7-ad57-46e2-954a-a487373ecf28   ext4       
/dev/sdb3        c03410b4-67c6-48ca-8132-0dd5f8ec4de9   swap       
/dev/sdc1        5A14174B14172A11                       ntfs       WinXP
/dev/sdc2        0fb28b1f-044f-43ff-a1b5-1b36cd43feeb   ext4       1010-root-Sephom
/dev/sdc4        b951593b-2ef3-4f1e-971e-6b1e4db61aa6   ext4       sdb4_home_data
/dev/sdc5        a317a865-87d3-4561-b339-3ad0497707ba   ext4       natty-64
/dev/sdc6        aea01fb0-bc28-4d0c-ae7c-5005af183509   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /home                    ext4       (rw,nosuid,nodev,commit=0)
/dev/sda6        /media/sda6              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
sudo nano /boot/grub/menu.lst

that's how this file was created, just testing
--------------------------------------------------------------------------------

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5a14174b14172a11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-23-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro quiet splash
    initrd /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-23-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single
    initrd /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz-2.6.32-1-mepis64-smp root=/dev/sdc5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sdc8)" {
    insmod ext2
    set root='(hd2,8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sdc8)" {
    insmod ext2
    set root='(hd2,8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sdc8)" {
    insmod ext2
    set root='(hd2,8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sdc8)" {
    insmod ext2
    set root='(hd2,8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-5-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                 <mount point>   <type>  <options>           <dump>  <pass>
proc                            /proc           proc    nodev,noexec,nosuid     0       0
# / was on /dev/sdc1 during installation
UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af     /               ext4    errors=remount-ro     0       1
# / was on /dev/sdc2 during installation
UUID=beba3cf3-e1e1-424c-bb79-92fe1a447734     /media/sdc2     ext4    errors=remount-ro     0       1
# / was on /dev/sdc3 Puppy 4.3.1 during installation
UUID=4556b6fd-c494-4200-9d85-3e4c96ea9609     /media/sdc3_Puppy ext4    errors=remount-ro     0       1
# swap was on /dev/sdc7 MEPIS during installation
UUID=339ad7c0-32c0-489d-a013-3c36d2181d73     none            swap    sw                     0       0
# swap was on /dev/sdb5 80GB drive
UUID=b83e0608-fd1f-4cc3-be87-622a0590da95     none            swap    sw                     0       0


--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.298884869 = 17.500794368   boot/grub/core.img                             1
  11.430125713 = 12.273004032   boot/grub/grub.cfg                             2
  16.222136974 = 17.418386944   boot/grub/menu.lst                             1
  16.292647839 = 17.494097408   boot/initrd.img-2.6.32-28-generic              1
  16.285220623 = 17.486122496   boot/initrd.img-2.6.32-29-generic              1
   8.116923809 = 8.715480576    boot/initrd.img-2.6.32-30-generic              2
   1.155974865 = 1.241218560    boot/initrd.img-2.6.35-22-generic              2
   3.312530041 = 3.556802048    boot/initrd.img-2.6.35-25-generic              2
  16.217475414 = 17.413381632   boot/vmlinuz-2.6.32-28-generic                 1
  16.378795147 = 17.586597376   boot/vmlinuz-2.6.32-29-generic                 1
  16.445300579 = 17.658007040   boot/vmlinuz-2.6.32-30-generic                 1
  16.393874645 = 17.602788864   boot/vmlinuz-2.6.35-22-generic                 1
  16.441531658 = 17.653960192   boot/vmlinuz-2.6.35-25-generic                 1
   8.116923809 = 8.715480576    initrd.img                                     2
   3.312530041 = 3.556802048    initrd.img.old                                 2
  16.445300579 = 17.658007040   vmlinuz                                        1
  16.441531658 = 17.653960192   vmlinuz.old                                    1

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sdb3     /            ext4     defaults               0 1
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  58.900890827 = 63.244349952   boot/vmlinuz                                   1

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# Pluggable devices are handled by uDev, they are not in fstab
/dev/sda6 / ext3 defaults,noatime 1 1
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/sdb1 /mnt/sdb1 ntfs-3g noauto,users,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/sdb2 /mnt/sdb2 ext4 noauto,users,exec,relatime 0 0
/dev/sdb4 /mnt/sdb4 ext4 noauto,users,exec,relatime 0 0
/dev/sdb5 /mnt/sdb5 ext4 noauto,users,exec,relatime 0 0
/dev/sdb6 swap swap sw,pri=1 0 0
/dev/sda1 /mnt/sda1 ext4 noauto,users,exec,relatime 0 0
/dev/sda2 /mnt/sda2 ext4 noauto,users,exec,relatime 0 0
/dev/sda3 /mnt/sda3 ext4 noauto,users,exec,relatime 0 0
/dev/sda5 /mnt/sda5 ext3 noauto,users,exec,relatime 0 0
/dev/sda7 swap swap sw,pri=1 0 0
/dev/sda8 /mnt/sda8 ext4 noauto,users,exec,relatime 0 0
/dev/sda9 /mnt/sda9 ext4 noauto,users,exec,relatime 0 0
/dev/sda10 /mnt/sda10 ext4 noauto,users,exec,relatime 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.164757729 = 111.846056960  boot/grub/stage2                               2
 104.188611031 = 111.871669248  boot/initrd.img                                4
 104.188611031 = 111.871669248  boot/initrd.img-2.6.32-1-mepis64-smp           4
 104.178174019 = 111.860462592  boot/vmlinuz                                   2
 104.178174019 = 111.860462592  boot/vmlinuz-2.6.32-1-mepis64-smp              2

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=12
fi
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    echo    'Loading Linux 2.6.38-5-generic ...'
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-5-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz-2.6.32-1-mepis64-smp root=/dev/sda5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root C0B4A5D4B4A5CD6A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 5A14174B14172A11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-9-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-9-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-9-generic
}
menuentry "Ubuntu, with Linux 2.6.38-9-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-9-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single
    initrd /boot/initrd.img-2.6.38-9-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single
    initrd /boot/initrd.img-2.6.38-5-generic
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                 <mount point>    <type>  <options>       <dump>  <pass>
proc                            /proc            proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a     /                ext4    errors=remount-ro     0       1
# swap was on /dev/sdb6 during installation
UUID=aea01fb0-bc28-4d0c-ae7c-5005af183509     none             swap    sw                  0       0
# swap was on /dev/sda7 during installation
UUID=339ad7c0-32c0-489d-a013-3c36d2181d73     none             swap    sw                   0       0
# mount the /homeData partition /dev/sda10
UUID=a9f5d94a-6571-4016-a267-1b425da6382f    /home     ext4     nodev,nosuid            0       2
# mount the /sdb4_home_data partition /dev/sdc4
#UUID=b951593b-2ef3-4f1e-971e-6b1e4db61aa6    /home/media     ext4     nodev,nosuid            0       2
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 146.857143402 = 157.686657024  boot/grub/core.img                             1
 149.070865631 = 160.063623168  boot/grub/grub.cfg                             1
 138.767536163 = 149.000507392  boot/initrd.img-2.6.38-10-generic              2
 149.603004456 = 160.635002880  boot/initrd.img-2.6.38-11-generic              2
 153.104259491 = 164.394446848  boot/initrd.img-2.6.38-5-generic               2
 145.900367737 = 156.659326976  boot/initrd.img-2.6.38-7-generic               2
 146.801376343 = 157.626777600  boot/initrd.img-2.6.38-8-generic               2
 137.555973053 = 147.699601408  boot/vmlinuz-2.6.38-10-generic                 2
 147.798160553 = 158.697066496  boot/vmlinuz-2.6.38-11-generic                 2
 147.113338470 = 157.961744384  boot/vmlinuz-2.6.38-5-generic                  1
 147.391906738 = 158.260854784  boot/vmlinuz-2.6.38-7-generic                  1
 148.590820312 = 159.548178432  boot/vmlinuz-2.6.38-8-generic                  2
 149.603004456 = 160.635002880  initrd.img                                     2
 138.767536163 = 149.000507392  initrd.img.old                                 2
 147.798160553 = 158.697066496  vmlinuz                                        2
 137.555973053 = 147.699601408  vmlinuz.old                                    2

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C0B4A5D4B4A5CD6A
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
UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=c03410b4-67c6-48ca-8132-0dd5f8ec4de9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  59.331874847 = 63.707115520   boot/grub/core.img                             1
  61.313293457 = 65.834647552   boot/grub/grub.cfg                             1
  38.486583710 = 41.324654592   boot/initrd.img-2.6.38-10-generic              2
  37.861545563 = 40.653524992   boot/initrd.img-2.6.38-8-generic               2
  37.674137115 = 40.452296704   boot/vmlinuz-2.6.38-10-generic                 1
  59.331546783 = 63.706763264   boot/vmlinuz-2.6.38-8-generic                  1
  38.486583710 = 41.324654592   initrd.img                                     2
  37.861545563 = 40.653524992   initrd.img.old                                 2
  37.674137115 = 40.452296704   vmlinuz                                        1
  59.331546783 = 63.706763264   vmlinuz.old                                    1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5a14174b14172a11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 63273959-3b6f-41b2-ba5e-b2acf87f093d
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=63273959-3b6f-41b2-ba5e-b2acf87f093d ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 63273959-3b6f-41b2-ba5e-b2acf87f093d
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=63273959-3b6f-41b2-ba5e-b2acf87f093d ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 63273959-3b6f-41b2-ba5e-b2acf87f093d
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=63273959-3b6f-41b2-ba5e-b2acf87f093d ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 63273959-3b6f-41b2-ba5e-b2acf87f093d
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=63273959-3b6f-41b2-ba5e-b2acf87f093d ro single
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 604baae7-b8c3-4354-b042-9c8a6cb909dd
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=604baae7-b8c3-4354-b042-9c8a6cb909dd ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "unknown Linux distribution (on /dev/sdc3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sdc3
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sdc5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz-2.6.32-1-mepis64-smp root=/dev/sdc5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sdc8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sdc8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sdc8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sdc8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos8)'
    search --no-floppy --fs-uuid --set 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-5-generic
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

=============================== sdc2/etc/fstab: ================================

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
UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=b83e0608-fd1f-4cc3-be87-622a0590da95 none            swap    sw              0       0
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=a9f5d94a-6571-4016-a267-1b425da6382f   /home    ext4          nodev,nosuid       0       2 
# FAT32 lba,BOOT /dev/sda8 Mint extracted iso install disc
# UUID=BBCB-2466                 /FAT32sda7    vfat    umask=0000,utf8       0       0
# swap was on /dev/sdc7 during installation
UUID=339ad7c0-32c0-489d-a013-3c36d2181d73 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  80.975172997 = 86.946429952   boot/grub/core.img                             1
  61.438715935 = 65.969318912   boot/grub/grub.cfg                             1
  70.159865379 = 75.333581824   boot/initrd.img-2.6.35-22-generic              2
  51.069506645 = 54.835465216   boot/initrd.img-2.6.35-23-generic              2
  70.170973778 = 75.345509376   boot/initrd.img-2.6.35-24-generic              2
  50.788256645 = 54.533475328   boot/initrd.img-2.6.35-25-generic              2
  51.866763115 = 55.691512832   boot/initrd.img-2.6.35-27-generic              2
  51.780444145 = 55.598828544   boot/initrd.img-2.6.35-28-generic              2
  81.104754448 = 87.085566976   boot/vmlinuz-2.6.35-22-generic                 1
  81.091170311 = 87.070981120   boot/vmlinuz-2.6.35-23-generic                 1
  81.158362389 = 87.143128064   boot/vmlinuz-2.6.35-24-generic                 1
  81.162364006 = 87.147424768   boot/vmlinuz-2.6.35-25-generic                 1
  81.206320763 = 87.194622976   boot/vmlinuz-2.6.35-27-generic                 1
  81.210322380 = 87.198919680   boot/vmlinuz-2.6.35-28-generic                 1
  51.780444145 = 55.598828544   initrd.img                                     2
  51.866763115 = 55.691512832   initrd.img.old                                 2
  81.210322380 = 87.198919680   vmlinuz                                        1
  81.206320763 = 87.194622976   vmlinuz.old                                    1

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    echo    'Loading Linux 2.6.38-9-generic ...'
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    echo    'Loading Linux 2.6.38-5-generic ...'
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=a317a865-87d3-4561-b339-3ad0497707ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-5-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root a317a865-87d3-4561-b339-3ad0497707ba
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01e2ae96-7804-4da9-a8b6-52b9f62a48af
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=01e2ae96-7804-4da9-a8b6-52b9f62a48af ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "unknown Linux distribution (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 4556b6fd-c494-4200-9d85-3e4c96ea9609
    linux /boot/vmlinuz root=/dev/sda3
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "MEPIS 8.5 (upgradable from Debian lenny) (8.5) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0c40042e-9f49-42b9-b724-974bda9c3264
    linux /boot/vmlinuz-2.6.32-1-mepis64-smp root=/dev/sda5
    initrd /boot/initrd.img-2.6.32-1-mepis64-smp
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 497a14e5-d299-43c7-ae42-3e835a4fce5a
    linux /boot/vmlinuz-2.6.38-5-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro single
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root C0B4A5D4B4A5CD6A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root a62cccf7-ad57-46e2-954a-a487373ecf28
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a62cccf7-ad57-46e2-954a-a487373ecf28 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 5A14174B14172A11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 0fb28b1f-044f-43ff-a1b5-1b36cd43feeb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=0fb28b1f-044f-43ff-a1b5-1b36cd43feeb ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a317a865-87d3-4561-b339-3ad0497707ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b83e0608-fd1f-4cc3-be87-622a0590da95 none            swap    sw              0       0
# swap was on /dev/sdc7 during installation
UUID=339ad7c0-32c0-489d-a013-3c36d2181d73 none            swap    sw              0       0
# (identifier)  (location, eg sda10 or sdb4)   (format, eg ext3 or ext4)      (some settings) 
UUID=a9f5d94a-6571-4016-a267-1b425da6382f   /home    ext4         nodev,nosuid       0       2 
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 147.127700329 = 157.977165312  boot/grub/core.img                             1
 149.390052319 = 160.406347264  boot/grub/grub.cfg                             1
 162.625335217 = 174.617624064  boot/initrd.img-2.6.38-10-generic              1
 148.515964031 = 159.467802112  boot/initrd.img-2.6.38-11-generic              2
 145.890922070 = 156.649184768  boot/initrd.img-2.6.38-5-generic               1
 151.304996014 = 162.462502400  boot/initrd.img-2.6.38-7-generic               1
 153.406547070 = 164.719025664  boot/initrd.img-2.6.38-8-generic               1
 153.504722118 = 164.824440320  boot/initrd.img-2.6.38-9-generic               2
 145.910247326 = 156.669935104  boot/vmlinuz-2.6.38-10-generic                 1
 147.824309826 = 158.725144064  boot/vmlinuz-2.6.38-11-generic                 2
 147.187846661 = 158.041746944  boot/vmlinuz-2.6.38-5-generic                  1
 146.351645947 = 157.143883264  boot/vmlinuz-2.6.38-7-generic                  2
 152.148524761 = 163.368234496  boot/vmlinuz-2.6.38-8-generic                  1
 152.246184826 = 163.473096192  boot/vmlinuz-2.6.38-9-generic                  1
 148.515964031 = 159.467802112  initrd.img                                     2
 162.625335217 = 174.617624064  initrd.img.old                                 1
 147.824309826 = 158.725144064  vmlinuz                                        2
 145.910247326 = 156.669935104  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error


```

---

### Post by soldersplash on 2011-08-25
The simple answer would seem to be keeping an MBR backup per drive.

The longer answer is could be:-
According to [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record) the MBR includes the 'Table of Primary Partitions', which given the output you posted would be different per drive. The code prior to a440 may well be identical.Try dd'ing just the first 440 bytes?

All the best,
Daniel.

---

### Post by oldfred on 2011-08-25
You have three different operating systems and each MBR is set to boot the system installed on that drive. (Which I suggest so if one drive fails your BIOS can be reset to boot another drive.

You need to be careful restoring the full 512 as that includes the partition table. If you change partition table then the backup will damage your system.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.

I just recommend that you use a liveCD to reinstall grub2's boot loader to the MBR and not use dd

---

### Post by Hakunka-Matata on 2011-08-25
@soldersplach:  Thanks, that makes sense, and comparing offset 0 to 440 produced no differences between the three MBRs.
@oldfred;  Thank you oldfred:  I'm doing this not to fix something, rather as an experiment for learning purposes.  Does reinstalling Grub2 from liveCD write the same 0 to 440 bytes I have now in the MBRs, then build the rest depending on what it finds installed on the drive?
thanks ahead of time

---

### Post by oldfred on 2011-08-25
I do not know details, but thought grub would have slight differences as you are booting different partitions in each drive. Windows uses a boot flag in the partition table to know where to jump to, grub has to know partition and uses the extra code in core.img to find grub.cfg and whatever else it needs to load all of grub.

---

### Post by Hakunka-Matata on 2011-08-26
> **oldfred said:**
> I do not know details, but thought grub would have slight differences as you are booting different partitions in each drive. Windows uses a boot flag in the partition table to know where to jump to, grub has to know partition and uses the extra code in core.img to find grub.cfg and whatever else it needs to load all of grub.

I am only comparing the first 440 bytes of MBR.  
Would not the Windows boot flag, and the partition information by in offset 440 to 512?
Anyway, I feel good to have learned this much, thanks.

---

### Post by oldfred on 2011-08-26
I find that most interesting. When I did some compares of the MBR, I never had the same version installed.

Since boot script does see the difference it must be in core.img where it finds which partition to boot from?

---

