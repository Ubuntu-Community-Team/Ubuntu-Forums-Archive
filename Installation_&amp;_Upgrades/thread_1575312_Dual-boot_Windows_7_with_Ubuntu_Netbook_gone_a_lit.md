---
title: "Dual-boot Windows 7 with Ubuntu Netbook gone a little wrong"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by KadirÖ on 2010-09-15
**Information about my HP Laptop:**

> Processor: 2x AMD Turion II Ultra Dual-core Mobile M620
Memory: 6GB of ram(Only 3,6GB used, because of Ubuntu Netbook not being 64-bit)
Ubuntu: Ubuntu 10.04 LTS(Kernel: Linux 2.6.32-21-generic (i686))
Windows: Windows 7 64-bit
Graphics card: ATI graphics card 1GB
**Full bootscript report: At bottom.**

It all started like this..

I bought my HP-laptop 4 weeks ago. 2 days ago I decided to dual-boot the pre-installed Windows 7 with Ubuntu Netbook. Thought it was a good idea.

Well, I created a partition for Ubuntu on 100GB on my current HDD and the whole disk went from a Primary Disc to Basic Disc(because of having more than 4 partitions).
After that I decided to delete the partitions created by HP called HP_TOOLS and HP_RECOVERY. I did.

After that I went and booted up with my USB and installed Ubuntu Netbook without SWAP-partition through advanced partition, as it didn't come up with "Install Ubuntu beside Windows" or anything like that, that I've seen others do.
At the advanded partition windows I chose the 100GB partition and checked "Reformat to Ext4 journaled". The mountpoint was "/".
It went fine and I loaded up Ubuntu Netbook after that.

Everything worked fine - I could load Windows 7 and Ubuntu Netbook through the GRUB bootloader.

But then it came.. Ubuntu Netbook decided to update to the latest Kernel I guess? and it did, well.. after that I haven't been able to load up Windows 7.

When I try to load up Windows 7, it goes on to the screen with the dots making the logo - doesn't even finish the logo - and then it freezes for a second, comes up with a blue-screen of death with errors for 0,5 seconds(so I can't read what it says), and then reboots.


This is my problem - I just want to be able to boot up my Windows 7. Could it have anything to do with Ubuntu Netbook changing something in the BIOS by itself, so I can't boot up Windows 7 64-bit?


Bootscript:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *  1,053,650,942 1,250,263,039   196,612,098   5 Extended
/dev/sda5       1,053,650,944 1,242,175,487   188,524,544  83 Linux
/dev/sda6       1,242,177,536 1,250,263,039     8,085,504  82 Linux swap / Solaris
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3             409,600 1,053,648,895 1,053,239,296  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        74DE4D6CDE4D2826                       ntfs       SYSTEM                        
/dev/sda3        E64ADC344ADBFEED                       ntfs                                     
/dev/sda5        7ae67b97-e867-4932-b9a7-912cabd8dd1d   ext4                                     
/dev/sda6        0803011f-b789-435a-9862-ab296c682e02   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 74de4d6cde4d2826
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e64adc344adbfeed
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
UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0803011f-b789-435a-9862-ab296c682e02 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 593.3GB: boot/grub/core.img
 593.3GB: boot/grub/grub.cfg
 593.3GB: boot/initrd.img-2.6.32-21-generic
 593.4GB: boot/initrd.img-2.6.32-24-generic
 593.2GB: boot/vmlinuz-2.6.32-21-generic
 593.2GB: boot/vmlinuz-2.6.32-24-generic
 593.4GB: initrd.img
 593.3GB: initrd.img.old
 593.2GB: vmlinuz
 593.2GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-09-15
It would be helpful if you posted the bootscript in my signature in code tags as described if you can. This text output from running the script will give us a larger overview of your whole setup. The zip has some information but not the nitty gritty we need like the MBR info and others.

---

### Post by KadirÖ on 2010-09-15
> **wilee-nilee said:**
> It would be helpful if you posted the bootscript in my signature in code tags as described if you can. This text output from running the script will give us a larger overview of your whole setup. The zip has some information but not the nitty gritty we need like the MBR info and others.

Okay, I have attached it to the first post.

---

