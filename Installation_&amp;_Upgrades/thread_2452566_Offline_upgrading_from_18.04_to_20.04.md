---
title: "Offline upgrading from 18.04 to 20.04"
date: 2020-10-24
forum: Installation &amp; Upgrades
---

### Post by axel-heyst on 2020-10-24
Hi

I have a simple question - is it possible to perform this upgrade offline (desktop version)? I mean - to download proper ISO first and then do the upgrade. I'm asking because I have poor network connection (only LTE/3G) and I'm afraid that standard upgrade might be interrupted. I understand that afterwards still I'd have to do the update of the packages but all of that would happen on the new system. In my view it would be a safer procedure. Thank you for any help.

Best regards

---

### Post by grahammechanical on 2020-10-24
This is an old wiki page that explains how to set up an off-line set of repositories. It might still be useful.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I suggest that you take 18.04 back to a basic install. I am also wondering if a fresh install without having updates during the installation process would be safest . Downloading a ISO image might use less data and take less time than an On-line upgrade.

Regards.

---

### Post by GhX6GZMB on 2020-10-24
In my experience, you're looking at a new install, not an OS upgrade. Already an online upgrade is hairy. Unfortunately, you don not say which flavour you'using.

---

### Post by axel-heyst on 2020-10-25
Thanks for the answers. I'm using [Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)] and I'm looking for the upgrade. What about doing some tricks like replacing "http://PATH_TO_REPOSITORY" with "file://PATH_TO_DOWNLOADED_PACKAGES" somewhere in the file defining repositories ("/etc/apt/sources.list" or maybe another one)? Can it be feasible?

---

