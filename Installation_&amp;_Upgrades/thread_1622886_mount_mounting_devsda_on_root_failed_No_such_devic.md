---
title: "mount: mounting /dev/sda on /root/ failed: No such device"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by Zulwaqar on 2010-11-16
Failed to boot Ubuntu 10.10:

mount: mounting /dev/sda7 on /root/ failed: No such device
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootrag


Please help me!!!

---

### Post by Zulwaqar on 2010-11-16
sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ee9a499

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7650    61440000    7  HPFS/NTFS
/dev/sda2            7650       42836   282633216    7  HPFS/NTFS
/dev/sda3   *       42836       49637    54629376    7  HPFS/NTFS
/dev/sda4           49637       77826   226426881    f  W95 Ext'd (LBA)
/dev/sda5           49637       70544   167936000    7  HPFS/NTFS
/dev/sda6           70544       73221    21502976    7  HPFS/NTFS
/dev/sda7           73221       73470     1998848   82  Linux swap / Solaris
/dev/sda8           73470       77826    34985984   83  Linux

Disk /dev/sdb: 16.0 GB, 16030597120 bytes
64 heads, 32 sectors/track, 15287 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7198

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15287    15653872    c  W95 FAT32 (LBA)

---

### Post by Rubi1200 on 2010-11-16
Hi and welcome to the forums :)

Please use a LiveCD to boot the computer and choose to try Ubuntu in live mode.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here to the forums and we will see what we can do to try and help you resolve the situation.

Thanks.

---

### Post by Zulwaqar on 2010-11-16
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Please use a LiveCD to boot the computer and choose to try Ubuntu in live mode.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here to the forums and we will see what we can do to try and help you resolve the situation.

