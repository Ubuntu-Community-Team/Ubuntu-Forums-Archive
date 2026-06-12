---
title: "apt-get error"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by .Michael on 2008-10-17
Whenever I try to do anything with aptitude, it throws this error:

> root@ubuntuadm-desktop:~# apt-get install mousepad
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty
_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
root@ubuntuadm-desktop:~#

I also tried apt-get update
I am running this remotely thru ssh, if that affects it any. (I su'd to get to root)

---

### Post by ShinobiTeno on 2008-10-17
Maybe the update server is down.. Tried to use other mirror?
Other thing..:
/var/lib/apt/lists/repoubuntusoftware.info_dists_har**d**y
_all_binary-i386_Packages

---

### Post by cariboo on 2008-10-17
The Ultimate Linux repositories have been down since October 13th. If you don't want to see the error message again, comment out all the Ultimax repositories and uncomment the repositories that were commented out when you set up the Ultimate Linux repositories.

Jim

---

