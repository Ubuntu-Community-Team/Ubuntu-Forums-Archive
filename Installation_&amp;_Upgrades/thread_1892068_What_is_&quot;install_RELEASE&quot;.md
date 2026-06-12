---
title: "What is &quot;install RELEASE&quot;??"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by matteosistisette on 2011-12-07
Hi,

I've just upgraded from 10.10 to 11.04 with the update manager.

In the ugly new launcher panel on the left of the screen, the first item on the top is called "install RELEASE" and its icon looks the same as the one that you would find in a Live CD to install the system into the hard disk.

If I click it, it launches what seems to be an installer.

What is it supposed to install? 11.04 is already installed. It doesn't make any sense to me..... 

thanks
m.

---

### Post by darkod on 2011-12-07
I never do upgrades, just clean installs, so I am not sure, but could it be that the upgrade is only downloaded and is letting you select when to install it now?

The upgrade process first downloads and then installs, in case your connection drops in middle of upgrading, if I remember correctly.

---

### Post by IWantFroyo on 2011-12-07
Probably for 11.10.

---

### Post by matteosistisette on 2011-12-07
> **darkod said:**
> I never do upgrades, just clean installs, so I am not sure, but could it be that the upgrade is only downloaded and is letting you select when to install it now?

The upgrade process first downloads and then installs, in case your connection drops in middle of upgrading, if I remember correctly.

No, I already went through the installation process. This is not the first time I upgrade btw (i previously upgraded from 10.04 to 10.10).

The upgrade first downloads then installs, but it's not like when you do a fresh install: rather, it installs new packages almost like when you install updates for the current release, and it already did that and there was no error (that I can tell).

The release 11.04 is already installed: the desktop has a totally new look (I guess it is the Unity desktop environment that has replaced gnome).

So I don't understand what the "install RELEASE" is there for. Is it possible that they just "forgot" to remove it in the case of an upgrade?

---

### Post by matteosistisette on 2011-12-07
> **IWantFroyo said:**
> Probably for 11.10.

That wouldn't make much sense. The normal way to upgrade to 11.10 is to open update manager and click on "upgrade"

---

### Post by josephmills on 2011-12-07
you can open your terminal and type in ```
lsb_release -a 
``` What is the version ? I have seen that when I went from 10.10 to 11.04 you can right click on it and get ride of it.

---

### Post by matteosistisette on 2011-12-07
> **josephmills said:**
> you can open your terminal and type in ```
lsb_release -a 
``` What is the version ? I have seen that when I went from 10.10 to 11.04 you can right click on it and get ride of it.

```
$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

```

Yes, I can right-click and uncheck "keep on launcher"; my fear is that the very fact that it is there may mean that something is wrong in the upgrade.

Or maybe they simply forgot to not include it in an upgraded install. If that is indeed the installer of the release, it is very stupid to have it there on an upgraded system. Even if you ran it, I seriously dubt it would work (where would it install _from_?) and I even wonder if it may damage the system.

---

### Post by josephmills on 2011-12-07
> **matteosistisette said:**
> ```
$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

```

Yes, I can right-click and uncheck "keep on launcher"; my fear is that the very fact that it is there may mean that something is wrong in the upgrade.

Or maybe they simply forgot to not include it in an upgraded install. If that is indeed the installer of the release, it is very stupid to have it there on an upgraded system. Even if you ran it, I seriously dubt it would work (where would it install _from_?) and I even wonder if it may damage the system.


lol there is also the cool commands 
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
which run the upgrade from the CLI (terminal/konsole whatever)
At any rate have a good one.

---

### Post by grahammechanical on 2011-12-07
I saw this when I tried out 11.04 Edubuntu and that was a fresh install. Likewise, I did not dare try it even out of curiosity. This is what I think:

The Live CD puts an install icon on the desktop. From 11.04 onwards icons are not supposed to be put on the desktop but in the Launcher; ugly launchers are not discriminated against.

Someone has failed to remove some code from the hard disk install program and so this icon gets put in the launcher even though it is not needed.

I put this down to an oversight on someone's part.

Regards.

---

### Post by oldtimer7777 on 2011-12-07
It sounds like it could be the gtk-ubiquity installer.. you can probably just do a quick search in synaptic package manager and remove it.

> **matteosistisette said:**
> Hi,

I've just upgraded from 10.10 to 11.04 with the update manager.

In the ugly new launcher panel on the left of the screen, the first item on the top is called "install RELEASE" and its icon looks the same as the one that you would find in a Live CD to install the system into the hard disk.

If I click it, it launches what seems to be an installer.

What is it supposed to install? 11.04 is already installed. It doesn't make any sense to me..... 

thanks
m.

---

### Post by matteosistisette on 2011-12-07
> **oldtimer7777 said:**
> It sounds like it could be the gtk-ubiquity installer.. you can probably just do a quick search in synaptic package manager and remove it.

Oh yes, thanks, it is. Searching applications for "ubiquity" brings up that icon.

So, it actually IS the live cd installer, right?

---

### Post by ubuntu27 on 2011-12-07
Any screenshots?

---

