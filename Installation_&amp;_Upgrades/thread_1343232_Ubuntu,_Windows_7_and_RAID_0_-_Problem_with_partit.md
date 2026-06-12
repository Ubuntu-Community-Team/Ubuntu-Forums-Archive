---
title: "Ubuntu, Windows 7 and RAID 0 - Problem with partitions"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by topikito on 2009-12-01
Hello,

Yesterday I installed Windows 7 x64 on my new PC (core i7 920 with a RAID 0). All okay, but today I'm trying to install Karmic Koala Ubuntu 9.10 AMD64 and i have this problem:

I'm actually on the screen where you choose where you want to install Ubuntu. The "default" option is formatting the harddrive (thats NOT what I want), and there's just one more option available: Specify manually the partitions. I select it and press next. Now I see my partition table, that have:
/dev/mapper/isw_...._<name of raid>
   /dev/mapper/isw_...._<name of raid>1   (type) ntfs   (size) 104 MB
   /dev/mapper/isw_...._<name of raid>2   (type) ntfs   (size) 1000103 MB

I can "create new table partition" (if the first row is selected) or I can "change", "delete" or "revert". I don't know the exact name of theese options in english, because of I'm installing in spanish.

What can I do?? Can someone help me? Thank you guys!

**
More information about my system: i7 920, 6GB Ram, ASUS Rampage II Extreme MotherBoard

---

### Post by darkod on 2009-12-01
I haven't tried installing on raid myself, but I think you need the alternate install CD for using LVM and/or RAID. According to ubuntu.com.
Also this thread seem to offer different advice, but don't know if it can work for you since you already created your array.
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/how-to-install-ubuntu-9.10-on-a-raid-hdd-772246/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/how-to-install-ubuntu-9.10-on-a-raid-hdd-772246/)

---

### Post by topikito on 2009-12-01
Thank you darkod,

Someone told me I could download the RAID controlers before I install and manage the HD so, do you know how is that?

---

### Post by darkod on 2009-12-01
Download the raid controllers? You mean drivers?

---

### Post by topikito on 2009-12-01
mmmhhh yeah :oops:

---

### Post by darkod on 2009-12-01
Not sure about that. The Alternate Install CD should have them in it. I guess that's why it's recommended for LVM or RAID.

---

### Post by topikito on 2009-12-01
yes, but if i can apt-get them before installing for the partitioning, I'll spare downloading that CD and burning it :(

---

