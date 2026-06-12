---
title: "My update center show 12.10 but I have 12.04 LTS"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by editheraven on 2013-01-04
When i did apt-get update this morning and updated my packages I also checked the update manager, just for a check. And i was surprised to see that my LTS is able to update to a normal release. I checked my repos and they are indeed only for precise, not quantal.

Why does it shows, then, that available upgrade?

---

### Post by zvacet on 2013-01-04
In synaptic>repositories>updates at the bottom of the window you can choose to upgrade to normal or LTS release.If you don´t want to upgrade from LTS to normal set upgrade to LTS.In case that you don´t have synaptic installed

```
sudo apt-get install synaptic
```

---

### Post by editheraven on 2013-01-04
I have selected in syn "lts support" already.

---

