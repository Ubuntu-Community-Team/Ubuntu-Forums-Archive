---
title: "Fix Grub in Windows 7 dual boot with Ubuntu"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by windrider42 on 2011-08-14
I have Ubuntu 11.04 installed and dual boot with Windows 7. I had some problems at one time and when i reninstalled linux, I made sure only the Windows 7 hdd and the Linux hdd were attached.

I want to remove the extra Windows 7 bootloaders. When I am in Windows 7, only one bootloader shows in BCDedit, yet in linux it shows as below.

I have Windows 7 installed on /dev/sdb 750GB hdd, and LInux on dev/sdd 320GB hdd.

I have no issues booting at all, just would like to clean the grub loader up and remove the extra Windows 7 bootloader as I only have the one Windows 7 OS installed.

I am fairly new to Linux and not quite sure how to go about it.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid bf15729b-8ec6-4576-9997-775336e431d7 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 369442944 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2    *        206,848 1,465,145,343 1,464,938,496   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   599,740,415   599,738,368  83 Linux
/dev/sdd2         599,742,462   625,141,759    25,399,298   5 Extended
/dev/sdd5         599,742,464   625,141,759    25,399,296  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63 1,953,525,167 1,953,525,105   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/ramzswap0                                          swap       
/dev/sda1        28A66940A669101C                       ntfs       New Volume
/dev/sdb1        2AD0FE99D0FE6A89                       ntfs       System Reserved
/dev/sdb2        84B006E4B006DD14                       ntfs       
/dev/sdc1        6A40E8CA40E89E57                       ntfs       New Volume
/dev/sdd1        bf15729b-8ec6-4576-9997-775336e431d7   ext4       
/dev/sdd5        0ea8b813-1357-4d02-9701-6d23c4359749   swap       
/dev/sde1        34E897E5E897A3A0                       ntfs       NEW
/dev/sdf1        7426349026345578                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="2"
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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

### BEGIN /etc/grub.d/09_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 28A66940A669101C
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 2AD0FE99D0FE6A89
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 84B006E4B006DD14
    chainloader +1
}
### END /etc/grub.d/09_os-prober ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro  vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro  vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro  vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro  vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0ea8b813-1357-4d02-9701-6d23c4359749 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.135238647 = 21.620047872   boot/grub/core.img                             1
  28.327804565 = 30.416748544   boot/grub/grub.cfg                             1
  46.891601562 = 50.349473792   boot/initrd.img-2.6.35-25-generic              3
  46.878219604 = 50.335105024   boot/initrd.img-2.6.35-28-generic              2
  46.660163879 = 50.100969472   boot/initrd.img-2.6.38-10-generic              3
  47.003875732 = 50.470027264   boot/initrd.img-2.6.38-8-generic               2
  20.133293152 = 21.617958912   boot/vmlinuz-2.6.35-25-generic                 1
   1.868164062 = 2.005925888    boot/vmlinuz-2.6.35-28-generic                 2
  47.727851868 = 51.247390720   boot/vmlinuz-2.6.38-10-generic                 2
   7.212223053 = 7.744065536    boot/vmlinuz-2.6.38-8-generic                  1
  46.660163879 = 50.100969472   initrd.img                                     3
  47.003875732 = 50.470027264   initrd.img.old                                 2
  47.727851868 = 51.247390720   vmlinuz                                        2
   7.212223053 = 7.744065536    vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by YesWeCan on 2011-08-14
Which drive does your bios boot from when you use Windows? The 1TB sda?

I suppose you would want to boot the 750GB sdb directly to get to Windows 7 on the same disk, then you free up the 1TB sda. You need a standard MBR code on sdb to boot sdb2 directly.

You have Grub installed to sdb rather than sdd where Ubuntu lives. I suspect that when you installed Ubuntu you only had the 320GB and 750GB drives connected and the Ubuntu installer defaulted to putting Grub on the 750GB Windows drive. So you probably want Grub on the 320GB sdd.

There is a boot partition sdb1 that has been corrupted by having Grub installed to it. Hopefully, sdb2 will boot directly and not require either sda1 or sdb1.

So if I have got that right, my recommendation would be:

a) Install Grub to the MBR of the 320GB sdd disk.
Boot Ubuntu
sudo grub-install /dev/sdd

b) Put a standard MBR in sdb.
sudo apt-get install lilo (ignore warnings)
sudo lilo -M /dev/sdb mbr

c) Set bios to boot sdb. Check W7 boots.
If it does, you do not need sda. You also do not need partition sdb1. Use W7 to delete/change any Windows partitions on sdb and sda.

If it does not boot then it gets a little tricker. It will still boot via sda, of course. Come back for advice.

d) Set bios to boot sdd. Check Ubuntu still boots.
Run sudo update-grub to add Windows to the Grub menu.

---

### Post by oldfred on 2011-08-14
Not sure what your issue is. I see MBRs with windows boot loaders but that code is not used unless you select that drive in BIOS to boot. No need to try to erase it and about the only way to delete is with dd which is also dangerous to use unless you are absolutely sure what your are doing.

I would install the grub2 boot loader to sdd the 320GB drive. I prefer to have to boot loader on the same drive as system install. Then each drive will work on its own.

Your windows may not work because of this:

