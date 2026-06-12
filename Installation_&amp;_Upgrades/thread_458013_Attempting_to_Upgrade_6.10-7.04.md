---
title: "Attempting to Upgrade 6.10-7.04"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by SangreDeThor on 2007-05-29
As per following the instructions and using update manager i get the following error:
> Failed to fetch [http://malteo.homelinux.net/dists/edgy-malteo/Release.gpg](http://malteo.homelinux.net/dists/edgy-malteo/Release.gpg) Could not connect to malteo.homelinux.net:80 (84.220.158.45). - connect (111 Connection refused)
Failed to fetch [http://malteo.homelinux.net/dists/edgy-malteo/all/i18n/Translation-en_US.bz2](http://malteo.homelinux.net/dists/edgy-malteo/all/i18n/Translation-en_US.bz2) Could not connect to malteo.homelinux.net:80 (84.220.158.45). - connect (111 Connection refused)
Failed to fetch [http://thomas.enix.org/pub/debian/packages/dists/edgy/main/binary-i386/Packages.gz](http://thomas.enix.org/pub/debian/packages/dists/edgy/main/binary-i386/Packages.gz) 302 Found
Any suggestions? thanks

---

### Post by The Fold on 2007-05-29
homelinux.net resolves to a dyndns redirect. My guess is whoever is running that particular repository is either not on that IP anymore or has their machine switched off.

---

### Post by SangreDeThor on 2007-05-29
I still can not update. So how can i do the update over the network then since those repos are down? am i forced to use the CD upgrade?

---

### Post by RevNL on 2007-05-29
Edit /etc/apt/sources.list and comment out the matching lines.  Then update.

---

### Post by SangreDeThor on 2007-05-29
but those lines were used for something.. Couldn't they be important?

*EDIT* actually just looked at the file and saw they were for non-key programs *EDIT*

---

