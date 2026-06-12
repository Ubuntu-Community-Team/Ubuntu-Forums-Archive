---
title: "Installed ubuntu but gets error message- DISK BOOT FAILURE"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by bmxboi42 on 2010-02-27
Hey

I just bought a brand new hardrive (40gb western digital) IDE, 10 pin.
I have gone through the installation and partioned the hardrive, when it gets to 100% it asks me to reboot.

So i take the disk out, and then it says DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER:.

So i press enter and i get the same message> How can i get Ubuntu to boot up?

The computer is a 2003 Medion pc with 512mb of RAM And an AMD Athlon processor. The computer has a sticker on that says: Designed for windows xp.

Any help on getting it to boot up please???
Its ubuntu 9.10!

Cheers 
Drew

---

### Post by darkod on 2010-02-27
Is this the only hdd in the computer? It might be trying to boot from another hdd that doesn't have a bootloader.

Is the BIOS set to boot from hdd at all?

---

### Post by bmxboi42 on 2010-02-27
Yes itss the only HDD. How do i know if the Hardrive has a bootloader.
And the number 1 boot priority is set to the hardrive.

---

### Post by darkod on 2010-02-27
Set the first boot device as CDRON, second as HDD. Boot again with Try Ubuntu into the live desktop and run the boot info script which will show more details. Instructions how to run it are here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by bmxboi42 on 2010-02-27
Thank you, will try it soon and post on what happened on here. Cheers

---

### Post by bmxboi42 on 2010-02-27
HERE YA GO MATE:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b192b18

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,168,134    75,168,072  83 Linux
/dev/sda2          75,168,135    78,156,224     2,988,090   5 Extended
/dev/sda5          75,168,198    78,156,224     2,988,027  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4005 MB, 4005560320 bytes
21 heads, 21 sectors/track, 17740 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7075642b

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               8,064     7,823,359     7,815,296   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        3c14b986-207e-450c-995b-0364a6e86757   ext4                                     
/dev/sda5        6b597951-7927-4541-b561-48e7db0d9df5   swap                                     
/dev/sdf1        FD57-D14C                              vfat       USB2                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdf1        /media/USB2              vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 3c14b986-207e-450c-995b-0364a6e86757
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3c14b986-207e-450c-995b-0364a6e86757
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3c14b986-207e-450c-995b-0364a6e86757 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3c14b986-207e-450c-995b-0364a6e86757
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3c14b986-207e-450c-995b-0364a6e86757 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3c14b986-207e-450c-995b-0364a6e86757 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6b597951-7927-4541-b561-48e7db0d9df5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location o
```

---

### Post by darkod on 2010-02-27
It looks normal. The Grub2 bootloader is installed on the hdd and it should boot fine.
I would go into BIOS again and double check the booting options, also check if the hdd is recognized correctly.
And you mentioned it's an IDE disk. If you also have IDE CDROM and they are on the same cable, make sure the master/slave settings are not in conflict, for example they can't both be master.
Otherwise the install was successful and it looks fine.

---

### Post by bmxboi42 on 2010-02-27
Thanks so much mate, will try what you said. For now i am using the live cd copy.

Will check BIOS and stuff and try installation again.
How do i check the Hardrive is Being read properly and how do i know if the CD Drive AND Hardrive are on the same one?

Thanks

---

### Post by darkod on 2010-02-27
Well, if it's a desktop we are talking about, there will be one cable going from the motherboard into the cdrom and continuing into the hdd. If they are on one cable.
Or the cdrom and the hdd will be connected to the motherboard with separate data cables.

When you go into BIOS, either on the main page or after entering something like Standard BIOS options, there will be list of all hdds detected on the computer. So you should see your hdd listed there.

---

### Post by bmxboi42 on 2010-03-01
Still doesnt work, i dont know what to do :confused: :(

---

