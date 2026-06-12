---
title: "do-release-upgrade failing for 7.10"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Noccy on 2007-10-20
I get this error trying to upgrade to 7.10

> Done downloading
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


A fatal error occured
Please report this as a bug and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

  File "/tmp/tmpZvmF4m/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmpZvmF4m/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmpZvmF4m/DistUpgradeControler.py", line 1251, in fullUpgrade
    if not self.getRequiredBackports():

  File "/tmp/tmpZvmF4m/DistUpgradeControler.py", line 1183, in getRequiredBackports
    self.cache._fetchArchives(fetcher, pm)

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 160, in _fetchArchives
    if not pm.GetArchives(fetcher, self._list, self._records):

SystemError: E:I wasn't able to locate file for the libgnomevfs2-common package. This might mean you need to manually fix this package.



**main.log**
> 2007-10-21 02:11:19,669 INFO release-upgrader version '0.81' started
2007-10-21 02:11:19,757 DEBUG lsb-release: 'feisty'
2007-10-21 02:11:22,131 DEBUG _pythonSymlinkCheck run
2007-10-21 02:11:23,237 DEBUG Have broken pkgs, trying to fix them
2007-10-21 02:11:23,642 DEBUG checkViewDepends()
2007-10-21 02:11:23,643 DEBUG getRequiredBackports()
2007-10-21 02:11:25,710 DEBUG marking 'release-upgrader-apt' for install
2007-10-21 02:11:25,820 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-21 02:11:25,960 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmpZvmF4m/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmpZvmF4m/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmpZvmF4m/DistUpgradeControler.py", line 1251, in fullUpgrade
    if not self.getRequiredBackports():

  File "/tmp/tmpZvmF4m/DistUpgradeControler.py", line 1183, in getRequiredBackports
    self.cache._fetchArchives(fetcher, pm)

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 160, in _fetchArchives
    if not pm.GetArchives(fetcher, self._list, self._records):

SystemError: E:I wasn't able to locate file for the libgnomevfs2-common package. This might mean you need to manually fix this package.

apt.log is empty

A apt-get upgrade gives me:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz-gnome: Depends: libmetacity0 (>= 1:2.19.5) but 1:2.18.2-0ubuntu1.1 is installed
                Depends: libwnck22 (>= 2.19.5) but it is not installed
                Depends: libcompizconfig-backend-gconf but it is not installed
  ekiga: Depends: libopal-2.2 (>= 2.2.11~dfsg1-1ubuntu1) but it is not installed or
                  libopal-2.2-ptrace (>= 2.2.11~dfsg1-1ubuntu1) but it is not installed or
                  libopal-2.2-develop (>= 2.2.11~dfsg1-1ubuntu1) but it is not installed
         Depends: libpt-1.10.0 (>= 1.10.10) but 1.10.3-0ubuntu1 is installed
  libgnomeui-0: Depends: libgnomeui-common (>= 2.20) but 2.17.92-0ubuntu1 is installed
  libgnomevfs2-0: Depends: libgnomevfs2-common (>= 1:2.20) but 1:2.18.1-0ubuntu1 is installed
  libgnomevfs2-extra: Depends: libgnomevfs2-common (>= 1:2.20) but 1:2.18.1-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

Any ideas? :)

Cheers,
Chris

---

### Post by Noccy on 2007-10-23
I get this after doing a apt-get -f upgrade. System is still stuck somewhere between 7.04 and 7.10:

> dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/metacity-common_1%3a2.20.0-0ubuntu3_all.deb
 /var/cache/apt/archives/libgnomevfs2-common_1%3a2.20.0-0ubuntu3_all.deb
 /var/cache/apt/archives/libgnomeui-common_2.20.1.1-0ubuntu1_all.deb
 /var/cache/apt/archives/gnome-power-manager_2.20.0-0ubuntu6_i386.deb
 /var/cache/apt/archives/gnome-applets_2.20.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

All of those failures are due to this occuring on every one of them:

> Preparing to replace gnome-applets 2.18.0-0ubuntu1 (using .../gnome-applets_2.20.0-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_set_translation_domain
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_set_translation_domain
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.20.0-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127

Help please? Would like to get it back to normal without having to reinstall the entire system.

Cheers,
Chris

---

### Post by micahrent on 2007-11-08
I am having the exact same problem on two computers. All I know is that in both cases the computer were shutdown while upgrading. Opps.

---

### Post by toniNZ on 2008-06-04
Hi, 
I have also a problem when upgrading from gutsy (7.10) to hardy. Although apparently not the same as previously stated.

The update stop and a look in the main.log indicates that it wants to delete ubuntu-desktop, which is in the black list. Apparently this issue has been found in previous distribution. I tried to delete all proprietary sources (at least I hope so).

Here the error msg:
[FONT="Courier New"]A unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 
[/FONT]

The main.log final line is:
2008-06-04 19:00:37,861 DEBUG The package 'ubuntu-desktop' is marked for removal but it's in the removal blacklist
2008-06-04 19:00:37,866 ERROR Dist-upgrade failed: 'A essential package would have to be removed'

I uploaded the main.log file. The sources.list file contains:

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-proposed main universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse 

The funny thing is that I did the upgrade on my laptop and there was no problems (on my laptop the update-manager proposed a dist update, which I did, on the desktop for unknown reasons no proposition so I want to go though the do-release-upgrade command).

Cheers

toni

---

