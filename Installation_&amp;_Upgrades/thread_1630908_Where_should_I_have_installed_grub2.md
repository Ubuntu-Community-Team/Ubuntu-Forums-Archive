---
title: "Where should I have installed grub2?"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-11-25
Greetings, all.

I have another concise-as-usual question for the Gurus out there.

I bought a new Dell AMD-64-based Windows-7 box in June and was unable to adjust partitions until now, when the System Rescue CD solved 2 problems I was unable to explain to Dell.  That's just my excuse for waiting this long to install Ubuntu.  (Also waiting for 10.10)

Here is my disk layout:
[LIST]
[*]Windows-7 comes with 3 partitions installed:
[*]Dell Utility (FAT-16)  ~ 40GB
[*]Recovery (ntfs) ~ 11GB
[*]The OS (ntfs) - the rest of the 1-TB disk.  Known as /dev/sda3 to gparted.
[*]An extended partition, /dev/sda4, that I created.  See below.
[/LIST]

I used Dell disk management to shrink that third partition by 400GB and used Gparted-Live to create an extended partition in that 400GB space. The main sub-partition I am interested in is
/dev/sda5 - 4GB (ext3), which I have set as my root mount point.

I have attached the gparted screen shot.

Now, that's what I did before I started to install Ubuntu.

During the install, it prompted me where to install the Grub.  it prompted with the name of the hard drive, the Samsung <yada yada>.  Coward that I am, I clicked the down-arrow and selected /dev/sda5.  I also designated that the root mount point.

Result:
When I boot the machine, it boots into Windows, like nothing has happened.  The way I got into Ubuntu now was by booting from the SuperGrub Disk 1.98 and selecting "Detect any OS", opting for the Linux Kernel at the next step.

Duh, that not what I had in mind.:confused:


Where should I have installed it?  I was terrified of having it overwrite my MBR on the hard drive.

And now that I DO have the SuperGrub disk, how do install the Grub back into where it belongs?  And where is that anyway?  On the Samsung as it originally wanted to do it?  (I do have Windows recovery disks handy but I'd hate to have to put them to the test.)

I have other questions as well but let's handle this basic one first.

---

### Post by jacob.david on 2010-11-25
You should have installed it on sda1. Don't worry about overwriting MBR, as GRUB is smart enough to detect Windows and add it to the menu. Having said that I personally faced some issue in setting up the dual boot with Windows 7. I hope you don't face any problem and everything goes smoothly.

---

### Post by wilee-nilee on 2010-11-25
That is a starange set up at the least, don't worry about the boot loading the MBR this is child's play one command with MS 2 with Linux for grub2.

So that being said you can't put anything in the unallocated as you have the maximum amount of partitions allowed on a single HD 3 primary types and one extended. That extended if you plan to have all Linux and even a shared NTFS I think (get confirmation here) should just cover the whole area past the last NTFS.

In the extended you can put as many partitions you can fit, a whole bunch of different bootable Linux type if you wanted. A plethora, a unlimited amount of partitions.;)

sda1 sda2 , and sda3=3 partitions the limit is 4 of any type unless inside a extended, or a raid setup; you don't want raid.

> **jacob.david said:**
> You should have installed **it** on sda1. Don't worry about overwriting MBR, as GRUB is smart enough to detect Windows and add it to the menu. Having said that I personally faced some issue in setting up the dual boot with Windows 7. I hope you don't face any problem and everything goes smoothly.

First what is it and sda1 is a firmware partition.

---

### Post by Quackers on 2010-11-25
Grub is normally installed to the mbr of sda - not in a numbered partition. It may (or may not :-)) , interfere with Windows booting, but that is fixable with a windows repair disc (not usually the recovery disc though).

---

### Post by rpaskudniak on 2010-11-25
Quackers stated:

