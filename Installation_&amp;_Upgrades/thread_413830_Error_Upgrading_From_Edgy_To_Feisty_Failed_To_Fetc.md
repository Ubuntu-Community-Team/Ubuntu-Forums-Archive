---
title: "Error Upgrading From Edgy To Feisty: Failed To Fetch"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by eheitner on 2007-04-19
When upgrading from Edgy to Feist using update manager, I get the following after the install has been running for a while:

Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/plf/dists/edgy/Release.gpg) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/main/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy/main/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy/restricted/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/universe/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy/universe/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy/multiverse/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)


******

My network connection is fine. Why are these connections timing out?

---

### Post by Honayo on 2007-04-19
> My network connection is fine. Why are these connections timing out?

Ubuntu servers are being slammed today by people like you and me trying to update, upgrade and download.

I got Kubuntu Feisty downloaded about 8 am my time but the iso is corrupt. I'll just wait till things slow down.:)

---

### Post by darrowconley on 2007-04-19
I got something similar. I just restarted it and it fetched them all the second time.

I will give the servers a few days before I DL it.

---

### Post by Mets on 2007-04-19
I got the same error - what in the world are they doing over there in French land.  The main site still works, the blog works, but the server doesn't?

---

### Post by boralyl on 2007-04-19
I also had the same error last night, yet somehow got lucky during the day today and was able to completely upgrade.  I would just give it a few days before you upgrade since I am sure the servers are getting hit hard.

---

### Post by eyelessfade on 2007-04-19
That is because the blog/forum are not on the same servers as the install files.

if thousands try to connect to the same server at the same time, most will not handle the stress and go down.

try in a few hours, or change download mirror. Or you can download the iso file with bittorrent and add that to the source.list. And upgrade from the cd.

---

### Post by hanzomon4 on 2007-04-19
> **eyelessfade said:**
> That is because the blog/forum are not on the same servers as the install files.

if thousands try to connect to the same server at the same time, most will not handle the stress and go down.

try in a few hours, or change download mirror. Or you can download the iso file with bittorrent and add that to the source.list. And upgrade from the cd.

How do you add the install cd......

---

