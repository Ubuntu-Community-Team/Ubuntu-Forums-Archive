---
title: "how regenerate grub.cfg for only one, specified hdd?"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by froff on 2011-06-27
Hello all
I have copied my system to new hdd. Now I would like to generate new grub.cfg file with grub-mkconfig but the file should contain _only_ entries for this new hdd. When I try to do this normally it generates entries for both bootable disk (current and new) but for the new one there is no memtest entries.
I would like to generate exactly the same entries as I have for the current disk but referencing to partition(s) on the new one. 
Should I do it manually? Isn't there any automated method?

And the second one:
I'm suprised that there is no "grub" program with its own simple shell when grub2 is installed. Is it replaced by sth? 

best regards

Now I can see that additional entries generated for new hdd have root set to the old one - it is complete nonsense :(

```

menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdb3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 6a26581f-084b-42e4-89dc-71b464b6b29c
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}

```

uuid 6a2... - partition on the new disk
uuid 415... - partition on the current disk

---

### Post by oldfred on 2011-06-27
Did you do a full partition copy with dd or gparted and not copy just the files to partitions created in advance. Then you may have duplicate UUIDs.
You are booting from the new drive but using the old as / (root).

Post this so we can see entire configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by froff on 2011-06-27
> **oldfred said:**
> Did you do a full partition copy with dd or gparted and not copy just the files to partitions created in advance. Then you may have duplicate UUIDs.


No I used rsync. uuids are different (look at supplement to first post)

> 
You are booting from the new drive but using the old as / (root).
Yes - I know that. This configuration file is wrong. When I simply copied my old grub.cfg and replaced old uuid by new uuid everything looks to be ok, system boots from new hdd and root is on the new hdd. But I'm afraid that os prober  (/etc/grub.d/30_os-prober) will destroy my configuration. I would like to have two stable, separated grub.cfg-s on both disks without _any_ entries concerning disk B in file belonging to disk A and vice versa.

> 
Post this so we can see entire configuration.
 Ok after reboot i'll place here my output in situation, after boot from old hdd with root on old hdd, but in my opinion problem lays on grub configuration scripts (grub-mkconfig and probably os-prober) and grub.cfg file, not on boot sectors configuration.
Grub is properly instaled on new disk's mbr and old disk is dual booted from windows mbr.

---

### Post by froff on 2011-06-27
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /linux.bin looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location. Grub 
                       Legacy (v) in the file /linux.bin.grub1_097.2011-06-19 
                       looks at sector 404101263 of the same hard drive for 
                       the stage2 file, but no stage2 files can be found at 
                       this location. Grub Legacy (v) in the file 
                       /linux.bin.old1 looks at sector 473122049 of the same 
                       hard drive for the stage2 file, but no stage2 files 
                       can be found at this location. Grub Legacy (v) in the 
                       file /linux.bin.old2 looks at sector 481502433 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location. Grub2 
                       (v1.97-1.98) in the file /mbr_grub.bin looks at sector 
                       1 of the same hard drive for core.img, but core.img 
                       can not be found at this location.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 81931563. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v) is installed in the boot sector of 
                       sda8 and looks at sector 404101263 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 0x4c28ef39
    Boot sector info:   Syslinux looks at sector 565280 of /dev/sdc1 for its 
                       second stage. According to the info in the boot 
                       sector, sdc1 starts at sector 0. But according to the 
                       info from fdisk, sdc1 starts at sector 1.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    81,931,499    81,931,437   7 NTFS / exFAT / HPFS
