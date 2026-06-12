---
title: "upgrading 12.04 to 14.04 &quot;could not calculate the upgrade&quot;"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by Kilarin on 2014-05-06
I'm trying to upgrade a 12.04 system to 14.04. But I get the following:
```
Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 

```


/var/log/dist-upgrade/apt.log
is FULL of "Broken" messages:
```

Starting 2
Investigating (0) libglib2.0-0 [ i386 ] < 2.32.4-0ubuntu1 -> 2.40.0-2 > ( libs )
Broken libglib2.0-0:i386 Breaks on libgnome-desktop-3-2 [ i386 ] < 3.4.2-0ubuntu0.2 > ( libs ) (< 3.4.2-2)
  Considering libgnome-desktop-3-2:i386 -1 as a solution to libglib2.0-0:i386 5090
  Added libgnome-desktop-3-2:i386 to the remove list
  Fixing libglib2.0-0:i386 via remove of libgnome-desktop-3-2:i386
  MarkDelete libgnome-desktop-3-2 [ i386 ] < 3.4.2-0ubuntu0.2 > ( libs ) FU=1
Investigating (0) libgirepository-1.0-1 [ i386 ] < 1.32.0-1 -> 1.40.0-1 > ( libs )
Broken libgirepository-1.0-1:i386 Breaks on libgjs0c [ i386 ] < 1.32.0-1ubuntu1 > ( libs )
  Considering libgjs0c:i386 1 as a solution to libgirepository-1.0-1:i386 231
  Added libgjs0c:i386 to the remove list
  Fixing libgirepository-1.0-1:i386 via remove of libgjs0c:i386
  MarkDelete libgjs0c [ i386 ] < 1.32.0-1ubuntu1 > ( libs ) FU=1
Investigating (0) cups-filters [ i386 ] < 1.0.18-0ubuntu0.2 -> 1.0.52-0ubuntu1 > ( net )
Broken cups-filters:i386 Conflicts on foomatic-filters [ i386 ] < 4.0.16-0ubuntu0.2 -> 4.0.17-1ubuntu1 > ( universe/text )
  Considering foomatic-filters:i386 38 as a solution to cups-filters:i386 125
  Added foomatic-filters:i386 to the remove list
  Conflicts//Breaks against version 4.0.16-0ubuntu0.2 for foomatic-filters but that is not InstVer, ignoring
Broken cups-filters:i386 Conflicts on ghostscript-cups [ i386 ] < 9.05~dfsg-0ubuntu4.2 > ( text )
  Considering ghostscript-cups:i386 25 as a solution to cups-filters:i386 125
  Added ghostscript-cups:i386 to the remove list
  Fixing cups-filters:i386 via remove of foomatic-filters:i386
  MarkDelete foomatic-filters [ i386 ] < 4.0.16-0ubuntu0.2 -> 4.0.17-1ubuntu1 > ( universe/text ) FU=1
  Fixing cups-filters:i386 via remove of ghostscript-cups:i386
  MarkDelete ghostscript-cups [ i386 ] < 9.05~dfsg-0ubuntu4.2 > ( text ) FU=1
Investigating (0) libclutter-1.0-0 [ i386 ] < 1.10.6-1~precise1 -> 1.16.4-0ubuntu2 > ( libs )
Broken libclutter-1.0-0:i386 Breaks on libcogl9 [ i386 ] < 1.10.0-0ubuntu2 > ( libs )
  Considering libcogl9:i386 3 as a solution to libclutter-1.0-0:i386 72
  Added libcogl9:i386 to the remove list
  Fixing libclutter-1.0-0:i386 via remove of libcogl9:i386
  MarkDelete libcogl9 [ i386 ] < 1.10.0-0ubuntu2 > ( libs ) FU=1
Investigating (0) libunity9 [ i386 ] < 5.12.0-0ubuntu1.1 -> 7.1.4+14.04.20140210-0ubuntu1 > ( libs )
Broken libunity9:i386 Breaks on unity-common [ i386 ] < 5.20.0-0ubuntu3 > ( gnome ) (< 7.1.2)
  Considering unity-common:i386 2 as a solution to libunity9:i386 68
  Added unity-common:i386 to the remove list
  Fixing libunity9:i386 via remove of unity-common:i386
  MarkDelete unity-common [ i386 ] < 5.20.0-0ubuntu3 > ( gnome ) FU=1

... cutting out the middle, I've got over a 1000 lines of broken messages in the log

Investigating (9) libcogl15 [ i386 ] < none -> 1.16.2-1 > ( libs )
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.10.6-1~precise1 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
  Considering libclutter-1.0-0:i386 72 as a solution to libcogl15:i386 75
  Upgrading libclutter-1.0-0:i386 due to Breaks field in libcogl15:i386
Investigating (9) libclutter-1.0-0 [ i386 ] < 1.10.6-1~precise1 -> 1.16.4-0ubuntu2 > ( libs )
Broken libclutter-1.0-0:i386 Breaks on libcogl9 [ i386 ] < 1.10.0-0ubuntu2 > ( libs )
  Considering libcogl9:i386 75 as a solution to libclutter-1.0-0:i386 72
  MarkKeep libclutter-1.0-0 [ i386 ] < 1.10.6-1~precise1 -> 1.16.4-0ubuntu2 > ( libs ) FU=0
  Holding Back libclutter-1.0-0:i386 rather than change libcogl9:i386
Investigating (9) libgdm1 [ i386 ] < none -> 3.10.0.1-0ubuntu3 > ( universe/libs )
Broken libgdm1:i386 Breaks on gdm [ i386 ] < 3.0.4-0ubuntu15.3 -> 3.10.0.1-0ubuntu3 > ( universe/gnome ) (< 3.8.3-3~)
  Considering gdm:i386 1 as a solution to libgdm1:i386 3
  Upgrading gdm:i386 due to Breaks field in libgdm1:i386
Investigating (9) gdm [ i386 ] < 3.0.4-0ubuntu15.3 -> 3.10.0.1-0ubuntu3 > ( universe/gnome )
Broken gdm:i386 Depends on gnome-session-bin [ i386 ] < 3.2.1-0ubuntu8 -> 3.9.90-0ubuntu12 > ( gnome ) (>= 3.6)
  Considering gnome-session-bin:i386 34 as a solution to gdm:i386 1
  MarkKeep gdm [ i386 ] < 3.0.4-0ubuntu15.3 -> 3.10.0.1-0ubuntu3 > ( universe/gnome ) FU=0
  Holding Back gdm:i386 rather than change gnome-session-bin:i386
Done

```

