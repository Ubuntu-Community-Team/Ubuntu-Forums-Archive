---
title: "How to operate GRUB loader !!???"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by scientistshrey on 2010-06-26
Hey !
I have Windows 7 and I recently installed Ubuntu 10.04 LTS.
After I restarted the system, I got GRUB rescue>

I have no idea at all how to use GRUB or how to use Ubuntu or any open-source stuff properly, yet !!
I tried to format a drive that I thought was containing Ubuntu, but nothing helpful happened.

I don't even have the windows CD as my windows came pre-installed.

I'm completely out of my wits and desperately need valuable advice.

---

### Post by darkod on 2010-06-26
Boot with the ubuntu cd in live mode. Go to the link in my signature and follow the instructions there to run the boot info script. Post the content of the results file as explained.

---

### Post by scientistshrey on 2010-06-26
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,402,047   102,195,200   7 HPFS/NTFS
/dev/sda3         102,402,048   204,802,047   102,400,000   7 HPFS/NTFS
/dev/sda4         204,802,048   312,580,095   107,778,048   f W95 Ext d (LBA)
/dev/sda5         204,804,096   312,579,759   107,775,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   353,814,427   353,812,380   7 HPFS/NTFS
/dev/sdb2         353,814,526   625,141,759   271,327,234   5 Extended
/dev/sdb5         353,814,528   614,037,503   260,222,976  83 Linux
/dev/sdb6         614,039,552   625,141,759    11,102,208  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6CA6BCF0A6BCBBC0                       ntfs                                     
/dev/sda2        08BAC5F8BAC5E274                       ntfs                                     
/dev/sda3        382C65AE2C656838                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9A4478E94478CA11                       ntfs       Local Disk                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0420E2B520E2AD3C                       ntfs       Shrey's Disk                  
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        566e88fb-8b2b-46eb-9c88-6492ca3b495b   ext4                                     
/dev/sdb6        f92bfea5-0c23-459f-8b9e-fd06435ce1d2   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Local Disk        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/566e88fb-8b2b-46eb-9c88-6492ca3b495b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/Shrey's Disk      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/6CA6BCF0A6BCBBC0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/08BAC5F8BAC5E274  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/382C65AE2C656838  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
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
search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8a6a95a66a958f95
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,402,047   102,195,200   7 HPFS/NTFS
/dev/sda3         102,402,048   204,802,047   102,400,000   7 HPFS/NTFS
/dev/sda4         204,802,048   312,580,095   107,778,048   f W95 Ext d (LBA)
/dev/sda5         204,804,096   312,579,759   107,775,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   353,814,427   353,812,380   7 HPFS/NTFS
/dev/sdb2         353,814,526   625,141,759   271,327,234   5 Extended
/dev/sdb5         353,814,528   614,037,503   260,222,976  83 Linux
/dev/sdb6         614,039,552   625,141,759    11,102,208  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6CA6BCF0A6BCBBC0                       ntfs                                     
/dev/sda2        08BAC5F8BAC5E274                       ntfs                                     
/dev/sda3        382C65AE2C656838                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9A4478E94478CA11                       ntfs       Local Disk                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0420E2B520E2AD3C                       ntfs       Shrey's Disk                  
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        566e88fb-8b2b-46eb-9c88-6492ca3b495b   ext4                                     
/dev/sdb6        f92bfea5-0c23-459f-8b9e-fd06435ce1d2   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Local Disk        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/566e88fb-8b2b-46eb-9c88-6492ca3b495b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/Shrey's Disk      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/6CA6BCF0A6BCBBC0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/08BAC5F8BAC5E274  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/382C65AE2C656838  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
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
search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8a6a95a66a958f95
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
# / was on /dev/sdb5 during installation
UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f92bfea5-0c23-459f-8b9e-fd06435ce1d2 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 286.5GB: boot/grub/core.img
 278.0GB: boot/grub/grub.cfg
 286.5GB: boot/initrd.img-2.6.32-21-generic
 286.5GB: boot/vmlinuz-2.6.32-21-generic
 286.5GB: initrd.img
 286.5GB: vmlinuz
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f92bfea5-0c23-459f-8b9e-fd06435ce1d2 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 286.5GB: boot/grub/core.img
 278.0GB: boot/grub/grub.cfg
 286.5GB: boot/initrd.img-2.6.32-21-generic
 286.5GB: boot/vmlinuz-2.6.32-21-generic
 286.5GB: initrd.img
 286.5GB: vmlinuz

