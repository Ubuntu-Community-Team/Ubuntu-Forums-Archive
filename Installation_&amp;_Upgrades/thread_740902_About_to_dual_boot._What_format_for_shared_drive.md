---
title: "About to dual boot. What format for shared drive?"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by Daminator on 2008-03-31
Hello all,

I occasionally need XP for work (no, a virtual macghine wouldn't cut the mustard), but I am about to move my work machine over to dual boot so that I don't have to use XP when I'm not doing animation in 3DS Max.

My question is, what format should I use for the partition that will store shared data?

I know the old advice used to be FAT32, but that's quite dated now and not great for big hard drives.
I know that there are a couple of utilities to enable Windows to read/write Ext2/3.
I also know that the NTFS read/write is pretty good now, but don't know how trust worthy it is.

What are your thoughts? What's the pro's and cons of each option and what are people actually using day to day?

Cheers
Damian

---

### Post by linuxisfree on 2008-03-31
> **Daminator said:**
> Hello all,

I occasionally need XP for work (no, a virtual macghine wouldn't cut the mustard), but I am about to move my work machine over to dual boot so that I don't have to use XP when I'm not doing animation in 3DS Max.

My question is, what format should I use for the partition that will store shared data?

I know the old advice used to be FAT32, but that's quite dated now and not great for big hard drives.
I know that there are a couple of utilities to enable Windows to read/write Ext2/3.
I also know that the NTFS read/write is pretty good now, but don't know how trust worthy it is.

What are your thoughts? What's the pro's and cons of each option and what are people actually using day to day?

Cheers
Damian

I'd suggest to format it to NTFS. Lots of programs are good with the read/write to NTFS. NTFS Config or NTFS 3G are good.

---

### Post by Daminator on 2008-03-31
Thanks for that linuxisfree,

Is that a fairly standard view these days or would many disagree?

---

### Post by linuxisfree on 2008-03-31
I personally think it is, but that may be just me:D

I definitely use ntfs, at least in some way. (my external harddisk is ntfs partitioned).

I wish you good luck with what you're going to do:)

---

### Post by twright on 2008-03-31
i would use ntfs, or you could just put your home folder on a ext3 partition and use this to allow windows to read it
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by prshah on 2008-03-31
> **Daminator said:**
> Thanks for that linuxisfree,

Is that a fairly standard view these days or would many disagree?

Yes, fairly standard... NTFS on external drive if you are going to be using the drive on other systems elsewhere. If you are worried about stability, I have had no problems ever since gutsy release. (October 2007).

Personally I would simply avoid any MS filesystem;
a) On principle
b) What if tomorrow they claim that it's a proprietary file system and to use it you need a licensed copy of Windows?

---

