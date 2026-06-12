---
title: "Network error in upgrading Gutsy to Hardy"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by personjerry on 2008-05-29
I'm having some troubles. The error is in the second step on the list of upgrading, it says it can't access the ubuntu pages.

So the list of steps is:

Preparing to Upgrade
Setting new software Channels
Getting new packages
Installing the upgrades
Cleaning up
Restarting the computer

At "Preparing to upgrade, at package 28 out of 37 it waits a long time, then tells me that in my sources.list file third party sources have been disabled.

Then at "Setting new software channels", at package 15 out of 24 it waits a long time, then says "0 seconds remaining". After that it says

"Error during update"

"A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry."

"Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out"


Please help me!!!
"

---

### Post by personjerry on 2008-06-01
bump

---

### Post by prshah on 2008-06-03
> **personjerry said:**
> I'm having some troubles. The error is in the second step on the list of upgrading, it says it can't access the ubuntu pages.

"Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out"


In gutsy, open Applications-Add/Remove, then click the "Preferences" button in the bottom left corner. If you can't find that, just open System-Administration-Software Sources. In the first tab, change your download server to "Main Server". OK, exit, etc.

Then try upgrading.

A "alternate" suggestion: get the "alternate" cd image for hardy, then pop it in the drive, and choose "upgrade" when asked. Since all packages are already present on the CD, the upgrade will not need to download anything and will finish faster. You can then download all updates thru update-manager.

---

### Post by personjerry on 2008-06-04
It worked! Thanks!!

---

