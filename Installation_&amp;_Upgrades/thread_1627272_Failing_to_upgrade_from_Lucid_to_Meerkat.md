---
title: "Failing to upgrade from Lucid to Meerkat"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by Quackers on 2010-11-21
I have upgraded this system 3 or 4 times from Lucid to Meerkat without any problems. After a nasty update to my Natty installation I have re-installed Lucid and am upgrading to Meerkat, then on to Natty again. However when I try to upgrade I am getting the error below. I enclose the last bit of the log too, if that helps.
Thanks

```
2010-11-21 14:01:39,632 DEBUG running doUpdate() (showErrors=True)
2010-11-21 14:01:40,265 DEBUG openCache()
2010-11-21 14:01:40,265 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-11-21 14:01:42,539 DEBUG /openCache(), new cache size 32161
2010-11-21 14:01:42,539 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-11-21 14:08:11,952 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2010-11-21 14:08:11,952 DEBUG abort called
2010-11-21 14:08:11,954 DEBUG openCache()
2010-11-21 14:08:11,955 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-11-21 14:08:14,079 DEBUG /openCache(), new cache size 30282
2010-11-21 14:08:14,080 DEBUG enabling apt cron job
```

---

### Post by sikander3786 on 2010-11-21
This is happening from Lucid > Meerkat right?

Are you sure you haven't added any custom ppas to Lucid?

And please post the output of

```
sudo apt-get install -f
```

It would tell us about the offensive packages.

---

