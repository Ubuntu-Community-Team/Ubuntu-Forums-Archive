---
title: "new user grub 2 setup"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by smokin74 on 2010-01-15
Hi there - yet another first post asking for help!! - ive recently installed 9.10 and i am enjoying most of the experience - just a few niggles including getting the sound to work with my audigy card - but ill deal with that later. im not entirely new to linux as such been using mepis for the last 4 years as my main desktop. i have a 2 disk setup = win xp on one disk and currently mepis 8 and ubuntu on the other . during install i chose to arrange my own partitions and as such it appears grub wasnt installed correctly (i assume this to be the reason) - all i get at boot is 'waiting for grub' - if you leave it long enough (15minutes) it does give you a boot menu. i can get round all this by fixing grub using mepis but i want to give grub 2 a go via ubuntu

ive tried reinstalling and i still get the same outcome - is it because mbr is on sda1 and ubuntu is on sdb6 (inmy case) do i need to edit a config somewhere


any help appreciated

thanks

Chris

---

### Post by tachuela on 2010-01-15
Have you tried changing the order of boot of the HH's in BIOS?

---

### Post by smokin74 on 2010-01-15
no - i wouldnt have thought i'd have to given that it has worked fine with grub legacy for so long - but i see your line of thinking and will give it a try. 

thanks

Chris

---

### Post by smokin74 on 2010-01-15
in short - that didnt work


back to the drawing board

used the boot script on another post to give this output if it helps anyone - looks like its still seeing my mepis grub legacy config - what to do now?

anyways heres the text:
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  MEPIS Linux 8.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf872f872

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   122,881,184    40,965,750   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000eb65f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    60,822,089    60,822,027  83 Linux
/dev/sdb2          60,822,090    62,926,604     2,104,515  82 Linux swap / Solaris
/dev/sdb3          62,926,605   146,818,034    83,891,430  83 Linux
/dev/sdb4         146,818,035   398,074,634   251,256,600   5 Extended
/dev/sdb5         146,818,098   251,674,289   104,856,192   7 HPFS/NTFS
/dev/sdb6         251,674,353   311,677,064    60,002,712  83 Linux
/dev/sdb7         311,677,128   398,074,634    86,397,507  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1021 MB, 1021837312 bytes
31 heads, 62 sectors/track, 1038 cylinders, total 1995776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00025369

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            247     1,995,775     1,995,529   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AEA41A68A41A32F7" LABEL="SYSTEM DRIVE" TYPE="ntfs" 
/dev/sda2: UUID="840C35AF0C359D5C" LABEL="stuff" TYPE="ntfs" 
/dev/sdb1: UUID="ca1ec592-78f3-4ecb-92d4-f91d3c82e397" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="f6cc8c25-3295-4c49-b27c-c54a12389e2b" TYPE="swap" 
/dev/sdb3: UUID="7b8653db-5310-4cdc-b208-dd8a98425215" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="2739F9893850C091" LABEL="Multimedia" TYPE="ntfs" 
/dev/sdb6: UUID="662539a2-dd8b-4b68-bcf0-9173d35f3f4e" TYPE="ext3" 
/dev/sdb7: UUID="c1908d7b-d8c6-4800-8dc8-eba665318f5d" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="" UUID="E0FD-1813" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,errors=remount-ro)
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
/dev/sdb7 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/smokin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=smokin)
/dev/sdc1 on /media/E0FD-1813 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=smokin)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdb1/boot/grub/menu.lst: ===========================

timeout 10
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at sdb1, newest kernel
root (hd1,0)
kernel /boot/vmlinuz root=/dev/sdb1 nomce quiet splash vga=795 
initrd /boot/initrd.img
boot

title MEPIS at sdb1, kernel 2.6.27-1-mepis-smp
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-1-mepis-smp root=/dev/sdb1 nomce quiet splash vga=795 
initrd /boot/initrd.img-2.6.27-1-mepis-smp
boot

title Microsoft Windows XP Professional at sda1
rootnoverify (hd0,0)
chainloader +1

title Ubuntu, Linux 2.6.31-17-generic
root (hd1,5)
kernel /boot/vmlinuz-2.6.31-17-generic root=UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e ro quiet splash
initrd /boot/initrd.img-2.6.31-17-generic

title MEMTEST
kernel /boot/memtest86+.bin


=============================== sdb1/etc/fstab: ===============================

