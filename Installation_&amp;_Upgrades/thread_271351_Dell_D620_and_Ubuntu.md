---
title: "Dell D620 and Ubuntu"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by RamenBooko on 2006-10-04
Here's the deal. I go to College, so my Windows XP install is perfect (for now).

I wanted to add Ubuntu and dualboot. I gave it a shot last night, but it turns out I have an extra partition (which turned out to be the EISA config - 47mb). The problem is, I don't want to reinstall Windows and Ubuntu would not allow more than 4 partitions.

So i need to have 4 partitions in total:

Memory Swap
Data Sharing
Windows
Linux

What can I do, any help appreciated.

---

### Post by whizbaby on 2006-10-04
No, four *primary* partitions is the correct term. That means that you still can create an *extended* partition and put other partitions in that (number of primary + number of extended < or = 4 ). I think the primary partition limit is not only limited to ubuntu, it is a hardware-thingy.

---

### Post by RamenBooko on 2006-10-04
So, how would I make this work? I remember from last night that when I select 'Extended Partition', it does not ive me an option at a file format. Whereas, these 4 partitions (plus 1 for the EISA config) need to be specific. The reason I am asking these questions is because I read somewhere that the EISA partition is needed.

---

### Post by whizbaby on 2006-10-04
> **RamenBooko said:**
> I remember from last night that when I select 'Extended Partition', it does not ive me an option at a file format.
Of course not, but it will for the partitions you create *in* the extended one.
EDIT:
E.g. you can put the swap and ext partitions for ubuntu into it.

---

### Post by Fatjoint on 2006-10-04
> **RamenBooko said:**
> So, how would I make this work? I remember from last night that when I select 'Extended Partition', it does not ive me an option at a file format. Whereas, these 4 partitions (plus 1 for the EISA config) need to be specific. The reason I am asking these questions is because I read somewhere that the EISA partition is needed.

You're limited to 4 primary partitions because the MBR contains information regarding each partition installed.  IIRC it so happens that the MBR size is 512k and each block assigned to a partition that can exist within the MBR is something like 115k, the last remaining space is dedicated to super block and magic number.

Create two primary partitions, one that is mounted / with a format of ext3, put all of your extended linux partitions in it - don't worry about format because they are ext3 anyways.

The other primarty mount as /data with a format of vfat.

4 total primary's
-----------------
1 EISA
1 NTFS
1 EXT3 -> Extended partitions - /, /home, /swap
1 VFAT -> FAT32

---

### Post by RamenBooko on 2006-10-04
Ah, I should have mentioned that I haven't gotten this nitty gritty with Linux before. Would I be an *** if I asked you to kind of walk me through it?

---