Thanks.
```

                Boot Info Script 0.55    dated February 15th, 2010                     

============================= Boot Info Summary: ============================== 

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub. 
 => Syslinux is installed in the MBR of /dev/sdb 

sda1: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  Windows 7 
    Boot files/dirs:   /Windows/System32/winload.exe 

sda2: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files/dirs:    

sda3: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /GRLDR /ntldr 
                       /NTDETECT.COM 

sda4: _________________________________________________________________________ 

    File system:       Extended Partition 
    Boot sector type:  - 
    Boot sector info:   

sda5: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048. 
    Operating System:   
    Boot files/dirs:    

sda6: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048. 
    Operating System:   
    Boot files/dirs:    

sda7: _________________________________________________________________________ 

    File system:       swap 
    Boot sector type:  - 
    Boot sector info:   

sda8: _________________________________________________________________________ 

    File system:       ext2 
    Boot sector type:  - 
    Boot sector info:   
    Operating System:  Ubuntu 10.10 
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 

sdb1: _________________________________________________________________________ 

    File system:       vfat 
    Boot sector type:  Fat32 
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 32. 
    Operating System:   
    Boot files/dirs:    

=========================== Drive/Partition Info: ============================= 

Drive: sda ___________________ _____________________________________________________ 

Disk /dev/sda: 640.1 GB, 640135028736 bytes 
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 

Partition  Boot         Start           End          Size  Id System 

/dev/sda1               2,048   122,882,047   122,880,000   7 HPFS/NTFS 
/dev/sda2         122,882,048   688,148,479   565,266,432   7 HPFS/NTFS 
/dev/sda3    *    688,148,480   797,407,231   109,258,752   7 HPFS/NTFS 
/dev/sda4         797,409,278 1,250,263,039   452,853,762   f W95 Ext d (LBA) 
/dev/sda5         797,409,280 1,133,281,279   335,872,000   7 HPFS/NTFS 
/dev/sda6       1,133,283,328 1,176,289,279    43,005,952   7 HPFS/NTFS 
/dev/sda7       1,176,291,328 1,180,289,023     3,997,696  82 Linux swap / Solaris 
/dev/sda8       1,180,291,072 1,250,263,039    69,971,968  83 Linux 


Drive: sdb ___________________ _____________________________________________________ 

Disk /dev/sdb: 16.0 GB, 16030597120 bytes 
64 heads, 32 sectors/track, 15287 cylinders, total 31309760 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 

Partition  Boot         Start           End          Size  Id System 

/dev/sdb1    *             32    31,307,775    31,307,744   c W95 FAT32 (LBA) 


blkid -c /dev/null: ____________________________________________________________ 

Device           UUID                                   TYPE       LABEL                          

/dev/loop0                                              squashfs                                  
/dev/loop1       a01ad302-72d9-40ff-a2d6-35357f21c152   ext3                                      
/dev/sda1        CCE8B558E8B5420E                       ntfs                                      
/dev/sda2        489ECAD19ECAB6AA                       ntfs       Data 1                         
/dev/sda3        2CFEFAB3FEFA7504                       ntfs       Master                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6CC0901DC08FEBA0                       ntfs       Data3                          
/dev/sda6        465A4E315A4E1E55                       ntfs       Data4                          
/dev/sda7        844824cd-d443-4f41-9be1-6b9451766e75   swap                                      
/dev/sda8        d6351098-edd1-46e0-aa95-73d994a167cb   ext2                                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        702C-434B                              vfat                                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: =========================== 

Device           Mount_Point              Type       Options 

aufs             /                        aufs       (rw) 
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) 
/dev/loop0       /rofs                    squashfs   (ro,noatime) 
/dev/sda5        /media/Data3             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) 
/dev/sda8        /media/d6351098-edd1-46e0-aa95-73d994a167cb ext2       (rw,nosuid,nodev,uhelper=udisks) 
/dev/sda2        /media/Data 1            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) 


================================ sda3/boot.ini: ================================ 

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda8/boot/grub/grub.cfg: =========================== 

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
set root='(hd0,msdos7)' 
search --no-floppy --fs-uuid --set d6351098-edd1-46e0-aa95-73d994a167cb 
if loadfont /usr/share/grub/unicode.pf2 ; then 
  set gfxmode=640x480 
  load_video 
  insmod gfxterm 
fi 
terminal_output gfxterm 
insmod part_msdos 
insmod ext2 
set root='(hd0,msdos7)' 
search --no-floppy --fs-uuid --set d6351098-edd1-46e0-aa95-73d994a167cb 
set locale_dir=($root)/boot/grub/locale 
set lang=id 
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { 
    recordfail 
    insmod part_msdos 
    insmod ext2 
    set root='(hd0,msdos7)' 
    search --no-floppy --fs-uuid --set d6351098-edd1-46e0-aa95-73d994a167cb 
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda7 ro   quiet splash 
    initrd    /boot/initrd.img-2.6.35-22-generic 
} 
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 
    recordfail 
    insmod part_msdos 
    insmod ext2 
    set root='(hd0,msdos7)' 
    search --no-floppy --fs-uuid --set d6351098-edd1-46e0-aa95-73d994a167cb 
    echo    'Loading Linux 2.6.35-22-generic ...' 
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda7 ro single 
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
    set root='(hd0,msdos7)' 
    search --no-floppy --fs-uuid --set d6351098-edd1-46e0-aa95-73d994a167cb 
    linux16    /boot/memtest86+.bin 
} 
menuentry "Memory test (memtest86+, serial console 115200)" { 
    insmod part_msdos 
    insmod ext2 
    set root='(hd0,msdos7)' 
    search --no-floppy --fs-uuid --set d6351098-edd1-46e0-aa95-73d994a167cb 
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8 
} 
### END /etc/grub.d/20_memtest86+ ### 

### BEGIN /etc/grub.d/30_os-prober ### 
menuentry "Windows 7 (loader) (on /dev/sda3)" { 
    insmod part_msdos 
    insmod ntfs 
    set root='(hd0,msdos3)' 
    search --no-floppy --fs-uuid --set 2cfefab3fefa7504 
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

=============================== sda8/etc/fstab: =============================== 

# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda7 during installation 
UUID=d6351098-edd1-46e0-aa95-73d994a167cb /               ext2    errors=remount-ro 0       1 
# swap was on /dev/sda6 during installation 
UUID=844824cd-d443-4f41-9be1-6b9451766e75 none            swap    sw              0       0 

=================== sda8: Location of files loaded by Grub: =================== 


 623.8GB: boot/grub/core.img 
 623.8GB: boot/grub/grub.cfg 
 623.7GB: boot/initrd.img-2.6.35-22-generic 
 623.6GB: boot/vmlinuz-2.6.35-22-generic 
 623.7GB: initrd.img 
 623.6GB: vmlinuz

```

---

### Post by Rubi1200 on 2010-11-16
Did you upgrade to Windows 7 from Windows XP?

There are remnants of the XP boot files as well as what appears to be something from BCD on sda3:
   > [COLOR=Red]/boot.ini[/COLOR] /bootmgr /Boot/BCD[COLOR=Red] /GRLDR[/COLOR] [COLOR=Red]/ntldr [/COLOR]
                       [COLOR=Red]/NTDETECT.COM[/COLOR] Did you install Ubuntu after the upgrade to Windows?

Please give a bit more detail about how you ended up with the errors you are seeing.

Thanks.

---

### Post by dino99 on 2010-11-16
your installation is confused, better to remove it and make a clean one:

boot on partedmagic ( [http://partedmagic.com/](http://partedmagic.com/) ) to create 3 partitions:

- / : which is "root", make it bootable, ext4, ~ 12 Gb (take note of its name, something like /dev/sd?, the installer in manual mode will ask about it )

- swap : ~ 2 Gb

- /home : ext3 or ext4, unlimited space to store your data and settings

then use the "alternate" iso to install it on / , and install grub2 on /dev/sd? ( ? is a letter )

then you can choose to boot on hdd into the bios.

---

