---
title: "Computer freezes after windows grub"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by woodwork78 on 2010-02-17
After I select Windows xp in grub, the screen goes blank then says grub at the top and nothing else happens.
This started after installing alpha 10.04.
I have reinstalled 9.10
I have 2 hard drives, one contains windows and one contains ubuntu
I'm not sure how to edit the grub file as it is on a separate hard drive.
I really have no clue what to do and should not have been installing alpha software :(
Any help would be greatly appreciated.
Thanks,
Aaron

---

### Post by darkod on 2010-02-17
If you formatted the partition when installing 9.10 or if you used the Erase and use whole disk option, there should be no remains of 10.04 at all.

Anyway, to see what is happening follow the instructions in post #2 here:
[http://ubuntuforums.org/showthread.php?t=1409267](http://ubuntuforums.org/showthread.php?t=1409267)

and post the content of your results.txt file as explained.

---

### Post by woodwork78 on 2010-02-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=339b982f-590a-4164-8ebf-bb7ad52bec12)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 54797623 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 54802399 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00085c22

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   470,254,679   470,254,617  83 Linux
/dev/sdb2         470,254,680   488,392,064    18,137,385   5 Extended
/dev/sdb5         470,254,743   488,392,064    18,137,322  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   234,436,544   234,436,482   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D6F4D3D1F4D3B24B                       ntfs                                     
/dev/sdb1        339b982f-590a-4164-8ebf-bb7ad52bec12   ext4                                     
/dev/sdb5        47757329-a801-41bf-ab85-678814768da8   swap                                     
/dev/sdc1        4B1A-02BD                              vfat       WD Passport                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/WD Passport       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 339b982f-590a-4164-8ebf-bb7ad52bec12
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 339b982f-590a-4164-8ebf-bb7ad52bec12
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=339b982f-590a-4164-8ebf-bb7ad52bec12 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 339b982f-590a-4164-8ebf-bb7ad52bec12
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=339b982f-590a-4164-8ebf-bb7ad52bec12 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d6f4d3d1f4d3b24b
    drivemap -s (hd0) ${root}
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
UUID=339b982f-590a-4164-8ebf-bb7ad52bec12 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=47757329-a801-41bf-ab85-678814768da8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  23.7GB: boot/grub/core.img
  14.5GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-19-generic-pae
    .5GB: boot/vmlinuz-2.6.31-19-generic-pae
    .2GB: initrd.img
    .5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by woodwork78 on 2010-02-17
After reading that boot file, it looks like grub is not accessing windows correctly, am I right?
Core.img cannot be found at this location
How do I point it in the right direction?

---

### Post by darkod on 2010-02-17
It's not only that. The main problem is that grub shouldn't be there at all, not on partitions boot sector. Usually it goes on Master Boot Record (MBR) of a hdd, that's the top of the results shows the bootloaders on all 3 drives.
Only in special cases you would tell grub to install onto a partition boot record. And definitely not on the windows system partition.
For XP I'm not 100% sure how to get rid of it, but the logic is that XP boot repair process should get rid of it.
Restore the XP boot process as explained here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Before you start that, make sure you go into BIOS and make the windows drive first choice for boot in hdd list.

After the repair is done, again go in BIOS and make the other 250GB first in the boot order and you shouls boot ubuntu fine. Run the script again to check that the /dev/sda1 partition is free of the grub bootloader (no need to post the results unless you really want to).

I think that should repair it. In addition, after you boot back into ubuntu you might need to run:
sudo update-grub

to recreate new grub.cfg.

---

### Post by woodwork78 on 2010-02-17
I cannot get into XP and I have no idea where to find the xp boot repair process?
Never mind,,,  I'll get it lol

---

### Post by darkod on 2010-02-17
> **woodwork78 said:**
> I cannot get into XP and I have no idea where to find the xp boot repair process?
Never mind,,,  I'll get it lol

You need to boot from XP install cd and in the first or second screen when it offers Recovery Console, open it. Then you'll need to enter you Administrator password and it will open a recovery console for your C: install. You type those commands into that.

---

### Post by meierfra. on 2010-02-17
It probably too late. But you only need to run "fixboot"

Edit:  If you are booting from Ubuntu drive. running fixmbr actually  won't cause any problem. So you can ignore this message,

---

### Post by woodwork78 on 2010-02-17
Thanks, fixed it!

---

