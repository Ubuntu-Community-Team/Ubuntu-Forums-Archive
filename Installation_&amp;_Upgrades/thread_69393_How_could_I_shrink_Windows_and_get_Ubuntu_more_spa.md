---
title: "How could I shrink Windows and get Ubuntu more space?"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by ppl on 2005-09-26
It is on a dual boot system.I have two disks, one for XP, it is NTFS and I would like windows keep it for a while, another disk I get three FAT32&#65292;Ubuntu lies at the end of the partition.

What I want to do is shrink the three FAT32's(there is no operation system beside Ubuntu on this disk, but has some data I want to keep,) so it will altogether give another 10-20G to Ubuntu root. Could I do that saftly and without too much works, of couse the safty is on high priority.

 I tried system Rescue CD for Linux, which has a run_qtparted , I tried, but can't get it work to enlarge my Ubuntu partition, after I allocated some free space for it, the resize/move opition for Ubuntu partition is still in grey, I can change the size of swap which is lie ahead in root. but not the root which is strange~

Another opition is try Partition magic 8, which is an Windows program, I tried it out, it can resize the partition of Ubuntu, but I didn't let it run it, afraid if I run  a windows program  in windows XP which change my Ubuntu partition, it will mess my Ubuntu partition up, did anyone tried that before?

I am backing up my Ubuntu data now, and will defrag my window FAT32 for couple of times to make the possible demage minimum if any.

---

### Post by greenstar on 2005-09-26
I've never used Partition Magic to resize a linux partition with data on it. I have used it many times to resize windows partitions and also to create linux partitions, but I always reformat those with linux before using. I have used gparted to resize my linux partitions. Install it if you haven't already:
```
sudo apt-get install gparted
```
then just use it from within Ubuntu. 
**Be sure to unmount the drive you want to change before using gparted**
```
sudo umount /dev/hdxy
``` where x=your disk and y=your partition
then remount when you're done
```
sudo mount -a
```

hope this helps

greenstar

**edit:**

gparted will also resize fat32 partitions from within Ubuntu, but I would test this ability before counting on it. Move the data off one of the fat32's then shrink or reformat or delete and create new and then try to read/write it from windows. If this goes well, then you'll be ok. If you find that the delete, resize/move and convert to options are greyed out on the partition menu, then the unmount option should be available - use it. This should now give you access to modify the partition.

---

### Post by ppl on 2005-09-26
Cool, looks like GParted is what I am looking for!
Things are much more clear now, I always has a bad feeling about change things in Linux from a Windows box.
Just out of curious, the Gparted is version 0.08, what's that mean, looks like for me softeware generally comes from ver 1.0 to be usable or stable.

---

### Post by ppl on 2005-09-26
Just installed Gparted, from what I can see I quite like Gparted, but still wandering why it is in ver 0.08, I am a newbie for Linux by the way.

---

### Post by greenstar on 2005-09-26
That version number lets you know how "old" the program is in terms of release cycles. Pretty new, and quite stable in my experience. Much better than qtparted (similar for KDE) which crashed often. Don't sweat the 1.0, 2.0, etc. stuff as much in linux. It's mostly ad hype in windows anyway. Listen to what people say about a peice of software. The human factor is better in linux in my experience. 

greenstar

---

