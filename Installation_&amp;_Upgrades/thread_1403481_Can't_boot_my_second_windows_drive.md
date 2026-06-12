---
title: "Can't boot my second windows drive"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by gcordoba0928 on 2010-02-10
I made the mistake of reinstalling windows and loosing Grub. with the help of all the previuos threads on this matter I have manage to have load grub and also have the access to Ubunut. My problem is with windows. I can't make it work. I have two hard drive one IDE 80 GB for windows (slave of my DVD). and a SATA 500GB where uburtu is loaded. when I run fdisk -l i get this:
 
Disk/dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512= 8225280 bytes
Disk indentifier: 0x000a0abf
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 59517 478070271 83 Linux
/dev/sda2 59518 60801 10313730 5 Extended
/dev/sda5 59518 60801 10313698+ 82 Linux swap / Solaris
 
Disk/dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk Indetifier: 0xfe5afe5a
 
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9729
 
 
my device.map file says
 
df(fd0) /dev/fd0
(hd0) /dev/hdb
(hd1) /dev/sda
 
 
and in my menu.lst file the kernel for linux run with out problem with root (hd0,0) and I can find the right disk for windows.
 
Lookng at all this information many things don't match. accordong to my device.map vs fdisk. My linux drive should be (hd1) still I have to put (hd0) to make it work. Then when I try (hd0) in windows or (hd1) it does not work. 
 
please help? dont know what to do.
 
regards

---

### Post by oldfred on 2010-02-10
If in BIOS you make the windows drive first does it boot ok? If so there may be some confusion in the devicemap commands. To see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by gcordoba0928 on 2010-02-11
I tried the first thing, swapping the boot sequence of the drives, and GRUB is not loaded. It goes directly to Windows. For the second recommendation here are the results from the script

```

```
============================ Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe5afe5a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        aeee5d8b-4e9d-422d-ae94-836a71aa7765   ext3                                     
/dev/sda5        efb34710-0778-4f44-8270-954bee3309bf   swap                                     
/dev/sdb1        B6404AE5404AABC5                       ntfs       principal                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /fastdetect /noexecute=optin

---

### Post by oldfred on 2010-02-12
Your results.txt is not complete?? Also highlight the entire thing and click on the # [code] tag in the top editing panel to make it easier to scroll thru.

Edit:
I just ran the latest version (52) and also got partial results. I PM'd meierfra to make sure he knew there was an issue with the script.

---

### Post by gcordoba0928 on 2010-02-12
this is all that there is in the file. I will run it again if you believe something is missing.
 
 
```
 
============================= Boot Info Summary: ==============================
 => Windows is installed in the MBR of /dev/sdb
sdb1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS
=========================== Drive/Partition Info: =============================
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe5afe5a
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        aeee5d8b-4e9d-422d-ae94-836a71aa7765   ext3                                     
/dev/sda5        efb34710-0778-4f44-8270-954bee3309bf   swap                                     
/dev/sdb1        B6404AE5404AABC5                       ntfs       principal                     
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)

================================ sdb1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /fastdetect /noexecute=optin


```

---

### Post by oldfred on 2010-02-12
Please download the script again. It has reverted to ver51 for the time being until ver53 can be released.

---

