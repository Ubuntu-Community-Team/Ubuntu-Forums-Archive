---
title: "Upgrade to software raid1 + xfs hangs during boot"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by dodtsair on 2008-08-16
I have a linux box with 2 200GB sata drives.  I want to set up software raid1 since I do not think I will use over 200GB.  I also was reading about the xfs filesystem and decided I wanted to give it a go.  I can get things working if I make the root fs ext3, but not xfs.  Ultimately if I fail with xfs I am okay falling back and just doing a manilla ext3 install.

The installer won't install raid onto xfs, it crashes.  So I decided to install onto a sda only xfs and upgrade the system to raid.  I am using the following guide
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)


The pieces are going to look like this:

sda1 512 MB reserved for raid
sda2 8 GB reserved for raid
sda3 ~ GB reserved for raid

sdb1 512 MB reserved for raid
sda2 8 GB reserved for raid
sda3 ~ GB reserved for raid

The plan is to mirror each sda# with its corresponding sdb# producing:

md0 512 MB ext3 /boot
md1 8 GB swap
md2 ~GB xfs /

Now the guide says to modify sda, but I do not like those modifications it looks like if md# fails then my modifications to sda will make it unbootable.  I have a working system on sda I would rather keep it until I have a working md system.  So I follow the guide up and until the point where it tells me to modify sda.

Instead I mount:
/dev/md2 /mnt/md2
/dev/md0 /mnt/md2/boot

cp -dpRx / /mnt/md2
cp -dpRx /boot /mnt/md2/boot
cp -aR /dev/* /mnt/md2/dev

Once there I chroot into /mnt/md2
Then I follow the guide when it tells me to modify /etc/mtab, /boot/grub/menu.lst, and /etc/fstab.  Except since I chroot into md2 I am modifying sdb's versions.

This might be where I get into trouble, but it seems to work.
Once I have the configuration files modified.
I run 
dpkg-reconfigure mdadm 
inside the chroot.
Next I install grub onto sdb using
grub-install /dev/sdb
I get an interesting warning that seems to amount to nothing:
Searching for GRUB installation directory ... found: /boot/grub
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb

After all this I reboot the system and I tell the bios to boot of the second SCSI this time.  Which boots off sdb.  
Now I get grub, and I get grub's menu and I select the kernel.  
The kernel boots, I get to the Ubuntu splash screen and progress bar and the progress bar just sits there spinning.  

at this point I can't ctrl-alt-f# into another console because the console does not seem to be initialized.  At this point I am unsure where in the boot process I am failing.  It might be that it can not find the root partition.

Any ideas?

---