/dev/sda2          81,931,500   490,223,474   408,291,975   f W95 Extended (LBA)
/dev/sda5          81,931,563    90,317,429     8,385,867   b W95 FAT32
/dev/sda6          90,317,493   362,940,479   272,622,987   7 NTFS / exFAT / HPFS
/dev/sda7         483,315,588   490,223,474     6,907,887  82 Linux swap / Solaris
/dev/sda8         362,940,543   483,315,524   120,374,982  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    81,922,047    81,920,000   7 NTFS / exFAT / HPFS
/dev/sdb2          81,922,048    90,114,047     8,192,000  82 Linux swap / Solaris
/dev/sdb3          90,124,650 1,953,520,064 1,863,395,415  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.1 GB, 16053960192 bytes
255 heads, 63 sectors/track, 1951 cylinders, total 31355391 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *              1    31,355,390    31,355,390  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F6E8D3BCE8D37977                       ntfs       C
/dev/sda5        8452-D600                              vfat       D
/dev/sda6        7EA88F5BA88F10B7                       ntfs       E
/dev/sda7        74cb58db-ec5d-408b-9761-6955ef24a3d2   swap       
/dev/sda8        415d9dc0-150c-404c-ba6f-704c40a71846   ext3       
/dev/sdb1        3B0B3F1A340E6C4F                       ntfs       
/dev/sdb2        aa86fbc8-2ad4-48a7-ae03-3b66e77e04f2   swap       
/dev/sdb3        6a26581f-084b-42e4-89dc-71b464b6b29c   ext4       
/dev/sdc1        3CE3-1678                              vfat       SYSRESC

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt/dysk_c              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /mnt/dysk_d              vfat       (rw,iocharset=utf8,umask=000)
/dev/sda6        /mnt/dysk_e              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/sdb1        /media/3B0B3F1A340E6C4F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/6a26581f-084b-42e4-89dc-71b464b6b29c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/SYSRESC           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=5 
default=C:\linux.bin 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\linux.bin="Ubuntu Linux" 
--------------------------------------------------------------------------------

=========================== sda8/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=415d9dc0-150c-404c-ba6f-704c40a71846

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.10, kernel 2.6.35-28-generic
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro quiet splash
initrd        /boot/initrd.img-2.6.35-28-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 10.10, kernel 2.6.35-25-generic
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro quiet splash
initrd        /boot/initrd.img-2.6.35-25-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, memtest86+
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1

--------------------------------------------------------------------------------

