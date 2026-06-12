---
title: "Upgrading a system with /home on a different physical drive"
date: 2019-07-22
forum: Installation &amp; Upgrades
---

### Post by Music_Guy on 2019-07-22
I plan to set up my computer so that the operating system is on an SSD, while the /home directory is on an HDD.  I know how to install Ubuntu so that the system will be as I want it to be.  When I eventually upgrade the operating system (say from Ubuntu 19.10 to 20.04), is there a way to just update the operating system without overwriting the /home directory?

---

### Post by TheFu on 2019-07-22
Yes. The upgrade process doesn't alter mounts or data inside HOME directories. But, you will need to have a full and complete backup that you know you can restore from BEFORE doing any major updates.

Stay patched.
Stay backed up.
When you are ready to move from 1 release to the next, run a fresh **sudo apt update && sudo apt dist-upgrade** first, then reboot, make a full backup, and once all that is done, run **sudo do-release-upgrade** when you have a few hours that you know won't have any power or network failures. 

 If there is a thunderstorm, wait.

If you need to reinstall a fresh OS wiping the prior OS first, use the "do something else" install option and when you setup the storage locations, verify that /home uses the correct partition/LV and doesn't have the "format" checkbox.

Did I mention that you should have backups that you know, 100%, can be restored before starting any of this?  I'm not kidding. It is very common for mistakes to be made by accident and lots of people completely wipe stuff they didn't want wiped.

---

### Post by Music_Guy on 2019-07-22
Thank you for the quick and detailed reply.  I thought that there was a way to upgrade, but I did not want to set up a system then find I had a lot of problems upgrading.  And, I ALWAYS backup, having been burned one time in the deep dark past where it cost me a lot of money to get some of my data back.  Thanks again.

---

### Post by TheFu on 2019-07-22
If any of the commands above fail. STOP and fix the issue.  Do not continue.  Issues don't get better by forcing a release-upgrade, just worse.

If you want to leave this open to see some other ideas/methods, that's fine.  But when you are good with the answers, please mark this thread as "SOLVED" using the thread tools button near the top. That helps the wider community greatly.

---

### Post by sevendogs1337 on 2019-07-22
I run this configuration, except my /home is on an SSD, and have had great luck with it for several years. Take TheFu's advice.

---

### Post by rsteinmetz70112 on 2019-07-24
Why doesn't **do-release-upgrade** just do the **apt update** and **apt upgrade** before starting the release upgrade?
Personally I always run them twice then do **apt  autoremove** before **do-release-upgrade**. 
You'd be surprised how often something else shows up.

---

