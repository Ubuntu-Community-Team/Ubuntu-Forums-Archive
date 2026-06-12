---
title: "error processing  capplets-data"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by Bruce Couper on 2007-05-04
Description of problem:

**capplets-data** is not updating, the computer is slow and some icons in top panel are rearranged from normal

Update notifier shows capplets-data (and four other packages) to be updated but fails with the following:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a ' to correct the problem.  E:_ cache->open () failed, please report.

Running> sudo dpkg --configure -a fails with the following error message:

> Package is in a very bad inconsistent state - you should reinstall it before attempting configuration.

I attempted reinstallation with apt-get but this, too, failed with a frozen system.

I attempted to mark all updates from within Synaptic Package Manager which is, again, frozen (at **Reading database...**.

System was recently upgraded from 6.10, with upgrade attempt interrupted at a point unknown to me but later upgraded, apparently successfully, when the upgrade button reappeared in the Update Notifier.

Any help would be greatly appreciated and I will provide any information required.  I'm attempting to help a friend, remotely, using VNC.  Her skill level is low and mine is moderate (I have only limited Linux experience but patience).  The new Network Manager is also not working properly (wired network must be manually selected after each boot) but I believe that is a known bug and probably not related.

Cheers, all

---

### Post by Bruce Couper on 2007-05-09
Update:

While I'm sure this could have been fixed with a deep enough knowledge of Linux it was easier to simply reinstall.  The details, should this help anyone:

I emptied the cache in Firefox and compacted the folders in Thunderbird.

I backed up most of my friend's home folder, including the hidden files, excluding what I knew would not be needed, burning everything to CD (DVD, would be more appropriate for many).

I did a clean install of 7.04, did the updates and installed software as appropriate.

I restored my friend's data.

This was very easy and much faster than trying to solve the problem and, of course, it provided my friend with a recent backup of her data.

---

