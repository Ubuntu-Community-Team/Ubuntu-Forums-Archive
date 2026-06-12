---
title: "Cannot updgrade Xubuntu from 16.04 to 18.04"
date: 2019-09-18
forum: Installation &amp; Upgrades
---

### Post by maketopsite on 2019-09-18
[FONT=Courier New]update-manager[/FONT] crashes on first step after downloading files.

Can anyone please help ?



```
 # do-release-upgrade
Reading the cache

Checking the package manager
Reading package lists ... Done
Building the dependency tree
Read status information ... Done
Att http://en.archive.ubuntu.com/ubuntu xenial InRelease
Take 1 http://en.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]
Take 2 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Take 3 http://en.archive.ubuntu.com/ubuntu xenial-updates InRelease [107 kB]
325 k received in 0s (0 o / s)
Reading package lists ... Done
Building the dependency tree
Read status information ... Done

Restoring the system to its original state

Cancellation
Reading package lists ... Done
Building the dependency tree
Read status information ... Done
=== Command detached from window (Tue Sep 17 07:50:18 2019) ===
=== Command terminated with exit status 1 (Tue Sep 17 07:50:28 2019) ===
 
```

```
  $ update-manager 
** (update-manager:3866): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-eDySYDwn1E: Connection refused
/usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
Searching new version of Ubuntu

** (do-release-upgrade:4205): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-eDySYDwn1E: Connection refused
/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcher.py:23: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk
/usr/lib/python3/dist-packages/DistUpgrade/ReleaseNotesViewerWebkit.py:33: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as WebKit

** (WebKitWebProcess:4231): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-eDySYDwn1E: Connection refused
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
authentification de « bionic.tar.gz » avec « bionic.tar.gz.gpg » 
extraction de 'bionic.tar.gz'

** (bionic:4205): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-eDySYDwn1E: Connection refused 
```

[FONT=courier new]/var/log/dist-upgrade/main.log:

```
 (do-release-upgrade)
2019-09-17 07:34:18,558 INFO Using config files '['./DistUpgrade.cfg.xenial']'
2019-09-17 07:34:18,559 INFO uname information: 'Linux ntb-TravelMate-P253 4.4.0-161-generic #189-Ubuntu SMP Tue Aug 27 08:10:16 UTC 2019 x86_64'
2019-09-17 07:34:19,080 INFO apt version: '1.2.32'
2019-09-17 07:34:19,080 INFO python version: '3.5.2 (default, Jul 10 2019, 11:58:48) 
[GCC 5.4.0 20160609]'
2019-09-17 07:34:19,084 INFO release-upgrader version '18.04.34' started
2019-09-17 07:34:19,091 INFO locale: 'fr_FR' 'UTF-8'
2019-09-17 07:34:19,329 DEBUG Using 'DistUpgradeViewText' view
2019-09-17 07:34:19,412 DEBUG enable dpkg --force-overwrite
2019-09-17 07:34:19,449 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2019-09-17 07:34:30,108 DEBUG lsb-release: 'xenial'
2019-09-17 07:34:30,110 DEBUG _pythonSymlinkCheck run
2019-09-17 07:34:30,111 DEBUG openCache()
2019-09-17 07:34:30,112 DEBUG No such plugin directory: ./plugins
2019-09-17 07:34:30,112 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2019-09-17 07:34:30,112 DEBUG plugins for condition 'bionicPreCacheOpen' are '[]'
2019-09-17 07:34:30,112 DEBUG plugins for condition 'from_xenialPreCacheOpen' are '[]'
2019-09-17 07:34:30,112 DEBUG quirks: running PreCacheOpen
2019-09-17 07:34:30,112 DEBUG running Quirks.PreCacheOpen
2019-09-17 07:34:30,974 DEBUG /openCache(), new cache size 89928
2019-09-17 07:34:30,975 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2019-09-17 07:34:30,975 DEBUG checkViewDepends()
2019-09-17 07:34:30,976 DEBUG running doUpdate() (showErrors=False)
2019-09-17 07:34:32,134 DEBUG openCache()
2019-09-17 07:34:33,027 DEBUG /openCache(), new cache size 89928
2019-09-17 07:34:33,027 DEBUG doPostInitialUpdate
2019-09-17 07:34:33,028 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2019-09-17 07:34:33,028 DEBUG plugins for condition 'bionicPostInitialUpdate' are '[]'
2019-09-17 07:34:33,028 DEBUG plugins for condition 'from_xenialPostInitialUpdate' are '[]'
2019-09-17 07:34:33,028 DEBUG quirks: running bionicPostInitialUpdate
2019-09-17 07:34:33,028 DEBUG running Quirks.bionicPostInitialUpdate
2019-09-17 07:34:38,049 DEBUG abort called
2019-09-17 07:34:38,050 DEBUG openCache()
2019-09-17 07:34:38,946 DEBUG /openCache(), new cache size 89928 
```

