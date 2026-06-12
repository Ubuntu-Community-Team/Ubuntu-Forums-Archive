---
title: "firefox-2-gnome-support error"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by jej2003 on 2008-04-19
During update of firefox-2-gnome-support I get the following
```

E: firefox-2: subprocess post-installation script returned error exit status 1
E: firefox-2-gnome-support: dependency problems - leaving unconfigured

```

```

Errors were encountered while processing:
 firefox-2
 firefox-2-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firefox-2 (2.0.0.14+2nobinonly-0ubuntu1) ...
Please restart any running Firefoxes, or you will experience problems.
cp: cannot stat `/usr/share/firefox-2/firefox-2-restart-required.update-notifier': No such file or directory
dpkg: error processing firefox-2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of firefox-2-gnome-support:
 firefox-2-gnome-support depends on firefox-2 (= 2.0.0.14+2nobinonly-0ubuntu1); however:
  Package firefox-2 is not configured yet.
dpkg: error processing firefox-2-gnome-support (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


```

if I take a look there is no /usr/share/firefox-2 directory, just a firefox directory, should this have been a symlink or did something get screwed up here I am unaware of?

---

### Post by slamgauge on 2008-05-05
I am having the same problem.  It started after I downgraded firefox 3 back to firefox 2.

---

