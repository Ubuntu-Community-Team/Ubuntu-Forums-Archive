---
title: "Upgrade aborted"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Terrycymru on 2010-03-10
I have just tried a distribution upgrade from Karmic to Lucid. Download went ago OK but once it got to installation stage the upgrade was aborted with the error message below. A partial upgrade was recommended but this made no difference. 

Error:root:Exception during pm.DoInstall()
Traceback (most recent call list):
File "/usr/lib/python2.6/dist-packages/DistUpgradeView.py", line182, in run
res=pm.DoInstall (self.write.fd)
SystemError: E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle

How can I fix this?

---

### Post by dino99 on 2010-03-10
into console, step by step:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

open your sources.list and check every line : 
  - comment all extra-repo (like ppa), only original Lucid repos might be active.
  - be sure that everything is well written (with space, and /)
  - save and exit.

sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade

---

### Post by slakkie on 2010-03-10
Remove openoffice.org-filter-binfilter and try again, if that keeps giving problems try removing the other openoffice packages as well, upgrade and install them again.

There is no need to clear your cache and check ppa's if you use update-manager/do-release-upgrade.

---

### Post by Terrycymru on 2010-03-10
Thanks guys. Removing openoffice allowed installation to proceed.

---

### Post by Terrycymru on 2010-03-10
> **Terrycymru said:**
> Thanks guys. Removing openoffice allowed installation to proceed.

But....although Synaptic shows openoffice present it is not available in menus.

---

### Post by slakkie on 2010-03-10
What does 'apt-cache policy openoffice.org' say (run it in the terminal)?

---

### Post by Terrycymru on 2010-03-10
> **slakkie said:**
> What does 'apt-cache policy openoffice.org' say (run it in the terminal)?

me@ubuntu:~$ apt-cache policy openoffice.org
openoffice.org:
  Installed: (none)
  Candidate: 1:3.2.0~rc4-1ubuntu1
  Version table:
     1:3.2.0~rc4-1ubuntu1 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages

---

### Post by slakkie on 2010-03-10
You don't have it installed, try to install it.

---

### Post by Terrycymru on 2010-03-10
Thanks slakkie. Installed now and everything is OK.

---

