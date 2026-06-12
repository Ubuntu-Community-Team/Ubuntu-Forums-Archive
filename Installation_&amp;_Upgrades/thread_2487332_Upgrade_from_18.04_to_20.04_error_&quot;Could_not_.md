---
title: "Upgrade from 18.04 to 20.04 error &quot;Could not calculate the upgrade&quot;"
date: 2023-05-30
forum: Installation &amp; Upgrades
---

### Post by baps55 on 2023-05-30
While trying to upgrade from 18.04 to 20.04 I am getting the following message

> 
Could not calculate the upgrade    
An unresolvable problem occurred while calculating the upgrade.

 If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If you want to investigate this yourself the log files in '/var/log/dist-upgrade' will contain details about the upgrade. Specifically, look at 'main.log' and 'apt.log'.

I have tried the following:

[LIST]
[*]apt-get update (all 0)
[*]apt-get upgrade (all 0)
[*]apt-get autoclean
[*]apt-get check
[*]apt-get dist-upgrade
[*]apt install -f
[*]apt update && apt full-upgrade
[*]dpkg --configure -a
[*]apt autoremove
[/LIST]
All outputs are 0

Output of grep Broken apt.log

```

Broken dpkg:amd64 Breaks on libapt-pkg5.0:amd64 < 1.6.17 @ii mK > (< 1.7~b)
Broken libuno-sal3:amd64 Breaks on uno-libs3:amd64 < 6.0.7-0ubuntu0.18.04.13 @ii mK >
Broken libgcc1:amd64 Conflicts on libgcc1:i386 < 1:8.4.0-1ubuntu1~18.04 -> 1:10.3.0-1ubuntu1~20.04 @ii umU Ib >
Broken libqt5core5a:amd64 Breaks on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mK > (< 4:4.8.7+dfsg-20~)
Broken libpython2-stdlib:amd64 Breaks on libpython-stdlib:amd64 < 2.7.15~rc1-1 @ii gK > (< 2.7.15-2)
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.15~rc1-1 @ii gK > (< 2.7.15-2)
Broken gnome-settings-daemon-common:amd64 Breaks on gnome-settings-daemon-schemas:amd64 < 3.28.1-0ubuntu1.3 @ii mK > (< 3.30.1.2-2~)
Broken libqtdbus4:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqt4-declarative:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqtgui4:amd64 Depends on libqt4-declarative:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqt4-xml:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken qt-at-spi:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (>= 4:4.8~)
Broken libqt4-network:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libldb2:amd64 Breaks on libldb1:amd64 < 2:1.2.3-1ubuntu0.2 @ii mK > (< 2:2~)
Broken libqt4-script:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libsensors-config:amd64 Conflicts on libsensors4:amd64 < 1:3.4.0-4ubuntu0.1 @ii mK >
Broken libsensors-config:amd64 Conflicts on libsensors4:i386 < 1:3.4.0-4ubuntu0.1 @ii mK >
Broken libqt4-sql:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libomp-dev:amd64 Depends on libomp-10-dev:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libqt4-sql-mysql:amd64 Depends on libqt4-sql:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqt4-dbus:amd64 Depends on libqtdbus4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqt4-xmlpatterns:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken fwupdate:amd64 Breaks on fwupdate-signed:amd64 < 12-7~ubuntu18.04.3 @ii mK >
Broken fwupdate:amd64 Breaks on libfwup1:amd64 < 12-3bionic2 @ii mK > (< 12-5)
Broken qdbus:amd64 Depends on libqt4-xml:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqt4-svg:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqt4-help:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libedata-book-1.2-25:amd64 Depends on libebackend-1.2-10:amd64 < 3.28.5-0ubuntu0.18.04.3 -> 3.36.5-0ubuntu1 @ii umU > (= 3.28.5-0ubuntu0.18.04.3)
Broken libqtassistantclient4:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (>= 4:4.8.1)
Broken libqt4-test:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libqt4-scripttools:amd64 Depends on libqt4-script:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libqt4-designer:amd64 Depends on libqt4-script:amd64 < 4:4.8.7+dfsg-7ubuntu1 @ii mR > (= 4:4.8.7+dfsg-7ubuntu1)
Broken libcupsppdc1:amd64 Depends on libcups2:amd64 < 2.2.7-1ubuntu2.9 -> 2.3.1-9ubuntu1.2 @ii umU > (= 2.2.7-1ubuntu2.9)
Broken python3-pyqt4:amd64 Depends on python3:amd64 < 3.6.7-1~18.04 -> 3.8.2-0ubuntu2 @ii umU > (< 3.7)
Broken libsnmp30:amd64 Depends on libsensors4:amd64 < 1:3.4.0-4ubuntu0.1 @ii mR > (>= 1:3.0.0)
Broken libedata-cal-1.2-28:amd64 Depends on libebackend-1.2-10:amd64 < 3.28.5-0ubuntu0.18.04.3 -> 3.36.5-0ubuntu1 @ii umU > (= 3.28.5-0ubuntu0.18.04.3)
Broken libpolkit-backend-1-0:amd64 Depends on libpolkit-gobject-1-0:amd64 < 0.105-20ubuntu0.18.04.6 -> 0.105-26ubuntu1.3 @ii umU > (= 0.105-20ubuntu0.18.04.6)
Broken libcupscgi1:amd64 Depends on libcups2:amd64 < 2.2.7-1ubuntu2.9 -> 2.3.1-9ubuntu1.2 @ii umU > (= 2.2.7-1ubuntu2.9)
Broken libcupsmime1:amd64 Depends on libcups2:amd64 < 2.2.7-1ubuntu2.9 -> 2.3.1-9ubuntu1.2 @ii umU > (= 2.2.7-1ubuntu2.9)
Broken libebook-1.2-19:amd64 Depends on libedata-book-1.2-25:amd64 < 3.28.5-0ubuntu0.18.04.3 @ii mR > (= 3.28.5-0ubuntu0.18.04.3)
Broken libapt-inst2.0:amd64 Depends on libapt-pkg5.0:amd64 < 1.6.17 @ii mR > (>= 1.1~exp9)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
Broken libomp5-9:amd64 Breaks on libomp5:amd64 < 5.0.1-1 | 1:10.0-50~exp1 @ii umH > (< 44)
Broken libomp5:amd64 Depends on libomp5-10:amd64 < none | 1:10.0.0-4ubuntu1 @un uH > (>= 10~)
```

