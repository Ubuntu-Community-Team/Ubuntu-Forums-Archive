---
title: "Windows xp missing from boot"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by sndarvekar on 2010-07-26
[SIZE=2]I installed ubuntu but since then cannot boot into Window Xp as I dont get that option on the Grub. Grub directly boots into Ubuntu.
What can I do.
After reading from other post I am posting the results.
Please help as my database program is windows only and I have to run it as have to update the data base regularly
Thanks
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63. According to the info in the boot 
                       sector, sdc5 has 38700521 sectors, but according to 
                       the info from fdisk, it has 74380886 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdb has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,371   976,773,119   874,374,749   f W95 Ext d (LBA)
/dev/sda5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sda6         204,796,683   511,991,549   307,194,867   7 HPFS/NTFS
/dev/sda7         511,991,613   936,375,411   424,383,799   7 HPFS/NTFS
/dev/sda8         974,999,552   976,773,119     1,773,568  82 Linux swap / Solaris
/dev/sda9         936,376,320   974,985,215    38,608,896  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdc2          81,915,435   156,296,384    74,380,950   f W95 Ext d (LBA)
/dev/sdc5          81,915,498   156,296,384    74,380,887   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BA308A013089C4BB                       ntfs       XP home                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        E06074BD60749BCA                       ntfs       F                             
/dev/sda6        F26C66686C662795                       ntfs       G                             
/dev/sda7        369C96859C963F75                       ntfs       K                             
/dev/sda8        0f2d6416-095e-4b61-add3-cb2a7d3b3dc8   swap                                     
/dev/sda9        9cce866c-19c2-439b-8912-8c1b307b2904   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         8421-35D9                              vfat       PHONE                         
/dev/sdc1        1674FC3C74FC1FE3                       ntfs       Backup Clin                   
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        16C8F7E8C8F7C451                       ntfs       XP home                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /media/G                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/K                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/F                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Backup Clin       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/XP home           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9cce866c-19c2-439b-8912-8c1b307b2904 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9cce866c-19c2-439b-8912-8c1b307b2904 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
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

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext4    errors=remount-ro 0       1
/dev/sda8       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================
[COLOR=Blue]

 [COLOR=Black]481.7GB: boot/grub/core.img
 497.2GB: boot/grub/grub.cfg
 481.7GB: boot/initrd.img-2.6.32-21-generic
 481.7GB: boot/vmlinuz-2.6.32-21-generic
 481.7GB: initrd.img
 481.7GB: vmlinuz

Boot script is as follows
[COLOR=Blue]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done[/COLOR]



[/COLOR][/COLOR] [/SIZE]

---

### Post by P4man on 2010-07-26
Have you tried running

```
sudo update-grub
```

from a terminal?

---

### Post by oldfred on 2010-07-26
You show wubi files and a full install but none of the NTFS partitions are showing any boot files.

WinXP boot files should be shown are I do not see them.
/boot.ini  /ntldr /NTDETECT.COM

Could you please go back and make your font smaller and preferably enclose you boot script in code tags. Highlight the boot script and click and the # in the edit panel above your message as you edit it.

---

### Post by sndarvekar on 2010-08-05
Friends, I am still waiting for solution.
Can anybody help me out. :(

---

### Post by oldfred on 2010-08-05
I think it is reinstall windows as you overwrote it. Did you check your windows partitions to see if the windows files are really there and the script somehow missed them?

---

### Post by sndarvekar on 2010-08-05
Windows is still there and I can see it from Ubuntu, 
I dont want to reinstall windows as it is a big headache, not as simple as installing Ubuntu.
Do we have some other way of accessing the windows as my database is in windows

---

### Post by oldfred on 2010-08-05
Which partition has these files (not your windows data)
/boot.ini  /ntldr /NTDETECT.COM

Did you have 2 windows installs? Windows combines its boot into the first install that is the active partition (boot flag). If you delete the first windows install the second has no boot files, but usually can be repaired if it is a primary partition.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