I'm assuming all of those "Broken" and "Holding Back" messages are BAD...

/var/log/dist-upgrade/main.log shows:
```
2014-05-05 22:47:02,870 INFO Using config files '['./DistUpgrade.cfg.precise']'
2014-05-05 22:47:02,870 INFO uname information: 'Linux malacandra 3.2.0-61-generic #92-Ubuntu SMP Mon Mar 31 23:50:23 UTC 2014 i686'
2014-05-05 22:47:02,870 INFO apt version: '0.8.16~exp12ubuntu10.16'
2014-05-05 22:47:02,870 INFO release-upgrader version '0.220.2' started
2014-05-05 22:47:04,774 DEBUG Using 'DistUpgradeViewText' view
2014-05-05 22:47:04,882 DEBUG aufsOptionsAndEnvironmentSetup()
2014-05-05 22:47:04,906 DEBUG using '/tmp/upgrade-rw-u35jg8' as aufs_rw_dir
2014-05-05 22:47:04,907 DEBUG using '/tmp/upgrade-chroot-8uXHdf' as aufs chroot dir
2014-05-05 22:47:04,907 DEBUG enable dpkg --force-overwrite
2014-05-05 22:47:04,945 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2014-05-05 22:47:11,807 DEBUG lsb-release: 'precise'
2014-05-05 22:47:11,809 DEBUG _pythonSymlinkCheck run
2014-05-05 22:47:11,840 DEBUG openCache()
2014-05-05 22:47:11,841 DEBUG No such plugin directory: ./plugins
2014-05-05 22:47:11,869 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2014-05-05 22:47:11,869 DEBUG plugins for condition 'trustyPreCacheOpen' are '[]'
2014-05-05 22:47:11,869 DEBUG plugins for condition 'from_precisePreCacheOpen' are '[]'
2014-05-05 22:47:11,870 DEBUG quirks: running PreCacheOpen
2014-05-05 22:47:11,870 DEBUG running Quirks.PreCacheOpen
2014-05-05 22:47:12,744 DEBUG /openCache(), new cache size 40977
2014-05-05 22:47:12,745 DEBUG need_server_mode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2014-05-05 22:47:12,745 DEBUG checkViewDepends()
2014-05-05 22:47:12,766 DEBUG running doUpdate() (showErrors=False)
2014-05-05 22:47:20,975 DEBUG openCache()
2014-05-05 22:47:20,975 DEBUG failed to SystemUnLock() (E:Not locked) 
2014-05-05 22:47:31,123 DEBUG /openCache(), new cache size 40977
2014-05-05 22:47:31,123 DEBUG doPostInitialUpdate
2014-05-05 22:47:31,123 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2014-05-05 22:47:31,123 DEBUG plugins for condition 'trustyPostInitialUpdate' are '[]'
2014-05-05 22:47:31,123 DEBUG plugins for condition 'from_precisePostInitialUpdate' are '[]'
2014-05-05 22:47:31,124 DEBUG quirks: running from_precisePostInitialUpdate
2014-05-05 22:47:31,124 DEBUG _checkPae
2014-05-05 22:47:31,216 DEBUG _test_and_warn_for_unity_3d_support: no unity running
2014-05-05 22:47:37,736 DEBUG Foreign: 
2014-05-05 22:47:37,736 DEBUG Obsolete: libedataserver1.2-14 language-support-en pytraffic-data nemo gir1.2-muffin-3.0 opentyrian muffin-common soulfu-data nemo-data autodownloader cinnamon-session libcinnamon-desktop0 nemo-fileroller naev-data naev sandboxgamemaker-data vavoom libnotify1 language-support-writing-en libmuffin0 cinnamon-common mineescape gnome-inform7 libgtkhtml2-0 gir1.2-cinnamondesktop-3.0 truecrypt cjs cinnamon-settings-daemon cinnamon-desktop-data linux-image-2.6.32-25-generic libegroupwise1.2-13 astromenace xjigmanager libdvdcss2 pytraffic scourge-data thunderbird-mozilla-build cinnamon-translations libnemo-extension1 linux-image-2.6.38-13-generic libcinnamon-menu-3-0 picsaw cinnamon-session-common gir1.2-cmenu-3.0 grub-customizer libcjs0c virtualbox-4.0 ttf-freecol opentyrian-data cube-escape getdeb-repository soulfu scourge w32codecs sandboxgamemaker-all sandboxgamemaker-bin bibledave qdvdauthor-data cinnamon passwordsafe deng astromenace-data
2014-05-05 22:47:37,736 DEBUG updateSourcesList()
2014-05-05 22:47:38,071 DEBUG rewriteSourcesList()
2014-05-05 22:47:38,077 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted'
2014-05-05 22:47:38,077 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted' updated to new dist
2014-05-05 22:47:38,077 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted'
2014-05-05 22:47:38,077 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted' updated to new dist
2014-05-05 22:47:38,078 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise universe'
2014-05-05 22:47:38,078 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty universe' updated to new dist
2014-05-05 22:47:38,078 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe'
2014-05-05 22:47:38,078 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe' updated to new dist
2014-05-05 22:47:38,078 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse'
2014-05-05 22:47:38,078 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse' updated to new dist
2014-05-05 22:47:38,078 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse'
2014-05-05 22:47:38,079 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse' updated to new dist
2014-05-05 22:47:38,079 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security main restricted'
2014-05-05 22:47:38,079 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security main restricted' updated to new dist
2014-05-05 22:47:38,079 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu precise-security main restricted'
2014-05-05 22:47:38,079 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted' updated to new dist
2014-05-05 22:47:38,079 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security universe'
2014-05-05 22:47:38,080 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security universe' updated to new dist
2014-05-05 22:47:38,080 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu precise-security universe'
2014-05-05 22:47:38,080 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu trusty-security universe' updated to new dist
2014-05-05 22:47:38,080 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security multiverse'
2014-05-05 22:47:38,080 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security multiverse' updated to new dist
2014-05-05 22:47:38,080 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu precise-security multiverse'
2014-05-05 22:47:38,080 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse' updated to new dist
2014-05-05 22:47:38,081 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe'
2014-05-05 22:47:38,081 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted main multiverse universe' updated to new dist
2014-05-05 22:47:38,083 DEBUG running doUpdate() (showErrors=True)
2014-05-05 22:48:25,511 DEBUG openCache()
2014-05-05 22:48:25,512 DEBUG failed to SystemUnLock() (E:Not locked) 
2014-05-05 22:48:34,401 DEBUG /openCache(), new cache size 46280
2014-05-05 22:48:34,402 DEBUG need_server_mode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2014-05-05 22:48:43,972 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2014-05-05 22:48:43,972 DEBUG abort called
2014-05-05 22:48:43,999 DEBUG openCache()
2014-05-05 22:48:51,567 DEBUG /openCache(), new cache size 40977
2014-05-05 22:48:51,598 DEBUG enabling apt cron job
```

