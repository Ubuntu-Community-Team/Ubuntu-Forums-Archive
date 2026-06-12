---
title: "Failed update 18.04 to 20.04 (An unresolvable problem occurred while ...)"
date: 2020-07-15
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2020-07-15
Ran ```
sudo do-release-upgrade -d
```

and got to:

```
Could not determine the upgrade 

An unresolvable problem occurred while calculating the upgrade. 


This was likely caused by: 
* Unofficial software packages not provided by Ubuntu 
Please use the tool 'ppa-purge' from the ppa-purge 
package to remove software from a Launchpad PPA and 
try the upgrade again. 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 



```


main log shows this:

```
2020-07-15 06:45:24,239 INFO Using config files '['./DistUpgrade.cfg.bionic']'2020-07-15 06:45:24,239 INFO uname information: 'Linux shan-Aspire-XC-780 4.15.0-111-generic #112-Ubuntu SMP Thu Jul 9 20:32:34 UTC 2020 x86_64'
2020-07-15 06:45:24,693 INFO apt version: '1.6.12ubuntu0.1'
2020-07-15 06:45:24,693 INFO python version: '3.6.9 (default, Apr 18 2020, 01:56:04) 
[GCC 8.4.0]'
2020-07-15 06:45:24,696 INFO release-upgrader version '20.04.19' started
2020-07-15 06:45:24,708 INFO locale: 'en_GB' 'UTF-8'
2020-07-15 06:45:24,771 INFO screen could not be run
2020-07-15 06:45:24,846 DEBUG Using 'DistUpgradeViewText' view
2020-07-15 06:45:24,891 DEBUG enable dpkg --force-overwrite
2020-07-15 06:45:24,925 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2020-07-15 06:45:31,112 DEBUG lsb-release: 'bionic'
2020-07-15 06:45:31,113 DEBUG _pythonSymlinkCheck run
2020-07-15 06:45:31,136 DEBUG openCache()
2020-07-15 06:45:31,136 DEBUG quirks: running PreCacheOpen
2020-07-15 06:45:31,136 DEBUG running Quirks.PreCacheOpen
2020-07-15 06:45:31,881 DEBUG /openCache(), new cache size 98456
2020-07-15 06:45:31,881 DEBUG need_server_mode(): can not find a desktop meta package or key deps, running in server mode
2020-07-15 06:45:31,881 DEBUG checkViewDepends()
2020-07-15 06:45:31,911 DEBUG running doUpdate() (showErrors=False)
2020-07-15 06:45:34,329 DEBUG openCache()
2020-07-15 06:45:35,072 DEBUG /openCache(), new cache size 98456
2020-07-15 06:45:35,072 DEBUG doPostInitialUpdate
2020-07-15 06:45:35,072 DEBUG quirks: running focalPostInitialUpdate
2020-07-15 06:45:35,072 DEBUG running Quirks.focalPostInitialUpdate
2020-07-15 06:45:36,653 DEBUG MetaPkgs: 
2020-07-15 06:45:44,432 DEBUG Foreign: adobe-flash-properties-gtk adobe-flashplugin
2020-07-15 06:45:44,432 DEBUG Obsolete: atunes brave-browser brave-keyring carla-bridge-win32 carla-bridge-wine32:i386 carla-data carla-git carla-lv2 carla-vst deb.torproject.org-keyring dpluzz dr14tmeter esound-common flacon get-iplayer gis-weather gnome-subtitles gstreamer0.10-plugins-base gstreamer0.10-plugins-good handbrake-gtk k9copy kxstudio-repos kxstudio-repos-gcc5 libaom0 libaudqt5 libav-tools libavcodec-ffmpeg-extra56 libavformat-ffmpeg56 libavutil-ffmpeg54 libbluray1 libcdio13 libcue2 libdav1d4 libdvdcss-dev libdvdcss2 libesd0 libglew1.13 libglib1.2ldbl libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk1.2 libgtk1.2-common libgtk1.2-dbg libgtk1.2-doc libid3-3.8.3c2a libiso9660-8 libmikmod2 libopenjpeg5 libplacebo18 libplacebo6 libpng12-0 libprotobuf9v5 libreadline6 libschroedinger-1.0-0 libspatialaudio0 libswresample-ffmpeg1 libswscale-ffmpeg3 libusbmuxd6 libva1 libvpx3 libwebp5 libx264-148 libx265-79 libzimg2 mac midori mod-host mod-ui mod-ui-common morituri mp3gain my-weather-indicator otter-browser python-gst0.10 python-pycdio python-support ruby-freedb shaderc skypeforlinux ttaenc tunesviewer ubuntu-cleaner unetbootin unetbootin-translations x-dev xmms xmms-crossfade xmms-cueinfo xmms-flac xmms-mp4plugin xmms-wavpack zoom
2020-07-15 06:45:44,432 DEBUG updateSourcesList()
2020-07-15 06:45:44,445 DEBUG rewriteSourcesList() with mirror_check
2020-07-15 06:45:44,445 DEBUG ['ubuntu-minimal', 'ubuntu-standard']
2020-07-15 06:45:44,445 DEBUG Checking pkg: ubuntu-minimal
2020-07-15 06:45:44,447 DEBUG Checking pkg: ubuntu-standard
2020-07-15 06:45:44,450 DEBUG examining: 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic main restricted multiverse'
2020-07-15 06:45:44,450 DEBUG verifySourcesListEntry: deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal main restricted multiverse
2020-07-15 06:45:44,450 DEBUG url_downloadable: http://mirrors.ircam.fr/pub/ubuntu/archive//dists/focal/Release
2020-07-15 06:45:44,450 DEBUG s='http' n='mirrors.ircam.fr' p='/pub/ubuntu/archive//dists/focal/Release' q='' f=''
2020-07-15 06:45:44,547 DEBUG entry 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal main restricted multiverse' updated to new dist
2020-07-15 06:45:44,548 DEBUG examining: 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic main multiverse universe restricted #Added by software-properties'
2020-07-15 06:45:44,549 DEBUG entry 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ focal main multiverse universe restricted #Added by software-properties' updated to new dist
2020-07-15 06:45:44,549 DEBUG examining: 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-updates main restricted multiverse'
2020-07-15 06:45:44,550 DEBUG entry 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-updates main restricted multiverse' updated to new dist
2020-07-15 06:45:44,550 DEBUG examining: 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-updates main multiverse universe restricted #Added by software-properties'
2020-07-15 06:45:44,551 DEBUG entry 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-updates main multiverse universe restricted #Added by software-properties' updated to new dist
2020-07-15 06:45:44,551 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted'
2020-07-15 06:45:44,551 DEBUG examining: 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic universe'
2020-07-15 06:45:44,552 DEBUG entry 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal universe' updated to new dist
2020-07-15 06:45:44,552 DEBUG examining: 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-updates universe'
2020-07-15 06:45:44,553 DEBUG entry 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-updates universe' updated to new dist
2020-07-15 06:45:44,553 DEBUG examining: 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-backports main restricted universe multiverse'
2020-07-15 06:45:44,554 DEBUG entry 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-backports main restricted universe multiverse' updated to new dist
2020-07-15 06:45:44,554 DEBUG examining: 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-backports main restricted universe multiverse #Added by software-properties'
2020-07-15 06:45:44,555 DEBUG entry 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-backports main restricted universe multiverse #Added by software-properties' updated to new dist
2020-07-15 06:45:44,555 DEBUG examining: 'deb http://archive.canonical.com/ubuntu xenial partner'
2020-07-15 06:45:44,555 DEBUG entry '# deb http://archive.canonical.com/ubuntu xenial partner' was disabled (unknown dist)
2020-07-15 06:45:44,555 DEBUG examining: 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-security main restricted multiverse'
2020-07-15 06:45:44,556 DEBUG entry 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-security main restricted multiverse' updated to new dist
2020-07-15 06:45:44,556 DEBUG examining: 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-security main multiverse universe restricted #Added by software-properties'
2020-07-15 06:45:44,557 DEBUG entry 'deb-src http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-security main multiverse universe restricted #Added by software-properties' updated to new dist
2020-07-15 06:45:44,557 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted'
2020-07-15 06:45:44,557 DEBUG examining: 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ bionic-security universe'
2020-07-15 06:45:44,558 DEBUG entry 'deb http://mirrors.ircam.fr/pub/ubuntu/archive/ focal-security universe' updated to new dist
2020-07-15 06:45:44,558 DEBUG examining: 'deb http://archive.canonical.com/ bionic partner'
2020-07-15 06:45:44,558 DEBUG verifySourcesListEntry: deb http://archive.canonical.com/ focal partner
2020-07-15 06:45:44,559 DEBUG url_downloadable: http://archive.canonical.com//dists/focal/Release
2020-07-15 06:45:44,559 DEBUG s='http' n='archive.canonical.com' p='//dists/focal/Release' q='' f=''
2020-07-15 06:45:44,722 DEBUG entry 'deb http://archive.canonical.com/ focal partner' updated to new dist
2020-07-15 06:45:49,154 DEBUG running doUpdate() (showErrors=True)
2020-07-15 06:46:29,429 DEBUG openCache()
2020-07-15 06:46:30,014 DEBUG /openCache(), new cache size 66241
2020-07-15 06:46:30,015 DEBUG need_server_mode(): can not find a desktop meta package or key deps, running in server mode
2020-07-15 06:46:31,453 DEBUG Running KeepInstalledSection rules
2020-07-15 06:46:32,033 DEBUG Kernel uname: '4.15.0-111-generic' 
2020-07-15 06:46:32,055 DEBUG nvidiaUpdate()
2020-07-15 06:46:33,006 INFO no old nvidia driver installed, installing no new
2020-07-15 06:46:33,007 DEBUG quirks: running PostDistUpgradeCache
2020-07-15 06:46:33,007 DEBUG running Quirks.PostDistUpgradeCache
2020-07-15 06:46:33,250 DEBUG Comparing 4.15.0-109 with 
2020-07-15 06:46:33,250 DEBUG Comparing 4.15.0-111 with 4.15.0-109
2020-07-15 06:46:33,251 DEBUG Comparing 5.4.0-40 with 4.15.0-111
2020-07-15 06:46:33,371 INFO installing python-is-python2 because python-minimal was installed
2020-07-15 06:46:33,371 DEBUG Installing 'python-is-python2' (python-minimal was installed on the system)
2020-07-15 06:46:33,479 DEBUG blacklist expr '^postgresql-.*[0-9]\.[0-9].*' matches 'postgresql-10-postgis-2.4'
2020-07-15 06:46:33,479 DEBUG The package 'postgresql-10-postgis-2.4' is marked for removal but it's in the removal blacklist
2020-07-15 06:46:33,558 ERROR Dist-upgrade failed: 'The package 'postgresql-10-postgis-2.4' is marked for removal but it is in the removal blacklist.'
2020-07-15 06:46:33,558 DEBUG abort called
2020-07-15 06:46:33,568 DEBUG openCache()
2020-07-15 06:46:36,989 DEBUG /openCache(), new cache size 98456



```


