---
title: "GRUB loadingRead Error when booting from SATA Drive"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by bakom on 2009-12-06
Hello,

I have installed Ubuntu 9.10 from the Live CD without problems on my SATA Drive. After setting this drive in the first position on the booting sequence I always get "GRUB loadingRead Error" and nothing more happens. I tried to reinstall GRUB from the Live CD -- it worked without problems, but still the error persists.

This is the configuration of my system

/dev/sda -- 500gb Samsung SATA Drive
/dev/sda1 -- Ubuntu Partition
/dev/sda2 -- Windows Partition
/dev/sda3 -- SWAP Space

/dev/sdb -- 120 gb. Maxtor Storage Drive (IDE)
/dev/sdb1 -- one and only partition with stuff on it

Any help and suggestions would be very much appreciated!

Greetings!

---

### Post by darkod on 2009-12-06
Before the change the IDE drive might have been labeled as hd0 and the SATA as hd1. Changing the order in BIOS can sometimes change that although /dev/sda and /dev/sdb will remain same. That can confuse grub where to find the OS.
Try this:
Set the SATA to be first as you want. Boot with the LiveCD and in terminal install grub2 again with:
sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Reboot with the cd out and see if it helps.

---

### Post by presence1960 on 2009-12-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bakom on 2009-12-07
> **darkod said:**
> Before the change the IDE drive might have been labeled as hd0 and the SATA as hd1. Changing the order in BIOS can sometimes change that although /dev/sda and /dev/sdb will remain same. That can confuse grub where to find the OS.
Try this:
Set the SATA to be first as you want. Boot with the LiveCD and in terminal install grub2 again with:
sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Reboot with the cd out and see if it helps.


Thank you for the response. I tried that, but it didn't worked.

---

### Post by bakom on 2009-12-07
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Thanks for your response. Here is the content of the results.txt file...

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00063ee5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   859,573,889   859,573,827  83 Linux
/dev/sda2         859,573,890   957,233,024    97,659,135  83 Linux
/dev/sda3         957,233,025   976,768,064    19,535,040  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8e718e71

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="db872281-087c-416c-bb50-5c42ce364ab9" TYPE="ext4" 
/dev/sda3: UUID="bf6ccec1-c59a-4713-a687-316f62a9224d" TYPE="swap" 
/dev/sdb1: LABEL="/files1" UUID="0bc66404-8342-4256-a4c5-c1ffbac2d4de" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set db872281-087c-416c-bb50-5c42ce364ab9
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set db872281-087c-416c-bb50-5c42ce364ab9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=db872281-087c-416c-bb50-5c42ce364ab9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set db872281-087c-416c-bb50-5c42ce364ab9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=db872281-087c-416c-bb50-5c42ce364ab9 ro single 
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=db872281-087c-416c-bb50-5c42ce364ab9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=bf6ccec1-c59a-4713-a687-316f62a9224d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by presence1960 on 2009-12-07
Everything seems to be ok. I noticed a couple of things, but should not keep you from booting.

You have boot flags on sda1 and sdb1, both are Linux filesystems- they do not need bootflags. From the Live CD use gparted to remove the boot flags from both of those.

You have windows on MBR of sdb- that is no biggie. Was that a disk that formerly had windows on it?

What is sda2 it is an unknown filesystem and is unable to be mounted? see here:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

[COLOR="Red"]sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''[/COLOR]

---

### Post by bakom on 2009-12-08
Hello,

thanks for your response.

I solved the problem by installing grub in /dev/sdb with pointing on /dev/sda1 as Ubuntu Partition. That works. I think its a problem with the SATA drive and his recognition. The bios does not always recognize the sata drive when booting up.

---