I went to Synaptic Package Manager/Settings/Repositories  to bring up the Software Sources gui, went to the "other software" tab and unchecked EVERYTHING.  Still get the same error.

Is there a solution to this problem better than just doing a clean install of 14.04 over my old system?

Thank you in advance for your help

---

### Post by monkeybrain20122 on 2014-05-06
Then don't "upgrade", for the time you spend trying to figure out what's wrong you could have re-install many times over. "Upgrade" is flaky and takes several hours even if works,  but there is a good chance that  it may leave you with a broken system after all that and you will then spend days to try to trouble shoot it. A clean install takes 15 minutes and maybe after that half an hour to reinstall your software.  

Why is it that everyone tries to 'upgrade'? It makes no sense.

P.S. For what it is worth you probably have ppas so the upgrader or whatever got confused with the package versions.

---

### Post by deadflowr on 2014-05-06
> **monkeybrain20122 said:**
>   
Why is it that everyone tries to 'upgrade'? It makes no sense.


It's less of a why do people try to upgrade, and more of a why do people try to upgrade using an, as of right now, unsupported method.
Upgrades from 12.04 to 14.04 are not yet officially supported.
To do so, you have to use the -d option which means development, which means it is still considered under development.

The only officially supported method to run a net-upgrade from 12.04 is to hop, skip and jump.
From 12.04 > 12.10 >(skip 13.04,EOL) > 13.10> 14.04.
Not exactly a safe way to do it, as any one of those upgrades could be a bust.

Far easier and safer, at this time, to do a clean run.

When net-upgrades do become officially supported, then we'll see.


All that being stated, To the OP: What version does the system say you are on now?
And are there any problems, aside from the release-upgrade?

---

