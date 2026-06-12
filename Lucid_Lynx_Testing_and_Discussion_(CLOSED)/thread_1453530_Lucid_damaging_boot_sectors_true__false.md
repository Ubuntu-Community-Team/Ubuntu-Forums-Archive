---
title: "Lucid damaging boot sectors? true / false"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-13
Some of us like to run the Boot Info Script from source forge to get info on an installation and boot problems.
[http://ubuntuforums.org/showthread.php?t=1291280&highlight=boot+info+script](http://ubuntuforums.org/showthread.php?t=1291280&highlight=boot+info+script)
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

After installing Lucid Beta 1 and 2 on different partitions I now get Unknown MBRs/Boot Sectors/etc listed at the end of the report. I have seen this problem listed a few times here and on other forums. When this applies to Windows Sda1 partition people cannot get grub to boot windows and there is a suspicion that grub is causing this. 
My unknown and those of lindsay7 are here:
[http://ubuntuforums.org/showthread.php?t=1453422](http://ubuntuforums.org/showthread.php?t=1453422)
[http://ubuntuforums.org/showthread.php?t=1448970&highlight=unknown+bootloader](http://ubuntuforums.org/showthread.php?t=1448970&highlight=unknown+bootloader)

Anyone know if this is a normal interaction after multiple installs where maybe Grub conflicts with previous installations?
Is this a phantom result of the script that is not compatible with Lucid in some way?
If everything works - do I worry about it? :)

---

### Post by dino99 on 2010-04-13
do you know where most of the bugs are ?

response: betwenn desktop and chair  :confused:

about your questions: 

multiple installations, resized partitions, non aligned blocs, crashes ...
let your hdds into troubles some times.

That's why we consider that we might always make a fresh install on a partition formated with a stable partitioner ( parted).

Even a partitioner can be bugged (it's software), so first thing before installing is to dig around what we use.

---

### Post by philinux on 2010-04-13
Previous versions of the script gave unknown mbr's etc and failed to recognise grub installed to a partition. The latest incarnation 055 works fine.

---

### Post by bcbc on 2010-04-13
> **BrokeMahPC said:**
> 
After installing Lucid Beta 1 and 2 on different partitions I now get Unknown MBRs/Boot Sectors/etc listed at the end of the report.

I had same issue. Ended up with an unknown bootloader on /dev/sda3 (extended partition) right after installing lucid on /dev/sdb1.

I think the problem people are having with windows not booting is due to a prompt during the upgrade as to where to install grub2 - the default shows everything (all MBRs (if multiple drives) and all partitions) checked, and if you don't uncheck them, it installs everywhere.

---

### Post by alexsimps on 2010-04-13
> **bcbc said:**
> 
I think the problem people are having with windows not booting is due to a prompt during the upgrade as to where to install grub2 - the default shows everything (all MBRs (if multiple drives) and all partitions) checked, and if you don't uncheck them, it installs everywhere.

I had the same problem yesterday when i upgraded to lucid, It asked for the partition to install to i forgot the partition(/was to lazy to look it up) and just let it do its thing on all of the partitions thinking nothing of it. It messed up my vista bootloader and took a while to figure out and fix up. So i guess that sounds like maybe what caused it.

---

### Post by BrokeMahPC on 2010-04-13
@ dino99 - guilty! - big 4 legged, grinning bug here! :lolflag:
Thanks for your help - I don't think it's anything to worry about. From the advice here and elsewhere - as soon as I have time I will nuke that extended partition with GParted and get rid of everything except windows on that drive. It's been in use for awhile so could do with some maintenance.

Oldfred had a look at it and believes it to be random data that has somehow been written to the PBR of the extended partition. Boot Info Script may be interpreting it as as a boot loader when in fact it may not be. 

It is odd though - I have used GParted (never use anything else) many times on that drive and not had a problem till this week. Whatever it is may have occurred between 10.9.2009 when I last used parted (Mint Helena) and now - difficult to tell.

I will install Lucid again just for fun and see if anything happens.

---

### Post by dino99 on 2010-04-13
yeah, software=logic, nothing but logic

---

### Post by nanog on 2010-04-13
i had an unrecoverable grub error on a recent karmic-lucid b2 upgrade. the mbr got nuked. both update-grub and grub-install failed due to partition size errors. i was feeling lazy so i just dded the image onto another drive and did a clean grub install (i hate testdisk). i would have filed a bug but apparently some of the things i've done make this ubuntu install persona non-grata. :(

---

### Post by bcbc on 2010-04-13
> **BrokeMahPC said:**
> @ dino99 - guilty! - big 4 legged, grinning bug here! :lolflag:
Thanks for your help - I don't think it's anything to worry about. From the advice here and elsewhere - as soon as I have time I will nuke that extended partition with GParted and get rid of everything except windows on that drive. It's been in use for awhile so could do with some maintenance.

Oldfred had a look at it and believes it to be random data that has somehow been written to the PBR of the extended partition. Boot Info Script may be interpreting it as as a boot loader when in fact it may not be. 

It is odd though - I have used GParted (never use anything else) many times on that drive and not had a problem till this week. Whatever it is may have occurred between 10.9.2009 when I last used parted (Mint Helena) and now - difficult to tell.

I will install Lucid again just for fun and see if anything happens.
I don't think it's you. I installed lucid to my external usb and not only did I get an unknown bootloader on my extended partition on the internal drive - it also modified the partition table in the process, according to 'fdisk -l' (I had a previous bootinfoscript result to compare it against).

Then after another Lucid (beta2) install, I noticed two more 'unknown bootloaders' on different partitions, this time on my external USB drive.

Anyway - so far it hasn't broken anything, as my XP partition has been unaffected and Ubuntu doesn't seem to care. And for the record, I only use GParted for partitioning.

---

### Post by BrokeMahPC on 2010-04-14
Thank you for your reply bcbc - unfortunately I have no previous boot info script to compare, but, I'm 99% sure this occurred after one of my Lucid installs. I will have to reinstall and see if it does anything else.
If you look at lindsay7's post above you will see multiple occurrences of this  - we will have to see if anyone else notices this problem.

---

### Post by Didius Falco on 2010-04-14
> **BrokeMahPC said:**
> Thank you for your reply bcbc - unfortunately I have no previous boot info script to compare, but, I'm 99% sure this occurred after one of my Lucid installs. I will have to reinstall and see if it does anything else.
If you look at lindsay7's post above you will see multiple occurrences of this  - we will have to see if anyone else notices this problem.

Before you reinstall, I'd have a look at post #3. 

What version of the Boot Info Script are you using? If it's <.055, I'd download and run that. It could be something in the older script that has now been corrected....

---

### Post by BrokeMahPC on 2010-04-14
I can confirm it is boot_info_script055.sh I am using
Some additional info - With my mint 8 live CD - Gparted gives a warning triangle on one of the partitions in sda2 and gives errors about it being busy and not being able to fully read it.
The Lucid live CD has no problem with it?

---

### Post by bcbc on 2010-04-14
I'm also using script 0.55.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 

    partition #5 for /boot/grub.

 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 

    partition #1 for /boot/grub.

 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat

    Boot sector type:  Dell Utility: Fat16

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs

    Boot sector type:  Windows XP

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  Windows XP

    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat

    Boot sector type:  DEll Restore: Fat32

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition

    Boot sector type:  Unknown

    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       

    Boot sector type:  Unknown

    Boot sector info:  

    Mounting failed:

mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap

    Boot sector type:  -

    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4

    Boot sector type:  -

    Boot sector info:  

    Operating System:  Ubuntu lucid (development 

                       branch)

    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition

    Boot sector type:  Unknown

    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4

    Boot sector type:  -

    Boot sector info:  

    Operating System:  

    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext2

    Boot sector type:  -

    Boot sector info:  

    Operating System:  

    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat

    Boot sector type:  Fat32

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       vfat

    Boot sector type:  Fat32

    Boot sector info:  According to the info in the boot sector, sdc2 starts 

                       at sector 0. But according to the info from fdisk, 

                       sdc2 starts at sector 2100870.

    Operating System:  

    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 78.5 GB, 78518522880 bytes

255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility

/dev/sda2    *         96,390   123,829,019   123,732,630   7 HPFS/NTFS

/dev/sda3         146,834,100   153,340,424     6,506,325  db CP/M / CTOS / ...

/dev/sda4         123,829,082   146,834,099    23,005,018   5 Extended

/dev/sda5         123,829,083   144,681,389    20,852,307  83 Linux

/dev/sda6         144,681,453   146,834,099     2,152,647  82 Linux swap / Solaris

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.3 GB, 100256292864 bytes

255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    16,771,859    16,771,797  83 Linux

/dev/sdb2          16,771,922   195,800,219   179,028,298   5 Extended

/dev/sdb5          16,771,923    37,736,684    20,964,762  83 Linux

/dev/sdb6          37,736,748    78,702,434    40,965,687  83 Linux

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8127 MB, 8127512576 bytes

251 heads, 62 sectors/track, 1020 cylinders, total 15874048 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     2,100,869     2,100,808   c W95 FAT32 (LBA)

/dev/sdc2           2,100,870    15,873,239    13,772,370   b W95 FAT32

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-0505                              vfat       DellUtility                   

/dev/sda2        10ACE996ACE9769E                       ntfs                                     

/dev/sda3                                               vfat       DellRestore                   

/dev/sda4: PTTYPE="dos" 

/dev/sda6        23ad6860-5ee6-46bb-a015-351b74fc5d7b   swap                                     

/dev/sda: PTTYPE="dos" 

/dev/sdb1        f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc   ext4       Ubuntu1                       

/dev/sdb5        282db25f-3fef-4557-810a-dacd13b9b389   ext4                                     

/dev/sdb6        33d2f143-fb4b-4597-83cf-e80fb60c33e2   ext2       Ubuntu2                       

/dev/sdb: PTTYPE="dos" 

/dev/sdc1        64B0-57D3                              vfat       BOOT                          

/dev/sdc2        71CD-3254                              vfat       Data                          

/dev/sdc: PTTYPE="dos" 

error: /dev/sda5: No such file or directory

error: /dev/sdb2: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)

/dev/sdb5        /home                    ext4       (rw)

/dev/sdc2        /media/Data              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

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

set root='(hd0,1)'

search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

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

set root='(hd0,1)'

search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

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

menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro   quiet splash

    initrd    /boot/initrd.img-2.6.32-19-generic

}

menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    echo    Loading Linux 2.6.32-19-generic ...

    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro single 

    echo    Loading initial ramdisk ...

    initrd    /boot/initrd.img-2.6.32-19-generic

}

