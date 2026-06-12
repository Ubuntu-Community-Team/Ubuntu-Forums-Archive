---
title: "Installing w32codec in automatix"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by derrekito on 2007-07-12
I tried installing codec packs via automatix, i got a FAILED error, and now it has broken my apt-get.

E: The package w32codecs needs to be reinstalled, but I can't find an archive for it.


I've tried using guides from the forums including [http://ubuntuforums.org/showthread.php?t=54549](http://ubuntuforums.org/showthread.php?t=54549)

but most of their site references give me a 404 Error.  I also tried using a debian repository that was mentioned in the above post, but it just didn't work.

Now I cannot do anything with apt-get except update because of this damned error.

---

### Post by Gremlinzzz on 2007-07-12
[https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles](https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles)
:guitar:

---

### Post by derrekito on 2007-07-12
THANK YOU!!!!!!!:guitar:

---

### Post by Gremlinzzz on 2007-07-12
try 
apt: apt-get install -f
:guitar:

---

### Post by derrekito on 2007-07-12
> **Gremlinzzz said:**
> try 
apt: apt-get install -f
:guitar:

yeah I tried that prior, but it just couldnt find the package in the repository ANYMORE which was strange.  But your first post worked like a charm.

---

### Post by Gremlinzzz on 2007-07-12
thought terminal was locked my mistake
:guitar:

---

