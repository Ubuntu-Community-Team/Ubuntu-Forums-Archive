---
title: "Upgrading Files in Repos?"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by VideoAddicted on 2010-08-22
Some of the programs that I can install from the repos are outdated.  Particularly, Amarok.  In the repos 2.3.0 is available and I need 2.3.1 to fix a bug that's occurring on my system.  How do accomplish this without having duplicates on the system along with any such error that might complicate the functioning of Amarok.

Am running 10.04

---

### Post by howefield on 2010-08-22
When you want a more up to date version of an application than is in the Ubuntu repository, you'll need to go to the programs webpage and look for a .deb package or repository that you can add to your package sources.

Follow the links here.

[http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download)

---

### Post by VideoAddicted on 2010-08-22
I did as you recommended, and downloaded amarok using the terminal command mentioned on their webpage.  Then my terminal worked it's way through and then informed me that no files had been added, removed, or modified in any way.

---

### Post by howefield on 2010-08-22
Lucid has Amarok 2.3.0 in the repository after a fresh install of 10.04.1, adding the Amarok repositories makes 2.3.1 available.

```
sudo add-apt-repository ppa:kubuntu-ppa/backports
```
```
sudo apt-get update
```
```
sudo apt-get install amarok
```

So if you haven't had any files changed, you either already have 2.3.1 or perhaps you didn't update your sources after adding the ppa ?

---

### Post by VideoAddicted on 2010-08-22
the ppa is likely where i stumbled.  Are you sure i should be using a kubuntu entry if I'm running ubuntu?

---

### Post by howefield on 2010-08-22
Amarok is a KDE application.

I don't see an alternative (non "k") ppa, even if there was, it would contain the same Amarok files as the one suggested.

---

### Post by VideoAddicted on 2010-08-22
thanks alot.  this has now upgraded my amarok and I of course appreciate how you've been patient with my noobiness :D

---

### Post by howefield on 2010-08-23
> **VideoAddicted said:**
> this has now upgraded my amarok

That's good, glad you are sorted.

You can disable the Amarok repository now that you have installed the version you need, this won't affect your shiny new install of 2.3.1, but obviously leaving the repository intact means that any further updates, eg 2.3.2 will be available to you.

---

