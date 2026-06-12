---
title: "pausable upgrades"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by unknown25 on 2008-09-20
im new to ubuntu ..nd itz look is also very gud nd simple...but i installed 7.10 version nd now they say to upgrade it to 8.40.1:cry:....the upgrade is about 632mb...but i cant download tat much in 1day so r the upgrades pausable????:confused:...bcoz my net speed is too slow....i cant do in 1day!!!!!pls sum1 help[-o<....nd i cant even use the package screenlets nor download Anavnt-window-Navigator nor i can download fusion-icon.....psl help guys....:sad::-(:icon_frown:

---

### Post by Partyboi2 on 2008-09-20
If you have access to a machine that has a faster internet connection, you could use the [[COLOR=Blue]synaptic package download script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") or try [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/").
Or you could just download a few updates each day, might take awhile but eventually you would get there.

---

### Post by kostkon on 2008-09-20
> **unknown25 said:**
> im new to ubuntu ..nd itz look is also very gud nd simple...but i installed 7.10 version nd now they say to upgrade it to 8.40.1:cry:....the upgrade is about 632mb...but i cant download tat much in 1day so r the upgrades pausable????:confused:...bcoz my net speed is too slow....i cant do in 1day!!!!!pls sum1 help[-o<....nd i cant even use the package screenlets nor download Anavnt-window-Navigator nor i can download fusion-icon.....psl help guys....:sad::-(:icon_frown:
Don't upgrade, you don't have to do it necessarily.

I am saying this because there are various ways you can install *AWN* in *Gutsy*, check [here]("http://wiki.awn-project.org/DistributionGuides").

Also, *Screenlets* are in the *Gutsy* *Backports* repository. Thus, if you enable this repository (i.e. *Backports*) from *System -> Administration -> Software Sources* (select the *Updates* tab), you will be able to install *Screenlets* using *Synaptic*.

Furthermore, you will be able to install *fusion-icon* using *Synaptic* if you add the following PPA to your software sources list
```
deb http://ppa.launchpad.net/maco.m/ubuntu gutsy main restricted universe multiverse
```
You can add it if you go again to *System -> Administration -> Software Sources* and in the *Third-Party Applications* tab add the above repo line by pressing the *Add* button.

Hope that helps you.

---

### Post by unknown25 on 2008-09-20
Thanx bro..thanx for saying how to install but i cant install the screenlets,i downloaded the .deb file nd i get some error like this **_[U][COLOR="Red"]Error: Dependency is not satisfiable: python-central[/COLOR]_[/U]**


[COLOR="Lime"]can u say me which is better avant or Cairo dock....[/COLOR]

---

