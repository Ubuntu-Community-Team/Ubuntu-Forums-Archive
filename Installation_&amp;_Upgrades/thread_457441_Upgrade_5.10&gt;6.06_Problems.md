---
title: "Upgrade 5.10&gt;6.06 Problems"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by mejohnsn on 2007-05-28
Following the instructsion in the Sticky Threads, no matter which option I choose, I quickly run into problems. If, for example, I try System>Administration>Update Manager, I am told that no updates are available, even though I am also told 5.10 is no longer supported, so I have to upgrade. Following the instructions shows I need 0.42 version of the Update Manager, but Synaptics Package Manager will not offer the update, pretending that 0.37 is the last available.

So I tried following the instructions for doing the upgrade by editing sources.list. But the first thing it says to do is remove xscreensaver, which produces the following flurry of error messages, leading me to believe that the paths to the souces are out of date:
sudo apt-get remove xscreensaver
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ubuntu-desktop xscreensaver
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2331kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 56660 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing xscreensaver ...
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

So what should I do? And why are the instructions saying to use these paths if they are out of date?

---