specifically it seems the problem:

```
2020-07-15 06:46:33,479 DEBUG The package 'postgresql-10-postgis-2.4' i[COLOR=#800000]s marked for removal but it's in the removal blacklist[/COLOR]
2020-07-15 06:46:33,558 ERROR Dist-upgrade failed: 'The package 'postgresql-10-postgis-2.4' [COLOR=#800000]is marked for removal but it is in the removal blacklist.[/COLOR]'
2020-07-15 06:46:33,558 DEBUG ***abort called***
```

so the culprit is here ?

```
sudo updatedb  ; locate  -i postgresql-10-postgis-2.4[sudo] password for shan: 
/usr/share/doc/postgresql-10-postgis-2.4
/usr/share/doc/postgresql-10-postgis-2.4-scripts
/usr/share/doc/postgresql-10-postgis-2.4/NEWS.Debian.gz
/usr/share/doc/postgresql-10-postgis-2.4/changelog.Debian.gz
/usr/share/doc/postgresql-10-postgis-2.4/copyright
/usr/share/doc/postgresql-10-postgis-2.4-scripts/NEWS.Debian.gz
/usr/share/doc/postgresql-10-postgis-2.4-scripts/changelog.Debian.gz
/usr/share/doc/postgresql-10-postgis-2.4-scripts/copyright
/usr/share/lintian/overrides/postgresql-10-postgis-2.4
/var/lib/dpkg/info/postgresql-10-postgis-2.4-scripts.list
/var/lib/dpkg/info/postgresql-10-postgis-2.4-scripts.md5sums
/var/lib/dpkg/info/postgresql-10-postgis-2.4.list
/var/lib/dpkg/info/postgresql-10-postgis-2.4.md5sums



```


How to proceed?  Any clever tips appreciated


Thanx


shan

---

### Post by ActionParsnip on 2020-07-15
[https://fossbytes.com/first-ubuntu-20-04-point-release-date-august-6/](https://fossbytes.com/first-ubuntu-20-04-point-release-date-august-6/)

when the first point release is available it will upgrade without the "-d" option. This may make things easier.

---

### Post by dino99 on 2020-07-15
Everything have been said:
- purge the non genuine package(s), like atunes, brave-browser, ...
- downgrade to genuine version if need
- let postgresql be removed
- clean the system via autoremove autoclean

and i cant comment about ircam archives, hopes they are allowing a dist upgrade; if not then swith to archive.ubuntu.com

---

### Post by shantiq on 2020-07-15
thanx guys i have now realized

**[SIZE=3]First Ubuntu 20.04 Point Release Arrives August 6 (Updated)[/SIZE]**

[COLOR=#333333][FONT=&amp]
what a dork is me hmmm i thought it was April anyway thanx [/FONT][/COLOR]

---

### Post by SeijiSensei on 2020-07-15
Yes, the first release was in April (that's why it's 20.**04**). The 20.04.1 August release cleans up any residual bugs in the initial release.

---

