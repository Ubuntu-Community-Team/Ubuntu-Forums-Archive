---
title: "Bug #557429 (RAID1 array corruption) removed from known issues but not fixed yet!"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andy80 on 2010-04-23
Hi all,

comparing these two changelog:

Ubuntu 10.04 beta 2: [http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2)
Ubuntu 10.04 RC: [http://www.ubuntu.com/getubuntu/releasenotes/1004overview](http://www.ubuntu.com/getubuntu/releasenotes/1004overview)

You have removed this bug from known issues:

> Activating a RAID 1 array in degraded mode is reported to lead to RAID disks being reported as in sync when they are not, resulting in data loss. Since RAID 1 arrays will automatically be brought up in degraded mode when a member disk is unavailable, users with production software RAID 1 disks are advised not to upgrade to the 10.04 LTS Beta until this bug is resolved. (557429)

Looking at the bug page ([https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/557429](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/557429) ), the bug is NOT FIXED yet! This could cause a data loss for users installing and using Ubuntu 10.04 RC.

---

### Post by Braineh on 2010-04-23
Cheers for posting this. Was already happy when I read the release notes that the bug is finally gone in RC just to realize some minutes later it isn't.

---

