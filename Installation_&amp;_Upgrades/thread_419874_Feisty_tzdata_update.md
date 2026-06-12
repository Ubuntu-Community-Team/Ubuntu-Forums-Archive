---
title: "Feisty: tzdata update"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by PartisanEntity on 2007-04-23
There was supposed to be an update in Feisty today for tzdata. But this is the message I get when I try to update:

```
W: Failed to fetch http://at.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb
  404 Not Found
```

Is this temporary? Anyone else get this?

---

### Post by jthirt on 2007-04-23
I have the same, although from a different URL :

```
W: Échec de la récupération de http://fr.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb
  404 Not Found
```

It actually prevents me from applying some other distribution updates related to nfs.

I have the same on another system still running edgy just like [here]("http://ubuntuforums.org/showpost.php?p=2494983&postcount=1")

---

### Post by PartisanEntity on 2007-04-24
I got it to work by opening Synaptic Package Manager > Settings > Repositories and then selecting a different server for 'Download from:'.

---

### Post by jthirt on 2007-04-24
Fixed itself tonight without changing anything :)

---

