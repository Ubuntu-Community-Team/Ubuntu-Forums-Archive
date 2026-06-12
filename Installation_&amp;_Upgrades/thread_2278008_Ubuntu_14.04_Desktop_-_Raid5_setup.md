---
title: "Ubuntu 14.04 Desktop - Raid5 setup"
date: 2015-05-13
forum: Installation &amp; Upgrades
---

### Post by Gekkegast on 2015-05-13
Hi Guys,

I'm trying to set up Raid5 using Software Raid (mdadm) on Ubuntu 14.04 Desktop. When I try to create the array using mdadm I get the following message:
mdadm: RUN_ARRAY failed: invalid argument.

I created the array using the following command:
mdadm --create --verbose /dev/md0 --level=raid5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

Is Raid5 by default supported on ubuntu desktop?

Greetings

---

### Post by Elizine on 2015-05-14
Hi,

You can refer to the link below containing information related to installation or software RAID. It includes instructions on RAID5 in the Checking the status of your RAID section. If you still get stuck on the issue, please do reply.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

