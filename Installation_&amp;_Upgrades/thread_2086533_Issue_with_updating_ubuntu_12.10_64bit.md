---
title: "Issue with updating ubuntu 12.10 64bit"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2012-11-21
[B]W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/restricted/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/restricted/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/restricted/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/restricted/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/universe/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/universe/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal/universe/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal/universe/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/i18n/Translation-en_SG](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/i18n/Translation-en_SG)  Connection failed

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/i18n/Translation-en)  Connection failed


[/B]Any help please :-(

---

### Post by zvacet on 2012-11-22
Under Ubuntu software center>edit >software repositories change server to main and see if that helps.

---

### Post by vksingh on 2012-11-29
I changed the sg.archive.....* to us.archive.....* and its working fine. Thanks :-)

---

