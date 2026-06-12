---
title: "tool to show repository packages"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-01-23
Is there a tool that, given a repository URL, will show all the packages at that repository?  If it can fetch package descriptions, that's even better.

To clarity, I want more than just "apt-get update".  I want to do this intentionally without adding such a repository to my sources.list (it is in part decide if I want to add it or not).  What I'd expect as a result is a file with a list of package names (maybe with a short description on each line), and maybe another file with the full descriptions.

---

### Post by cortman on 2012-01-24
Don't all repositories have a zipped Packages file? That usually contains an ASCII text file with lists and descriptions of packages in the repo.
That's the way it is with the Ubuntu repositories, anyway.

---

### Post by bluexrider on 2012-01-24
Try Y PPA launchpad manager [https://launchpad.net/y-ppa-manager](https://launchpad.net/y-ppa-manager)

also [http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

---

