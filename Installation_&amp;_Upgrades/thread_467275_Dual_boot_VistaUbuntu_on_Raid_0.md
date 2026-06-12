---
title: "Dual boot Vista/Ubuntu on Raid 0 ???"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by PaulFXH on 2007-06-07
We have a new Dell XPS 9200 with MS Vista pre-installed. This machine has two 250 GB HDs connected in a Raid 0 arrangement which certainly seems to significantly improve responsiveness.
As with all of our computers, I want to dual boot this one with Ubuntu. However, it seems that Raid 0 does not make this type of dual boot system easy. In particular, the Feisty  Live CD does not recognise the partitions (or the unallocated space) on the Raid 0 system.
Does anybody know how I can overcome this problem without taking out the Raid 0?

---

### Post by mckinneycm on 2007-06-07
Try using the alternate Feisty CD. It does a text-based install. It may help in your situation. Go back to Ubuntu and download 7.04. When it asks you where you want to download it from, make sure you check the box that asks if you need the alternate version.

---

### Post by PaulFXH on 2007-06-07
Thanks for your reply.
However, I'm not at all sure that can help me. My problem is that the Live CD just doesn't see the Raid-0 system as Vista sees it. So, while Vista sees one large (465GB) HD with multiple partitions including the 20 GB unallocated space I made to accomodate Ubuntu, Ubuntu just sees two unpartitioned 250GB HDs.
I really don't believe the alternate Live CD is going to see things any differently.

---

### Post by dagadetman on 2007-06-08
Hi Paul, 

I am facing the same issue here. I have just built a PC with RAID 0 on two Seagate SATA 320G drives and Vista Home Premium is working very nicely. I've put aside a 200G unpartioned space for Ubuntu 7.04 to slot into - but PC also only sees the physical drives not RAID from Ubuntu's partition manager.  

I did find a link on an Indian Ubuntu forum re SATA RAID ([http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)) which said to install dmraid once booted from the Live CD - however on my PC when the dmraid installation was about 80% complete it failed as it couldn't re-write a config file in an etc folder. :(

Cheers,
Ken

---

### Post by dagadetman on 2007-06-08
Hi again,

Just found two useful sites - 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
and
[https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

I'll try these tonight and let you know how I go.

Cheers,
Ken

---

### Post by PaulFXH on 2007-06-08
> I'll try these tonight and let you know how I go
Please do. However, I don't believe FakeRaid is the same as Raid-0 which is what you and I have.
I'm going to go the VM route using this [howto]("http://http://homepage.sunrise.ch/mysunrise/ekeller00/EricKellerUbuntuPage.html").
I'm also keeping this [guide]("https://help.ubuntu.com/community/BootFromUSB") up my sleeve as a contingency in case the VM doesn't work well. I've already used this to successfully boot a number of Linux OSes from an external HD even though my computer did not support USB booting.

---

