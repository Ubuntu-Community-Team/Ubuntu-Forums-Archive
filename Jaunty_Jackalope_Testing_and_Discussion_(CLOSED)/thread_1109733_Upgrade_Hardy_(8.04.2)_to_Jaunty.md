---
title: "Upgrade Hardy (8.04.2) to Jaunty?"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by infoseeker on 2009-03-29
I have Kubuntu Hardy Heron (8.04.2) installed and was wondering whether an upgrade to Kubuntu Jaunty would be a good idea or not, or could even be possible. The reason I ask is because I have a messy mixture of KDE3 and KDE4 (double menu entries, etc), and was wondering if this mess would be cleaned up in the process?

Currently attempting to remove KDE4 menu items results in warnings of potential errors (breakage).

KDE4 in Jaunty is what I'm willing to have a look at ;)

Thanks

---

### Post by cariboo on 2009-03-29
You may be better off doing a clean install, as you will have to update to Intrepid before updating to Jaunty. If you do want to take the update path, comment out any ppa's you have enabled, then make sure Hardy is fully updated then press Alt-F2 and type:

```
gksu update-manager -d
```

This will start the udate process to Intrepid. Then be absolutly certian that the update has finished, then you can run the above command again to update to Jaunty.

Jim

---

### Post by cookieforyou on 2009-03-29
> **cariboo907 said:**
> You may be better off doing a clean install, as you will have to update to Intrepid before updating to Jaunty. If you do want to take the update path, comment out any ppa's you have enabled, then make sure Hardy is fully updated then press Alt-F2 and type:

```
gksu update-manager -d
```

This will start the udate process to Intrepid. Then be absolutly certian that the update has finished, then you can run the above command again to update to Jaunty.

Jim

I presume the 'gksu' would be replaced with 'kdesu' ?

---

### Post by infoseeker on 2009-03-29
```
$ sudo update-manager -d
passprompt

sudo: update-manager: command not found

```

```
$ sudo apt-get install update-manager
Reading package lists...


Building dependency tree...

Reading state information...


Package update-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  update-manager-core

E: Package update-manager has no installation candidate


```
```
$ sudo apt-get install update-manager-core
Reading package lists...


Building dependency tree...

Reading state information...


update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

hmmmmm ?

EDIT: I presume my sources.list file needs editing?
EDIT: I think the clean install is going to be a better option ;)

---

### Post by pbpersson on 2009-03-29
My advice would be this......if you have a corrupted system, save your data and do a fresh install.

An update to a new version is not going to untangle your mess, it will just give you an updated mess.....and since the system.....well, I would consider the system unstable and it could just crash in the middle of the upgrade.

An update to a new version is never designed to think "let me do a sanity check on your current system and fix all possible problems", that is what a fresh install is for.

---

### Post by Justin Trouble on 2009-03-30
You need the Kubuntu specific instructions - it's been assumed you are running the Gnome desktop. *update-manager* is not installed under Kubuntu - your installation isn't corrupted or messed up.

See [https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu](https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu) to upgrade from Hardy (8.04) to Intrepid (8.10) first.

Then [https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu) to upgrade from Intrepid to Jaunty beta (9.04).

Or you can upgrade directly from Hardy to Jaunty beta: [https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04)

---

