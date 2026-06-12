---
title: "BTRFS quick questions"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-08-19
Hi all!

Does anybody know:

1) Why ext2 or 3 is recommended over ext4 for /boot in a an otherwise BTRFS install of Maverick here: [https://help.ubuntu.com/community/btrfs#Fresh](https://help.ubuntu.com/community/btrfs#Fresh) Install on 10.10 Maverick

2) What the progress is on a fsck tool for BTRFS? (Surely this should be a priority of anybody considering using it!)

3) If BTRFS will be the default FS for Maverick

Thanks!

Luke

---

### Post by Blue Beard on 2010-08-20
> **goseph said:**
> 
1) Why ext2 or 3 is recommended over ext4 for /boot in a an otherwise BTRFS install of Maverick here: [https://help.ubuntu.com/community/btrfs#Fresh](https://help.ubuntu.com/community/btrfs#Fresh) Install on 10.10 Maverick
Low overhead and most proven filesystem.

> **goseph said:**
> 
2) What the progress is on a fsck tool for BTRFS? (Surely this should be a priority of anybody considering using it!)
At least one Oracle employee has been working on this.  Power loss and abnormal crashes seem to be the problem cause.  The best work around appears to be "use snapshots".
> **goseph said:**
> 
3) If BTRFS will be the default FS for Maverick
Canonical has missed at least one milestone.  
Many organizations have concern about the "Experiemental" label.
I doubt it will make default in 10.10

---

### Post by goseph on 2010-08-21
Thanks!

---

### Post by Blue Beard on 2010-08-27
From Chris Mason:
We're still actively developing it.  I don't have a release date planned
yet but we should have betas coming out over the next few months.

[[[http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg05898.html]]](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg05898.html]])

---

### Post by Blue Beard on 2010-08-27
Canonical confirms btrfs won't happen until 11.04

+ (robbie.w: I deferred this for completion in Natty, as we won't be able
+ to complete all the remainin work for Maverick.)

[[[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support]]](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support]])

---

### Post by uRock on 2010-08-27
> **Blue Beard said:**
> Canonical confirms btrfs won't happen until **11.04**

+ (robbie.w: I deferred this for completion in Natty, as we won't be able
+ to complete all the remainin work for Maverick.)

[[[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support]]](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support]])
Fixed it for ya, thanx for sharing the link.

---

