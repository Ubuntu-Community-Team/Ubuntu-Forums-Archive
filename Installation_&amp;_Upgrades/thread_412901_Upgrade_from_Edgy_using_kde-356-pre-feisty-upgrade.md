---
title: "Upgrade from Edgy using kde-356-pre-feisty-upgrade serious error."
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by shabeer on 2007-04-18
Hello, 

I have followed instructions as per

[https://help.ubuntu.com/community/FeistyUpgrades#head-6146e7b1dd7a50f5029fd0704e38cad9420c000a](https://help.ubuntu.com/community/FeistyUpgrades#head-6146e7b1dd7a50f5029fd0704e38cad9420c000a)

for upgrading edgy kubuntu to feisty kubuntu.

I have included  following in my sources.list
deb  [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/) edgy main

I get following error

Preparing to replace kcontrol 4:3.5.6-0ubuntu1~edgy1 (using .../kcontrol_4%3a3.5.6-0ubuntu1really3.5.5_i386.deb) ...
Unpacking replacement kcontrol ...
dpkg: error processing /var/cache/apt/archives/kcontrol_4%3a3.5.6-0ubuntu1really3.5.5_i386.deb (--unpack):
 trying to overwrite `/usr/share/doc/kde/HTML/en/kinfocenter/cdinfo/index.docbook', which is also in package kdebase-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kcontrol_4%3a3.5.6-0ubuntu1really3.5.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


It seems there is some problem in kcontrol_4%3a3.5.6-0ubuntu1really3.5.5_i386.deb present in 
 [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/)


Any ideas what  can be done?

Shabeer.

---

### Post by Chareos on 2007-04-20
I'm going to upgrade the same way...
is it solved ? Nobody else received this error ?

---

