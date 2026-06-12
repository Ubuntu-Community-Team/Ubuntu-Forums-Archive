---
title: "How to upgrade dapper-&gt;edgy from CD?"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by jrjazzman on 2006-11-13
I downloaded the Edgy ISO thinking I could upgrade from it.  I've seen some references to the cdromupgrade command, but not sure if this method has been blessed by people who actually understand the upgrade.  

So can you upgrade from CD and is it recommended?

---

### Post by missmoondog on 2006-11-13
it is generally recommended to just do a clean install of any new version. i do believe if you try to upgrade from the cd, being an iso, it won't do anything, and if it does, i'm sure it will turn into a full, clean install. you can add the cd drive to your list of repositorys and try it.

---

### Post by shirilover on 2006-11-13
You need the alternate install CD to upgrade.
then just
```

gksu "sh /media/cdrom/cdromupgrade"

```

---

### Post by jrjazzman on 2006-11-13
> **missmoondog said:**
> it is generally recommended to just do a clean install of any new version. i do believe if you try to upgrade from the cd, being an iso, it won't do anything, and if it does, i'm sure it will turn into a full, clean install. you can add the cd drive to your list of repositorys and try it.

I'll just use the update-manager (whatever this is.  no --help or man page).  Too bad update-manager can't use torrents.  It took me about 30 minutes to download the ISO.  It looks like it will take all night to download packages via update-manager. 

I hope someone is working on making upgrades work in a reasonably user friendly way.

---

