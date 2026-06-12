---
title: "New Dell PC will not boot from 500 GB USB"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by efflandt on 2010-07-08
Just got a new Dell Studio XPS desktop SX8100-1408NBC with i5 cpu and nVidia GT220 video and everything seems to work out of the box (including wireless) with 64-bit 10.04 live iso on USB.  In fact the startup guide primarily for Win7 mentions: "**Set Up Unbuntu** To set up Ubuntu for the first time, follow the instructions on the screen."

However, it seems to be unable to boot an installed system on a 500 GB USB WD Passport.  It drops to grub rescue with **error: unknown filesystem** (it is ext3), and grub rescue seems to give that error for all partitions.  I did have that issue with an HP PC from 2004, but that USB drive boots fine on a Dell Inspiron 6400 work laptop from around 2006 and my Toshiba laptop from same time period.  In fact I booted the USB drive on the 6400 while out of town last week.

The new PC came with a 1 TB drive, so any clue why it will not boot from a 500 GB drive?  Following is RESULTS.txt when the drive was connected after booting from flash.  The 4 vacant drives are a built-in card reader.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdf
 => Grub 2 is installed in the MBR of /dev/sdg and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    24,743,935    24,662,016   7 HPFS/NTFS
/dev/sda3          24,743,936 1,953,521,663 1,928,777,728   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63     7,855,784     7,855,722   b W95 FAT32


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   869,855,489   869,855,427   7 HPFS/NTFS
/dev/sdg2         869,855,490   874,353,689     4,498,200  82 Linux swap / Solaris
/dev/sdg3    *    874,353,690   976,768,064   102,414,375  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       abbe33ad-5f8d-4f7d-8478-171ad88a46b6   ext3                                     
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        423C50023C4FEF89                       ntfs       RECOVERY                      
/dev/sda3        88985264985250B4                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdf1        9FE7-21BF                              vfat       LUCID                         
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        481C6AFD1C6AE582                       ntfs       WD Passport                   
/dev/sdg2        e49e71a4-d1f2-4564-a9ca-be370e04a691   swap                                     
/dev/sdg3        041864cb-1c12-4537-849e-032fe103b8d1   ext3                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/WD Passport       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdg3        /media/041864cb-1c12-4537-849e-032fe103b8d1 ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdg3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
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
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=041864cb-1c12-4537-849e-032fe103b8d1 ro partman/alignment=cylinder radeon.modeset=0  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=041864cb-1c12-4537-849e-032fe103b8d1 ro single partman/alignment=cylinder radeon.modeset=0
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=041864cb-1c12-4537-849e-032fe103b8d1 ro partman/alignment=cylinder radeon.modeset=0  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=041864cb-1c12-4537-849e-032fe103b8d1 ro single partman/alignment=cylinder radeon.modeset=0
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 041864cb-1c12-4537-849e-032fe103b8d1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdg3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
UUID=041864cb-1c12-4537-849e-032fe103b8d1 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=b82de8c8-fb6d-47a1-bdff-997b0e00f28a none            swap    sw              0       0
# swap was on /dev/sdc2 during installation
UUID=e49e71a4-d1f2-4564-a9ca-be370e04a691 none            swap    sw              0       0

=================== sdg3: Location of files loaded by Grub: ===================


 453.3GB: boot/grub/core.img
 453.3GB: boot/grub/grub.cfg
 453.4GB: boot/initrd.img-2.6.32-21-generic
 453.3GB: boot/initrd.img-2.6.32-22-generic
 453.4GB: boot/vmlinuz-2.6.32-21-generic
 453.3GB: boot/vmlinuz-2.6.32-22-generic
 453.3GB: initrd.img
 453.4GB: initrd.img.old
 453.3GB: vmlinuz
 453.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde
