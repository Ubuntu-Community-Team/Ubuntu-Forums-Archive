---
title: "Grub wont boot windows"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by gunner_uk2000 on 2009-12-13
Windows XP appears on the boot menu, however when you attempt to boot it. it will just say Grub with a flashing _ and do nothing. ie it doesn't seem to get to booting windows.

Any ideas?

---

### Post by darkod on 2009-12-13
Download the boot script from my signature, move it on the desktop for example and execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

That will create results.txt file. Copy the content of that file here and please put CODE tags around it (with the text selected hit the # button in the toolbar above) to make it easier to read. It will detail you whole boot process.

---

### Post by gunner_uk2000 on 2009-12-13
Right here is the file. One thing I've noticed is the line that says "    Boot sector type:  Windows Vista". Which is wrong as it's windows xp that is installed.

```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks for 
    (UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 391617063 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
16 heads, 63 sectors/track, 486344 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7512f0b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,016   379,167,263   379,165,248   7 HPFS/NTFS
/dev/sda2         379,167,264   490,233,743   111,066,480   5 Extended
/dev/sda5         379,167,327   385,026,767     5,859,441  82 Linux swap / Solaris
/dev/sda6         385,026,831   490,233,743   105,206,913  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa53da53d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,344,579   156,344,517   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DEDA75EADA75BEF9" TYPE="ntfs" 
/dev/sda5: UUID="f63e67af-eb87-47f4-b83f-b98a7f0f4b16" TYPE="swap" 
/dev/sda6: UUID="31f25ff2-def5-48bb-87fe-7f496d8e4573" TYPE="ext4" 
/dev/sdb1: UUID="0054D5FD54D5F4FE" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/ian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ian)


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
search --no-floppy --fs-uuid --set 31f25ff2-def5-48bb-87fe-7f496d8e4573
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
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 31f25ff2-def5-48bb-87fe-7f496d8e4573
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 31f25ff2-def5-48bb-87fe-7f496d8e4573
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 31f25ff2-def5-48bb-87fe-7f496d8e4573
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 31f25ff2-def5-48bb-87fe-7f496d8e4573
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 31f25ff2-def5-48bb-87fe-7f496d8e4573
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 31f25ff2-def5-48bb-87fe-7f496d8e4573
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 0054d5fd54d5f4fe
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
UUID=31f25ff2-def5-48bb-87fe-7f496d8e4573 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f63e67af-eb87-47f4-b83f-b98a7f0f4b16 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 197.1GB: boot/grub/grub.cfg
 197.1GB: boot/initrd.img-2.6.31-14-generic
 197.1GB: boot/initrd.img-2.6.31-15-generic
 197.1GB: boot/initrd.img-2.6.31-16-generic
 197.1GB: boot/vmlinuz-2.6.31-14-generic
 197.1GB: boot/vmlinuz-2.6.31-15-generic
 197.1GB: boot/vmlinuz-2.6.31-16-generic
 197.1GB: initrd.img
 197.1GB: initrd.img.old
 197.1GB: vmlinuz
 197.1GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

thanks for any help :-)

---

### Post by darkod on 2009-12-13
sdb1: _________________________________________________________________________

    File system:       ntfs
    [COLOR=Red]Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 391617063 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
[COLOR=Black]
First of all, grub2 shouldn't be installed on a partition at all, usually on a MBR of the disk. Second, this is your XP partition. That's why selecting XP in the menu shows Grub and cursor.

You could try: Set /dev/sdb (the 80GB disk) as first in BIOS boot order. Get your XP cd and repair the bootloader. Instructions to repair different bootloaders here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Then with /dev/sdb still first in boot order check if it will boot XP straight away when you turn on the computer. It should.
If that works, go again in BIOS and return the 250GB disk as first in boot order. This time grub2 menu should show up. Try the XP entry, it might work or not. If it doesn't, boot into ubuntu and execute in terminal:
sudo update-grub

Reboot and check now.
[/COLOR][/COLOR]

---

