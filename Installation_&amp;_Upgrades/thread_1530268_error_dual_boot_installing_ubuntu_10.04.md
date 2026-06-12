---
title: "error dual boot installing ubuntu 10.04"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by israelariel on 2010-07-13
i have a dell inspiron 1564 i3 with 3 primary partition used by dell system and windows 7 by default. I successfully install ubuntu 10.04 on one extended partition where i create the swap partition, the root / partition and another one for /home i always like to create for the safe of my data.
This partition method is because i can not create another primary partition due the original dell partition.
now if i work on windows the grub disappear and the system can noy find any operating system. if i reinstall the grub with the live cd everything go find until i used windows again.

i reinstall cd by:

sudo mount /dev/sda6 /mnt  (sda6 contain root partition)
sudo grub-install --root-directory=/mnt/ /dev/sda

thanks for your time

---

### Post by Rubi1200 on 2010-07-13
Hi,
you seem to have followed the right steps to re-install GRUB, but as you point out there is still a problem.

Since you have a LiveCD, use it and then click on the link at the bottom of my post.

Follow the instructions there and post the results back here. 

The results will give us a better idea of your setup and help us offer solutions.

Good luck!

---

### Post by scott1541 on 2010-07-13
There might be a problem with the about of partitions you have, I can only have four partitions on my hard drive (sata) and as soon as I add more than four I get problems. I can't even have a swap partition, just boot,win7,ubuntu and win recovery partitions.

I know my explanation of the problem I get is by now means technical but it might help you to resolve your problem, I hope you get it sorted out :)

---

### Post by israelariel on 2010-07-13
thanks for the answer but let me remain you that the problem is when i use windows 7.. when a reinstall the grub i can use ubuntu with no problem at all; the problem is in the moment i use win 7 and reboot or sut down, because when the pc on the sistem found no operating system.

i have three primary partition of the windows, the dell utilities and windows recovery. so i make 3 logical partitions for the root, the swap and home partitions.

i will use the scrip suggested and send the results.
thanks

---

### Post by oldfred on 2010-07-13
I saved all these comments  & links from others:

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.
I un-installed norton and a gateway recovery management application and that seems to have fixed it.
It appears that Acronis does not work with the new inode size of 256 instead of 128. Size 256 is used since Ubuntu 8.10.

---

### Post by israelariel on 2010-07-14
well i was doing the solution presented in the first link and none of last 3 solution work for me, since the first try to locate and disable  the windows program which write in the master boot record (I dont like this solution since it can disable the windows). Anyway i do the other three and no result came out: install the grub on other partition and install the lilo set to booting windows directilly; the installation on the grub legacy activate the dell test program reporting an error which didnt exist if i do the test before booting, booting from the live cd didnt solve this so i have to reinstall all over again. 
in the re installation seems the grub write the mbr on a different part where windows do because everything goes fine. this is a pirric's victorty.
now i need to know how what happen so i can solve the problem in the future when i need to reinstall
thank for your support.

---

### Post by oldfred on 2010-07-14
I have seen several posts where removing the Dell datasafe solved the problem.
The MBR is reserved for Boot info. What is the datasafe program supposed to do?

---

### Post by israelariel on 2010-07-14
olferd can you send me information of the post you write about so check the dell Recovery Tools. 
thanks

---

### Post by oldfred on 2010-07-14
I have posted the same info many times. Often users do not respond. Most that do respond say removing one or the other application works.

