---
title: "Win7/Ubuntu Dual-Boot"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by TopHatMatt on 2012-01-15
So, I apologize in advance if this is an old and frequently asked question, but I plan on dual-booting my Win7 laptop with the latest Ubuntu release. Now I have only set this up once before on an older model (Win98 laptop) and I am unsure how to do this on my Win7.

I currently own a Compaq Presario CQ56 with Windows 7 64bit OS installed and I noticed that it has four partions, (C:), HP Tools, Recovery (D:) and System. Now I assume that HP Tools consists mostly of bloatware, but I am a bit wary of deleting it, so I can shrink down the (C:) partion to make room for Ubuntu, as it seems to possibly control functions such as the system hot keys that turn functions such as HP Wireless Assistant on and off.

So in short I guess the question is, how might I go about properly setting up dual-booting without completely messing up my laptop?

Any help will be greatly appreciated, and once again, sorry if this is an over asked question, but I'm still a bit new at this.

---

### Post by 2F4U on 2012-01-15
You can have a maximum of four primary partitions on a harddrive. So if already four primary partitions have been created and are in use, you won't be able to install Ubuntu.

---

### Post by TopHatMatt on 2012-01-15
Right, I got that. Hence the, "what to do about HP Tools" partion. Wondering if its ok to get rid of or if its not, my options.

---

### Post by darkod on 2012-01-15
1. What ever you do, don't delete the System Reserved partition. It has win7 boot files on it, it can't boot without it.

2. One option is creating recovery CDs/DVDs using the recovery software it has, after which it's safe to delete the recovery partition. If you ever need a restore to factory default, you can use the DVDs.

3. HP Tools is safe to be deleted from what has been mentioned here. The Wireless Assistant you mention is a software installed, it doesn't run from HP Tools AFAIK.

---

### Post by Savio2010 on 2012-01-15
4 Partitions are not the limit for any hard disk, it is like this

**4 Primary Partions (limit)**
if you create 4 primary partitions then you are limited to that

**3 Primary Partitions 1 Extended Partitions**
if you create this scenario you have 3 + unlimited partitions
What I mean is in 1 extended partitions you can create as many Logical partitions you desire.

it can even be 1 Primary Partition 1 Extended partition
2 Primary Partition 1 Extended partition
However you are limited to only 1 extended partition on a hard disk.

---

### Post by fantab on 2012-01-15
> **darkod said:**
> 
2. One option is creating recovery CDs/DVDs using the recovery software it has, after which it's safe to delete the recovery partition. If you ever need a restore to factory default, you can use the DVDs.

+1.

The Data Partition Or D: or E: drive can be converted to Extended Partition. Just back up the Data on that Partition and then delete that partition. And using Gparted from Ubuntu LiveCD you can create an EXTENDED PARTITION and make Logical Partitions. You can search the net to learn more about the Extended Partition.

---

### Post by TopHatMatt on 2012-01-15
Thank you guys for the help. Its much appreciated.

---

### Post by presence1960 on 2012-01-15
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

For your reference.

---

