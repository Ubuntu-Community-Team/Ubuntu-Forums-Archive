---
title: "Install with RAID.. help!"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by debest on 2007-12-17
Hi, folks.  Getting back into trying out Ubuntu, but otherwise a total noob, so take that into consideration...

My frankenstein PC is an older beast, but should be serviceable (Asus A7V133, 1 GB ram, 1 GHz Athlon).  I have a 12 GB hd as hda, and identical 160 GB drives as hde & hdf (on the mobo's built-in Promise IDE chip).  I am *not* using the "fakeraid", but rather want to set up software RAID in Ubuntu.

My intent is to use the 12GB drive as the boot drive and for swap, and leave the rest of the space to install XP in case I need it.  For the two larger drives, I would like to have RAID1 for a root partition, RAID1 for a home partition, and two standard partitions on the remaining space for both drives for MythTV content.

I used the DVD for Kubuntu Gutsy, and entered the text install option on bootup.  Here is the way I partitioned the drives:

- HDA:
    hda1: 100MB, ext3, "/boot"
    hda2: 2GB, swap

- HDE:
    hde1: 16GB, RAID1, md0
    hde2: 84GB, RAID1, md1
    hde3: remaining, XFS, "/media/hde3"

- HDF:
    hdf1: 16GB, RAID1, md0
    hdf2: 84GB, RAID1, md1
    hdf3: remaining, XFS, "/media/hdf3"

- RAID:
    md0:  ext3, "/"
    md1:  ext3, "/home"

Install went flawlessly, as far as I know (I wasn't in the room for some of it).  Then on reboot, this screen appeared:

> Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/hda1) = hda1(3,1)
kinit: trying to resume from /dev/hda1
kinit: No resume image, doing normal boot...
mount: Mounting /dev/md0 on /root failed: Device or resource busy
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

... and that's it.  So, what did I do wrong???  Thanks!

---

