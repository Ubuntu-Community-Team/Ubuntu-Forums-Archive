---
title: "Ubuntu &amp; WinXP, Dual boot problem after upgrade"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by ArnoldoT on 2010-06-28
Hello there, 

I apologize if this question its been answered before, I couldn't find the answer by doing a search on the forum.

Ok, so... here is the situation that got me here.

I had a perfectly working dual system working,** Windows XP Media Center Edition** and** Ubuntu** (originally installed via wabi). But, one day my Ubuntu said there was important updates so, I decided to update Ubuntu; really bad idea on my case!

Nothing worked after that, my **Windows XP wouldn't run, nor my Ubuntu.**

So, with lack of sobriety and excess interest on having my laptop back, I decided to get the new version of **Ubuntu (10.04**), which I really like, much better than 9.0 that I had originally. I installed via LiveCD and everything was easier than using Wubi.

Here are the problems I have now...


[LIST]
[*]Since I originally installed **Ubuntu via Wubi**, I now have two Ubuntu installations, which makes me wonder if thats why I can't run Windows (Original Ubuntu installation reported problems during installation, failed to install and computer stop registering any OS. - I only had the grub thing and the prompt)
[*]Even though I do see** Windows NT and Windows XP** listed on the grub, I can't access either one of them, if I do chose one of them, the computer just lags for about 10 minutes then it shuts down.
[*]I don't have the **Windows XP recovery disk** so, I can't re-install Windows.
[/LIST]
Please note that, if I was able to run all my software from Ubuntu, I would forget about Windows all together but,** I can seem to figure out how to run Adobe CS4 on Ubuntu, even with Wine** (not even with the liquid one! hehe) Even though I have a lot of information on Windows I wouldn't mind having to manual recover each file but, I need to be able to run the software I have.

I know there should be something I can do, someone told me to use** Windows Bootloader** instead of Ubuntu's grub but, I can't figure out how to do that.

I really need to get this thing going ASAP, I have work to do on Adobe CS4 and I can't use it via Ubuntu!

Please help...

---

### Post by bcbc on 2010-06-28
Please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Instructions in link.

---

### Post by ArnoldoT on 2010-06-28
bcbc:

Thanks for your fast reply. I did what you told me and here are the results:





```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 270400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 270400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 270400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda3 has 71858108 sectors.. But according to the info 
                       from the partition table , it has 71858744 sectors.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/home.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 270400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
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
    Boot files/dirs:   /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2          10,233,405   102,285,854    92,052,450   c W95 FAT32 (LBA)
/dev/sda3    *    102,285,855   174,144,599    71,858,745   c W95 FAT32 (LBA)
/dev/sda4         174,145,534   195,371,007    21,225,474   5 Extended
/dev/sda5         174,145,536   194,369,535    20,224,000  83 Linux
/dev/sda6         194,371,584   195,371,007       999,424  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   523,004,975   523,004,913   c W95 FAT32 (LBA)
/dev/sdb2         523,005,950   625,141,759   102,135,810   5 Extended
/dev/sdb5         523,005,952   620,873,727    97,867,776  83 Linux
/dev/sdb6         620,875,776   625,141,759     4,265,984  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       17bfb25d-bb5d-444d-be97-b390861eb84b   ext4                                     
/dev/sda1        16D9-B5D2                              vfat       PQSERVICE                     
/dev/sda2        9739-40A3                              vfat       ACER                          
/dev/sda3        A919-98F8                              vfat       ACERDATA                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        79db78d3-54d7-476c-beeb-1244c4f7c4c1   ext4                                     
/dev/sda6        60008d1e-7be0-46e8-8b80-4975b0214fdb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        39D8-62EF                              vfat       My Book                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ca29a787-2536-4504-a1d9-992d418c8ef6   ext4                                     
/dev/sdb6        51d5175e-0cb6-478e-a519-84cd2975e92f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb5        /media/ca29a787-2536-4504-a1d9-992d418c8ef6 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer 
C:\wubildr.mbr = "Ubuntu" 

======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod fat
set root='(hd0,3)'
search --no-floppy --fs-uuid --set a919-98f8
loopback loop0 /ubuntu/disks/usr.disk
set root=(loop0)
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod fat
set root='(hd0,3)'
search --no-floppy --fs-uuid --set a919-98f8
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a919-98f8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 16d9-b5d2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 9739-40a3
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/home.disk /home           ext4    loop            0       2
/host/ubuntu/disks/usr.disk /usr            ext4    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


    .1GB: boot/grub/core.img
   3.0GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.31-14-generic
    .9GB: boot/initrd.img-2.6.31-16-generic
   1.5GB: boot/initrd.img-2.6.31-17-generic
   1.5GB: boot/initrd.img-2.6.31-19-generic
   1.3GB: boot/initrd.img-2.6.31-20-generic
   3.0GB: boot/initrd.img-2.6.31-22-generic
   3.2GB: boot/initrd.img-2.6.32-22-generic
    .4GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-16-generic
   1.1GB: boot/vmlinuz-2.6.31-17-generic
    .8GB: boot/vmlinuz-2.6.31-19-generic
   1.0GB: boot/vmlinuz-2.6.31-20-generic
   1.7GB: boot/vmlinuz-2.6.31-22-generic
   2.8GB: boot/vmlinuz-2.6.32-22-generic
   3.2GB: initrd.img
   3.0GB: initrd.img.old
   2.8GB: vmlinuz
   1.7GB: vmlinuz.old

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 16d9-b5d2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 9739-40a3
    drivemap -s (hd0) ${root}
    chainloader +1
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=60008d1e-7be0-46e8-8b80-4975b0214fdb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  91.4GB: boot/grub/core.img
  98.3GB: boot/grub/grub.cfg
  91.7GB: boot/initrd.img-2.6.32-21-generic
  90.3GB: boot/initrd.img-2.6.32-22-generic
  91.6GB: boot/vmlinuz-2.6.32-21-generic
  91.7GB: boot/vmlinuz-2.6.32-22-generic
  90.3GB: initrd.img
  91.7GB: initrd.img.old
  91.7GB: vmlinuz
  91.6GB: vmlinuz.old

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
UUID=ca29a787-2536-4504-a1d9-992d418c8ef6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=51d5175e-0cb6-478e-a519-84cd2975e92f none            swap    sw              0       0
```


