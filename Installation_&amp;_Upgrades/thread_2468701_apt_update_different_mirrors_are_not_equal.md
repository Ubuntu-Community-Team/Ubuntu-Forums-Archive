---
title: "apt update different mirrors are not equal"
date: 2021-11-08
forum: Installation &amp; Upgrades
---

### Post by pharmya on 2021-11-08
Hello, i am running 2 Ubuntu 18.04.6 LTS installs. I upgraded the first install and noticed a new version of linux-generic:
linux-generic/bionic-updates,now 4.15.0.**162.151** amd64
The other install says linux-generic up to date but version is:
linux-generic/bionic-updates,bionic-security,now 4.15.0.**161.150** amd64 [installed]

On both installs i executed apt update.
I noticed the first install shows:
Hit:1 [http://nginx.org/packages/ubuntu](http://nginx.org/packages/ubuntu) bionic InRelease
Hit:2 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) bionic-pgdg InRelease
Hit:3 [http://ppa.launchpad.net/linbit/linbit-drbd9-stack/ubuntu](http://ppa.launchpad.net/linbit/linbit-drbd9-stack/ubuntu) bionic InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease

and second install:
Hit:1 [http://ppa.launchpad.net/linbit/linbit-drbd9-stack/ubuntu](http://ppa.launchpad.net/linbit/linbit-drbd9-stack/ubuntu) bionic InRelease
Hit:2 [http://nginx.org/packages/ubuntu](http://nginx.org/packages/ubuntu) bionic InRelease
Hit:3 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:5 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:6 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-security InRelease
Hit:7 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) bionic-pgdg InRelease


So it seems the French mirror does not have 4.15.0.**162.151**

I checked [http://fr.archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/bionic-updates/main/binary-amd64/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/bionic-updates/main/binary-amd64/Packages.gz) and the current version is :
Package: linux-generic
Architecture: amd64
Version: 4.15.0.161.150

Why the mirrors have different versions?

---

### Post by ActionParsnip on 2021-11-08
Its probably just not updated yet. It will come in time.

---

