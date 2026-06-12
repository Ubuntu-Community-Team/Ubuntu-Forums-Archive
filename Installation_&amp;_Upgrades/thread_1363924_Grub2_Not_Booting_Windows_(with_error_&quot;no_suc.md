---
title: "Grub2 Not Booting Windows (with error &quot;no such device&quot;)"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by DinkyDogg on 2009-12-25
I've just done a fresh install first of Windows 7 on my secondary internal hard drive (partitioned with MBR), then Ubuntu 9.10 on my primary (partitioned with GPT.) update-grub adds the Windows 7 drive to my Grub menu, but when I try to boot it, I get the error "No such device" followed by the device id. I can boot Windows successfully by changing my hard drive boot order from my BIOS, but this is far from a good solution.

When I remove the line "search --no-floppy --fs-uuid --set ba123456-7890-abcd-efghijklmnop" from the grub entry, Grub gives the error "No such partition" instead of "No such device".

Here is the output of the boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks at sector 
    500450712 of the same hard drive for core.img, core.img is at this 
    location on /dev/sda and looks on partition #4 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   488,419,551   488,009,912 HFS+
/dev/sda3     488,681,696   492,874,199     4,192,504 Linux Swap
/dev/sda4     492,874,200   574,789,634    81,915,435 Linux (usually)
/dev/sda5     574,789,635 1,255,431,554   680,641,920 Linux (usually)

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdd442434

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat" 
/dev/sda2: UUID="3d7032de-2490-3477-b7cb-402a45ee2c50" LABEL="OSX" TYPE="hfsplus" 
/dev/sda3: UUID="513d9406-761f-4b1b-bc38-b5567e568ee8" TYPE="swap" 
/dev/sda4: UUID="15c13abd-ed7f-4a14-8ad6-5fb43b6408c6" TYPE="ext4" 
/dev/sda5: LABEL="Linux-Home" UUID="df43be62-3812-483f-8244-1e3b772e368b" TYPE="ext4" 
/dev/sdb1: UUID="D6B6E4B3B6E49571" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/dinkydogg/.Private on /home/dinkydogg type ecryptfs (ecryptfs_sig=0095e796056a27cf,ecryptfs_fnek_sig=b09d253a59c00ef1,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/dinkydogg/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dinkydogg)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 15c13abd-ed7f-4a14-8ad6-5fb43b6408c6
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
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 15c13abd-ed7f-4a14-8ad6-5fb43b6408c6
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=15c13abd-ed7f-4a14-8ad6-5fb43b6408c6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 15c13abd-ed7f-4a14-8ad6-5fb43b6408c6
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=15c13abd-ed7f-4a14-8ad6-5fb43b6408c6 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 15c13abd-ed7f-4a14-8ad6-5fb43b6408c6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=15c13abd-ed7f-4a14-8ad6-5fb43b6408c6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 15c13abd-ed7f-4a14-8ad6-5fb43b6408c6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=15c13abd-ed7f-4a14-8ad6-5fb43b6408c6 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set d6b6e4b3b6e49571
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=15c13abd-ed7f-4a14-8ad6-5fb43b6408c6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=df43be62-3812-483f-8244-1e3b772e368b /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=513d9406-761f-4b1b-bc38-b5567e568ee8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 252.3GB: boot/grub/grub.cfg
 252.3GB: boot/initrd.img-2.6.31-14-generic
 252.3GB: boot/initrd.img-2.6.31-16-generic
 252.3GB: boot/vmlinuz-2.6.31-14-generic
 252.3GB: boot/vmlinuz-2.6.31-16-generic
 252.3GB: initrd.img
 252.3GB: initrd.img.old
 252.3GB: vmlinuz
 252.3GB: vmlinuz.old

```

Anyone have any ideas how to troubleshoot this further?

---

### Post by DinkyDogg on 2009-12-25
I found a temporary fix.

When I entered the command line in grub, I used the command "ls" to list the available partitions. (hd1,1) which is what I thought Windows would be on, didn't show up. There was only (hd1). When I removed the line "search --no-floppy --fs-uuid --set ba123456-7890-abcd-efghijklmnop" from the entry and changed the root to "(hd1)" instead of "(hd1,1)", it booted.

Oddly, if I ran the command "exit", it booted windows too.

I'm guessin this is happening because Windows installed its bootloader to the MBR of the secondary disk. I have to imagine this is a fairly common occurrence - **update-grub should be modified to handle this.**

I'll be looking into a more permanent fix for my own problem in the future.

---

