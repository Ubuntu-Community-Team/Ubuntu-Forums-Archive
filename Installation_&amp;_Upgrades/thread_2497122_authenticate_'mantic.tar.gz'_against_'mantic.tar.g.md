---
title: "authenticate 'mantic.tar.gz' against 'mantic.tar.gz.gpg'"
date: 2024-04-23
forum: Installation &amp; Upgrades
---

### Post by normlewis on 2024-04-23
On a new install of Ubuntu server 22, I'm trying to upgrade but keep getting the following;

> 
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:        22.04
Codename:       jammy

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <KEY_ID>
sudo apt-get install --reinstall ubuntu-keyring
sudo apt-key update

Continue [yN] y
Get:1 Upgrade tool signature [833 B]
Get:2 Upgrade tool [1,271 kB]
Fetched 1,272 kB in 0s (0 B/s)
authenticate 'mantic.tar.gz' against 'mantic.tar.gz.gpg'
Authentication failed



Hours of searching and I cannot find a solution. Does anyone know how I can get past this?

---

### Post by normlewis on 2024-04-24
I see the board I'm using is having a problem with communications. 
Is it possible the upgrade is failing with a generic message that is really about my board not being able to reliably connect?

---

