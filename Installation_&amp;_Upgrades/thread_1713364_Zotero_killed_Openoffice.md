---
title: "Zotero killed Openoffice"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by BigBaka on 2011-03-24
Help!

I just upgraded a version of Zotero, the references plugin for Firefox, and it had a long java install process that was some sort of integration with open office, but it seems to have completely killed openoffice. I couldn't open anything in open office afterwards as it says the openoffice3 not found. So I removed openoffice in synaptic, then removed zotero and then tried to reinstall openoffice 3.3.3 from the deb, and half way through I get the following error.

```
Setting up openoffice.org3-dict-es (3.3.0-20) ...

Setting up openoffice.org3-writer (3.3.0-20) ...
Setting up openoffice.org3-calc (3.3.0-20) ...
Processing triggers for menu ...
Errors were encountered while processing:
 DEBS/desktop-integration/openoffice.org3.3-debian-menus_3.3-9556_all.deb

```
And the whole process quits and now I can't do any work! WTF? 

I looked in synaptic and despite the error in the installation it has openoffice 3 recorded as having been installed. But if i try and run writer on anything I get

```
Failed to execute child process "openoffice.org3" (No such file or directory)
```

Any assistance much appreciated!

Lucky it is now lunch time so I have some time to deal with this bollocks! 

I'm running Lynx with OOo 3.3 en-GB. Zotero is no more!

BB

---

### Post by BigBaka on 2011-03-24
Hmmm,

seems like whatever zotero did it was some problem with the command in the main menu. To fix it I went to system - preferences - main menu and once in there I manually changed each launch command for the office applications in openoffice (base, calc, draw, math, impress, writer) to point directly at the launch file as below.

```
/opt/openoffice.org3/program/s[name] %U
```

That seemed to fix things, although I'm still worried about the installation error. As for zotero, well for it's troubles i think it can stay dead.

BB

---

