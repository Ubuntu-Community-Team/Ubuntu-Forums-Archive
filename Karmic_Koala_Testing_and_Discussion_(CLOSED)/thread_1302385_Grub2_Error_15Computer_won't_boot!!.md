---
title: "Grub2 Error 15/Computer won't boot!!"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2009-10-27
Hi guys,

Well I just tried to upgrade to grub2 and I missed the thing where you have to press spacebar to choose /dev/sda to install it on, I just pressed OK. I thought because /dev/sda was highlighted it was already selected. Pretty stupid if you ask me.

Anyway, I rebooted to find a lovely Error 15 message. I've looked around the net at other threads with people having this problem but I can't seem to fix it with the liveCD. Firstly, my chroot command is this:

```

sudo chroot "/media/50f680be-9892-4f8b-a659-e03265301b9e"

```

Because that's where my /dev/sda drive is mounted... I can't mount it to a /mnt point for some reason.

Anyway, I run the commands to remove grub-pc, install grub to sda and then update grub... but I get a tonne of permission errors and things along the way.

I ran a script I found in another thread that generates a results txt file to help diagnose the problem. Here it is:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac578e16

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   304,688,789   304,688,727  83 Linux
/dev/sda2         304,688,790   312,576,704     7,887,915   5 Extended
/dev/sda5         304,688,853   312,576,704     7,887,852  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac578e17

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 2021 MB, 2021654528 bytes
201 heads, 19 sectors/track, 1033 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000555f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *              1     3,948,543     3,948,543   c W95 FAT32 (LBA)

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="1a1f13c2-f0af-40cd-89a8-39ae6fb5f416" TYPE="ext3" 
/dev/sda1: UUID="50f680be-9892-4f8b-a659-e03265301b9e" TYPE="ext4" 
/dev/sda5: UUID="c2007176-af3e-454f-874d-c2fe7201cd75" TYPE="swap" 
/dev/sdb1: LABEL="Media Disk" UUID="440d6604-ea4d-4fd1-8983-b3fe1d4726ef" TYPE="ext4" 
/dev/sdc1: UUID="9DC5-31FB" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /sys/kernel/debug type debugfs (rw)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/50f680be-9892-4f8b-a659-e03265301b9e type ext4 (rw,nosuid,nodev,uhelper=devkit)

=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST


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
search --no-floppy --fs-uuid --set 50f680be-9892-4f8b-a659-e03265301b9e
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
  set timeout=3
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
	search --no-floppy --fs-uuid --set 50f680be-9892-4f8b-a659-e03265301b9e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=50f680be-9892-4f8b-a659-e03265301b9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 50f680be-9892-4f8b-a659-e03265301b9e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=50f680be-9892-4f8b-a659-e03265301b9e ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 50f680be-9892-4f8b-a659-e03265301b9e
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=50f680be-9892-4f8b-a659-e03265301b9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 50f680be-9892-4f8b-a659-e03265301b9e
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=50f680be-9892-4f8b-a659-e03265301b9e ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=50f680be-9892-4f8b-a659-e03265301b9e /               ext4    relatime,errors=remount-ro 0       0
# swap was on /dev/sda5 during installation
UUID=c2007176-af3e-454f-874d-c2fe7201cd75 none            swap    sw              0       0

UUID=440d6604-ea4d-4fd1-8983-b3fe1d4726ef /mnt/media    ext4    defaults,errors=remount-ro  0  2


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```

So.... help me!

---

### Post by kansasnoob on 2009-10-27
I've found having combined grub and grub 2 files in /boot/grub can cause conflicts.

Anyway it looks to me like Karmic is on sda1 so I'd boot the Live CD and run these commands:

```
sudo mount /dev/sda1 /mnt
```
```
sudo mount --bind /dev /mnt/dev
```
```
sudo mount --bind /proc /mnt/proc
```
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``` 
```
sudo chroot /mnt
```

(It may be a good idea to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition.)

Then run through steps one through three here:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

(No sudo needed because as "chroot" you are already root.)

When you're done be sure to:
```
exit
```
```
sudo umount /mnt/dev
```
```
sudo umount /mnt/proc
```
```
sudo umount /mnt
```

---

### Post by humphreybc on 2009-10-27
Thanks for the reply, but i've given up and reinstalled Karmic RC. I suppose the benefit of this is that I get a fresh install and an encrypted home directory :)

Not taking me too long to set everything back to how I had it before...

---

