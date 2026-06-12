---
title: "Unable to upgrade to 10.04.1"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by joao82 on 2010-08-31
Hi,
I'm using Ubuntu 10.04 (upgraded from 9.10) and I can't find a way to upgrade to the new 10.04.1 version.
I've updated all the software sources, changed my country location to US, and even generated a new sources.list file, but my update manager never displays an option to make an upgrade to 10.04.1


What am I missing?

Here are my current settings:
```
###### Ubuntu Main Repos
deb http://pt.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse

###### Ubuntu Update Repos
deb http://pt.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
deb http://pt.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://pt.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu lucid partner
```

[IMG]http://a.imageshack.us/img820/214/screenshotsoftwaresourc.png[/IMG]

[IMG]http://a.imageshack.us/img831/214/screenshotsoftwaresourc.png[/IMG]

thanks in advance.

---

### Post by dabl on 2010-08-31
I don't see anything wrong with your source repos.

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
lsb_release -a
```


What does it say?

---

### Post by 3Miro on 2010-08-31
Just run regular update, 10.04.1 is not a new release, it is just 10.04 with all the current updates. They do this because there have been many updates since the original release and it is better if users can just install more up-to-date packages from the start (I think they do this only for LST releases).

---

### Post by joao82 on 2010-08-31
Thanks dabl and 3Miro, it makes sense.
Looks like I'm running 10.04.1 all along.

```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid
```

---

