---
title: "[SOLVED] Oh ****... Synaptic is dead."
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by Truckerpunk on 2008-10-12
Damn. Something screwed up Synaptic. When I start Synaptic I get this error: 

E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

It seems like some error with the name of the file as it says harTy not harDy... So I changed the name to hardy. But it didn't help. Then I decided to try and delete the file. And that didn't solve my problem either(maybe it made worse?).

Any one have an idea how to fix this?

Help is greatly appreciated.

---

### Post by Truckerpunk on 2008-10-12
Stupid me.... I got it fixed. I forgot to uncheck the repo's in the software source's.

---

### Post by Partyboi2 on 2008-10-12
> **Truckerpunk said:**
> Stupid me.... I got it fixed. I forgot to uncheck the repo's in the software source's.
That is one way of working around it. You could also check that the spelling of repo is correct in your /etc/apt/sources.list, so that it is
```
deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") hardy all
```

---

