---
title: "Critical: dirty shutdown"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-09-21
Up to date Kubuntu Karmic is in use (the problem is not related to X11 use at all). I don't have kdm in rc.X, so use 'sudo shutdown' from console to shutdown. At the very last second - just before turning power off - I see messages about remounting this ot that fs 'read only' and '...Failed!', and 'Segfault', and something else... You see, I can not exactly reproduce the messages as I have not high speed video camera :-)

On next turning power on fsck founds, commonly, 1-3 not-clean filesystems (recovering journals or orphaned nodes).

It's definitely critical bug (I'm sure it is related to upstart and Ko massive upgrades just before A6), but, as far as I can not supply exact information, I'm not sure it is worth to report new bug. At case anybody has the same experience, I'll report.

Anybody?

---

### Post by VMC on 2009-09-21
Look AT 'SYSLOG' Either from a terminal or from System>Admin>LogViewer Then on the right side you see time stamp. Look for last time when you logged off. Then from there you should be able to see the messages your referring to.

---

### Post by ilna on 2009-09-21
> **VMC said:**
> Look AT 'SYSLOG' Either from a terminal or from System>Admin>LogViewer Then on the right side you see time stamp. Look for last time when you logged off. Then from there you should be able to see the messages your referring to.What files you are saying about when all filesystems are unmounted?

---

### Post by chrismine on 2009-09-21
I see the same behavior from time to time - after rebooting Karmic does not start up and then have to go into recovery mode and run fsck manually - shows filesystem has errors and fsck died with status 4 and timestamp in the future. After rebooting from recovery mode Karmic then start again.

I had checked the syslog via System -admin -logfile viewer and see nothing untowards. I may be overlooking it.

I may not remember correctly  but when in recovery console it says something about mountall - may it be the culprit? 

I though my hard drive may be going bad - thanks this set my mind at rest.

This is with ext4 on root and home partitions.

---

### Post by ilna on 2009-09-21
> **chrismine said:**
> I see the same behavior from time to time - after rebooting Karmic does not start up and then have to go into recovery mode and run fsck manually - shows filesystem has errors and fsck died with status 4 and timestamp in the future. After rebooting from recovery mode Karmic then start again.

I had checked the syslog via System -admin -logfile viewer and see nothing untowards. I may be overlooking it.

I may not remember correctly  but when in recovery console it says something about mountall - may it be the culprit? 

I though my hard drive may be going bad - thanks this set my mind at rest.

This is with ext4 on root and home partitions.

I also have all partitions of ext4 type except for /boot one (ext3). Can you try to stop X (something like 'sudo /etc/init.d/gdm stop') and then 'sudo halt' from console to be able to catch last messages?



P.S. Of course, starting thread post has typo: 'sudo shutdown' must be read as 'sudo halt'.

---

### Post by chrismine on 2009-09-21
When I stop gdm I get a corrupt screen in the colours of my background which just hangs until I reset the PC so I do not have access to the console menu.

---

### Post by ilna on 2009-09-21
The issue [https://bugs.launchpad.net/ubuntu/+bug/434224](https://bugs.launchpad.net/ubuntu/+bug/434224) is reported. Please, at confirming be sure you have the same experience during shutting down **in console mode** as I have.

---