```
sdb1: ________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    [COLOR=Red]Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 369442944 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.[/COLOR]
    Operating System:  
    Boot files:        /bootmgr [COLOR=Blue]/boot/bcd /boot/BCD[/COLOR]


```Windows partitions have to have Windows boot code in the windows partition. windows keeps a backp boot sector that you usually can restore.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Secto]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

You also have this which you cannot have two identical folders, but I cannot tell which is the valid one:
/boot/bcd /boot/BCD

To install grub2's boot loader to sdd. Boot into Ubuntu:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdd"  then just run:
sudo grub-install /dev/sdd
#If that returns any errors run:
sudo grub-install --recheck /dev/sdd
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by windrider42 on 2011-08-14
Thank you YesWeCan and oldfred for both your answers. I had my BIOS set to boot the 750GB hdd. 
 
Ok I think I have got it the way it should be now
 
```
                  Boot Info Script 0.60    from 17 May 2011
 
 
============================= Boot Info Summary: ===============================
 
 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
 
    ---------------------------------------------------------------------------
    search.fs_uuid bf15729b-8ec6-4576-9997-775336e431d7 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/sdf.
 
sda1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sdb1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sdb2: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
 
sdc1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sdd1: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
sdd2: __________________________________________________________________________
 
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
 
sdd5: __________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
 
sde1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sdf1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS
 
 
Drive: sdb _____________________________________________________________________
 
Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdb1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2    *        206,848 1,465,145,343 1,464,938,496   7 NTFS / exFAT / HPFS
 
 
Drive: sdc _____________________________________________________________________
 
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdc1               2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS
 
 
Drive: sdd _____________________________________________________________________
 
Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdd1               2,048   599,740,415   599,738,368  83 Linux
/dev/sdd2         599,742,462   625,141,759    25,399,298   5 Extended
/dev/sdd5         599,742,464   625,141,759    25,399,296  82 Linux swap / Solaris
 
 
Drive: sde _____________________________________________________________________
 
Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sde1                  63 1,953,525,167 1,953,525,105   7 NTFS / exFAT / HPFS
 
 
Drive: sdf _____________________________________________________________________
 
Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdf1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/ramzswap0                                          swap       
/dev/sda1        28A66940A669101C                       ntfs       New Volume
/dev/sdb1        2AD0FE99D0FE6A89                       ntfs       System Reserved
/dev/sdb2        84B006E4B006DD14                       ntfs       
/dev/sdc1        6A40E8CA40E89E57                       ntfs       New Volume
/dev/sdd1        bf15729b-8ec6-4576-9997-775336e431d7   ext4       
/dev/sdd5        0ea8b813-1357-4d02-9701-6d23c4359749   swap       
/dev/sde1        34E897E5E897A3A0                       ntfs       NEW
/dev/sdf1        7426349026345578                       ntfs       New Volume
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/sdd1        /                        ext4       (rw,errors=remount-ro,commit=0)
 
 
=========================== sdd1/boot/grub/grub.cfg: ===========================
 
--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}
 
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
 
### BEGIN /etc/grub.d/09_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 84B006E4B006DD14
    chainloader +1
}
### END /etc/grub.d/09_os-prober ###
 
### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro vga=769   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single vga=769 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro vga=769   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single vga=769 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro vga=769   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single vga=769 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro vga=769   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=bf15729b-8ec6-4576-9997-775336e431d7 ro single vga=769 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root bf15729b-8ec6-4576-9997-775336e431d7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------
 
=============================== sdd1/etc/fstab: ================================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0ea8b813-1357-4d02-9701-6d23c4359749 none            swap    sw              0       0
--------------------------------------------------------------------------------
 
=================== sdd1: Location of files loaded by Grub: ====================
 
           GiB - GB             File                                 Fragment(s)
 
  20.264934540 = 21.759307776   boot/grub/core.img                             1
  12.340843201 = 13.250879488   boot/grub/grub.cfg                             1
  46.891601562 = 50.349473792   boot/initrd.img-2.6.35-25-generic              3
  46.878219604 = 50.335105024   boot/initrd.img-2.6.35-28-generic              2
  46.660163879 = 50.100969472   boot/initrd.img-2.6.38-10-generic              3
  47.003875732 = 50.470027264   boot/initrd.img-2.6.38-8-generic               2
  20.133293152 = 21.617958912   boot/vmlinuz-2.6.35-25-generic                 1
   1.868164062 = 2.005925888    boot/vmlinuz-2.6.35-28-generic                 2
  47.727851868 = 51.247390720   boot/vmlinuz-2.6.38-10-generic                 2
   7.212223053 = 7.744065536    boot/vmlinuz-2.6.38-8-generic                  1
  46.660163879 = 50.100969472   initrd.img                                     3
  47.003875732 = 50.470027264   initrd.img.old                                 2
  47.727851868 = 51.247390720   vmlinuz                                        2
   7.212223053 = 7.744065536    vmlinuz.old                                    1
 
=============================== StdErr Messages: ===============================
 
unlzma: Decoder error
unlzma: Decoder error

```
 
I now have the BIOS set too boot the 320GB hdd with the linux installed on it. I am able to now boot into both linux and Windows 7 with what I want showing in Grub2
Thank you both for your help

---

### Post by oldfred on 2011-08-15
It looks like the os-prober should be able to find your windows and add it to your menu. Have you tried.
```

sudo update-grub
```

You may want to houseclean out older kernels, Best to keep current & one older that you know works:

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Since you have a lot of larger hard drives, you might want to review this:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