> **Quackers said:**
> Grub is normally installed to the mbr of sda - not in a numbered partition. It may (or may not :-)) , interfere with Windows booting, but that is fixable with a ***[COLOR="Blue"]windows repair disc[/COLOR]*** (not usually the recovery disc though).

Just to hang on to the words I highlighted:

I thought the Windows Recovery DVD's I burned he other day ***are*** the repair disks.  If these do not recover the MBR, how do I burn the Windows Repair Disc that you described?  Though I suspect that both the Windows Installation DVD (Recovery Panel/fixmbr) and System Rescue CD will fix the the MBR for me.

Bottom line for me:  I should restart the install process before I commit any serious downloads to Ubuntu.  And allow it to install in the default location.

Thank you all for this apparent consensus.

BTW, Quackers, I like the avatar.  I was considering "Dr. Quackenbush" before deciding on my screen name/avatar.

---

### Post by Quackers on 2010-11-25
The Recovery Discs you have created are effectively a copy of the recovery partition on your hard drive and may prove invaluable to you in the future. Keep them safe :-)  However, they may not offer a full complement of repair tools, such as command prompt or startup repair (which may be needed to fix an mbr).

BTW I think Quackenbush is a distant relation of mine :-)

---

### Post by Quackers on 2010-11-25
It is still possible to re-install grub to the mbr of sda, but first I would suggest booting from the live cd/usb and selecting "try ubuntu" and when the desktop loads connect to the internet.
Then please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications menu > Accessories > terminal) and copy/paste this command into it
```
 sudo bash ~/Desktop/boot_info_script*.sh
```
The script will run then produce a results.txt file on your desktop. 
Please copy the contents of that file and paste them into your next post using CODE tags. For CODE tags click on New Reply rather than quick reply and then click on the # symbol in the toolbar.

This will give a fuller view of your system.  Once this is done stay in the live cd environment, where the necessary commands to install grub can be used.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by rpaskudniak on 2010-11-26
Quackers,

I'ts getting late for me and I may not have the chance to get back to this for a few days.  However, I just had an epiphany:

I was looking at the options in the [Partitions] drop-down menu and notices the check-box for []Boot.  Only one partition can have this flag on; that partition happens to be /dev/sda2, the ntfs RECOVERY partition.

Now I did install the grub on /dev/sda5.  Suppose I were to set the Boot flag on /dev/sda5, which would clear the Boot flag from /dev/sda2. Grub is grub no matter where it's located, I think.

What do you think?

As for pasting the RESULTS.txt - I had mercy on the other readers of this forum and have sent it as an attachment.  It is over 400 lines long! I'm looking into it with vim now, with an interest to making sure Windows is still the default OS.  (I printed the [grub2 community documentation]("https://help.ubuntu.com/community/Grub2") )

---

### Post by Quackers on 2010-11-26
If you use CODE tags it appears like this
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 1134686456 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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
    Boot files/dirs:   /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    22,286,335    22,204,416   7 HPFS/NTFS
