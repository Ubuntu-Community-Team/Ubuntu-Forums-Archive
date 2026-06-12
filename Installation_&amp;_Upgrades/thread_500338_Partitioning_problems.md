---
title: "Partitioning problems"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by scru on 2007-07-13
After spending the entire morning just getting a live boot of ubuntu to work (my fauly really, the last blank cd i had burned with an error, and i had to configure a flash drive to do it instead), i was finally able to use linux for the first time. I had a good experience too, especially the very pleasant surprise i found in driver support, which should make Vista flush in embarassment (I'm not kidding...all my devices were up and running, except for my graphics card, and even then i was offered the driver without having to go hunt for it...i still used the default one since the boot was a live one)

Now, the problem arose when i decided to add ubuntu to my list of OSes that i use. My drive partitions are ntfs. I went so far as to free some space from my main drive to unallocated space (about 20 Gigs) with the partition mager, but it told me i cant have more than four partitions(there was an adjective i can't remember).

My partitions are as follows:
Acer (C):
MediaStorage (I):
PQSERVICE (hidden partition used for recovery by acer software)
WinXP (L): (contains boot record for my vista and xp)

I guess I should have mentioned that i dual boot xp and vista currently (XP for games, vista for productivity)

since ACER and MediaStorage are both larger than 32MB, the only possible solution i can think of is to convert WinXP to FAT32 and install linux there. However, searches seem to say that this can't be done without data loss. This is a no no because my windows boot record is on there, and additionally, my XP cd is old and scratched badly and tends to do erratic installations most of the time, so i cant afford to have XP erased (well i CAN do without it, but I dont really want to...i like my games).

SO does anybody have any suggestions about what to do about this problem at all? I would really hate to let this just pass...because i would definitely have to wipe that flash drive off by tomorrow (its my mom's--mine is only 512MB) and restore its original data...

sorry if this is long

Please help me...ill give you a cow and marry your wife

---

### Post by Vajra Vrtti on 2007-07-13
The problem is that you can't have more than 4 primary partitions in a disk. But you can create secondary partitions inside a primary partitions. Ubuntu will install in a secondary partition without any problem (mine is so).

---

### Post by Pumalite on 2007-07-13
If you cannot make space for Ubuntu in an extended partition formatted ext3 or similar, you will have to pass up Ubuntu.

---

### Post by scru on 2007-07-13
> **Vajra Vrtti said:**
> The problem is that you can't have more than 4 primary partitions in a disk. But you can create secondary partitions inside a primary partitions. Ubuntu will install in a secondary partition without any problem (mine is so).

How is this done exactly? I'm not exactly familiar

---

### Post by Pumalite on 2007-07-13
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Vajra Vrtti on 2007-07-14
It is Gparted that is used during the installation, so you can do the partition stuff either before or during the installation, as you wish. During installation you have to select the manual option in order to do that. In any case, when you select the primary partition you will have the option to create secondary partition(s) inside it. The primary partitions are numbered from 1 to 4, and the secondary ones from 5 on (even if you don't have 4 primary partitions). Once created, the secondary partition(s) behave just like the primary ones.

---

### Post by scru on 2007-07-14
Ok, sorry for wasting your time but I've decided to just put in an older hard drive instead and partition that. I'll let you know how it goes

---

