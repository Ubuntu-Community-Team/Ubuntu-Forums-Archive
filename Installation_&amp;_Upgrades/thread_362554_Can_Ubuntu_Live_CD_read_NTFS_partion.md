---
title: "Can Ubuntu Live CD read NTFS partion?"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-02-15
Can ubuntu read NTFS partition of Windows 2000?

---

### Post by rsambuca on 2007-02-15
Yes, but it will not write to NTFS.

---

### Post by EngDrewman on 2007-02-15
yes it can read NTFS, but it does not automatically mount the partition. To mount the partition do the following:

1. locate the disk in the devices folder (should be somewhere under /dev)
2. open the terminal and use the mount command to mount the partition. The syntax for the mount command is as follows: "sudo mount [device path in /dev folder] [destination]"

For example, lets say that your disk is /dev/hda1, and you want to mount it to the /media folder, you would type "sudo mount /dev/hda1 /media/hda1"

---

