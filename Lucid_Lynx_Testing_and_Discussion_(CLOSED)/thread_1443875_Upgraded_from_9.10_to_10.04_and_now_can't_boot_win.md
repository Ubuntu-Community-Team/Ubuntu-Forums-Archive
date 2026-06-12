---
title: "Upgraded from 9.10 to 10.04 and now can't boot windows 7 partition..."
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JMack89427 on 2010-03-31
So I decided to upgrade my 9.10 partition to 10.04 to mess around with it.  I ran the "update-manager -d" command per the documentation on ubuntu.com.  I screwed up when it went to upgrade grub and selected the partitions, not the disk itself and ended up at the grub rescue> prompt.  A quick boot to my UBCD got me back into Ubuntu and now I can't boot my Windows 7 partition or my Vista recovery partition.  I tried reconfiguring grub, using the disk, not the partitions, and even uninstalling and reinstalling it.  Nothing will get me back into Windows.  Any help would be appreciated.  

Here's the boot-info-script output:

>                 Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1034110111 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1034118967 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  27 Hidden HPFS/NTFS
/dev/sda2          20,482,875 1,033,814,879 1,013,332,005   7 HPFS/NTFS
/dev/sda3       1,033,814,880 1,250,258,624   216,443,745   5 Extended
/dev/sda5    *  1,033,814,943 1,233,808,064   199,993,122  83 Linux
/dev/sda6       1,233,808,128 1,250,258,624    16,450,497  82 Linux swap / Solar
is


Drive: sdb ___________________ _________________________________________________
____

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1     ?            63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


Drive: sdc ___________________ _________________________________________________
____

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        
                 

/dev/sda1        86E05608E055FEBD                       ntfs       PQSERVICE    
                 
/dev/sda2        9C80D4BF80D4A0D6                       ntfs                    
                 
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8ccaefb3-b73f-4907-b432-3c3b876d9d65   ext4                    
                 
/dev/sda6        d3b700bf-b990-4baf-8e08-1d201124b67e   swap                    
                 
/dev/sda: PTTYPE="dos" 
/dev/sdc1        4C1815BD1815A6CC                       ntfs       FreeAgent Dri
ve               
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb1: No such file or directory
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ======================
=====

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
set default="7"
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfa
il; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
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
search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
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
menuentry "Ubuntu, with Linux 2.6.32-18-generic" --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=8ccaefb3-b73f-4907-b43
2-3c3b876d9d65 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode)" --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
    echo    Loading Linux 2.6.32-18-generic ...
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=8ccaefb3-b73f-4907-b43
2-3c3b876d9d65 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8ccaefb3-b73f-4907-b43
2-3c3b876d9d65 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8ccaefb3-b73f-4907-b43
2-3c3b876d9d65 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8ccaefb3-b73f-4907-b432-3c3b876d9d65
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 86e05608e055febd
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 9c80d4bf80d4a0d6
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8ccaefb3-b73f-4907-b432-3c3b876d9d65 /               ext4    errors=remount
-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d3b700bf-b990-4baf-8e08-1d201124b67e none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 529.4GB: boot/grub/core.img
 534.3GB: boot/grub/grub.cfg
 532.9GB: boot/initrd.img-2.6.31-20-generic
 542.2GB: boot/initrd.img-2.6.32-18-generic
 529.9GB: boot/vmlinuz-2.6.31-20-generic
 530.8GB: boot/vmlinuz-2.6.32-18-generic
 542.2GB: initrd.img
 532.9GB: initrd.img.old
 530.8GB: vmlinuz
 529.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc ======================
=

Unknown BootLoader  on sdb1



=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory


---

### Post by Mark Phelps on 2010-03-31
When you were running Win7, since you knew you would be messing around with partitioning, you took the trouble to use the Win7 Backup feature to create and burn a Win7 Repair CD? Right?

There's no way to repair Win7 boot from Ubuntu.

So, if you didn't create that CD, then go to the following link, download and burn a Win7 Repair CD, and boot from it -- selecting Startup Repair three times:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

And, next time, post your beta-related questions to the correct forum: Development & Programming, Lucid Lynx Testing.

You also know, that since you "updated" your existing Ubuntu install, there is no way to "roll back" to the previous, stable version. Right?

---

### Post by JMack89427 on 2010-03-31
> **Mark Phelps said:**
> When you were running Win7, since you knew you would be messing around with partitioning, you took the trouble to use the Win7 Backup feature to create and burn a Win7 Repair CD? Right?

There's no way to repair Win7 boot from Ubuntu.

So, if you didn't create that CD, then go to the following link, download and burn a Win7 Repair CD, and boot from it -- selecting Startup Repair three times:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

And, next time, post your beta-related questions to the correct forum: Development & Programming, Lucid Lynx Testing.

You also know, that since you "updated" your existing Ubuntu install, there is no way to "roll back" to the previous, stable version. Right?

Wow...while I appreciate you taking the time to respond, could you sound more condescending?  If it had occurred to me that grub2 would be reinstalled during the update, I would have taken more precautions during this ordeal.  I don't run Ubuntu as my main desktop as my wife is uncomfortable with it so rolling back, or even a fresh install doesn't bother me.  I apologize for putting this in the wrong forum, I didn't see the Lynx forum.

---

### Post by bcbc on 2010-03-31
I had a slightly different problem, but basically Grub2 decided to install itself to one of my partitions, even though I requested it to not install at all. It changed the partition table on the internal HDD in the process, even though I was installing Lucid to an external USB. 

In your case, you have grub installed on a number of your partitions included Win7 so that probably explains why you can't boot windows. If you did an fdisk -l (or ran bootinfoscript) from before before you can compare before and after on your partition, but how to fix it? I don't know. 

There's a launchpad bug registered for this - you might want to add a comment there: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996)

---

### Post by JMack89427 on 2010-04-05
For what it's worth, I was able to save my Windows 7 installation.  I had to use the Windows 7 recovery disc that was linked in this post, however just using the simple recovery options didn't work.  What I ended up having to do, after trying a number of different things, was follow the guide located here: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD) .  The Nuclear Holocaust section is what got me through.  After that, I was able to boot Windows 7 and promptly proceeded to reinstall 10.04 and grub, correctly this time :)

---

