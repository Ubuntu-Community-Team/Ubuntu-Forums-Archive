---
title: "Format Harddrive with GRUB installed"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by rypicken on 2011-01-17
Upon installation of Ubuntu a while back, i was using a windows xp machine with two different harddrives. Instead of formatting the xp drive and installing Linux, i decided to install Linux on the secondary harddrive. This worked all fine and dandy until recent, when I have found my linux drive filling up near capacity. I would like to format the XP harddrive and mount it in linux to give some more disk space. The problem i have found, is that the XP drive is the drive with GRUB. Any advice on how this could be done without TOO much troubles.

Thanks in advance.

---

### Post by dabl on 2011-01-17
I'll take a stab at it ... I'll stay high level, and see if you need more details.

First, review the guidance on installing/reinstalling Grub.  It's not that difficult -- here's what a guy wrote on  Kubuntu Forums -- just scroll to Section 4:  [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

So, use GParted, highlight the partition on the XP drive, right-click it and change the filesystem to ext4, and "Apply".

Make a mount point, recommended location for hard drive partitions is /mnt.

Example:  ```
sudo mkdir -p /mnt/NEWSTUFF
```

Next, you'll need to edit /etc/fstab to change whatever the mount line for XP says.  Use "mount by-uuid", and you can find the UUID for the new filesystem with the "blkid" command.  Use "mount -a" to mount it, and "mount" to verify that it mounts correctly.

Finally, use the guidance to install grub wherever you want it.

---

### Post by oldfred on 2011-01-17
Which drive you use to boot is a separate question from using/formating a drive. You can entirely format your windows drive and grub will not change since the MBR is separate from the partitions. But I always recommend that you boot from the same drive as the system install. After reinstalling grub to sdb, change BIOS to boot that drive.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
To see what drive is uses:
sudo debconf-show grub-pc

---

### Post by rypicken on 2011-01-17
Thank you all!

---

