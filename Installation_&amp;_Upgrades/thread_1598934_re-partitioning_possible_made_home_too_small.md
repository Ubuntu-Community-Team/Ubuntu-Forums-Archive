---
title: "re-partitioning possible? made /home too small"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by XanII on 2010-10-17
Made a huge mistake when installing 10.04 on my brand new box. I miscalculated the HD space reservations when i installed using manual partitioning. Left out a zero from the size allocation when allocating space for /home so now my home is now way too small for anything. 

Any suggestions on how to grab some space from a 1,2TB windows 7 ntfs partition and move some of it to the ext4 /home?

---

### Post by Lazaruss on 2010-10-17
Assuming ext4 partition comes after Windows partition
1. Download GParted Live CD [here]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/"), and burn ISO to a blank disk
2. Back up anything you don't want to lose
3. Defragment Windows drive (And check how much data there is on it
4. Insert the GParted disk into your CD drive and reboot your computer (You may need to change BIOS to start from CD)
5. Resize the windows partition down a small amount (Don't make it smaller than the amount of data on it)
6. Grow the ext4 partition

All Done

**Modifying partitions has the potential to cause LOSS of DATA. Ensure data is backed up before resizing partitions**

---

### Post by 73ckn797 on 2010-10-17
Here is some helpful info: [https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

---

### Post by XanII on 2010-10-17
Thanks for the tips. I'll try theese.

---

