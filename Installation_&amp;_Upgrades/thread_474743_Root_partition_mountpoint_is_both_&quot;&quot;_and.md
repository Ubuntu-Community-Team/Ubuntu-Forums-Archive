---
title: "Root partition mountpoint is both &quot;/&quot; and &quot;dev/.static/dev&quot;"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2007-06-15
I've been trying to move a working Ubuntu installation from a partition on one drive to a partition on another drive. I'm now running Ubuntu from the new, and faster, partition but there are still some issues. My current and new root partition is both mounted as / and /dev/.static/dev according to GParted and I got this message from the terminal so it seems it's no only GParted that sees it this way:

/dev/.static/dev/mapper/home is active:

The above is supposed to be my home drive but it's rather confusing. Why is my root partiton mounted twice?

---

### Post by soniiic on 2007-09-04
I've just done the same by moving my ubuntu installation from sdb2 to sdb1 and i get the same message in Gparted.

Here's a screenshot: [http://i139.photobucket.com/albums/q297/soniiic/Screenshot--dev-sdb-GParted.png](http://i139.photobucket.com/albums/q297/soniiic/Screenshot--dev-sdb-GParted.png)

just wondering if it can cause errors :S how do i switch it back?

(also is it ok to have the swap partition so far away from the linux partition? how often is the swap accessed?)

EDIT: running 'sudo umount /dev/.static/dev' unmounts it fine but obviously it's then mounted at boot again!

---

### Post by kevinfishburne on 2008-03-12
I have this same issue, apparently resulting somehow from copying partitions either on the same disk or between two disks. So, this is a bump with a screenshot for fun:

[IMG]http://sales.eightvirtues.com/misc/gparted_1.jpg[/IMG]

My fstab is:

```
# proc
proc			/proc		proc		defaults			0	0

# swap partition
/dev/sda1		none		swap		sw				0	0

# root partition
/dev/sda2		/		ext3		defaults,errors=remount-ro	0	1

# data partition
/dev/sda3		/media/Data	reiserfs	defaults			0	0
#/dev/sda3		/media/Data	reiserfs	auto,users,exec			0	0

# CD-ROM
/dev/hda		/media/cdrom0	udf,iso9660	user,noauto,exec		0	0

# download on lycaeum
lycaeum:/media/Download	/media/Download	nfs		rsize=8192,wsize=8192,timeo=14,intr

# video on lycaeum
lycaeum:/media/Video	/media/Video	nfs		rsize=8192,wsize=8192,timeo=14,intr

# audio on lycaeum
lycaeum:/media/Audio	/media/Audio	nfs		rsize=8192,wsize=8192,timeo=14,intr

# backup on lycaeum
lycaeum:/media/Backup	/media/Backup	nfs		rsize=8192,wsize=8192,timeo=14,intr
```

Checking the disk, uninstalling EVMS, and rebooting make no difference. I checked "/dev/.static/dev" and the root partition is not mounted there as gparted suggests. Attempting to unmount /dev/sda2 in gparted gives me the error:

[INDENT]Count not unmount /dev/sda2
umount: /: device is busy
umount: /: device is busy
[/INDENT]

...and afterward it no longer reports sda2 as being mounted in /dev/.static/dev (until I reboot). It may be relevant that the partition sda2 was copied from was mounted as sda1. sda2 was created by booting to a LiveCD, connecting a USB HDD, and copying sda1 on the USB HDD to sda2 on the internal HDD.

Any leads in the right direction are highly appreciated.

---

### Post by theonhighgod on 2008-07-23
I have been able to move my partion, but it seems like this thread is dead, if someone is interested i'll write how :) its not a very elegant method at all so I wouldn't recommend my method.......

---

