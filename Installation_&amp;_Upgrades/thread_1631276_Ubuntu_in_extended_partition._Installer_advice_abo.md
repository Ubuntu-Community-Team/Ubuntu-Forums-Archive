---
title: "Ubuntu in extended partition. Installer advice about boot flag (but finished install)"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by whitewolf573 on 2010-11-26
I have installed Ubuntu in a extended partition, and the installer, when i am in the partitioning part , when i try to make the root partition bootable , i can't , it says that if i sure that i want to make it bootable , because says that from a logical partition is not possible to boot (i think says only with certain bios),i say yes, but the parition hasn't the bootable flag nor in the installer nor in gparted after the first boot.

I installed grub in the mbr.

My fdisk -lu of my hdd is :

mulder@Quantico:~$ sudo fdisk -lu /dev/sda

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00050d90

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048    20983807    10490880   82  Linux swap / Solaris
/dev/sda2        20983808  1312831487   645923840   8e  Linux LVM
/dev/sda3      1312831488  1522556927   104862720    7  HPFS/NTFS
/dev/sda4      1522558974  1953523711   215482369    5  Extendida
/dev/sda5      1522558976  1522763775      102400   83  Linux
/dev/sda6      1522765824  1575204863    26219520   83  Linux
/dev/sda7      1576030208  1953523711   188746752    7  HPFS/NTFS

/dev/sda6 is my ubuntu root , i have no home,nor swap activated (that sda1 swap`is for use with CentOS 5.5 that i want to install inside lvm , and have a ubuntu installation outside for recovering and like , so i don't need more.


I have discovered that the not used swap has a boot flag xd . ¿ Can i chang it to the /dev/sda6 logical partition (root partition) or should be a primary  one ?


Could i have any problem because having ubuntu / in a logical partition with no outside /boot ?


I could format hdd , and put the swap inside lvm so be able to have ubuntu / as primary.


And only have Centos /boot and a ntfs data partition (i suppose for data a logical ntfs partition is allowed by windows 7 (installed in /dev/sdb))  in the extended one.


Linux can boot from a boot partition inside a extended partition , i mean , having / and /home inside lvm and /boot as logical partition , will be able to boot ?


This is because my intention is to have ubuntu outside lvm,with grub2 in mbr , and chainload to the centos grub that would be in /dev/sda5, a logical partition.


I have used the alternate x86_64 ubuntu cd.

---

### Post by Quackers on 2010-11-26
Only Windows uses boot flags. Your boot flag shows as being on sda1, which is now a swap partition. I would imagine that it should be on sda3 or sda7, looking at the output you posted. It would depend whether sda1 was originally Windows 7's boot partition or not. Windows may not boot now.

Please boot from the Ubuntu Live cd and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by whitewolf573 on 2010-11-26
the hard disk hadn't got any partition prior yesterday, well had windows, but i have some viruses and i used dd to zero out the drive, and then partitioning to install ubuntu and CentOS.

/dev/sda1 is a swap partition for centOS , that i have not used it (and in gparted is not mounted), as i don't know if is good to share swap between both.

Windows 7 , i will install it later in a SSD , that will be sdb (using the 128 Gb for windows only) , and chainload to the bootloader in his mbr.

The ntfs partitions , /dev/sda7 and /dev/sda3 are one for save windows data , and one scratch for photoshop respectively.

/dev/sda5 is a ext3 partition to mount the CentOS /boot.
 
This is what haves RESULTS.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    20,983,807    20,981,760  82 Linux swap / Solaris
/dev/sda2          20,983,808 1,312,831,487 1,291,847,680  8e Linux LVM
/dev/sda3       1,312,831,488 1,522,556,927   209,725,440   7 HPFS/NTFS
/dev/sda4       1,522,558,974 1,953,523,711   430,964,738   5 Extended
/dev/sda5       1,522,558,976 1,522,763,775       204,800  83 Linux
/dev/sda6       1,522,765,824 1,575,204,863    52,439,040  83 Linux
/dev/sda7       1,576,030,208 1,953,523,711   377,493,504   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        cbe080eb-eb8d-4e04-bffb-8a28879431f3   swap       swap                          
/dev/sda2        PYUdeI-PY3r-3FH1-K4oK-7djj-B5gS-bdyytT LVM2_member                               
/dev/sda3        402DA3A1379CE065                       ntfs       scratch                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d89d8e46-0060-4218-9553-bb4539228b3f   ext3       bootctos                      
/dev/sda6        31ceecab-3d94-478b-bb14-1220e209494a   ext4       ubuntu                        
/dev/sda7        63029D5C2918706F                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 31ceecab-3d94-478b-bb14-1220e209494a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 31ceecab-3d94-478b-bb14-1220e209494a
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 31ceecab-3d94-478b-bb14-1220e209494a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=31ceecab-3d94-478b-bb14-1220e209494a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 31ceecab-3d94-478b-bb14-1220e209494a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=31ceecab-3d94-478b-bb14-1220e209494a ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 31ceecab-3d94-478b-bb14-1220e209494a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 31ceecab-3d94-478b-bb14-1220e209494a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=31ceecab-3d94-478b-bb14-1220e209494a /               ext4    errors=remount-ro 0       1

=================== sda6: Location of files loaded by Grub: ===================


 797.2GB: boot/grub/core.img
 784.2GB: boot/grub/grub.cfg
 780.3GB: boot/initrd.img-2.6.35-22-generic
 797.1GB: boot/vmlinuz-2.6.35-22-generic
 780.3GB: initrd.img
 797.1GB: vmlinuz

```

---

### Post by oldfred on 2010-11-26
As Quackers mentioned windows uses a boot flag and grub does not. But some BIOS will not let you boot unless you have a boot flag on a primary partition. Windows has to boot from a primary partition. 

You can share a swap and normally installs find the swap and automatically use it. The only time it may be an issue is if you tried to hibernate in one system and then boot another as then swap would get overwritten. It looks like Ubuntu did not see the swap as your fstab does not show it. You can run without swap if you have lots of memory but it is better to have a smaller 2GB swap even with lots of memory.

It looks like grub2 osprober did not find the Centos install. Not sure if it normally does or not. Have you tried this when booted into Ubuntu and after you install windows on another drive you will have to run this:

sudo update-grub

---

