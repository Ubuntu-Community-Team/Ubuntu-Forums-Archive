---
title: "Can't boot into Ubuntu 10.04 after Windows XP install"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by xp_even on 2010-10-01
I have two hard disks: 160GB and 1TB. I had Ubuntu 10.04 installed on the 1TB drive (sdb). Then I installed Windows Xp on the 160GB drive (sda) following which I could no longer boot into Ubuntu (as Windows XP boots straight away). I have already tried to repair GRUB2 using the Live CD using the commands:

# fdisk -l  (shows sdb5 to be the 'Linux' partition)

# mkdir /media/sdb5
# mount /dev/sdb5 /media/sdb5
# grub-install --root-directory=/media/sdb5 /dev/sdb

The above procedure shows success but I still don't get the GRUB menu. Please help.

---

### Post by Rubi1200 on 2010-10-01
From the LiveCD, post the results of the boot-script linked at the bottom of my post please.

Thanks.

---

### Post by xp_even on 2010-10-01
Thanks for the quick response, Rubi1200. Please note that I no longer have Windows 7 installed (I deleted that partition) Here's the RESULTS.TXT:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
127 heads, 63 sectors/track, 39067 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   157,288,447   157,286,400   7 HPFS/NTFS
/dev/sda2         157,288,448   312,575,999   155,287,552   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,126    41,945,087    41,928,962   f W95 Ext d (LBA)
/dev/sdb5              18,432    32,251,903    32,233,472  83 Linux
/dev/sdb6          37,408,768    41,945,087     4,536,320  82 Linux swap / Solaris
/dev/sdb2    *     41,945,088   985,663,487   943,718,400   7 HPFS/NTFS
/dev/sdb3         985,663,488 1,953,523,711   967,860,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4E6C66686C664B33                       ntfs       New Volume                    
/dev/sda2        44DC13F1DC13DC4C                       ntfs       Windows XP                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        71CEBB3E22DCAE27                       ntfs       Old                           
/dev/sdb3        200AEC8917F07253                       ntfs       New                           
/dev/sdb5        a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef   ext4                                     
/dev/sdb6        0644d08d-f65e-453c-93bc-9fa02f624b57   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINXP 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINXP="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 71cebb3e22dcae27
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=0644d08d-f65e-453c-93bc-9fa02f624b57 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   5.5GB: boot/grub/grub.cfg
   5.3GB: boot/initrd.img-2.6.32-21-generic
   5.5GB: boot/initrd.img-2.6.32-24-generic
   5.6GB: boot/initrd.img-2.6.32-25-generic
   5.2GB: boot/vmlinuz-2.6.32-21-generic
   5.4GB: boot/vmlinuz-2.6.32-24-generic
   5.5GB: boot/vmlinuz-2.6.32-25-generic
   5.6GB: initrd.img
   5.5GB: initrd.img.old
   5.5GB: vmlinuz
   5.4GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2010-10-01
Thanks for posting the results. Did you delete the Windows 7 partition before or after running the script?

If before, please run it again so we can see the current situation.

Thanks.

---

### Post by xp_even on 2010-10-01
I deleted Windows 7 partition before running the script.

---

### Post by xp_even on 2010-10-01
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
127 heads, 63 sectors/track, 39067 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   157,288,447   157,286,400   7 HPFS/NTFS
/dev/sda2         157,288,448   312,575,999   155,287,552   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,126    41,945,087    41,928,962   f W95 Ext d (LBA)
/dev/sdb5              18,432    32,251,903    32,233,472  83 Linux
/dev/sdb6          37,408,768    41,945,087     4,536,320  82 Linux swap / Solaris
/dev/sdb2    *     41,945,088   985,663,487   943,718,400   7 HPFS/NTFS
/dev/sdb3         985,663,488 1,953,523,711   967,860,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4E6C66686C664B33                       ntfs       New Volume                    
/dev/sda2        44DC13F1DC13DC4C                       ntfs       Windows XP                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        71CEBB3E22DCAE27                       ntfs       Old                           
/dev/sdb3        200AEC8917F07253                       ntfs       New                           
/dev/sdb5        a0a7e4a7-fdf7-4e09-9a12-a10fabd401ef   ext4                                     
/dev/sdb6        0644d08d-f65e-453c-93bc-9fa02f624b57   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /media/New               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/sdb5              ext4       (rw)
/dev/sdb5        /mnt                     ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINXP 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINXP="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sdb5: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
```

---

### Post by Mark Phelps on 2010-10-02
That doesn't make sense.  Win7 is still THERE, in sda2 and in sdb.

---

### Post by Ed_Ziffel on 2010-10-02
Install XP first and then install Ubuntu. The trick is to install XP first then Ubuntu will pick up the Xp isntall.  Choose the let me pick option for the disk assignment when installing 10.04.  Also start with an unformatted disk for 10.04.

---

### Post by Ed_Ziffel on 2010-10-02
Oh yeah, start by doing a complete format of the XP disk to remove any annoying left overs.  Starting clean can save you a world of grief.  If you need backups, do them first.  You've two disks so that shouldn't be a problem.

---

