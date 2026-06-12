---
title: "Having issues installing 10.10 on RAID1 Array"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by n64guys5 on 2011-03-16
HP
3.2Ghz Core i5
4GB DDR3
2 2TB Western Digital Caviar Green HDDs

Brand new system I took out the original HDD and put mine in and I want to mirror the HDDs via RAID1.  This I have no problem with, it's when I try to install 10.10 on them.  Here's my setup:

500MB /boot  ext4
20GB /   ext4
4GB swap
20GB /home   ext4

When I start installing I get the error message:
The ext4 file system creation in partition #2 of RAID1 device #0 failed.

Bare in mind also that I am doing all of this just off of the cd I burned, because try as I might I couldn't get the system to boot from my flash drive (which I put 10.10 on as well).

There you have it, any and all advice is graciously accepted.  I'm primarily a mac user and don't have too much experience with linux but I know a few basic terminal commands to get myself by.

---

### Post by nogoodnamesleft on 2011-03-17
No controller card mentioned so I assume this is a fakeraid? i.e. the motherboard's onboard SATA raid controllers?

Or is it Ubuntu software raid?

try this if it's fakeraid.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

this if software raid

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

After it's setup make sure you can boot from it and that you perform a trial drive replacement. There's nothing like having a mirror and finding that when it fails (a) you can't boot off the remaining drive due to configuration problem, or (b) you have no idea how to rebuild it, and mirror the new blank drive onto the existing drive [seen it happen, don't laugh].

edit - I should add that I use mdadm not dmraid due to some bug which i cant remember which was probably unique to my configuration; but try mkadm if you have issues with dmraid.

---

### Post by n64guys5 on 2011-03-19
Yah,  there's no controller, what would be more beneficial?  A fakeraid or a Linux Software Raid?  I am not dual booting.

---