```

---

### Post by drs305 on 2010-06-26
scientistshrey,

Welcome to Ubuntu and the Ubuntu forums.

> 
[B]=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #5 for /boot/grub.
[/B]=> Windows is installed in the MBR of /dev/sdb


Grub 2 is looking at a Windows partition for its configuration files on sda5, but they are actually installed in sd**b**5.  Therefore, it is necessary to reinstall G2 to point it to the sdb5 files. This will also put G2 in the MBR of sdb but Windows should boot with this configuration.

To install G2 in the proper location, boot the Ubuntu LiveCD and then run the following commands. Make sure you mount the *partition* (sdb5) and install to the *drive* (sdb).

```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

```

After you reboot into Ubuntu, you may need to run "sudo update-grub" to allow Grub 2 to see your Windows partition.

Note: I edited you post to put the RESULTS.txt within "code" tags to make the format more forum-friendly. You can do this by pressing the "#" symbol in the post's menu, which will generate the **[noparse]```

```[/noparse]** tags. You paste the content between the two tags.

---

### Post by scientistshrey on 2010-06-26
This is what I got :

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb5
mount: /dev/sdb5 already mounted or /media/566e88fb-8b2b-46eb-9c88-6492ca3b495b busy
mount: according to mtab, /dev/sdb5 is already mounted on /media/566e88fb-8b2b-46eb-9c88-6492ca3b495b
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /mnt//boot: Not found or not a block device.

```

---

### Post by drs305 on 2010-06-26
Run these commands:
```

sudo umount /dev/sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
My mistake - I think part of the command got dropped. I've corrected the previous post and added the command to unmount /dev/sdb5 first in case it is mounted elsewhere.

---

### Post by darkod on 2010-06-26
When you boot the live mode DON'T mount /dev/sdb5, the ubuntu partition. Don't look for it in Places, don't click on it, anything.

Restart, go into live mode again, open terminal and just run those commands. Don't mount anything.

---

### Post by scientistshrey on 2010-06-26
```

ubuntu@ubuntu:~$ sudo umount /dev/sdb5
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb


