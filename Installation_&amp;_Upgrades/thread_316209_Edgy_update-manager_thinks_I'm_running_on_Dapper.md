---
title: "Edgy: update-manager thinks I'm running on Dapper"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by zakhooi on 2006-12-10
Hi,

For some reason the update-manager thinks my server is running on Dapper while it is running on Edgy.

```

uname -a
Linux linuxbak.zakhooi.net 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

```

WHen I start the update manager it suggest to do a distribution-upgrade but as explained above this is wrong.

Is there a way to re-initialize the update-manager/package-database so it really knows what distribution is running?

Please help

THanks in advance

---

### Post by spd106 on 2006-12-10
Go through the /etc/apt/sources.list and swap "dapper" for "edgy" on every line.

---

### Post by zakhooi on 2006-12-10
> **spd106 said:**
> Go through the /etc/apt/sources.list and swap "dapper" for "edgy" on every line.

I already did that including an apt-get update afterwards, but still with no luck.
Also, I found out that it has problems with a few packages and therefore cannot finish the distribution upgrade, I think that might have something to do with it.

My question is: is there a way to some kind of 're-initialize' the package-manages/update-manager so obtain full integrity?

---

### Post by spd106 on 2006-12-10
Have you tried installing the meta-packages ubuntu-minimal, ubuntu-standard and ubuntu-desktop. These should resolve all the necessary dependencies, though if you're not using gnome there might be another package to install instead of ubuntu-desktop.

---

