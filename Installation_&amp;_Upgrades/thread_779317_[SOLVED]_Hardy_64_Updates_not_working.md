---
title: "[SOLVED] Hardy 64 Updates not working"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by ztirffritz on 2008-05-02
I have a fresh installation of Hardy 64.  Updates fail with the following error from Update Manager:

*****************************
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
******************************

Anyone know how to resolve this?  I've tried apt-get update, synaptic, and a few other standard solutions, but all generate the same or similar error.

---

### Post by ztirffritz on 2008-05-02
I filed a bug report too, so if anyone wants to latch onto that, feel free.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/225830](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/225830)

---

### Post by ztirffritz on 2008-05-03
I think that I solved it, then I completely broke it.  I need to use the 64bit version, but it is like tip-toeing through a minefield trying to get it to work.

I started out be finding the offending file in /var/apt/lists/ and deleting it.  I don't know if that was the right thing to do or not, but it made the error message go away, I could install files again, and it even found a pair of updates that had been pushed out.  Then I rebooted.  Just to make sure that things were still working, I tried to install a game and the system locked up.  I rebooted again and it said that the drive was corrupted.  FSCK failed, so re-install for the 37 time.  (Yes, I've been counting)  You know that Windows is bad when you're willing to to this so many times to get it right.

---

### Post by ztirffritz on 2008-05-30
Bad RAM was the culprit.  It was working sporadically and corrupting things.

---