```

---

### Post by scientistshrey on 2010-06-26
What to do now ??

---

### Post by drs305 on 2010-06-26
That looks correct. You should be able to reboot into Ubuntu after removing the LiveCD. If Grub doesn't see your Windows install, run:
```
sudo update-grub
```

If your system is still broken, please boot the LiveCD and rerun the boot info script.

---

### Post by scientistshrey on 2010-06-26
Thanks for your help.
I'll reboot and see the response

---

### Post by scientistshrey on 2010-06-26
It's still giving the same response on reboot i.e.  GRUB rescue>

Here is the new boot info script :

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,402,047   102,195,200   7 HPFS/NTFS
/dev/sda3         102,402,048   204,802,047   102,400,000   7 HPFS/NTFS
/dev/sda4         204,802,048   312,580,095   107,778,048   f W95 Ext d (LBA)
/dev/sda5         204,804,096   312,579,759   107,775,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6CA6BCF0A6BCBBC0                       ntfs                                     
/dev/sda2        08BAC5F8BAC5E274                       ntfs                                     
/dev/sda3        382C65AE2C656838                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9A4478E94478CA11                       ntfs       Local Disk                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by drs305 on 2010-06-26
The results still show Grub2 installed in sda5 instead of sdb5 and the results don't even show sdb this time, which is where your Linux installation should have been.

It's possible the drives are mounting differently in the LiveCD, so reboot the LiveCD and run the following command to find out what your Linux partition is. The "-l" is a lowercase L.
```
sudo fdisk -l
```
Your Linux partitions should  look like the following, **but check the drive and partition designations**.
> /dev/**sdb5 **        353,814,528   614,037,503   260,222,976  83 Linux
/dev/sdb6         614,039,552   625,141,759    11,102,208  82 Linux swap / Solaris

Once you have determined the correct partition and the drive which contains your Ubuntu installation, rerun the installation commands with the correct information.

---

### Post by scientistshrey on 2010-06-26
@drs305

I have an external hard disk which i removed after the first trial. Maybe that's why the result didn't show sdb.
After reconnecting it, here's the new result :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,402,047   102,195,200   7 HPFS/NTFS
/dev/sda3         102,402,048   204,802,047   102,400,000   7 HPFS/NTFS
/dev/sda4         204,802,048   312,580,095   107,778,048   f W95 Ext d (LBA)
/dev/sda5         204,804,096   312,579,759   107,775,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   353,814,427   353,812,380   7 HPFS/NTFS
/dev/sdb2         353,814,526   625,141,759   271,327,234   5 Extended
/dev/sdb5         353,814,528   614,037,503   260,222,976  83 Linux
/dev/sdb6         614,039,552   625,141,759    11,102,208  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6CA6BCF0A6BCBBC0                       ntfs                                     
/dev/sda2        08BAC5F8BAC5E274                       ntfs                                     
/dev/sda3        382C65AE2C656838                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9A4478E94478CA11                       ntfs       Local Disk                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0420E2B520E2AD3C                       ntfs       Shrey's Disk                  
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        566e88fb-8b2b-46eb-9c88-6492ca3b495b   ext4                                     
/dev/sdb6        f92bfea5-0c23-459f-8b9e-fd06435ce1d2   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/566e88fb-8b2b-46eb-9c88-6492ca3b495b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/Shrey's Disk      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
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
search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 566e88fb-8b2b-46eb-9c88-6492ca3b495b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8a6a95a66a958f95
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
# / was on /dev/sdb5 during installation
UUID=566e88fb-8b2b-46eb-9c88-6492ca3b495b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f92bfea5-0c23-459f-8b9e-fd06435ce1d2 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 286.5GB: boot/grub/core.img
 278.0GB: boot/grub/grub.cfg
 286.5GB: boot/grub/stage2
 286.5GB: boot/initrd.img-2.6.32-21-generic
 286.5GB: boot/vmlinuz-2.6.32-21-generic
 286.5GB: initrd.img
 286.5GB: vmlinuz
```And if the linux partitions are installed on the external hard disk, i would like to remove them from there too !!

And here is the latest result for the code :```
 sudo fdisk -l 
```:-->

```
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6375    51097600    7  HPFS/NTFS
/dev/sda3            6375       12749    51200000    7  HPFS/NTFS
/dev/sda4           12749       19458    53889024    f  W95 Ext'd (LBA)
/dev/sda5           12749       19458    53887832    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0019dca7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       22024   176906190    7  HPFS/NTFS
/dev/sdb2           22024       38914   135663617    5  Extended
/dev/sdb5           22024       38223   130111488   83  Linux
/dev/sdb6           38223       38914     5551104   82  Linux swap / Solaris
 
```

---

### Post by drs305 on 2010-06-26
scientistshrey,

If you don't want the Linux on the external drive, the best thing for you to do at this point is disconnect the drive and reinstall Ubuntu on the original drive. To do this however you will need to create a partition for the installation (/) and a swap partition. The Ubuntu installer can do this for you but the results as to how large and where Ubuntu takes the space from can be different than what you desire. You can let the installer make the determination for you if you wish but just carefully review how it is going to repartition your drive before committing to the process.

