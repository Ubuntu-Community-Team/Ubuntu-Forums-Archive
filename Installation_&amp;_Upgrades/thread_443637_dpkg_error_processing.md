---
title: "dpkg error processing"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by christooss on 2007-05-14
I have tried to install kde4 alfa (I know its alfa stage but i couldnt help myself) and when installing I get this error:

```
Unpacking replacement kde4base-data ...
dpkg: error processing /var/cache/apt/archives/kde4base-data_3.90.1-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/apps/solidfakenetbackend/fakenetworking.xml', which is also in package kde4libs-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde4base-data_3.90.1-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas?

---

### Post by HeavyAl on 2007-08-29
Yep, having the same problem. Someone suggested removing the kde5 libs but I have no idea what effect that would have .. I'm usually a gnome kind of guy so I'm just getting my feet wet with kde and dont understand the dependencies yet.

---

