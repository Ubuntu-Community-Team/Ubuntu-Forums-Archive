---
title: "Corrupt xenial_main_binary-i386 file"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by drphysic2033 on 2016-05-03
I just upgraded this morning to 16.04 Xubuntu, and after some issues with "sources.list" entries, I am left with this problem:

The file '/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages'

reports the issue below when trying to do an "apt-get-update", or running the Package Manager (note Software Updater does not run at all):

E: Problem parsing dependency Recommends
E: Error occurred while processing fcitx-frontend-all (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I tried to use gedit to look into the file, I got a warning that the file contained invalid characters. Can I regenerate this file or is there some other method to correct the problem?

drphysic

---

### Post by oldos2er on 2016-05-03
Try ```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages

sudo apt-get update
```

---

### Post by drphysic2033 on 2016-05-03
Thanks for confirming that removal would help, but didn't realize that it would then allow all the rest to function correctly. Issue appears resolved. Thanks  
drphysic

---

