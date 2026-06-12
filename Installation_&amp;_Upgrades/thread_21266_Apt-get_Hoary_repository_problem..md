---
title: "Apt-get Hoary repository problem."
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by Mase Track on 2005-03-21
I've updated my apt-get sources list to Hoary, however when I run an upgrade or synaptic, or the gnome update manager I get this error(?). Ive copy and pasted from apt-get.

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

Creating this directory manually also causes an error.

any help would be appreciated

---

### Post by c_dog on 2005-03-21
As noted in the default /etc/apt/sources.list file these two repositories are for updates after Hoary has been released. Hoary hasn't been released yet.  Disable them for now (or at least until after April 6th).

---

