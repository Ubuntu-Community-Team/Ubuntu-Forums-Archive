---
title: "How to show Lubuntu logo/startup icon?"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by bill101 on 2016-04-24
Since upgrade to 16.04, the Lubuntu startup icon no longer appears.  I simply have a blank screen until I hit the Lubuntu default background at the prompt for user login/password.  Thus, is there a way to bring back the Lubuntu icon with the crawling dots (while grub processes)?  I assume its something configurable in Grub?  Additionally, is there something similar for shutdown?

thx!

Bill

---

### Post by Dennis N on 2016-04-24
There is a bug report about this:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707)
For 2016 reports - see posts #17 and on.
I see the same problem.

---

### Post by Dennis N on 2016-04-25
I found the cause and a solution in cases where a new install of Lubuntu 16.04 was done (not an in-place upgrade). The details are here:
[http://ubuntuforums.org/showthread.php?t=2321997&p=13477423#post13477423](http://ubuntuforums.org/showthread.php?t=2321997&p=13477423#post13477423)

(If you did an in-place upgrade, then the user who started the linked thread says that a different kernel solved his problem. See the thread.)

---

