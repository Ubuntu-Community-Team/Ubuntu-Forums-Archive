---
title: "Upgrade Manager from 7.04 to 7.10 failure"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by SkorMT on 2007-10-18
I get the following error when trying to upgrade using the update manager:

> Getting upgrade prerequisites failed

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

The log directory in reference only has one file main.log that has any info and is as follows:
> :/var/log/dist-upgrade$ more main.log
2007-10-18 09:34:37,136 INFO release-upgrader version '0.81' started
2007-10-18 09:34:37,568 DEBUG lsb-release: 'feisty'
2007-10-18 09:34:37,568 DEBUG _pythonSymlinkCheck run
2007-10-18 09:34:40,181 DEBUG checkViewDepends()
2007-10-18 09:34:40,182 DEBUG getRequiredBackports()
2007-10-18 09:34:40,183 ERROR IOError in cache.update(): 'Failed to lock /var/li
b/apt/lists/lock'. Retrying (currentRetry: 0)
2007-10-18 09:34:40,184 ERROR IOError in cache.update(): 'Failed to lock /var/li
b/apt/lists/lock'. Retrying (currentRetry: 1)
2007-10-18 09:34:40,184 ERROR IOError in cache.update(): 'Failed to lock /var/li
b/apt/lists/lock'. Retrying (currentRetry: 2)
2007-10-18 09:34:40,184 ERROR doUpdate() failed complettely
2007-10-18 09:34:42,830 ERROR Can not find backport 'release-upgrader-apt'


is there a quick way to fix this lock issue?.. or just download the iso and go from there?

---

### Post by linuxwizard on 2007-10-18
Have you added extra repos to your source list ? If so try removing or disable them.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by SkorMT on 2007-10-18
naw.. most of what I did was just the updates through update manager

only been having it running for about 3 weeks or so.. trying to see if I can make a go of it at non windows.. :/

of course.. when I got home to try just a playing reboot to see if that would help (windows habit) .. power was out *sigh*

---

### Post by luminair on 2007-10-18
> **SkorMT said:**
> I get the following error when trying to upgrade using the update manager:



The log directory in reference only has one file main.log that has any info and is as follows:


is there a quick way to fix this lock issue?.. or just download the iso and go from there?

It still isn't working, and you aren't alone on this either: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980)  :popcorn:

---

### Post by luminair on 2007-10-19
Great justice bump

---

### Post by jagannath on 2007-10-21
> **linuxwizard said:**
> Have you added extra repos to your source list ? If so try removing or disable them.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

I had a similar problem. The upgrade would just stall after fetching 43 files. 
I then followed your advice, unchecked the box for " flomertens... ... edgy/main all " under third party software and tried the upgrade again.

The whole upgrade went through without a hitch and now I'm a Gutsy Gibbon user.

Thanks!

Jaggu

---

### Post by ukripper on 2007-11-28
if you had open another instance of update manager close it first. If automatic update manager is showing up avialble updates icon click on it and upgrade from there. Else it will lock upgrade process. I know this post is old but people looking for answers can get help!!

---