### Post by wilee-nilee on 2010-09-15
Here it is for the others who have interests. Lrt me just take a look, at it.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 128.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600 1,053,648,895 1,053,239,296  42 SFS
/dev/sda4       1,053,648,896 1,250,261,679   196,612,784  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            128     7,839,871     7,839,744   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        74DE4D6CDE4D2826                       ntfs       SYSTEM                        
/dev/sda3        E64ADC344ADBFEED                       ntfs                                     
/dev/sda4        a1f60749-d251-461d-afd7-bd4387cacc91   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EBF9-9DF9                              vfat       KADIR                         
/dev/sdb                                                iso9660    robby - 0.9 (PreFinal)        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/E64ADC344ADBFEED  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/KADIR             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set a1f60749-d251-461d-afd7-bd4387cacc91
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set a1f60749-d251-461d-afd7-bd4387cacc91
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set a1f60749-d251-461d-afd7-bd4387cacc91
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a1f60749-d251-461d-afd7-bd4387cacc91 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set a1f60749-d251-461d-afd7-bd4387cacc91
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a1f60749-d251-461d-afd7-bd4387cacc91 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set a1f60749-d251-461d-afd7-bd4387cacc91
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set a1f60749-d251-461d-afd7-bd4387cacc91
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 74de4d6cde4d2826
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set e64adc344adbfeed
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=a1f60749-d251-461d-afd7-bd4387cacc91 /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


 616.9GB: boot/grub/core.img
 591.1GB: boot/grub/grub.cfg
 616.9GB: boot/initrd.img-2.6.32-21-generic
 616.9GB: boot/vmlinuz-2.6.32-21-generic
 616.9GB: initrd.img
 616.9GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-09-15
As far as I can tell the bootscript looks as it should, but there are others on the forum who are more attune to this sort of problem.

I wonder if you can do a safe mode start for W7 by hitting f8 as soon as you choose it from grub, if so I would go to the command choice and run chkdsk /p/r. This will just have it start a chkdsk when starting W7 again.

You can before doing this look at the Windows partitions from gparted in Ubuntu to see if there are any flags to run a chkdsk, in the information right click on the flagged partition to see.

I do see though that in sda2 which is set as active=boot-flag has the **Boot files/dirs:   /bootmgr /Boot/BCD**, and sda3 has a full boot file set.
    **Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe**

It may be that the flag should be on sda3, probably not though but you can change it from gparted if needed.

If you have not installed gparted to the netbook run
```
sudo apt-get install gparted
```

---

### Post by KadirÖ on 2010-09-15
> **wilee-nilee said:**
> As far as I can tell the bootscript looks as it should, but there are others on the forum who are more attune to this sort of problem.

I wonder if you can do a safe mode start for W7 by hitting f8 as soon as you choose it from grub, if so I would go to the command choice and run chkdsk /p/r. This will just have it start a chkdsk when starting W7 again.

You can before doing this look at the Windows partitions from gparted in Ubuntu to see if there are any flags to run a chkdsk, in the information right click on the flagged partition to see.

I do see though that in sda2 which is set as active=boot-flag has the **Boot files/dirs:   /bootmgr /Boot/BCD**, and sda3 has a full boot file set.
    **Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe**

It may be that the flag should be on sda3, probably not though but you can change it from gparted if needed.

If you have not installed gparted to the netbook run
```
sudo apt-get install gparted
```

As I can see, the Windows 7 OS is on sda3.. maybe the grub-loader loads the sda2? I don't really know. But, there is only 1 flag, and that is on sda1, which says: "Unable to detect file system!" but that's kinda unrelated I bet.

I can try the Recovery mode.. hmm.

But I do think the problem is that, at Grub bootloader it loads the sda2, which there is mainly nothing on, instead of sda3. But how would it show me the "Starting windows" and the small little dots? Hmm.

Picture of gparted:
[IMG]http://i.imgur.com/2w2L9.png[/IMG]

---

### Post by wilee-nilee on 2010-09-15
It looks to me that sda1 was the hp stuff you said you thought you had removed the partition, I don't know. It could be that what you did remove was the recovery, and or that sda1 was attached to that removed HP somehow.

It probably is what is causing the problem, and it appears everything else is okay I think sda2 is the usual W7 boot partition so I think it is correct to have the boot-flag.

It looks to me that you can just remove sda1 with gparted and then reboot and W7 should boot.

Does sda1 when right clicked give any information, or a reference to a chkdsk.

