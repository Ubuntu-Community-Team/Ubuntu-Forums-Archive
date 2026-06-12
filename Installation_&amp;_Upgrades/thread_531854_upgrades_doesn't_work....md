---
title: "upgrades doesn't work..."
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by sreejithr on 2007-08-22
~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  compiz-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/186kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-core
Install these packages without verification [y/N]? y
(Reading database ... 105595 files and directories currently installed.)
Preparing to replace compiz-core 1:0.5.2-0ubuntu3~ppa4 (using .../compiz-core_1%3a0.5.2-0ubuntu3~ppa4_i386.deb) ...
Unpacking replacement compiz-core ...
Setting up compiz-core (0.5.2-0ubuntu3~ppa4) ...


and then stops...and never installs the file...i tried the manager and terminal and both dont work...any ideas??

---

### Post by ThrobbingBrain66 on 2007-08-22
I've read some posts recently where the PPA Dogfood repo was having some troubles. Specifically repeatedly offering an update that has already been installed.  Looks like this is just another issue.  If you wish, you can either switch to Vorian's or Trevino's Compiz repo.

[http://vorian.org/?p=82](http://vorian.org/?p=82)
[http://compiz.org/Compiz_and_Compiz_Fusion_GIT_Ubuntu_Repository](http://compiz.org/Compiz_and_Compiz_Fusion_GIT_Ubuntu_Repository)

---

### Post by sreejithr on 2007-08-22
too late reinstalled...tks for the help thou..

---

