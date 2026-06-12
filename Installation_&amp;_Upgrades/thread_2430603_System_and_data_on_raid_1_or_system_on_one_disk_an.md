---
title: "System and data on raid 1 or system on one disk and data on raid 1 ??"
date: 2019-11-04
forum: Installation &amp; Upgrades
---

### Post by llmclsn on 2019-11-04
I want to setup a fileserver with Ubuntu server.
Should i use 1 hdd for the system and another 2 hdd for data in raid 1 or should i use 2 hdd for system and data?
Who can advise me.

---

### Post by uRock on 2019-11-04
I'd go with multiple data drives. I really don't like wasting space. I already have backups.

---

### Post by llmclsn on 2019-11-04
Thank you uRock,
But can i acces those data drives when my system drive fails ?

---

### Post by uRock on 2019-11-04
> **llmclsn said:**
> Thank you uRock,
But can i acces those data drives when my system drive fails ?

If they're not encrypted, then yes, you can easily access them once the system is reinstalled or you connect them to a new system. I have my desktop set up that way. SSD has the OS on it, as well as /home, and my two 1TB drives are used as data drives.

Always have backups. There's nothing worse than losing a data drive and realizing you've lost 20 years of pictures.

They can be encrypted, but read the documentation before doing so.

---

### Post by llmclsn on 2019-11-10
Thank you for our answer.
I have now a test server were i have 2 hdd set up as raid 1 with the system on it.
I have this done because the server will be used in a production envirement, so it has to be up all the time.

---

### Post by TheFu on 2019-11-10
> **llmclsn said:**
> Thank you for our answer.
I have now a test server were i have 2 hdd set up as raid 1 with the system on it.
I have this done because the server will be used in a production envirement, so it has to be up all the time.

I agree with  uRock.  RAID can never replace backups.  RAID solved 2-3 problems.  Backups solve 1001 problems, including a corrupted RAID set.  There should be no use of RAID without having solid, know-you-can-restore backups first.

Plus, good backups can be restored in 30-45 min, so there are very few businesses who can't handle that amount of downtime.  RAID is a bunch of hassle for that result.

I use RAID1 a few places, but only for 1 reason.  Running Virtual Machine storage.  Actually, we are looking to drop RAID and switch to network-based replication for our VM systems. This way, if an entire disk subsystem fails, other machines will automatically switch to the other storage location and continue running.

If I needed to setup RAID1, I'd begin with an OS running LVM. The installer will set that up no problem.  Then using LVM commands, I'd enable RAID1.  Think I posted those specific commands here a few months ago.  LVM provides volume management just like the commercial Unix systems have and has been in production use over 20 yrs on Linux.

If I needed to used drives over 1TB in size, then I'd probably deploy ZFS for all data needs. ZFS provides LVM-like abilities plus a file system plus data validation and correction that no other solutions provides. It is a different way of thinking.  I would not use ZFS for boot storage or the OS at this point.

But we all have different needs. Only you can decide which of the answers fits best. Knowing about all the options should help people make more informed choices.

---

### Post by Tadaen_Sylvermane on 2019-11-10
I'd say it depends on your data. If it's stuff that almost never changes and your IO needs aren't extreme then maybe a combination of mergerfs and snapraid might be better? Then you wouldn't waste any real space as mergerfs and snapraid work off of paths instead of devices. I use it at home for media storage. Downside is if something happens to a drive before it's been recently synced then anything done after the last sync is lost. Again, good for stuff that rarely changes. Bad for regular data and os use though.

And always backups regardless of chose solution.

---

