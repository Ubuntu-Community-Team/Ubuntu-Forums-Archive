---
title: "Another:  File not found; grub rescue"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-11-30
Greetings.

I am reading spc456's thread with the same subject line and trying to work through the thread with suggestions by drs305.

My situation is very similar.  It started with a sudden Windows boot problem (still my primary OS):> BOOTMGR is missingThis was only if I selected Windows from the boot menu. I thought I could cure it with the Windows-7 Repair Disk from neosmart.net.  This appears to have wiped my Boot partition completely and now I can't boot anything. ](*,) (I'm using the Ubuntu 10.10 live as I type this.)

I downloaded boot_info_script055.sh and here are the RESULTS but I don't know what needle to look for in that haystack.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
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
    Boot files/dirs:   

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
/dev/sda5       1,134,325,760 1,201,437,089    67,111,330  83 Linux
/dev/sda6       1,201,437,153 1,234,996,874    33,559,722  82 Linux swap / Solaris
/dev/sda7       1,234,996,938 1,268,556,659    33,559,722  83 Linux
/dev/sda8       1,268,556,723 1,370,023,199   101,466,477  83 Linux


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

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        B6248003247FC4C1                       ntfs       RECOVERY                      
/dev/sda3        9AF08259F0823B8F                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        831b4fa3-b7eb-4daf-83f4-5edcb625795c   ext3       Ubuntu-Root                   
/dev/sda6        b131bed3-9334-4baa-9573-bf15c9465e83   swap       swap                          
/dev/sda7        9e735636-ce42-41ae-bf77-d81fb8ea2094   ext2       Ubuntu-Tmp                    
/dev/sda8        b1eade53-1833-4b2c-9622-bd7e8f79477a   ext3       Ubuntu-SW                     
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

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     ext3       (rw)


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
set default="6"
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
  set timeout=30
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

UUID=831b4fa3-b7eb-4daf-83f4-5edcb625795c / ext3 defaults 0 1
#UUID=B6248003247FC4C1 /tmp ntfs-3g defaults 1 0
UUID=b131bed3-9334-4baa-9573-bf15c9465e83 swap swap sw 0 0
#UUID=9e735636-ce42-41ae-bf77-d81fb8ea2094 /tmp ext2 defaults 1 0
UUID=9AF08259F0823B8F /media/OS ntfs-3g defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


 581.0GB: boot/grub/core.img
 581.0GB: boot/grub/grub.cfg
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
Well, I see why the Windows boot didn't show up.  Looks like 30-OS_prober was failing to find the Windows boot record, which makes sense if the whole blessed (ahem) boot partition has been hosed.

I tried to follow the grub-install instructions:
```
ubuntu@ubuntu:~/Downloads$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
```No error, but a scary warning.

But since grub2 is obviously not going to find the Windows boot record, I will continue with drs305's advice and ```
ubuntu@ubuntu:~/Downloads$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```
No, I have not mounted /dev.  Where would I do that? Against which FS?

In any case, I am now printing the article "[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")" to see if I can get that going.

To my dismay, I discovered that the disk supplied with my Dell machine is **_NOT_** a Windows Installation disk, :mad:  so no straightforward "fixmbr" command will be possible at this time.

I'll let y'all know how I have fared with this.  I am sceptical because it's not merely the master boot record that has gotten corrupted but the whole blessed (have I used that adjective already?) boot partition.

Thanks much for any additional advice I might apply here.

---

### Post by rpaskudniak on 2010-11-30
OK!

Following the advice on that [aforementioned page]("http://ubuntuforums.org/showthread.php?t=1014708"), I have managed to restore the Ubuntu boot menu.  Not Windows, however.  Now I need to sit tight for a day while Dell ships me the Win-7 installation disk and I can try running the "repair your computer" section of that disk.

I am curious:  After I run the two bootrec commands (/fixboot and /fixmbr) won't these wipe out the grub from the MBR?

Of course, if they do, I still have those sudo commands - the mount and the grub-install that I can run from the Ubuntu-live cd.  And once I have the Windows disk, I won't be as afraid to take every step.

Thanks with much relief to have my Ubuntu back.

---

### Post by wilee-nilee on 2010-11-30
No sign of this which would be in the windows OS
```
 /Windows/System32/winload.exe
