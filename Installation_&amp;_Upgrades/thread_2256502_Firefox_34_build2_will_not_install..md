---
title: "Firefox 34 build2 will not install."
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by facosta on 2014-12-13
I was trying to install firefox_34 and I get this error:
How can I resolve the error below.

E: /var/cache/apt/archives/firefox_34.0+build2-0ubuntu0.14.04.1_amd64.deb: cannot copy extracted data for './usr/lib/firefox/libxul.so' to '/usr/lib/firefox/libxul.so.dpkg-new': unexpected end of file or stream

---

### Post by mikewhatever on 2014-12-13
Most likely, you just need to redownload the deb package. Clean the cache with <sudo apt-get clean>, then try updating.

---

### Post by facosta on 2014-12-14
Gracias amigo.I used sudo apt-get clean and was able to install firefox 34.

---