Content of main.log


```
2023-05-29 22:19:44,598 INFO Using config files '['./DistUpgrade.cfg.bionic', '/etc/update-manager/release-upgrades.d/ubuntu-advantage-upgrades.cfg']'
2023-05-29 22:19:44,599 INFO uname information: 'Linux Aspire-A515-51G 4.15.0-211-generic #222-Ubuntu SMP Tue Apr 18 18:55:06 UTC 2023 x86_64'
2023-05-29 22:19:45,326 INFO apt version: '1.6.17'
2023-05-29 22:19:45,327 INFO python version: '3.6.9 (default, Mar 10 2023, 16:46:00) 
[GCC 8.4.0]'
2023-05-29 22:19:45,331 INFO release-upgrader version '20.04.40' started
2023-05-29 22:19:45,430 INFO locale: 'en_IN' 'ISO8859-1'
2023-05-29 22:19:45,862 DEBUG Using 'DistUpgradeViewGtk3' view
2023-05-29 22:19:45,943 DEBUG enable dpkg --force-overwrite
2023-05-29 22:19:45,967 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2023-05-29 22:19:53,435 DEBUG lsb-release: 'bionic'
2023-05-29 22:19:53,436 DEBUG _pythonSymlinkCheck run
2023-05-29 22:19:53,437 DEBUG openCache()
2023-05-29 22:19:53,437 DEBUG quirks: running PreCacheOpen
2023-05-29 22:19:53,437 DEBUG running Quirks.PreCacheOpen
2023-05-29 22:19:55,812 DEBUG Comparing 4.15.0-211 with 
2023-05-29 22:19:55,815 DEBUG Comparing 4.15.0-88 with 4.15.0-211
2023-05-29 22:19:56,632 DEBUG /openCache(), new cache size 115764
2023-05-29 22:19:56,632 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2023-05-29 22:19:56,633 DEBUG checkViewDepends()
2023-05-29 22:19:56,636 DEBUG running doUpdate() (showErrors=False)
2023-05-29 22:20:01,608 DEBUG openCache()
2023-05-29 22:20:03,996 DEBUG Comparing 4.15.0-211 with 
2023-05-29 22:20:03,999 DEBUG Comparing 4.15.0-88 with 4.15.0-211
2023-05-29 22:20:04,835 DEBUG /openCache(), new cache size 115764
2023-05-29 22:20:04,835 DEBUG doPostInitialUpdate
2023-05-29 22:20:04,836 DEBUG quirks: running focalPostInitialUpdate
2023-05-29 22:20:04,836 DEBUG running Quirks.focalPostInitialUpdate
2023-05-29 22:20:08,550 WARNING error reading deb2snap.json file (Expected a string or a pair of strings)
2023-05-29 22:20:09,059 DEBUG Snap core18 is installed
2023-05-29 22:20:09,671 DEBUG Snap gnome-3-34-1804 is installed
2023-05-29 22:20:09,674 DEBUG Snap gnome-3-34-1804 is not tracking the release channel
2023-05-29 22:20:09,906 DEBUG Snap gtk-common-themes is installed
2023-05-29 22:20:10,570 DEBUG Snap bare is installed
2023-05-29 22:20:10,570 DEBUG Snap bare is not tracking the release channel
2023-05-29 22:20:10,877 DEBUG Snap canonical-livepatch is installed
2023-05-29 22:20:10,878 DEBUG Snap canonical-livepatch is not tracking the release channel
2023-05-29 22:20:11,286 DEBUG Snap chromium-ffmpeg is installed
2023-05-29 22:20:11,287 DEBUG Snap chromium-ffmpeg is not tracking the release channel
2023-05-29 22:20:11,793 DEBUG Snap core is installed
2023-05-29 22:20:11,793 DEBUG Snap core is not tracking the release channel
2023-05-29 22:20:12,001 DEBUG Snap core20 is installed
2023-05-29 22:20:12,002 DEBUG Snap core20 is not tracking the release channel
2023-05-29 22:20:12,413 DEBUG Snap core22 is installed
2023-05-29 22:20:12,413 DEBUG Snap core22 is not tracking the release channel
2023-05-29 22:20:12,635 DEBUG Snap gnome-3-26-1604 is installed
2023-05-29 22:20:12,890 DEBUG Snap gnome-3-28-1804 is installed
2023-05-29 22:20:12,891 DEBUG Snap gnome-3-28-1804 is not tracking the release channel
2023-05-29 22:20:13,235 DEBUG Snap gnome-3-38-2004 is installed
2023-05-29 22:20:13,235 DEBUG Snap gnome-3-38-2004 is not tracking the release channel
2023-05-29 22:20:13,456 DEBUG Snap gnome-42-2204 is installed
2023-05-29 22:20:13,457 DEBUG Snap gnome-42-2204 is not tracking the release channel
2023-05-29 22:20:13,843 DEBUG Snap gnome-calculator is installed
2023-05-29 22:20:14,263 DEBUG Snap gnome-characters is installed
2023-05-29 22:20:14,447 DEBUG Snap gnome-logs is installed
2023-05-29 22:20:14,772 DEBUG Snap gnome-system-monitor is installed
2023-05-29 22:20:15,173 DEBUG Snap john-the-ripper is installed
2023-05-29 22:20:15,174 DEBUG Snap john-the-ripper is not tracking the release channel
2023-05-29 22:20:15,590 DEBUG Snap opera is installed
2023-05-29 22:20:15,591 DEBUG Snap opera is not tracking the release channel
2023-05-29 22:20:15,860 DEBUG Snap ruby is installed
2023-05-29 22:20:15,861 DEBUG Snap ruby is not tracking the release channel
2023-05-29 22:20:22,348 DEBUG MetaPkgs: ubuntu-desktop
2023-05-29 22:20:29,924 DEBUG Foreign: 
2023-05-29 22:20:29,924 DEBUG Obsolete: cpu-g icaclient virtualbox-5.2 zoom
2023-05-29 22:20:29,925 DEBUG updateSourcesList()
2023-05-29 22:20:30,017 DEBUG rewriteSourcesList() with mirror_check
2023-05-29 22:20:30,018 DEBUG ['ubuntu-minimal', 'ubuntu-standard']
2023-05-29 22:20:30,018 DEBUG Checking pkg: ubuntu-minimal
2023-05-29 22:20:30,022 DEBUG Checking pkg: ubuntu-standard
2023-05-29 22:20:30,026 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic main restricted'
2023-05-29 22:20:30,026 DEBUG verifySourcesListEntry: deb https://cz.archive.ubuntu.com/ubuntu/ focal main restricted
2023-05-29 22:20:30,026 DEBUG url_downloadable: https://cz.archive.ubuntu.com/ubuntu//dists/focal/Release
2023-05-29 22:20:30,026 DEBUG s='https' n='cz.archive.ubuntu.com' p='/ubuntu//dists/focal/Release' q='' f=''
2023-05-29 22:20:30,236 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal main restricted' updated to new dist
2023-05-29 22:20:30,237 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic-updates main restricted'
2023-05-29 22:20:30,237 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal-updates main restricted' updated to new dist
2023-05-29 22:20:30,237 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic universe'
2023-05-29 22:20:30,238 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal universe' updated to new dist
2023-05-29 22:20:30,238 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic-updates universe'
2023-05-29 22:20:30,238 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal-updates universe' updated to new dist
2023-05-29 22:20:30,239 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic multiverse'
2023-05-29 22:20:30,239 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal multiverse' updated to new dist
2023-05-29 22:20:30,239 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic-updates multiverse'
2023-05-29 22:20:30,239 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal-updates multiverse' updated to new dist
2023-05-29 22:20:30,240 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic-security main restricted'
2023-05-29 22:20:30,240 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal-security main restricted' updated to new dist
2023-05-29 22:20:30,240 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic-security universe'
2023-05-29 22:20:30,240 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal-security universe' updated to new dist
2023-05-29 22:20:30,240 DEBUG examining: 'deb https://cz.archive.ubuntu.com/ubuntu/ bionic-security multiverse'
2023-05-29 22:20:30,241 DEBUG entry 'deb https://cz.archive.ubuntu.com/ubuntu/ focal-security multiverse' updated to new dist
2023-05-29 22:20:30,246 DEBUG running doUpdate() (showErrors=True)
2023-05-29 22:21:03,484 DEBUG openCache()
2023-05-29 22:21:05,318 DEBUG Comparing 4.15.0-211 with 
2023-05-29 22:21:05,319 DEBUG Comparing 4.15.0-88 with 4.15.0-211
2023-05-29 22:21:06,019 DEBUG /openCache(), new cache size 86403
2023-05-29 22:21:06,019 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2023-05-29 22:21:06,020 DEBUG quirks: running PreDistUpgradeCache
2023-05-29 22:21:06,020 DEBUG running Quirks.PreDistUpgradeCache
2023-05-29 22:21:06,020 INFO checking for python-dbg (auto_inst=False)
2023-05-29 22:21:06,020 INFO checking for python-doc (auto_inst=False)
2023-05-29 22:21:06,020 INFO checking for python-minimal (auto_inst=False)
2023-05-29 22:21:06,020 INFO installing python-is-python2 because python-minimal was installed
2023-05-29 22:21:06,020 DEBUG Installing 'python-is-python2' (python-minimal was installed on the system)
2023-05-29 22:21:06,052 INFO removing python-minimal because python-is-python2 is being installed
2023-05-29 22:21:06,052 DEBUG Removing 'python-minimal' (python-is-python2 is being installed on the system)
2023-05-29 22:21:06,080 INFO failed to remove python-minimal
2023-05-29 22:21:06,081 INFO checking for python-dev (auto_inst=False)
2023-05-29 22:21:06,081 INFO checking for libpython-dev (auto_inst=False)
2023-05-29 22:21:06,081 INFO checking for libpython-stdlib (auto_inst=False)
2023-05-29 22:21:06,081 INFO removing libpython-stdlib because None is being installed
2023-05-29 22:21:06,082 DEBUG Removing 'libpython-stdlib' (None is being installed on the system)
2023-05-29 22:21:06,110 INFO failed to remove libpython-stdlib
2023-05-29 22:21:06,110 INFO checking for libpython-dbg (auto_inst=False)
2023-05-29 22:21:06,111 INFO checking for python-dbg (auto_inst=True)
2023-05-29 22:21:06,111 INFO checking for python-doc (auto_inst=True)
2023-05-29 22:21:06,111 INFO checking for python-minimal (auto_inst=True)
2023-05-29 22:21:06,111 INFO installing python-is-python2 because python-minimal was installed
2023-05-29 22:21:06,111 DEBUG Installing 'python-is-python2' (python-minimal was installed on the system)
2023-05-29 22:21:06,141 INFO removing python-minimal because python-is-python2 is being installed
2023-05-29 22:21:06,141 DEBUG Removing 'python-minimal' (python-is-python2 is being installed on the system)
2023-05-29 22:21:06,141 INFO failed to remove python-minimal
2023-05-29 22:21:06,142 INFO checking for python-dev (auto_inst=True)
2023-05-29 22:21:06,142 INFO checking for libpython-dev (auto_inst=True)
2023-05-29 22:21:06,142 INFO checking for libpython-stdlib (auto_inst=True)
2023-05-29 22:21:06,142 INFO removing libpython-stdlib because None is being installed
2023-05-29 22:21:06,142 DEBUG Removing 'libpython-stdlib' (None is being installed on the system)
2023-05-29 22:21:06,142 INFO failed to remove libpython-stdlib
2023-05-29 22:21:06,142 INFO checking for libpython-dbg (auto_inst=True)
2023-05-29 22:27:33,918 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2023-05-29 22:27:33,948 DEBUG abort called
2023-05-29 22:27:33,949 DEBUG openCache()
2023-05-29 22:27:40,599 DEBUG Comparing 4.15.0-211 with 
2023-05-29 22:27:40,602 DEBUG Comparing 4.15.0-88 with 4.15.0-211
2023-05-29 22:27:41,443 DEBUG /openCache(), new cache size 115764
```

