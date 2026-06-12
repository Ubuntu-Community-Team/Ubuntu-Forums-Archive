---
title: "multi-boot issues... think I screwed up on my grub-pc config."
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by shayne122 on 2010-04-13
Originally I had a fully functioning triple boot setup with Windows XP and 7 RTM on my SATA HDD, and Ubuntu 9.10 on my IDE.

I decided to upgrade to 10.04 through the update manager (I believe that's what it's called?) After downloading all the required files, it proceeded to install blah blah blah. Then a prompt came up asking me to update grub. I just assumed yes, with a kernel update, you'd maybe want to avoid errors by also updating the boot manager... It prompted me as to which drives I wanted to install grub to. I selected all of them (I guess I just assumed I wanted to be able to address all my drives under grub?).

After configuring the ATI drivers and such, the installation worked fairly perfectly. Neat.

So I go to reboot it, and try to enter the Windows 7 Bootloader. All that happens is it brings me to a blinking cursor. As you can tell by now, I have no idea what I'm doing with this whole linux thing, haha. But that's what you guys are here for?

I can mount my XP and 7 drives no problem, so it's not a hardware issue. I've also tried to run the windows 7 install disc, but it just can't find any volumes.

This is my boot script log:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 4466495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 4466495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 4466495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 4466495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   186,498,584   186,498,522   7 HPFS/NTFS
/dev/sda2         186,498,585   625,137,344   438,638,760   5 Extended
/dev/sda5         312,576,768   625,137,344   312,560,577   7 HPFS/NTFS
/dev/sda6         186,498,711   312,576,704   126,077,994  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   295,435,349   295,435,287  83 Linux
/dev/sdb2         295,435,350   398,283,479   102,848,130   f W95 Ext d (LBA)
/dev/sdb5         295,435,413   398,283,479   102,848,067   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        381856BA1856773A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        01CA69CC40AAA310                       ntfs       7                             
/dev/sda6        51462bd5-8a55-4aa4-aee3-01a80aac7439   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        adf02797-070a-42e5-94e8-a23eb79fef94   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9E886EF9886ECEF9                       ntfs       Plugins, programs             
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/Windows 7         udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER 
 
C:\tboot=Mac Os X System
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
set default="6"
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
search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
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
search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
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
menuentry 'Ubuntu, with Linux 2.6.32-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=adf02797-070a-42e5-94e8-a23eb79fef94 ro   splash quiet
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
    echo    'Loading Linux 2.6.32-20-generic ...'
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=adf02797-070a-42e5-94e8-a23eb79fef94 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=adf02797-070a-42e5-94e8-a23eb79fef94 ro   splash quiet
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=adf02797-070a-42e5-94e8-a23eb79fef94 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set adf02797-070a-42e5-94e8-a23eb79fef94
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 381856ba1856773a
    chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=adf02797-070a-42e5-94e8-a23eb79fef94 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=51462bd5-8a55-4aa4-aee3-01a80aac7439 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
   5.4GB: boot/initrd.img-2.6.31-20-generic
   4.1GB: boot/initrd.img-2.6.32-20-generic
   3.7GB: boot/vmlinuz-2.6.31-20-generic
   4.0GB: boot/vmlinuz-2.6.32-20-generic
   4.1GB: initrd.img
   5.4GB: initrd.img.old
   4.0GB: vmlinuz
   3.7GB: vmlinuz.old
```Thanks fellows.

---

### Post by presence1960 on 2010-04-13
You installed GRUB 2 onto the boot sector of the windows partitions. I would fix that with the windows install CD/DVD. An alternate method is boot the Ubuntu Live CD, choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo apt-get install lilo
```Ignore the warnings. Now in terminal run ```
sudo lilo -M /dev/sda mbr
``` Reboot without the Live CD and make sure sda is set to boot first in the BIOS hard disk boot order. Make sure windows boots properly.

Then you will have to reinstall GRUB to MBR of sdb. After fixing the windows boot and making sure they boot properly boot the 9.10 Live CD. Choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```

next in terminal run```
 sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot without Live CD & go into BIOS and set sdb as first hard disk to boot in the hard disk boot order. Save changes to CMOS and continue booting. If windows is not in the GRUB menu boot into ubuntu. Open a terminal and run ```
sudo update-grub
```

Lastly from Ubuntu run in terminal ```
sudo dpkg-reconfigure grub-pc
```Hit Enter at all screens until you get to the window where you can choose sda & sdb. Use the arrow keys to maneuver to sda. if it is ticked use the space bar to untick it. next move to sdb and select it by using the space bar. Hit Tab and then Enter. This will set it up so any updates to GRUB go only to the MBR of sdb.

P.S. After reinstalling GRUB if you can't boot ubuntu from GRUB you may have to highlight ubuntu at the GRUB menu and hit "e". Then use your arrow keys to maneuver to (hd0,1) and change it to (hd1,1). Then hit CTRL + x to boot. Once you get into ubuntu run in terminal ```
sudo update-grub
``` Then run ```
sudo dpkg-reconfigure grub-pc
``` and follow the instructions above for that process

---

### Post by webtechquery on 2010-04-13
Well, if it your problem is about not able to boot your Ubuntu (i.e. grub or grub2), then the following url may help:

[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

---

### Post by presence1960 on 2010-04-13
> **webtechquery said:**
> Well, if it your problem is about not able to boot your Ubuntu (i.e. grub or grub2), then the following url may help:

[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

> So I go to reboot it, and try to enter the Windows 7 Bootloader. All that happens is it brings me to a blinking cursor. As you can tell by now, I have no idea what I'm doing with this whole linux thing, haha. But that's what you guys are here for?

I can mount my XP and 7 drives no problem, so it's not a hardware issue. I've also tried to run the windows 7 install disc, but it just can't find any volumes.

Not the problem. The OP can't boot windows.

---

### Post by shayne122 on 2010-04-13
Thank you, I'll try that immediately.

I appreciate your thoroughness.

---

### Post by shayne122 on 2010-04-13
> **shayne122 said:**
> Thank you, I'll try that immediately.

I appreciate your thoroughness.

Alright, so because my win7 install disk wouldn't recognize a partition through startup repair, I have tried your ubuntu live cd (I ended up using a Mint 8 (ubuntu-based) live usb, which as far as I know should do the trick?) method.

While checking the Disk Utility, it's come to my attention that the windows 7 partition (sda5) is for some reason listed as "unknown or unused" as opposed to NTFS or the like. in the "partition type" field, it says that it is HPFS/NTFS partition with no label. it used to be simply "7".

I do have another XP partition (sda1) that if I absolutely have to, I can use to at least have one windows environment available. Though my critical information is all on the sda5.

Thoughts?

EDIT: ends up I got access to part of sda, and I'm just going to use the 65gb swap partition as free space, install a vanilla windows 7, and try a partition recovery utility.

THEN I'll proceed with the dual boot.

---

### Post by oldfred on 2010-04-13
When you checked all the boxes on where to install grub you also checked all the partitions. Windows has key boot files in the partition boot record (PBR).

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

From Ubuntu you can repair the boot sector,, with two installs you may have to choose twice:
(Vista's "fixboot" usually only repairs the boot code in the boot sector, but not the boot parameters)

From liveCD
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

Otherwise you have to use the windows repair CD to run fixboot.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

or from working Ubuntu:
sudo apt-get install testdisk
sudo testdisk

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk, reboot and see whether you can boot into Vista.

---