If you remove sda1 be sure to run this before rebooting.
```
sudo update-grub
```

---

### Post by KadirÖ on 2010-09-15
> **wilee-nilee said:**
> It looks to me that sda1 was the hp stuff you said you thought you had removed the partition, I don't know. It could be that what you did remove was the recovery, and or that sda1 was attached to that removed HP somehow.

It probably is what is causing the problem, and it appears everything else is okay I think sda2 is the usual W7 boot partition so I think it is correct to have the boot-flag.

It looks to me that you can just remove sda1 with gparted and then reboot and W7 should boot.

Does sda1 when right clicked give any information, or a reference to a chkdsk.

If you remove sda1 be sure to run this before rebooting.
```
sudo update-grub
```

Didn't change anything. :(
Windows 7 still blue-screens me. :(

---

### Post by wilee-nilee on 2010-09-15
If it was me I would run a chkdsk, I have mentioned this several times in this thread, but have yet to get any response.

You can run set up a chkdsk /p/r from a install or recovery W7 DVD/CD, or from safe mode by hitting the f8 key at choosing windows, and going to the command line. Here is a link to W7 recovery disc. In each case you will be asked if it should be run a restart, yes is what you want.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Does this make sense to you W7 problems may be not necessarily associated with the netbook install but within its OS, it is hard to say. 

Also blue screen means nothing are then any errors shown, that description is void of content.

So if you wanted to just put the W7 bootloader back in to get in run the one highlighted command from the recovery or install disc; booted. There is a http link that gives you instructions to get to the command line.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Reloading the bootloader for W7 will tell us if it is W7 itself, you can reload grub to the mbr as easily as loading the MS bootloader. Personally I would run the chkdsk first,before trying to reload the mbr.

To reload grub if you want here is a link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

This link defaults to putting grub2 back in the mbr from a live cd.

---

### Post by KadirÖ on 2010-09-15
> **wilee-nilee said:**
> If it was me I would run a chkdsk, I have mentioned this several times in this thread, but have yet to get any response.

You can run set up a chkdsk /p/r from a install or recovery W7 DVD/CD, or from safe mode by hitting the f8 key at choosing windows, and going to the command line. Here is a link to W7 recovery disc. In each case you will be asked if it should be run a restart, yes is what you want.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Does this make sense to you W7 problems may be not necessarily associated with the netbook install but within its OS, it is hard to say. 

Also blue screen means nothing are then any errors shown, that description is void of content.

So if you wanted to just put the W7 bootloader back in to get in run the one highlighted command from the recovery or install disc; booted. There is a http link that gives you instructions to get to the command line.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Reloading the bootloader for W7 will tell us if it is W7 itself, you can reload grub to the mbr as easily as loading the MS bootloader. Personally I would run the chkdsk first,before trying to reload the mbr.

To reload grub if you want here is a link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

This link defaults to putting grub2 back in the mbr from a live cd.

Tried the chkdsk, wouldn't allow me to do it. Plus, when I run the other commands it says that it couldn't find any Windows installations.
Now I tried the start-up repair and it went succesfull, but it says: "No bootable device -- insert boot disk and press any key"..

HMM!

---

### Post by wilee-nilee on 2010-09-15
> **KadirÖ said:**
> Tried the chkdsk, wouldn't allow me to do it. Plus, when I run the other commands it says that it couldn't find any Windows installations.
Now I tried the start-up repair and it went succesfull, but it says: "No bootable device -- insert boot disk and press any key"..

HMM!

When you say start up repair did you run the command I put in bold.

Since you have done some changes lets see the bootscript run again, if you can.

---

### Post by KadirÖ on 2010-09-16
> **wilee-nilee said:**
> When you say start up repair did you run the command I put in bold.

Since you have done some changes lets see the bootscript run again, if you can.

Well, after I've done everything you suggested, even the bold, it starts Windows 7 but still does blue-screen of death. Plus, I installed Ubuntu again because I needed it for school today.

If I just somehow could see what the blue-screen of death errors was.. hmm, I could video-tape my screen and stop at that frame? I should try. I will update you. Feel free to post other solutions, if you do have any. :)

---

### Post by wilee-nilee on 2010-09-16
> **KadirÖ said:**
> Well, after I've done everything you suggested, even the bold, it starts Windows 7 but still does blue-screen of death. Plus, I installed Ubuntu again because I needed it for school today.

