---
title: "Windows 7 Hibernation Corrupts Grub"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by appstateguy on 2009-11-20
Hey guys, I recently installed Ubuntu onto my Windows 7 laptop. Everything worked fine until I booted into Windows to play a game. I hibernated the computer and went to bed. The next morning I go to boot up and GRUB gave me an error (something about an unknown symbol). 

I was able to restore GRUB using the Ubuntu Live CD, but I can not hibernate my computer. This is very frustrating because its a laptop. Plus, if the battery runs very low the computer automatically hibernates. 

I found an older thread that sounded like the person had a similar issue. ([http://ubuntuforums.org/showthread.php?t=1208497](http://ubuntuforums.org/showthread.php?t=1208497)) No one gave a definite solution but one person did suggest a page that looks like it make help: [http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

The "Classic Solution" looked promising but I couldn't find any files which contained "stage1_5" in their names. So I'm not sure where or what to do now, does anyone have any suggestions?

---

### Post by appstateguy on 2009-11-22
Anyone? This is really frustrating! I would love some help :)

---

### Post by lisati on 2009-11-23
Does a search for "stage1" bring anything up?

---

### Post by namok on 2009-11-23
First sorry for my english.
I suggest to install grub into Ubuntu PBR partition(first sector of partition), set boot flag to Ubuntu partition (reset boot flag windows partition) an install syslinux in MBR. This working for Ubuntu on primary partition. But i know nothing about Your system, so download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the desktop, open a terminal (Applications > Accessories > Terminal) and do:```
sudo bash ~/Desktop/boot_info_script*.sh
```Script will create a "RESULTS.txt" file on the your desktop. Please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by appstateguy on 2009-11-23
Here you go namok--also I've discovered shutting the computer down while in windows also can corrupt GRUB. It doesn't happen every time, but it does happen at least half the time.

Here are the contents of results.txt:
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       160,649       160,587   6 FAT16
/dev/sda2             161,792    31,619,071    31,457,280   7 HPFS/NTFS
/dev/sda3          31,619,072   914,259,149   882,640,078   7 HPFS/NTFS
/dev/sda4         914,259,150   976,768,064    62,508,915   5 Extended
/dev/sda5         914,259,213   975,354,344    61,095,132  83 Linux
/dev/sda6         975,354,408   976,768,064     1,413,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0918" TYPE="vfat" 
/dev/sda2: UUID="7284A8FA84A8C249" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="4CC4AC91C4AC7F38" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="a7445ae2-c593-4447-aca8-c4c785927530" TYPE="ext4" 
/dev/sda6: UUID="e902bfde-512e-4e23-bc4c-e1f220e5c611" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/andrew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrew)


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
search --no-floppy --fs-uuid --set a7445ae2-c593-4447-aca8-c4c785927530
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
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set a7445ae2-c593-4447-aca8-c4c785927530
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=a7445ae2-c593-4447-aca8-c4c785927530 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set a7445ae2-c593-4447-aca8-c4c785927530
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=a7445ae2-c593-4447-aca8-c4c785927530 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set a7445ae2-c593-4447-aca8-c4c785927530
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a7445ae2-c593-4447-aca8-c4c785927530 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set a7445ae2-c593-4447-aca8-c4c785927530
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a7445ae2-c593-4447-aca8-c4c785927530 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 4cc4ac91c4ac7f38
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
UUID=a7445ae2-c593-4447-aca8-c4c785927530 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e902bfde-512e-4e23-bc4c-e1f220e5c611 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 468.1GB: boot/grub/grub.cfg
 468.1GB: boot/initrd.img-2.6.31-14-generic
 468.1GB: boot/initrd.img-2.6.31-14-generic-pae
 468.1GB: boot/vmlinuz-2.6.31-14-generic
 468.1GB: boot/vmlinuz-2.6.31-14-generic-pae
 468.1GB: initrd.img
 468.1GB: vmlinuz
```

---

### Post by namok on 2009-11-23
As I mentioned before, my solution works when Ubuntu is installed on the primary partition. In your Ubuntu is installed on an extended partition(sda5). Therefore, [you should go back to the grub legacy]("http://ubuntuforums.org/showpost.php?p=8071880&postcount=18"), and then use the method you provided earlier [http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub).

---

