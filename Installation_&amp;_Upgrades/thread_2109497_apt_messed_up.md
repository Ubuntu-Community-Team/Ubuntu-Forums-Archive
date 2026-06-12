---
title: "apt messed up"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by lavacano on 2013-01-27
My bash history to get apt is:

```
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_restricted_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-updates_main_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-updates_multiverse_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-updates_restricted_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-updates_universe_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-backports_main_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-backports_multiverse_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-backports_restricted_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-backports_universe_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-security_main_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-security_multiverse_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-security_restricted_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-security_universe_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-proposed_multiverse_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-proposed_restricted_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-proposed_universe_i18n_Translation-en%5fUS
apt-get upgrade
rm /var/lib/apt/lists/ppa.launchpad.net_ehoover_compholio_ubuntu_dists_quantal_main_i18n_Translation-en

```


Every time I run apt-get update these files spit out errors.

---