/dev/sda3          22,286,336 1,134,321,663 1,112,035,328   7 HPFS/NTFS
/dev/sda4       1,134,325,758 1,478,266,879   343,941,122   5 Extended
/dev/sda5       1,134,325,760 1,142,714,367     8,388,608  83 Linux
/dev/sda6       1,142,716,416 1,176,270,847    33,554,432  82 Linux swap / Solaris
/dev/sda7       1,176,272,896 1,209,827,327    33,554,432  83 Linux
/dev/sda8       1,209,829,376 1,344,047,103   134,217,728  83 Linux
/dev/sda9       1,344,049,152 1,478,266,879   134,217,728  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,794,175    15,794,113   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   268,430,084   268,430,022   7 HPFS/NTFS
/dev/sdc2         268,430,085   469,756,664   201,326,580   7 HPFS/NTFS
/dev/sdc3         469,756,665   625,137,344   155,380,680   5 Extended
/dev/sdc5         469,756,728   603,979,739   134,223,012  83 Linux
/dev/sdc6         603,979,803   625,137,344    21,157,542  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        B6248003247FC4C1                       ntfs       RECOVERY                      
/dev/sda3        9AF08259F0823B8F                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        831b4fa3-b7eb-4daf-83f4-5edcb625795c   ext3       Ubuntu-Boot                   
/dev/sda6        b131bed3-9334-4baa-9573-bf15c9465e83   swap       swap                          
/dev/sda7        0902758e-eda1-4a63-bb83-ad141ce4dc22   ext2       Ubuntu-tmp                    
/dev/sda8        23b67cc2-a31f-4881-8af8-839eb1035b78   ext3       Ubuntu-Users                  
/dev/sda9        669ccf70-1b6e-4c65-9c69-9e4e1d21af3e   ext3       Ubuntu-VAR                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2469-090C                              vfat       CORSAIR                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        441FCCDB2C9E0892                       ntfs       Backup                        
/dev/sdc2        129163807CBCA1CC                       ntfs       Media                         
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        06382323-3fe8-4b1f-a0ba-5338134776cc   ext3       DB-ifmx                       
/dev/sdc6        f5f5d92d-7b16-4f47-9403-8789efa6534c   ext3       DB-pg                         
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdc5        /media/DB-ifmx           ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc6        /media/DB-pg             ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/CORSAIR           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc2        /media/Media             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=831b4fa3-b7eb-4daf-83f4-5edcb625795c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=831b4fa3-b7eb-4daf-83f4-5edcb625795c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=831b4fa3-b7eb-4daf-83f4-5edcb625795c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=831b4fa3-b7eb-4daf-83f4-5edcb625795c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 831b4fa3-b7eb-4daf-83f4-5edcb625795c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set b6248003247fc4c1
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=831b4fa3-b7eb-4daf-83f4-5edcb625795c /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b131bed3-9334-4baa-9573-bf15c9465e83 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 580.9GB: boot/grub/core.img
 580.9GB: boot/grub/grub.cfg
 581.0GB: boot/initrd.img-2.6.35-22-generic
 581.0GB: boot/initrd.img-2.6.35-23-generic
 580.9GB: boot/vmlinuz-2.6.35-22-generic
 580.9GB: boot/vmlinuz-2.6.35-23-generic
 581.0GB: initrd.img
 581.0GB: initrd.img.old
 580.9GB: vmlinuz
 580.9GB: vmlinuz.old

======================== sdc2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
```

---

### Post by Quackers on 2010-11-26
Only Windows uses boot flags.
From within the live cd open a terminal and copy/paste these commands into it, one line at a time and press enter.. You may need to enter your password after the first line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
The second line should report that it ran without any reported errors.
If it does type into the terminal
```
sudo update-grub
```
and hit enter. Then watch the terminal as grub.cfg is configured to see if Windows 7 (loader) appears.
After this reboot and you should see the grub menu where you can choose to boot each OS. Try both to ensure that they boot ok.

---

### Post by rpaskudniak on 2010-11-26
Well, Quackers, that was one little voyage of discovery.  I am currently booted from the Ubuntu-Live CD.  It failed to boot from /dev/sda5 because it was missing some file, presumably the one referred to in the quoted text. (BTW, I didn't know you could scroll the quoted text like that.)

```
sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 1134686456 of the same hard drive
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```


However, the commands you suggested did not come out error-free:
```
**ubuntu@ubuntu:~$** sudo mount /dev/sda5 /mnt
**ubuntu@ubuntu:~$** sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

**ubuntu@ubuntu:~$** sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

BTW, I did the above after I changed the boot flag back to /dev/sda2.

OK, so gparted ain't perfect in allowing me to do set the flag on a non-ntfs partition.

In any case, I need to reboot to Windows now, if for no better reason than to see if I still can.  As I indicated earlier, I have not committed much to this Ubuntu installation; I can do it over with no loss of data.  Still, it's a better hack if I can avoid that cowardly way out.

