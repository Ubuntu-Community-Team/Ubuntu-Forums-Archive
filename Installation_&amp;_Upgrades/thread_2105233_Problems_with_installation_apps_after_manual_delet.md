---
title: "Problems with installation apps after manual deleting of firefox"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by ModX on 2013-01-15
I wanted to have Firefox 17 instead Aurora 19.
And I deleted all firefox folders manually.
:lolflag: 

](*,)

Now I have a problem with installation any apps.
Ubuntu Software Center need to repair, but the repair has been ended with error:
> The installation or removal of a software package failed.

Details:
> installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 254136 files and directories currently installed.)
Unpacking firefox (from .../firefox_19.0~a2~hg20130107r119234-0ubuntu1~umd1~precise_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_19.0~a2~hg20130107r119234-0ubuntu1~umd1~precise_i386.deb (--unpack):
 trying to overwrite '/usr/lib/firefox/plugins', which is also in package adobe-flashplugin 11.2.202.258-0precise1
No apport report written because MaxReports is reached already
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_19.0~a2~hg20130107r119234-0ubuntu1~umd1~precise_i386.deb
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 19.0~a2~hg20121220r119016-0ubuntu1~umd1~precise); however:
  Package firefox is not installed.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured


sudo apt-get -f install

> 1 not fully installed or removed.
Need to get 0 B/24.9 MB of archives.
After this operation, 50.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 254136 files and directories currently installed.)
Unpacking firefox (from .../firefox_19.0~a2~hg20130107r119234-0ubuntu1~umd1~precise_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_19.0~a2~hg20130107r119234-0ubuntu1~umd1~precise_i386.deb (--unpack):
 trying to overwrite '/usr/lib/firefox/plugins', which is also in package adobe-flashplugin 11.2.202.258-0precise1
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_19.0~a2~hg20130107r119234-0ubuntu1~umd1~precise_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please, advise how I can solve this problem?

---

### Post by zvacet on 2013-01-16
```
sudo dpkg --configure -a
```

---

### Post by ModX on 2013-01-17
The result of: sudo dpkg --configure -a

> dpkg: dependency problems prevent configuration of firefox-globalmenu:
firefox-globalmenu depends on firefox (= 19.0~a2~hg20121220r119016-0ubuntu1~umd1~precise); however:
Package firefox is not installed.
dpkg: error processing firefox-globalmenu (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox-globalmenu

I think, needs to delete dependency of dpkg and firefox...

I tried to delete 
/var/cache/apt/archives/firefox_19.0~a2~hg20130107r119234-0ubuntu1~umd1~precise_i386.deb
but it didn't help
This package downloads again.

---

### Post by ModX on 2013-01-17
SOLVED !!!!!

[http://www.iasptk.com/ubuntu-fix-broken-package-best-solution]("http://www.iasptk.com/ubuntu-fix-broken-package-best-solution")

> the problem of a broken package still exist the solution is to edit the dpkg status file manually.

1. $ sudo gedit /var/lib/dpkg/status    (you can use vi or nano instead of gedit)
2. Locate the corrupt package, and remove the whole block of information about it and save the file.

---