menuentry "Ubuntu, with Linux 2.6.32-18-generic" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro   quiet splash

    initrd    /boot/initrd.img-2.6.32-18-generic

}

menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    echo    Loading Linux 2.6.32-18-generic ...

    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro single 

    echo    Loading initial ramdisk ...

    initrd    /boot/initrd.img-2.6.32-18-generic

}

menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro   quiet splash

    initrd    /boot/initrd.img-2.6.32-17-generic

}

menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    echo    Loading Linux 2.6.32-17-generic ...

    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro single 

    echo    Loading initial ramdisk ...

    initrd    /boot/initrd.img-2.6.32-17-generic

}

menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro   quiet splash

    initrd    /boot/initrd.img-2.6.32-16-generic

}

menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {

    recordfail

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    echo    Loading Linux 2.6.32-16-generic ...

    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc ro single 

    echo    Loading initial ramdisk ...

    initrd    /boot/initrd.img-2.6.32-16-generic

}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###

menuentry "Memory test (memtest86+)" {

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    linux16    /boot/memtest86+.bin

}

menuentry "Memory test (memtest86+, serial console 115200)" {

    insmod ext2

    set root='(hd0,1)'

    search --no-floppy --fs-uuid --set f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc

    linux16    /boot/memtest86+.bin console=ttyS0,115200n8

}

### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###

menuentry "Dell Utility Partition (on /dev/sda1)" {

    insmod fat

    set root='(hd1,1)'

    search --no-floppy --fs-uuid --set 07d6-0505

    drivemap -s (hd0) ${root}

    chainloader +1

}

menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {

    insmod ntfs

    set root='(hd1,2)'

    search --no-floppy --fs-uuid --set 10ace996ace9769e

    drivemap -s (hd0) ${root}

    chainloader +1

}

menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda5)" {

    insmod ext2

    set root='(hd1,5)'

    search --no-floppy --fs-uuid --set b1372c47-f471-41cb-abec-120321bfa3ef

    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=b1372c47-f471-41cb-abec-120321bfa3ef ro quiet splash

    initrd /boot/initrd.img-2.6.31-20-generic

}

menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda5)" {

    insmod ext2

    set root='(hd1,5)'

    search --no-floppy --fs-uuid --set b1372c47-f471-41cb-abec-120321bfa3ef

    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=b1372c47-f471-41cb-abec-120321bfa3ef ro single

    initrd /boot/initrd.img-2.6.31-20-generic

}

menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda5)" {

    insmod ext2

    set root='(hd1,5)'

    search --no-floppy --fs-uuid --set b1372c47-f471-41cb-abec-120321bfa3ef

    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=b1372c47-f471-41cb-abec-120321bfa3ef ro quiet splash

    initrd /boot/initrd.img-2.6.31-19-generic

}

menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda5)" {

    insmod ext2

    set root='(hd1,5)'

    search --no-floppy --fs-uuid --set b1372c47-f471-41cb-abec-120321bfa3ef

    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=b1372c47-f471-41cb-abec-120321bfa3ef ro single

    initrd /boot/initrd.img-2.6.31-19-generic

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

UUID=f7ee4ba8-9a3f-4817-aed9-df2b4e599ffc /               ext4    errors=remount-ro 0       1

# /home was on /dev/sdb5 during installation

UUID=282db25f-3fef-4557-810a-dacd13b9b389 /home           ext4    defaults        0       2

# swap was on /dev/sda6 during installation

/dev/sda6 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================

   4.4GB: boot/grub/core.img

   2.6GB: boot/grub/grub.cfg

   5.5GB: boot/initrd.img-2.6.32-16-generic

   7.3GB: boot/initrd.img-2.6.32-17-generic

   7.7GB: boot/initrd.img-2.6.32-18-generic

   8.2GB: boot/initrd.img-2.6.32-19-generic

   5.5GB: boot/vmlinuz-2.6.32-16-generic

   5.7GB: boot/vmlinuz-2.6.32-17-generic

   7.4GB: boot/vmlinuz-2.6.32-18-generic

   6.2GB: boot/vmlinuz-2.6.32-19-generic

   8.2GB: initrd.img

   7.7GB: initrd.img.old

   6.2GB: vmlinuz

   7.4GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  2a fe f9 f4 ff 28 fe f9  f4 ff 27 fe f9 f4 ff 26  |*....(....'....&|

00000010  fd f9 f4 ff 26 2f fe f9  f4 ff 29 fd f9 f4 ff 25  |....&/....)....%|

00000020  2a fc f9 f4 ff 3c ff f9  f4 ff 3d ff f9 f4 ff 2f  |*....<....=..../|

00000030  fd f9 f4 ff 3c 3d fe f9  f4 ff 27 fe f9 f4 ff 26  |....<=....'....&|

00000040  fd f9 f4 ff 3b 3c fe f9  f4 ff 31 fd f9 f4 ff 3a  |....;<....1....:|

