---
title: "grub2 not booting windows"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by thol4u on 2010-07-18
Hi All,

I have 2 different hard-disks, 1 for ubuntu and the other for win xp. If XP is hibernating then grub2 boots normally into XP, but if XP is attempted to boot normally from shutdown, I'm getting blank screen after seeing windows logo. Only way around to boot xp is to change the boot order of disks in bios. This is a fresh install of ubuntu 10.04 (lucid) on a new hard disk.

Relevant information are below: Appreciate any any help or pointers.
-----------------------------------------
Win XP entry in /boot/grub/grub.cfg

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d88018158017f8a8
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

---------------------

fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8a64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150253568   83  Linux
/dev/sda2           18706       19458     6034433    5  Extended
/dev/sda5           18706       19458     6034432   82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x074028f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12921    97682728+   7  HPFS/NTFS

Thanks
Thol

---

### Post by oldfred on 2010-07-18
Run this.  It will show all the configuration but I am interested if windows boot.ini thinks it is drive 0 or drive 1.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

It may be change boot.ini or physically change drive order (SATA port order) and then maybe reinstall grub and sudo update grub.

---

### Post by thol4u on 2010-07-19
Hi oldfred,

Thank you very much for your reply. Below is the information you have requested. As you have mentioned boot.ini thinks it is drive 0. I'll try to change it to drive 1 and see if it helps.
Thanks again.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   300,509,183   300,507,136  83 Linux
/dev/sda2         300,511,230   312,580,095    12,068,866   5 Extended
/dev/sda5         300,511,232   312,580,095    12,068,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   195,365,519   195,365,457   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7a0a0201-7d6a-4b77-9295-5712642a53fa   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0b370936-7a4b-4026-9a38-1d85aa88ac42   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D88018158017F8A8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/winnt             fuseblk    (ro,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a0a0201-7d6a-4b77-9295-5712642a53fa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d88018158017f8a8
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
proc                                       /proc         proc  nodev,noexec,nosuid               0  0  
# / was on /dev/sda1 during installation
UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa  /             ext4  errors=remount-ro                 0  1  
# swap was on /dev/sda5 during installation
UUID=0b370936-7a4b-4026-9a38-1d85aa88ac42  none          swap  sw                                0  0  
/dev/sdb1                                  /media/winnt  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  

=================== sda1: Location of files loaded by Grub: ===================


 137.6GB: boot/grub/core.img
  64.8GB: boot/grub/grub.cfg
 137.6GB: boot/initrd.img-2.6.32-21-generic
 137.6GB: boot/initrd.img-2.6.32-22-generic
 137.7GB: boot/initrd.img-2.6.32-23-generic
 137.5GB: boot/vmlinuz-2.6.32-21-generic
 137.5GB: boot/vmlinuz-2.6.32-22-generic
 137.6GB: boot/vmlinuz-2.6.32-23-generic
 137.7GB: initrd.img
 137.6GB: initrd.img.old
 137.6GB: vmlinuz
 137.5GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="IBM Client for e-business Windows XP v2.09" /noexecute=alwaysoff /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 


```

---

### Post by oldfred on 2010-07-19
windows does think it is drive 0 and grub sees it as sdb1 or hd1,1. Usually the drivemap command makes windows think it is drive 0 even when it is not. Some obviously is different with hibernation and booting.

Since windows was the first drive before the new install of Ubuntu, I would just swap the SATA port order so windows is still first, Ubuntu will not care. You may or may not have to reinstall grub, but will have to run sudo update-grub to get it to change the windows setting from drive 1 to drive 0.

---

### Post by thol4u on 2010-07-19
Hi oldfred,

Can you please let me know or point me how to swap the SATA port order?
Thank you

---

### Post by oldfred on 2010-07-19
Port order for my system is the order the SATA connectors are plugged into the motherboard. My motherboard defines port one as top left as you look at the motherboard a certain way. There are also tiny labels next to each or at least first & last of the connectors on the motherboard.

My drives sda, sdb, sdc are in the same order as the drives are plugged into the motherboard.

---

### Post by thol4u on 2010-07-20
Hi,

Thanks for the reply. I have a Thinkpad T60p laptop with 2 hard-disks (one of them in place of cd drive). I'm not sure how to look at motherboard. I tried physically swapping the 2 disks, but both Lucid and XP didn't boot :( so I switched back.

Thanks
Thol

---

### Post by oldfred on 2010-07-20
When you switched drives did you try booting both? I would have expected windows to boot as it says it is drive 0 and Ubuntu to boot also as the search command should override the set root and find the correct partition to boot.

---

### Post by thol4u on 2010-07-20
Yes, After swapping I tried booting from both disks by changing bios. Both didn't go beyond the respective logo. Additionally xp gave BSOD when attempting to read the hibernate file.

---

### Post by oldfred on 2010-07-20
I do not understand why windows will not boot. I am now grasping at straws. Sometimes the search line has caused issues, When booting windows use e on the grub menu and delete the entire search line. Control x to boot.

But as a caution you should not hibernate and then use Ubuntu to modify the XP partition. You can read from it, but if you ever write anything it will corrupt the hibernation and cause huge problems. Hiberation of any system & dual boot do not mix.

---

### Post by thol4u on 2011-03-16
I booted ubuntu in recovery mode and found that fsck utility is prompts to run a check on Windows hard drive and waits for response. In normal boot this appears as hang.

After I edited the /etc/fstab and commented out the Windows hard drive, ubuntu boots without any problem. Now I can swap the drives.

fstab entries right now:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc         proc  nodev,noexec,nosuid               0  0  
# / was on /dev/sda1 during installation
UUID=7a0a0201-7d6a-4b77-9295-5712642a53fa  /             ext4  errors=remount-ro                 0  1  
# swap was on /dev/sda5 during installation
#UUID=0b370936-7a4b-4026-9a38-1d85aa88ac42  none          swap  sw                                0  0  
#/dev/sdb1                                  /media/winnt  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  

```

Thanks for all the replies

---