This ain't finished yet, friend. :guitar:

---

### Post by Quackers on 2010-11-26
The boot flag is an irrelevance to Linux and Gparted.
I have seen Flexnet causing boot failures before. I have no idea what it is but I know that the last time I saw it causing problems the OP was advised to get rid of it.
Try rebooting. You may now get a grub menu, or worse a grub prompt. If Windows doesn't boot you may need to download a Windows repair cd and run the startup repair. Or alternatively we could see if Lilo will install (which can boot Windows) but I hope it won't come to that.

---

### Post by rpaskudniak on 2010-11-26
Quackers,
After consuming 1/2 pound of gobblers, my brain seems unaffected.  Should I worry? :p

Good news and mediocre news:

Good news: I got the Grub menu and on first reboot, chose windows.  On the next reboot I allowed the default Ubuntu to come up.

Mediocre news: Windows is at the bottom of the menu.  I would rather have it at the top, where it will be the default.  That's be virtue of the directive in /etc/defailt/grub:```
GRUB_DEFAULT=0
```
As I understand the doc, if I want Windows at the top (and I have no intention of installing yet another OS here, though I have the Fedora DVD sitting on my desk). I would rename **[FONT="Courier New"]30_os-prober[/FONT]** to something like NO-WAY-30_os-prober and turn off its "executable" flags so that it does not get executed.  Then I would copy the code to 09_Windows so that it would generate the menuentry code first and would therefore be at the top of the list.

Why not just rename 30_os-prober?  In case I decide I *do* want to add Fedora to the mix. Also, since the new 09-Windows has only one function, I would like to pare it down to remove the now-irrelevant code.  But until I do, that code is dead yeast in the beer; messy but harmless.

Again, I am soliciting your opinion.  (I have already established that what sounds like a good idea will not necessarily pan out as such.)

So what do you think of my suggestion?

BTW, I have edited /etc/default/grub to set the countdown timer to 30 seconds and [FONT="Courier New"]GRUB_HIDDEN_TIMEOUT_QUIET=false[/FONT] so that I can see what's going on.

Thank very much for your help, Quackers.

---

### Post by Quackers on 2010-11-26
Since you have edited /etc/default/grub already, you can do so again if you wish :-) to change the default booting option to the number which Windows is.
Or a much easier way is to install Startup Manager via Synaptic Package Manager and change the default OS from there.
Did you run sudo update-grub in the terminal after making the changes to /etc/default/grub?
This makes the changes take effect.

I must admit to being relieved that you can boot both OSes. It was looking a bit dodgy for a while :-)

As far as I'm aware you only turn off os_prober if you have made a custom menu, or if you just don't want to pick up any OSes any more. Not something I'd want, personally.

---

### Post by rpaskudniak on 2010-11-27
> **Quackers said:**
> Since you have edited /etc/default/grub already, you can do so again if you wish :-) to change the default booting option to the number which Windows is.
Or a much easier way is to install Startup Manager via Synaptic Package Manager and change the default OS from there.
Did you run sudo update-grub in the terminal after making the changes to /etc/default/grub?
This makes the changes take effect.

I must admit to being relieved that you can boot both OSes. It was looking a bit dodgy for a while :-)

As far as I'm aware you only turn off os_prober if you have made a custom menu, or if you just don't want to pick up any OSes any more. Not something I'd want, personally.

Quackers,
You have saved me a great deal of skull sweat by telling me about StartupManager.  How would I have found it had you not told me about it?

In any case, my big issues are now solved.  I used StartupManager to set Windows as the default OS and in the menu it now shows up hightlighted at the bottom of the menu.  These are smaller issues and call for a separate thread.  I'll post it later or tomorrow.  However, I am marking this thread as [SOLVED].

I will diddle the partitions, now that I realize the root is too small and I will play some other games to make my installation more practical.

Quackers, you have been terrific help to me, and anyone else who encounters my kind of questions.  I give you Kudos and a beer!

---

### Post by Quackers on 2010-11-27
Very kind sir, but a small fish would be more to my taste :-)
You're welcome.

BTW be careful "diddling" partitions. Only one diddle at a time and everything (including swap) should be unmounted.

---

### Post by rajeeja on 2010-12-13
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

Reboot into the LiveCD and execute:

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Simply rebooting without the live CD gets me to grub> prompt. It's because the old grub files are gone and the new one didn't update?

Vista doesn't show up now, so I don't know what to do?

Many thanks,

---

### Post by rpaskudniak on 2010-12-13
Rajeeja,

Do not repeat my mistake!  I tried to recover my Windows by booting from my Dell Recovery disks and it messed up my files.

Before you do ANYTHING, print out [article 1014708]("http://ubuntuforums.org/showthread.php?t=1014708") in this forum.

If you have the Windows installation DVD, boot from that.

Scary as it seems, start the installation process.  At the 3rd of 4th step, it will prompt you for a region. After that, you will have the chance to enter command mode.  If you choose that you will get a DOS-like command window.  Here, enter these commands:

```
bootrec.exe /fixboot

