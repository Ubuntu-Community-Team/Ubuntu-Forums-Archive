---
title: "gthumb install = Broken Package"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by Ichido on 2010-04-10
Using Ubuntu Software Center, gthumb will not install.
Error: Broken Packages:
installArchives() failed: (Reading database ... 
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
(Reading database ... 201641 files and directories currently installed.)

Unpacking gthumb-data (from .../gthumb-data_3%3a2.11.2.1-1+git20100312~webupd8~karmic4_all.deb) ...

dpkg: error processing /var/cache/apt/archives/gthumb-data_3%3a2.11.2.1-1+git20100312~webupd8~karmic4_all.deb (--unpack):

 trying to overwrite '/usr/share/icons/hicolor/16x16/actions/flickr.png', which is also in package kipi-plugins 0:1.0.0-1ubuntu1~karmic1

dpkg-deb: subprocess paste killed by signal (Broken pipe)

Selecting previously deselected package gthumb.

Unpacking gthumb (from .../gthumb_3%3a2.11.2.1-1+git20100312~webupd8~karmic4_i386.deb) ...

Processing triggers for hicolor-icon-theme ...

Processing triggers for man-db ...

Processing triggers for desktop-file-utils ...

Processing triggers for menu ...

Errors were encountered while processing:

 /var/cache/apt/archives/gthumb-data_3%3a2.11.2.1-1+git20100312~webupd8~karmic4_all.deb

---

### Post by mac9416 on 2010-04-10
Hello,

Perhaps that .deb is corrupted. Try running

```
$ sudo apt-get clean
```

That will empty the apt cache and force it to re-download that package.

---

### Post by Ichido on 2010-04-10
```
$ sudo apt-get clean
```

I ran the command and nothing changed.

---

### Post by mac9416 on 2010-04-10
Did you try to install gthumb again and get the exact same error?

---

### Post by Ichido on 2010-04-10
Yes

---

### Post by Ichido on 2010-06-11
Quit trying to use gthumb.

---

