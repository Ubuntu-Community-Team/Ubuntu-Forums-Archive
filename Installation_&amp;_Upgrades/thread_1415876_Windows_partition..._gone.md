---
title: "Windows partition... gone?"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by pullvie on 2010-02-25
I installed Ubuntu a while ago and I love it(so much that I forgot about windows!).

But I have a problem. Before the installation I had three partitions:

C: Windows
D: Stuff
E: Some Compaq recovery thing

I installed Ubuntu on D: and I didn't do anything to C: (unless the ubuntu installer did). 

But I can't boot into Windows. When I pick Windows Xp in GRUB it boots the recovery thing instead. I tried to uninstall GRUB but it boots into Recovery Mode anyway.

Also something weird:

[http://img534.imageshack.us/img534/8619/depp.png](http://img534.imageshack.us/img534/8619/depp.png)

This is wrong. Presario_RP is actually about 7 gigs not 150.

[http://img534.imageshack.us/img534/3570/screenshotlo.png](http://img534.imageshack.us/img534/3570/screenshotlo.png)

The hard disk with ubuntu(incase yuo need it)

I don't really care about not being able to use windows but I have alot of important stuff on there that I can't access.

Sorry if my wording confuses you, I'm from Sweden so my English isn't perfect.

---

### Post by darkod on 2010-02-25
Can you run the boot info script as per the instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of your results file, it will show details about your boot process.

---

### Post by pullvie on 2010-02-25
Done.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       14620977 sectors.. But according to the info from the 
                       partition table , it has 312560576 sectors.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577  44 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd581d581

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   194,563,214   194,563,152  44 Unknown
/dev/sdb2         194,563,215   312,576,704   118,013,490   5 Extended
/dev/sdb5         194,563,278   198,467,009     3,903,732  82 Linux swap / Solaris
/dev/sdb6         198,467,073   218,002,049    19,534,977  83 Linux
/dev/sdb7         218,002,113   312,576,704    94,574,592  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        432A-D3D0                              vfat       PRESARIO_RP                   
/dev/sdb1        D85C59995C5972EC                       ntfs       New Volume                    
/dev/sdb5        57146dab-f28c-44a8-a557-495cbb61827f   swap                                     
/dev/sdb6        76894b1f-97bf-4547-911c-7616f2a8cc57   ext4                                     
/dev/sdb7        e774627c-0ac6-43a4-987c-255965de6edf   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb7        /home                    ext4       (rw)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=pullvie)
/dev/sda1        /media/PRESARIO_RP       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set 76894b1f-97bf-4547-911c-7616f2a8cc57
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 76894b1f-97bf-4547-911c-7616f2a8cc57
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=76894b1f-97bf-4547-911c-7616f2a8cc57 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 76894b1f-97bf-4547-911c-7616f2a8cc57
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=76894b1f-97bf-4547-911c-7616f2a8cc57 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 76894b1f-97bf-4547-911c-7616f2a8cc57
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=76894b1f-97bf-4547-911c-7616f2a8cc57 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 76894b1f-97bf-4547-911c-7616f2a8cc57
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=76894b1f-97bf-4547-911c-7616f2a8cc57 ro single 
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
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 432a-d3d0
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults               0  0  
# Entry for /dev/sdb6 :
UUID=76894b1f-97bf-4547-911c-7616f2a8cc57  /              ext4         errors=remount-ro      0  1  
# Entry for /dev/sdb7 :
UUID=e774627c-0ac6-43a4-987c-255965de6edf  /home          ext4         defaults               0  2  
# Entry for /dev/sdb5 :
UUID=57146dab-f28c-44a8-a557-495cbb61827f  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/sdb1    ntfs         defaults               0  0  

=================== sdb6: Location of files loaded by Grub: ===================


 104.6GB: boot/grub/core.img
 102.5GB: boot/grub/grub.cfg
 102.4GB: boot/initrd.img-2.6.31-14-generic
 105.0GB: boot/initrd.img-2.6.31-19-generic
 104.0GB: boot/vmlinuz-2.6.31-14-generic
 104.4GB: boot/vmlinuz-2.6.31-19-generic
 105.0GB: initrd.img
 102.4GB: initrd.img.old
 104.4GB: vmlinuz
 104.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by dE_logics on 2010-02-25
Give it another shot -- Run - 

```
sudo dpkg-reconfigure grub-pc
```

Whatever it says, keep selecting OK with it (with the keyboard).

---

### Post by darkod on 2010-02-25
=> Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

You don't have grub2 to neither disk, but that is not the main issue.

The main issue is that both ntfs partitions sda1 and sdb1 are reported as Unknown. In this situation of course grub2 will not be able to boot XP or even see that it's present.

It also reports that /dev/sda is one large partition while you say it should have 7GB Presarion partition and I guess the rest should be the XP system partition.

Scanning for partitions that are missing can be done with TestDisk. And if they are found the changes can be written to the partition table.

I suggest to check the disk with testdisk first, see if you can recover the XP partition that way. I haven't used it myself but the website also has instructions how to use it.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Later one it would be better to put windows mbr on /dev/sda, and reinstall grub2 on /dev/sdb.

---

