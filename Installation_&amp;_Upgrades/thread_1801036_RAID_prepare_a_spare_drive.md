---
title: "RAID prepare a spare drive"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by kjuergen on 2011-07-09
After I had my share of problems I want to be prepared for failure....

For my home directory I run a RAID-1 array with two 1TB drives. Unfortunately my HDD controller doesn't have more I/O's to have a spare drive connected for the RAID. What I want to do is prepare another drive to be ready in case one of the used RAID units fails.

Is it possible to do the following:
- replace one of the RAID drives with a new one
- boot
- use Disk Utility to format the new HDD as a RAID unit and make it a member of the existing array which at this time only consists of one drive.

My question is whether the newly added drive can be added and will then be sync'ed with the data from the running array????

Thanks in advance!

---

### Post by YesWeCan on 2011-07-10
Hi there. I think the only thing you need to do is duplicate the partition table from a current RAID disk (sdx) to your spare disk (sdy):
sudo sfdisk -d /dev/sdx | sfdisk /dev/sdy
When needed you just add it to the array and mdadm will sync it.
There is very little to do so it is not normally necessary to prepare a spare disk in advance.

---