```
 (update-manager)
2019-09-17 07:35:43,412 INFO Using config files '['./DistUpgrade.cfg.xenial']'
2019-09-17 07:35:43,412 INFO uname information: 'Linux ntb-TravelMate-P253 4.4.0-161-generic #189-Ubuntu SMP Tue Aug 27 08:10:16 UTC 2019 x86_64'
2019-09-17 07:35:43,933 INFO apt version: '1.2.32'
2019-09-17 07:35:43,934 INFO python version: '3.5.2 (default, Jul 10 2019, 11:58:48) 
[GCC 5.4.0 20160609]'
2019-09-17 07:35:43,938 INFO release-upgrader version '18.04.34' started
2019-09-17 07:35:44,050 INFO locale: 'fr_FR' 'UTF-8'
2019-09-17 07:35:44,533 DEBUG Using 'DistUpgradeViewGtk3' view
2019-09-17 07:35:44,613 DEBUG enable dpkg --force-overwrite
2019-09-17 07:35:44,638 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2019-09-17 07:35:55,530 DEBUG lsb-release: 'xenial'
2019-09-17 07:35:55,532 DEBUG _pythonSymlinkCheck run
2019-09-17 07:35:55,534 DEBUG openCache()
2019-09-17 07:35:55,534 DEBUG No such plugin directory: ./plugins
2019-09-17 07:35:55,534 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2019-09-17 07:35:55,534 DEBUG plugins for condition 'bionicPreCacheOpen' are '[]'
2019-09-17 07:35:55,534 DEBUG plugins for condition 'from_xenialPreCacheOpen' are '[]'
2019-09-17 07:35:55,534 DEBUG quirks: running PreCacheOpen
2019-09-17 07:35:55,534 DEBUG running Quirks.PreCacheOpen
2019-09-17 07:35:56,402 DEBUG /openCache(), new cache size 89928
2019-09-17 07:35:56,403 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2019-09-17 07:35:56,403 DEBUG checkViewDepends()
2019-09-17 07:35:56,403 DEBUG running doUpdate() (showErrors=False)
2019-09-17 07:35:57,653 DEBUG openCache()
2019-09-17 07:35:58,545 DEBUG /openCache(), new cache size 89928
2019-09-17 07:35:58,545 DEBUG doPostInitialUpdate
2019-09-17 07:35:58,545 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2019-09-17 07:35:58,545 DEBUG plugins for condition 'bionicPostInitialUpdate' are '[]'
2019-09-17 07:35:58,546 DEBUG plugins for condition 'from_xenialPostInitialUpdate' are '[]'
2019-09-17 07:35:58,546 DEBUG quirks: running bionicPostInitialUpdate
2019-09-17 07:35:58,546 DEBUG running Quirks.bionicPostInitialUpdate
2019-09-17 07:36:03,567 DEBUG abort called
2019-09-17 07:36:03,569 DEBUG openCache()
2019-09-17 07:36:04,471 DEBUG /openCache(), new cache size 89928 
```
[/FONT]

---

### Post by Rick St. George on 2019-09-19
Follow instructions here;
[https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver)

Workded for me!
:popcorn:

---

### Post by Terry_Heislen on 2019-09-24
After initial failure, with same messages re: "import Gtk" and "import Webkit," tried the instructions at linuxconfig.org, ended up in the same place as marketopsite, with command terminated.
Any advice?

---

### Post by Impavidus on 2019-09-25
In my experience, release upgrades usually work. However, if it doesn't work, it can be hard to fix. The output you posted doesn't give any clear clues about what could have gone wrong. The easiest option is a fresh install of 18.04. It will take less time than finding out why the upgrade doesn't work.

Note that Xubuntu 16.04 had 3 years of support, so it reached end of live five months ago. The parts it has in common with Ubuntu are still supported, but the Xubuntu-specific parts are not.

---

### Post by maketopsite on 2019-09-27
> **Rick St. George said:**
> Follow instructions here;
[https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver)

Workded for me!
:popcorn:

I've tried 
```
 apt autoremove 
```

mentioned there, used another init system and logged in as another user and upgrade has finished successfully :)

---

### Post by cmcanulty on 2019-09-27
This seems crazy but it has worked several times for me. Boot to live usb or dvd and select try ubuntu NOT install.. Then when it boots to live desktop on desktop click the install option.

---

### Post by KBD47 on 2019-09-28
> **cmcanulty said:**
> This seems crazy but it has worked several times for me. Boot to live usb or dvd and select try ubuntu NOT install.. Then when it boots to live desktop on desktop click the install option.

So you are upgrading with a Live USB? I haven't tried that, but have thought about giving it a shot.

---

### Post by maketopsite on 2019-09-29
> **cmcanulty said:**
> This seems crazy but it has worked several times for me. Boot to live usb or dvd and select try ubuntu NOT install.. Then when it boots to live desktop on desktop click the install option.

Does it make distribution upgrade and preserves all documents, settings, installed apps ?

---