[http://ubuntuforums.org/showthread.php?t=1459782&highlight=datasafe](http://ubuntuforums.org/showthread.php?t=1459782&highlight=datasafe)

[http://ubuntuforums.org/showthread.php?t=1475646&highlight=datasafe](http://ubuntuforums.org/showthread.php?t=1475646&highlight=datasafe)

---

### Post by israelariel on 2010-07-14
the report for Boot Info Script 0.55





                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

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

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652   6 FAT16
/dev/sda2    *        178,176    19,310,591    19,132,416   7 HPFS/NTFS
/dev/sda3          19,310,592   332,617,727   313,307,136   7 HPFS/NTFS
/dev/sda4         332,619,774   625,141,759   292,521,986   5 Extended
/dev/sda5         332,619,776   339,984,383     7,364,608  82 Linux swap / Solaris
/dev/sda6         339,986,432   390,766,591    50,780,160  83 Linux
/dev/sda7         390,768,640   625,141,759   234,373,120  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 1999 MB, 1999568384 bytes
62 cabezas, 62 sectores/pista, 1015 cilindros, 3905407 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     3,901,659     3,901,598   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-061E                              vfat       DellUtility                   
/dev/sda2        389C8E1C9C8DD4B2                       ntfs       RECOVERY                      
/dev/sda3        48FE9119FE91007C                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4889d5f1-6bbe-4d88-9805-b646beb6a34e   swap                                     
/dev/sda6        aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9   ext4                                     
/dev/sda7        270884b4-6731-4456-b029-da4f814a78e3   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        49E5-9332                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sdc1        /media/49E5-9332         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, con Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	echo	'Cargando Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	echo	'Cargando Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 389c8e1c9c8dd4b2
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=270884b4-6731-4456-b029-da4f814a78e3 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=4889d5f1-6bbe-4d88-9805-b646beb6a34e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 189.2GB: boot/grub/core.img
 180.8GB: boot/grub/grub.cfg
 189.2GB: boot/initrd.img-2.6.32-21-generic
 189.2GB: boot/initrd.img-2.6.32-23-generic
 189.2GB: boot/vmlinuz-2.6.32-21-generic
 189.2GB: boot/vmlinuz-2.6.32-23-generic
 189.2GB: initrd.img
 189.2GB: initrd.img.old
 189.2GB: vmlinuz
 189.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by israelariel on 2010-07-15
i have the same problem again.

---

### Post by israelariel on 2010-07-15
with the problem n

ow
                Boot Info Script 0.55    dated February 15th,  2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

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

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652   6 FAT16
/dev/sda2    *        178,176    19,310,591    19,132,416   7 HPFS/NTFS
/dev/sda3          19,310,592   332,617,727   313,307,136   7 HPFS/NTFS
/dev/sda4         332,619,774   625,141,759   292,521,986   5 Extended
/dev/sda5         332,619,776   339,984,383     7,364,608  82 Linux swap / Solaris
/dev/sda6         339,986,432   390,766,591    50,780,160  83 Linux
/dev/sda7         390,768,640   625,141,759   234,373,120  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-061E                              vfat       DellUtility                   
/dev/sda2        389C8E1C9C8DD4B2                       ntfs       RECOVERY                      
/dev/sda3        48FE9119FE91007C                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4889d5f1-6bbe-4d88-9805-b646beb6a34e   swap                                     
/dev/sda6        aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9   ext4                                     
/dev/sda7        270884b4-6731-4456-b029-da4f814a78e3   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, con Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	echo	'Cargando Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	echo	'Cargando Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 389c8e1c9c8dd4b2
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=aff2f0a0-5ab6-4e91-bf1a-0c1ff0cb9bd9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=270884b4-6731-4456-b029-da4f814a78e3 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=4889d5f1-6bbe-4d88-9805-b646beb6a34e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 189.2GB: boot/grub/core.img
 180.8GB: boot/grub/grub.cfg
 189.2GB: boot/initrd.img-2.6.32-21-generic
 189.2GB: boot/initrd.img-2.6.32-23-generic
 189.2GB: boot/vmlinuz-2.6.32-21-generic
 189.2GB: boot/vmlinuz-2.6.32-23-generic
 189.2GB: initrd.img
 189.2GB: initrd.img.old
 189.2GB: vmlinuz
 189.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc

---

### Post by kooia on 2010-07-15
Had the same problem, but from upgrading.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

That's how I fixed it.

---

### Post by israelariel on 2010-07-15
kooia the report the web you send me is totally different from mine.. are you sure you have the same problem?

---

### Post by oldfred on 2010-07-15
kooia's problem is grub was installed in the windows boot sector. You do not have that problem from the boot script results which look ok as far as I can see.

I think you still have some application in windows that corrupts the MBR when you are in windows.

---

### Post by israelariel on 2010-07-15
i will looking with the first post you send me the windows aplication that is messing with  the MBR.

---

### Post by Cason on 2010-07-15
My dad was having somewhat similar problems the other day; apparently Windows 7 combined with Grub doesn't play very nice when there's a ton of partitions. If there are more than 4 OS partitions, Windows 7 seems to go nuts. We were able to fix dad's by simply eliminating some of the partitions. Your config file says you've got 7. Considering the heck my dad and I went through earlier this week, you might try eliminating some of them and seeing if that fixes your problem.

---

### Post by israelariel on 2010-07-15
I will like to solve the problem without uninstall anything and if i do i will like to be sure on that
look what i do : referer to the solution: looking which windows software is writing on the MBR:

************************************************************************
 Solution 1 Disable the Window Program Writing to the MBR

See what happens if you disable or uninstall programs in Windows which might be writing to extended MBR. You also might be able to determine the program by looking at a hexdump of the extended MBR. Open a terminal in your Linux OS and type

  sudo dd if=/dev/sda of=/good_mbr  count=63

(this assume that you are booting from /dev/sda, otherwise you might have to use /dev/sdb, /dev/sdc, ...)

Next time grub fails to boot, boot into a Linux Live CD, type

   sudo dd if=/dev/sda of=/bad_mbr  count=63

and compare the two files:

   sudo mount /dev/sda3 /mnt
   sudo hexdump  -C /mnt/good_mbr
   sudo hexdump  -C /bad_mbr

(here /dev/sda3 needs replace by the device name of the Ubuntu partition) 
************************************************************************
NOW .... I HAVE THE TWO FILES good_mbr AND bad_mbr...I CAN NOT UNDERSTAND THE RESULT OF HEXDUMP COMMAND . HOW DO I DO THAT?

THANK AGAIN ALL THE PEOPLE WHO IS TRYING HELP ME.

---

### Post by israelariel on 2010-07-15
i did the two file indicated on the last post and there was a differences between the addresses 00005e00 and 00005ff0
THESE IS THE REPORT:

*************************************************************************** 
                   GOOD
*************************************************************************** 
00005e00  6c f8 3b c9 e5 52 72 9f  50 7a d3 ec 1b cd 99 fd  |l.;..Rr.Pz......|
00005e10  c2 bc c1 d5 ba 10 45 a5  db 16 5d 0d 79 96 6d 90  |......E...].y.m.|
00005e20  a2 84 37 69 1e e4 df dd  74 76 64 ac c2 85 82 43  |..7i....tvd....C|
00005e30  0c aa 6b 0d 71 7e 3a 00  7c 4d 76 bf 1d f0 3c 87  |..k.q~:.|Mv...<.|
00005e40  4a b1 3f 87 35 e7 3d b9  d8 fa 4f 79 b3 4e ab d6  |J.?.5.=...Oy.N..|
00005e50  40 8e a8 be b8 00 ba 04  9c c6 ac eb 70 04 59 82  |@...........p.Y.|
00005e60  f7 ca 18 f8 5c 35 eb dc  a7 c5 03 95 8d f4 25 47  |....\5........%G|
00005e70  b3 c5 dc e4 74 1a fd 56  d1 8b 04 5d fd cf 6a 3e  |....t..V...]..j>|
00005e80  5e bd dc 65 34 e5 39 ce  aa 08 c2 81 82 16 9a 71  |^..e4.9........q|
00005e90  7d 06 92 4b 00 0f 98 de  cb d7 62 54 82 34 fa fd  |}..K......bT.4..|
00005ea0  23 e2 ba e1 08 48 16 67  eb 7f ff 56 4d 05 62 14  |#....H.g...VM.b.|
00005eb0  06 18 55 7d 39 75 7f 21  89 bd ca bd 2d 71 37 24  |..U}9u.!....-q7$|
00005ec0  e4 6b 4f cb e3 45 20 5e  a5 8d 87 fc ba 02 9f c7  |.kO..E ^........|
00005ed0  2d 8c 14 ec 0b 07 20 02  78 f4 b2 44 5d d6 1c bb  |-..... .x..D]...|
00005ee0  04 57 85 1a 35 9b 8f 4f  61 26 a4 3e 6b bf 88 c0  |.W..5..Oa&.>k...|
00005ef0  e0 72 bc 0e ab 42 a9 38  43 bf 8c c5 ac 1c 27 a1  |.r...B.8C.....'.|
00005f00  47 b0 05 8e 3f 12 7f 30  4c 4a 06 46 cf a7 6a a7  |G...?..0LJ.F..j.|
00005f10  ad 3c 8f c1 ae 2e 5e 76  32 fe 2b 19 dc bd 9e b0  |.<....^v2.+.....|
00005f20  7b d8 e1 dd 36 f0 bd 4a  15 e9 14 54 05 52 a8 cf  |{...6..J...T.R..|
00005f30  f8 1b 13 fe 8e b2 2e 12  61 1f 9f e5 11 e8 c3 e2  |........a.......|
00005f40  81 c5 1c bd 61 55 f1 ed  ad fd 12 22 fb f8 4c fc  |....aU....."..L.|
00005f50  87 46 10 fb 7d f0 d2 9f  d3 6b a5 66 59 22 97 7b  |.F..}....k.fY".{|
00005f60  9b e5 80 44 5b 56 88 6f  e4 94 d9 2e ac dc fe 87  |...D[V.o........|
00005f70  ba d0 15 20 be c1 22 7c  40 5b 6a e9 b9 6f 8b fe  |... .."|@[j..o..|
00005f80  dd 75 a4 63 d2 3d e2 eb  ad 20 fd c9 ec 75 49 31  |.u.c.=... ...uI1|
00005f90  8e ce ae 5d 71 8d e2 8b  8e 12 0c 3e e9 33 17 ce  |...]q......>.3..|
00005fa0  1d ff fd 39 87 08 99 ec  65 52 2c 74 96 69 1a db  |...9....eR,t.i..|
00005fb0  f5 21 34 b4 82 4c 3e ad  48 49 1c d5 9c e3 89 df  |.!4..L>.HI......|
00005fc0  8a 07 0c 55 e5 79 4b 26  c7 fb be e4 92 c0 e6 a5  |...U.yK&........|
00005fd0  45 37 88 b8 4b c7 16 b1  75 0b 4b da 55 b7 f1 e3  |E7..K...u.K.U...|
00005fe0  78 f2 e4 e0 3e 7d a1 58  13 be f5 8a fb c8 f4 83  |x...>}.X........|
00005ff0  11 27 fc 0b 9b 33 71 45  48 06 81 49 f2 cd 42 95  |.'...3qEH..I..B.|

