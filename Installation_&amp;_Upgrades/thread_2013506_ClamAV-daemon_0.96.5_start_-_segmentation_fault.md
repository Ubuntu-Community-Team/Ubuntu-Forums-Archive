---
title: "ClamAV-daemon 0.96.5 start - segmentation fault"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by robinnelu on 2012-06-30
I was running clamav daemon on Ubuntu 10.04 for many months and then I did an apt-get update followed by an upgrade recently. I cannot be sure if the clamav updates caused it, but now the daemon will not start. I get Segmentation fault when trying to run: sudo /etc/init.d/clamav-daemon start. I understand that the version is out of date, which is typical because I install what Ubuntu has available and that is not always the most current. I am currently running 0.96.5

I have tried the following to resolve this:
Sudo add-apt-repository ppa:ubuntu-clamav/ppa (to upgrade outside of what Ubuntu offers). When I go to Ubuntu Software Center there is an item on left called PPA for Clamav Update Team. Selecting that only shows one option: to install “clamAV interface for PHP Scripts” (php-clamav) which is not something I need or want. I was hoping the add-apt-repository would help me to upgrade clamav, am I missing a step?

I’ve also tried:
Sudo dpkg-reconfigure clamav-daemon (get same segmentation fault error)


My recent update logs for apt get are as follows:


Start-Date: 2012-06-22  06:48:48
Upgrade: apt-transport-https (0.7.25.3ubuntu9.11, 0.7.25.3ubuntu9.13), adobe-flash-properties-gtk (11.2.202.235-0lucid1, 11.2.202.236-0lucid1), clamav (0.96.5+dfsg-1ubuntu1.10.04.3, 0.96.5+dfsg-1ubuntu1.10.04.4), libecal1.2-7 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), libapparmor-perl (2.5.1-0ubuntu0.10.04.3, 2.5.1-0ubuntu0.10.04.4), libgdata-google1.2-1 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), libedata-cal1.2-6 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), clamav-base (0.96.5+dfsg-1ubuntu1.10.04.3, 0.96.5+dfsg-1ubuntu1.10.04.4), libclamav6 (0.96.5+dfsg-1ubuntu1.10.04.3, 0.96.5+dfsg-1ubuntu1.10.04.4), libmysqlclient16 (5.1.62-0ubuntu0.10.04.1, 5.1.63-0ubuntu0.10.04.1), apt-utils (0.7.25.3ubuntu9.11, 0.7.25.3ubuntu9.13), apt (0.7.25.3ubuntu9.11, 0.7.25.3ubuntu9.13), firefox (13.0+build1-0ubuntu0.10.04.1, 13.0.1+build1-0ubuntu0.10.04.1), apparmor-utils (2.5.1-0ubuntu0.10.04.3, 2.5.1-0ubuntu0.10.04.4), linux-headers-2.6.32-41 (2.6.32-41.89, 2.6.32-41.90), libedataserverui1.2-8 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), libedata-book1.2-2 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), libegroupwise1.2-13 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), libexchange-storage1.2-3 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), linux-image-2.6.32-41-generic (2.6.32-41.89, 2.6.32-41.90), libapparmor1 (2.5.1-0ubuntu0.10.04.3, 2.5.1-0ubuntu0.10.04.4), clamav-freshclam (0.96.5+dfsg-1ubuntu1.10.04.3, 0.96.5+dfsg-1ubuntu1.10.04.4), apparmor (2.5.1-0ubuntu0.10.04.3, 2.5.1-0ubuntu0.10.04.4), libcamel1.2-14 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), evolution-data-server-common (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), libraptor1 (1.4.21-1ubuntu1, 1.4.21-1ubuntu1.1), evolution-data-server (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), linux-libc-dev (2.6.32-41.89, 2.6.32-41.90), libebackend1.2-0 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), clamav-daemon (0.96.5+dfsg-1ubuntu1.10.04.3, 0.96.5+dfsg-1ubuntu1.10.04.4), libgdata1.2-1 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), linux-headers-2.6.32-41-generic (2.6.32-41.89, 2.6.32-41.90), mysql-common (5.1.62-0ubuntu0.10.04.1, 5.1.63-0ubuntu0.10.04.1), firefox-gnome-support (13.0+build1-0ubuntu0.10.04.1, 13.0.1+build1-0ubuntu0.10.04.1), libedataserver1.2-11 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6), adobe-flashplugin (11.2.202.235-0lucid1, 11.2.202.236-0lucid1), libebook1.2-9 (2.28.3.1-0ubuntu5, 2.28.3.1-0ubuntu6)

---

### Post by emmenlau on 2013-01-18
Same problem here, did you find a solution?

~> lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

~> apt-show-versions|grep clam
clamav/lucid uptodate 0.96.5+dfsg-1ubuntu1.10.04.4
clamav-base/lucid uptodate 0.96.5+dfsg-1ubuntu1.10.04.4
clamav-daemon/lucid uptodate 0.96.5+dfsg-1ubuntu1.10.04.4
clamav-freshclam/lucid uptodate 0.96.5+dfsg-1ubuntu1.10.04.4
libclamav6/lucid uptodate 0.96.5+dfsg-1ubuntu1.10.04.4

---