```

You have the bootflag where it should be, but you have a lot of partitions including a wubi in sdc2, it helps at the least to identify where the Windows OS is supposed to be.

---

### Post by rpaskudniak on 2010-11-30
Wilee,

Sorry, I omitted that vital statistic.

All the pertinent partitions are in /dev/sda.
[LIST]
[*]/dev/sda1: The Dell Utilities partition
[*]/dev/sda2: The blessed Boot partition ;)
[*]/dev/sda3: The Win-7 main partition (C:\)
[*]/dev/sda4: The extended partition, subdivided into sda5-8
[*]/dev/sda5: The Ubuntu root partition.
[*]/dev/sda6: The Ubuntu Swap partition
[/LIST]
All others are not yet relevant, until I resolve this.  Then I will use /dev/sda7 for /tmp and install commercial software into sda8.

/dev/sdb in my corsair flash memory.
/dev/sdc in my MyBook, with what was once considered an enormous 320GB. The partitions on /dev/sdc have served to keep many of my files out of harms way.

All that said, please explain your remark about/```
Windows/System32/winload.exe
```This is something I should see in the RESULTS.txt file?  Where would this appear?

---

### Post by wilee-nilee on 2010-11-30
Here is my boot script, you will notice that I have it in one partition, so the sda2 in yours=/bootmgr /Boot/BCD...is in the same partition.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD **/Windows/System32/winload.exe**

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    83,888,127    83,886,080   7 HPFS/NTFS
/dev/sda2         113,676,001   312,580,095   198,904,095   5 Extended
/dev/sda5         113,676,003   264,669,183   150,993,181  83 Linux
/dev/sda6         308,385,792   312,580,095     4,194,304  82 Linux swap / Solaris
/dev/sda7         264,671,232   308,383,743    43,712,512  83 Linux
/dev/sda3          83,891,430   113,675,939    29,784,510   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CFB6750453E160C                       ntfs       W7                            
/dev/sda2: PTTYPE="dos" 
/dev/sda3        7D061649158B4024                       ntfs       share                         
/dev/sda5        6f28beba-e464-480e-9d4c-329416a13f3c   ext4       Lucid                         
/dev/sda6        c739a546-bd75-4a85-8a36-dc860c0895d2   swap                                     
/dev/sda7        dadc267d-cff9-4d6f-8551-b4a9c02fbeae   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=5
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro  vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro single  vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2cfb6750453e160c
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d26066da6066c537
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=6f28beba-e464-480e-9d4c-329416a13f3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=05e757f7-cfb0-4edb-b045-f5c46524db5e none            swap    sw              0       0




=================== sda5: Location of files loaded by Grub: ===================


 109.8GB: boot/grub/core.img
  59.3GB: boot/grub/grub.cfg
 110.1GB: boot/initrd.img-2.6.32-24-generic
 110.2GB: boot/vmlinuz-2.6.32-24-generic
 110.1GB: initrd.img
 110.2GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
	echo	'Loading Linux 2.6.35-19-generic ...'
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2cfb6750453e160c
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro vga=758 quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro single vga=758
	initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c739a546-bd75-4a85-8a36-dc860c0895d2 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 148.6GB: boot/grub/core.img
 155.1GB: boot/grub/grub.cfg
 140.1GB: boot/initrd.img-2.6.35-19-generic
 149.0GB: boot/vmlinuz-2.6.35-19-generic
 140.1GB: initrd.img
 149.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  18 55 72 6c 50 61 72 61  6d 65 74 65 72 52 65 61  |.UrlParameterRea|
00000010  64 65 72 20 43 6c 61 73  73 95 cf 52 b8 cf 52 d3  |der Class..R..R.|
00000020  cf 52 00 01 2a 07 4d 65  6d 62 65 72 73 00 01 30  |.R..*.Members..0|
00000030  14 55 72 6c 50 61 72 61  6d 65 74 65 72 57 72 69  |.UrlParameterWri|
00000040  74 65 72 28 29 01 01 43  0c 43 6f 6e 73 74 72 75  |ter()..C.Constru|
00000050  63 74 6f 72 73 ad d0 52  00 01 30 0d 47 65 74 52  |ctors..R..0.GetR|
00000060  65 71 75 65 73 74 55 72  6c 01 01 4d 07 4d 65 74  |equestUrl..M.Met|
00000070  68 6f 64 73 d8 d0 52 03  1d 65 63 6d 61 3a 32 34  |hods..R..ecma:24|
00000080  38 32 23 55 72 6c 50 61  72 61 6d 65 74 65 72 57  |82#UrlParameterW|
00000090  72 69 74 65 72 2f 18 55  72 6c 50 61 72 61 6d 65  |riter/.UrlParame|
000000a0  74 65 72 57 72 69 74 65  72 20 43 6c 61 73 73 a2  |terWriter Class.|
000000b0  d0 52 c5 d0 52 e9 d0 52  00 01 2a 07 4d 65 6d 62  |.R..R..R..*.Memb|
000000c0  65 72 73 00 01 30 20 56  61 6c 75 65 43 6f 6c 6c  |ers..0 ValueColl|
000000d0  65 63 74 69 6f 6e 50 61  72 61 6d 65 74 65 72 52  |ectionParameterR|
000000e0  65 61 64 65 72 28 29 01  01 43 0c 43 6f 6e 73 74  |eader()..C.Const|
000000f0  72 75 63 74 6f 72 73 c3  d1 52 00 01 30 0e 47 65  |ructors..R..0.Ge|
00000100  74 49 6e 69 74 69 61 6c  69 7a 65 72 00 01 31 0a  |tInitializer..1.|
00000110  49 6e 69 74 69 61 6c 69  7a 65 00 01 32 2c 49 73  |Initialize..2,Is|
00000120  53 75 70 70 6f 72 74 65  64 28 53 79 73 74 65 6d  |Supported(System|
00000130  2e 52 65 66 6c 65 63 74  69 6f 6e 2e 50 61 72 61  |.Reflection.Para|
00000140  6d 65 74 65 72 49 6e 66  6f 29 00 01 33 3c 49 73  |meterInfo)..3<Is|
00000150  53 75 70 70 6f 72 74 65  64 28 53 79 73 74 65 6d  |Supported(System|
00000160  2e 57 65 62 2e 53 65 72  76 69 63 65 73 2e 50 72  |.Web.Services.Pr|
00000170  6f 74 6f 63 6f 6c 73 2e  4c 6f 67 69 63 61 6c 4d  |otocols.LogicalM|
00000180  65 74 68 6f 64 49 6e 66  6f 29 02 0b 49 73 53 75  |ethodInfo)..IsSu|
00000190  70 70 6f 72 74 65 64 0b  49 73 53 75 70 70 6f 72  |pported.IsSuppor|
000001a0  74 65 64 9a d2 52 ca d2  52 00 01 34 04 52 65 61  |ted..R..R..4.Rea|
000001b0  64 04 01 4d 07 4d 65 74  68 6f 64 73 fa d1 00 fe  |d..M.Methods....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 1d f9 ff 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 1f 01  9b 0b 00 08 40 00 00 00  |............@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