Also, *sdb* has Grub legacy installed on it now. Are you using a 10.04 LiveCD? If you use an older one, such as Hardy, it would not install Grub 2 via the method we have been using. It could be a bug in the boot info script as well, since it appears only parts of an old Grub legacy install exist in sdb5.

---

### Post by darkod on 2010-06-26
> **scientistshrey said:**
> @drs305

I have an external hard disk

And when were you going to tell us that? :)

You need to decide what you want to do. You currently have grub2 installed on your int hdd but the ubuntu partition with the necessary config files is on the ext hdd. So you will not be able to boot anything without the ext hdd connected.
If you do wish to boot windows directly without the ext hdd, you need to unplug it, boot the computer with the 10.04 in live mode and execute:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

After the first command there will be warning messages, ignore them. Restart without the cd and that should load windows directly.

Once that is done, again boot with the ubuntu cd in live mode but this time with the ext hdd connected, run:

sudo fdisk -l

to confirm your windows hdd is still sda and the ext hdd is still sdb, and if it is so, execute:

sudo umount /dev/sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Then restart and try to boot from the ext usb hdd, you should see grub2 working. If you boot from your int hdd, it will go straight to windows.

---

### Post by scientistshrey on 2010-06-26
@darkod

First of all, thnx a lot buddy !! It is after a tense whole day that my windows started working again.

After putting in all those codes, my system's now booting windows only, without the ubuntu live cd in and with/without the ext hdd attached.

So, now I want to erase any remaining parts of ubuntu n grub left  in the system, which I want to know from u how to do.

Also I want to install ubuntu only as application inside windows. The feasibilty for which I want to know from u as i havent used it before...

And i've also deleted the linux dedicated partitions in the ext hdd..

---

### Post by darkod on 2010-06-26
If you deleted the linux partitions on the ext hdd, there is nothing more to remove. As you already noticed, grub2 is gone from your int hdd and you can boot windows fine. So there is nothing to remove.

It's strange you say it boots windows directly even with the ext hdd connected, it shouldn't. You have tried to select to boot from the usb hdd at start, right? You know you have to do that if wanting to boot from a usb hdd?

You can try wubi, no problem. But actually the way you tried it, is the correct one. Only during the ubuntu install, in the last screen, click the Advanced button and tell it to install grub2 to /dev/sdb, not /dev/sda. That created the whole mess, if you can call it that. :)

And again, you will have to select to boot from the usb hdd if you want that to work.

---

### Post by scientistshrey on 2010-06-26
Please enlighten me more about this sda and sdb or direct me to any post or external link concerning these topics.

---

### Post by darkod on 2010-06-26
> **scientistshrey said:**
> Please enlighten me more about this sda and sdb or direct me to any post or external link concerning these topics.

[https://help.ubuntu.com/9.10/installation-guide/sparc/device-names.html](https://help.ubuntu.com/9.10/installation-guide/sparc/device-names.html)

NOTE: These days IDE disks also get named /dev/sdX and not /dev/hdX.

Usually sda would be your internal hdd and we want to leave the MBR alone. sdb would be your usb hdd. You will see the disk names in step 4 when selecting where to install.

By clicking the Advanced button in the last screen, you make sure to install the bootloader (grub2) to /dev/sdb and can boot it later by selecting to boot from USB-HDD, not HDD.

---

### Post by scientistshrey on 2010-06-26
I think i get it a bit now.
But what about 'MBR' ?

---

### Post by darkod on 2010-06-26
> **scientistshrey said:**
> I think i get it a bit now.
But what about 'MBR' ?

Master Boot Record. The first cylinder of all hdds. When it says only /dev/sdb it means the MBR. If it says /dev/sdb1, that's the first partition on disk sdb. You almost never want the bootloader onto a partition.

---

### Post by varunendra on 2010-06-26
> **darkod said:**
> And when were you going to tell us that? :)

:lolflag::lolflag:...........LOL..........  :lolflag::lolflag:

Yeah, I know......... it's not a support answer. But.....................:lolflag::lolflag::lolflag::lolflag:

---

