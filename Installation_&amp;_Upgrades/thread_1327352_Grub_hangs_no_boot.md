---
title: "Grub hangs no boot"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Stevertheo on 2009-11-15
I have xp and have added 9.10 from live cd. several attemps have resulted in Grub2 hangup. goes to >grub rescue 

the plan is to have xp and 9.10 dual boot

I have tried, several times, The Live Cd, reinstall described in several places in this forum,     ( grub-setup)as well as the chroot version.  

I have reinstalled 9.10 one time

in all cases I still end up with grub rescue> or sh:grub

Any ideas ???

Thanks

---

### Post by drs305 on 2009-11-15
Have you tried/been able to boot into Ubuntu from the grub-rescue prompt? Usually getting the rescue prompt means that G2 can't find the grub.cfg file or it is unusable.

From the grub-rescue prompt you might be able to boot into your system by entering the following:
set root=(hdX,Y)  # Drives start at 0, partitions at 1 
linux /boot/vmlin  then tab to complete, **then add:**  root=/dev/sdXY
initrd /boot/initr then tab to complete
boot

If it doesn't boot, you can use the "ls" command to see what drives/partitions it sees, and "ls (hdX,Y)/boot to see what is in the boot partition (or "ls (hdX,Y)/xxxxxxx for other folders.

Let us know if that doesn't help.

---

### Post by Stevertheo on 2009-11-15
so I tried , but the following happens;

ls reports (hd,0) (hd,1) (hd,5)  I believe this makes sense as sda2 is where xp is and sda6 is where 9.10 is however i have sda1, 2, 4, 5, 6, 7, 8

any further ls inquires results in: unknown file system

Tab function does not work and has never worked.

am I missing something ????


Thanks Again

---

### Post by Stevertheo on 2009-11-15
I ran " boot info script 0.34" and it produced these results:
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bef1bef

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   488,392,064   406,476,630   f W95 Ext d (LBA)
/dev/sda5          81,915,498   210,162,329   128,246,832   7 HPFS/NTFS
/dev/sda6         334,409,103   484,745,309   150,336,207  83 Linux
/dev/sda7         484,745,373   488,392,064     3,646,692  82 Linux swap / Solaris
/dev/sda8         210,162,393   334,409,039   124,246,647  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6050934450931FB8" TYPE="ntfs" 
/dev/sda5: UUID="0A3C6EEA3C6ECFED" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="f973b8d8-42fa-482d-8964-6b6a341341c8" TYPE="ext4" 
/dev/sda7: UUID="1339d03a-e1cc-409f-942a-66df74c25c5f" TYPE="swap" 
/dev/sda8: UUID="2704544b-f8e1-4c33-86b9-e0d55ad2c533" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/6050934450931FB8 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/f973b8d8-42fa-482d-8964-6b6a341341c8 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sda8 on /media/2704544b-f8e1-4c33-86b9-e0d55ad2c533 type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set f973b8d8-42fa-482d-8964-6b6a341341c8
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
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set f973b8d8-42fa-482d-8964-6b6a341341c8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f973b8d8-42fa-482d-8964-6b6a341341c8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set f973b8d8-42fa-482d-8964-6b6a341341c8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f973b8d8-42fa-482d-8964-6b6a341341c8 ro single 
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
    search --no-floppy --fs-uuid --set 6050934450931fb8
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=f973b8d8-42fa-482d-8964-6b6a341341c8 /               ext4    errors=remount-ro 0       1
# /opt was on /dev/sda8 during installation
UUID=2704544b-f8e1-4c33-86b9-e0d55ad2c533 /opt            ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=1339d03a-e1cc-409f-942a-66df74c25c5f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 171.2GB: boot/grub/grub.cfg
 171.2GB: boot/initrd.img-2.6.31-14-generic
 171.2GB: boot/vmlinuz-2.6.31-14-generic
 171.2GB: initrd.img
 171.2GB: vmlinuz
```

---