=========================== sda8/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
if loadfont /boot/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu Linux (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f6e8d3bce8d37977
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8 lub sdb8
# stary uudid przed resize: UUID=2d1108ce-6b4f-428f-8dfb-9664e87de82f

UUID=415d9dc0-150c-404c-ba6f-704c40a71846 /               ext3    relatime,errors=remount-ro     0       1

# /dev/sda7 lub sdb7
UUID=74cb58db-ec5d-408b-9761-6955ef24a3d2 none            swap    sw                      0       0

/dev/scd0               /media/cdrom0   auto users,noauto                 0       0

# /dev/sda1
UUID=F6E8D3BCE8D37977        /mnt/dysk_c    ntfs-3g    defaults,noauto                0    2

# /dev/sda5
# stary uuid przed resize: UUID=7C29-5990
UUID=8452-D600            /mnt/dysk_d    vfat iocharset=utf8,umask=000            0    2

# /dev/sda6
# stary uuid przed resize: UUID=640C9AB40C9A812A         
UUID=7EA88F5BA88F10B7         /mnt/dysk_e    ntfs-3g    defaults                    0    2

# WD80, parycja 1
UUID=C2A0A165A0A160A1        /mnt/wd80    ntfs-3g    rw,users,noauto                0    2

# samsung solid B2700
#UUID=3065-6539            /media/solid    vfat rw,users,iocharset=utf8,umask=000,noauto        0    2

# sandisk 16GB
#UUID=3CE3-1678            /media/sandisk    vfat rw,users,iocharset=utf8,umask=000,noauto        0    2

#adata ext3
#UUID=283746f9-574f-41bb-a26b-513a26d70788     /media/adata_ext3    ext3      rw,users,noauto        0       2

#adata fat32
#UUID=F3C3-8468            /media/adata_fat32    vfat rw,users,iocharset=utf8,umask=000        0    2

--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 192.812285900 = 207.030615552  boot/grub/core.img                             1
 192.790168285 = 207.006866944  boot/grub/grub.cfg                             1
 192.790198803 = 207.006899712  boot/grub/menu.lst                             1
 192.839385509 = 207.059713536  boot/initrd.img-2.6.35-25-generic             29
 193.173667431 = 207.418646016  boot/initrd.img-2.6.35-28-generic             32
 206.873404980 = 222.128627200  boot/vmlinuz-2.6.35-25-generic                47
 194.773803234 = 209.136778752  boot/vmlinuz-2.6.35-28-generic                 4
 193.173667431 = 207.418646016  initrd.img                                    32
 192.839385509 = 207.059713536  initrd.img.old                                29
 194.773803234 = 209.136778752  vmlinuz                                        4
 206.873404980 = 222.128627200  vmlinuz.old                                   47

=========================== sdb3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=415d9dc0-150c-404c-ba6f-704c40a71846

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.10, kernel 2.6.35-28-generic
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro quiet splash
initrd        /boot/initrd.img-2.6.35-28-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 10.10, kernel 2.6.35-25-generic
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro quiet splash
initrd        /boot/initrd.img-2.6.35-25-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, memtest86+
uuid        415d9dc0-150c-404c-ba6f-704c40a71846
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1

--------------------------------------------------------------------------------

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
if loadfont /boot/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=415d9dc0-150c-404c-ba6f-704c40a71846 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 415d9dc0-150c-404c-ba6f-704c40a71846
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu Linux (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f6e8d3bce8d37977
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# 3B0B3F1A340E6C4F                ntfs na nowym hitachi
# aa86fbc8-2ad4-48a7-ae03-3b66e77e04f2        swap na nowym hitachi
# 6a26581f-084b-42e4-89dc-71b464b6b29c        ext4 na nowym hitachi


UUID=6a26581f-084b-42e4-89dc-71b464b6b29c /               ext4    relatime,errors=remount-ro     0       1
UUID=aa86fbc8-2ad4-48a7-ae03-3b66e77e04f2 none            swap    sw                      0       0

# ext3 na starym:
UUID=415d9dc0-150c-404c-ba6f-704c40a71846 /mnt /old_ext3  ext3    defaults             0       2

/dev/scd0               /media/cdrom0   auto users,noauto                 0       0

# /dev/sda1
UUID=F6E8D3BCE8D37977        /mnt/dysk_c    ntfs-3g    defaults,noauto                0    2

# /dev/sda5
# stary uuid przed resize: UUID=7C29-5990
UUID=8452-D600            /mnt/dysk_d    vfat iocharset=utf8,umask=000            0    2

# /dev/sda6
# stary uuid przed resize: UUID=640C9AB40C9A812A         
UUID=7EA88F5BA88F10B7         /mnt/dysk_e    ntfs-3g    defaults                    0    2

# WD80, parycja 1
UUID=C2A0A165A0A160A1        /mnt/wd80    ntfs-3g    rw,users,noauto                0    2

--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 719.114758492 = 772.143592448  boot/grub/core.img                             1
 719.114789009 = 772.143625216  boot/grub/grub.cfg                             1
 719.114987373 = 772.143838208  boot/grub/menu.lst                             1
  43.115406990 = 46.294815744   boot/initrd.img-2.6.35-25-generic              2
  43.125672340 = 46.305838080   boot/initrd.img-2.6.35-28-generic              1
 719.110058784 = 772.138546176  boot/vmlinuz-2.6.35-25-generic                 1
 719.114106178 = 772.142892032  boot/vmlinuz-2.6.35-28-generic                 1
  43.125672340 = 46.305838080   initrd.img                                     1
  43.115406990 = 46.294815744   initrd.img.old                                 2
 719.114106178 = 772.142892032  vmlinuz                                        1
 719.110058784 = 772.138546176  vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
UI vesamenu.c32
F2 f2images.msg
F3 f3params.msg
F4 f4arun.msg
F5 f5troubl.msg
F6 f6pxe.msg
F7 f7net.msg

PROMPT 0
TIMEOUT 900
ONTIMEOUT rescuecd_std

MENU DEFAULT rescuecd_std
MENU TABMSG Press <TAB> to edit options or <F2>,<F3>,<F4>,<F5>,<F6>,<F7> for help
MENU TITLE SYSTEM-RESCUE-CD 1.5.8 (www.sysresccd.org)
MENU ROWS 16
MENU TIMEOUTROW 22
MENU TABMSGROW 24
MENU CMDLINEROW 24
MENU HELPMSGROW 26
MENU WIDTH 78
MENU MARGIN 6
MENU BACKGROUND #c00090f0

MENU color title    1;31;40    #FFFF0000 #00000000 std
MENU color sel      7;37;40    #FF000000 #FFC0C0C0 all
MENU color unsel    37;44      #FF000000 #00000000 none
MENU color hotsel   1;7;37;40  #FF000000 #FFC0C0C0 all
MENU color tabmsg   1;31;40    #FFFFFF00 #00000000 std
MENU color help     1;31;40    #FFFFFFFF #00000000 none

LABEL rescuecd_std
  MENU LABEL 1) SystemRescueCd: default boot options
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5
  TEXT HELP
  Boot standard 32bit kernel with default options (should always work)
  You should use this entry if you don't know which one to use
  ENDTEXT

LABEL rescuecd_docache
  MENU LABEL 2) SystemRescueCd: all files cached to memory (docache)
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 docache
  TEXT HELP
  Boot standard 32bit kernel and run system from RAM (cdrom can be removed)
  It requires 512 MB of memory to work and takes some time during the
  boot process, but the cdrom can be removed and system will be faster.
  ENDTEXT

