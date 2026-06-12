---
title: "Add/Remove Error"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by esplode on 2008-01-10
Whenever I try to install anything from the Add/Remove Applications thing, it gives me an error that says
```
The list of applications is not availabe
Click on 'Reload' to load it. To reload the list you need a working internet connection.
```
After that, I click the Refresh button and it brings up a down loader and then finishes downloading the package information. Then after I've done that it just keeps giving me the error. I even went into the package manager and tried updating it from there and it still didn't work. Anyone know how to fix this?

Also, if this helps, I'm using Ubuntu 7.10 and I do have an an internet connection.

---

### Post by zipperback on 2008-01-10
> **esplode said:**
> Whenever I try to install anything from the Add/Remove Applications thing, it gives me an error that says
```
The list of applications is not availabe
Click on 'Reload' to load it. To reload the list you need a working internet connection.
```
After that, I click the Refresh button and it brings up a down loader and then finishes downloading the package information. Then after I've done that it just keeps giving me the error. I even went into the package manager and tried updating it from there and it still didn't work. Anyone know how to fix this?

Also, if this helps, I'm using Ubuntu 7.10 and I do have an an internet connection.



What happens when you type:

```
sudo apt-get update
```

- zipperback
:popcorn:

---

### Post by esplode on 2008-01-10
Nope. It still isn't letting me install anything, but in the terminal it is saying
```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 http://ca.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Hit http://ca.archive.ubuntu.com gutsy-updates Release
Hit http://ca.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 1B in 0s (7B/s)
Reading package lists... Done

```

---

### Post by taurus on 2008-01-10
You don't have any repos available in /etc/apt/sources.list to install stuff.  Therefore, you need to go into System -> Administration -> Synaptic -> Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code and CDROM at the bottom window.  Close it and press Refresh.  Now, you should be able to install whatever you have in mind.

---

### Post by esplode on 2008-01-10
Thanks. That worked perfectly. :)

---

