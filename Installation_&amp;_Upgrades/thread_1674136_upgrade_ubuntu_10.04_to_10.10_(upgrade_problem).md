---
title: "upgrade ubuntu 10.04 to 10.10 (upgrade problem)"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by zium on 2011-01-23
hi,

I tried to upgrade Ubuntu version 10.04 to 10.10. And the pop-ups "Distribution Upgrade" showing and the first step is "to upgrade Prepering" no problem. Then the second step "setting new software channels" exit pop up 

_**Third party sources disabled**_

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.

So what should I do?. So I continued to press the "close"

and then out again pop up

**Error during update**

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://my.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

any suggestions and your help is greatly appreciated. thanks

---

### Post by Alxl on 2011-01-23
Hi zium,
I am not good enough to analyze your problem and give advice. But I can tell you how I do it.
My home folder is regularly backed-up on an external hard drive;  that includes a list of the additions that I have downloaded .
So it is just a matter of spending a couple of hours to do a fresh install.

You may also consider learning about the Ubuntu 10.10 Minimal - it has just enough to run and you add only what you need.

---

### Post by zium on 2011-01-23
Alxl, thanks for the suggestion, I have finished my problem. I thought, perhaps because the server I use. I use the server from malaysia, so I tried to change the server from singapore. Yes, it was successful.

---

