---
title: "konqueror package blocks upgrage"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by laluz on 2008-05-09
Hi, I have just upgraded to Hardy and something went wrong with the upgrade. Basically this is how the error message looks like, that comes out when I try to finalize the upgrade of KDE i.e. install kde-core

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libtwolame0 libwildmidi

SNIP

The following extra packages will be installed:
  konqueror
Suggested packages:
  gij-4.1 konq-plugins ksvg libgcj7-awt libjessie-java
The following NEW packages will be installed:
  konqueror
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
4 not fully installed or removed.
Need to get 0B/1967kB of archives.
After this operation, 5390kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 155142 files and directories currently installed.)
Unpacking konqueror (from .../konqueror_4%3a3.5.9-0ubuntu7.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.1_i386.deb (--unpack):
 trying to overwrite `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', which is also in package kio-umountwrapper
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have been doing all the tricks I know but do not manage to get this pesky media_safelyremove.desktop disappear. 

What could I try more?

---

### Post by laluz on 2008-05-09
just started adept_manager again after all the mumbo jumbo I did in the command line and it went through.

---

