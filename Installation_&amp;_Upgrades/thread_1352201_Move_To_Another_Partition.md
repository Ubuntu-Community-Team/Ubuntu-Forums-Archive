---
title: "Move To Another Partition"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by rykel on 2009-12-11
Hi,

I have Ubuntu Karmic fully working on Partition 2 (reiserfs).

I would like to copy the whole installation to Partition 1 (ext4), which is also on the same hard disk.

Then, I will format Partition 2 into ext4 and move the copy back.

How should I do it?

Thanks!

---

### Post by lemming465 on 2009-12-12
One good way would be using *tar*, *star*, or *cpio* from a live CD which can read reiserfs.  Afterwards, you'd need to fix up the /etc/fstab and bootloader.  *chroot* helps with this.

It would be helpful to know things like if you have done this before, how comfortable you are at the command line, which boot loader you are using, whether or not there are exotic things like Samba ACL's or SeLinux involved which imply doing the copy using *star* to pay attention to extended file attributes, etc.

---

### Post by rykel on 2009-12-15
> **lemming465 said:**
> One good way would be using *tar*, *star*, or *cpio* from a live CD which can read reiserfs.  Afterwards, you'd need to fix up the /etc/fstab and bootloader.  *chroot* helps with this.

It would be helpful to know things like if you have done this before, how comfortable you are at the command line, which boot loader you are using, whether or not there are exotic things like Samba ACL's or SeLinux involved which imply doing the copy using *star* to pay attention to extended file attributes, etc.

Hi,

To answer all the questions:

[LIST=1]
[*]No, I have NEVER done this before.
[*]I am very comfortable at the commandline.
[*]I am using grub2 (Karmic default).
[*]There are NO exotic stuff like the ones you mentioned.
[/LIST]
I tried "cp -ax /* destination" but I got a LOT of "permission not copied over" errors.

---

### Post by lemming465 on 2009-12-17
Suppose you are running from a live CD.  To copy files from sda2 to sda1, you could do something like```
sudo -i
mkdir /media/{p1,p2}
mount /dev/sda1 /media/p1
mount /dev/sda2 /media/p2
cd /media/p2
tar cf - . | (cd /media/p1 && tar -xf -)
```
Permissions should be set correctly, but you might get messages about unknown users or groups, which you can ignore.  (The live CD doesn't have the same passwd and group files as the hard drive OS.)  If there are no other mounted filesystems, then this copies enough stuff.  

Otherwise you need a strategy for dealing with the other filesystems, e.g. planning to mount them on sda1 the same way as on sda2, or pre-mounting them on /media/p2/wherever by hand and then absorbing them into a consolidate /media/p2 copy, or something.

Now you need to do some fixup on /media/p1 before it will be bootable,.  This will be easiest from a chroot environment:```
cd /media/p1
for f in sys proc dev; do mount -o bind /$f $f; done
chroot .
```
One problem is that /etc/fstab (mounted in /media/p1) points the root filesystem at the wrong place.  Typically ubuntu will be mounting filesystems by block id. You can do it that way, which is highly necessary for USB devices.  Or you can revert to the older more static way. I'd suggest opening two terminal windows.  In one edit /etc/fstab with nano, vi, emacs, gedit, or whatever your favorite editor on the live CD is.  Find the line that looks something like:> 
UUID=adcaa1b1-e7ff-4394-96e1-99f2d94899ff /               resierfs    errors=remount-ro 0       1
Note that your UUID will be different.  If you are continuing with UUID's, run **sudo blkid** in your second window, and cut & paste the sda1 value in place of the sda2 value.  Also change the file system type from reiserfs to ext4.  Or just specify the partition directly.  One possible result is:> /dev/sda1  /  ext4  errors=remount-ro 0 1
You also have to fix the boot menu and lay down a secondary boot loader.  Running **grub-update** should suffice for that.  Verify that the resulting /boot/grub/grub.cfg specifies (hd0,1) aka Linux sda1 as the root partition and that the kernel line specifies the correct root filesystem by partition or by UUID.  There should be boot entries for both sda1 and sda2, I'm thinking.

Do a test reboot onto the hard drive and see if the right root (sda1, ext4) is booted and mounted, and that you have all your users and data files.  If so, you are half done.  After reformatting sda2 (sudo mkfs -t ext4 /dev/sda2) you can boot back into a live CD and repeat the clone & adapt scenario we just outlined.

If you aren't doing it from a live CD, you have to be a bit more careful about subdirectories of the root directory and not copying mounted special non-disk filesystems, but it can still be done.

Note that the *tar -cf - .... | (... tar -xf -)* trick can be done between two different computers over a network link if you pipe the data through something like netcat ("nc") on each end.

---

### Post by webscorp on 2009-12-17
Omg.

---

