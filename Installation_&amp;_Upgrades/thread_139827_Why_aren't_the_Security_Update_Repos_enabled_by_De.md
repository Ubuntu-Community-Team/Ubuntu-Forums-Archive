---
title: "Why aren't the Security Update Repos enabled by Default"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by Maverick88 on 2006-03-04
I just installed Breezy Badger and noticed that the following lines in /etc/apt/sources.list are commented out:

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Why are the Security Updates Repos NOT enabled by default?
Should I uncomment these lines and enable them?

Rob

---

### Post by weijie90 on 2006-03-04
yes, do uncomment them and run sudo apt-get update and sudo apt-get upgrade to get the security fixes for ubuntu.

---

