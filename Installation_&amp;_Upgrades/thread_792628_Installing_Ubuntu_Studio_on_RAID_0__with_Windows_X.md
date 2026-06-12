---
title: "Installing Ubuntu Studio on RAID 0  with Windows XP already installed"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Leggie on 2008-05-13
Hi all,

Here is the situation. I have two SATA drives in a RAID 0 array. The array uses the motherboard onboard nForce4 controller, so it's fakeraid, I presume.

I have Windows XP installed on one partition, with another partition being used by Windows for documents, etc. Both use NTFS.
There is about 80GB of unpartitioned space available, upon which I would like to install Ubuntu Studio 8.04.

My difficulty is that when installing from the DVD, the Partition Manager doesn't detect the RAID array, just the two individual SATA hard disks.

After spending a fair time searching, I found the [FakeRaidEdgy]("https://wiki.ubuntu.com/FakeRaidEdgy") guide, and tried following that; unfortunately it didn't work for me right from the "type dmesg | tail to reveal the device name of the stick" point. I suppose it's out of date, but I don't know for sure.

Would someone please be good enough to give me an explanation of what I need to do, along with how I need to do it?

Thanks,

Leggie

---

### Post by lemming465 on 2008-05-19
Does [this SATA RAID Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto") help any?  I use use mdadm striping on my dual-drive office PC, so I don't have hardware RAID experience with Ubuntu.  On servers at work we make a point of buying RAID controllers supported by our OS vendors.

---

