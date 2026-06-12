---
title: "section header problem in synaptic"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by mirinamulhaq on 2011-05-11
hello,
every time i try to open Synaptic i am getting following error
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_maverick_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)

however i can temporarily solve the problem using
sudo rm /var/lib/apt/lists/* -vf
apt-get update
but after restarting the computer i again get the same problem
any help will be appreciated

---

