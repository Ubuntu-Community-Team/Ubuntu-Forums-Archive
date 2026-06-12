---
title: "Ubuntu Installation - SATA RAID problem"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by dboyd13 on 2007-05-04
Hi All,

A friend of mine wants to give Ubuntu a try, but is having trouble with his SATA RAID 1 array during installation (Edgy 06.10) - he is seeing two separate disks rather than a single disk. The chipset ULI-1697. 

Any ideas on how to get the raid array initialized?

Thanks,
 Darran

---

### Post by Big Ed on 2007-05-06
> **dboyd13 said:**
> Hi All,

A friend of mine wants to give Ubuntu a try, but is having trouble with his SATA RAID 1 array during installation (Edgy 06.10) - he is seeing two separate disks rather than a single disk. The chipset ULI-1697. 

Any ideas on how to get the raid array initialized?

Thanks,
 Darran

You want the fakeraid howto:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

This one is a little old, but still informative:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

And on the topic of avoiding fakeraid altogether and just using software raid:
[https://answers.launchpad.net/ubuntu/+question/4738](https://answers.launchpad.net/ubuntu/+question/4738)

HTH,
Ed

---

### Post by dboyd13 on 2007-05-06
Thanks for all the info. I have forwarded this too him... hopefully it'll all work out.

---

