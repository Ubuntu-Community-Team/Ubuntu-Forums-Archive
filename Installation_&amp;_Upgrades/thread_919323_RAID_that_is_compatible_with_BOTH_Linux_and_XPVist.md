---
title: "RAID that is compatible with BOTH Linux and XP/Vista?"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2008-09-13
I am planning to use my system in dual/multi boot configuration: Ubuntu 8.04 along with Vista and XP (for development/testing purposes).

Ideally, I would like to use my 2 identical 500GB SATA HDDs in RAID configuration.

My motherboard supports RAID in the BIOS but it turns out the while Windows XP and Vista work well with that BIOS RAID, Linux completely ignores it and continues to see my 2 HDDs as completely separate drives... :(

So, my question is: is there a software-based RAID implementation that is transparent to both Windows and Linux?

Thanks,
Alex

---

### Post by Pumalite on 2008-09-13
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by xp_newbie on 2008-09-13
> **Pumalite said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

Wow! Thank your for your quick and accurate answer. I didn't even know about the existence of the term FakeRAID. It is right on the money but seems dangerous since it is not really supported (yet) by Ubuntu.

> **Pumalite said:**
> [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)
This URL doesn't work for me for some reason. The following one does:

[http://ubuntu-in.info/wiki/index.php/SATA_RAID_Howto]("http://ubuntu-in.info/wiki/index.php/SATA_RAID_Howto")

---

### Post by Pumalite on 2008-09-13
I'd tell you that software Raid is not worth the time. Minimal performance improvement and lots of headaches. I'd install with independent drives.

---