*************************************************************************** 
                   BAD
*************************************************************************** 
00005e00  54 35 ee 1a 0a 2a ee 8e  26 fe c3 b5 4f 69 80 87  |T5...*..&...Oi..|
00005e10  57 17 74 bf 50 b4 37 05  37 be bb 08 9e cf 73 e8  |W.t.P.7.7.....s.|
00005e20  0f 4f d8 61 17 20 77 81  ad 2d c8 ee 75 89 69 85  |.O.a. w..-..u.i.|
00005e30  f9 77 15 45 6f 36 35 43  4e 4e 46 35 4e 36 31 30  |.w.Eo65CNNF5N610|
00005e40  30 30 30 30 30 30 30 31  32 d9 ef 5d 24 0b 32 d6  |000000012..]$.2.|
00005e50  d3 a3 7e f6 7c b6 09 22  34 0b 3b 3a 47 1a b6 58  |..~.|.."4.;:G..X|
00005e60  a1 35 0a 8e 1d 65 19 72  ed ef 9e f3 29 2a c6 d2  |.5...e.r....)*..|
00005e70  fd f0 cc 9b c5 fa 9f 90  e6 dc 62 60 ac 62 ed 10  |..........b`.b..|
00005e80  2a aa 8d 81 31 a4 1e 6a  7b cb db b6 13 d6 79 a3  |*...1..j{.....y.|
00005e90  15 a8 c3 8d 5a bf 7e b8  a2 6e 3b 9d 48 13 c1 73  |....Z.~..n;.H..s|
00005ea0  af ac 68 06 d3 ee 60 94  3a be 57 3f b7 b3 00 ca  |..h...`.:.W?....|
00005eb0  3a 0a 47 ba 91 27 e6 00  58 0b 84 d4 13 e9 19 6b  |:.G..'..X......k|
00005ec0  95 b2 50 93 3c 3f 0f fe  1c 8d df 3a 2d 18 f2 9b  |..P.<?.....:-...|
00005ed0  12 c6 63 25 82 03 79 1f  fd f1 22 7c 44 d8 bf b7  |..c%..y..."|D...|
00005ee0  c1 27 23 b8 e5 42 3f 0d  1c 70 6b 6a d1 91 d0 3e  |.'#..B?..pkj...>|
00005ef0  c4 84 c4 e2 8b 5e bd 23  0e d5 99 22 5b 04 64 67  |.....^.#..."[.dg|
00005f00  9d 6c df 93 0f 5d 69 f6  b3 15 92 a3 45 5d 79 2e  |.l...]i.....E]y.|
00005f10  fe dd bd 1f 4d 74 1d 6c  84 dc 17 62 9a c5 1b 62  |....Mt.l...b...b|
00005f20  1a d4 aa d8 ba a3 6a c4  62 9d 91 cf 6a ef b3 ba  |......j.b...j...|
00005f30  71 5f c3 18 ad 37 67 ae  e5 a2 68 f1 09 aa db e1  |q_...7g...h.....|
00005f40  28 a9 ca 51 32 62 81 d5  2e 9d 4b 6c e9 f0 a8 87  |(..Q2b....Kl....|
00005f50  d0 0e f0 9f d5 c9 cd 74  b4 37 81 97 6e f5 80 73  |.......t.7..n..s|
00005f60  3e 26 2c d8 7d 17 d4 de  1b 1f c1 8a 30 ba 65 8d  |>&,.}.......0.e.|
00005f70  55 5c 83 9b b1 05 e6 99  fb 1c f8 af d9 1c c8 78  |U\.............x|
00005f80  58 7a df df 6e f3 ea e4  b8 9d 9f cf 6e df da 97  |Xz..n.......n...|
00005f90  bc 37 dc 87 f3 f5 ac 4f  49 4a 09 a7 9e c6 d9 27  |.7.....OIJ.....'|
00005fa0  75 4a 18 6b 96 60 b0 c3  92 0c b1 74 18 20 5f 46  |uJ.k.`.....t. _F|
00005fb0  c6 fa 82 70 10 dc fe 9a  2f a9 11 04 52 d3 b8 89  |...p..../...R...|
00005fc0  16 ae 2e 13 4d f5 f7 a9  40 ce 69 46 63 75 2c 0d  |....M...@.iFcu,.|
00005fd0  b8 fa 9f f8 c0 2d 1f 53  41 1c 15 dc 4e 54 d2 7d  |.....-.SA...NT.}|
00005fe0  c2 b2 9d 81 ae 04 72 19  d6 be d9 27 4f 8a 5e b2  |......r....'O.^.|
00005ff0  da 7b 01 57 82 90 b4 a6  9b 74 b9 db b1 8d 75 b4  |.{.W.....t....u.|

******************************************************************

WHAT ITS MEANS?

---

### Post by israelariel on 2010-07-18
HERE IS THE SOLUTION...:

the problems is that you have to o uninstall delldatasafe on windows..  ....the method is the way you want.. it means by reinstalling grub with a live cd or reinstalling MBR with windows cd recovery then entering windows and uninstall the delldatasafe, then you have to reinstall grub, this time only by ubuntu live cd or you wont be able to see linux (of course). Problem solve.
any way thanks for the help

---