```

---

### Post by WinRiddance on 2010-07-08
You're aware of the fact that Ubuntu 10.04 uses ext4 by default, right?
The switch was introduced as an option with Karmic, then finalized for Lucid.
Perhaps that's where some of the issues are coming from if you're using ext3 file system?

---

### Post by oldfred on 2010-07-08
With multiple drives I have had some of the same issues. I thought the search with a UUID overrides the set root but it did not on my USB install.

Your:
set root='(hd1,3)'

I default boot karmic from sdc and have lucid's grub in sda but I have to set root to hd1 not hd0 to chainload to sda. It seems that the boot drive becomes hd0 and then the remaining drives are in order. I would test all the alternatives but hd2,3 may be the choice.  You can easily test from the grub menu with the e edit command.

Once booted run the sudo update-grub and see if it renumbers it or not.

---

### Post by efflandt on 2010-07-09
The issue is not that it is ext3.  That is more mature and stable and certainly supported by Linux and grub for some time.

And I know that the drive you boot from becomes (hd0), but that is where the search for UUID comes into play.  The fact that 2 other different laptops can boot from the 500 GB drive indicates that the drive is not bad.  A Dell Inspiron 1545 that I had temporarily also booted 64-bit 9.10 from the same partition on the 500 GB.

The **partition/alignment=cylinder** boot parameter is because my old desktop would not even boot a 160 GB USB drive with the new 10.04 partition alignment.

So the 500 GB drive boots on several laptops (including Dell) dating back to 2006, but fails to boot on my 2004 HP PC and brand new Dell desktop.  But a 160 GB WD Passport w/64-bit 10.04 boots fine on all of them.  This is RESULTS.txt for the 160 GB drive booted on the new PC:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    24,743,935    24,662,016   7 HPFS/NTFS
/dev/sda3          24,743,936 1,953,521,663 1,928,777,728   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   218,371,544   218,371,482   c W95 FAT32 (LBA)
/dev/sdf2    *    218,371,545   308,078,504    89,706,960  83 Linux
/dev/sdf3         308,078,505   312,576,704     4,498,200  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        423C50023C4FEF89                       ntfs       RECOVERY                      
/dev/sda3        88985264985250B4                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdf1        4B1A-02BD                              vfat       WD Passport                   
/dev/sdf2        432030cc-906f-4678-a9bd-9975ef3047c2   ext3                                     
/dev/sdf3        d77f4ee6-429b-4cfa-bf2d-ddebf11c6983   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdf2        /                        ext3       (rw,errors=remount-ro)
/dev/sdf1        /media/WD Passport       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdf2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=432030cc-906f-4678-a9bd-9975ef3047c2 ro radeon.modeset=0 partman/alignment=cylinder  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=432030cc-906f-4678-a9bd-9975ef3047c2 ro single radeon.modeset=0 partman/alignment=cylinder
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=432030cc-906f-4678-a9bd-9975ef3047c2 ro radeon.modeset=0 partman/alignment=cylinder  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=432030cc-906f-4678-a9bd-9975ef3047c2 ro single radeon.modeset=0 partman/alignment=cylinder
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 432030cc-906f-4678-a9bd-9975ef3047c2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=432030cc-906f-4678-a9bd-9975ef3047c2 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70789c50-0fab-48c6-9879-4670012084ec none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=d77f4ee6-429b-4cfa-bf2d-ddebf11c6983 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdf2: Location of files loaded by Grub: ===================


 118.8GB: boot/grub/core.img
 118.8GB: boot/grub/grub.cfg
 118.8GB: boot/initrd.img-2.6.32-22-generic
 118.9GB: boot/initrd.img-2.6.32-23-generic
 118.8GB: boot/vmlinuz-2.6.32-22-generic
 118.8GB: boot/vmlinuz-2.6.32-23-generic
 118.9GB: initrd.img
 118.8GB: initrd.img.old
 118.8GB: vmlinuz
 118.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde
```

---

### Post by oldfred on 2010-07-09
If you unplug the card reader does it boot. That may be just enough to confuse grub on device numbers. Yes the search should work, but in my case on a USB flash it did not.

---

### Post by efflandt on 2010-07-09
I would have to open the computer to unplug the multi-card reader.  But that makes no difference from the view of grub because that is not necessary to boot the 160 GB drive from any of the computers.  And "grub rescue" from the 500 GB drive or grub prompt from the 160 GB drive sees the USB boot drive as (hd0) because I can tell from the list of partitions (hd0,3) (hd0,2) (hd0,1) which drive is which.

But grub from the 160 GB drive can **ls** ext3 or fat32 partitions on itself or ext3 or ntfs on internal drive.  Or if grub 1.98 is booted from internal drive on old PC [in which case the USB drive already connected during boot is (hd1)] can likewise **ls** partitions on the 160 GB USB or 200 GB internal drive.  But on those 2 PC's, grub rescue on the 500 GB drive cannot read any partitions on the 500 GB drive.  And grub prompt from internal drive of old PC can **ls** the ntfs partition on the 500 GB drive, but not the ext3 partition out about 453 MB (error: unknown filesystem).  As I mentioned, the 500 GB USB boots fine on other computers.

The new Dell PC seems to have a faulty DVD writer in Win7 (replacement on the way), so I cannot back up its system that way, but as soon as I have a chance to image its 1 TB drive to USB, I will see if Ubuntu can boot from that 1 TB internal drive.  That will be a new experience because Windows says that drive is using Raid.

PS: 64-bit Lucid boots fine way out on a 1 TB internal drive, on the new PC, with Win7 mbr and grub 1.98 on sda4.  So it is still a mystery why it will not boot from the 500 GB USB drive.

```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    24,743,935    24,662,016   7 HPFS/NTFS
/dev/sda3          24,743,936 1,748,721,663 1,723,977,728   7 HPFS/NTFS
/dev/sda4    *  1,748,723,445 1,953,520,064   204,796,620  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        423C50023C4FEF89                       ntfs       RECOVERY                      
/dev/sda3        88985264985250B4                       ntfs       OS                            
/dev/sda4        f2d7ada5-a6a9-4836-83cd-4cfc27ce360d   ext3       LUCID64                       
/dev/sda: PTTYPE="dos"
```
=================== sda4: Location of files loaded by Grub: ===================


 962.6GB: boot/grub/core.img
 962.6GB: boot/grub/grub.cfg
 962.7GB: boot/initrd.img-2.6.32-21-generic
 962.6GB: boot/initrd.img-2.6.32-23-generic
 962.6GB: boot/vmlinuz-2.6.32-21-generic
 962.6GB: boot/vmlinuz-2.6.32-23-generic
 962.6GB: initrd.img
 962.7GB: initrd.img.old
 962.6GB: vmlinuz
 962.6GB: vmlinuz.old

---

