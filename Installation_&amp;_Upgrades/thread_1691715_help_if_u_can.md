---
title: "help if u can"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by slyblade900 on 2011-02-20
this is one heck of a day. I'm writing this not in the hope that someone can find a solution for me (It would be really cool if someone did !!) but because i don't want anyone else doing the same mistake i did.

System config:
I own a x64 machine with intel core 2 quad CPU and Nvidia GDDR3 Graphic card. 

Problem: I was using windows7 earlier and locked a particular drive using BITLOCKER. after sometime i decided to switch to Linux and put the Fedora x86_64 DVD inside and rebooted. The disk was a bit faulty. I went up till formatting my drive ( I left the Bitllocker drive untouched ). When i clicked next after setting up the partition tables, Anaconda failed ( I'm not sure if it was cos the disk was faulty or because of BITLOCKER). And i had to restart my computer. I thought windows would boot. But i didn't. The partitioning system in windows7 CD shows the C:\ Drive to be completely empty. The only other OS i had was ubuntu 10.04 and i installed a fresh copy of it. This time i did the same partitioning i did for fedora. But the problem is a part of my Drives namely the Bitlocker drive and Another Drive I have fused into an unknown drive. (Learnt it through Disk utility in Ubuntu). Now even if i was to separate the drive to use some kind of recovery tool, won't that recovery tool damage the BITLOCKER drive ? I have some really valuable data there. Any ideas ANYONE? I'm willing to accept even stupid ideas hoping it might work.

---

### Post by Quackers on 2011-02-20
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by slyblade900 on 2011-02-20
Did not produce any results. Currently i'm booted into ubuntu 10.04. Booting is not the problem, Its what happened to the Other Drives and Where did windows go
[IMG]http://i52.tinypic.com/2kpy8p.png[/IMG]

---

### Post by Quackers on 2011-02-20
Try again using the command, as posted :-) Half of it's missing!

---

### Post by lisati on 2011-02-20
When it does its stuff, the script creates a file called results.txt containing the output...... :D

---

### Post by slyblade900 on 2011-02-20
Thanks. This is what is generated in that results.txt file


             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       52426751 sectors, but according to the info from 
                       fdisk, it has 819482671 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             208,894   155,334,655   155,125,762   5 Extended
/dev/sda5             208,896    20,207,615    19,998,720  83 Linux
/dev/sda6          20,209,664    24,207,359     3,997,696  82 Linux swap / Solaris
/dev/sda7          24,209,408   155,334,655   131,125,248  83 Linux
/dev/sda4         157,288,448   976,771,119   819,482,672  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        BEB867A9B8675F41                       ntfs       System Reserved               
/dev/sda3: PTTYPE="dos" 
/dev/sda4        587ED9F07ED9C742                       ntfs       Local Disk                    
/dev/sda5        16280065-4560-4588-ad10-311311f03c8b   ext4                                     
/dev/sda6        52478efa-026e-4bae-af90-6aa6a103fd9f   swap                                     
/dev/sda7        8c90cbde-8b08-4ce5-99a3-b448cb9a6c78   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
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
search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=16280065-4560-4588-ad10-311311f03c8b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=16280065-4560-4588-ad10-311311f03c8b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=16280065-4560-4588-ad10-311311f03c8b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=16280065-4560-4588-ad10-311311f03c8b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 16280065-4560-4588-ad10-311311f03c8b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set beb867a9b8675f41
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
/dev/sda5       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=8c90cbde-8b08-4ce5-99a3-b448cb9a6c78 /home           ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/core.img
   6.7GB: boot/grub/grub.cfg
   6.9GB: boot/initrd.img-2.6.32-21-generic
   7.0GB: boot/initrd.img-2.6.32-28-generic
   6.8GB: boot/vmlinuz-2.6.32-21-generic
   6.9GB: boot/vmlinuz-2.6.32-28-generic
   7.0GB: initrd.img
   6.9GB: initrd.img.old
   6.9GB: vmlinuz
   6.8GB: vmlinuz.old

---

### Post by Quackers on 2011-02-20
Which hard drive is set to boot first in the bios? If it's sda, Ubuntu should be booting.
Windows partitions have been changed to dynamic disks (SFS). This is often caused by creating more than 4 primary partitions on one hard drive.

---

### Post by slyblade900 on 2011-02-21
So isn't there a solution for me to restore my Disks back to normal, Like back to static ? And yes Ubuntu is booting but it does not recognize any of the Bit Locker Drives. and furthur more, it is fused into one disk.

---

### Post by Quackers on 2011-02-21
You can have a look at post #5 in this thread
[http://ubuntuforums.org/showthread.php?t=1669910](http://ubuntuforums.org/showthread.php?t=1669910)
Linux systems will not recognise dynamic disks (SFS type) that's why Microsoft do it, I suspect.

---

### Post by YesWeCan on 2011-02-21
You may have better luck at a Windows forum or by consulting the MS site. I found this for example: [http://support.microsoft.com/kb/928201](http://support.microsoft.com/kb/928201)
Better to install linux on its own disk, if you can.

---

### Post by slyblade900 on 2011-02-21
Thanks but i'm switching over completely to Ubuntu. I need Ubuntu to 'see', i mean mount it at the least. Does that mean i will have to use windows 7 to repair that disk to SFD to normal and then again go through the process of installing Ubuntu with all its updates ? 
                                                                           And although its not my problem here, i have a general doubt about computers. Is it good to format your system completely and keep switching OS's. Many Linux users keep tying different distros. won't it harm the comp. in general to format like that ?

---

### Post by Quackers on 2011-02-21
Just re-install Ubuntu and choose to "use the whole disc" at partitioning stage. Obviously that will over-write all previous partitions and Windows will not be usable again.
I have a twin drive laptop. I currently have 6 operating systems installed and running. These 6 are the latest in a long line of operating systems. It will cause no damage to install/wipe out/re-install etc etc etc. Enjoy yourself.

---

### Post by YesWeCan on 2011-02-21
> **slyblade900 said:**
> Thanks but i'm switching over completely to Ubuntu. I need Ubuntu to 'see', i mean mount it at the least. Does that mean i will have to use windows 7 to repair that disk to SFD to normal and then again go through the process of installing Ubuntu with all its updates ? 
Well if you have important data then you should probably focus on recovering it and take the possible hit of reinstalling Ubuntu. Unlike Windows, Ubuntu is quite quick to install :)
Ubuntu can read and write standard NTFS partitions.

---

### Post by slyblade900 on 2011-02-21
Thanks for the help, both of you =) Will post back if i can recover that partition after going through all the mess. I'm marking this thread as solved ( If this forum has one =) )

---

### Post by slyblade900 on 2011-02-21
I guess i've lost all the data. Windows installation disk says "No drives found". It typically finds No drive at all in my computer =) What is lost is lost.

---