LABEL rescuecd_791
  MENU LABEL 3) SystemRescueCd: console in high resolution (framebuffer)
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791
  TEXT HELP
  Boot standard 32bit kernel with console in high resolution
  This mode is useful only if you want to work in console mode
  ENDTEXT

LABEL rescuecd_us
  MENU LABEL 4) SystemRescueCd: do not ask for keyboard, use US keymap
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5
  TEXT HELP
  Boot standard 32bit kernel and use the keymap for american keyboards
  This way it will not prompt for the keymap during the boot process
  ENDTEXT

LABEL rescuecd_xorg
  MENU LABEL 5) SystemRescueCd: directly start the graphical environment
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 dostartx
  TEXT HELP
  Boot standard 32bit kernel and start the XFCE graphical environment
  directly. You can also get in this environment by typing "startx" from
  the console.
  ENDTEXT

LABEL rescue64_std
  MENU LABEL 6) SystemRescueCd: 64bit kernel with default options
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5
  TEXT HELP
  Boot standard 64bit kernel with default options (should work on 64bit CPU)
  A 64bit kernel is required if you want to execute 64bit programs or to 
  chroot to an existing 64bit Linux OS on the disk. It requires a 64bit CPU. 
  ENDTEXT

MENU SEPARATOR

# ------------------------------------------------------------------------------

MENU BEGIN
MENU TITLE A) Standard 32bit kernel (rescuecd) with more choice...

LABEL rescuecd_1
  MENU LABEL 1. SystemRescueCd with default options
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5
  TEXT HELP
  Boot standard 32bit kernel with default options (should always work)
  ENDTEXT

LABEL rescuecd_2
  MENU LABEL 2. SystemRescueCd with all files cached to memory
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 docache
  TEXT HELP
  Boot standard 32bit kernel and run system from memory.
  It requires 512 MB of memory to work and takes some time during the
  boot process, but the cdrom can be removed and system will be faster.
  ENDTEXT

LABEL rescuecd_3
  MENU LABEL 3. SystemRescueCd with console in high resolution (1024x768)
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791
  TEXT HELP
  Boot standard 32bit kernel with console in high resolution
  ENDTEXT

LABEL rescuecd_4
  MENU LABEL 4. SystemRescueCd with the default graphical environment
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 dostartx
  TEXT HELP
  Boot standard 32bit kernel and start the XFCE graphical environment
  directly. You can also get in this environment by typing "startx" from
  the console.
  ENDTEXT

LABEL rescuecd_5
  MENU LABEL 5. SystemRescueCd with VESA based graphical environment
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791 dostartx forcevesa
  TEXT HELP
  Boot standard 32bit kernel and use VESA based graphical environment
  Try this if you have problems to get the default graphical environment
  ENDTEXT

MENU SEPARATOR

LABEL return
  MENU LABEL Return to main menu
  MENU EXIT

MENU END

# ------------------------------------------------------------------------------

MENU BEGIN
MENU TITLE B) Standard 64bit kernel (rescue64) with more choice...

LABEL rescue64_1
  MENU LABEL 1. SystemRescueCd with default options
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5
  TEXT HELP
  Boot standard 64bit kernel with default options (should always work)
  ENDTEXT

LABEL rescue64_2
  MENU LABEL 2. SystemRescueCd with all files cached to memory
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 docache
  TEXT HELP
  Boot standard 64bit kernel and run system from RAM (cdrom can be removed)
  It requires 512 MB of memory to work and takes some time during the
  boot process, but the cdrom can be removed and system will be faster.
  ENDTEXT

LABEL rescue64_3
  MENU LABEL 3. SystemRescueCd with console in high resolution (1024x768)
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791
  TEXT HELP
  Boot standard 64bit kernel with console in high resolution
  ENDTEXT

