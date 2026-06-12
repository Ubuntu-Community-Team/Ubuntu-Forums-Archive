---
title: "Thunderbird crashes, eats RAM"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by pmorton on 2008-04-29
Since Hardy install, Thunderbird has started crashing and max-ing out memory. Running it from a terminal gives the repeated message: 

"recurrence tweaking exception:TypeError: baseDuration has no properties"

Does anyone know what that means? Has anyone got the same problem? I've tried removing and reinstalling TB but to no effect. I've now uninstalled and installed the tarball from Mozilla, and got that working, but I'm puzzled. Hardy's got a lot of quirks kicking about!

---

### Post by pmorton on 2008-04-29
I've discovered this is an extensions problem; which, I don't know, but I've moved all extensions from ~/.mozilla-thunderbird/xx.xxx.defaul//extensions, and I guess I'll need to put them back one by one to find the culprit.

---

### Post by pmorton on 2008-05-08
> **pmorton said:**
> I've discovered this is an extensions problem; .

And the extension is Lightning 0.8. Disabling it resolves the problem; Enabling it causes at launch Thunderbird to hang and memory to max out.

The Mozilla download is doing the same thing.

---

### Post by pmorton on 2008-05-08
Removing the lightning data file, storage.sdb, from the ~/.thunderbird/xx12yy3z.default data directory cures the problem. It seems that storage.sdb has become corrupted. Now I need to try to find a way to recover the data from it. But I'm wondering if I should change calendar programs if its reliability is not much better than the deadly Outlook .pst file.

---

