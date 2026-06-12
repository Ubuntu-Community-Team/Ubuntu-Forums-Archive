---
title: "Partitioning without formatting?"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by Blackylol on 2011-05-27
Im trying to install ubuntu with windows xp, but I only have 1 disk

People at irc told me i Could make a new partition in this same disk without having to format the whole drive.. and this option should appear at the setup, but i dont have that option, it only show the option to format the drive or "do something else", And here i cant see anything that let me use the free space i have in the windows partition to make a new one...

my ntfs partition has at least 35gb contiguous free space of 200gb free  so i thought  i could use this to make a new partition, but idk how, can anyone guide me please?

Thanks

---

### Post by 67GTA on 2011-05-27
You have to choose the advanced or manual option. This will let you use the partitioning tool to shrink the existing partition and create a new one in the resulting free space on the drive. I would strongly advise you to back up everything important before doing this.

---

### Post by oldfred on 2011-05-27
IF your NTFS partition is 200GB and only has 35GB free, you do not have enough room. Windows likes 30% free, starts to slow down with 20% free and just about stops at 10%. With 200GB you need at least 40GB free for windows to work reasonably well.

How many partitions have you used? MBR/msdos only allow 4 primary partitions one of which can be an extended partition with many logical partitions. Ubuntu will work just fine from logicals.

---

### Post by Blackylol on 2011-05-27
no, my disk is 1 partition of  500gb (470gb real), and i have 200gb free i wanted to use at least 40 gb for ubuntu, but idk how to make a new partition without formatting...

I found the tool gparted but it doesnt let me resize it as is supposed to work... 

I dismount the disk, go to resize and then it doesnt let me move the bar or write the number i want because it goes back to 0.

I did full defrag in windows using perfectdisk to create free contiguous space for 2 days nonstop, then i ran chkdsk /f /r and today i cant create the new partition.

---

### Post by oldfred on 2011-05-27
How many partitions have you used.

Post this and/or a screenshot from gparted.

```
sudo fdisk -lu
```

---

