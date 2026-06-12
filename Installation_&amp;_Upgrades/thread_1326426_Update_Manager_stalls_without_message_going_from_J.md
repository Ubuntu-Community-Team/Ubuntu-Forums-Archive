---
title: "Update Manager stalls without message going from Jaunty to Karmic."
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by shof2k on 2009-11-14
Hi,
Tried to use update manager to upgrade from Jaunty to Karmic, however, it would stop without any messages after it had asked for my password.  Running through the terminal and doing some googling, came across  [Bug 461744]("https://bugs.launchpad.net/ubuntu/karmic/+source/update-manager/+bug/461744/").

The problem is that I had set my /tmp to use the noexec option for performance, but update manager cannot handle this. 

I edited /etc/fstab to remove the option, rebooted, and upgraded successfully.  The report mentions a fix for Karmic and Lucid, but I've requested it be backported to Jaunty otherwise it stops an upgrade path.

Hope this helps, Peace

---

