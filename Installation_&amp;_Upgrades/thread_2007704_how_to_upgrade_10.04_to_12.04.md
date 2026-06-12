---
title: "how to upgrade 10.04 to 12.04"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-06-21
Hi all,

Is there any way upgrade Ubuntu 10.04.2 LTS, server, to 12.04 LTS?

$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

Or can I run upgrade with ubuntu-12.04-alternate-amd64.ISO.  If YES, would it ask for "upgrade" option after booting?

TIA

satimis

---

### Post by dino99 on 2012-06-21
on my end, i've tried the same command, but failed to
so i've also tried:

sudo do-release-upgrade -p
but did not get more success

sudo do-release-upgrade -d
this command did the job ;) thats curious because it normally upgrade to U+1 release.
So be carefull before hitting "Enter" key that it wants to install 12.04, not 12.10

An other way is to modify the sources.list, replacing lucid by precise; but clean the system as much as you can before updating/upgrading (autoclean/autoremove/bleachbit) and deactivate all the third party archive(s)

---

### Post by satimis on 2012-06-21
> **dino99 said:**
> on my end, i've tried the same command, but failed to
so i've also tried:

sudo do-release-upgrade -p
but did not get more success

sudo do-release-upgrade -d
this command did the job ;) thats curious because it normally upgrade to U+1 release.
So be carefull before hitting "Enter" key that it wants to install 12.04, not 12.10

An other way is to modify the sources.list, replacing lucid by precise; but clean the system as much as you can before updating/upgrading (autoclean/autoremove/bleachbit) and deactivate all the third party archive(s)

Hi,

Thanks for your advice.

I prefer to wait as advised in following thread;

[http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts](http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts)```

Upgrades from Ubuntu 10.04 LTS to 12.04 LTS do not work using the alternate CD or the server CD as a package repository. It is recommended that users running Ubuntu 10.04 LTS wait for the 12.04.1 LTS point release, scheduled for July, before upgrading. (988941) 

```

B.R.
satimis

---

