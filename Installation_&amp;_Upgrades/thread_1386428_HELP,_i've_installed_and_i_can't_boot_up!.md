---
title: "HELP, i've installed and i can't boot up!"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by rudebuntu on 2010-01-20
well i figured i'd pay homage to an old lady from the 80s to get my thread started..

first time ubuntu installer, but a fan of the forums and google in general.. i say this because i don't consider myself to be 100% stupid.. but i definitely made a mistake
that isn't very normal:


i was running windows by itself and decided to dual boot.. normally this would've been fine i'm sure, but i forgot to unplug my external usb drive before installation and during the setup i don't know where i went wrong but i ended up getting the external usb very involved in the installation lol. when i run ubuntu it's fine.. everything works but when i unplug it it fails hard.. i get a resource error then it dies after all the icons disappear.. and i get errors like: ext4-fs errors and directory device errors with sdb5.. also if i dont have my external usb plugged in.. when i start my computer grub comes on and says no such disk everytime.. so i must have the grub boot info on my usb drive? very confusing to me..

i'd be more than willing to provide any txt outputs or screenshots of my setup if you think it will help..

so my question is where would i get started correcting this issue.. i definitely want to continue dual booting.. but i dont know if i can just edit grub to point to my windows drive initially.. or if i can just fix the mbr like ive been reading that.. or probably there are ways of correcting this that i'm ignorant to, at any rate, any help would be greatly appreciated.

thanks!

---

### Post by presence1960 on 2010-01-20
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external HDD plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by rudebuntu on 2010-01-20
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2             178,176    21,149,695    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,149,696   574,404,074   553,254,379   7 HPFS/NTFS
/dev/sda4         574,404,075   625,137,344    50,733,270  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   582,243,794   582,243,732   c W95 FAT32 (LBA)
/dev/sdb2         582,243,795   625,137,344    42,893,550   5 Extended
/dev/sdb5         582,243,858   623,257,739    41,013,882  83 Linux
/dev/sdb6         623,257,803   625,137,344     1,879,542  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-090A" TYPE="vfat" 
/dev/sda2: UUID="18D82ED0D82EAC46" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="885831BD5831AAB8" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="ubuntu" UUID="02b78318-d214-48b1-b32b-183ed88f8e22" TYPE="ext4" 
/dev/sdb1: UUID="4A01-005C" TYPE="vfat" 
/dev/sdb5: UUID="6289a680-84be-421f-8c8f-2b7b0078ca9b" TYPE="ext4" 
/dev/sdb6: UUID="21b8cd73-a903-4c3d-a765-7741fb031e4e" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/v/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=v)
/dev/sdb1 on /media/4A01-005C type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 6289a680-84be-421f-8c8f-2b7b0078ca9b
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6289a680-84be-421f-8c8f-2b7b0078ca9b
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6289a680-84be-421f-8c8f-2b7b0078ca9b
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6289a680-84be-421f-8c8f-2b7b0078ca9b
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6289a680-84be-421f-8c8f-2b7b0078ca9b
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6289a680-84be-421f-8c8f-2b7b0078ca9b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6289a680-84be-421f-8c8f-2b7b0078ca9b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 885831bd5831aab8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=6289a680-84be-421f-8c8f-2b7b0078ca9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=21b8cd73-a903-4c3d-a765-7741fb031e4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 298.1GB: boot/grub/core.img
 298.1GB: boot/grub/grub.cfg
 298.1GB: boot/initrd.img-2.6.31-14-generic
 298.1GB: boot/initrd.img-2.6.31-15-generic
 298.1GB: boot/initrd.img-2.6.31-16-generic
 298.1GB: boot/vmlinuz-2.6.31-14-generic
 298.1GB: boot/vmlinuz-2.6.31-15-generic
 298.1GB: boot/vmlinuz-2.6.31-16-generic
 298.1GB: initrd.img
 298.1GB: initrd.img.old
 298.1GB: vmlinuz
 298.1GB: vmlinuz.old

---

### Post by presence1960 on 2010-01-20
you installed ubuntu to the external drive but put GRUB on the MBR of the internal disk. You have 2 choices:

1. reinstall Ubuntu to the internal (leave the external unplugged) and fix your external partitioning later. OR

2. It will work like this but you need to do two things from the Ubuntu Live CD. First you want to fix the internal disk's MBR so windows will boot. Then you want to put GRUB on the external disk's MBR. This will do the following: Allow you to boot right to windows when the external is unplugged and when you boot with ther external plugged in GRUB will take over and you can boot Ubuntu.

If it is #1 proceed with the new install with the external unplugged.
If it is #2 boot the Ubuntu Live CD with external plugged in & choose "try ubuntu without any changes". When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
```
This will install lilo to the live CD session. Now you will repair the MBR of the internal disk so windows can boot. In terminal run ```
sudo lilo -M /dev/sda mbr
```

Now you want to put GRUB on MBR of the external disk. In terminal run ```
sudo mount /dev/sdb5 /mnt
```
This will mount your ubuntu / partition. next you will install GRUB to MBR of the external disk. In terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
When complete reboot without the Live CD and the external unplugged to boot windows, then reboot with the external plugged in to boot GRUB and choose Ubuntu.

---

