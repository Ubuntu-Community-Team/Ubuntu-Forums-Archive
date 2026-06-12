---
title: "Need help restoring my MBR after Windows 7 install"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by wbao on 2010-07-23
I hope this is the right sub-forum for a question like this. It seemed like the best match from what I could find, but my issue stems from installing Windows 7 after I already had Ubuntu installed.

I don't know what details are important, so I'll be as thorough as I can. I was running Ubuntu 9.10 on a machine with two SATA hard drives. I was only using one since Ubuntu kept complaining that the second drive was having some issues. The drive with Ubuntu had only two partitions, one tiny one for the swap and the rest of the hard drive was the second partition.

I needed to install Windows for my work, and since I was not very familiar with the whole partition thing (which is the reason why the hard drive was basically one huge partition) I decided to follow this guide: [http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/](http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/). I backed up my important data, I used a live CD to create a new partition for windows, I backed up my MBR using the command given, and installed Windows 7. Everything went pretty smoothly. Now, whenever I boot up I don't get a choice of what OS to boot, it just goes straight to Windows, as expected.

I used the same live CD to restore the MBR using the command given on the guide, but I get this error:
dd: opening `/media/sda/mbr.bin': No such file or directory

I searched for a solution and found this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But I can't mount my Ubuntu partition as stated in step 2 from the live CD option because the Places menu shows none of my partitions. I tried searching for a solution on that, but I couldn't find anything that related to my problem.

So now I'm kind of stumped on what to do, and I'd appreciate if one of you can help me solve this :p

-----------------------------------------------------------------

Edit: I saw a thread a little below where someone is also having issues with GRUB although I don't think it's the same issue. Someone suggested he run the boot_info_script, so in case it's useful here are the results I got:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   216,202,769   216,202,707  83 Linux
/dev/sda2    *    216,203,264   216,408,063       204,800   7 HPFS/NTFS
/dev/sda3         216,408,064   476,213,247   259,805,184   7 HPFS/NTFS
/dev/sda4         476,214,795   488,279,609    12,064,815   5 Extended
/dev/sda5         476,214,858   488,279,609    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   246,678,074   246,678,012  83 Linux
/dev/sdb2         476,214,795   488,279,609    12,064,815   5 Extended
/dev/sdb5         476,214,858   488,279,609    12,064,752  82 Linux swap / Solaris
/dev/sdb3         246,678,075   476,214,794   229,536,720   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4a9a8650-d66b-486c-9cf2-68089cb8b615   ext4       ubuntu                        
/dev/sda2        B88E15258E14DDA6                       ntfs       System Reserved               
/dev/sda3        A2DE19EFDE19BD0B                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        356b950f-f23c-4cf9-b88e-bd25257da8d1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e2c60275-fe3b-43be-9e20-c40b5f626130   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        35EBE37B79CE0A75                       ntfs       windows                       
/dev/sdb5        356b950f-f23c-4cf9-b88e-bd25257da8d1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 4a9a8650-d66b-486c-9cf2-68089cb8b615
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
    search --no-floppy --fs-uuid --set 4a9a8650-d66b-486c-9cf2-68089cb8b615
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4a9a8650-d66b-486c-9cf2-68089cb8b615 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4a9a8650-d66b-486c-9cf2-68089cb8b615
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4a9a8650-d66b-486c-9cf2-68089cb8b615 ro single 
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
menuentry "Ubuntu 9.10 (9.10) (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c9a78bd3-e9dc-485f-8a2d-fb6774cc5c23
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1
    initrd /boot/initrd.img-2.6.31-14-generic
}
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
UUID=4a9a8650-d66b-486c-9cf2-68089cb8b615 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=356b950f-f23c-4cf9-b88e-bd25257da8d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.8GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz

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
search --no-floppy --fs-uuid --set e2c60275-fe3b-43be-9e20-c40b5f626130
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2c60275-fe3b-43be-9e20-c40b5f626130
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e2c60275-fe3b-43be-9e20-c40b5f626130 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2c60275-fe3b-43be-9e20-c40b5f626130
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e2c60275-fe3b-43be-9e20-c40b5f626130 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2c60275-fe3b-43be-9e20-c40b5f626130
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=e2c60275-fe3b-43be-9e20-c40b5f626130 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2c60275-fe3b-43be-9e20-c40b5f626130
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=e2c60275-fe3b-43be-9e20-c40b5f626130 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2c60275-fe3b-43be-9e20-c40b5f626130
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e2c60275-fe3b-43be-9e20-c40b5f626130 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2c60275-fe3b-43be-9e20-c40b5f626130
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e2c60275-fe3b-43be-9e20-c40b5f626130 ro single 
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
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4a9a8650-d66b-486c-9cf2-68089cb8b615
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=4a9a8650-d66b-486c-9cf2-68089cb8b615 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4a9a8650-d66b-486c-9cf2-68089cb8b615
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=4a9a8650-d66b-486c-9cf2-68089cb8b615 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=e2c60275-fe3b-43be-9e20-c40b5f626130 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=356b950f-f23c-4cf9-b88e-bd25257da8d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0


=================== sdb1: Location of files loaded by Grub: ===================


   5.3GB: boot/grub/core.img
   5.2GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .3GB: boot/initrd.img-2.6.31-21-generic
   2.7GB: boot/initrd.img-2.6.31-22-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.1GB: boot/vmlinuz-2.6.31-21-generic
   1.5GB: boot/vmlinuz-2.6.31-22-generic
   2.7GB: initrd.img
    .3GB: initrd.img.old
   1.5GB: vmlinuz
   1.1GB: vmlinuz.old

---

### Post by confused57 on 2010-07-23
See section #13 in this thread for reinstalling grub's IPL to the mbr:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Once you are able to boot into Ubuntu run sudo update-grub to add a Window's entry to grub.

---

### Post by oldfred on 2010-07-23
Be sure to follow instructions for grub2, not grub legacy (0.97).

previous link by confused57 will work. 

Another link.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD install on sda1 and want grub2 in drive sda's MBR:
Find linux partition, change sda1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

After rebooting 
sudo update-grub

You have another install on sdb1.

---

### Post by wbao on 2010-07-23
Thanks I got it to work! The only thing is that Windows seems to have created a few new partitions (even across both hard drives), and now I'm not sure which one is my main linux partition (I didn't label it, and I should have). Is there a way I can check what partition I'm currently using so I can label it?

---

### Post by oldfred on 2010-07-23
you can easily label with Disk Utility.

df

Will show you / (root) and other mounted partitions (My partition is a little large :))
```
fred@fred-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc5            100790004   6247128  89422964   7% /

```

---

