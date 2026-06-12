---
title: "rpm manager?"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2013-08-16
Hi
currently updating 13.04 and it downloads also rpm manager? What it that used for?
Thanks

---

### Post by vasa1 on 2013-08-16
> **MikeCyber said:**
> Hi
currently updating 13.04 and it downloads also rpm manager? What it that used for?
Thanks
What is the actual name of the package? I ran `apt-cache search rpm` and there are quite a few hits. One is plain "rpm". Then, running `apt-cache show rpm` gives
> Description-en: package manager for RPM
 The RPM Package Manager (RPM) is a command-line driven package
 management system capable of installing, uninstalling, verifying,
 querying, and updating computer software packages.
 .
 On Debian and derived systems it is recommended to use "alien" to
 convert RPM packages into .deb format instead of bypassing the Debian
 package management system by installing them directly with rpm.
Homepage: [http://rpm.org/](http://rpm.org/)

I don't see it as being installed on my system but I know that a lot of software is actually installed as part of the set-up procedure and then later on automatically removed before the installation process is completed so you might not see it later on when your system is up and running..

---

### Post by vasa1 on 2013-08-16
Also see: [http://askubuntu.com/q/324303/25656](http://askubuntu.com/q/324303/25656)

---

