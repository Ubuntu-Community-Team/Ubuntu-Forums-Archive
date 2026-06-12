---
title: "Cross platform disk cloning software"
date: 2017-04-06
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2017-04-06
Hi,
I'm looking for a cross platform disk cloning software. I read the comparative [here]("https://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software") and I think that a good solution could be clonezilla. However, it misses the support of cloning mounted partitions and of a GUI. I prefer using FLOSS, can you suggest me the best alternative?

Thank you

---

### Post by TheFu on 2017-04-06
When copying bits, cross-platform doesn't mean anything.  Either it copies the bits or it doesn't.  **dd** does 1 thing. It copies bits, as instructed. Nothing more.

I tend to use **ddrescue** most of the time, since it handles source problems gracefully and strives to get the data if there is any failure along the way. It also is slightly easier to use than dd.  Nothing will be faster than these 2 options.

Cloning anything mounted is a bad idea, unless it is read-only.  If you go into single-user mode and don't allow anything to run that could modify the source data in any way, then it isn't an issue.  Clonezilla is normally used from a live-boot (external media) to prevent data corruption due to changes while the clone occurs. Actually, most imaging software should be run in this way.  If you want to make a backup and don't want to take a multi-user system off line, then it would be smart to use LVM and snapshots to quiesce the file system being cloned.  But if you use LVM, you'll be cloning at the LV level, not partition.

I've used partimage and fsarchiver too.  I like that  **fsarchiver** compresses out unused space and that it can restore to smaller partitions than the source. Most other tools won't do that.  It also must be booted from alternate media before making a compressed image, so corruption isn't possible.  It will copy bit-for-bit if it doesn't know a file system.

You probably know all this stuff.

---

### Post by erotavlas on 2017-04-07
> **TheFu said:**
> When copying bits, cross-platform doesn't mean anything.  Either it copies the bits or it doesn't.  **dd** does 1 thing. It copies bits, as instructed. Nothing more.

I tend to use **ddrescue** most of the time, since it handles source problems gracefully and strives to get the data if there is any failure along the way. It also is slightly easier to use than dd.  Nothing will be faster than these 2 options.

Cloning anything mounted is a bad idea, unless it is read-only.  If you go into single-user mode and don't allow anything to run that could modify the source data in any way, then it isn't an issue.  Clonezilla is normally used from a live-boot (external media) to prevent data corruption due to changes while the clone occurs. Actually, most imaging software should be run in this way.  If you want to make a backup and don't want to take a multi-user system off line, then it would be smart to use LVM and snapshots to quiesce the file system being cloned.  But if you use LVM, you'll be cloning at the LV level, not partition.

I've used partimage and fsarchiver too.  I like that  **fsarchiver** compresses out unused space and that it can restore to smaller partitions than the source. Most other tools won't do that.  It also must be booted from alternate media before making a compressed image, so corruption isn't possible.  It will copy bit-for-bit if it doesn't know a file system.

You probably know all this stuff.

Thank you for your reply. I did not know about ddrescue and I also found that it has [GUI]("https://launchpad.net/ddrescue-gui"). So it is very interesting since I'm also looking for something with GUI for no expert user.
What do you suggest to use clonezilla or ddrescue with GUI? I'm going to create a liveCD with one of these software.
Thank you

---

