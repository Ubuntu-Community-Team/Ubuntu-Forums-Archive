---
title: "Another noob with Dual boot issues"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by No1Daemon on 2011-01-31
Hi all

First time posting here and first time using Linux.

I like the look of Linux and it seems pretty easy to use although I seem to have a steep learning curve but nothing I cant handle.

I recently bought a second hand laptop for a cnc project and I have installed Ubuntu 10.0.4 which comes preloaded with EMC2

I first installed Ubuntu 10.0.4 on the whole drive and attempted to use vurtualbox and vmware to run windows 7 inside it.

These steps failed as 
1. Virtualbox does not support parallel ports which I require
2. VMware would not install windows in the virtual window, it kept hanging the pc. After spending more than a day on each googling and trying to get them working I decided to dual boot instead.

I followed the guide here [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) and followed all the steps except for setting up the shared folder properties

I had many issues trying to install windows 7 again as the installer wouldn't find a disc but through a combination of hirens boot cd tools and gparted off the live cd I managed to get it to install.

So windows 7 was installed to the drive first successfully, I then shrank the partition from inside windows and then ran the live cd and created a storage partition and a second partition for the ubuntu 10.0.4 install.

I then installed ubuntu to the partition I had created and it went fine.

When I rebooted it just came up to a grub prompt like this Grub>

I have googled and tried to solve this problem myself. I followed the steps in the reinstalling grub2 guide on these forums and it seems to install fine but it doesn't work. It always comes back to the same grub prompt

I have downloaded the boot script and here is the results.

```

           Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    24,782,847    24,576,000   7 HPFS/NTFS
/dev/sda3          24,796,800    54,093,674    29,296,875   7 HPFS/NTFS
/dev/sda4          54,093,822    78,139,391    24,045,570   5 Extended
/dev/sda5          57,653,248    78,139,391    20,486,144  83 Linux
/dev/sda6          54,093,824    57,653,247     3,559,424  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2002 MB, 2002780160 bytes
16 heads, 63 sectors/track, 3880 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,911,679     3,911,617   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F8F412F3F412B43A                       ntfs       System Reserved               
/dev/sda2        144816154815F668                       ntfs                                     
/dev/sda3        15FCB9FD39F15926                       ntfs       Storage                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8907c5a1-7006-43af-9a9c-26727e09c8f0   ext4                                     
/dev/sda6        20b55470-00d1-4425-8738-f03cc50ecd6e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        581D-4ABA                              vfat       NEW VOLUME                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 8907c5a1-7006-43af-9a9c-26727e09c8f0
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
search --no-floppy --fs-uuid --set 8907c5a1-7006-43af-9a9c-26727e09c8f0
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
menuentry 'Ubuntu, with Linux 2.6.32-122-rtai' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8907c5a1-7006-43af-9a9c-26727e09c8f0
    linux    /boot/vmlinuz-2.6.32-122-rtai root=UUID=8907c5a1-7006-43af-9a9c-26727e09c8f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-122-rtai
}
menuentry 'Ubuntu, with Linux 2.6.32-122-rtai (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8907c5a1-7006-43af-9a9c-26727e09c8f0
    echo    'Loading Linux 2.6.32-122-rtai ...'
    linux    /boot/vmlinuz-2.6.32-122-rtai root=UUID=8907c5a1-7006-43af-9a9c-26727e09c8f0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-122-rtai
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8907c5a1-7006-43af-9a9c-26727e09c8f0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8907c5a1-7006-43af-9a9c-26727e09c8f0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'

```Any help would be appreciated.

I am currently typing this having loaded ubuntu in live mode again.

Thanks
Steve

---

### Post by No1Daemon on 2011-01-31
Hi again

I have solved my own issue. I reinstalled Ubuntu and this time just selected side by side and it has installed correctly.

Thanks for looking

---

