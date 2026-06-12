---
title: "unable to access repositories?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Locuss on 2007-04-20
Well, I tried to update to Feisty yesterday, was pretty excited. And I ran into some problems. After a bit of testing, and alternate commands, I came up with this:

sudo apt-get update
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [189B]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_CA
Get:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_CA
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_CA
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_CA
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Fetched 381B in 1s (305B/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Reading package lists... Done


Thats what I get when I just try a simple sudo apt-get update. My upgrade keeps failing because it cannot connect with ca.archive.ubuntu.com, and I know that part way through the upgrade, the upgrader said it changed my repository list.

What do I do?

---

### Post by Locuss on 2007-04-20
Please help, guys?

---

### Post by skip27 on 2007-04-20
I think the servers are just victim to high traffic, since I presume everyone is trying to upgrade. I can't access most of the repos, either. Unless they've simply changed servers and I didn't get the memo, wait a few days (yeah, it sucks). Things will be back to normal.

EDIT: Here's a temporary workaround for apt-get/Synaptic. Go to Settings -> Repositories and change "Download from:" to "Main server" instead of "Server for United States." I'll try dist-upgrading now...

---

### Post by Locuss on 2007-04-20
Thanks!

---

### Post by skip27 on 2007-04-20
This seems to have got it! Upgrading now.

---

### Post by tjk on 2007-04-20
Hmm...  Didn't work for me...  I guess the repositories are just too busy??  I'll just have to wait a few days/weeks until I upgrade. <sigh>

---

