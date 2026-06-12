---
title: "Notebook: to less space for upgrade"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-21
My notebook has only a 6 GB harddisk. To upgrade I need to have 1.5G free (that it says during my attempt to upgrade.

I wonder if I can move temperoary staff to an external USB harddisk and make a symlink from the original location to get more space free.

What would be a good choice to move away?

bye

R.

---

### Post by jimv on 2008-05-21
Upgrading is a rather iffy process.  The safest and most reliable way to go to the newest release it to backup any important files, then format the partition and install a fresh copy of the latest Ubuntu.

---

### Post by housam on 2008-05-21
I think that you can make an image of the entire system to your ext.HDD using this guide : [[COLOR="Red"]_Creating disc images using dd_[/COLOR]]("https://help.ubuntu.com/community/Backupsolutionsforlinux#head-68dc127a2f841561239a3e34db5bb9b029cf3bc7"), then you can recover it on the ext.HDD and update it.

---

### Post by prshah on 2008-05-21
> **ELMIT said:**
> My notebook has only a 6 GB harddisk. To upgrade I need to have 1.5G free (that it says during my attempt to upgrade.
What would be a good choice to move away?


A good choice (but complicated) would be to set a mountpoint for an ext2/3 partition (on your external drive) as "/var/cache/apt/archives/" because this is where package files will be downloaded, and thus where the most space will be needed.

A better idea; download and use the alternate CD; it's painless, fast and will not require as much space.

As a matter of curiosity: _how_ much free space do you have? (df -h will tell you)

---

### Post by prshah on 2008-05-21
> **jimv said:**
> Upgrading is a rather iffy process.  The safest and most reliable way to go to the newest release it to backup any important files, then format the partition and install a fresh copy of the latest Ubuntu.

This is OK for non-production systems, but _bad_ advice for those who have set up their systems by investing a lot of time and effort.

There is no problem with upgrading; I have upgraded across 4 releases, on varied machines, and it has been a smooth process in each case.

What _can_ cause problems is some hardware not being recognized after an upgrade because of an architectural or driver change ; that will happen even if you have a new installation.

A reinstall/format-reinstall process should be the last step, rather than the first.

---

### Post by ELMIT on 2008-05-21
Thanks for your suggestions. I like this one best:

> A good choice (but complicated) would be to set a mountpoint for an ext2/3 partition (on your external drive) as "/var/cache/apt/archives/" because this is where package files will be downloaded, and thus where the most space will be needed.

A new installation is almost impossible for me, because this notebook has an USB CD drive. At my original installation I used another notebook and swapped the hard disk. Unfortunately this installation notebook is broken, ...

I will give it a try.

Thanks!

R.

---

### Post by dstew on 2008-05-21
Try to free up disk space first. In the Synaptic package manager, Settings --> Preferences --> Files, click the Delete Cached Package Files button. You might be surprised at how much space you can free up with this. Also, empty the trash.

---

### Post by ELMIT on 2008-05-22
besides the ln -s I could move .evolution to the external harddisk, ... after 14 hours this little notebook (Toshiba portage CT3440) upgraded from 7.04 to 7.10.

Now I try to upgrade to 8.04.

---