bootrec.exe /fixmbr
```
This will blow away the grub and you will be able to boot only into Windows.  Do that just to make sure you CAN boot to Windows.  Then, however, you can now get back the grub by booting the Ubuntu Live CD and following the directions in that article.

And when you have everything back, send a [virtual] beer or similar kudos to talsemgeest for writing it.

---

### Post by rajeeja on 2010-12-14
Thanks for the detailed reply, I'll have to search for the windows CD..

---

### Post by rajeeja on 2010-12-14
> **rpaskudniak said:**
> Rajeeja,

Do not repeat my mistake!  I tried to recover my Windows by booting from my Dell Recovery disks and it messed up my files.

Before you do ANYTHING, print out [article 1014708]("http://ubuntuforums.org/showthread.php?t=1014708") in this forum.

If you have the Windows installation DVD, boot from that.

Scary as it seems, start the installation process.  At the 3rd of 4th step, it will prompt you for a region. After that, you will have the chance to enter command mode.  If you choose that you will get a DOS-like command window.  Here, enter these commands:

```
bootrec.exe /fixboot

bootrec.exe /fixmbr
```
This will blow away the grub and you will be able to boot only into Windows.  Do that just to make sure you CAN boot to Windows.  Then, however, you can now get back the grub by booting the Ubuntu Live CD and following the directions in that article.

And when you have everything back, send a [virtual] beer or similar kudos to talsemgeest for writing it.




How did you fix Ubuntu after restoring windows?

---

### Post by rajeeja on 2010-12-14
> **rpaskudniak said:**
> Rajeeja,

Do not repeat my mistake!  I tried to recover my Windows by booting from my Dell Recovery disks and it messed up my files.

Before you do ANYTHING, print out [article 1014708]("http://ubuntuforums.org/showthread.php?t=1014708") in this forum.

If you have the Windows installation DVD, boot from that.

Scary as it seems, start the installation process.  At the 3rd of 4th step, it will prompt you for a region. After that, you will have the chance to enter command mode.  If you choose that you will get a DOS-like command window.  Here, enter these commands:

```
bootrec.exe /fixboot

bootrec.exe /fixmbr
```
This will blow away the grub and you will be able to boot only into Windows.  Do that just to make sure you CAN boot to Windows.  Then, however, you can now get back the grub by booting the Ubuntu Live CD and following the directions in that article.

And when you have everything back, send a [virtual] beer or similar kudos to talsemgeest for writing it.

I have a OS CD and I did fixboot and fixmbr, after doing that (both of them ran successfully) I simply ejected the Vista CD.

Now when I try to reboot, nothing comes to the screen just a cursor blinking. No more "grub>" prompt.

Any pointers?

Should I run startup recovery on Vista CD or do something with the 10.10 live CD?

---

