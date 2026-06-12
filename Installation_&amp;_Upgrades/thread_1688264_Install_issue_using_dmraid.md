---
title: "Install issue using dmraid"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by nextwebmaster on 2011-02-15
Followed the tutorial at [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID).

Everything fine and dandy, except after installation, the dmraid device couldn't be found by UUID, thus resulting in a mount error at boot time, "**Target Filesystem doesn't have /sbin/init**". 

After numerous attempts, found the problem: the partitions need to be pre-created, using a live cd. I just created the partitions, empty, no filesystem, on both drives, and then created the dmraid devices a the partitioner screen in alternate install.

Works flawlessly now.

---

### Post by ronparent on 2011-02-15
Welcome to the forum.

Just a quick observation. If you are using dmraid to discover your raids then your system has a FakeRAID and the SoftwareRAID is not applicable!

Also dmraid in the 10.04 distro has a bug in it that doesn't allow the partitioner to create raid partitions during the install. To work around that bug I usually suggest that the user boot to a 10.04 live cd, install kpartx, and, then run a normal install from that session. Your solution works also for that case. Glad you are up and running.

---

### Post by nextwebmaster on 2011-02-22
Yes, thank you. I have mis-formed my approach. I am using software RAID, since I find it a little easier to manage in the event of a drive failure, versus fakeRAID., which, in most cases, has an odd 'rebuild' procedure, depending on controller BIOS implementations.

Side question: is software RAID5 worth the extra harddrive(s), in terms of performance?

---