### Post by Quackers on 2010-11-21
Yes, boss, from Lucid to Meerkat.
I have added 3 ppa's but the upgrade disables them during the process. I have also unticked them before running the upgrade, but the error persists :-(
Here is the output you requested
```
natty64@natty64-laptop:~$ sudo apt-get install -f
[sudo] password for natty64: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Also Synaptic lists 0 broken packages.

---

### Post by Rubi1200 on 2010-11-21
Hi Quackers,
did you lock any packages on the install?

Search in Synaptic for anything where there is a Lock Version and unlock it before trying again.

Also, look for any packages which were held back because of dependencies or any backports.

Try looking in /var/log/dist-upgrade for these types of messages.

---

### Post by Quackers on 2010-11-21
> **Rubi1200 said:**
> Hi Quackers,
did you lock any packages on the install?

Search in Synaptic for anything where there is a Lock Version and unlock it before trying again.

Also, look for any packages which were held back because of dependencies or any backports.

Try looking in /var/log/dist-upgrade for these types of messages.

If I did, it was entirely accidental :-) But that would give some sense to the error in the log :-)
I'll go and do some mooching in synaptic - back soon :-)

Edit
There were no messages of any kind regarding packages held back during the install.

---

### Post by Quackers on 2010-11-21
Here's the whole main.log from var/log/dist-upgrade. It seems to me to be saying that it couldn't SystemUnLock because it isn't locked! Seems strange.
```
2010-11-21 15:18:29,105 INFO Using config files '['./DistUpgrade.cfg']'
2010-11-21 15:18:29,105 INFO uname information: 'Linux natty64-laptop 2.6.32-26-generic #47-Ubuntu SMP Wed Nov 17 15:58:05 UTC 2010 x86_64'
2010-11-21 15:18:29,106 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-11-21 15:18:29,315 INFO release-upgrader version '0.142.20' started
2010-11-21 15:18:29,457 DEBUG svg pixbuf loader failed (Error displaying image)
2010-11-21 15:18:30,417 DEBUG Using 'DistUpgradeViewGtk' view
2010-11-21 15:18:30,447 DEBUG aufsOptionsAndEnvironmentSetup()
2010-11-21 15:18:30,448 DEBUG using '/tmp/upgrade-rw-wJQm7r' as aufs_rw_dir
2010-11-21 15:18:30,448 DEBUG using '/tmp/upgrade-chroot-XLgEXT' as aufs chroot dir
2010-11-21 15:18:30,448 DEBUG enable dpkg --force-overwrite
2010-11-21 15:18:30,571 DEBUG lsb-release: 'lucid'
2010-11-21 15:18:30,592 DEBUG who -m --ips: ''
2010-11-21 15:18:30,593 DEBUG _pythonSymlinkCheck run
2010-11-21 15:18:30,627 DEBUG openCache()
2010-11-21 15:18:30,913 DEBUG /openCache(), new cache size 30282
2010-11-21 15:18:30,913 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-11-21 15:18:30,913 DEBUG checkViewDepends()
2010-11-21 15:18:30,914 DEBUG running doUpdate() (showErrors=False)
2010-11-21 15:18:31,691 DEBUG openCache()
2010-11-21 15:18:31,971 DEBUG /openCache(), new cache size 30282
2010-11-21 15:18:31,972 DEBUG doPostInitialUpdate
2010-11-21 15:18:31,972 DEBUG Plugin modules in ./plugins: deb_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py dpkg_status_plugin.py langpack_manual_plugin.py
2010-11-21 15:18:31,972 DEBUG Loading module ./plugins/deb_plugin.py
2010-11-21 15:18:31,973 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2010-11-21 15:18:31,973 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2010-11-21 15:18:31,974 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2010-11-21 15:18:31,974 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2010-11-21 15:18:31,975 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2010-11-21 15:18:31,975 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2010-11-21 15:18:31,976 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2010-11-21 15:18:31,976 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2010-11-21 15:18:31,977 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2010-11-21 15:18:31,977 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2010-11-21 15:18:31,977 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2010-11-21 15:18:31,977 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2010-11-21 15:18:35,147 DEBUG Foreign: xserver-xorg-video-intel xserver-xorg-video-ati conkyforecast r5u87x nvidia-173-modaliases nvidia-current-modaliases nvidia-current xserver-xorg-video-radeon fglrx-modaliases nvidia-96-modaliases nvidia-settings intel-gpu-tools
2010-11-21 15:18:35,147 DEBUG Obsolete: 
2010-11-21 15:18:35,148 DEBUG updateSourcesList()
2010-11-21 15:18:35,201 DEBUG rewriteSourcesList()
2010-11-21 15:18:35,204 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted'
2010-11-21 15:18:35,204 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2010-11-21 15:18:35,204 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted'
2010-11-21 15:18:35,204 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2010-11-21 15:18:35,204 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2010-11-21 15:18:35,204 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2010-11-21 15:18:35,204 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2010-11-21 15:18:35,205 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2010-11-21 15:18:35,205 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe'
2010-11-21 15:18:35,205 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2010-11-21 15:18:35,205 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe'
2010-11-21 15:18:35,205 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2010-11-21 15:18:35,205 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2010-11-21 15:18:35,205 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2010-11-21 15:18:35,205 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2010-11-21 15:18:35,205 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2010-11-21 15:18:35,205 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse'
2010-11-21 15:18:35,205 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2010-11-21 15:18:35,206 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse'
2010-11-21 15:18:35,206 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2010-11-21 15:18:35,206 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2010-11-21 15:18:35,206 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2010-11-21 15:18:35,206 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2010-11-21 15:18:35,206 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2010-11-21 15:18:35,206 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse'
2010-11-21 15:18:35,206 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse' updated to new dist
2010-11-21 15:18:35,206 DEBUG examining: 'deb http://archive.canonical.com/ubuntu lucid partner'
2010-11-21 15:18:35,206 DEBUG entry 'deb http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2010-11-21 15:18:35,206 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu lucid partner'
2010-11-21 15:18:35,207 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2010-11-21 15:18:35,207 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted'
2010-11-21 15:18:35,207 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2010-11-21 15:18:35,207 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted'
2010-11-21 15:18:35,207 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2010-11-21 15:18:35,207 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security universe'
2010-11-21 15:18:35,207 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2010-11-21 15:18:35,207 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security universe'
2010-11-21 15:18:35,207 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2010-11-21 15:18:35,207 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse'
2010-11-21 15:18:35,207 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2010-11-21 15:18:35,208 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse'
2010-11-21 15:18:35,208 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2010-11-21 15:18:35,208 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe'
2010-11-21 15:18:35,208 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe' updated to new dist
2010-11-21 15:18:35,208 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main'
2010-11-21 15:18:35,211 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-21 15:18:35,211 DEBUG examining: 'deb http://ppa.launchpad.net/r5u87x-loader/ppa/ubuntu lucid main'
2010-11-21 15:18:35,213 DEBUG entry '# deb http://ppa.launchpad.net/r5u87x-loader/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-21 15:18:35,213 DEBUG examining: 'deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu lucid main'
2010-11-21 15:18:35,216 DEBUG entry '# deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-21 15:18:35,216 DEBUG examining: 'deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu lucid main'
2010-11-21 15:18:35,218 DEBUG entry '# deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-21 15:18:42,319 DEBUG running doUpdate() (showErrors=True)
2010-11-21 15:19:09,542 DEBUG openCache()
2010-11-21 15:19:09,543 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-11-21 15:19:11,692 DEBUG /openCache(), new cache size 32161
2010-11-21 15:19:11,693 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-11-21 15:20:41,030 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2010-11-21 15:20:41,031 DEBUG abort called
2010-11-21 15:20:41,033 DEBUG openCache()
2010-11-21 15:20:41,033 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-11-21 15:20:43,281 DEBUG /openCache(), new cache size 30282
2010-11-21 15:20:43,294 DEBUG enabling apt cron job
```

---

### Post by Rubi1200 on 2010-11-21
Take a look here:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652)
You might want to investigate if you have ubuntu-desktop installed and the xorg-server comments there.

Check especially the **ubuntu-desktop** angle.

By the way, wouldn't it be easier, and less frustrating, just to create a separate partition for testing purposes?

---

### Post by Quackers on 2010-11-21
> **Rubi1200 said:**
> Take a look here:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652)
You might want to investigate if you have ubuntu-desktop installed and the xorg-server comments there.

Check especially the **ubuntu-desktop** angle.

By the way, wouldn't it be easier, and less frustrating, just to create a separate partition for testing purposes?

I have :-) This is on my separate partition :-)
My normal Meerkat installation is safe and sound ;)

---

### Post by Quackers on 2010-11-21
Thanks for that Launchpad link Rubi, it seems others have had similar problems, but some of them seem to have had broken packages. I don't appear to have any broken packages showing. 
I re-installed ubuntu-desktop as that was mentioned in the log but it doesn't seem to have had any effect.
I am conceding defeat here and am currently downloading 10.10 amd64.iso and will install that.
Thanks to Sikander3786 and Rubi1200 for your efforts :-)

---

### Post by Rubi1200 on 2010-11-21
No problem, you are more than welcome :)

Unfortunately, I just don't have the time right now to research this further.

A fresh install may well be the best solution under the circumstances.

Good luck and let me know if you need help with anything.

---

### Post by Quackers on 2010-11-21
Thanks Rubi.
I'm now back to a fully updated 10.10 with all installed drivers working fully :-)
It's almost a shame to risk that upgrading further - but I will :-)

---

### Post by sikander3786 on 2010-11-21
> It's almost a shame to risk that upgrading further - but I will

It is part of the testing you intend to do with Natty ;-) Carry on.

Good Luck!

---

### Post by jrussell88 on 2011-05-05
Hi Quackers, Did you figure out what was causing the problem?

I am also trying to upgrade from Lucid to Meerkat and getting the same error messages as you were, which I've logged on Launchpad. 

From /var/log/dist-upgrade/main.log:
> 2011-05-05 18:24:38,390 DEBUG running doUpdate() (showErrors=True)
2011-05-05 18:26:11,159 DEBUG openCache()
2011-05-05 18:26:11,159 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-05-05 18:26:13,073 DEBUG /openCache(), new cache size 32879
2011-05-05 18:26:13,074 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-05-05 18:43:48,411 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2011-05-05 18:43:48,423 DEBUG abort called
2011-05-05 18:43:48,426 DEBUG openCache()
2011-05-05 18:43:48,426 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-05-05 18:43:50,278 DEBUG /openCache(), new cache size 31587
2011-05-05 18:43:50,293 DEBUG enabling apt cron job


I've updated my installation, removed all third-party repositories, removed NVidia proprietary driver and Nouveau, and I'm still getting the same error. 

From apt.log:
> Broken playonlinux:amd64 Depends on wine [ amd64 ] < none -> 1.2.2-0ubuntu6 > ( universe/otherosfs )
  Considering wine:amd64 1 as a solution to playonlinux:amd64 -1
  Try Installing wine [ amd64 ] < none -> 1.2.2-0ubuntu6 > ( universe/otherosfs ) before changing playonlinux:amd64
    Installing wine1.2 as Depends of wine
    Installing lib32nss-mdns as Depends of wine
      Installing avahi-daemon as Depends of lib32nss-mdns
        Installing upstart as Depends of avahi-daemon
          Installing initscripts as Depends of upstart
          Installing mountall as Depends of upstart
            Installing plymouth as Depends of mountall
              Installing libdrm-nouveau1a as Depends of plymouth
              previously satisfied important dependency on plymouth-theme-ubuntu-text
              Installing plymouth-theme-ubuntu-text as Recommends of plymouth
          Installing ifupdown as Depends of upstart
        previously satisfied important dependency on libnss-mdns
        Installing libnss-mdns as Recommends of avahi-daemon


Since Nouveau caused problems during the upgrade from 10.04 to 10.10 I wonder if the version libdrm-nouveau1a is causing the failure?

---