LABEL rescue64_4
  MENU LABEL 4. SystemRescueCd with the default graphical environment
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 dostartx
  TEXT HELP
  Boot standard 64bit kernel and start the XFCE graphical environment
  directly. You can also get in this environment by typing "startx" from
  the console.
  ENDTEXT

LABEL rescue64_5
  MENU LABEL 5. SystemRescueCd with VESA based graphical environment
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791 dostartx forcevesa
  TEXT HELP
  Boot standard 64bit kernel and use VESA based graphical environment
  Try this if you have problems to get the default graphical environment
  ENDTEXT

MENU SEPARATOR

LABEL return
  MENU LABEL Return to main menu
  MENU EXIT

MENU END

# ------------------------------------------------------------------------------

MENU BEGIN
MENU TITLE C) Alternative 32bit kernel (altker32) with more choice...

LABEL altker32_1
  MENU LABEL 1. SystemRescueCd with default options
  LINUX altker32
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5
  TEXT HELP
  Boot alternative 32bit kernel with default options (should always work)
  ENDTEXT

LABEL altker32_2
  MENU LABEL 2. SystemRescueCd with all files cached to memory
  LINUX altker32
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 docache
  TEXT HELP
  Boot alternative 32bit kernel and run system from memory.
  It requires 512 MB of memory to work and takes some time during the
  boot process, but the cdrom can be removed and system will be faster.
  ENDTEXT

LABEL altker32_3
  MENU LABEL 3. SystemRescueCd with console in high resolution (1024x768)
  LINUX altker32
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791
  TEXT HELP
  Boot alternative 32bit kernel with console in high resolution
  ENDTEXT

LABEL altker32_4
  MENU LABEL 4. SystemRescueCd with the default graphical environment
  LINUX altker32
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 dostartx
  TEXT HELP
  Boot alternative 32bit kernel and start the XFCE graphical environment
  directly. You can also get in this environment by typing "startx" from
  the console.
  ENDTEXT

LABEL altker32_5
  MENU LABEL 5. SystemRescueCd with VESA based graphical environment
  LINUX altker32
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791 dostartx forcevesa
  TEXT HELP
  Boot alternative 32bit kernel and use VESA based graphical environment
  Try this if you have problems to get the default graphical environment
  ENDTEXT

MENU SEPARATOR

LABEL return
  MENU LABEL Return to main menu
  MENU EXIT

MENU END

# ------------------------------------------------------------------------------

MENU BEGIN
MENU TITLE D) Alternative 64bit kernel (altker64) with more choice...

LABEL altker64_1
  MENU LABEL 1. SystemRescueCd with default options
  LINUX altker64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5
  TEXT HELP
  Boot alternative 64bit kernel with default options (should always work)
  ENDTEXT

LABEL altker64_2
  MENU LABEL 2. SystemRescueCd with all files cached to memory
  LINUX altker64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 docache
  TEXT HELP
  Boot alternative 64bit kernel and run system from memory.
  It requires 512 MB of memory to work and takes some time during the
  boot process, but the cdrom can be removed and system will be faster.
  ENDTEXT

LABEL altker64_3
  MENU LABEL 3. SystemRescueCd with console in high resolution (1024x768)
  LINUX altker64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791
  TEXT HELP
  Boot alternative 64bit kernel with console in high resolution
  ENDTEXT

LABEL altker64_4
  MENU LABEL 4. SystemRescueCd with the default graphical environment
  LINUX altker64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 dostartx
  TEXT HELP
  Boot alternative 64bit kernel and start the XFCE graphical environment
  directly. You can also get in this environment by typing "startx" from
  the console.
  ENDTEXT

LABEL altker64_5
  MENU LABEL 5. SystemRescueCd with VESA based graphical environment
  LINUX altker64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791 dostartx forcevesa
  TEXT HELP
  Boot alternative 64bit kernel and use VESA based graphical environment
  Try this if you have problems to get the default graphical environment
  ENDTEXT

MENU SEPARATOR

LABEL return
  MENU LABEL Return to main menu
  MENU EXIT

MENU END

# ------------------------------------------------------------------------------

MENU BEGIN
MENU TITLE E) Boot an exising Linux OS installed on the disk...

