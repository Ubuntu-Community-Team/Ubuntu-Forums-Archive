---
title: "Partition table errors -&gt; unallocated for GPartEd"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by mme oscar on 2012-07-01
Hi all,

I have a minor problem with my partition table (dual boot). "Minor" because I can still boot and everything, the only consequence as far as I'm aware is that GPartEd does not see the partitions (latest GpartEd, 0.12.1). 

I have now read a fair amount of threads about similar problems but could not find a way to fix it (without re-installing everything, I don't want to currently).

Here is the bootinfoscript output:

```

                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       31457279 sectors, but according to the info from 
                       fdisk, it has 31465471 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 136118871.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /120701-temp-backup-MBR-with-errors.img looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 573440000.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,467,519    31,465,472  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,471,335    31,664,114       192,780   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   136,118,744   104,454,617   7 NTFS / exFAT / HPFS
/dev/sda4         136,118,745   625,141,759   489,023,015   5 Extended
/dev/sda5         136,118,871   402,363,989   266,245,119   b W95 FAT32
/dev/sda6         402,364,053   500,649,659    98,285,607  83 Linux
/dev/sda7         500,649,660   583,352,279    82,702,620  83 Linux
/dev/sda8         583,352,343   605,875,409    22,523,067  83 Linux
/dev/sda9         605,884,416   625,141,759    19,257,344  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disque /dev/sdb: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   573,439,999   573,439,937   b W95 FAT32
/dev/sdb2         573,440,000   614,399,999    40,960,000   b W95 FAT32
/dev/sdb3         614,400,000   976,773,119   362,373,120   5 Extended
/dev/sdb5         614,402,048   942,082,047   327,680,000  83 Linux
/dev/sdb6         942,084,096   976,773,119    34,689,024  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D8D272EFD272D0EC                       ntfs       RECOVERY
/dev/sda2        AA0091BC00918FC5                       ntfs       SYSTEM
/dev/sda3        BE1E75901E754307                       ntfs       
/dev/sda5        EF86-5271                              vfat       sharedfat
/dev/sda6        23dc1874-f991-4981-95b7-1a88510fa5d8   ext4       data
/dev/sda7        ab129daf-9009-486b-bb7b-6bf6065e19a9   ext4       linux!
/dev/sda8        d29ba00b-5ca2-46d6-bedb-5ee8ce8da642   ext4       linux2
/dev/sda9        aed15349-2481-4cc4-bfee-6c6053781db6   swap       
/dev/sdb1        4919-AA9B                              vfat       MBBIGFAT
/dev/sdb2        C3C0-6707                              vfat       MBSMALLFAT
/dev/sdb5        f8ca249a-8c01-40c1-ae52-d86f2b7dd148   ext4       mb-big-ext4
/dev/sdb6        f9d44cdb-5960-49e3-8710-183a8d970930   ext4       mb-small-ext4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/sharedfat         vfat       (rw,umask=0000)
/dev/sda6        /media/data              ext4       (rw,commit=0)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda8        /media/linux2            ext4       (rw,commit=0)
/dev/sdb1        /media/MBBIGFAT          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb2        /media/MBSMALLFAT        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb5        /media/mb-big-ext4       ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb6        /media/mb-small-ext4     ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set ab129daf-9009-486b-bb7b-6bf6065e19a9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set ab129daf-9009-486b-bb7b-6bf6065e19a9
set locale_dir=($root)/boot/grub/locale
set lang=fr
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=60
fi
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu 10.10, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ab129daf-9009-486b-bb7b-6bf6065e19a9
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=ab129daf-9009-486b-bb7b-6bf6065e19a9 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu 10.10, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ab129daf-9009-486b-bb7b-6bf6065e19a9
    echo    'Loading Linux 2.6.35-32-generic ...'
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=ab129daf-9009-486b-bb7b-6bf6065e19a9 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-32-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 sur /dev/sda3 (via loader sur /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set dae8c39ae8c37375
    chainloader +1
}

menuentry "--------------------------------------------------" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set dae8c39ae8c37375
    chainloader +1
}

menuentry "--------------------------------------------------" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set dae8c39ae8c37375
    chainloader +1
}

menuentry "--------------------------------------------------" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set dae8c39ae8c37375
    chainloader +1
}

menuentry "/dev/sda1 : partition Samsung Recovery ! DANGER ! " {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d8d272efd272d0ec
    chainloader +1
}

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid      0  0  
/dev/sda7                                  /                 ext4  errors=remount-ro        0  1  
/dev/sda9  none              swap  sw                       0  0  
/dev/sda3                                  /media/windows    ntfs  nls=iso8859-1,umask=000  0  0  
/dev/sda5                                  /media/sharedfat  vfat  umask=0000               0  0  
/dev/sda6                                  /media/data       ext4  defaults                 0  0  
/dev/sda8                                  /media/linux2     ext4  defaults                 0  0  
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 250.978479385 = 269.486090240  boot/grub/core.img                             1
 249.545270920 = 267.947194368  boot/grub/grub.cfg                             1
 260.526144028 = 279.737817088  boot/initrd.img-2.6.35-32-generic              2
 260.243539810 = 279.434373120  boot/vmlinuz-2.6.35-32-generic                 1
 260.526144028 = 279.737817088  initrd.img                                     2
 260.243539810 = 279.434373120  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  03 02 03 7c b4 06 c0 c5  08 03 02 03 7c b4 06 c0  |...|........|...|
00000010  c6 08 03 02 03 7c b7 06  c0 df 08 03 02 03 7c b7  |.....|........|.|
00000020  06 c0 e0 08 03 02 03 7c  b7 06 c0 e1 08 03 02 03  |.......|........|
00000030  7c b7 06 c0 e2 08 03 02  03 7c b7 06 c0 e3 08 03  ||........|......|
00000040  02 03 7c b7 06 c0 e4 08  03 02 03 7c b7 06 c0 e5  |..|........|....|
00000050  08 03 02 03 7c b7 06 c0  e6 08 03 02 03 7c b7 06  |....|........|..|
00000060  c0 e7 08 03 02 03 7c b7  06 c0 e8 08 03 02 03 7c  |......|........||
00000070  b7 06 c0 e9 00 00 00 5a  00 00 00 00 00 00 00 00  |.......Z........|
00000080  09 00 00 00 00 00 00 00  00 09 00 00 00 00 00 00  |................|
00000090  00 00 09 00 00 00 00 00  00 00 00 09 00 00 00 00  |................|
000000a0  00 00 00 00 09 00 00 00  00 00 00 00 00 09 00 00  |................|
000000b0  00 00 00 00 00 00 09 00  00 00 00 00 00 00 00 09  |................|
000000c0  00 00 00 00 00 00 00 00  09 00 00 00 00 00 08 03  |................|
000000d0  02 03 7c ba 06 c0 f4 08  03 02 03 7c ba 06 c0 f5  |..|........|....|
000000e0  08 03 02 03 7c ba 06 c0  f6 08 03 02 03 7c ba 06  |....|........|..|
000000f0  c0 f7 08 03 02 03 7c ba  06 c0 f8 08 03 02 03 7c  |......|........||
00000100  ba 06 c0 f9 08 03 02 03  7c ba 06 c0 fa 08 03 02  |........|.......|
00000110  03 7c ba 06 c0 fb 08 03  02 03 7c ba 06 c0 fc 08  |.|........|.....|
00000120  03 02 03 7c ba 06 c0 fd  08 03 02 03 7c bb 06 c0  |...|........|...|
00000130  fe 08 03 02 03 7c bb 06  c0 ff 08 03 02 03 7c bb  |.....|........|.|
00000140  06 c1 00 08 03 02 03 7c  bb 06 c1 01 08 03 02 03  |.......|........|
00000150  7c bb 06 c1 02 08 03 02  03 7c bb 06 c1 03 08 03  ||........|......|
00000160  02 03 7c bb 06 c1 04 08  03 02 03 7c bb 06 c1 05  |..|........|....|
00000170  08 03 02 03 7c bb 06 c1  06 08 03 02 03 7c bb 06  |....|........|..|
00000180  c1 07 08 03 02 03 7c bb  06 c1 08 08 03 02 03 7c  |......|........||
00000190  bc 06 c1 09 08 03 02 03  7c bc 06 c1 0a 08 03 02  |........|.......|
000001a0  03 7c bc 06 c1 0b 08 03  02 03 7c bc 06 c1 0c 08  |.|........|.....|
000001b0  03 02 03 7c bc 06 c1 0d  08 03 02 03 7c bc 00 fe  |...|........|...|
000001c0  ff ff 0b fe ff ff 7e 00  00 00 ff 93 de 0f 00 fe  |......~.........|
000001d0  ff ff 05 fe ff ff 01 00  00 00 2e fb 25 01 00 00  |............%...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```a few precisions about the 3 first partitions, in case you want to know:

[LIST=1]
[*]manufacturer recovery software (Samsung laptop).  didn't want to remove this, in order to be able to go back to the original state (even if I actually also have PartImage backups)
[*]the useless Windows hidden partition
[*]the actual Windows 7
[/LIST]

Also don't be surprised with the number of (extended) partitions, I like to organize my disk this way.

I have already tried to write the table again with fdisk, didn't work. btw I would be interested in understanding why fdisk can show something different from what is actually in the table?

Thank you!

---

### Post by oldfred on 2012-07-01
I cannot see an issue & script often highlights an error in partition table.

What does gparted show? Do you see partitions but errors or warning icons. If you click on those it will tell you more about the issue.

I have had gparted not even show my drive. I had XP installed and it was working, but gparted would take forever to try to mount then just show my other drives. I ran chkdsk, Windows actually booted a bit faster and then gparted worked.

Just a comment or two.
I do not like FAT anymore for larger partitions or partitions on a hard drive. (Unless you absolutely have to have it for some compatibility reason wtih Mac or Xbox.) I thought I was creating backups but they were over 4GB and every one was exactly 4GB. It turns out that is the max file size in FAT32, so I never had a valid backup. Converted to NTFS for data I needed with XP and ext4 for backup data. FAT32 also does not have a journal, so file recovery can be more difficult or impossible where with NTFS it might be.
With multiple drives I prefer to have each system on a separate drive. Drives fail and I like to have at least one drive bootable, but I also have multiple bootable flash drives with Ubuntu, repair ISOs and other ISO.

---

### Post by mme oscar on 2012-07-01
For Gparted the whole disk is "unallocated space", no partitions at all. 

Yes I know the FAT32 limitation. until now I wasn't sure if NTFS was properly supported by most Linux tools, which is why my "shared partition" is still FAT32. 
About multiple drives, this is a laptop so wouldn't be really convenient here ;)  

Thanks for the comments anyway

---

### Post by oldfred on 2012-07-01
I think the issue was there in 2006 when I used FAT32, but I changed to NTFS in 2009 and not had any issues.  Most that have issues use hibernation and that was not the NTFS driver but an issue trying to use two systems to write into the same space.

I might try chkdsk from a Windows repair CD on every NTFS & FAT32 partition. Not sure what else may be the issue.

Did you change BIOS to turn RAID on? That might write a setting that gparted would not be compatible with, but that normally is before any install and drive has RAID settings left.

---

### Post by mme oscar on 2012-07-02
ok thanks for the tip about FAT32/NTFS.

Don't have any windows CD but did a chkdsk from windows, no error found.

Did not change anything in the BIOS (and btw  I forgot to say that GParted used to work fine with my disk)

Other ideas? Do you think it looks more like a real error or a bug in Gparted? Because in the latter case I can live with that, and later when I want to re-install everything I will re-create all my partitions.

---

### Post by oldfred on 2012-07-02
I do not see anything wrong other than these comments in your recovery & FAT partitions.

I know NTFS - PBR (partition boot sector) has to have the same start & size info as the partition table. I am not sure about FAT but bet it does also.

> Boot sector info:  According to the info in the boot sector, sda1 has 
                       31457279 sectors, but according to the info from 
                       fdisk, it has 31465471 sectors.

Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 136118871.

IS FAT sdb1:
Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /120701-temp-backup-MBR-with-errors.img looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.


With NTFS a chkdsk or fixBoot is required to fix PBR. 
Not sure how the fix the FAT partition with grub2 install since now Windows will not recognize it as a FAT partition.

This says the recovery is the same for FAT32.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
> Recovery of a FAT32 partition (instead of an NTFS partition) can be accomplished by following exactly the same steps.

---

### Post by mme oscar on 2012-07-03
> 
With NTFS a chkdsk or fixBoot is required to fix PBR.
Do you know if it's possible to run chkdisk or fixboot without a Windows CD?

> 
This says the recovery is the same for FAT32.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
testdisk didn't help me because it does not find any problem to fix: as far as I understand you can only write a new partition table if some partition recovery was done before.

---

### Post by oldfred on 2012-07-03
Do you know someone with the some 32 or 64 bit version of Windows?

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Not sure what this really has.
Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by mme oscar on 2012-07-18
Sorry for the delay, since everything was still working I didn't want to break anything before being ready to deal with it.

So recently after doing my backups I tried to rebuild the partitions with testdisk... didn't work. My understanding is that there was some kind of inconsistency with the partition table: I strongly suspect the first partition with the "Samsung Recovery" system, because as far as I understand it has some hidden sectors and probably I did something wrong about that with grub or soem other tool.

So basically I ended reinstalling everything: since I wanted to get rid of both this recovery partition and the Windows "hidden" boot partition, I found these useful pieces of information: 
[LIST=1]
[*]  you can download a windows install CD legally: [http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html](http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html)
[*] and you can simply avoid creating the windows hidden partition: [http://www.mydigitallife.info/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation](http://www.mydigitallife.info/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation)
[/LIST]

and I installed Ubuntu 12.04, but unfortunately I now have another problem... for which I started this new thread (since it's not related to this one):

[http://ubuntuforums.org/showthread.php?p=12113397](http://ubuntuforums.org/showthread.php?p=12113397)

Anyway thank you very much for your help!

---

