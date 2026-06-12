---
title: "[SOLVED] Re-Partitioning"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2008-10-16
OK, here's the thing. When I bought my PC it came with a 200G Vista partition, my wife would not let me mess with it at the time as she panics when she spends cash on something. So I installed a second 76G hard disk & I dual boot Vista and Ubuntu 8.04. The second drive is partitioned as 30G for /, 44G for /home and the remaining for swap. What I have now done is reduce the Vista drive to 100G leaving me 100G spare. Can I move my /home partition to this space, and if so how ??

:confused:

---

### Post by dabl on 2008-10-16
Heh heh heh -- dare I ask whether The Mrs. is aware of this little revision?   :lolflag:


Instead of moving /home, why don't you just decide upon the nature of the data that you plan to save there, give the partition an appropriate name, and symlink that to your present /home?

For example, make a mount point in /media named /media/music, edit /etc/fstab appropriately to mount /media/music at boot time, and then make a directory on the new partition named "music" and symlink that to your /home directory, so "music" appears to be a folder in /home.

Or, if there are more than one kinds of data (say "images" and "music"), then mount it as /media/data, make an "images" directory and a "music" directory, and symlink those into your present /home directory, and they will be just as available as if they were physically on the same partition. Seems easier to me that relocating the /home directory, plus then you would need to do something with your empty 44GB partition.  :)

---

### Post by celticbhoy on 2008-10-16
That sounds like an ok idea, will it work if I format to NTFS enabling use by Vista also ?

---

### Post by dabl on 2008-10-17
Yes, your non-Linux partitions can be formatted NTFS, and then the data folders on them can be symlinked in to your /home directory in Linux.  You may need to install the package ntfs-3g if you don't already have it.

Search the forum for details on setting the NTFS formatted partition(s) up in you /etc/fstab file so they are automatically mounted at boot.  :)

---

### Post by celticbhoy on 2008-10-17
worked a treat

---

