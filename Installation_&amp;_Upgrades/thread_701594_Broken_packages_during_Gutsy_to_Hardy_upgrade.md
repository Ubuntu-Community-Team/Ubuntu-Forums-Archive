---
title: "Broken packages during Gutsy to Hardy upgrade"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by Gagnefury on 2008-02-19
user@server:~$ sudo aptitude dist-upgrade
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  feisty-gdm-themes gutsy-wallpapers libcamel1.2-10 libdb4.5
  libdirectfb-0.9-25 libgoffice-0-4 libgpod2 libgsl0 libicu36 libmtp6
  libneon26 liboobs-1-3 libsnmp10 libsvg1 libtotem-plparser7 libuniconf4.3
  libwvstreams4.3-base libwvstreams4.3-extras libxine1-gnome
  linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic python-at-spi
  python-numarray python-software-properties software-properties-gtk
The following packages will be upgraded:
  language-selector-common libusplash0 python-apt update-manager
  update-manager-core usplash vinagre
The following partially installed packages will be configured:
  apturl gnome-app-install language-selector ubufox ubuntu-desktop
7 packages upgraded, 0 newly installed, 25 to remove and 0 not upgraded.
Need to get 559kB/1708kB of archives. After unpacking 105MB will be freed.

After I say yes I get the following results:

Errors were encountered while processing:
 language-selector
 gnome-app-install
 ubuntu-desktop
 language-selector-common
 apturl
 ubufox


Any thoughts on how I can resolve these package errors? I am currently unable to run update-manager -d again :(

---

### Post by Gagnefury on 2008-02-19
Found the fix for anyone else having this issue:

[https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/193260](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/193260)

---

