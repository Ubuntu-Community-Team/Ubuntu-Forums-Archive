---
title: "post 2.6.31-17; grub.cfg fails to process"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by sfryer on 2010-01-08
This morning I updated my system as prompted by the update manager. Upon reboot, I got "grub:sh>". After doing some googling and a bit of trial and error, I managed to figure out that I can manually boot successfully by executing the following commands.

```

grub:sh> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
grub:sh> initrd /boot/initrd.img-2.6.31-14-generic
grub:sh> boot

```

What I've been thus far unable to determine, is how to restore my system to a state which will allow it to boot without having to enter the above each and every time. Unfortunately a simple `sudo update-grub2` did not solve my problem. Following is detailed info concerning my system configuration as obtained via a [very helpful script]("http://sourceforge.net/projects/bootinfoscript/").

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd65316e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   173,694,779   173,694,717   7 HPFS/NTFS
/dev/sda2         173,694,780   302,230,844   128,536,065   7 HPFS/NTFS
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="708411CB841194A6" TYPE="ntfs" 
sda1/Wubi: UUID="a7389c7d-0196-42be-802e-b9af84d83249" TYPE="ext4" 
sda2: UUID="A000B2F200B2CF12" LABEL="audio-video" TYPE="ntfs" 
sda3: LABEL="PE" UUID="CCED-990E" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/loop0 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /host type fuseblk (rw)
/dev/sda2 on /media/audio-video type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sfryer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sfryer)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=5

default=C:\wubildr.mbr

[operating systems]

C:\wubildr.mbr = "Ubuntu Netbook Remix"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 708411cb841194a6
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 708411cb841194a6
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 708411cb841194a6
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 708411cb841194a6
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 708411cb841194a6
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 708411cb841194a6
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 708411cb841194a6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda3)" {
	insmod fat
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
UUID=A000B2F200B2CF12 /media/audio-video ntfs-3g defaults 0 0

================= sda1/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

Anyhow, if anyone can help me get my system to boot ubuntu automatically, that'd be very much appreciated. :D

---

### Post by mlsquad on 2010-01-11
I'm in the exact same boat as you.  I'm running Ubuntu Karmic 9.10 via Wubi, and after the update pushed out the 2.6.31-17-generic kernel I have to type in the exact same commands to boot up.
Karmic via Wubi has turned out to be rather unpleasant. :(

---

### Post by meierfra. on 2010-01-11
You have been hit by a bug in Grub2 ntfs module. Luckily  the author of Wubi has released an easy  fix. Boot into Windows and  follow these instruction:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by Dale61 on 2010-01-12
I had the same problem booting up a few weeks ago, and used the same 'code' to get mine up and running (I used kernel 2.6.31-16-generic), then sudo update-grub2, and haven't had a problem since.

---

### Post by meierfra. on 2010-01-12
> Then sudo update-grub2, and haven't had a problem since.
You got lucky and probably will be hit by the bug again in the future.
Your current Grub 2 is only able to read the first 4GB of your Windows partition. During the kernel update the file  "grub.cfg" was moved outside these limits.  Running "update-grub2" generated a new "grub.cfg" and just by chance, it ended up in the 4GB limit.   
If  you follow the instruction from the link in my previous post and replace your "wubildr", Grub2 will be able to see your whole Windows partition.

---

### Post by gstanden on 2010-02-06
The wubildr patch worked great - thank you!

---

### Post by sfryer on 2010-02-07
> **meierfra. said:**
> You have been hit by a bug in Grub2 ntfs module. Luckily  the author of Wubi has released an easy  fix. Boot into Windows and  follow these instruction:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

This worked great! I just had the problem reoccur with the -19 kernel update, and this fixed it! I hope it's officially incorporated into wubi soon.

---

### Post by fiklein on 2010-03-02
There is a wubildr patch, but I would suggest you back up the original wubildr version before using the patch. I had a similar problem with WUBI on a different computer and just did a native linux install. On another computer that was working with Jaunty 9.04 with the previous "defective" wubildr, I installed the patch before trying to upgrade to Karmic 9.10. The patch made Ubuntu unbootable, so I reverted to the previous wubildr and was up and going again.

---

