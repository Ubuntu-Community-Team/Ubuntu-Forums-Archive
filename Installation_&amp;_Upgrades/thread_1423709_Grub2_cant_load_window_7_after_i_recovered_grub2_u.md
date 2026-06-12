---
title: "Grub2 cant load window 7 after i recovered grub2 using live cd to boot windows 7"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by mrcet007 on 2010-03-07
i initilally installed ubuntu 9.10 then installed windows 7 ,then i recovered grub2 using livecd as told in the post [http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html](http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html) i did "sudo update-grub"  and got windows 7 menu entry but when i select that entry windows 7 does not load but the grub2 is reloaded again.:frown: 
i cant boot to windows 7.

Windows 7 have 100 mb partition "System Reserved" the grub2 points to that partition but still windows 7 not loaded.

**sudo fdisk -l**

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c3a81f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1520    12209368+  83  Linux
/dev/sda2            1521       38913   300359272+   5  Extended
/dev/sda3   *        3388        3400      102400    7  HPFS/NTFS
/dev/sda4            3400       13841    83865600    7  HPFS/NTFS
/dev/sda5            1521        3387    14996646   83  Linux
/dev/sda6           13842       26378   100703421    7  HPFS/NTFS
/dev/sda7           26379       38913   100687356    7  HPFS/NTFS

**sudo update-grub**
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
done

---

### Post by mrcet007 on 2010-03-07
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 3414047 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
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
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 4096079 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c3a81f5

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,418,799    24,418,737  83 Linux
/dev/sda2          24,418,800   625,137,344   600,718,545   5 Extended
/dev/sda5          24,418,863    54,412,154    29,993,292  83 Linux
/dev/sda6         222,355,728   423,762,569   201,406,842   7 HPFS/NTFS
/dev/sda7         423,762,633   625,137,344   201,374,712   7 HPFS/NTFS
/dev/sda3    *     54,413,312    54,618,111       204,800   7 HPFS/NTFS
/dev/sda4          54,618,112   222,349,311   167,731,200   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        647bbaf9-f130-4673-b81d-1c567065d564   ext4                                     
/dev/sda3        CAEE90ADEE9092F5                       ntfs       System Reserved               
/dev/sda4        3440D0EA40D0B438                       ntfs                                     
/dev/sda5        ba605f7b-addb-43ad-9aa1-ddd8fdaec332   ext4                                     
/dev/sda6        742A3C4E42C7B7B9                       ntfs       Rose                          
/dev/sda7        5F771097EA076AE3                       ntfs       Mathew                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=sherin)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_msdos
insmod part_msdos
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
search --no-floppy --fs-uuid --set 647bbaf9-f130-4673-b81d-1c567065d564
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 647bbaf9-f130-4673-b81d-1c567065d564
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=647bbaf9-f130-4673-b81d-1c567065d564 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 647bbaf9-f130-4673-b81d-1c567065d564
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=647bbaf9-f130-4673-b81d-1c567065d564 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set caee90adee9092f5
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=647bbaf9-f130-4673-b81d-1c567065d564 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=ba605f7b-addb-43ad-9aa1-ddd8fdaec332 /home           ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: initrd.img
   2.4GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb ```

```

---

### Post by lidex on 2010-03-07
Things look a little mixed up there. Did you, by chance, have XP installed originally, then installed karmic and then win7? It looks like grub2 is installed into sda1 AND sda3 and core.img for the first one cannot be located (overwritten??).

What is the output of this command:
```
cat /boot/grub/device.map
```

---

### Post by meierfra. on 2010-03-07
You have two problems:

**First Problem:**

 > Boot sector info: Grub 2 is installed in the boot sector of sda3 and
looks at sector 4096079 of the same hard drive for
core.img, core.img is at this location on /dev/sda and
looks on partition #1 for /boot/grub. No errors found
in the Boot Parameter Block.
Operating System: 

You installed Grub to the boot sector of the Windows 7 partition.  That erased some of the code necessary to "Window 7".
I suggest to use "testdisk" to restore the boot sector from the backup:

   ```
sudo apt-get install testdisk
```
(if apt-get cannot find the "testdisk" you need to enable the "universe" repository in "System->Administration->Software Sources" and run "sudo apt--get update" )
  
  ```
 sudo testdisk /dev/sda
```

At the first  press "enter" to "proceed".
At the next screen:  "intel"
 "advanced",
Select the Windows system partition /dev/sda3  and choose "boot" 
 "BackupBS"
 type "Y" to confirm

The press "q" a few times to quit testdisk.

Reboot and see whether you can boot into Window 7.


[B]Second Problem;
[/B]

> /dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda4

Your partition table is messed up slightly.  Almost everthing will work just fine, but some programs (for example 'gparted") will not be able to detect your partition. Let me know if you would like to fix this problem.

---

