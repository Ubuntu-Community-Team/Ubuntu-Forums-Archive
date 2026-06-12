---
title: "QT library conflict running Sigil"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by angelsguitar on 2013-06-06
Hi.

First of all, I'm running Precise (Ubuntu 12.04)

I installed Sigil from this ppa, but used the repository from Ubuntu Raring (13.04) since for some reason sigil is not available for Precise right now:

[https://launchpad.net/~sunab/+archive/sigil-git]("https://launchpad.net/~sunab/+archive/sigil-git")

I also added the QT Edgers ppa ([https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-proper]("https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-proper")) in order to have the most recent QT, as Sigil requires it.

The installl went without problems.  However, when I try to run Sigil, I get this error:

```
Cannot mix incompatible Qt library (version 0x50001) with this library (version 0x50002)
Aborted

```

Seems Sigil has a conflict between QT versions, as I have both QT 4 and 5 installed.  Any suggestions on how to make Sigil use the correct libraries?

---