### Post by gcordoba0928 on 2010-02-12
this is with version 51

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe5afe5a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        aeee5d8b-4e9d-422d-ae94-836a71aa7765   ext3                                     
/dev/sda5        efb34710-0778-4f44-8270-954bee3309bf   swap                                     
/dev/sdb1        B6404AE5404AABC5                       ntfs       principal                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /fastdetect /noexecute=optin 
```

---

### Post by darkod on 2010-02-12
Sorry for all this confusion but there was some problem with the script it seems. There is a new ver52 online now. Please delete all older scripts you downloaded, download it again and try again. There should be much more data. One of the disks doesn't even seem recognized.

---

### Post by meierfra. on 2010-02-12
I  have no clue why the script does not detect /dev/sda.
You might try the newest version (0.53) but I doubt that it will make a difference.

Could you post the output of


```
sudo fdisk -lu /dev/sda
sudo fdisk -s /dev/sda
sudo sfdisk -s /dev/sda
sudo parted /dev/sda print
```

Please use "copy and paste". Your fdisk output in your first post has several typos.

---

### Post by meierfra. on 2010-02-12
If "root(hd0,0)" works for ubuntu, then the correct entry for Windows  should be


title Windows XP
rootnoverify  (hd1,0)
map (hd0) (hd1)
map (hd1)  (hd0)
chainloader +1

---

### Post by andrewthomas on 2010-02-13
I hate to jump right in but I have a similar problem after installing Karmic.  I now have grub on both my hard drives and windows will not load.  Could you look at my bootscript and lead me in the right direction?

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 410499364 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 410543996 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   145,950,524   145,950,462   7 HPFS/NTFS
/dev/sda2         145,950,525   488,392,064   342,441,540   5 Extended
/dev/sda5         145,950,588   474,415,514   328,464,927  83 Linux
/dev/sda6         474,415,578   488,392,064    13,976,487  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   150,384,464   150,384,402   7 HPFS/NTFS
/dev/sdb2         150,384,465   608,751,044   458,366,580  83 Linux
/dev/sdb3         608,751,045   625,137,344    16,386,300  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        52A0C5F8A0C5E299                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        022b33a9-6c12-44bc-b573-114ffe8ae906   ext4                                     
/dev/sda6        358dff3b-4bc5-4a99-83bf-f86272b725db   swap                                     
/dev/sdb2        a58a1181-597b-421b-a493-63c23d114b3e   ext4                                     
/dev/sdb3        a2a9dcb0-8ed2-4bc3-a831-ad20d10b0adf   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-13-generic" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux    /boot/vmlinuz-2.6.32-13-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    echo    Loading Linux 2.6.32-13-generic ...
    linux    /boot/vmlinuz-2.6.32-13-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux    /boot/vmlinuz-2.6.32-10-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    echo    Loading Linux 2.6.32-10-generic ...
    linux    /boot/vmlinuz-2.6.32-10-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 52a0c5f8a0c5e299
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro single
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro single
    initrd /boot/initrd.img-2.6.31-17-generic
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
UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=358dff3b-4bc5-4a99-83bf-f86272b725db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 210.1GB: boot/grub/core.img
 240.2GB: boot/grub/grub.cfg
 210.2GB: boot/initrd.img-2.6.32-10-generic
 210.3GB: boot/initrd.img-2.6.32-13-generic
 210.1GB: boot/vmlinuz-2.6.32-10-generic
 210.1GB: boot/vmlinuz-2.6.32-13-generic
 210.3GB: initrd.img
 210.2GB: initrd.img.old
 210.1GB: vmlinuz
 210.1GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set default="7"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro  vga=775 splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro single  vga=775 splash quiet
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro  vga=775 splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set a58a1181-597b-421b-a493-63c23d114b3e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=a58a1181-597b-421b-a493-63c23d114b3e ro single  vga=775 splash quiet
    initrd    /boot/initrd.img-2.6.31-17-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 52a0c5f8a0c5e299
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux /boot/vmlinuz-2.6.32-13-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro quiet splash
    initrd /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux /boot/vmlinuz-2.6.32-13-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro single
    initrd /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux /boot/vmlinuz-2.6.32-10-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro quiet splash
    initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux /boot/vmlinuz-2.6.32-10-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro single
    initrd /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a58a1181-597b-421b-a493-63c23d114b3e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a2a9dcb0-8ed2-4bc3-a831-ad20d10b0adf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  78.6GB: boot/grub/core.img
  80.5GB: boot/grub/grub.cfg
  78.7GB: boot/initrd.img-2.6.31-17-generic
  78.8GB: boot/initrd.img-2.6.31-19-generic
  77.6GB: boot/vmlinuz-2.6.31-17-generic
  78.3GB: boot/vmlinuz-2.6.31-19-generic
  78.8GB: initrd.img
  78.7GB: initrd.img.old
  78.3GB: vmlinuz
  77.6GB: vmlinuz.old
```

---

### Post by meierfra. on 2010-02-13
> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR="Red"]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 410499364 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM



andrewthomas:  You overwrote the Windows boot sector.   To fix the boot sector use this How-To

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If the Howto does not work for you or you have additional questions, please start a new thread. But  post a link to your new thread  in this thread.

---

### Post by gcordoba0928 on 2010-02-14
> **darkod said:**
> Sorry for all this confusion but there was some problem with the script it seems. There is a new ver52 online now. Please delete all older scripts you downloaded, download it again and try again. There should be much more data. One of the disks doesn't even seem recognized.

