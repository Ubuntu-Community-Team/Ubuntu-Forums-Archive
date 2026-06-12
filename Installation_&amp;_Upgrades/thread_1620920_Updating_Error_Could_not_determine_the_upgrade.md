---
title: "Updating Error: Could not determine the upgrade"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by MdNtSnow on 2010-11-13
I'm updating from 10.04 to 10.10 using the update manager. During the update I get the following error message:

```
Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generate breaks, this may be caused by held packages.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
```

Ok so I am not upgrading to or running a pre-release version of Ubuntu but I do now know whether an unofficial software package is causing the issue. I'll include the main.log file to give you more information about the error. What do I do?

```
2010-11-13 20:11:44,030 INFO Using config files '['./DistUpgrade.cfg']'
2010-11-13 20:11:44,031 INFO uname information: 'Linux paul 2.6.32-26-generic #46-Ubuntu SMP Tue Oct 26 16:47:18 UTC 2010 x86_64'
2010-11-13 20:11:44,031 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-11-13 20:11:44,217 INFO release-upgrader version '0.142.20' started
2010-11-13 20:11:44,398 DEBUG svg pixbuf loader failed (Error displaying image)
2010-11-13 20:11:45,147 DEBUG Using 'DistUpgradeViewGtk' view
2010-11-13 20:11:45,192 DEBUG aufsOptionsAndEnvironmentSetup()
2010-11-13 20:11:45,193 DEBUG using '/tmp/upgrade-rw-Iipgpy' as aufs_rw_dir
2010-11-13 20:11:45,193 DEBUG using '/tmp/upgrade-chroot-nLsR3t' as aufs chroot dir
2010-11-13 20:11:45,193 DEBUG enable dpkg --force-overwrite
2010-11-13 20:11:45,259 DEBUG lsb-release: 'lucid'
2010-11-13 20:11:45,273 DEBUG who -m --ips: ''
2010-11-13 20:11:45,274 DEBUG _pythonSymlinkCheck run
2010-11-13 20:11:45,292 DEBUG openCache()
2010-11-13 20:11:45,713 DEBUG /openCache(), new cache size 30247
2010-11-13 20:11:45,714 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-11-13 20:11:45,714 DEBUG checkViewDepends()
2010-11-13 20:11:45,714 DEBUG running doUpdate() (showErrors=False)
2010-11-13 20:11:47,002 DEBUG openCache()
2010-11-13 20:11:47,365 DEBUG /openCache(), new cache size 30247
2010-11-13 20:11:47,365 DEBUG doPostInitialUpdate
2010-11-13 20:11:47,365 DEBUG Plugin modules in ./plugins: dpkg_status_plugin.py remove_lilo_plugin.py deb_plugin.py langpack_manual_plugin.py kdelibs4to5_plugin.py
2010-11-13 20:11:47,366 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2010-11-13 20:11:47,369 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2010-11-13 20:11:47,369 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2010-11-13 20:11:47,371 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2010-11-13 20:11:47,371 DEBUG Loading module ./plugins/deb_plugin.py
2010-11-13 20:11:47,372 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2010-11-13 20:11:47,372 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2010-11-13 20:11:47,374 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2010-11-13 20:11:47,374 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2010-11-13 20:11:47,375 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2010-11-13 20:11:47,375 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2010-11-13 20:11:47,375 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2010-11-13 20:11:47,375 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2010-11-13 20:11:50,862 DEBUG Foreign: xserver-xorg-video-intel xserver-xorg-video-ati nvidia-current xserver-xorg-video-radeon fglrx-modaliases nvidia-settings intel-gpu-tools gstreamer0.10-fluendo-plugins-mp3-partner
2010-11-13 20:11:50,863 DEBUG Obsolete: 
2010-11-13 20:11:50,864 DEBUG updateSourcesList()
2010-11-13 20:11:50,929 DEBUG rewriteSourcesList()
2010-11-13 20:11:50,933 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties'
2010-11-13 20:11:50,933 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties' updated to new dist
2010-11-13 20:11:50,933 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted'
2010-11-13 20:11:50,933 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2010-11-13 20:11:50,933 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties'
2010-11-13 20:11:50,934 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties' updated to new dist
2010-11-13 20:11:50,934 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2010-11-13 20:11:50,934 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2010-11-13 20:11:50,934 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties'
2010-11-13 20:11:50,934 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties' updated to new dist
2010-11-13 20:11:50,934 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe'
2010-11-13 20:11:50,934 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2010-11-13 20:11:50,934 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2010-11-13 20:11:50,934 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2010-11-13 20:11:50,934 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse'
2010-11-13 20:11:50,934 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2010-11-13 20:11:50,935 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2010-11-13 20:11:50,935 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2010-11-13 20:11:50,935 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse'
2010-11-13 20:11:50,935 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse' updated to new dist
2010-11-13 20:11:50,935 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse'
2010-11-13 20:11:50,935 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse' updated to new dist
2010-11-13 20:11:50,935 DEBUG examining: 'deb http://archive.canonical.com/ubuntu lucid partner'
2010-11-13 20:11:50,935 DEBUG entry 'deb http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2010-11-13 20:11:50,935 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu lucid partner'
2010-11-13 20:11:50,936 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2010-11-13 20:11:50,936 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted'
2010-11-13 20:11:50,936 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2010-11-13 20:11:50,936 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties'
2010-11-13 20:11:50,936 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties' updated to new dist
2010-11-13 20:11:50,936 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security universe'
2010-11-13 20:11:50,936 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2010-11-13 20:11:50,936 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse'
2010-11-13 20:11:50,936 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2010-11-13 20:11:50,936 DEBUG examining: 'deb http://archive.canonical.com/ lucid partner'
2010-11-13 20:11:50,937 DEBUG entry 'deb http://archive.canonical.com/ maverick partner' updated to new dist
2010-11-13 20:11:50,937 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe'
2010-11-13 20:11:50,937 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe' updated to new dist
2010-11-13 20:11:50,937 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main'
2010-11-13 20:11:50,941 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-13 20:11:59,164 DEBUG running doUpdate() (showErrors=True)
2010-11-13 20:12:32,614 DEBUG openCache()
2010-11-13 20:12:32,615 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-11-13 20:12:34,717 DEBUG /openCache(), new cache size 32155
2010-11-13 20:12:34,718 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-11-13 20:13:36,396 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2010-11-13 20:13:36,397 DEBUG abort called
2010-11-13 20:13:36,399 DEBUG openCache()
2010-11-13 20:13:36,399 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-11-13 20:13:38,449 DEBUG /openCache(), new cache size 30247
2010-11-13 20:13:38,459 DEBUG enabling apt cron job
```

---