# Pluggable devices are handled by uDev, they are not in fstab
/dev/sdb1 / ext3 defaults,noatime 1 1
/dev/sdb2 swap swap sw,pri=1 0 0
/dev/sdb3 /home auto defaults,noatime 1 2
/dev/sda1 /mnt/sda1 ntfs-3g rw,users,auto,umask=000 0 0
/dev/sda2 /mnt/sda2 ntfs-3g rw,users,auto,umask=000 0 0
/dev/sda3 /mnt/sda3 ext3 noauto,users,exec,relatime 0 0
/dev/sdb5 /mnt/sdb5 ntfs-3g rw,users,auto,umask=000 0 0
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/sdb6 /mnt/sdb6 ext3 noauto,users,exec,relatime 0 0
/dev/sdb7 /mnt/sdb7 ext3 noauto,users,exec,relatime 0 0
/dev/sdc1 /mnt/sdc1 vfat noauto,users,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/sr0 /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img
    .0GB: boot/initrd.img-2.6.27-1-mepis-smp
    .0GB: boot/initrd.img-2.6.27-1-mepis-smp.bak
    .0GB: boot/vmlinuz
    .0GB: boot/vmlinuz-2.6.27-1-mepis-smp

================================ sdb5/menu.lst: ================================

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title 1-MEPIS at sdb1, newest kernel
root (hd1,0)
kernel /boot/vmlinuz root=/dev/sdb1 nomce quiet splash vga=791 resume=/dev/sdb2

title 2-ANTIX at sdb6, newest kernel
root (hd1,5)
kernel /boot/vmlinuz root=/dev/sdb6 nomce quiet splash vga=791 
boot

title 3-WINDOWS XP PRO at sda1
rootnoverify (hd0,0)
chainloader +1

title 4-ANTIX at sdb6, previous kernel (if any)
root (hd1,5)
kernel /boot/vmlinuz.old root=/dev/sdb6 nomce quiet splash vga=791 
boot

title 5-ANTIX at sdb6, kernel 2.6.27-1-mepis-smp
root (hd1,5)
kernel /boot/vmlinuz-2.6.27-1-mepis-smp root=/dev/sdb6 nomce quiet splash vga=791 
boot

title 6-SIDUX GNU/Linux, kernel 2.6.27-7.slh.4-sidux-686
root (hd0,2)
kernel /boot/vmlinuz-2.6.27-7.slh.4-sidux-686 root=UUID=80613286-3590-46c5-ab1e-a89cdaddeaf0 ro quiet vga=791
initrd /boot/initrd.img-2.6.27-7.slh.4-sidux-686



title 7-MEMTEST
kernel /boot/memtest86+.bin


=================== sdb5: Location of files loaded by Grub: ===================


  75.1GB: menu.lst

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
search --no-floppy --fs-uuid --set 662539a2-dd8b-4b68-bcf0-9173d35f3f4e
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 662539a2-dd8b-4b68-bcf0-9173d35f3f4e
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 662539a2-dd8b-4b68-bcf0-9173d35f3f4e
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e ro single 
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 662539a2-dd8b-4b68-bcf0-9173d35f3f4e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 662539a2-dd8b-4b68-bcf0-9173d35f3f4e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 662539a2-dd8b-4b68-bcf0-9173d35f3f4e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 662539a2-dd8b-4b68-bcf0-9173d35f3f4e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set aea41a68a41a32f7
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "MEPIS at sdb1, newest kernel (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ca1ec592-78f3-4ecb-92d4-f91d3c82e397
    linux /boot/vmlinuz root=/dev/sdb1 nomce quiet splash vga=795
    initrd /boot/initrd.img
}
menuentry "MEPIS at sdb1, kernel 2.6.27-1-mepis-smp (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ca1ec592-78f3-4ecb-92d4-f91d3c82e397
    linux /boot/vmlinuz-2.6.27-1-mepis-smp root=/dev/sdb1 nomce quiet splash vga=795
    initrd /boot/initrd.img-2.6.27-1-mepis-smp
}
menuentry "MEMTEST (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ca1ec592-78f3-4ecb-92d4-f91d3c82e397
    linux /boot/memtest86+.bin 
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=662539a2-dd8b-4b68-bcf0-9173d35f3f4e /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=c1908d7b-d8c6-4800-8dc8-eba665318f5d /home           ext3    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=f6cc8c25-3295-4c49-b27c-c54a12389e2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 128.8GB: boot/grub/core.img
 128.8GB: boot/grub/grub.cfg
 128.8GB: boot/initrd.img-2.6.31-14-generic
 128.8GB: boot/initrd.img-2.6.31-17-generic
 128.8GB: boot/initrd.img-2.6.31-18-generic
 128.8GB: boot/vmlinuz-2.6.31-14-generic
 128.8GB: boot/vmlinuz-2.6.31-17-generic
 128.8GB: boot/vmlinuz-2.6.31-18-generic
 128.8GB: initrd.img
 128.8GB: initrd.img.old
 128.8GB: vmlinuz
 128.8GB: vmlinuz.old
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
```

hope this helps !!!

cheers

chris

---

