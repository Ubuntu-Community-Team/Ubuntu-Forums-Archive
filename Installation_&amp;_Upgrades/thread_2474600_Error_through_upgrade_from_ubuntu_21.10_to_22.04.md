---
title: "Error through upgrade from ubuntu 21.10 to 22.04"
date: 2022-05-03
forum: Installation &amp; Upgrades
---

### Post by debaculus on 2022-05-03
I have upgrade today by invoking ```
do-release-uprade
``` on the command line and this rendered my system broken with the following log entry
at the end of /var/log/dist-upgrade/date/main.log right before the upgrade process crashed

2022-05-03 14:59:42,632 DEBUG quirks: running StartUpgrade
2022-05-03 14:59:42,632 DEBUG running Quirks.StartUpgrade
2022-05-03 14:59:42,632 DEBUG skipping 'README' (no '.')
2022-05-03 14:59:42,632 DEBUG killing update-notifier
2022-05-03 14:59:42,639 DEBUG killing kblueplugd kbluetooth4
2022-05-03 14:59:42,647 DEBUG setup poke timer for the screensaver
2022-05-03 14:59:42,652 DEBUG apt btrfs snapshots supported: False
2022-05-03 14:59:42,652 INFO cache.commit()
2022-05-03 15:00:19,165 ERROR got an error from dpkg for pkg: '/tmp/apt-dpkg-install-LvrpZt/51-yaru-theme-gnome-shell_22.04.4_all.deb': 'new yaru-theme-gnome-shell package pre-installation script subprocess returned error exit status 1'
2022-05-03 15:00:19,166 DEBUG running apport_pkgfailure() yaru-theme-gnome-shell: new yaru-theme-gnome-shell package pre-installation script subprocess returned error exit status 1
2022-05-03 15:00:24,955 ERROR Exception during pm.DoInstall()
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-h1r20e4t/DistUpgrade/DistUpgradeView.py", line 220, in run
    res = pm.do_install(self.writefd)
apt_pkg.Error: E:Sub-process /usr/bin/dpkg returned an error code (1)
2022-05-03 15:00:24,997 ERROR SystemError from cache.commit(): installArchives() failed
2022-05-03 15:00:24,997 ERROR found exception: 'E:Sub-process /usr/bin/dpkg returned an error code (1)'
2022-05-03 15:00:38,196 DEBUG Running PostInstallScript: './xorg_fix_proprietary.py'
2022-05-03 15:00:38,242 DEBUG Running PostInstallScript: '/usr/lib/ubuntu-advantage/upgrade_lts_contract.py

I could heal this a bit by removing yaru-theme-gnome-shell and some other packages. yaru-theme-gnome-shell  
seems to be the culprit here!?

---

### Post by k-schindler on 2022-05-13
you cannot remove it, if you try it will also remove the gnome shell and many other packages depending on it.
what i tried: 
after the white screen, rebooted and selected recovery mode and then repair. done this several time
after that i was able to boot and start and login.
**BUT**
the shell is still v. 41.
most stuff works, even firefox is on snap, but that means no extension manager plug in. and installing  the deb package extensions manager fails because of the yaru error....
and the error you mentioned keeps popping up.
it just sucks. this happened on my laptop. my pc upgraded from 21.10 to 22.04 without a problem...

so i restored my 21.10 backup and hope i see a fix of this coming some time and catch the notification of it...
googling a bit it seems that this problem is very old and happened in previous versions.
obviously release management is not working and having bug fixes merged with the main fork as the same bugs pop up again and again.

---

