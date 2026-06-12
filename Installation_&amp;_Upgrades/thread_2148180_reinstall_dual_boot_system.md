---
title: "reinstall dual boot system"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by akinchansinha on 2013-05-24
I have a dual boot system with Windows XP and Ubuntu11.10. Now I want to upgrade ubuntu to 12.04 LTS with a live cd, as well as want to reinstall the xp. The XP portion is flooded with viruses. So I would like to format the whole system and reinstall both the O.S. But I am not much familiar with Ubuntu. So please help me how to do this.Thank you in advance.

---

### Post by holycow131415 on 2013-05-24
Make sure all your data is backed up.

Just boot up xp cd, delete and format all the partitions so that it creates 1 partition. Install xp drivers as normal. Right click My computer > Manage. Go into disk management. Shrink the volume enough so you create a partition large enough for your Ubuntu to install into.

Boot ubuntu livecd. during the install, chose the partition that was created.

---

### Post by fantab on 2013-05-25
> **akinchansinha said:**
> I have a dual boot system with Windows XP and Ubuntu11.10. Now I want to upgrade ubuntu to 12.04 LTS with a live cd, as well as want to reinstall the xp. The XP portion is flooded with viruses. So I would like to format the whole system and reinstall both the O.S. But I am not much familiar with Ubuntu. So please help me how to do this.Thank you in advance.

Since you already have XP and Ubuntu Dual-Boot setup it will will be as simple as:

1. Boot with your XP Install Disk. Format the 'C' partition and other WINDOWS Partitions ONLY if need be, and install XP. DON'T touch Linux/Ubuntu partitions.
2. Boot Ubuntu 12.04 install Disk and 'TRY UBUNTU". Let the desktop load. Establish Internet connectivity. And from Desktop 'Install Ubuntu'. At the dialog which reads "Installation Type" choose/select "SOMETHING ELSE". 
This will open another dialog which will show your Partitions. Select Ubuntu partitions and click 'CHANGE'. Another dialog will open where you will select: USE AS=ext4, MOUNTPOINT=/ and select FORMAT. 
If you have a separate /home partition then just select the partition, click 'CHANGE' and just MOUNTPOINT=/home, Do NOT format it. Thats it. Continue with Installation.

BACK UP ALL YOUR IMPORTANT DATA FIRST.

If you run into any issues or have problems then post your Computer specs, like RAM, Graphics card etc. And also tell us what your HDD partitions look like or better still post a screenshot.

Good LucK and Welcome to the Ubuntu forums.

---

