---
title: "[SOLVED] Partial upgrade to Hardy... HELP!"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by lost09 on 2008-06-17
Due to a shoddy internet connection, upgrading from Ubuntu 7.10 to 8.04 was aborted partway through. I started this process by going through Update Manager, which said that "8.04 is available" (or something along those lines). However, I suspect because of the degree to which the update was completed, Update Manager now says "your system is up to date", despite the fact that I am still stuck with 7.10 (which I checked via "cat /etc/lsb-release").

I desperately need to upgrade... soon. Any help would be infinitely appreciated.

---

### Post by Pumalite on 2008-06-17
You might want to try this:
sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade


Make sure your Gutsy is totally updated before you attempt the upgrade.

---

### Post by circusmonkey on 2008-06-17
Forget it , do a clean fresh install , I have had the update fail twice and completely wreck 7.10 .Be prepared to manually connect yourself to the Internet also.

CM

---

### Post by Pumalite on 2008-06-17
Clean install is always better, but upgrades work if well done.

---

### Post by lost09 on 2008-06-18
For a clean install of Hardy, I need the live CD, correct? Anyone know where to find one?

---

### Post by lost09 on 2008-06-18
Everything I've read seems to say that Gutsy must be completely up to date for the upgrade to work; though Update Manager claims that I'm up to date, I keep getting "GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783" every time I run "sudo apt-get update". However, I've moved on to "sudo apt-get dist-upgrade", which seems to be working. 

I don't know where to get a Hardy CD, so I may have to upgrade via internet if possible.

---

### Post by lost09 on 2008-06-19
This seems to have worked:

> sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

Through some miracle I managed to keep a connection overnight, and am now running (I think) Hardy. Thanks!

---

