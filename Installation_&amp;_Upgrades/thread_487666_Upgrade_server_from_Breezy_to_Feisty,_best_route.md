---
title: "Upgrade server from Breezy to Feisty, best route?"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by blueorder on 2007-06-29
Hey y'all...

I have a dual Xeon server running 5.10 server and am wondering what the best route would be to get to 7.04.

The server has 2 hard drives and has system + some storage on first drive and second drive is purely storage.

I have a feeling that the answer is going to be clean install. If it is, how would I go about that without touching the storage in drive 1.

Thanks in advace...

---

### Post by az on 2007-06-29
> **blueorder said:**
> Hey y'all...

I have a dual Xeon server running 5.10 server and am wondering what the best route would be to get to 7.04.

The server has 2 hard drives and has system + some storage on first drive and second drive is purely storage.

I have a feeling that the answer is going to be clean install. If it is, how would I go about that without touching the storage in drive 1.

Thanks in advace...

The upgrade route would be to dist-upgrade to breezy, then to Dapper, then Edgy and then to Feisty.  It should be striaghtforward.  Dist-uipgrading from one LTS release to another LST release will be easy, since you will be able to skip all the releases in between.

Dist-upgrading on a desktop is easy too.  The hard part is that a lot of people install third-party applications that stop working, or that interefere with the rest of the system.  This is typically not a prpoblem on a server, since things are much more lean and you don't go around installing things willy-nilly.

Still, if you want to reinstall, just boot the installer and wipe the Hoary root partition.  You can tell the install to mount your storage drive and partitions and it will not touch them unless you tell the installer to format them.

---

