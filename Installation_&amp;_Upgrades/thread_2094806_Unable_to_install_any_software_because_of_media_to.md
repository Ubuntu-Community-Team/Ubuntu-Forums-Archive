---
title: "Unable to install any software because of media tomb?"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by Mb0742 on 2012-12-14
Hey guys,

My server while running like a champ has hit a really frustrating problem. If I try to install or uninstall any programs mediatomb configures and I am forced to kill -9 dpkg (which in turn requires dpkg reconfigure a).
```

matt@matt-desktop:~$ sudo dpkg --configure -a
dpkg: error processing mediatomb-daemon (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 mediatomb-daemon


```

```

matt@matt-desktop:~$ sudo apt-get install powertop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libobrender21 libswscale0 libavutil49 libobparser21 libncurses-ruby1.8
  linux-headers-2.6.32-32 bind9utils g++-4.4 libvncserver0 librrd4
  libstdc++6-4.4-dev openoffice.org-l10n-common libavformat52 libmcrypt4
  linux-headers-2.6.32-32-generic libavcodec52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnl2 mediatomb-daemon
Suggested packages:
  cpufrequtils laptop-mode-tools
The following NEW packages will be installed:
  libnl2 powertop
The following packages will be upgraded:
  mediatomb-daemon
1 upgraded, 2 newly installed, 0 to remove and 330 not upgraded.
1 not fully installed or removed.
Need to get 288 kB/298 kB of archives.
After this operation, 808 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com/ubuntu/ precise/main libnl2 i386 2.0-1 [163 k                                                 B]
Get:2 http://au.archive.ubuntu.com/ubuntu/ precise/main powertop i386 1.97-2 [12                                                 5 kB]
Fetched 288 kB in 1s (279 kB/s)
(Reading database ... 243341 files and directories currently installed.)
Preparing to replace mediatomb-daemon 0.12.0~svn2018-6ubuntu2 (using .../mediatomb-daemon_0.12.1-0ubuntu4_all.deb) ...

MediaTomb UPnP Server version 0.12.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2012-12-15 12:13:42    INFO: Loading configuration from: /home/matt/.mediatomb/config.xml
2012-12-15 12:13:42    INFO: Checking configuration...
2012-12-15 12:13:42    INFO: Setting filesystem import charset to UTF-8
2012-12-15 12:13:42    INFO: Setting metadata import charset to UTF-8
2012-12-15 12:13:42    INFO: Setting playlist charset to UTF-8
2012-12-15 12:13:42    INFO: Configuration check succeeded.
2012-12-15 12:13:42 WARNING: Sqlite3 database seems to be corrupt or doesn't exist yet.
2012-12-15 12:13:42    INFO: no sqlite3 backup is available or backup is corrupt. automatically creating database...
2012-12-15 12:13:42    INFO: database created successfully.
2012-12-15 12:13:42    INFO: Initialized port: 49152
2012-12-15 12:13:42    INFO: Server bound to: 192.168.1.39
2012-12-15 12:13:43    INFO: MediaTomb Web UI can be reached by following this link:
2012-12-15 12:13:43    INFO: http://192.168.1.39:49152/

```

---

### Post by Mb0742 on 2013-04-03
Sorry to bump guys but this is really crap, when it is my server box :mad:

---