I hope there is something I can do to get access to Windows XP, even though I am more than likely to use Ubuntu as my main Operating System

---

### Post by wilee-nilee on 2010-06-28
This is fixable with a quick look at the script, I think bcbc can help you better than myself and a couple of other regulars on the forum. You have grub in 3  partitions sda1, sda2, and sda3 this is a fairly easy fix it is whether lilo or a reload of the ms bootloader to the mbr is needed is where I'm not sure.:p

There are other anomalies as well but it is all still there it just needs a cleanup persons approach.

---

### Post by oldfred on 2010-06-28
You have managed to install grub everywhere. With wubi you have to have windows in the MBR and the windows boot in the partition boot sector.

Boot sector info:  Grub 2 is installed in the boot sector of sda3

You need a liveCD to run these commands. Or there are ways to use windows repairs from a windows CD. 

this should fix the boot sectors, it looks like your main windows is sda3 but you may want to run this also on sda1 & sda2:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)


Are you still using the wubi or just the install of Ubuntu in sda5, your grub in sdb is not correct and looks like it came from the wubi install of grub showing partition 256.

---

### Post by warfacegod on 2010-06-28
> So, with lack of sobriety...

&

```
even with Wine (not even with the liquid one!
```

Just my two cents. I've been down that road with computers. It's never a good idea. And it's never pretty in the morning. Vodka, computers, and I don't mix. Unless I'm playing Death Metal then all bets are off.

---

### Post by ArnoldoT on 2010-06-28
oldFred:
Well, I guess now I am an experienced Ubuntu Installer, right? Because I do have it all over the place according to that file...

Ok, Yes, I did use Wubi the first time I installed Ubuntu, it was not until the upgrade from version 9 to version 10 that everything stop working and thats when I used an Ubuntu LiveCD to install it once again, thats how I am here.

I do have the Ubuntu LiveCD
I do not have Windows install CD

---

### Post by wilee-nilee on 2010-06-28
> **ArnoldoT said:**
> oldFred:
Well, I guess now I am an experienced Ubuntu Installer, right? Because I do have it all over the place according to that file...

Ok, Yes, I did use Wubi the first time I installed Ubuntu, it was not until the upgrade from version 9 to version 10 that everything stop working and thats when I used an Ubuntu LiveCD to install it once again, thats how I am here.

I do have the Ubuntu LiveCD
I do not have Windows install CD

Follow oldfreds advice and here is a W7 recovery ISO link if needed.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by oldfred on 2010-06-28
If you can boot into your install in sda5 then you can run the commands from that. I thought initially with wubi you might not have the liveCD.

I have not been into the wine (liquid kind) tonight. That was several days ago. I really nailed answers that night.  Of course everyone else, including me the next day, wondered what I was suggesting.:smile:

