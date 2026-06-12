---
title: "Partitioning Problem"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by dh04000 on 2010-01-15
Heres my problem, when I got my new 160 GB harddrive, I used jaunty to partition it into a three main partitions.

/dev/sda1   ~50 GB NTFS (windows xp)
/dev/sda4   ~50 GB EXT3 (jaunty)
/dev/sda3   ~2 GB Extended Partition
/dev/sda5   ~2 GB Linux Swap

------The extended and linux swap are the same thing of coarse -----

/dev/sda2    ~50 GB FAT32 (OS Exchange)


Now I want to increase he size of my ntfs filesystem without formating it.
I think its called "extending". I decreased the EXT3 to 30GB and the fat32 to 30 GB. Now i want to add the unallocated space (both new spaces) to my ntfs partition.

The tools I have are gparted on jaunty, a magic partition disk live GB(4.8), and easeus partitionor(like gparted but on windows, has less options).

I also have a 4 GB usb drive as well as a netbook loaded with jaunty and gparted.


How can I make this work?

---

### Post by dh04000 on 2010-01-15
You guys are my go-to-people.

I know someone here will be able to solve this problem for me. 

The ubuntu forums rock!

---

### Post by x33a on 2010-01-15
Firstly the fat32 freed space cannot be allocated to the ntfs one, as there are other partitions in between.

as for the ext3 partition, you'll have to resize it like this:

1. boot from a live cd containing gparted. (this is required since you are resizing the root partition.)
2. open gparted.
3. unmount the ext3 partition (if mounted).
4. Drag the slider from left to right, so as to add free space before the partition. the free space should be added to the free space preceeding option.

Then you can resize the ntfs partition to include the freed up space.

note: since you are resizing the root partition, you might experience some problems, so backup your important data beforehand.

---

### Post by dh04000 on 2010-01-15
Ahhhh.... I had to click and drag in order to move the partition.

I did it, works fine, Windows XP even recognized the filesystem size change.

Sucks that I can't use that extra space I don't need from the fat32 filesystem. I'll eventually blank and reinstall both windows and linux,so I won't make the same mistake next time.


Thank you,
I knew I could depend on the Ubuntu forums! :)

---

