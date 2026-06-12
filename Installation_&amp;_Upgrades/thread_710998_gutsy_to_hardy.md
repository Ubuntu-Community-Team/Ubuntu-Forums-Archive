---
title: "gutsy to hardy"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2008-02-29
I'm currently running Gutsy on a dell notebook, works great.  Just to have a look, I downloaded the Hardy live cd to have a look, ran it yesterday but did not install anything.  Now update-manager and synaptic want to install 11 new packages from the hardy cd.  Is there an easy way to stop and correct this?  I do want to upgrade at some point in the future, but not yet?

Thanks

Jim

---

### Post by Rocket2DMn on 2008-02-29
Is the CD being used as a repository?  Check is System->Adminstration->Software Sources.  Otherwise please post your sources.list file
```
cat /etc/apt/sources.list
```
If there is no hardy stuff in there, run
```
sudo apt-get update
sudo apt-get upgrade -s
```
The -s will make it simulate an upgrade (not a dist-upgrade).

---

### Post by jamaas on 2008-02-29
Thanks Rocket2DMn

I did have a look in the repositories and the new hardy cd had been added.  Removed it, rebooted, and all is well, got 8 new updates which worked fine and no further problems. 

Thanks a bunch.

Jim


> **Rocket2DMn said:**
> Is the CD being used as a repository?  Check is System->Adminstration->Software Sources.  Otherwise please post your sources.list file
```
cat /etc/apt/sources.list
```
If there is no hardy stuff in there, run
```
sudo apt-get update
sudo apt-get upgrade -s
```
The -s will make it simulate an upgrade (not a dist-upgrade).

---

