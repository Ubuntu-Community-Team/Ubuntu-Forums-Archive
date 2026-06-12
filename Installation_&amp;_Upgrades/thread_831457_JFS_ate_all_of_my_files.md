---
title: "JFS ate all of my files"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by Tigera on 2008-06-16
I have been using Ubuntu for about two or three years now, and it worked great all the way up to Feisty.  When I moved to Hardy, I decided to reformat and do a clean reinstall rather than an upgrade, and this was a pain because I had to back up /home too.  So, when I reinstalled, I decided to create a separate /home partition using JFS.
I hadn't rebooted since the install, and I had to shut down my laptop today as I was going on a trip.  For some reason, the machine wouldn't shut down by itself.  I was in a hurry and just switched the power off, and when I booted back up, /home was gone.  It would mount, so I tried to jfs_fsck it, and then an error message said that the primary and secondary block were corrupt and the data was unrecoverable.  Luckily, I remembered how to make a new reiserfs file system and I was able to recreate the partition (which apparently was also missing), and with a recent backup, I didn't lose too much, but obviously, this was very irritating.
Should I file a bug report, or is this a known issue when improperly shutting down with JFS partitions?  Why couldn't it recover the journal?

---

