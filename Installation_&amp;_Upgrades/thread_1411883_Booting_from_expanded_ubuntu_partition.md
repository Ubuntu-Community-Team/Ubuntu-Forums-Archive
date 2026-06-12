---
title: "Booting from expanded ubuntu partition"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by amrSamir on 2010-02-20
Hi all,

I have tried ubuntu 9.10 for 2 months, and I really liked it. So I decided to get rid of my Windows XP and expand my 10 GB linux partition to 146 GB.

So I used GParted. I backed up the windows on some hard drive, and copied the 10 GB partition to the 146 GB partition (so I had the same data twice on my laptop). Here is a [screenshot]("http://img715.imageshack.us/img715/6214/screenshotpalimpsestdis.png") of my partitions

When I restarted, I booted normally to find myself in the 146 GB partition (which is great). The next time I booted normally to find my self back in the 10 GB partition. Every time I try to boot now I end up in the 10 GB partition. 

Can someone help pls? I'm a noob, but I guess it has to do with the configuration of GRUB to boot to one partition not another?

---

### Post by drs305 on 2010-02-20
amrSamir,

Welcome to Ubuntu and the Ubuntu forums.

Please post the results of the [boot info script]("http://bootinfoscript.sourceforge.net/"). It will most likely give us the information we need to provide you with a solution. Post the results between [noparse]```

```[/noparse] tags by using the # icon in the message menu.

---

### Post by amrSamir on 2010-02-20
Thanks for your reply. Here it is.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 293494591 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #6 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       224,909       224,847  de Dell Utility
/dev/sda2    *        224,910   286,342,559   286,117,650  83 Linux
/dev/sda4         286,342,621   312,578,047    26,235,427   f W95 Ext d (LBA)
/dev/sda5         307,337,216   312,578,047     5,240,832  dd Dell Media Direct
/dev/sda6         286,342,623   306,343,484    20,000,862  83 Linux
/dev/sda7         306,343,548   307,323,449       979,902  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0919                              vfat       DellUtility                   
/dev/sda2        2c6e811d-d20b-4f54-a93f-7f10b6954a63   ext4                                     
/dev/sda5        4473-C438                              vfat       MEDIADIRECT                   
/dev/sda6        2c6e811d-d20b-4f54-a93f-7f10b6954a63   ext4                                     
/dev/sda7        e753ab3c-244b-4fff-97b9-4c1e79729170   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=amr)


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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
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
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
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
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 07d7-0919
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 06f06fc2f06fb699
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod fat
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4473-c438
	drivemap -s (hd0) ${root}
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
proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda6 during installation
UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63  /              ext4         errors=remount-ro        0  1  
# swap was on /dev/sda7 during installation
UUID=e753ab3c-244b-4fff-97b9-4c1e79729170  none           swap         sw                       0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0  
/dev/sda3                                  /media/OS      ntfs         nls=iso8859-1,umask=000  0  0  

=================== sda2: Location of files loaded by Grub: ===================


   9.0GB: boot/grub/core.img
   9.6GB: boot/grub/grub.cfg
   7.7GB: boot/initrd.img-2.6.31-14-generic
   8.3GB: boot/initrd.img-2.6.31-15-generic
   5.4GB: boot/initrd.img-2.6.31-16-generic
   3.7GB: boot/initrd.img-2.6.31-17-generic
   2.1GB: boot/initrd.img-2.6.31-19-generic
   2.5GB: boot/vmlinuz-2.6.31-14-generic
   8.1GB: boot/vmlinuz-2.6.31-15-generic
   6.7GB: boot/vmlinuz-2.6.31-16-generic
   3.9GB: boot/vmlinuz-2.6.31-17-generic
   4.0GB: boot/vmlinuz-2.6.31-19-generic
   2.1GB: initrd.img
   3.7GB: initrd.img.old
   4.0GB: vmlinuz
   3.9GB: vmlinuz.old

================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

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
search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
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
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c6e811d-d20b-4f54-a93f-7f10b6954a63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63 ro single 
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
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 07d7-0919
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod fat
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4473-c438
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
proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda6 during installation
UUID=2c6e811d-d20b-4f54-a93f-7f10b6954a63  /              ext4         errors=remount-ro        0  1  
# swap was on /dev/sda7 during installation
UUID=e753ab3c-244b-4fff-97b9-4c1e79729170  none           swap         sw                       0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0  
/dev/sda3                                  /media/OS      ntfs         nls=iso8859-1,umask=000  0  0  

=================== sda6: Location of files loaded by Grub: ===================


 150.2GB: boot/grub/core.img
 150.5GB: boot/grub/grub.cfg
 154.1GB: boot/initrd.img-2.6.31-14-generic
 154.8GB: boot/initrd.img-2.6.31-15-generic
 151.9GB: boot/initrd.img-2.6.31-16-generic
 150.2GB: boot/initrd.img-2.6.31-17-generic
 148.6GB: boot/initrd.img-2.6.31-19-generic
 149.0GB: boot/vmlinuz-2.6.31-14-generic
 154.6GB: boot/vmlinuz-2.6.31-15-generic
 153.2GB: boot/vmlinuz-2.6.31-16-generic
 150.4GB: boot/vmlinuz-2.6.31-17-generic
 150.5GB: boot/vmlinuz-2.6.31-19-generic
 148.6GB: initrd.img
 150.2GB: initrd.img.old
 150.5GB: vmlinuz
 150.4GB: vmlinuz.old

```

---

### Post by drs305 on 2010-02-20
Both your old and new partitions have the same UUID, so you must change the old one. The following will give sda6 a new UUID and set up Grub 2 to boot from sda2.

Change the UUID of the sda6 / partition:
```
sudo tune2fs -U random /dev/sda6
```
At this point, the UUID of your (old) root / partition has changed and the boot files don't have the correct information. Make sure to complete the next step before rebooting.

You now want to get Grub 2 to boot from the files in sda2, so mount sda2 and then reinstall Grub 2:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot, then run```

sudo update-grub
```

---

### Post by amrSamir on 2010-02-20
Thanks alot, worked like charm. :D

If you don't mind, can you explain whats the UUID of a partition.

---

### Post by drs305 on 2010-02-20
> **amrSamir said:**
> Thanks alot, worked like charm. :D

If you don't mind, can you explain whats the UUID of a partition.

Previously devices (drives) were identified as hda, hdb, hdc and their partitions 1, 2, 3, etc. So the first partition on the first drive was hda1. A few years ago, the designation was changed to **s**dXY.  As removable drives became more common, there was a problem identifying drives in this manner - the designations were made by the order the devices were mounted, but the mounting order didn't always stay the same. Thus, a drive that was *sdb* on one boot may be *sdd* on another boot. This caused obvious problems with system files which relied on consistently identifying a particular device/partition.

Linux now uses UUIDs, Universally Unique Identifiers. These normally do not change (unless the partition is formattted, etc) and provide consistency in these days of swappable drives.

[http://en.wikipedia.org/wiki/Universally_Unique_Identifier]("http://en.wikipedia.org/wiki/Universally_Unique_Identifier")

---

### Post by DasEi on 2010-02-20
uuid is a  disk identifier used to provide unique labels for partitions. you can run sudo blkid to show your current ones, they consist of a long string and are used in grub2 and fstab.
Rationale behind this that they don't change like /dev/sda1 to /dev/sdb1 when you just change a master drive to slave,, same o'course in multidisk (think external) environments.
You can have two identical uuids on the same system if you use tools like dd.

---

