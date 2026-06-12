---
title: "apt-get issue : kde4base-data"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by sc0g on 2008-01-01
I recently tried to install the RC2 release of KDE4 using apt. I no longer want to try and install it. However, whenever I try to run updates, I get the following error:

[COLOR="Red"]
mascogin@sc0g:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kde4base-data
The following NEW packages will be installed:
  kde4base-data
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
8 not fully installed or removed.
Need to get 0B/61.3MB of archives.
After unpacking 89.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 136387 files and directories currently installed.)
Unpacking kde4base-data (from .../kde4base-data_3.94.0-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kde4base-data_3.94.0-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/kde4/services/kuiserver.desktop', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde4base-data_3.94.0-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

I have tried clearing the cache in /var/cache/apt but that did not fix the problem. Can someone please give me some tips as to how to fix this?

Thanks!

---

### Post by lptr on 2008-03-14
same here: I added 
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
``` in /etc/apt/sources.list and sudo apt-get update.

Could select KDE4 Desktop on login screen. After some tries I ended up in using Synaptic to get kde4utils / admin tools and the like because of missing superuser button in settings dialog. Whatever I try there seem to be a problem with kde4base and data.

sudo apt-get install -f and the like did not help, too.

This is a brand new installed kubuntu 7.10 test machine (IBM Thinkpad z60m w. ATI gracard), so no malconfig could be there. Using ATI proprietary drivers provided with distro.

Any ideas?

rob*/

---