LABEL linuxosdisk32
  MENU LABEL Boot an exising 32bit Linux OS installed on the disk
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 root=auto
  TEXT HELP
  Detect partition where linux is installed and boot from it. You can use 
  this to boot Linux if your boot loader (eg: Grub) is broken or has been
  removed by another OS. This will work if the Linux OS is 32bit.
  ENDTEXT

LABEL linuxosdisk64
  MENU LABEL Boot a 32bit or 64bit Linux OS installed on the disk
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 root=auto
  TEXT HELP
  Detect partition where linux is installed and boot from it. You can use 
  this to boot Linux if your boot loader (eg: Grub) is broken or has been
  removed by another OS. This will work with both 32bit and 64bit Linux OS.
  ENDTEXT

MENU SEPARATOR

LABEL return
  MENU LABEL Return to main menu
  MENU EXIT

MENU END

# ------------------------------------------------------------------------------

MENU BEGIN
MENU TITLE F) Run system tools from floppy disk image...

LABEL memtest
  MENU LABEL MEMTEST: Memory test using Memtest86+
  kernel /bootdisk/memtestp
  APPEND setkmap=pl -
  TEXT HELP
  Use this tool if you suspect your RAM from being damaged. Damaged memory can
  explain crashes or unexpected bahaviors on stable operating systems.
  ENDTEXT

LABEL ntpass
  MENU LABEL NTPASSWD: Reset or edit Windows passwords
  kernel /ntpasswd/vmlinuz
  APPEND setkmap=pl rw vga=1 initrd=/ntpasswd/initrd.cgz,/ntpasswd/scsi.cgz
  TEXT HELP
  This tool can be used to reset windows users accounts. It works will all 
  windows user accounts including the administrator. You can use this tool if
  you forgot the administrator's password.
  ENDTEXT

LABEL freedos
  MENU LABEL FREEDOS: Clone of the MSDOS Operating System
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/freedos.img floppy
  TEXT HELP
  FreeDOS can be used to execute DOS programs such as BIOS upgrade tools
  ENDTEXT

LABEL netboot
  MENU LABEL NETBOOT: Boot from the network
  kernel netboot
  APPEND setkmap=pl -

LABEL hdt
  MENU LABEL HDT: recent hardware diagnostics tool
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/hdt.img floppy
  TEXT HELP
  This diagnostic tool will give you information about your hardware
  ENDTEXT

LABEL ranish
  MENU LABEL RANISH: Partition Manager tool
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/ranish.img floppy

LABEL aida
  MENU LABEL AIDA: old hardware diagnostics tool
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/aida.img floppy

LABEL gag
  MENU LABEL GAG: Graphical Boot Manager
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/gag.img floppy

LABEL dban
  MENU LABEL DBAN: erase all data from the disk
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/dban.img floppy

LABEL mhdd
  MENU LABEL MHDD: Low-level Hard Drive diagnostic tool
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/mhdd.img floppy

LABEL grubdisk
  MENU LABEL SGD: Super Grub Disk
  kernel memdisk
  APPEND setkmap=pl initrd=/bootdisk/grubdisk.img floppy

MENU SEPARATOR

LABEL return
  MENU LABEL Return to main menu
  MENU EXIT

MENU END

# ------------------------------------------------------------------------------

MENU SEPARATOR

LABEL local1
  MENU LABEL *) Boot from first hard disk
  kernel chain.c32
  APPEND setkmap=pl hd0
  TEXT HELP
  Boot local OS installed on first hard disk
  ENDTEXT

LABEL local2
  MENU LABEL *) Boot from second hard disk
  kernel chain.c32
  APPEND setkmap=pl hd1
  TEXT HELP
  Boot local OS installed on second hard disk
  ENDTEXT

LABEL rescuecd
  MENU HIDE
  LINUX rescuecd
  INITRD initram.igz

LABEL rescue64
  MENU HIDE
  LINUX rescue64
  INITRD initram.igz

LABEL altker32
  MENU HIDE
  LINUX altker32
  INITRD initram.igz

LABEL altker64
  MENU HIDE
  LINUX altker64
  INITRD initram.igz

LABEL uk32
  MENU HIDE
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5

LABEL uk64
  MENU HIDE
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5

LABEL fd32
  MENU HIDE
  LINUX rescuecd
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791 docache dostartx

LABEL fd64
  MENU HIDE
  LINUX rescue64
  INITRD initram.igz
  APPEND setkmap=pl scandelay=5 vga=791 docache dostartx