If I just somehow could see what the blue-screen of death errors was.. hmm, I could video-tape my screen and stop at that frame? I should try. I will update you. Feel free to post other solutions, if you do have any. :)

The only thing that makes sense to me is the chkdsk /p/r this can be run from that same command terminal from the W7 recovery cd I gave the link to or a install DVD.

I suspect this is what is holding it up, but it is really hard to say all the correct boot information was in the original script. Those of us that try to work in this boot area use that bootscript as a reference so when you have done changes and it still isn't booting it is great if you can post it again. This will update the thread for the others that are good at this boot fix stuff.

---

### Post by KadirÖ on 2010-09-16
> **wilee-nilee said:**
> The only thing that makes sense to me is the chkdsk /p/r this can be run from that same command terminal from the W7 recovery cd I gave the link to or a install DVD.

I suspect this is what is holding it up, but it is really hard to say all the correct boot information was in the original script. Those of us that try to work in this boot area use that bootscript as a reference so when you have done changes and it still isn't booting it is great if you can post it again. This will update the thread for the others that are good at this boot fix stuff.

Okay, well the chkdsk wouldn't work, so I will just post the bootscript again. :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *  1,053,650,942 1,250,263,039   196,612,098   5 Extended
/dev/sda5       1,053,650,944 1,242,175,487   188,524,544  83 Linux
/dev/sda6       1,242,177,536 1,250,263,039     8,085,504  82 Linux swap / Solaris
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3             409,600 1,053,648,895 1,053,239,296  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        74DE4D6CDE4D2826                       ntfs       SYSTEM                        
/dev/sda3        E64ADC344ADBFEED                       ntfs                                     
/dev/sda5        7ae67b97-e867-4932-b9a7-912cabd8dd1d   ext4                                     
/dev/sda6        0803011f-b789-435a-9862-ab296c682e02   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 74de4d6cde4d2826
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e64adc344adbfeed
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
UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0803011f-b789-435a-9862-ab296c682e02 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 593.3GB: boot/grub/core.img
 593.3GB: boot/grub/grub.cfg
 593.3GB: boot/initrd.img-2.6.32-21-generic
 593.4GB: boot/initrd.img-2.6.32-24-generic
 593.2GB: boot/vmlinuz-2.6.32-21-generic
 593.2GB: boot/vmlinuz-2.6.32-24-generic
 593.4GB: initrd.img
 593.3GB: initrd.img.old
 593.2GB: vmlinuz
 593.2GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2010-09-16
No expert here, but 2 things struck me as a bit odd.

1. the boot flag (shown by an * in the bootscript) is on the extended partition sda1. I was under the impression that it needs to be on the actual boot partition i.e. either sda5 or sda3.

2. the bootscript shows the Windows file system to be NTFS, but fdisk flags it as SFS?

Hope this helps.

---

### Post by wilee-nilee on 2010-09-16
> **Rubi1200 said:**
> No expert here, but 2 things struck me as a bit odd.

1. the boot flag (shown by an * in the bootscript) is on the extended partition sda1. I was under the impression that it needs to be on the actual boot partition i.e. either sda5 or sda3.

2. the bootscript shows the Windows file system to be NTFS, but fdisk flags it as SFS?

Hope this helps.

Good eye, sda2 is the W7 boot partition though, Ubuntu doesn't need a flag only Windows does.

> 42 SFS (Secure Filesystem)

    SFS is an encrypted filesystem driver for DOS on 386+ PCs, written by Peter Gutmann.
Here is the link.
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

Is your W7 set up encrypted?

The second boot script is showing grub looking at sda3 for windows, when it should be sda2, change the boot flag to sda2 and run sudo update-grub.

I think you might want to have a thread over at the W7 forums for more help as well.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

The only thing here which can make this even more confusing is it looks like you put the second bootscript in the first post and the first one is #4 where I posted it for you, then the second one again #14. I would take that second script out of your opening post so the thread flows at it happened it will make it much easier to understand.

It is possible since I missed the SFS partitions to begin with that saying it is probably okay to remove sda1 was not correct. I suspect that this is encrypted and that sda1 was part of that. If this ends up being the crux of the problem, it was one that started before the thread and encryption was never mentioned, but I should have seen the SFS notations I am remiss here.

