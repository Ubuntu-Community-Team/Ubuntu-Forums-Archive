---
title: "4 Disks Raid0. Ubuntu Edgy doesnt see my raid."
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by Orcun on 2006-12-23
Hi guys,

I have read the wiki. I am not using software raid and I am not sure If this raid0 is FakeRaid or Hardware raid.

I have Nvidia nForce Raid Controller and nForce 590/570/550 Sata Controller on an EVGA board with 680i chipset.

I have 250Gbx4 Raid0 which has 3 partitions 200Gb (Vista on here), 700Gb(Archieve),100Gb(Ubuntu will be installed here)

But when I booted from Live CD, It shows me my 4 drives but not the array. How can I solve this ? and which type of raid is my computer ? Fake or hardware ?

Thanks.

---

### Post by cervicor on 2007-01-04
Hello Orcun,

I'm quite sure, that you have a FakeRaid on your board. FakeRaid is not supportet by ubuntu yet. You have to use dmraid. I guess that you chipset is supportet by **dmraid**. Please see the following HowTo:

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")

and

[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

regards

cervicor

PS: I was not so lucky, my ULi M1575 chipset is not supportet by **dmraid**. I will setup a software raid for my server.

---

