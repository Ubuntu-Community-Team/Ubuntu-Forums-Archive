---
title: "My grub config seems to be broken..."
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by kolya_m on 2010-02-01
Hi,

I've been messing round with Ubuntu for the past few days and have run into a problem. Before, I used to boot up and get the GRUB2 menu which would let me pick a partition to boot, which was great.

Now, however, I get a message saying something like 'No such filesystem' and a grub rescue prompt. After a bit of digging online, I worked out that I can get to the normal GRUB menu by typing:

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod /boot/grub/linux.mod
```...which gets me to the normal grub prompt where I can type 'normal' to get to the familiar GRUB2 boot menu with all my partitions.

Question is, how can I get it back to how it was before? I downloaded and ran [this boot script]("http://bootinfoscript.sourceforge.net/") and this was the result:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=337c6524-cf9b-451a-b639-76ba6e6f1f30)/boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Recovery: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   355,775,489   355,663,035   7 HPFS/NTFS
/dev/sda3         481,966,065   488,263,544     6,297,480  db CP/M / CTOS / ...
/dev/sda4         355,775,490   481,966,064   126,190,575   5 Extended
/dev/sda5         355,775,553   476,728,874   120,953,322  83 Linux
/dev/sda6         476,728,938   481,966,064     5,237,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0111                              vfat       DellUtility                   
/dev/sda2        0A1C0D751C0D5D57                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda5        c743b535-ed5a-4443-af6d-246a735d210b   ext4                                     
/dev/sda6        4ed4a851-3cf7-4d3e-a68a-384d4d54aa6b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/cdrom1            iso9660    (ro,nosuid,nodev,utf8,user=nick)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=nick)
/dev/sr2         /media/web'n'walk        iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set c743b535-ed5a-4443-af6d-246a735d210b
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set c743b535-ed5a-4443-af6d-246a735d210b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c743b535-ed5a-4443-af6d-246a735d210b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set c743b535-ed5a-4443-af6d-246a735d210b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c743b535-ed5a-4443-af6d-246a735d210b ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set c743b535-ed5a-4443-af6d-246a735d210b
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=c743b535-ed5a-4443-af6d-246a735d210b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set c743b535-ed5a-4443-af6d-246a735d210b
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=c743b535-ed5a-4443-af6d-246a735d210b ro single 
    initrd    /boot/initrd.img-2.6.31-9-rt
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
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 07d7-0111
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0a1c0d751c0d5d57
    drivemap -s (hd0) ${root}
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
UUID=c743b535-ed5a-4443-af6d-246a735d210b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4ed4a851-3cf7-4d3e-a68a-384d4d54aa6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```Can anyone see what might be wrong? Thanks in advance.

Kolya

PS - This all started after I installed the StartUp-Manager. Could this have anything to do with it?

---

### Post by darkod on 2010-02-01
I don't know what you did but the UUID of the root partition seems to have changed, hence the error. You should be able to reinstall grub2 to the MBR and get it sorted.
Boot with the 9.10 cd, Try Ubuntu option, and in terminal do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd and see how it goes.

---

### Post by oldfred on 2010-02-01
Startup manager should not have done this. Did you edit any partitions?

The grub in the MBR is looking for UUID 337c... but you have no UUID with that number. Your install is on 
/dev/sda5        c743b535-ed5a-4443-af6d-246a735d210b

Reinstall grub so it points to the correct partition.

reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

or 
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) 
Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by kolya_m on 2010-02-01
Amazing! Thanks so much for the replies. I tried darkod's suggestion and it worked perfectly. No idea how this happened, but at least I know how to mend it in the future.

Thanks again.

Kolya

---

