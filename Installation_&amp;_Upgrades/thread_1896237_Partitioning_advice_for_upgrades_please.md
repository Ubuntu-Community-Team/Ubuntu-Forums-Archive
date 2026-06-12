---
title: "Partitioning advice for upgrades please"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by xchecker on 2011-12-16
I currently run 10.04 as the only OS on my desktop and I'm ready to try the upgrade.  Just updating has grown too cumbersome so I want to do a fresh install.  I have no partitions currently but understand it is recommended that I create two or more for safety and convenience.  Unfortunately I have received different opinions on which partitions and what sizes I should have.  

What are your best recommendations about partitioning as part of the migration from 10.04 to 11.10?  Thanks!

---

### Post by mikewhatever on 2011-12-16
Decide what you want first, update, upgrade or fresh install. ...and by the way, why is updating cumbersome?

As for partitions, how can you not have any, and run 10.04?

There are different opinions about the amount of partitions needed. IMHO, you only need one, which also solves the question of sizes. In other words, if you are going for a fresh install, let the installer use the whole hdd.

Backup your data first!

---

### Post by xchecker on 2011-12-16
My wireless is a bit erratic; the update takes so long that my connection drops and the update fails to complete.  I have downloaded and burned the 11.10 iso to a disk on another machine.  I guess I need to understand the difference between upgrade and a fresh install first.

---

### Post by ratcheer on 2011-12-16
If you have /home on a separate partition, you can do a fresh install to / as long as you tell the installation routine NOT to format the partition with /home. This is euphemistically referred to as a "dirty install".

After doing that, you will still have to reinstall your apps, but the configuration info, data, etc will still be in /home. E.g., after you reinstall your web browser, when you start it, all of your bookmarks, etc, should still be intact.

I have done this before and it works pretty well.

Tim

---

### Post by mikewhatever on 2011-12-16
> **xchecker said:**
> My wireless is a bit erratic; the update takes so long that my connection drops and the update fails to complete.  I have downloaded and burned the 11.10 iso to a disk on another machine.  I guess I need to understand the difference between upgrade and a fresh install first.

Perhaps you should post a help request about the wireless. Doing a fresh install or upgrading just to, hopefully, fix the wireless, is like shooting birds with a canon. The problem may actually get fixed, but you never know how many more will be introduced.

Upgrading and reinstalling are different. For example, you don't have to download an ISO and burn anything when upgrading.

---

