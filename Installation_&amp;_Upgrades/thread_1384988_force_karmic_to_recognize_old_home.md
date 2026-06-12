---
title: "force karmic to recognize old /home"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by emeraldgirl08 on 2010-01-19
I had a problem earlier that required me to reinstall Karmic. I reinstalled only the / file. Little did I know that install would squeeze everything into that little partition. I have a /home and /swap part from my previous install.

How do I force Karmic to recognize my old /home?

This is my boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 8192.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004506a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 HPFS/NTFS
/dev/sda2          41,945,715    56,645,189    14,699,475  83 Linux
/dev/sda3          56,645,190    73,481,309    16,836,120   5 Extended
/dev/sda5          56,645,253    71,344,664    14,699,412  83 Linux
/dev/sda6          71,344,728    73,481,309     2,136,582  82 Linux swap / Solaris
/dev/sda4          73,481,310    94,462,199    20,980,890   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3999 MB, 3999793152 bytes
98 heads, 33 sectors/track, 2415 cylinders, total 7812096 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52a8513c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192     7,812,095     7,803,904   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="77C9E1866B7F8803" TYPE="ntfs" 
/dev/sda2: UUID="83c338f1-3296-4c5e-91f3-b080eb21d981" TYPE="ext4" 
/dev/sda4: UUID="13867B827C3AE69C" LABEL="Share" TYPE="ntfs" 
/dev/sda5: UUID="6c7fca7c-5914-4e7d-bea9-cb5f8a2d6425" TYPE="ext4" 
/dev/sda6: UUID="b22f8ff4-18e1-4dae-aa7a-939158536271" TYPE="swap" 
/dev/sdb1: LABEL="New Volume" UUID="776A-2F6B" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tyreneb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tyreneb)
/dev/sdb1 on /media/New Volume type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 83c338f1-3296-4c5e-91f3-b080eb21d981
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 83c338f1-3296-4c5e-91f3-b080eb21d981
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=83c338f1-3296-4c5e-91f3-b080eb21d981 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 83c338f1-3296-4c5e-91f3-b080eb21d981
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=83c338f1-3296-4c5e-91f3-b080eb21d981 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 77c9e1866b7f8803
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=83c338f1-3296-4c5e-91f3-b080eb21d981 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b22f8ff4-18e1-4dae-aa7a-939158536271 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  21.4GB: boot/grub/core.img
  21.4GB: boot/grub/grub.cfg
  21.4GB: boot/initrd.img-2.6.31-14-generic
  21.4GB: boot/vmlinuz-2.6.31-14-generic
  21.4GB: initrd.img
  21.4GB: vmlinuz
```



TIA.

---

### Post by kellemes on 2010-01-19
Next time, you could go for a manual partitioning.. and tell the partitioner to not format the /home-partition, personally I'd never trust this but it should work.

So you better reinstall Karmic as it was installed to begin with.. and simply copy the contents of the old /home-directory to the newly made /home-directory. For this you need to create a backup of the original /home-directory obviously..

You have to understand it's a directory structure here.. so / is the top of the tree and /home comes beneath that.

By the way, swap you don't have to backup.

---

### Post by emeraldgirl08 on 2010-01-19
Gotcha. Going for a reinstall now. Thanks!

---

