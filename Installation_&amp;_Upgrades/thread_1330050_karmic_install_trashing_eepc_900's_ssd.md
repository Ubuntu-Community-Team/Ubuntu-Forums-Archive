---
title: "karmic install trashing eepc 900's ssd"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by fasterthanawatch on 2009-11-18
Ok, I'm working to install karmic on my eeepc 900.

First I installed it directly, making an ext4 partition, nuking my crunchee 8.10 install.  It would not boot with grub 2.

I monkeyed around in grub until I got something to try and boot, and ended up saying a disk error or some such.

I thought it was a grub error, so I installed grub 1 using a livecd.  Got it installed, booted up once under grub 1, after that the disk became unreadable.  eventually fdisk -l wouldn't show it.

Fixed it with a 

dd if=/dev/zeros of=/dev/sda bs=1M

and then repartitioned.

Then I installed jaunty just fine on an ext4 partition.  dist-upgraded to karmic, one boot up fine, next boot up, disk trashed.  Had to dd again

Installed jaunty on an ext2 partition, dist-upgraded to karmic.  First boot up, 1 error but got in just fine.  Next boot up, disk trashed

The obvious question would be "is my ssd hardware bad?"  and I think the answer is no, because it works just fine in jaunty for as long as I need.

Anyone out there have any idea what to try next?

Another thread that says it is "solved" however, they just gave up and reinstalled jaunty [http://ubuntuforums.org/showthread.php?t=1318992](http://ubuntuforums.org/showthread.php?t=1318992)

Another thread  [http://ubuntuforums.org/showthread.php?t=1318338](http://ubuntuforums.org/showthread.php?t=1318338)

They link to this bug  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387272](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387272)

---

### Post by fasterthanawatch on 2009-11-18
One more thing, I can consistently get this sort of error when trying to fsck the main partition from a live cd

fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

I've searched for that, and it says that it could possibly be a corrupted superblock.
Not sure where to go from here.

---