--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/ifcpu64.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/reboot.c32                            1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v3.xx)
 syslinux/ifcpu64.c32               :  COM32R module (v3.xx)
 syslinux/menu.c32                  :  COM32R module (v3.xx)
 syslinux/reboot.c32                :  COM32R module (v3.xx)
 syslinux/vesamenu.c32              :  COM32R module (v3.xx)


```

---

### Post by oldfred on 2011-06-27
The issues I see are grub installed to the windows PBR which prevents windows from booting, various copies of grub legacy still floating around, and the install in sdb3 still refering to sda8's UUID.

Grub.cfg in sdb3, I changed entries in red:
This is one time where manually editing the first boot line of grub.cfg may be the easiest way.


```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='([COLOR=Red]hd1,msdos3[/COLOR])'
    search --no-floppy --fs-uuid --set [COLOR=Red]6a26581f-084b-42e4-89dc-71b464b6b29c[/COLOR]
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=[COLOR=Red]6a26581f-084b-42e4-89dc-71b464b6b29c[/COLOR] ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}

```#Normally we do not directly edit grub.cfg. Edit from liveCD.
sudo mount /dev/sdb3 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

If you boot from sdb then you should be able to boot into your install in sdb3 and then running these should be ok.

sudo update-grub

You also want to make sure grub is seeing the sdb drive as the drive to reinstall to on updates:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If you can boot ok, then we can work on windows and housecleaning old grub.

---

### Post by froff on 2011-06-29
Hi
Thanks for help.
Now I got stuck on trying to revive windows installation after performed sector-by sector copy. 
I made my new disk dual booted. There is dopied via "dd" windows xp installation on 1-st partition. I saved my grub2 mbr into file and recreated mbr by ms-sys.
Then I made windows partition bootable with testdisk program.

New windows partition looks ok. I performed chkdsk /f from original windows installation.
Gparted shows no errors and I'm able to mount it under linux.

But new windows partition have to have boot sector repaired/readjusted to be bootable.
Without any additional action disk is unbootable.

I tired to do this with testdisk program but with no success:
After rebuilding windows boot sector gparted started to inform, that partition has errors.
When tried to boot system I got windows boot menu (so mbr is perfectly ok!) but when choose windows to start normally I got blue screen of death after a few seconds.

I'm almost sure that testdisk created improper boot sector.
Is there any other tool that can rebuild windows boot sector?

best regards.

---

### Post by oldfred on 2011-06-29
Windows. You may only need fixboot which repairs partition boot sector. But if you get to windows then the boot sector must be ok. Is boot.ini ok? But boot.ini errors normally throws a hal.dll error. Boot sector just calls ntldr, besides having some partition settings.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer. 

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
[COLOR=Red]FIXBOOT  C:[/COLOR]
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by froff on 2011-07-01
Thanks a lot!
Now System seems to work perfectly.

But I have one more puzzle to solve:
Is it possible to start linux on other (second) physical hdd via windows boot.ini menu?
When I try to put second disk mbr into second_disk_mbr.bin and create boot.ini options like that:
C:\first_disk_mbr.bin="Ubuntu Linux on current disk"
C:\second_disk_mbr.bin="Ubuntu Linux on second disk"

It always starts first linux - no mater what option I choose. :(

---

### Post by oldfred on 2011-07-01
I have not used the mbr.bin method to boot. You have to copy two different grub MBR or PBR to make your method work. Also any grub install in a PBR will probably have to be regularly updated as it is using hard coded addresses to boot which change on grub updates. 

But why not just use grub2's  boot loader from the second drive. It gives you the choice of all three systems. You can set a default to boot any one of the systems.

---

### Post by froff on 2011-07-12
> **oldfred said:**
> 
But why not just use grub2's  boot loader from the second drive. It gives you the choice of all three systems. You can set a default to boot any one of the systems.


Hello
Sorry for delay.
You are completely right - boot from second system is good idea. 
But now I treat the following problem just as puzzle or exercise:
How to boot multiple linux installations on multiple disks from one windows start menu.

Best regards :)

---

### Post by oldfred on 2011-07-12
I do not know EasyBCD. A few here do use it and say it works. Not exactly sure how it chainloads to the grub/Ubuntu install. I like grub2, so have used it for everything. I even converted a windows repair Flash USB to boot from grub so I could also loopmount additional repair ISO from same flash.

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