---

### Post by KadirÖ on 2010-09-16
> **Rubi1200 said:**
> No expert here, but 2 things struck me as a bit odd.

1. the boot flag (shown by an * in the bootscript) is on the extended partition sda1. I was under the impression that it needs to be on the actual boot partition i.e. either sda5 or sda3.

2. the bootscript shows the Windows file system to be NTFS, but fdisk flags it as SFS?

Hope this helps.
I did think to myself that there must be something wrong with the bootfile.. well.

> **wilee-nilee said:**
> Good eye, sda2 is the W7 boot partition though, Ubuntu doesn't need a flag only Windows does.


Here is the link.
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

Is your W7 set up encrypted?

The second boot script is showing grub looking at sda3 for windows, when it should be sda2, change the boot flag to sda2 and run sudo update-grub.

I think you might want to have a thread over at the W7 forums for more help as well.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

The only thing here which can make this even more confusing is it looks like you put the second bootscript in the first post and the first one is #4 where I posted it for you, then the second one again #14. I would take that second script out of your opening post so the thread flows at it happened it will make it much easier to understand.

It is possible since I missed the SFS partitions to begin with that saying it is probably okay to remove sda1 was not correct. I suspect that this is encrypted and that sda1 was part of that. If this ends up being the crux of the problem, it was one that started before the thread and encryption was never mentioned, but I should have seen the SFS notations I am remiss here.
I don't know if my Windows7 is encrypted. Well, it came pre-installed with my HP laptop and I didn't touch any settings with encryption, so that must mean no.

Hmm. So, how would I change the boot-flag to sda2?
According to gparted sda2 is the SYSTEM partition and I do not have much experience with boot-up stuff etc.. does the SYSTEM partition have to be booted-up, which then will boot-up the sda3 - which is the windows7 partition?

---

### Post by wilee-nilee on 2010-09-16
> **KadirÖ said:**
> I did think to myself that there must be something wrong with the bootfile.. well.


I don't know if my Windows7 is encrypted. Well, it came pre-installed with my HP laptop and I didn't touch any settings with encryption, so that must mean no.

Hmm. So, how would I change the boot-flag to sda2?
According to gparted sda2 is the SYSTEM partition and I do not have much experience with boot-up stuff etc.. does the SYSTEM partition have to be booted-up, which then will boot-up the sda3 - which is the windows7 partition?

With gparted right click on the sda2 partition-manage flags then click boot.

I didn't think that if you had encryption, that you probably new this. If you have windows ultimate that may be why you have SFS partitions, I'm not sure. Ultimate is the only version that has the MS encryption available. I would suspect you would have to set up with a pass word for it to be doing what ever it does. 

This is an area I just have no clue in; encryption, or on what systems it is and how to deal with it, but you may not even have it set up if it's there. I think the W7 forums people will know about this. Others on this forum would know but it will probably go a lot faster with some help from a regular windows 7 users as well.

I'm not trying to get rid of you I just want to see you up and running in the end.

Edit: I am curious to see another screen shot of gparted as well, the best way to do this is use the screenshot but choose select area to grab, this will give us a easier look at it within the page. This is just like using the snipping-tool in W7.

---

### Post by KadirÖ on 2010-09-18
> **wilee-nilee said:**
> With gparted right click on the sda2 partition-manage flags then click boot.

I didn't think that if you had encryption, that you probably new this. If you have windows ultimate that may be why you have SFS partitions, I'm not sure. Ultimate is the only version that has the MS encryption available. I would suspect you would have to set up with a pass word for it to be doing what ever it does. 

This is an area I just have no clue in; encryption, or on what systems it is and how to deal with it, but you may not even have it set up if it's there. I think the W7 forums people will know about this. Others on this forum would know but it will probably go a lot faster with some help from a regular windows 7 users as well.

I'm not trying to get rid of you I just want to see you up and running in the end.

Edit: I am curious to see another screen shot of gparted as well, the best way to do this is use the screenshot but choose select area to grab, this will give us a easier look at it within the page. This is just like using the snipping-tool in W7.

I tried setting the sda2 to "boot" - didn't work. Even tried to do sda3 to "boot" - didn't work either.

[IMG]http://imgur.com/T2C7j.png[/IMG]

---

