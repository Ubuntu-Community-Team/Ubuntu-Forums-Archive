---
title: "Upgrading to Feisty from CDROM without network?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by mikelygee on 2007-05-06
I've got an Apple eMac running Edgy. Network connection is dialup, though I have access to a faster connection at work.

My plan was to upgrade using the "alternative' CDROM, then use the package manager to prepare a script to download all the "extras" I've installed that also need upgrading.

Unfortunately, no matter what I tell the installer about not downloading additional packages from the Internet, it insists that it needs to download hundreds of megs to complete the install!

Any help would be greatly appreciated!

---

### Post by confused57 on 2007-05-06
Maybe this will help:
[http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807](http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807)

---

### Post by mikelygee on 2007-05-06
> **confused57 said:**
> Maybe this will help:
[http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807](http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807)

That's what I was trying. Even though I tell it not to download any additional upgrades, it fails without altering the system if I'm not connected to the Internet.

---

### Post by phidia on 2007-05-06
I think if you don't want apt to download from the net you need to disable/comment out your sources in /etc/apt/sources.list

---

