---
title: "Question about resizing partitions"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by bomber991 on 2007-05-11
Alright, what I do know is that it is possible to resize an NTSF partition and still retain the data on it.  My question is, can you do the same thing with a linux partition?

I ask because I plan on running a dual-boot rig, and if in the future I need to add more space to my ntfs partition, can I resize the linux partition to create some free space without erasing any of the data on the linux partition?

Hope the question makes sense, thanks in advance to those who answer.

---

### Post by phiphedog on 2007-05-11
Yes it is possible, you should defrag the NTFS partition before you resize but apart from that you should have no troubles. You can use partition magic in windows or gparted in ubuntu. As always, back up your data before mucking around with partitions because things can go wrong with one slip of the mouse button.

---

### Post by bomber991 on 2007-05-12
> **phiphedog said:**
> Yes it is possible, you should defrag the NTFS partition before you resize but apart from that you should have no troubles. You can use partition magic in windows or gparted in ubuntu. As always, back up your data before mucking around with partitions because things can go wrong with one slip of the mouse button.

I did defrag before I did the resize on the NTFS partition the other day.  I wasn't too sure if partition magic lets you resize the linux partitions.

It seems like on these forums you search for a similar problem that you have, you find a thread that deals with it exactly, except it links you to another guide or thread that just doesn't exist anymore.    I'll check it out later today and let everyone know if pm works or not for this.

---

