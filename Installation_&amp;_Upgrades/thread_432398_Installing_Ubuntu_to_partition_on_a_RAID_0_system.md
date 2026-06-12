---
title: "Installing Ubuntu to partition on a RAID 0 system"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by BungaDunga on 2007-05-04
I have two hard disks that are set up with RAID 0 so they appear as one, doubly-big HD in Windows. I've no idea of the particulars, the computer came configured like this.

There is a small D:\ drive that shows up in Windows, which I think is a partition on the RAID; I would like to install Ubuntu to this partition to check it out. The installation program just sees the two drives separately as sda and sdb. GParted sees two 74 GB drives "unallocated". Is there any way I can do what I'm going for?

Edit: Ah, I think I have a "fakeraid" as covered [here]("https://help.ubuntu.com/community/FakeRaidHowto"). Far too complicated for me, I might as well just reinstall everything and keep the two disks separate, I need to redo Windows anyway.

---

