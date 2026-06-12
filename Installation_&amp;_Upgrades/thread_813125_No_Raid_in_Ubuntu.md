---
title: "No Raid in Ubuntu"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by Cerin on 2008-05-30
Hi,

I'm a newbie to Ubuntu, coming from Fedora, so please excuse my ignorance. I just installed Ubuntu 8.04 and was unable to setup a software RAID-1 array. Fedora's installer has a marginally functional, if not clunky interface for setting up a software RAID array using LVM. After reading [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid), I had hoped Ubuntu 8.04 had something similar, but I saw no mention of *any* RAID setup in the installer. In fact, the "partition editor" didn't even let me use both of my hard drives. It would only let me repartition Ubuntu next my existing Fedora install, overwrite either of the drives (but not both), or manually configure the partitions, which boiled down to letting me change the drive formating and/or mount point.

Considering the Wiki's last mentioned release is 5, does Ubuntu no longer support RAID? The installer was otherwise fairly straight-forward and problem free, but did I miss something? Is there any other way to setup a basic RAID-1 array in Ubuntu?

---

### Post by Pumalite on 2008-05-30
Have you read this?:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Cerin on 2008-05-30
I don't think that's what I'm looking for. I'm trying to do software RAID, not firmware-based RAID, which I'm not even sure my motherboard supports. Since you pointed me to a how-to, can I assume the Ubuntu installer no longer supports RAID partitioning?

---

### Post by Pumalite on 2008-05-30
Ubuntu installer supports a hardware Raid

---

### Post by dstew on 2008-05-30
The Alternate Install CD fully supports creating and installing to software RAID (at least it did for Gutsy -- haven't tried Hardy, but I bet it still supports it). The Live CD does not support a software RAID install, as far as I know.

---

### Post by Cerin on 2008-05-30
> **dstew said:**
> The Alternate Install CD fully supports creating and installing to software RAID (at least it did for Gutsy -- haven't tried Hardy, but I bet it still supports it). The Live CD does not support a software RAID install, as far as I know.

I suppose I should have waited until Hardy was finalized, because the alternate CD is practically unusable. I tried following the guide at [http://bobbyallen.wordpress.com/2008/05/19/installing-ubuntu-with-a-software-raid1-configuration/](http://bobbyallen.wordpress.com/2008/05/19/installing-ubuntu-with-a-software-raid1-configuration/) and it seems to proceed correctly, but then I get a package dependency error when trying to install the kernel, and the whole install just dies. I tried capturing the error in /var/log/syslog, but it seems to get cleared after reboot. I even tried copying it /root, but apparently the Live CD wipes that out.

---

### Post by Cerin on 2008-05-30
Actually, the problem I ran into on the alternate install CD seems to be identical to the problem reported here: [http://ubuntuforums.org/showthread.php?t=797431](http://ubuntuforums.org/showthread.php?t=797431)

---

