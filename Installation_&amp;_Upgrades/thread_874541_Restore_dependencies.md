---
title: "Restore dependencies"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by Nonno Bassotto on 2008-07-30
I went through the upgrade from Gutsy and I got stuck with the [locales bug]("https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340"). So I had to stop the install process and continue the installation manually after a reboot.

Now all dependencies are broken. I have a lot of stuff under the "auto removable" or the "Local" sections in Synaptic. Is there any hope to restore the dependencies? The auto removable section was actually useful to remove unused dependecies after software remotion.

---

### Post by zvacet on 2008-07-30
**synaptic>edit tab>fix broken packages**

or 

```
sudo apt-get -f install
```

---

### Post by Nonno Bassotto on 2008-07-30
There are no broken packages to fix. Simply I have packages like "gutsy-wallpapers"  (and many more others) under Auto removable and packages like "cdrecord" and "libtotem-plparser7" under Local or obsolete. In other words, a complete mess. Should I make a clean install or can I fix it somehow?

---

### Post by Nonno Bassotto on 2008-07-30
Bump...

---

### Post by Nonno Bassotto on 2008-08-01
Bump

---

