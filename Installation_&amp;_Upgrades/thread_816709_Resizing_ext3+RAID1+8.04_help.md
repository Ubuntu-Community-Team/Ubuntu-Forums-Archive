---
title: "Resizing ext3+RAID1+8.04 help"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by armitage1337 on 2008-06-02
Hi,

So the way I have my partitions set up right now, I've got one 250GB hard drive with Windows on it, and one 500GB hard drive with Linux on it, with a 148GB / (root) partition and the 309GB /home partition. I'm getting another 500GB hard drive in the  mail in the next day or two. My plan is to move root to a partition on the 250GB hard drive, and then use the entire 500GB hard drive for the /home partition. However, I also want to RAID1 the two 500GB hard drives - the one that I've been using, and the one I'm about to get. Thus, I want to preserve the data on the /home partition on the hard drive I've had. Additionally, I'm running Gutsy Gibbon right now, and I would like to upgrade to Hardy Heron during the process. What would be the best way to do so?

A few of the specific questions that I have are:
1) Can I expand the /home partition to take up the entire 500GB hard drive without losing data?
2) Can I set up RAID during the Ubuntu install while preserving the data on one of the partitions that I want to RAID? That is, immediately mirror all the data from one hard drive onto the other and use those two in RAID1. Or do I need to do this beforehand using Knoppix or some other live distro?
3) Can I have RAID for the /home partition while not having RAID for the root partition?

Thanks in advance for the help!!!

---

### Post by tgrimley on 2008-06-03
1) Yes, I believe so.  I know you can resize ext3 partitions as I've done it when I expanded my RAID5 volume.
2) I don't know if you can set it up during install.  Probably, but I think you'd lose data.  You likely want to install /home to the root partition under the installer and then change it later to the RAID volume.
3). Yes, as far as I know.

Safest thing to do is to back up your data, and wipe all the disks during the installer and set up RAID1 if it lets you (or set it up in knoppix and let the installer find it).

Here is a guide: [http://www.rot13.org/~dpavlin/md-raid1.html](http://www.rot13.org/~dpavlin/md-raid1.html) on something similar, maybe you can use this technique to make your /home drive the first disk, and then mirror to the new disk.  Obviously you'd not want to format like it instructs.

If you're using md you can try that technique out with disk images I believe to see if it works properly.. but still backing up is the best strategy.

---

