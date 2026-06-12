---
title: "Problems Updating Ubuntu 7.04"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by james.cr on 2007-08-28
Hi I want to install alien in my computer but I'm having some problems with the update, that's the error:

jgutierrez@Coffea:~$ sudo apt-get install alien
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing language-pack-is (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


thanks,
jaime.

---

### Post by bobbybobington on 2007-08-28
That sounds like a problem with the packages and apt, not your computer. I found a workaround and hopefully it works.

```
$ sudo apt-get update -o APT::Cache-Limit=25165824
```

---

