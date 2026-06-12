---
title: "Why this: &quot;Media change: please insert the disc labeled...&quot; ??"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by mattengland on 2006-12-28
I loaded 6.06.1 alternate cd on the new desktop that I purchased, and in the process of building a new kernel (to handle duo-core stuff, etc)--and more specifically loading the kernel-building stuff--I get asked to insert the 6.06.1 cdrom.

My first thought is:  "didn't I leave this stuff behind when I dumped Microsoft for Linux"?  It seems rather frustrating.

My general question: why am I getting asked to reload an install cdrom at all?  This is rather disconcerting for all my Linux-machine management.

Details from my session below.

-Matt

```

root@devdesktop1:/usr/src# sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
Reading package lists... Done
Building dependency tree... Done
wget is already the newest version.
libncurses5 is already the newest version.
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libaudio-dev
  libc6-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgl1-mesa-dev libglu1-mesa-dev libice-dev libjpeg62-dev liblcms1-dev
  libmng-dev libpng12-0 libpng12-dev libqt3-mt libsm-dev
  libstdc++6-4.0-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxt-dev
  linux-kernel-headers make mesa-common-dev qt3-dev-tools x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev zlib1g-dev
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc
  lib64stdc++6 manpages-dev autoconf automake1.9 libtool flex bison
  gcc-doc libc6-dev-amd64 lib64gcc1 linux-source libdb3-dev docbook-utils
  glibc-doc libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc libqt3-i18n
  qt3-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev libqt3-compat-headers
The following NEW packages will be installed:
  bin86 binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc
  gcc-4.0 kernel-package libaudio-dev libc6-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgl1-mesa-dev libglu1-mesa-dev
  libice-dev libjpeg62-dev liblcms1-dev libmng-dev libncurses5-dev
  libpng12-dev libqt3-headers libqt3-mt libqt3-mt-dev libsm-dev
  libstdc++6-4.0-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxt-dev
  linux-kernel-headers make mesa-common-dev qt3-dev-tools x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev zlib1g-dev
The following packages will be upgraded:
  libpng12-0
1 upgraded, 57 newly installed, 0 to remove and 61 not upgraded.
Need to get 12.6MB/24.4MB of archives.
After unpacking 92.6MB of additional disk space will be used.
Do you want to continue [Y/n]?
Media change: please insert the disc labeled
 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)'
in the drive '/cdrom/' and press enter

Get:1 http://us.archive.ubuntu.com dapper/main x11proto-core-dev 7.0.4-0ubuntu2 [75.0kB]
Get:2 http://us.archive.ubuntu.com dapper/main libice-dev 2:1.0.0-0ubuntu2 [49.1kB]
....

```

---

### Post by bulldog on 2006-12-28
You have the cd-rom enabled as a repo in your sources.list I guess.
You can use the cd or download everything again,it's your choice what will be quicker to do.

---

### Post by christhemonkey on 2006-12-28
It is asking for the install cdrom as it wants to install some packages from the cdrom (saves people bandwidth and time).

You can easily remove the cd repository from your system (either by commenting out the relevant lines in your sources.list or by using synaptics repositories dialog) and then it will only get updates and packages from online.

---

### Post by mattengland on 2006-12-28
> **christhemonkey said:**
> It is asking for the install cdrom as it wants to install some packages from the cdrom (saves people bandwidth and time).

Here's the problem, in at least my environment:

A sysadmin loads Ubuntu on several machines (could be 10, could be 100, whatever) and expects the system to be autonomous.  Users with appropriate privileges can upgrade the software as needed.  Alas, unless a cd copy is kept with every machine, this is not feasible--and there's a snowball's chance in a very warm place that anyone is going to magically find the right cd when they need it.

I generally prefer Debian-based systems (including Ubuntu) for installations because of their wonderful ease-of-upgrade and administration via apt and silimilar mechanisms...and specifically, upgrading with any internet connection.  If the default install doesn't point to the internet repos for Debian/Ubuntu, and instead requires a user to ** insert a cdrom ** (shudder), this really defeats the purpose.

What may seem speedy to someone else (ie, the cdrom-based repo) is a total nightmare for a more-than-one-person (or at least bigger) operation.  It's clear to me know that the Ubuntu decision makers don't seem to be targeting this type of market.  And to me, that's disappointing.  I'll aruge, however: I would imagine the average single user of Ubuntu has a nice, big, fat internet pipe for which he/she connects to.  I'd further guess that such a user would prefer an internet-based upgrade system as well.  Practically speaking, no one can really find a cd (or figure out which one is the right now) when you really need it. I consider that a sysadmin fact of life that could be theorertically disputed...but I suspect not by those with experience in such matters.

Yes, someone can go update the /etc/apt/sources.list file, but I prefer that users, even those with upgrade privileges, keep their grubby mitts off that file, else Debian systems get rather inconsistent rather quickly.  Why make somone edit this to make the thing work?

I manage my own open-source community, so I'm inclined to not get on someone's bad side here.  However, I am raising a bit of a stink for at least this fact:  I'd like to see what decision is going to be made on this matter for the Feisty cd/dvd releases...and why cdrom-based upgrades are still considered "appropriate."

Thoughts?

-Matt

---

### Post by christhemonkey on 2006-12-29
> What may seem speedy to someone else (ie, the cdrom-based repo) is a total nightmare for a more-than-one-person (or at least bigger) operation 
If you have a problem with this,
file a bug report/write a spec on it.

EDIT:

> Practically speaking, no one can really find a cd (or figure out which one is the right now) when you really need it.

The items contained on the install cd, such as build-essential and ndiswrapper are things that people might need very close to installing (wireless drivers for example if they have no internet) so the likelyhood is that they will have just installed so the cd will be fairly to hand!

> Yes, someone can go update the /etc/apt/sources.list file, but I prefer that users, even those with upgrade privileges, keep their grubby mitts off that file, else Debian systems get rather inconsistent rather quickly. Why make somone edit this to make the thing work?


There is a menu item (system > administration > software sources) that contains a dialog box with easy repository selection, no need to mess round and edit a file.

---

### Post by meng on 2006-12-29
> **mattengland said:**
> I manage my own open-source community, so I'm inclined to not get on someone's bad side here.  However, I am raising a bit of a stink for at least this fact:  I'd like to see what decision is going to be made on this matter for the Feisty cd/dvd releases...and why cdrom-based upgrades are still considered "appropriate."
I totally see your point. Some unfortunate folks don't have internet access though, and the demand for ShipIt CD's is high. There has to be some default position, so which group do you decide in favor of? Perhaps the installer could ask for a preference post-install.

---

