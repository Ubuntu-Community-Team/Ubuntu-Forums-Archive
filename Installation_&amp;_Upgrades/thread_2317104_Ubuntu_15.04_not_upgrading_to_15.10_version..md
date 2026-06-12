---
title: "Ubuntu 15.04 not upgrading to 15.10 version."
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by rishabh1351995 on 2016-03-13
I have an Ubuntu 15.04 version installed but when I try upgrading it to version 15.10 it gives "Failed to fetch error" , I have tried both command line and software updater to no avail .

---

### Post by bozo_the_grey on 2016-03-14
can you please give more details ? at which point of the installation process you get this error ?

---

### Post by Edison_James on 2016-03-14
> **rishabh1351995 said:**
> I have an Ubuntu 15.04 version installed but when I try upgrading it to version 15.10 it gives "Failed to fetch error" , I have tried both command line and software updater to no avail .

Welcome to the forum. From my own experience, upgrading ubuntu is problematic, often bringing problems and glitches that you never had before the upgrade. As a result I no longer upgrade but wait for a newer version, then do a new clean install of that new version.
I know this doesn't solve your issue directly but since 16.04 will be available within a few weeks and is an LTS version (long term support)
perhaps you could wait until then and do a new install?:D

edit; you may want to look at this thread.
[http://ubuntuforums.org/showthread.php?t=2316723](http://ubuntuforums.org/showthread.php?t=2316723)

---

### Post by grahammechanical on 2016-03-14
Failed to fetch errors usually occur when we try to update/upgrade and one or more software repositories are unavailable. The apt-get update command will usually list what repositories are unavailable.

It is usual to fully update an existing version of Ubuntu before trying to upgrade to the next version. In the case of 15.04 this may prove difficult as 15.04 reached end of life 4th February 2016. The 15.04 repositories may no longer be available because they may have been archived and moved to the old-releases.ubuntu.com server.

I do not know if this is the case with 15.04. But if it is then we have to follow this guide

[https://help.ubuntu.com/community/EOLUpgrades#SpecificOlder](https://help.ubuntu.com/community/EOLUpgrades#SpecificOlder)

Basically, the idea is to edit the /etc/apt/sources.list file and change the URLs to point old-releases.ubuntu.com instead of the archive they are pointing to. For example, change this 

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid multiverse

to this

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) vivid multiverse

And do it to all the URLs. Then run apt-get update; apt-get upgrade & apt-get dist-upgrade. And then see if update manager will offer to upgrade to 15.10.

A lot depends on what URLs those failed to fetch errors are referring to. If those errors are about vivid URLs then this advice may be useful. If those errors are regarding some other repository, then following this advice may make matters worse.

Backup the data and fresh install 15.10 and then upgrade to 16.04 before the end of August otherwise the same situation will occur.

Regards.



[URL="https://help.ubuntu.com/community/EOLUpgrades#SpecificOlder"]


[/URL]

---

### Post by rishabh1351995 on 2016-03-15
It breaks when I click on upgrade and then it starts fetching software packages which results in the error.

---

### Post by kansasnoob on 2016-03-16
Please copy-n-paste the full terminal output of this command and post it here so we can see if there are any errors:

```
sudo apt-get update
```

---

### Post by rishabh1351995 on 2016-03-28
[IMG]http://imgur.com/gallery/cbr7EwJ/new[/IMG][IMG]http://i.imgur.com/cbr7EwJ.png[/IMG]

---

