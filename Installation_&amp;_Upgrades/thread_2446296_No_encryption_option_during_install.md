---
title: "No encryption option during install"
date: 2020-06-27
forum: Installation &amp; Upgrades
---

### Post by Yahoé on 2020-06-27
I just tried to install 20.04 on a brand new Dell Inspiron 1500 5000, but unlike older versions (I have not installed for about two versions), there is no encryption during install option unless I choose the default LVM with the encryption option.
Since I like to partition myself, I could not encrypt drive.

Am I missing something here, is that an actual feature change?

Any help would be welcome :-)

---

### Post by CelticWarrior on 2020-06-28
The option to encrypt only /home was indeed removed years ago.
The full drive encryption - I think - was always like it is today, LVM+LUKS.

---

### Post by sudodus on 2020-06-28
> **CelticWarrior said:**
> The option to encrypt only /home was indeed removed years ago.
The full drive encryption - I think - was always like it is today, LVM+LUKS.

+1, I can confirm this.

If you want something else, [this link](https://ubuntuforums.org/showthread.php?t=2399092) and links from it may help you.

---

### Post by deadflowr on 2020-06-28
Home encryption using ecryptfs has been gone on installation setup for a few releases.
(It is still an option to setup post install though.
The packages still exist in the Ubuntu archives, just they've been moved to the community repositories)
See bug report on removal reasoning:
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840")

Other than that you can still encrypt physical volumes through the Something Else option.
(on top of the Advanced Feature luks/lvm option)

So really the only encryption option removed was encrypting home.
Which is still possible, if only a tad more complex to do now.

---

### Post by TheFu on 2020-06-28
Think of an LV as a partition.

Post-install, just shrink the "root" LV, then create other LVs (think partitions) as you like.  

Don't use all the storage for LVs.  Leave some free space in the VG for snapshots and other needs.  Growing an LV is 10 seconds on a live filesystem.  Shrinking an LV is much harder so i try to allocate only what is required for the next 3-6 months.

All the storage inside the VG is held inside an encrypted LUKS container, so all the LVs are also encrypted and opened pre-boot. For example: [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)

LVM provides lots of flexibility, but only if we use it in that way.

---

### Post by Yahoé on 2020-06-29
Great. Exactly what I was looking for. Thank you all. :-)

---

