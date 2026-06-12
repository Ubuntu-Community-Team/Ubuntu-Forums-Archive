---
title: "Update Manager will not run"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by Griffen07 on 2012-06-12
I installed ubuntu last night.  I could not connect to install the updates.  When I ran update manager today I got this message

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

How do I fix it?

---

### Post by wojox on 2012-06-12
Run this command:
```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

---

### Post by Griffen07 on 2012-06-12
that promoted this response

Code
 rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release.gpg': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index': Permission denied
rm: cannot remove `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en': Permission denied
rm: cannot remove `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources': Permission denied
rm: cannot remove `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release': Permission denied
rm: cannot remove `/var/lib/apt/lists/lock': Permission denied
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages.IndexDiff': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages.IndexDiff': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en': Permission denied
rm: cannot remove `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources': Permission denied
rm: cannot remove `/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20i386%20(20120423)_dists_precise_main_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20i386%20(20120423)_dists_precise_Release': Permission denied
rm: cannot remove `/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20i386%20(20120423)_dists_precise_Release.gpg': Permission denied
rm: cannot remove `/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20i386%20(20120423)_dists_precise_restricted_binary-i386_Packages': Permission denied
rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release': Permission denied
rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_Release': Permission denied
rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release': Permission denied

---

### Post by Griffen07 on 2012-06-12
The issue has been fixed.  I found the solution in the Launch Pad questions.  
This command sequence solved the issue.  

sudo fuser -vvv /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/lock
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists
sudo rm /var/cache/apt/*.bin
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
LANG=C;sudo apt-get clean
LANG=C;sudo apt-get autoclean
LANG=C;sudo apt-get --purge autoremove
LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
sudo dpkg --clear-avail
sudo dpkg --configure -a
LANG=C;sudo apt-get -f install
LANG=C;sudo apt-get --fix-missing install
LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade

---

### Post by askar11 on 2012-06-14
My issue was resolved with this command : sudo rm /var/lib/apt/lists/* -vf

---

### Post by mkshantilal on 2012-10-13
I am getting the following error when I try to update my software inUbuntu 12.04, can I use the same method shown above to fix it? It is slightly different than the originally posted.


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Regards, 
mkshantilal

---

### Post by bartekklimczak on 2013-01-15
thanks a bunchkin, 

worked like a charm!

best
BK

---

### Post by kayakchris on 2013-03-26
post #2 worked for me

Cheers
Chris

---

