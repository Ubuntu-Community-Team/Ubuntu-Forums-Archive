---
title: "Cant boot after new install"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by Ojustaboo on 2010-06-28
Hi all, have just installed 10.04, from USB  (64 bit version)

I have two separate hard drives with windows 7 64 bit on them  (one which the op system is on, other data files are on)  but installed this to a 3rd drive.

Everything appeared to go fine, but on reboot, the post BIOS screen hangs just after seeing if there's a CD ROM to boot from ( in other words, it cant find any boot loader info, ift fails at the point it used to start booting windows 7)

I've tried selecting all 3 hard drives to boot from, but same thing happens, it simply hangs and I don't get the option top boot to either operating system?

Any suggestions please?

thanks

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 168080576 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
135 heads, 14 sectors/track, 775211 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             14       206,009       205,996   7 HPFS/NTFS
/dev/sda2             206,010 1,048,577,669 1,048,371,660   7 HPFS/NTFS
/dev/sda3       1,048,578,048 1,465,143,295   416,565,248   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,429,266,431 1,429,264,384  83 Linux
/dev/sdb2       1,429,268,478 1,465,147,391    35,878,914   5 Extended
/dev/sdb5       1,429,268,480 1,465,147,391    35,878,912  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   964,184,063   964,182,016   7 HPFS/NTFS
/dev/sdc2         964,186,112   976,766,975    12,580,864   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2048 MB, 2048901120 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4001760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     4,001,759     4,001,697   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7E1876311875E913                       ntfs       System Reserved               
/dev/sda2        86607B04607AFA6F                       ntfs                                     
/dev/sda3        B602C42602C3E987                       ntfs       Misc                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        235861f9-7db7-40c7-9521-d7bb009ef6b3   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2aea3e86-5f90-469a-a1b3-df72af9e503b   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4E6CF1AB6CF18DC9                       ntfs       Data                          
/dev/sdc2        B03EB06E3EB02F6A                       ntfs       Email                         
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        46E7-F597                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 235861f9-7db7-40c7-9521-d7bb009ef6b3
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 235861f9-7db7-40c7-9521-d7bb009ef6b3
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 235861f9-7db7-40c7-9521-d7bb009ef6b3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=235861f9-7db7-40c7-9521-d7bb009ef6b3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 235861f9-7db7-40c7-9521-d7bb009ef6b3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=235861f9-7db7-40c7-9521-d7bb009ef6b3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 235861f9-7db7-40c7-9521-d7bb009ef6b3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 235861f9-7db7-40c7-9521-d7bb009ef6b3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7e1876311875e913
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=235861f9-7db7-40c7-9521-d7bb009ef6b3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=2aea3e86-5f90-469a-a1b3-df72af9e503b none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  86.0GB: boot/grub/core.img
  86.0GB: boot/grub/grub.cfg
  86.0GB: boot/initrd.img-2.6.32-21-generic
  86.0GB: boot/vmlinuz-2.6.32-21-generic
  86.0GB: initrd.img
  86.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf 

```

---

### Post by darkod on 2010-06-28
=> Grub 2 is installed in the MBR of /dev/sda and looks at sector  168080576 
    of the same hard drive for core.img, but core.img can not be found  at this 
    location.

Out of what ever reason, grub2 is looking for it's files at the wrong place.

You might use this situation to install grub2 to the MBR of sdb, where your ubuntu is. From live mode do:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Obviously set sdb as first hdd to boot from, the second 750GB disk. It should work out OK.

---

### Post by Yarui on 2010-06-28
Have you tried unplugging either the Ubuntu hard drive or the Windows drives to see if they boot when the other OS isn't present?  If Ubuntu doesn't boot even when the Windows drives aren't connected then you need to fix your grub setup.  If it does boot up then the grub and the windows boot loader must not be getting along.

---

### Post by Ojustaboo on 2010-06-28
> **darkod said:**
> => Grub 2 is installed in the MBR of /dev/sda and looks at sector  168080576 
    of the same hard drive for core.img, but core.img can not be found  at this 
    location.

Out of what ever reason, grub2 is looking for it's files at the wrong place.

You might use this situation to install grub2 to the MBR of sdb, where your ubuntu is. From live mode do:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Obviously set sdb as first hdd to boot from, the second 750GB disk. It should work out OK.


Many many many thanks.

That worked perfectly (typing this from my newly booted ubuntu :)  )

---

