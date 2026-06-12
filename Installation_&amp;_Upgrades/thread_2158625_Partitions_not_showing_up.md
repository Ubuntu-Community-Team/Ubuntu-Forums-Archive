---
title: "Partitions not showing up"
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by dr1094 on 2013-06-29
background info:
I had ubuntu and winxp 64bit working side by side.
I have 2 hard drives. i.e. Sda and Sdb
Sda was divided in to at least three partitions where one was for ubuntu, one for windows, and one for storage.
Everything was working nicely, i.e. HDD's being detected in both systems as they should
I decided to install winxp 32 bit.

1. Had to reset grub
2. Unity 3d wouldn't load, had to blacklist floppy

Now I do not see any of the partitions from ubuntu. The partitions do have data on them, and I do see them from windows. I wanted to open disk utility to perhaps mount them manually as root, but no luck since disk utility doesn't open at all. Any help would be much appreciated Otherwise I may have to reinstall ubuntu, and I'm not sure that will solve the issue. Also, in GParted, Sda shows up as unallocated space of full drive size as oppose to several partitions.

---

### Post by Bashing-om on 2013-06-29
dr1094; Hi !

Don't know ...we look and see ...recon the partition's UUIDs are all messed up ?

from a liveDVD (USB) -> try ubuntu -> ctl+alt+t @ desktop yields a terminal:
what results:
```
sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print
sudo blkid
ls /dev/disk/by-uuid -alh
ls -l /dev/disk/by-uuid/
##and last but not least:
sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test
cat /mnt/test/etc/fstab
mount ##just to see what haps
sudo umount /mnt/test ##do not forget this one, no need to add to the problem!
##
```insure that all agree - one with the other and the /etc/fstab - File System TABle - also sees same same ??

[INDENT][INDENT]it's a thought[/INDENT][/INDENT]

---

### Post by dr1094 on 2013-06-30
I ended up doing a fresh install of ubuntu, since none of the data was on that partition except the OS. Sorry, I couldn't wait. Now I'm not sure if I should mark this thread as solved or not.

---

### Post by Bashing-om on 2013-06-30
dr1094; Hey ...

All's well that ends well...(re-)installing is a sure solution ! Resorted to that a few times myself.

So, yeah; 
Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT]ubuntu, there is always a way[/INDENT][/INDENT]

---

