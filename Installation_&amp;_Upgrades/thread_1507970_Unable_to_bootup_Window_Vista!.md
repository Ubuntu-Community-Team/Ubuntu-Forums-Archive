---
title: "Unable to bootup Window Vista!"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-06-12
I am running a dual-boot system (Windows Vista and Ubuntu) and after I upgraded to Ubuntu 10.04 I am unable to boot up Windows Vista.

How can I fix this?  Grub is probably where the problem is; but I need some help to fix this so my Windows partition of my hard drive is found and I can boot from it.  

Any help would be greatly appreciated!

Thank you very much.

---

### Post by X-Windows on 2010-06-12
Try running **sudo update-grub** and post the results. That will update your grub boot-loader and check for other operating systems you have installed.

---

### Post by virsto on 2010-06-12
Ok,

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
virgil@virgil-desktop:~$ ^C
virgil@virgil-desktop:~$ 

This is what happened.

--V

---

### Post by darkod on 2010-06-12
When you did the upgrade, was there a window asking where to install grub2 and did you select all partitions, not just disks?

When you select vista from the boot menu, what happens?

---

### Post by virsto on 2010-06-12
I get the following error when I try to boot Windows Vista:

Geom Error
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

(which is the same as before I executed  sudo update-grub)

I do not believe that Windows Vista (load) is on /dev/sda1. I have attached a screenshot of my computer and indicated with the mouse pointer where the boot folder is for Windows Vista; but, I do not know how I can get Grub to execute the boot part of this partition.

Again, help would be greatly appreciated.

--V

---

### Post by virsto on 2010-06-12
I do not believe there was a window asking about where to install Grub2 and there was nothing about selecting all partitions. When I select to boot from Windows Vista, the screen goes blank and the following message appears at the top left of a black screen.

Geom Error
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Thanks for looking at my problem darkod.

--V

---

### Post by darkod on 2010-06-12
Run the boot info script for more detailed information and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by virsto on 2010-06-12
I went to the link that you gave; but, I do not understand what is posted there. First, I can boot Ubuntu from a HD. Please explain (in more detail for my situation) how I can create a detailed listing of what happens during the boot process.

Thank you.

--V

---

### Post by virsto on 2010-06-12
Does it make sense to edit the Grub file to change the device from sda? to different values (e.g. sda2, sda3,...)?

However, I do not know how to edit the Grub file.

--V

---

### Post by darkod on 2010-06-12
Download the boot info script from the link in my signature. When it finishes, it will probably be in your Downloads folder. Open Places-Downloads to see if the script (file) is there. Don't try to open it or anything, just check it's there.

If it is, for execution you only need to do in terminal:

sudo bash ~/Downloads/boot_info_script*.sh

That will create results.txt file in the same folder where the script is (Downloads). Open the file and just copy the text as from any document and paste it here. When you paste it it's better to select all of it and hit the # button in the toolbar above to put CODE tags around the text for easier reading.

---

### Post by virsto on 2010-06-12
Ok done!
Here are the results

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1141884946 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1141873810 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 1141879314 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 1141867690 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sde1 and 
                       looks at sector 1141881618 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   732,721,143   732,719,096   7 HPFS/NTFS
