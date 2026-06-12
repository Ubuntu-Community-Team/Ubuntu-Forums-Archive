---
title: "Change of partition name"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by momist on 2012-04-29
Hi everyone.

I have a clean install of 12.04 with home and data on separate partitions.  I also use a separate partition for my images, both scanned and photographs etc.  Unfortunately, when I set up my new system I made a typo when I named that partition, and didn't notice until after everything else was working.

I can access the data on there under the new name, as it mounts fine.  However, I now have a lot of broken symlinks due to the change in partition name.  Is there a way to change the name of the partition to make those links work again?  Or would changing the partition name (maybe using gparted or similar) cause different damage to my new system.  

I really don't want to have to re-install again.

Thanks fo any help.

---

### Post by oldfred on 2012-04-30
Was the name a label which is easily changed with Disk Utility or gparted or the mount point and is the name in fstab.

If in fstab, you need to create a new mount point, unmount the old,  and edit fstab with new name.

Always after editing fstab run this to make sure it is ok.

sudo mount -a

If no errors it just remounts everything. Otherwise you need to fix before attempting to reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

### Post by momist on 2012-05-01
> **oldfred said:**
> Was the name a label which is easily changed with Disk Utility or gparted or the mount point and is the name in fstab.


# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

Thanks for the help OldFred.  

It took me a while, but I got there in the end.  

The LABEL in blkid was correct, but the entries in fstab had an & in it.  This at first meant that I couldn't unmount the partition, but eventually I twigged what was wrong and managed to do so by putting the erroneous name in quote marks.

The next problem was that all the partitions are mounted on root, not in /media.  Once I sorted that out it has worked correctly, and I'm now very happy! :lolflag:

Thanks for the guidance.

---