Please advise!

---

### Post by TheFu on 2023-05-30
Backup everything you can't afford to lose.

Sometimes systems have so much cruft that a fresh install is required.

Your 18.04 is running the 4.15 kernel, so you haven't moved to the HWE kernel (5.4.x).  

When I'm do an LTS-to-LTS upgrade, I do
[LIST=1]
[*]Create a backup, if I have any concern that the automated backup from last night isn't good.
[*]Move to the HWE kernel, if I'm not already there. I usually do that a few months before any planned OS release upgrade. I want to be certain the next kernel works well.
[*]sudo apt update
[*]sudo apt dist-upgrade
[*]sudo do-release-upgrade
[/LIST]

I only do 1 LTS-to-LTS upgrade.  The next LTS is a fresh install.  This cleans out cruft from all the different subsystem changes that happen over a 4 yr period.

---

### Post by guiverc on 2023-05-30
> **TheFu said:**
> Move to the HWE kernel, if I'm not already there. I usually do that a few months before any planned OS release upgrade. I want to be certain the next kernel works well.


I'll just add to what TheFu mentioned (step 2)

I usually add the HWE stack (*or if I'm already using the HWE stack; add the GA stack*) so both stacks are installed, that way after the *release-upgrade* I'll have the HWE kernel stack from the prior LTS release, plus whatever HWE is currently using for the newer LTS I just upgraded too.

Maybe this is just my understanding of TheFu's words, but I want to know that after *release-upgrade* I have an older kernel still installed.  

If GA + HWE was installed pre-*release-upgrade*, I'll have both post-*release-upgrade* too, thus rather than the "*move*" I tend to ensure both are installed.  Sure they use extra space (*esp. in /boot*) and more packages to upgrade; but the cost I feel isn't material.

Do note:  If using closed source kernel modules (esp. video kernel modules; aka nvidia) they can have rules that prevent more than a single kernel stack being installed, thus what I'm suggesting here isn't possible where using some closed-source kernel modules.

Looking up package issues is harder given *bionic* or 18.04 has already completed *standard support* (five years ending end of April 2023), thus its removed from [https://packages.ubuntu.com/](https://packages.ubuntu.com/) which makes it harder for others to help you, I'd plan the *release-upgrade* during the five years of supported life next time if you're likely to need support (*its now harder*)

I noted many Qt4 refs; Qt4 was replaced with Qt5 back in 2012 & was finally removed from both Debian & Ubuntu in 2019 (see [https://discourse.ubuntu.com/t/removing-qt-4-from-ubuntu-before-the-20-04-release/12295](https://discourse.ubuntu.com/t/removing-qt-4-from-ubuntu-before-the-20-04-release/12295)) so whatever you have that has need for those old may need you to look at.

---

### Post by MAFoElffen on 2023-05-30
> **guiverc said:**
> Do note:  If using closed source kernel modules (esp. video kernel modules; **[COLOR=#ff0000]aka nvidia[/COLOR]**) they can have rules that prevent more than a single kernel stack being installed, thus what I'm suggesting here isn't possible where using some closed-source kernel modules.
Just a sidenote-- nVidia just released their driver code for Linux Kernel 6.4 as open source. 

This should mean 'different things' by the next LTS release. (24.04)

---

### Post by baps55 on 2023-05-31
Thank you @TheFu and @guiverc for the recommendations.
I will check articles about how to move to the HWE Kernel and add the GA stack.
I am not aware of all these as this is my first LTS upgrade.

---

### Post by baps55 on 2023-06-01
> **TheFu said:**
> Backup everything you can't afford to lose.

Sometimes systems have so much cruft that a fresh install is required.

Your 18.04 is running the 4.15 kernel, so you haven't moved to the HWE kernel (5.4.x).  

When I'm do an LTS-to-LTS upgrade, I do
[LIST=1]
[*]Create a backup, if I have any concern that the automated backup from last night isn't good.
[*]Move to the HWE kernel, if I'm not already there. I usually do that a few months before any planned OS release upgrade. I want to be certain the next kernel works well.
[*]sudo apt update
[*]sudo apt dist-upgrade
[*]sudo do-release-upgrade
[/LIST]

I only do 1 LTS-to-LTS upgrade.  The next LTS is a fresh install.  This cleans out cruft from all the different subsystem changes that happen over a 4 yr period.

I found this link regarding installing HWE stack: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Should I follow the command under the section for 18.04?

---

### Post by baps55 on 2023-06-01
> **guiverc said:**
> I'll just add to what TheFu mentioned (step 2)

I usually add the HWE stack (*or if I'm already using the HWE stack; add the GA stack*) so both stacks are installed, that way after the *release-upgrade* I'll have the HWE kernel stack from the prior LTS release, plus whatever HWE is currently using for the newer LTS I just upgraded too.

Maybe this is just my understanding of TheFu's words, but I want to know that after *release-upgrade* I have an older kernel still installed.  

If GA + HWE was installed pre-*release-upgrade*, I'll have both post-*release-upgrade* too, thus rather than the "*move*" I tend to ensure both are installed.  Sure they use extra space (*esp. in /boot*) and more packages to upgrade; but the cost I feel isn't material.

Do note:  If using closed source kernel modules (esp. video kernel modules; aka nvidia) they can have rules that prevent more than a single kernel stack being installed, thus what I'm suggesting here isn't possible where using some closed-source kernel modules.

Looking up package issues is harder given *bionic* or 18.04 has already completed *standard support* (five years ending end of April 2023), thus its removed from [https://packages.ubuntu.com/](https://packages.ubuntu.com/) which makes it harder for others to help you, I'd plan the *release-upgrade* during the five years of supported life next time if you're likely to need support (*its now harder*)

I noted many Qt4 refs; Qt4 was replaced with Qt5 back in 2012 & was finally removed from both Debian & Ubuntu in 2019 (see [https://discourse.ubuntu.com/t/removing-qt-4-from-ubuntu-before-the-20-04-release/12295](https://discourse.ubuntu.com/t/removing-qt-4-from-ubuntu-before-the-20-04-release/12295)) so whatever you have that has need for those old may need you to look at.

How do I add the GA stack? I read it was default for a Server install but mine is a Desktop. I couldn't find any document regarding GA stack installation.

---

### Post by deadflowr on 2023-06-01
> How do I add the GA stack?
```
sudo apt install linux-generic
```

---

### Post by baps55 on 2023-06-01
> **deadflowr said:**
> ```
sudo apt install linux-generic
```
Thank you @deadflowr

---

### Post by guiverc on 2023-06-01
I'll add this, though I'd hope it's not necessary as already answered.

All details can be found in [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) which has already been provided.

Ubuntu Server ISOs default to the GA kernel stack by default.

Ubuntu Desktop ISOs up to 18.04 ([*which is now EOSS*]("https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/")) with initial media or the .1 media (eg. 18.04 & 18.04.1) install with the GA kernels tack by default, however 18.04.2 & later media default to using the HWE kernel stack by default on install. [Ubuntu *flavors*]("https://ubuntu.com/download/flavours") can still use this pattern, eg. installs with a Lubuntu 22.04.1 or Xubuntu 22.04 LTS media will have your system using the GA kernel stack, however installs using Lubuntu 22.04.2 & Xubuntu 22.04.2 LTS media will use the HWE kernel stack.  Ubuntu *flavors* can still follow the pattern of Ubuntu 18.04 LTS media & earlier (*why I'm mentioning the EOSS 18.04 here*).

Ubuntu Desktop ISOs starting with 20.04 all default to HWE for all.

If using the HWE kernel stack & you want to switch to GA, search the wiki for the section titled "***To downgrade from HWE/OEM to GA kernel:***" as all information is in that page, though because the ISO used to make your install sets the default of which kernel stack is default (*its not a flag or setting, its only the packages installed*), we can have different stacks installed depending on what ISO we installed with.

---

### Post by baps55 on 2023-06-11
Thank you everyone for the advice :) but I took a different route and was successful! :cool:
After doing some research I got a few more articles on this issue and everywhere it was one or two package issues reported by user which was the culprit: e.g. python, gqrx-sdr, gnuradio, libomp5, pocl-opencl-icd, clang-6, etc.
[LIST]
[*][https://ubuntuforums.org/showthread.php?t=2453051&page=2](https://ubuntuforums.org/showthread.php?t=2453051&page=2)
[*][https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1875523](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1875523)
[*][https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg5920206.html](https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg5920206.html)
[/LIST]

So I reported this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal as mentioned in the error and it launched a browser window with that issue: 

[https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-9/+bug/1886748](https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-9/+bug/1886748)

Taking idea from this and the above links, I read the 'main.log' file carefully and found that the following lines were giving a picture where the problem was due to which the upgrade was failing.

[HTML]
2023-05-29 22:21:06,111 INFO installing python-is-python2 because python-minimal was installed
2023-05-29 22:21:06,111 DEBUG Installing 'python-is-python2' (python-minimal was installed on the system)
2023-05-29 22:21:06,141 INFO removing python-minimal because python-is-python2 is being installed
2023-05-29 22:21:06,141 DEBUG Removing 'python-minimal' (python-is-python2 is being installed on the system)
2023-05-29 22:21:06,141 INFO failed to remove python-minimal
2023-05-29 22:21:06,142 INFO checking for python-dev (auto_inst=True)
2023-05-29 22:21:06,142 INFO checking for libpython-dev (auto_inst=True)
2023-05-29 22:21:06,142 INFO checking for libpython-stdlib (auto_inst=True)
2023-05-29 22:21:06,142 INFO removing libpython-stdlib because None is being installed
2023-05-29 22:21:06,142 DEBUG Removing 'libpython-stdlib' (None is being installed on the system)
2023-05-29 22:21:06,142 INFO failed to remove libpython-stdlib
2023-05-29 22:21:06,142 INFO checking for libpython-dbg (auto_inst=True)
2023-05-29 22:27:33,918 ERROR Dist-upgrade failed[/HTML]

And 'python-minimal' and 'libpython-stdlib' were Broken in the 'apt.log'

[HTML]
Broken libpython2-stdlib:amd64 Breaks on libpython-stdlib:amd64 < 2.7.15~rc1-1 @ii gK > (< 2.7.15-2)
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.15~rc1-1 @ii gK > (< 2.7.15-2)[/HTML] 

So I removed it:
[HTML] 
apt remove python-minimal
apt clean
apt autoclean
apt autoremove
[/HTML] 

Then ran the upgrade again
[HTML] do-release-upgrade -p
[/HTML]

And this time I didn't get an error related to broken packages
'apt.log' contained 
[HTML]
Log time: 2023-06-11 15:20:52.293358
Log time: 2023-06-11 15:21:03.127909
Log time: 2023-06-11 15:21:45.739526[/HTML]

'main.log' contained
[HTML]
2023-06-11 15:21:41,293 ERROR IOError/SystemError in cache.update(): 'E:Release file for http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease is not valid yet (invalid for another 2h 29min 25s). Updates for this repository will not be applied., E:Release file for http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease is not valid yet (invalid for another 2h 30min 53s). Updates for this repository will not be applied.'. Retrying (currentRetry: 2)
2023-06-11 15:21:41,293 ERROR doUpdate() failed completely
2023-06-11 15:21:41,294 DEBUG abort called[/HTML]

So I followed the link I got after putting bug report command in the terminal and as advised I adjusted /etc/apt/sources.list file from bionic to focal

[HTML]
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.agh.edu.pl/ubuntu/ focal main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to ## your rights to use the software. Also, please note that software in ## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.agh.edu.pl/ubuntu/ focal multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
deb http://security.ubuntu.com/ubuntu/ focal-security multiverse restricted main
deb http://ftp.agh.edu.pl/ubuntu/ focal-updates multiverse restricted main
[/HTML]

I ran the upgrade command again but got a different message (not an error anymore) which was promising :)

[HTML]
baps@Aspire-A515-51G:~$ sudo do-release-upgrade -p
[sudo] password for baps: 
Checking for a new Ubuntu releasePlease install all available updates for your release before upgrading.
[/HTML]

From there I followed another article

[https://fedingo.com/how-to-fix-please-install-all-available-updates-before-upgrading/](https://fedingo.com/how-to-fix-please-install-all-available-updates-before-upgrading/)

I followed Solution2 in there

[HTML]
In this case, run the following commands to upgrade state cache.
$ apt clean 
$ apt autoclean Then execute the following commands.
$ sudo apt update 
$ sudo apt upgrade -y (this installed/upgraded almost 1600 packages so took a while. I did a reboot)
$ sudo apt dist-upgrade (this installed another 250 packages) [/HTML]And voila! My Ubuntu is now upgraded to 20.04!!!I didn't had to run 'do-release-upgrade -p' command anymore or install the 5.4 Kernel, it was upgraded automatically with the above commands and old 4.15 Kernel was also removed :-)

[HTML]
baps@Aspire-A515-51G:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 
LTSRelease:    20.04
Codename:    focal
[/HTML]

---

