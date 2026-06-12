---
title: "problem parsing dependency"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by pacice on 2008-10-16
Trying to update my packages, but I keep getting the following error.
I think it may be something related to having missing dependencies, but not sure what to do about it.

suggestions welcome.

E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


PROBLEM SOLVED
unticked repoubuntusoftware.hardy_all from my software sources, and problem solved.

Can also be done by editing sources.list
sudo gedit /etc/apt/sources.list

also see
[http://ubuntuforums.org/showthread.php?t=945926&highlight=problem+parsing+dependency](http://ubuntuforums.org/showthread.php?t=945926&highlight=problem+parsing+dependency)

---

