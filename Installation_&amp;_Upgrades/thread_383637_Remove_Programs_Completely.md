---
title: "Remove Programs Completely"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by jengerer on 2007-03-13
Hello,

Whenever I open MP3 files, it opens them with Totem Movie Player which, strangely, can't open MP3 files correctly... so I used sudo apt-get remove and removed it, and now it uses VLC player which is awesome...

but whenever I get updates, it redownloads it.

Is there any way to remove this program from automatically downloading?

---

### Post by bruenig on 2007-03-13
If you sudo apt-get remove totem, it shouldn't redownload.

---

### Post by zvacet on 2007-03-13
```
sudo apt-get remove --purge filename
```

---

