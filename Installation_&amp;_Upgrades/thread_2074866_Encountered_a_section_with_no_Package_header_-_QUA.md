---
title: "Encountered a section with no Package: header - QUANTAL"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by AtomikBioHazard on 2012-10-22
I just upgraded my ubuntu to the new 12.10 version and I've been having this problem whenever the system or I try to update the packages either trough the synaptic or the terminal and the system give's me this error message:

Problem with MergeList /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Does any one have any idea how to solve this? 

Thx for your help

---

### Post by plucky on 2012-10-22
> **AtomikBioHazard said:**
> I just upgraded my ubuntu to the new 12.10 version and I've been having this problem whenever the system or I try to update the packages either trough the synaptic or the terminal and the system give's me this error message:

Problem with MergeList /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Does any one have any idea how to solve this? 

Thx for your help

Open a terminal and run ```
sudo rm /var/lib/apt/lists/* -vf
``` to delete the list files and then run ```
sudo apt-get update
``` to reload the list files.

If problem occurs again,change your download server in **Software Sources** and run the two commands again.


Good Luck

---

### Post by AtomikBioHazard on 2012-10-22
Thanks plucky that went perfectly well with out changing the download server.

---