/dev/sdb2         732,721,152 1,141,559,271   408,838,120   7 HPFS/NTFS
/dev/sdb3       1,141,562,835 1,465,144,064   323,581,230   5 Extended
/dev/sdb5       1,141,562,898 1,451,922,569   310,359,672  83 Linux
/dev/sdb6       1,451,922,633 1,465,144,064    13,221,432  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 203.9 GB, 203927060480 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398295040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   398,267,414   398,267,352   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E45E9EF65E9EC12A                       ntfs       SYSTEM                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A5C56EB5C56D175                       ntfs       APPLIC                        
/dev/sdb2        9E60F96860F94813                       ntfs       MISC                          
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        1c2739db-9258-4b62-b736-be3857c711e9   ext4                                     
/dev/sdb6        37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        0108-16A0                              vfat       TREKSTOR                      
/dev/sdd: PTTYPE="dos" 
/dev/sde1        18EC-3E16                              vfat       MAXTOR                        
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/MAXTOR_           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /media/TREKSTOR_         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/APPLIC            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e45e9ef65e9ec12a
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1c2739db-9258-4b62-b736-be3857c711e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 584.6GB: boot/grub/core.img
 591.6GB: boot/grub/grub.cfg
 590.1GB: boot/initrd.img-2.6.31-20-generic
 590.2GB: boot/initrd.img-2.6.32-22-generic
 586.6GB: boot/vmlinuz-2.6.31-20-generic
 593.3GB: boot/vmlinuz-2.6.32-22-generic
 590.2GB: initrd.img
 593.3GB: vmlinuz
```

Hope this is what you needed.

--V

---

### Post by darkod on 2010-06-12
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 1141884946 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

You have grub2 installed in the vista partition. Use this procedure to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So you need to remove it from /dev/sda1, partition #1 on disk /dev/sda. It should be fine after that.

---

### Post by virsto on 2010-06-12
Ok done!
Here are the results

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1141884946 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1141873810 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 1141879314 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 1141867690 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sde1 and 
                       looks at sector 1141881618 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   732,721,143   732,719,096   7 HPFS/NTFS
/dev/sdb2         732,721,152 1,141,559,271   408,838,120   7 HPFS/NTFS
/dev/sdb3       1,141,562,835 1,465,144,064   323,581,230   5 Extended
/dev/sdb5       1,141,562,898 1,451,922,569   310,359,672  83 Linux
/dev/sdb6       1,451,922,633 1,465,144,064    13,221,432  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 203.9 GB, 203927060480 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398295040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   398,267,414   398,267,352   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E45E9EF65E9EC12A                       ntfs       SYSTEM                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A5C56EB5C56D175                       ntfs       APPLIC                        
/dev/sdb2        9E60F96860F94813                       ntfs       MISC                          
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        1c2739db-9258-4b62-b736-be3857c711e9   ext4                                     
/dev/sdb6        37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        0108-16A0                              vfat       TREKSTOR                      
/dev/sdd: PTTYPE="dos" 
/dev/sde1        18EC-3E16                              vfat       MAXTOR                        
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/MAXTOR_           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /media/TREKSTOR_         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/APPLIC            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e45e9ef65e9ec12a
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1c2739db-9258-4b62-b736-be3857c711e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 584.6GB: boot/grub/core.img
 591.6GB: boot/grub/grub.cfg
 590.1GB: boot/initrd.img-2.6.31-20-generic
 590.2GB: boot/initrd.img-2.6.32-22-generic
 586.6GB: boot/vmlinuz-2.6.31-20-generic
 593.3GB: boot/vmlinuz-2.6.32-22-generic
 590.2GB: initrd.img
 593.3GB: vmlinuz
```

Hope this is what you needed.

--V

---

### Post by virsto on 2010-06-12
This worked!
Thanks for the scripts and very good instructions on how to fix this irritating problem. I now remember why I like Ubuntu so much --- great help when you need it!

Have a good day

---

### Post by mnpilgrim on 2010-06-12
I am a newbie that has encountered the same issue when trying to create a dual boot with 10.4 and Vista Ultimate on my primary computer as well as a dual boot on 10.4 and Vista Premium on my second computer. 
Unfortunately, I did not explore this forum before taking action. Nevertheless, I did find an easy fix. I used the terminal command in windows to fix my MBR and then I deleted the Ubuntu partition in Windows. I re-installed 10.4 using the largest available space option during installation off a live 10.4 CD. This method worked flawlessly on both systems. Grub 2 was installed and both systems boot both OS selections.
I post this reply for other newbies that may still feel uncomfortable about using the Ubuntu terminal and Sudo commands  until they further familiarize themselves with their new OS.

---