---

### Post by wilee-nilee on 2010-06-28
> **oldfred said:**
> If you can boot into your install in sda5 then you can run the commands from that. I thought initially with wubi you might not have the liveCD.

I have not been into the wine (liquid kind) tonight. That was several days ago. I really nailed answers that night.  Of course everyone else, including me the next day, wondered what I was suggesting.:smile:

I noticed you seemed a little off your game on one day, but hey who am I to talk.:-\"

---

### Post by ArnoldoT on 2010-06-29
Ok..

So, first of all... Thanks!
I am now able to load Windows XP properly so I went ahead and uninstalled the first version of Ubuntu [The one installed via Wabi].

I still get the prompt screen asking about which OS to run, giving Windows XP and Ubuntu as options. Please note, this is the second screen asking for this info, once I click Windows XP on my grub, I am taken to the screen that used to pop-up with Wubi Ubuntu.

But hey, being able to log in to Windows XP is a big step so, thanks!

I ran the boot info thing again, just in case you guys want to give me another tip on how to correct the current problem... [wink]

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 270400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 270400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda3 has 71858108 sectors.. But according to the info 
                       from the partition table , it has 71858744 sectors.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 270400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
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
    Boot files/dirs:   /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2          10,233,405   102,285,854    92,052,450   c W95 FAT32 (LBA)
/dev/sda3    *    102,285,855   174,144,599    71,858,745   c W95 FAT32 (LBA)
/dev/sda4         174,145,534   195,371,007    21,225,474   5 Extended
/dev/sda5         174,145,536   194,369,535    20,224,000  83 Linux
/dev/sda6         194,371,584   195,371,007       999,424  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   523,004,975   523,004,913   c W95 FAT32 (LBA)
/dev/sdb2         523,005,950   625,141,759   102,135,810   5 Extended
/dev/sdb5         523,005,952   620,873,727    97,867,776  83 Linux
/dev/sdb6         620,875,776   625,141,759     4,265,984  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        16D9-B5D2                              vfat       PQSERVICE                     
/dev/sda2        9739-40A3                              vfat       ACER                          
/dev/sda3        A919-98F8                              vfat       ACERDATA                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        79db78d3-54d7-476c-beeb-1244c4f7c4c1   ext4                                     
/dev/sda6        60008d1e-7be0-46e8-8b80-4975b0214fdb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        39D8-62EF                              vfat       My Book                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ca29a787-2536-4504-a1d9-992d418c8ef6   ext4                                     
/dev/sdb6        51d5175e-0cb6-478e-a519-84cd2975e92f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb5        /media/ca29a787-2536-4504-a1d9-992d418c8ef6 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer 
C:\wubildr.mbr = "Ubuntu" 

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 79db78d3-54d7-476c-beeb-1244c4f7c4c1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 16d9-b5d2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 9739-40a3
    drivemap -s (hd0) ${root}
    chainloader +1
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=79db78d3-54d7-476c-beeb-1244c4f7c4c1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=60008d1e-7be0-46e8-8b80-4975b0214fdb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  91.4GB: boot/grub/core.img
  98.3GB: boot/grub/grub.cfg
  91.7GB: boot/initrd.img-2.6.32-21-generic
  90.3GB: boot/initrd.img-2.6.32-22-generic
  91.6GB: boot/vmlinuz-2.6.32-21-generic
  91.7GB: boot/vmlinuz-2.6.32-22-generic
  90.3GB: initrd.img
  91.7GB: initrd.img.old
  91.7GB: vmlinuz
  91.6GB: vmlinuz.old

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
UUID=ca29a787-2536-4504-a1d9-992d418c8ef6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=51d5175e-0cb6-478e-a519-84cd2975e92f none            swap    sw              0       0
```

---

### Post by bcbc on 2010-06-29
Great that everything is working again. 

You can get rid of the 'extra' windows boot menu by editing the c:\boot.ini file - remove the wubildr line at the bottom.

Also, you might want to repair the bootsector on /dev/sda1 - it's looks like a diagnostic partition. You can use testdisk for this. I don't know if you'll ever use it, but - it's there. 

Finally, the boot flag is set on /dev/sda3. This isn't a problem now as you're booting with grub, but if you ever switch back to the windows bootloader, it will try and boot this partition. You should set it back to /dev/sda2.

---

### Post by ArnoldoT on 2010-07-26
Running out of space on disk!

Sorry for the long delay replying to the thread, I've been working 18hr shifts almost everyday and I have not had much time to work on my laptop.

Anyway,  since I've done a lot of partitions and moving and all that, I think I managed to screw something up. The problem is that I am not able to edit partition sizes now, I tried via windows and via ubuntu... nothing seems to work. :(

I know I have quite some free GB of space on my HD but, since I partitioned the disk in order to install Ubuntu I think I did it twice...

Any ideas of what can be done??

---

### Post by oldfred on 2010-07-26
Have you changed since last list from boot script? Then you had an install on sda and linux partitions on sdb that did not look complete.

Mount (click on each in places left panel)any extra partitions you have and run this which shows only mounted partitions.

df
```

