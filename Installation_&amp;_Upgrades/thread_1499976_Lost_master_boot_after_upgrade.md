---
title: "Lost master boot after upgrade"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by jfedor on 2010-06-02
Upgraded to 10.04 and now ubuntu will not load and we are sent to a grub shell.  Tried reinstalling grub without success.  can't find /boot/grub/stage1.  can't reinstall system from CD.  Partitioner fails with ??? ???

---

### Post by darkod on 2010-06-02
Can you run the boot info script as per these instructions?
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of the results file as explained. It should show us more.

---

### Post by jfedor on 2010-06-03
Here are the results from the script you told me to run.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 483393 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #256 for /grub.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 479629 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb1 starts at sector 0. But according to the info 
                       from fdisk, sdb1 starts at sector 63.
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

Disk /dev/sda: 500.0 GB, 499989348352 bytes
255 heads, 63 sectors/track, 60786 cylinders, total 976541696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       498,014       497,952  83 Linux
/dev/sda2             498,015    29,794,863    29,296,849  83 Linux
/dev/sda3          29,794,864    45,417,910    15,623,047  82 Linux swap / Solaris
/dev/sda4          45,417,911   976,541,695   931,123,785  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b5590d0e-2d08-4a7a-8510-08f0e2cd671d   ext3       mbr                           
/dev/sda2        018c5214-5a80-469b-b3a4-63f271ca06d6   ext3                                     
/dev/sda3        9ee93eed-2231-4385-9125-b87b680812e9   swap                                     
/dev/sda4        4a5ea30e-237b-416d-a794-dcecd4cbdc39   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4637-7ED5                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8807-2C2B                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/mbr               ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/018c5214-5a80-469b-b3a4-63f271ca06d6 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/8807-2C2B         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 018c5214-5a80-469b-b3a4-63f271ca06d6
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
menuentry "Ubuntu, Linux 2.6.31-21-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-21-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-21-server
}
menuentry "Ubuntu, Linux 2.6.31-21-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-21-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-21-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-20-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-20-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-19-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-19-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-19-server
}
menuentry "Ubuntu, Linux 2.6.31-19-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-19-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-19-server
}
menuentry "Ubuntu, Linux 2.6.31-17-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-17-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-17-server
}
menuentry "Ubuntu, Linux 2.6.31-17-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-17-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-17-server
}
menuentry "Ubuntu, Linux 2.6.31-16-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-16-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-16-server
}
menuentry "Ubuntu, Linux 2.6.31-16-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-16-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-16-server
}
menuentry "Ubuntu, Linux 2.6.31-14-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-14-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-server
}
menuentry "Ubuntu, Linux 2.6.31-14-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-14-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-14-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-server
    .0GB: initrd.img-2.6.31-16-server
    .0GB: initrd.img-2.6.31-17-server
    .0GB: initrd.img-2.6.31-19-server
    .0GB: initrd.img-2.6.31-20-server
    .1GB: initrd.img-2.6.31-21-server
    .0GB: vmlinuz-2.6.31-14-server
    .0GB: vmlinuz-2.6.31-16-server
    .0GB: vmlinuz-2.6.31-17-server
    .0GB: vmlinuz-2.6.31-19-server
    .0GB: vmlinuz-2.6.31-20-server
    .0GB: vmlinuz-2.6.31-21-server

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	defaults	0	0
# / was on /dev/sda2 during installation
UUID=018c5214-5a80-469b-b3a4-63f271ca06d6	/	ext3	errors=remount-ro	0	1	# /dev/sda2
# /boot was on /dev/sda1 during installation
UUID=b5590d0e-2d08-4a7a-8510-08f0e2cd671d	/boot	ext3	defaults	0	2	# /dev/sda1
# /home was on /dev/sda4 during installation
UUID=4a5ea30e-237b-416d-a794-dcecd4cbdc39	/home	ext3	defaults	0	2	# /dev/sda4
# swap was on /dev/sda3 during installation
UUID=56c8381e-bc2f-46da-83a1-bb10fc3272c6	none	swap	sw	0	0	# /dev/sda3
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

```

---

### Post by darkod on 2010-06-03
You are using grub2, it doesn't use any more /boot/grub/stage1, that procedure is for reinstalling grub1.

However, it seems the upgrade didn't finish at all:

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    [COLOR=Red]Operating System:  Ubuntu 9.10[/COLOR]
    Boot files/dirs:   /etc/fstab

As for reinstalling grub2 to the MBR, you have /boot partition on /dev/sda1 and / on /dev/sda2. Not sure how you reinstall grub2 on a server version, but on desktop version from live mode with separate /boot partition it would be like:

sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

---

