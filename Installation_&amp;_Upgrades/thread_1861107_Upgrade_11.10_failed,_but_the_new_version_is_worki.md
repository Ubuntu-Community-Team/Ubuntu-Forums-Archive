---
title: "Upgrade 11.10 failed, but the new version is working..."
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by hannes88 on 2011-10-15
As many others, I also upgraded to Ubuntu 11.10. Went good, downloaded all updates and made nearly all installations, then with just a few minutes left of the installation step I got an error message saying that something went wrong.

I rebooted the system and to my surprise, Ubuntu 11.10 was there. Now I run the new version and it seems to be working good.

I read in /var/log/dist-upgrade/main.log (see below) that something went wrong with the flashplugin-installer.

I ran the commands:
apt-clean
apt-update
apt-upgrade

and then it installed some packages, for example the flashplugin-installer.

Now to my question:

Is there any way to find out if the upgrade succeeded or not? (Or if something is missing, what's really missing?)


last lines from /var/log/dist-upgrade/main.log:

2011-10-14 13:23:54,595 WARNING unexpected target md5sum, skipping: '/usr/bin/pycompile'
2011-10-14 13:23:54,620 DEBUG killing update-notifier
2011-10-14 13:23:54,634 DEBUG killing kblueplugd kbluetooth4
2011-10-14 13:23:54,648 DEBUG killing gnome-screensaver
2011-10-14 13:23:54,661 DEBUG quirks: running oneiricStartUpgrade
2011-10-14 13:23:54,661 DEBUG oneiric StartUpgrade quirks
2011-10-14 13:23:54,677 DEBUG apt btrfs snapshots supported: False
2011-10-14 13:23:54,677 INFO cache.commit()
2011-10-14 13:23:54,677 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-10-14 14:22:01,755 ERROR got an error from dpkg for pkg: 'flashplugin-installer': 'dependency problems - leaving unconfigured'
2011-10-14 14:22:01,770 DEBUG running apport_pkgfailure() flashplugin-installer: dependency problems - leaving unconfigured
2011-10-14 14:22:01,770 ERROR got an error from dpkg for pkg: 'flashplugin-installer': 'dependency problems - leaving unconfigured'
2011-10-14 14:23:33,406 ERROR Exception during pm.DoInstall()
Traceback (most recent call last):
  File "/tmp/update-manager-c19lM7/DistUpgradeView.py", line 201, in run
    res = pm.do_install(self.writefd)
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
2011-10-14 14:23:33,456 ERROR SystemError from cache.commit(): installArchives() failed
2011-10-14 14:23:33,456 ERROR found exception: 'E:Sub-process /usr/bin/dpkg returned an error code (1)'
2011-10-14 14:25:45,025 DEBUG enabling apt cron job
2011-10-14 14:25:45,042 DEBUG Running PostInstallScript: './xorg_fix_proprietary.py'
2011-10-14 14:26:46,325 DEBUG enabling apt cron job

---

### Post by 23dornot23d on 2011-10-18
There were a lot of people saying it had failed on the Flash-installer ... the upgrades completed afterwards though.

But check my link below on failed upgrades to see if there is anything that helps you ........

---

### Post by hannes88 on 2011-10-24
Your link below?

---

