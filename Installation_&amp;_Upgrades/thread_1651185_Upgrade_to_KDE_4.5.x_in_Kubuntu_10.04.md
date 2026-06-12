---
title: "Upgrade to KDE 4.5.x in Kubuntu 10.04?"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by chip616 on 2010-12-22
It would appear than one cannot search for numbers when doing a search of the forum....  (Or, at least, I can't figure out how to find "KDE 4.5" in the forum.)

I want to upgrade Kubuntu 10.04 to KDE 4.5.x.  I found [this thread]("http://ubuntuforums.org/showthread.php?t=1568166&highlight=pager%2C+background") giving some instructions.

I executed the command:

```
sudo add-apt-repository ppa:kubuntu-ppa/backport
```

Synaptic reports that the backport repository is indeed listed, and active, as follows:

> [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) lucid main

I also refreshed the package list.

I then executed the command:

```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

It ran, but reported that I already had the most recent version of the KDE desktop available.  Sadly, checking my installation shows 4.4.2 as the installed version.

So, what went wrong?

Frank.

---

### Post by chip616 on 2010-12-22
OK, the problem has gone away, but I am not sure why.

I did an update with KPackageKit.  That upgraded me to KDE 4.5.3, though 43 packages are listed as 'blocked updates' for some reason.

I'm not listing this as solved, as it really isn't.  I still don't know why the apt-get command did not do the job.  And, I don't know why there are 43 packages listed as 'blocked updates' either.

If anyone has some insight on this, I'd still like to know.

thanks

Frank.

---

