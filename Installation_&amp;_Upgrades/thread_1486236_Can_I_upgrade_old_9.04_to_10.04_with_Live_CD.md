---
title: "Can I upgrade old 9.04 to 10.04 with Live CD?"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2010-05-17
I'd like to upgrade the Ubuntu 9.04 on a system to the 10.04 and I have the 10.04 LiveCD. Usually I would get a new HDD and install on that , then move stuff onto the new HDD, but I thought that this time i'd try some other method. I've done the online upgrade once but it took a long time, while connected, and it worried me.

Can I replace the 9.04 with 10.04 without losing anything (although perhaps requiring an Update Manager run to refresh some apps, Like OO, VLC, etc.)?

---

### Post by drs305 on 2010-05-17
You could move your /home to a separate partition to save (many of) your configuration settings, but the remainder of the / partition will be overwritten by the new release. 

If you have or make a separate /home, make sure you choose manual partitioning, designate the /home partition, and DO NOT format it.

Although they will be replaced, you could copy folders such as /etc and /boot, which contain configuration files, to a backup partition. You can't restore them, but you could access them after the install to review old settings from your previous install.

---

