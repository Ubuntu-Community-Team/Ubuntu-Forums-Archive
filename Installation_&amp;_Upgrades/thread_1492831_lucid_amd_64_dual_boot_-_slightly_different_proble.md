---
title: "lucid amd 64 dual boot - slightly different problem?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by welshchap on 2010-05-25
Hi All,

another xp / lucid dual boot issue here 

I'm aware of , and have fixed several different lucid dual boot issues on other machines by:

* booting from the install cd , 
* installing grub
* mounting the /dev/sda parition 
* chrooting to the disk 
* updating grub
* reboot

but this particular case has me stumped ! :(

I can "see" the problem - just don't know how to fix it.

scenario is as follows.

[pre-installl]

XP 32 bit on C: (/dev/sda1 now) NTFS
DVD-RW on D:
NTFS formatted data only disk as E: (retro-fitted post xp installl)  

[during install]

shrunk the NTFS partition of C:  to create a few gb of space on /dev/sda1

installed amd64 lucid desktop into space created as follows (all sizes approximate) 

XP partition still /dev/sda1 (shrunk but otherwise unchanged )
10gb as "/" in /dev/sda2
8gb as "/home" in /dev/sda3
2gb as swap in /dev/sda4
no files written to /dev/sdb 

watched grub install itself to /dev/sda

reboot 

[post-install]

grub config reports linux and boots fine

Windows XP on /dev/sda1 but doesnt' boot.


ran the bootinfo script... here's the apparent issue 

```

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

```somehow something has pointed my windows install to /dev/sdb ?? ...where it isnt !!

furthermore  /dev/sdb has never had windows installed upon it !! it was  formatted as an NTFS disk and fitted into the machine some 4-5 months AFTER the original XP install and almost a year before Lucid was installed .

logic suggests that I need to re-point <something>  but what and where ??

any ideas please ?

(Full bootinfo log below) 

regards

WelshChap

```



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   115,346,699   115,346,637   7 HPFS/NTFS
/dev/sda2         115,346,700   135,829,574    20,482,875  83 Linux
/dev/sda3         135,829,575   152,199,809    16,370,235  83 Linux
/dev/sda4         152,199,810   156,296,384     4,096,575  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        62F95E257116E30E                       ntfs       SYSTEM                        
/dev/sda2        4c2234c9-71de-4fa0-a5b6-c7933ba39ea5   ext4                                     
/dev/sda3        909042ca-3465-4f77-9e59-8cd4b932b390   ext4                                     
/dev/sda4        7969720d-e88a-4eb9-a86c-bba52db8f660   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6C40990D4098DEE0                       ntfs       DATA                          
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /home                    ext4       (rw)
/dev/sr0         /media/XP_PRO_SP2        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 62f95e257116e30e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=909042ca-3465-4f77-9e59-8cd4b932b390 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=7969720d-e88a-4eb9-a86c-bba52db8f660 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  61.5GB: boot/grub/core.img
  67.7GB: boot/grub/grub.cfg
  62.0GB: boot/initrd.img-2.6.32-21-generic
  62.4GB: boot/initrd.img-2.6.32-22-generic
  62.3GB: boot/vmlinuz-2.6.32-21-generic
  59.4GB: boot/vmlinuz-2.6.32-22-generic
  62.4GB: initrd.img
  62.0GB: initrd.img.old
  59.4GB: vmlinuz
  62.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 


```

---

### Post by darkod on 2010-05-25
This is not your problem:

Windows is installed in the MBR of /dev/sdb

It doesn't actually mean windows OS is installed on /dev/sdb, it means /dev/sdb has windows type MBR, which is true.

However, this looks like your problem:

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    [COLOR=Red]Boot files/dirs:   /ntldr /NTDETECT.COM[/COLOR]

The boot.ini is missing.

---

### Post by welshchap on 2010-05-25
thanks darkod! 

However, boot.ini IS on the root of /dev/sda1 :

```

[contents of boot.ini]

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```

I'll compare the command line in another machine - lord alone knows how that happened ???


regards

WelshChap

---

### Post by welshchap on 2010-05-25
damn!

every other machine in the house thats dual boot capable is still running grub 1

is there a syntax guide anywhere ? {googles for it}

regards

WelshChap

---

### Post by darkod on 2010-05-25
The results file you posted looks fine, with the exception that boot.ini is not shown. I wonder why, the script is usually very good at detecting boot files.

---

### Post by welshchap on 2010-05-25
even weirder ...

just re-ran the script after no system changes and 
boot.ini is there again now 
```

                Boot Info Script 0.55    dated February 15th, 2010             $

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

```

ran a sudo grub-install /dev/sda after this ....then rebooted 

XP pro still not booting 

as at least one parameter has evidently changed ???  I'll repost the latest boot info script output :

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   115,346,699   115,346,637   7 HPFS/NTFS
/dev/sda2         115,346,700   135,829,574    20,482,875  83 Linux
/dev/sda3         135,829,575   152,199,809    16,370,235  83 Linux
/dev/sda4         152,199,810   156,296,384     4,096,575  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        62F95E257116E30E                       ntfs       SYSTEM                        
/dev/sda2        4c2234c9-71de-4fa0-a5b6-c7933ba39ea5   ext4                                     
/dev/sda3        909042ca-3465-4f77-9e59-8cd4b932b390   ext4                                     
/dev/sda4        7969720d-e88a-4eb9-a86c-bba52db8f660   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6C40990D4098DEE0                       ntfs       DATA                          
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /home                    ext4       (rw)
/dev/sr0         /media/XP_PRO_SP2        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c2234c9-71de-4fa0-a5b6-c7933ba39ea5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 62f95e257116e30e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=4c2234c9-71de-4fa0-a5b6-c7933ba39ea5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=909042ca-3465-4f77-9e59-8cd4b932b390 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=7969720d-e88a-4eb9-a86c-bba52db8f660 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  61.5GB: boot/grub/core.img
  67.7GB: boot/grub/grub.cfg
  62.0GB: boot/initrd.img-2.6.32-21-generic
  62.4GB: boot/initrd.img-2.6.32-22-generic
  62.3GB: boot/vmlinuz-2.6.32-21-generic
  59.4GB: boot/vmlinuz-2.6.32-22-generic
  62.4GB: initrd.img
  62.0GB: initrd.img.old
  59.4GB: vmlinuz
  62.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 


regards

WelshChap

---

### Post by darkod on 2010-05-25
Did you boot XP few times after the shrink so it can run its disk checks, and before installing ubuntu? Maybe something got corrupted during the shrink and you don't even know it.

I suggest running chkdsk from the XP cd in Recovery Console or similar, but don't remember exact commands right now.

Also from ubuntu you can force a chkdsk on next XP boot with:

sudo apt-get install ntfsprogs (if you don't already have it installed)
sudo ntfsfix /dev/sda1

It can't really fix a lot, but it will set some flag to run chkdsk next time you try to boot XP. So just reboot and select XP in the menu. Hopefully it works.

---

### Post by welshchap on 2010-05-25
> **darkod said:**
> Did you boot XP few times after the shrink so it can run its disk checks, and before installing ubuntu? 


yes - everything was fine 100%

> 
Maybe something got corrupted during the shrink and you don't even know it.
I suggest running chkdsk from the XP cd in Recovery Console or similar, but don't remember exact commands right now.


chkdisk ran and is completely clean 

> 
Also from ubuntu you can force a chkdsk on next XP boot with:
sudo apt-get install ntfsprogs (if you don't already have it installed)
sudo ntfsfix /dev/sda1

It can't really fix a lot, but it will set some flag to run chkdsk next time you try to boot XP. So just reboot and select XP in the menu. Hopefully it works.
[/quote]

Thanks - I'll give it a try, but I don't even get as far as loading XP - just a flashing underscore symbol in the top right hand of the screen :(

---

### Post by welshchap on 2010-05-26
ntfsfix /dev/sda1 did its bit (after I remembered to umount /dev/sda1 (blush)

however no change in my xp boot situation regrettably

regards


WelshChap

---

### Post by darkod on 2010-05-26
> **welshchap said:**
> ntfsfix /dev/sda1 did its bit (after I remembered to umount /dev/sda1 (blush)

however no change in my xp boot situation regrettably

regards


WelshChap

Hmmm... stop using XP??? :)

Sorry, I have no new ideas.

---

### Post by welshchap on 2010-05-27
if only I could...

when Wine / crossover pro  supports COM ports properly maybe I can ? 

I live in the hope that one day it will happen <sigh>

gracias para todo! 

un abrazo de

WelshChap

---

