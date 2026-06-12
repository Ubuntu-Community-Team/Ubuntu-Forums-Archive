---
title: "Can't boot in Windows 7 after upgrading to Lucid"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vogabe on 2010-04-14
Hi,

when I upgraded to Lucid I made the terrible mistake to install Grub 2 to all my partitions. After realising this fault I restored the windows bootloader with the BootRec.exe /FixBoot command.

But nog when I select Windows 7 on startup I just get a black screen with a white cursor blinking.

This is my Boot Info Script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 140199936. But according to the info from 
                       fdisk, sda1 starts at sector 71762355. According to 
                       the info in the boot sector, sda1 has 122654719 
                       sectors, but according to the info from fdisk, it has 
                       191092300 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 284671 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 284671 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 200.0 GB, 200049647616 bytes
255 koppen, 63 sectoren/spoor, 24321 cilinders, totaal 390721968 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     71,762,355   262,854,655   191,092,301   7 HPFS/NTFS
/dev/sda2         262,855,530   390,716,864   127,861,335   f W95 Ext d (LBA)
/dev/sda5         262,855,593   390,716,864   127,861,272   7 HPFS/NTFS
/dev/sda3                  63    68,726,069    68,726,007  83 Linux
/dev/sda4          68,726,070    71,762,354     3,036,285  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BABAB995BAB94E9F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        70d2b8c6-b226-4042-88d1-32c2c729b83a   ext4                                     
/dev/sda4        b996178e-2e44-4fb8-bb61-daa94496c321   swap                                     
/dev/sda5        90262FD4C4700794                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/data              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/windows           fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/cdrom0            udf        (rw,nosuid,nodev,utf8,user=leendert)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 70d2b8c6-b226-4042-88d1-32c2c729b83a
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 70d2b8c6-b226-4042-88d1-32c2c729b83a
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry "Ubuntu, met Linux 2.6.32-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 70d2b8c6-b226-4042-88d1-32c2c729b83a
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=70d2b8c6-b226-4042-88d1-32c2c729b83a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-20-generic
}
menuentry "Ubuntu, met Linux 2.6.32-20-generic (herstelmodus)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 70d2b8c6-b226-4042-88d1-32c2c729b83a
	echo	Linux 2.6.32-20-generic laden ...
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=70d2b8c6-b226-4042-88d1-32c2c729b83a ro single 
	echo	Initiële ramdisk laden ...
	initrd	/boot/initrd.img-2.6.32-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 70d2b8c6-b226-4042-88d1-32c2c729b83a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 70d2b8c6-b226-4042-88d1-32c2c729b83a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
menuentry "Windows 7" {
set root=(hd0,1)
chainloader (hd0,1)+1
}

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=70d2b8c6-b226-4042-88d1-32c2c729b83a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=b996178e-2e44-4fb8-bb61-daa94496c321 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1   /media/windows   ntfs-3g   user,fmask=0111,dmask=0000   0   0
/dev/sda5   /media/data   ntfs-3g   user,fmask=0111,dmask=0000   0   0

=================== sda3: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
   8.5GB: boot/initrd.img-2.6.32-20-generic
   6.0GB: boot/vmlinuz-2.6.32-20-generic
   8.5GB: initrd.img
   6.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by lisati on 2010-04-14
Have a look here: [http://ubuntuforums.org/showthread.php?p=9114223#post9114223](http://ubuntuforums.org/showthread.php?p=9114223#post9114223)

---

### Post by Vogabe on 2010-04-14
I restored the mbr with the command BootRec.exe /Fixmbr but after that when I booted I get the black screen right from the start. I now restored the grub loader.

So it's the Windows 7 bootloader that's corrupt for sure. I now gonna try a disk check of the windows 7 partition and then try to restore the boot once again. Hope that that works.

Other suggestions are still welcome

---

### Post by kansasnoob on 2010-04-14
I've had about a 90% success rate following Meierfra's suggestion using testdisk here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Vogabe on 2010-04-14
Nope no luck with the testdisk application. It says boot sector status OK and the tab backupBS isn't displayed.

But it's the boot sector info that concerns me. I think it isn't normal that the bootsector thinks the partition starts on another sector then fdisk. It would explain why I get zero output. But how can I fixe this?

```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 140199936. But according to the info from 
                       fdisk, sda1 starts at sector 71762355. According to 
                       the info in the boot sector, sda1 has 122654719 
                       sectors, but according to the info from fdisk, it has 
                       191092300 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

```

---

### Post by kansasnoob on 2010-04-14
This may be worth a try:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Vogabe on 2010-04-14
I tried to overwrite the Boot Sector with testDisk.

Now I can boot in windows but it gives me a bluescreen on start-up.
I have used the Windows 7 cd-rom to repair the installation but this only resulted in a corrupted NTFS. I have fixed that but still get a bluescreen when windows loads. The recovery disk says he found a fault but can't fix it.

---

### Post by Vogabe on 2010-04-15
I give it up.
Bluescreen says: "Verification of a known dll failed" and in safe mode it hangs when it tries to load classpnp.sys .
I think the partition is so corrupted it is better to just do a clean install of Windows 7.

---

