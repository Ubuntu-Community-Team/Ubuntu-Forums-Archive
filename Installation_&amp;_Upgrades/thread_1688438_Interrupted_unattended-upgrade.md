---
title: "Interrupted unattended-upgrade"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Chris1492 on 2011-02-15
Hello Ubuntu people

A client's laptop, running Ubuntu 10.4, suddenly lost its wifi a few days ago.

It turned out that unattended-upgrades had installed a new kernel version, but had then been interrupted before the installation was complete.  Possibly the user had switched off the laptop in the middle of the update process.

All that was required to fix the problem was 'dpkg --configure -a'.

So I'm looking for a way to stop this happening again.

Would running 'dpkg --configure -a' via cron at every boot be over the top?  Would it cause other problems?

cheers

Chris

---