here it is with version 54

       ```
             Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 855507031 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a0abf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   956,140,604   956,140,542  83 Linux
/dev/sda2         956,140,605   976,768,064    20,627,460   5 Extended
/dev/sda5         956,140,668   976,768,064    20,627,397  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe5afe5a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        aeee5d8b-4e9d-422d-ae94-836a71aa7765   ext3                                     
/dev/sda5        efb34710-0778-4f44-8270-954bee3309bf   swap                                     
/dev/sdb1        B6404AE5404AABC5                       ntfs       principal                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.27-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro  single
initrd        /boot/initrd.img-2.6.27-16-generic

title        Ubuntu 9.10, kernel 2.6.24-25-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-25-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-25-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 ro  single
initrd        /boot/initrd.img-2.6.24-25-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aeee5d8b-4e9d-422d-ae94-836a71aa7765 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=efb34710-0778-4f44-8270-954bee3309bf none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 438.0GB: boot/grub/menu.lst
 438.0GB: boot/grub/stage2
 437.9GB: boot/initrd.img-2.6.24-25-generic
 437.9GB: boot/initrd.img-2.6.24-25-generic.bak
 438.0GB: boot/initrd.img-2.6.27-16-generic
 438.0GB: boot/initrd.img-2.6.28-17-generic
 437.9GB: boot/initrd.img-2.6.31-16-generic
 438.0GB: boot/initrd.img-2.6.31-17-generic
 438.0GB: boot/initrd.img-2.6.31-19-generic
 438.0GB: boot/vmlinuz-2.6.24-25-generic
 438.0GB: boot/vmlinuz-2.6.27-16-generic
 437.9GB: boot/vmlinuz-2.6.28-17-generic
 438.0GB: boot/vmlinuz-2.6.31-16-generic
 438.0GB: boot/vmlinuz-2.6.31-17-generic
 437.9GB: boot/vmlinuz-2.6.31-19-generic
 438.0GB: initrd.img
 438.0GB: initrd.img.old
 437.9GB: vmlinuz
 438.0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /fastdetect /noexecute=opti
```

---

### Post by gcordoba0928 on 2010-02-14
> **meierfra. said:**
> I  have no clue why the script does not detect /dev/sda.
You might try the newest version (0.53) but I doubt that it will make a difference.

Could you post the output of


```
sudo fdisk -lu /dev/sda
sudo fdisk -s /dev/sda
sudo sfdisk -s /dev/sda
sudo parted /dev/sda print
```Please use "copy and paste". Your fdisk output in your first post has several typos.


```
gcordoba@gcordoba-desktop:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a0abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   956140604   478070271   83  Linux
/dev/sda2       956140605   976768064    10313730    5  Extended
/dev/sda5       956140668   976768064    10313698+  82  Linux swap / Solaris



```

```
gcordoba@gcordoba-desktop:~$ sudo fdisk -s /dev/sda
488386584
```

```
gcordoba@gcordoba-desktop:~$ sudo sfdisk -s /dev/sda
488386584

```

```
gcordoba@gcordoba-desktop:~$ sudo parted /dev/sda print
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  490GB  490GB   primary   ext3            boot
 2      490GB   500GB  10.6GB  extended
 5      490GB   500GB  10.6GB  logical   linux-swap(v1
```)

---

### Post by gcordoba0928 on 2010-02-14
> **meierfra. said:**
> If "root(hd0,0)" works for ubuntu, then the correct entry for Windows  should be


title Windows XP
rootnoverify  (hd1,0)
map (hd0) (hd1)
map (hd1)  (hd0)
chainloader +1


I tried this and it fixed it. Thanks, the addition of the map command worked. thanks all for your support and patience. Should I show it as Solve now? As see there is a new "thread" growing that has not been resolved. Again thanks to all:D:D:D:D

---

### Post by meierfra. on 2010-02-14
> I tried this and it fixed it. 
Great.

>  Should I show it as Solve now? 
Yes.

Could you do me favor?  Yesterday I ran into a  similar case like yours where some of the hard drives were not detected by the boot info script. After some debugging, I was able to work around the problem, and as you can see on your new RESULTS.txt, the script  is now able  to find all the  hard drive.  But I still do not really understand why this problem occured in the first place. So to help my understanding could you post the output of

```
sudo blkid /dev/sda
```

---

### Post by gcordoba0928 on 2010-02-15
> **meierfra. said:**
> Great.


Yes.

Could you do me favor?  Yesterday I ran into a  similar case like yours where some of the hard drives were not detected by the boot info script. After some debugging, I was able to work around the problem, and as you can see on your new RESULTS.txt, the script  is now able  to find all the  hard drive.  But I still do not really understand why this problem occured in the first place. So to help my understanding could you post the output of

```
sudo blkid /dev/sda
```

sure no problem 

```
/dev/sda: TYPE="promise_fasttrack_raid_member" 
```

thanks all.

---

### Post by meierfra. on 2010-02-15
> /dev/sda: TYPE="promise_fasttrack_raid_member"

Thanks.  If you have some time, could you answer a couple of  questions (if your never heard of "raid"  just ignore my questions)

Did you ever use "raid" on your computer?
Do you have some "raid" setting enabled in the Bios?

---

### Post by gcordoba0928 on 2010-02-17
> **meierfra. said:**
> Thanks.  If you have some time, could you answer a couple of  questions (if your never heard of "raid"  just ignore my questions)

Did you ever use "raid" on your computer?
 I don't have one yet. But my Sata drive is SEtup as RAID ready. I did this if I decide to add more drives than the road.

Do you have some "raid" setting enabled in the Bios?
Yes. for the reason above described.

hope this helps

---

### Post by meierfra. on 2010-02-17
> hope this helps
It does. Thanks.

---