00000050  31 fd f9 f4 ff 39 3c fe  f9 f4 ff 3b fe f9 f4 ff  |1....9<....;....|

00000060  29 fd f9 f4 ff 38 3d fe  f9 f4 ff 3a fe f9 f4 ff  |)....8=....:....|

00000070  2d fe f9 f4 ff 2a fe f9  f4 ff 27 fd f9 f4 ff 37  |-....*....'....7|

00000080  3b fe f9 f4 ff 37 fe f9  f4 ff 29 fe f9 f4 ff 28  |;....7....)....(|

00000090  fd f9 f4 ff 36 37 fe f9  f4 ff 31 fe f9 f4 ff 2c  |....67....1....,|

000000a0  fe f9 f4 ff 2b fd f9 f4  ff 35 3a fd f9 f4 ff 34  |....+....5:....4|

000000b0  29 fd f9 f4 ff 33 3c fe  f9 f4 ff 34 fe f9 f4 ff  |)....3<....4....|

000000c0  31 fd f9 f4 ff 32 38 fe  f9 f4 ff 36 fe f9 f4 ff  |1....28....6....|

000000d0  35 fe f9 f4 ff 32 fe f9  f4 ff 31 fe f9 f4 ff 30  |5....2....1....0|

000000e0  fe f9 f4 ff 2f fd f9 f4  ff 30 2c fd f9 f4 ff 2f  |..../....0,..../|

000000f0  38 fe f9 f4 ff 30 fe f9  f4 ff 2d fe f9 f4 ff 2b  |8....0....-....+|

00000100  fe f9 f4 ff 27 fd f9 f4  ff 2e 3d fe f9 f4 ff 33  |....'.....=....3|

00000110  fe f9 f4 ff 2b fe f9 f4  ff 26 fe f9 f4 ff 25 fd  |....+....&....%.|

00000120  f9 f4 ff 2d 3e fd f9 f4  ff 2c 38 fe f9 f4 ff 32  |...->....,8....2|

00000130  fd f9 f4 ff 2b 32 fe f9  f4 ff 30 fd f9 f4 ff 2a  |....+2....0....*|

00000140  25 fd f9 f4 ff 29 ff f9  f4 ff 3d fe f9 f4 ff 3b  |%....)....=....;|

00000150  fe f9 f4 ff 36 fe f9 f4  ff 32 fe f9 f4 ff 30 fe  |....6....2....0.|

00000160  f9 f4 ff 28 fe f9 f4 ff  27 fd f9 f4 ff 28 33 fe  |...(....'....(3.|

00000170  f9 f4 ff 2d fd f9 f4 ff  27 36 fe f9 f4 7f ee b4  |...-....'6......|

00000180  1f 65 ed b4 5f ff ff ff  ff dc ff ff ff a2 1f 08  |.e.._...........|

00000190  fc 1f ff 30 fd f9 f4 ff  26 3d fd f9 f4 ff 25 3a  |...0....&=....%:|

000001a0  fe f9 f4 ff 2f fe f9 f4  ff 28 fc f9 f4 ff 3b ff  |..../....(....;.|

000001b0  f7 ef bd 3f 3d 3c fe f9  f4 ff 37 fe f9 f4 00 fe  |...?=<....7.....|

000001c0  ff ff 83 fe ff ff 01 00  00 00 53 2e 3e 01 00 fe  |..........S.>...|

000001d0  ff ff 05 fe ff ff 54 2e  3e 01 06 d9 20 00 00 00  |......T.>... ...|

000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|

00000200

Unknown BootLoader  on sda5

Unknown BootLoader  on sdb2

=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory

hexdump: /dev/sda5: No such file or directory

hexdump: /dev/sdb2: No such file or directory

hexdump: /dev/sdb2: No such file or directory 
```

Edit:
PS. this is what my /dev/sda4 looked like before and after
```
/dev/sda4 123,829,020 146,834,099 23,005,080 5 Extended
/dev/sda4 123,829,082 146,834,099 23,005,018 5 Extended
```

---