fred@fred-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc5            100790004   6957316  88712776   8% /
udev                   2028592       344   2028248   1% /dev
none                   2028592       200   2028392   1% /dev/shm
none                   2028592       292   2028300   1% /var/run
none                   2028592         0   2028592   0% /var/lock
none                   2028592         0   2028592   0% /lib/init/rw
/dev/sda1             57665280  36255008  21410272  63% /media/cdrive
/dev/sdc8             51174096  23343408  27830688  46% /media/gdrive
/dev/sda4             20472848  19377968   1094880  95% /media/share
/dev/sda2             76912416  44268116  28737296  61% /media/backup
/dev/sdc6            100790004  54647648  41022444  58% /usr/local/fred/data
/dev/sdc9             28588924   1337480  25799172   5% /home
/dev/sdc2            104446596  22277708  82168888  22% /home/fred/shared
/dev/sdd1              1972496    179456   1793040  10% /media/WIN7 Repair
/dev/sr0                145228    145228         0 100% /media/cdrom0
fred@fred-desktop:~$ 



```

---

### Post by wilee-nilee on 2010-07-26
n

---

### Post by ArnoldoT on 2010-07-26
Mmhh, well, did have not done much since I fixed (with your help) my boot file.

> Mount (click on each in places left panel)any extra partitions you have and run this which shows only mounted partitions.

Sorry... I don't know what that means. I really new to Ubuntu.

I hope you wanted me to type "df" into the terminal... (Is there an Ubuntu for dummies? - haha)

If so, here are the results...

```

arnoldo@arnoldo-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              9953120   3963860   5483660  42% /
none                   1155324       324   1155000   1% /dev
none                   1159536       204   1159332   1% /dev/shm
none                   1159536       192   1159344   1% /var/run
none                   1159536         0   1159536   0% /var/lock
none                   1159536         0   1159536   0% /lib/init/rw
/dev/sdb1            261438560 230145056  31293504  89% /media/My Book
/dev/sda2             46014944  39335392   6679552  86% /media/ACER
/dev/sda3             35920224  13926272  21993952  39% /media/ACERDATA
arnoldo@arnoldo-laptop:~$ 
```

---

### Post by oldfred on 2010-07-26
Your partition sdb1 is at 89% or 230GB, but your root is only 42%. So where are you running out of space or is it just time to buy a new larger drive to store all your stuff?

---

### Post by ArnoldoT on 2010-07-26
230 GB?

My laptop came with a 100 GB, HDD.
I do have an external HDD (My Book)
I don't understand why is listed on sdb1, though

Where am I running out of space?
Honestly, I have no idea.
Sometimes when I start Ubuntu it says something like "you need to free some space, delete temporary files and empty trash bin", or something like that.

computer:///100%20GB%20Hard%20Disk.drive
computer:///100%20GB%20Hard%20Disk-1.drive
computer:///320%20GB%20Hard%20Disk.drive
computer:///CD%5CDVD%20Drive.drive
computer:///root.link

That's what I see when I browse "My Computer"
However, I don't understand why it says that my ACER drive is 100 GB, and my ACERDATA is 100 GB too. There is only one hard drive although it was partitioned from factory, its capacity is 100 GB, not 200. Maybe I am reading/interpreting that data wrong but, I thought I would post it and see what you think.

Since the last Ubuntu upgrade, my "My Book" (External HDD, 320 GB) keeps mounting and unmounting itself for some reason, could that be the reason why I am having problems with the "free space"?

---

### Post by oldfred on 2010-07-26
That listing shows the drive size and then the partition size within the drive. So the ACER is in the 100 and the ACERDATA is in the 100. It does not total 200.

You can update

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Recover Lost Disk Space 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by wblack on 2010-07-27
Thanks for the tip oldfed. I was having a similar problem where I couldn't boot to my XP partition after upgrading to Ubuntu 10.4. The link to the the SourceForge Boot Problems wiki fixed the problem. Now why do I need my Windows partition agian?....Oh ya, Netflix and Matlab.

---

