---
title: "Installation of KDE blows package"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by mgw2008 on 2010-03-06
After installation of the Kubuntu desktop via aptitude I get the following error from synaptics et al:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_karmic_main_i18n_Translation-de

What do I need to do to resolve this issue?

---

### Post by mgw2008 on 2010-03-06
Killed update was the reason...

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-get clean
sudo apt-get update
sudo mv /etc/apt/sources.list.old /etc/apt sources.list
sudo apt-get update 

did the trick

---

