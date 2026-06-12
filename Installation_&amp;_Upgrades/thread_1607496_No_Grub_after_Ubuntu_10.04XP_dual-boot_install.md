---
title: "No Grub after Ubuntu 10.04/XP dual-boot install"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by 55Rebel on 2010-10-27
Hey guys,
Having a little bit of an issue with ubuntu 10.04/XP dual-boot install.

When computer starts up it goes right into win xp; no grub, no error. 

For those of u that may have the time, help would be much appreciated.  THX!

The following is the mbr info from the 'Boot Info Script' tool:
(It's all Greek to me ...mostly :P

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #9 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 771955443.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb1 starts at sector 16128.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   361,815,929   361,815,867   7 HPFS/NTFS
/dev/sda2         361,816,054   976,768,064   614,952,011   f W95 Ext d (LBA)
/dev/sda5         904,202,460   976,768,064    72,565,605   7 HPFS/NTFS
/dev/sda6         566,837,523   771,955,379   205,117,857   7 HPFS/NTFS
/dev/sda7         361,816,056   566,837,459   205,021,404   7 HPFS/NTFS
/dev/sda8         771,955,443   792,582,839    20,627,397   b W95 FAT32
/dev/sda9         792,584,192   899,536,895   106,952,704  83 Linux
/dev/sda10        899,538,944   904,185,855     4,646,912  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,128   205,969,364   205,953,237   7 HPFS/NTFS
/dev/sdb2         205,969,365   234,436,544    28,467,180   f W95 Ext d (LBA)
/dev/sdb5         205,969,428   234,436,544    28,467,117   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       bae93bf4-49c5-403f-ba03-fd35d9b4f916   swap                                     
/dev/sda1        4A28DEDD28DEC75B                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        44F0FFAF061B0C08                       ntfs                                     
/dev/sda6        74A86504217C18AA                       ntfs       Data_2                        
/dev/sda7        3E3A30A63FF4C6DD                       ntfs       Data_1                        
/dev/sda8        00E7-5505                              vfat       Share_XP/Li                   
/dev/sda9        bd83baa9-a455-4846-9774-226730a6795a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CFC6B47519C968E5                       ntfs       Data                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        16415272DA945769                       ntfs       restoreXP                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/4A28DEDD28DEC75B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set bd83baa9-a455-4846-9774-226730a6795a
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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set bd83baa9-a455-4846-9774-226730a6795a
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set bd83baa9-a455-4846-9774-226730a6795a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=bd83baa9-a455-4846-9774-226730a6795a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set bd83baa9-a455-4846-9774-226730a6795a
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=bd83baa9-a455-4846-9774-226730a6795a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set bd83baa9-a455-4846-9774-226730a6795a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set bd83baa9-a455-4846-9774-226730a6795a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 4a28dedd28dec75b
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=bd83baa9-a455-4846-9774-226730a6795a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=bae93bf4-49c5-403f-ba03-fd35d9b4f916 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 451.0GB: boot/grub/core.img
 433.9GB: boot/grub/grub.cfg
 451.0GB: boot/initrd.img-2.6.32-24-generic
 451.0GB: boot/vmlinuz-2.6.32-24-generic
 451.0GB: initrd.img
 451.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2...

[the rest not included. Hopefully not needed, hex code & all]
```

---

### Post by oldfred on 2010-10-28
You missed the beginning of the results.txt as that shows what boot loader is installed in each drive.

Please post inside code (#) tags. You highlight the entire results.txt after you have pasted it in your message and in the edit panel above on the right is a # or code tag auto inserter. You can hover over the icons in the edit menu for explanation. You have to manually insert code tags in your previous post. If I try to show the tags they get converted to code tags and disappear. 

But it is like [ code] insert data here [ /code] without space in the bracket, this becomes:
```
 insert data here 
```

If you are directly booting windows and did not choose where to install grub, it just may have installed to the other drive. Otherwise you will need to reinstall grub2. The first part of the results.txt shows what boot loader is in each drive. Check that and in BIOS try booting the other drive. If not post entire results.txt and we can suggest how to reinstall grub2.

---

### Post by 55Rebel on 2010-10-28
Thanks oldfred.
My bad, big help i am...

Updated the results.txt above; inserting the missing text.


One stupid question though, 
what's with the "Boot sector type: Windows Vista/7"?

```
sda5: __________________________________________________ _______________________

File system: ntfs
**Boot sector type: Windows Vista/7**
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sda6: __________________________________________________ _______________________

File system: ntfs
**Boot sector type: Windows Vista/7**
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sda7: __________________________________________________ _______________________

File system: ntfs
**Boot sector type: Windows Vista/7**
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:
```

---

### Post by garvinrick4 on 2010-10-28
sda drive grub2 is in sda9 so this is for sda.
Put in install cd and use try ubuntu and open a terminal and copy and paste
```
sudo mkdir /media/root
``````
sudo mount /dev/sda9 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
```Boot into sda in Ubuntu
```
sudo update-grub
```Now sdb I hope it is external. If it is unplug it for time being.
Looks like grub2 tried to be installed in sdb by mistake.

---

### Post by 55Rebel on 2010-10-28
> **garvinrick4 said:**
> 
Now sdb I hope it is external. If it is unplug it for time being.

No, it's an internal drive (guess i could still disconnect it).  Problem!?
Must be from old install of grub previously before tthis newer 500 gig drive.


Thx

---

### Post by garvinrick4 on 2010-10-28
> **55Rebel said:**
> No, it's an internal drive (guess i could still disconnect it).  Problem!?
Must be from old install of grub previously before tthis newer 500 gig drive.


Thx No problem will still boot sda fine just did not want any trouble from it there was an attempt to put grub2 in there from a partition that did not exist on sdb. When you update-grub it makes a new config file and if it is plugged in will attempt to read it when it probes for drives and operating Systems. Not to much on sdb a bit of a mess. Reformat
and start over on that guy, sdb I mean.
 oldfred must be offline or busy or I would not jump in the middle but get your system working.

---

### Post by oldfred on 2010-10-28
It looks like it installed grub to sdb. If in BIOS you select the 120GB drive do you boot Ubuntu?

NTFS partitions have to have a boot sector set up. There are two versions one for XP and before and another for Vista/7. The NTFS partition does not work without the boot sector, but you cannot directly boot windows in logical partitions.

Did you want to install grub into sda?

---

### Post by 55Rebel on 2010-10-28
Success!
the sdb drive was the culprit...
Disconnected sdb as garvinrick4 suggested, and reinstalled ubuntu. 

Grub is up and running now and everything is working like it should.

I'm now in the process of transferring all wanted files from sdb and reformatting it.

Thanks for the help guys, u rock!


Mark

---

### Post by garvinrick4 on 2010-10-29
55rebel we did nothing you reinstalled and put grub in sda where it belonged. I suggested you fix the install you had by replacing the grub into sda looking in sda9 where it resided.
You chose to reinstall and did it correctly. Enjoy your Ubuntu and take credit for your own
installation, you did it.

---

