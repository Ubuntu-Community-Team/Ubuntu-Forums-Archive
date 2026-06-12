---
title: "timeout error while trying to upgrade to feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by radioactivebug on 2007-04-21
So I start the upgrade to Feisty, and it gets to the first part where it says "preparing the upgrade" and it starts downloading files. It gets to a point where it says "fetching file 94 of 96" then it just sits there, it might restart this process a few times, but it always stops at 94, until eventually it gives up and gives me this message:

Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/plf/dists/edgy/Release.gpg) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy/free/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out

then the upgrade process exits out. Any ideas? I thought originally it was just because the servers where under stress, but I've tried this 7 or 8 times in the last few days and it always stops at the same time.

---

### Post by DougieFresh4U on 2007-04-21
I would comment out those lines in the sources list (##)  then save and close sources list and then do **sudo apt-get update** then **sudo apt-get dist-upgrade **

---

### Post by radioactivebug on 2007-04-21
Ah, brilliant. I probably should have seen that. But anyways, it worked like a charm. Thanks.

---

### Post by DougieFresh4U on 2007-04-21
Glad I could help!!:) :)

---

