---
title: "Need help upgrading from Ubuntu 16.04.7 LTS with ESM enabled"
date: 2021-09-22
forum: Installation &amp; Upgrades
---

### Post by jrahman2 on 2021-09-22
I am attempting to execute ```
do-release-upgrade -m server
``` via SSH on this NIS client after I have ensured that all the installed packages are up-to-date and I have rebooted the machine. While attempting to upgrade, the above command terminates with exit status 1 without any helpful debug message as follows.

```
Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
Hit http://de.archive.ubuntu.com/ubuntu xenial InRelease
Hit http://de.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit http://de.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu xenial InRelease
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Hit https://esm.ubuntu.com/infra/ubuntu xenial-infra-security InRelease
Hit https://esm.ubuntu.com/infra/ubuntu xenial-infra-updates InRelease
Fetched 109 kB in 0s (0 B/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done


Restoring original system state


Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
=== Command terminated with exit status 1 (Wed Sep 22 11:25:38 2021) ===

```

I found the following information in [FONT=courier new]/var/log/dist-upgrade/main.log[/FONT].

```

INFO Using config files '['./DistUpgrade.cfg.xenial', '/etc/update-manager/release-upgrades.d/ubuntu-advantage-upgrades.cfg']'
INFO uname information: 'Linux 4.4.0-216-generic #249-Ubuntu x86_64'
INFO apt version: '1.2.35'
INFO python version: '3.5.2 (default) [GCC 5.4.0 20160609]'
INFO release-upgrader version '18.04.45' started
INFO locale: 'en_US' 'UTF-8'
DEBUG Using 'DistUpgradeViewText' view
DEBUG enable dpkg --force-overwrite
DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
DEBUG lsb-release: 'xenial'
DEBUG _pythonSymlinkCheck run
DEBUG openCache()
DEBUG No such plugin directory: ./plugins
DEBUG plugins for condition 'PreCacheOpen' are '[]'
DEBUG plugins for condition 'bionicPreCacheOpen' are '[]'
DEBUG plugins for condition 'from_xenialPreCacheOpen' are '[]'
DEBUG quirks: running PreCacheOpen
DEBUG running Quirks.PreCacheOpen
DEBUG /openCache(), new cache size 94661
DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
DEBUG checkViewDepends()
DEBUG running doUpdate() (showErrors=False)
DEBUG openCache()
DEBUG /openCache(), new cache size 94661
DEBUG doPostInitialUpdate
DEBUG plugins for condition 'PostInitialUpdate' are '[]'
DEBUG plugins for condition 'bionicPostInitialUpdate' are '[]'
DEBUG plugins for condition 'from_xenialPostInitialUpdate' are '[]'
DEBUG quirks: running bionicPostInitialUpdate
DEBUG running Quirks.bionicPostInitialUpdate
DEBUG abort called
DEBUG openCache()
DEBUG /openCache(), new cache size 94661 
```
Can you please help me overcome this issue? Thank you!

---

### Post by grahammechanical on 2021-09-22
I am not in any way suggesting that this is the answer, but you should disable that PPA in the sources.list file by commenting it out with a # or removing the line completely. The upgrade process will rename all the other Sources or Repositories (xenial) to find the 18.04 repositories (bionic).

It is quite likely that the esm repositories will remain as sources but pointing to bionic repositories. I just do not know.

Regards

---

### Post by coffeecat on 2021-09-22
@jrahman2, I have restored the original text of your post and removed the solved tag.

Replacing your original text with "[Wiped the system -- Problem no longer exists]" is discourteous to the forum member who took time and trouble to try and help and, by removing context, makes their post meaningless. Marking the thread as solved was misleading - you have not found a solution. Those searching for a solution to their own similar problems in the expectation that your problem was actually solved will find their time has been wasted.

You could have left your first post untouched and simply posted that you had abandoned the effort to find a solution, and also acknowledged grahammechanical's contribution.

Thread closed.

---

