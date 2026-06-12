---
title: "update manager does not work"
date: 2014-03-09
forum: Installation &amp; Upgrades
---

### Post by harun3d2 on 2014-03-09
this thread already exists but since it is solved I may not write there. that is why I opened a new thread.
software sources also do not work. I have no access to them.  so disabling bchemnet in the repositories is impossible for me since I don´t have access to the repositories.

I have tried the proposed solutions.  It did not work for me.
sudo apt-get update gives this at the end (only last lines):

Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring/main Translation-en_US                 
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring/multiverse Translation-en_US           
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring/restricted Translation-en_US           
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring/universe Translation-en_US             
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-updates/main Translation-en_US         
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-updates/multiverse Translation-en_US   
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-updates/restricted Translation-en_US   
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-updates/universe Translation-en_US     
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-backports/main Translation-en_US       
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-backports/multiverse Translation-en_US 
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-backports/restricted Translation-en_US 
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) raring-backports/universe Translation-en_US   
Fetched 19.6 MB in 4min 15s (76.8 kB/s)     
                              
Reading package lists... Done
W: Duplicate sources.list entry [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian/extra i386 Packages (/var/lib/apt/lists/www.bchemnet.com_suldr_dists_debian_extra_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian/extra i386 Packages (/var/lib/apt/lists/www.bchemnet.com_suldr_dists_debian_extra_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



sudo update-manager     gives: 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    from gi.repository import Gtk
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 27, in <module>
    from ._gi import _API, Repository
ImportError: No module named _gi

---

### Post by Frogs Hair on 2014-03-09
Ubuntu 13.04 reached end of life and the repository closed so you should backup and install a supported version. This is important because a Linux security vulnerability was discovered last week and a patch was issued , but only for supported version of Ubuntu.

---

### Post by harun3d2 on 2014-04-06
so 13.04 reached end of life and 12.04 did not because it is LTS. so I shouldn't do an update then.

---

### Post by coffeecat on 2014-04-06
You need to re-install if you want to run a supported version of Ubuntu. 12.04 and the soon to be released 14.04 are LTS (long term support) and supported for five years. The intermediate releases are supported for 9 months only (since 13.04). You need to choose between running LTS versions if you want to upgrade only frequently, or running intermediate versions, but only if you make sure you upgrade soon after the next version is released. I always run the latest version as my main system, making a fresh install shortly after its release - that is every six months I upgrade or re-install to the latest. Others prefer to run LTS versions, only upgrading every 2 years or so. There are pros and cons to both strategies, and you would have to choose which you would prefer.

One option would be to re-install with the current 13.10, bearing in mind that it will go end of life in July of this year, and then upgrade to 14.04 when it becomes available later this month. When October arrives you would then have the choice of continuing to run the LTS 14.04, and keeping it up to date, or upgrade to the then new 14.10. But if you do the latter, you need to remember that 14.10 will only be supported for 9 months.

---

