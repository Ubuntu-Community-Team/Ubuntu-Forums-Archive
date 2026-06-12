---
title: "HDD not detected - Installation impossible"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by jeroen94704 on 2008-02-21
Installing Ubuntu 7.10 on my laptop (Toshiba Satellite 1415-S105. Not new, but not quite ancient either) has proven to be impossible. The problem is that the partitioner does not detect any hard drives at all. Other distributions (Fedora, PCLinuxOS, but also older versions of Ubuntu) have no problem detecting the HD and install just fine. 

According to a helpful individual over at LinuxQuestions, this issue may be due to some recent instability in the ide controller modules that were rolled into libata. This laptop has an Intel 845MZ chipset.

I suspect it's not possible to work around this in the current version. Is this message enough to make the Ubuntu devs aware of this issue and/or give them a feel for how widespread the problem is, or can/should I submit a bug about this somewhere?

Thanks,

Jeroen

---

### Post by logos34 on 2008-02-21
One workaround would be to try 7.04 or 6.10 cds.  If they recognize the disk, install and then [upgrade.]("https://help.ubuntu.com/community/UpgradeNotes?highlight=%28upgrade%29") (get the text-based **alternate** install cds--then you can [upgrade directly off the disc]("https://help.ubuntu.com/community/GutsyUpgrades#head-93ac2e597b9e0c5ff78111d4fd2bbe34a35799c7") instead of network).

---

### Post by jeroen94704 on 2008-02-21
Yes, well, I was really hoping to install MythBuntu on that laptop (to use it as a frontend). I think upgrading from Ubuntu 7.04 to MythBuntu 7.10 (The only version available) is not a recommended upgrade path :).

---

