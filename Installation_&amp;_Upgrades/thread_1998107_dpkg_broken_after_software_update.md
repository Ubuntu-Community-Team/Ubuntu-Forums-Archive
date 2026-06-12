---
title: "dpkg broken after software update"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by SophieD on 2012-06-06
Hi, I am hoping that someone here might be able to help me. We are running the ArtistX version of Ubuntu (couldn't find that in the drop down menu.)

A recent  automatic update appeared to fail - it announced that it was going to  text console then froze completely. Upon restart we have been unable to  perform any further updates or upgrades. Running **sudo apt-get install -f** in a Terminal window results in the following:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libegl1-mesa libegl1-mesa-drivers libxcb-xfixes0 libgbm1 libtextcat0
  libtextcat-data libwayland0 libopenvg1-mesa libkwineffects1abi2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde-window-manager kde-window-manager-common kde-workspace-kgreet-plugins
  kdm ktorrent ktorrent-data libkdecorations4 libkephal4abi1 libkscreensaver5
  libkwineffects1abi3 libkwinglutils1 libsolidcontrolifaces4abi2
  plasma-widget-ktorrent plasma-widget-lancelot tvpvrd
Suggested packages:
  kde-wallpapers
The following packages will be REMOVED:
  libplasmaclock4abi2 libtaskmanager4abi2 plasma-widget-adjustableclock
  plasma-widget-daisy plasma-widget-fancytasks plasma-widget-smooth-tasks
The following NEW packages will be installed:
  kde-window-manager-common libkwineffects1abi3 libkwinglutils1
The following packages will be upgraded:
  kde-window-manager kde-workspace-kgreet-plugins kdm ktorrent ktorrent-data
  libkdecorations4 libkephal4abi1 libkscreensaver5 libsolidcontrolifaces4abi2
  plasma-widget-ktorrent plasma-widget-lancelot tvpvrd
12 upgraded, 3 newly installed, 6 to remove and 149 not upgraded.
10 not fully installed or removed.
Need to get 0 B/7,383 kB of archives.
After this operation, 6,033 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 454963 files and directories currently installed.)
Preparing to replace tvpvrd 3.3.3-1~getdeb1 (using .../tvpvrd_3.3.5-1~getdeb1_i386.deb) ...
Unpacking replacement tvpvrd ...
update-rc.d: /etc/init.d/tvpvrd exists during rc.d purge (use -f to force)
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
update-rc.d: /etc/init.d/tvpvrd exists during rc.d purge (use -f to force)
dpkg: error processing /var/cache/apt/archives/tvpvrd_3.3.5-1~getdeb1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                               update-rc.d: /etc/init.d/tvpvrd exists during rc.d purge (use -f to  force)
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/tvpvrd_3.3.5-1~getdeb1_i386.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)Can anyone here advise us how to return the system to its previous healthy state?

---

### Post by SophieD on 2012-06-06
It occurs to me that I should perhaps have posted in the Absolute Beginners section as I don't think I can claim to be totally up to speed regarding Ubuntu.

Running **sudo apt-get -f install --reinstall dpkg** obtains the following:

> Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-workspace-bin : Depends: libkephal4abi1 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
                     Depends: libkscreensaver5 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
                     Depends: libsolidcontrolifaces4abi2 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
                     Depends: kde-workspace-kgreet-plugins (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
 libplasmaclock4abi3 : Depends: libkephal4abi1 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
 libplasmagenericshell4 : Depends: libkephal4abi1 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
 libtaskmanager4abi3 : Depends: libkephal4abi1 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
 plasma-desktop : Depends: libkephal4abi1 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
 plasma-netbook : Depends: libkephal4abi1 (= 4:4.8.2a-0ubuntu1~oneiric1~ppa1) but 4:4.7.4-0ubuntu0.1~ppa1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).I don't know if that will shed any light on the situation.

EDIT: subsequently running **apt-get -f install** as advised gets pretty much exactly the same stuff as that obtained in the first post.

---

### Post by SophieD on 2012-06-06
Found a solution at

[http://www.artistx.org/site3/Software/1822-tvpvrd-sticking.html#1822](http://www.artistx.org/site3/Software/1822-tvpvrd-sticking.html#1822)

which worked. Now able to update and upgrade as normal.

---

### Post by wilee-nilee on 2012-06-06
Cool Sophie, I noticed though that it looked like a partial upgrade, you don't really want to run a partial.

This is the key line of what you want to avoid.

12 upgraded, 3 newly installed, 6 to remove and **149 not upgraded.**

Not sure of your set up or what may have been added to the source list.

If you get it completely running do a backup of home if not separate, and consider cloning the whole thing.

A clone will save a lot of hassle if it totally bricks at some point.

---

