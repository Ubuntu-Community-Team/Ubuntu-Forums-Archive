---
title: "Can not find backport 'release-upgrader-apt'"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by jimdhall2 on 2007-10-22
I have tried an upgrade from Fiesty to Gutsy using the upgrade manager.  It fails and the upgrade log displays the following:


2007-10-22 11:37:58,804 INFO release-upgrader version '0.81' started
2007-10-22 11:38:00,085 DEBUG lsb-release: 'feisty'
2007-10-22 11:38:00,086 DEBUG _pythonSymlinkCheck run
2007-10-22 11:38:06,846 DEBUG checkViewDepends()
2007-10-22 11:38:06,847 DEBUG getRequiredBackports()
2007-10-22 11:38:11,115 ERROR IOError in cache.update(): 'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release) Unable to find expected entry  univers$/binary-i386/Packages in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 0)
2007-10-22 11:38:13,147 ERROR IOError in cache.update(): 'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release) Unable to find expected entry  univers$/binary-i386/Packages in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 1)
2007-10-22 11:38:15,132 ERROR IOError in cache.update(): 'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release) Unable to find expected entry  univers$/binary-i386/Packages in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 2)
2007-10-22 11:38:15,132 ERROR doUpdate() failed complettely
2007-10-22 11:38:21,455 ERROR Can not find backport 'release-upgrader-apt'

I'm a relative newbie, does anyone have any suggestions????

Thanks in advance,
Jim

---

### Post by jimdhall2 on 2007-10-23
I fixed my problem.  My repositories source list needed to be cleaned up.  I followed kevmaster's suggestion as listed below:
 


Re: PLEASE use the official upgrade method! (if you decide to upgrade)
My guess would be that you need to clean up your sources.list. I see references the the Ubuntu CD and to repositories like:

flomertens.keo.in
ntfs-3g.sitesweetsite.info
givre.cabspace.com

I can imagine that they aren't trusted or don't have gutsy packages yet. To cleanup our sources list press ALT+F2, type gksudo "gedit /etc/apt/sources.list" and click Run.

Ubuntu only needs:
Code:

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

(maybe replace NL with a mirror closeby)

The rest is 3rd party and might not work with Gutsy. For example, your ntfs-3g repository enables NTFS write support (for windows disks), but that's already included in Gutsy, so no need to import those unsupported 3rd party feisty reps. More details on this at my blog article: How to: Upgrade to Ubuntu Gutsy with Compiz-Fusion



After this repair the update worked fine.  I'm now running 7.10.  __________________

---

